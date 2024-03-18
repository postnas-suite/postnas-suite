## PostNAS-Suite Anwendertreffen am 25.5.2016 in Unna

- Termin: 25.05.2016 Kreishaus Unna
- Einladungsmail: http://lists.osgeo.org/pipermail/nas/2016-April/000833.html
- 17 TeilnehmerInnen


### Themen 

- Einleitung
- Performanztuning (Marvin Brandt, Andreas Fischer – Kreis Unna)
- Kartographische Darstellung des QGIS-Projektes (Norbert Dephoff – Stadt Münster)
- Umsetzung der Amtlichen Basiskarte (Jutta Lusebrink, Marina Kühn – Oberbergischer Kreis, Andreas Fischer – Kreis Unna)
- Verschiedenes 
- Vorbereitung des nächsten Anwendertreffens


### Einleitung 

#### PostNAS Suite Schaubild 

- Schaubild Jäger und norBIT 
- Folien: http://trac.wheregroup.com/PostNAS/browser/trunk/anwendertreffen/PostNAS_Anwendertreffen20160525.pdf?order=name

Komponenten:
- PostGIS Datenbank und Postprozessing nach der Dateneingabe 
- Nutzerabhängige Datenvereinbarung: 
- QGIS Plugins: ALKIS Kartendarstellung, NorBIT Suche, Datenbankimport
- NorBIT Mapfile Erstellung (Mapbender Einbindung und WMS Erstellung)
- ALKIS Suche mit neuem Fokus
- Mapfile Anpassungen
- Mapbender: PHP Anpassungen für Infoabfrage und Navigation 
- PostNAS ABK-light Mapfile (OBK)

### Performanztuning (Kreis Unna) 

- Hardwareausstattung
- Konfiguration des DBMS (Herr Brandt) 
- Verarbeitungslogik intern
- technische Implementierung

Problem: 
- Verarbeitungszeit mit Nachbearbeitung dauert lange
- Postprozessing müsste optimiert werden für Zeitersparnis 
- neues Feedback in der Mailingliste Thema: '''[PostNAS Suite] PostgreSQL-Tuning''' siehe https://lists.osgeo.org/pipermail/nas/2016-June/000873.html

Lösung: 
- Konfiguration in der postgres.conf 
- Cachen: 
 - mehr RAM zur Verfügung stellen
 - Shared Buffer auf 1⁄4 des RAM setzen – default: 128 MB
- Transaktionen des Datenbankservers: 
 - Veränderungen werden zunächst in Logfiles gespeichert
 - Zwischenstände nach 3 Logfiles (je 16 MB) werden in Datenbank gespeichert 
 - Problem: Plattenzugriffe bremsen System aus
 - Lösung: Anzahl der Segmente empirisch bestimmen (hier 64) – default: 3 (1 = 16 MB), Parameter -checkpointsegments- auf 64 Segmenten setzen
 - Logging muss aktiviert werden um Checkpoints zu nutzen, optimal: weniger Checkpoints, z.B. alle 5 Minuten
- Planer optimiert
 - SQLs optimieren
 - RandomPageCost auf 2 = HDD oder 1,01 = SSD setzen – default: 4 (veraltet)
 - effektive_cache-size auf RAM – Shared Buffer setzten - default deaktiviert
 - Festplattenzugriffe
 - Arbeitsspeicher hochsetzen, -effective_cache_size- aktivieren
- Vacuum Analyse durchführen
 - in Postprocessing Skript integrieren (default: nicht vorhanden)
- Verarbeitungslogik intern 
 - Vorschlag: Postprocessing Aufbereitung nur in Teilen oder bei neuen Objekten 
- technische Implementierung
 - parallele Transaktion
 - verb. SQL-Syntax
 - Qualitätsprüfung

Ergebnis: 
- verbesserte Verarbeitungszeit zu 1,5 h der Fortführungsdaten/ 7 h aller Daten --> Reduktion auf 25% der ursprünglichen Aufwendung
- RVR: Empfehlungen größtenteils durchgesetzt
 - deutliches Performanztuning festgestellt
 - große Flurstückanzahl macht Import noch immer kritisch 
 - Unabhängig von der Größe des Folgedatensatzes gibt es keine starken Unterschiede
- Veränderungen an dem DBMS für weiteres Performanztuning nötig
- Verbesserung durch erhöhte Ressourcenzuteilung leicht möglich

### Kartographische Darstellung des QGIS-Projektes (Stadt Münster) 

- Stadt Münster Herr Vielain-Scheu
- NorGIS ALKIS-Einbindung → Version: QGIS Plugin Import 2.0.4
- Verbesserung zur Ansicht der Gemarkung und Fluren der Stadt Münster
- QGIS Projekt der NorBIT Lösung von der Stadt Münster

Verbesserungsansätze für die Darstellung:
- Flurgrenzen, Gemarkungsgrenzen und Landkreisgrenzen wurden dicker gezeichnet
- Beschriftungen für Flurgrenzen und Flurbezeichnungen, Gemarkungsgrenzen und Landkreisgrenzen wurden eingefügt (Ansatz: Politische Grenzen)

Lösung: 
- Layer wurden regelbasiert nach Maßstab eingeteilt
- Flurgrenzen und Gemarkungsgrenzen nach Signaturnummer mit unterschiedlicher Linienbreite in Maßstäbe eingeteilt

Problem: Gemarkungsbeschriftungstabelle wird standardmäßig nicht mit der norGIS ALKIS-Einbindung angelegt, daher Skript von Frank Jäger nötig

Flurgrenzen: 
- 0 – 1.000 Breite : 1,01
- 1.000 – 5.000 Breite: 2,00
- 5.000 – 10.000 Breite: 4,00
- 10.000 – 50.000 Breite: 6,00 

Gemarkungsgrenzen: 
- 0 – 1.000 Breite : 1,01
- 1.000 – 5.000 Breite: 4,00
- 5.000 – 10.000 Breite: 8,00
- 10.000 – 50.000 Breite: 14,00
- 50.000 – 100.000 Breite: 17,00 
- 100.000 – 500.000 Breite: 22,00 

Landkreisgrenzen: 
- 0 – 1.000 Breite : 1,51
- 1.000 – 5.000 Breite: 4,00
- 5.000 – 10.000 Breite: 8,00
- 10.000 – 50.000 Breite: 12,00
- 50.000 – 100.000 Breite: 17,00 
- 100.000 – 500.000 Breite: 22,00 
- 500.000 – 2.000.000 Breite: 27,00 

Flurbezeichnungen:
- 1 – 2.500 Größe: aus der Tabelle alte Einstellung übernommen
- 2.500 – 5.000 Größe: 10
- 5.000 – 10.500 Größe: 20
- 10.000 – 25.000 Größe: 40

Lagebezeichnungen (Straßennamen):
- 1 – 5.000 Größe: aus der Tabelle alte Einstellung übernommen
- automatische Ableitungsregeln gibt die Tabellenschriftgröße weiter

Gemarkungsnamen: 
- Gemarkungsbeschriftungstabelle wird standardmäßig nicht mit der norGIS ALKIS-Einbindung angelegt, daher Skript von Frank Jäger nötig (zur Ableitung der Platzierung der Gemarkungsnamen wurden die Tabelle pp_gemarkung.simple_geom)
- 1 - 1.000 Größe: 10
- 1.000 – 5.000 Größe: 20
- 5.000 – 10.000 Größe: 40
- 10.000 – 25.000 Größe: 80
- 25.000 – 50.000 Größe: 150
- 50.000 – 100.000 Größe: 250
- 100.000 – 250.000 Größe: 500

Diskussion zur vereinheitlichten Farbdarstellung Herr Jäger: 
- Vorlage der Farbdarstellung gut
- je nach Projekt eigene Lösung zur Darstellung optimaler
- in großen Maßstäben hoher Anpassungsbedarf laut Norbert Dephoff/ Stadt Münster
- Einbindung in die generelle Darstellung gewünscht/  Modell für alle gewünscht (RVR)

Lösung: 
- Jürgen Fischer schaut sich die Styles an und prüft die Umsetzbarkeit

### Umsetzung ABK (Kreis Unna, OBK Frau Lusebrink) 

- WMS auf Grundlage der Rasterdaten
- WMS auf Grundlage der PostNAS Daten
- Integration in die PostNAS-Suite

WMS auf Grundlage der Rasterdaten (Kreis Unna): 
- schnell und unkompliziert zur Unterstützung der schrittweisen Einführung
- "GeoInfoDok"-konforme Darstellung
- „Zwischenlösung“ aufgrund eingeschränkter Darstellungsqualität / -möglichkeiten
- Kacheldiensteinbindung 
- schrittweise Gemeindeeinführung
- DGK wird in den Bereichen nicht weitergeführt
- Zwischenlösung da Darstellung sehr eingeschränkt ist
- Anwendung GeoService .online Kreis Unna (http://www.geoservice.kreis-unna.de/)

Andere Lösung: 
- David WMS bei Münster 
 - begrenzt auf Katasteramt
 - Performanz nicht optimal
 - Anpassungsbedarf der Darstellung für Beschriftung usw.
 - Maßstabsabhängig erstellte Layer sind nicht optimal (z.B. Bäume und Gebäude 1:1000)

WMS auf Grundlage der PostNAS Daten (OBK):
- „ABK light“
- MapFile-Erstellung für den UMN-MapServer
- Entwicklung und Einsatz (Intranet) im Oberbergischen Kreis
- Transparenzdarstellung eher nötig für Hintergrund-Dienste, daher nicht GeoinfoDok-Konform
- Style: schwarze/ graue Grenzen, simpel gehalten, nur Linien
- noch in Bearbeitung, noch keine SVG-Symbole wegen der Serverversion und MapServer Version 6.4
- gemeindeweise Einführung der -ABK bis 2019- (DGK-Ablösung bis 2019 in NRW)
 - roter Punkt: Darstellung eines unbekanntes Objekts in dem Kreis
 - parallel zu DGK die ABK im Amt im Einsatz
 - in Münster: keine Fortführung der DGK
-  '''Böschungsschraffuren problematisch''' darzustellen 
 - Böschungskliffen nicht dargestellt, nur Flächen schraffiert
 - Böschungsinfos sind in den ALKIS-Daten enthalten

Integration in die PostNAS-Suite (Kreis Unna):
- Umsetzung aller Darstellungsvorschriften der GeoInfoDok sehr umfangreich (SVG-Graphiken)
- Erstellung weiterer Kartendarstellungen im QGIS-Projekt
- Bereitstellung eines WMS auf der Grundlage des QGIS-Projektes (QGIS-Server) und / oder des UMN MapServer (MapFile-Generierung)

### Verschiedenes 

- RVR: Dateneinbindung in ArcGIS problematisch

#### Harmonisierung Postprocessing, Vereinheitlichung 

- Anpassung der Buchauskunft von Frank Jäger (im svn unter alkisn)
- Anpassung des Mapfiles von Frank Jäger (Anpassung des QGIS-Mapfiles)
 - Layer aus dem QGIS-Mapfile übernommen: Gruppierung und Prioritäten werden aus QGIS übernommen, aber im WMS nicht immer korrekt angezeigt
- Legende wird nicht korrekt angezeigt,z.B. noch riesige Symbole, muss noch weiter bearbeitet werden
 - Copyright und Templates eingefügt 
 - Anpassungsbedarf: es fehlen z.B. Flur, Gemarkung (ehemals pp-Tabellen)
  - nur relevante Daten für die jeweiligen Ortsteile notwendig

;Bodenschätzung 
- Bodenschätzungsdaten werden in der NorBIT Lösung nicht eingesetzt
- Frage: Sollen die Daten aus dem Schema entfernt werden?
- Frage: Welches Modell beinhaltet welche Infos? 
 - für unterschiedliche Maßstäbe liegen doppelte Infos bei mehreren Modellen vor, aber es treten auch fehlende Infos bei Nutzung von einem Modell auf z.b. nur Präsentationsmodell DKKM 1000 statt auch DKKM 500 
 - jeweils ein Präsentationsmodell und ein Datenmodell sollten kombiniert werden
 - Mix der Modelle in einer PostNAS Datenbank bei Münster

#### Google Server & QGIS-Server 

- Frage: Macht es Sinn ein Projekt bei Google Server online zur Verfügung zu stellen? 
 - Google Server ist schneller geworden, aber mit UMN-Mapserver-Performanz nicht zu vergleichen
 - MapServer ist anpassbarer, FeatureInfo-Templating ist mit Mapserver simpler
- QGIS-Server
 - Performanz noch nicht so wie UMN Mapserver
 - Dokumentation nicht auf gleichem Stand wie bei UMN-Mapserver
 - MSQL Inkompabiltät / Fehlermeldungen fehlen/ Logfiles nicht hilfreich

Ergebnis: 
- kein Bedarf an Google Server 

#### Mapbender 

Solr Apache Suche
- Grundbuch-, Eigentümer- und Flurstückssuche
- bis FossGIS/ nächstem Anwendertreffen soll eine Demo-Anwendung entstehen mit Solr auf Basis von RLP-Musterdaten

#### Genauigkeit der Daten 

- Genauigkeit der Grenzpunkte
- Wo die Daten herkommen ist über den ALKIS-Import nicht erkennbar
- Die Lagezuverlässigkeit wird nicht importiert
 - Fehlende Infos aus den NAS-Daten können folgendermaßen importiert werden: 
  - Datenbankstruktur vor dem Import anlegen
  - Datenbanktabellen um fehlende Spalten erweitern
  - dadurch können einige Daten auch in die jeweilige Spalte der Tabelle übertragen werden 

### Vorbereitung nächstes Treffen 

Themen der nächsten Sitzung/ Festgestellte Entwicklung: 

- Umstellung der ALKIS-Nutzungsdaten auf das norBIT-DBSchema
 - keine weitere Nutzung der ursprünglichen/ klassischen Mapfiles

- Modellarterweiterung
 - Abstimmung mit Peter Korduan auf der FOSSGIS
 - '''Genauigkeit von Vermessungspunkten''' → Integration/ Schemaerweiterung durch NorBIT
 - '''Bodenschätzung?''' → offen
 - '''kommunale Objekte'''
 - adminstrative Einheiten (Gemarkungen, Fluren als Flächenobjekten)

- Skript Flächengenerierung
 - Gemarkungen- und Gemeindegrenzen 
 - bis jetzt keine saubere Flächendeckung/ Löcher
 - wird erst einmal nicht weiterverfolgt

- Darstellungsregeln der ALKIS-Daten
 - Orientierung an SLD von Münster (s.o.)
 - einheitliche Anpassung und Einbindung in QGIS Plugin in Diskusion 
 - 1 Tag Aufwand

- ABK
 - ABK muss bis 2019 (NRW) realisiert werden
 - Realisierung mit hohem Arbeitsaufwand verbunden
 - Aufwand: 1-2 Wochen, 5.000-6.000€ Aufwand
 - Einwand RVR:  Eher David WMS/ IBR WMS nutzen?
  - Problem AutoCAD, da hier keine David-WMS-Einbindung möglich ist
  - David ist maßstabsstufenabhängig und stark spezialisiert auf bestimmte Ansprüche und Zoomstufen
  - Datenüberarbeitung vor ABK Erstellung nötig

- Performanzverbesserung: 
 - RVR: bessere Performanz gewünscht, Termin für einen Test steht noch nicht fest
 - Aufwand: 3 Wochen
- Einsatz von QGIS-Server/ QGIS-WMS mit ALKIS-Infoauskunft:
 - Erweiterung von QGIS Server:  wird immer wieder stetig aber langsam verbessert, Performanz nicht optimal, 
 - FeatureInfo: nur HTML-FeatureInfo
 - Interesse wurde genannt im Zusammenhang mit dem Einsatz von norBIT und Kartenpublikation über QGIS Server 

Peter Korduan: 
- Bericht zum Aufbau eines vollständiges Datenmodell für den PostNAS Konverter auf der Basis des Implementierungsschemas des AAA Modells 
- war am 25.5.2016 nicht anwesend, Vortrag auf einem der nächsten Anwendertreffen erwünscht

### nächstes Treffen 

FOSSGIS 2016 Salzburg
- 1.Tag 04.07.16
- 18:30-19:00 Uhr
- Grüner HS
- http://frab.fossgis-konferenz.de/de/2016/public/events/5026 

 
übernächstes Treffen:
- Anfang Dezember 
- Münster


