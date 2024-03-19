## PostNAS-Suite Anwendertreffen am Mittwoch 25. Oktober 2017 , 11 – 16 Uhr in Gummersbach


- Termin: Mittwoch 25. Oktober 2017 , 11 – 16 Uhr
- Ort: Hohenzollernbad, Sitzungsraum Erdgeschoss E-12, Moltkestraße 45, 51643 Gummersbach
- Moderation Marina Kühn
- Einladungsmail: [https://lists.osgeo.org/pipermail/nas/2017-May/000972.html](https://lists.osgeo.org/pipermail/nas/2017-May/000972.html)
- Teilnehmer/-Innen: 16 Personen

### Themen 

- Erweiterung des PostNAS ALKIS-Schemas (ax_lagebezeichnung.beziehtsichauf(ax_gebaeude) fehlt/inverszu)
- Harmonisierung Postprocessing, Vereinheitlichung
- Darstellungsregeln der ALKIS-Daten
- Symbole in QGIS/AutoCAD/MAP-File
- ABK NRW
- QGIS Plugin PostNAS Suche
- Performanzverbesserung
- QGIS Server mit ALKIS-Infoauskunft
- Mapbender3 (Nutzung Mapbender3 beim OBK)
- Modellartenerweiterung (Vorstellung verschiedener Erweiterungen beim OBK)
 - ALKIS Straßen- und Gebäudemarker
 - ALKIS Info Nutzung, Info Gebäude
- ALKIS Themenkarte (Flächendifferenzen)
 - Böschungen (vorläufige Lösung beim OBK)
 - Bodenschätzung (Nutzung beim OBK)
- Verschiedenes
 - FOSSGIS 2018 im März 2018 in Bonn
 - Termin für nächstes Anwendertreffen

Vorschläge und Beiträge zur Tagesordnung per E-Mail an Marina Kühn (marina.kuehn (at) obk.de).

Über eine rege Teilnahme würden wir uns sehr freuen.


### Protokoll 

vgl alte punkte aus ![PostNASAnwendertreffen 2017-05-03](./anwendertreffen-2017-05-03.md)


### 1) Erweiterung des PostNAS ALKIS-Schemas 

Frage, ob die Punktauskunft in norBIT mittlerweile integriert ist: 
- Jürgen Fischer:
 - Punkttabellen sollten bereits vollständig im Modell gewesen sein
 - Von der GeoInfoDok abweichende Darstellungen sind aber derzeit nicht vorgesehen (über eigene postprocessing-Skripten aber möglich)
 - Anmerkung:
  - Mit GDAL 2.3 wird auch das vollständige Modell unterstützt (GFS-Datei mit eindeutigen Abbildungen und anderes Schema für die Datenbank-Anlage)
  - Der master-Branch von alkis-import unterstützt dies schon (PostNAS-Wiki wurde bereits aktualisiert)

Demo-Dienste (demo.postnas.org): 
 - Mapbender Demo Anwendung (normal/mobil) kann gerne für Präsentationszwecke genutzt werden
 - Anzeige der Punktnummernübersicht und Abfrage per Feature Info möglich 
 - Demodaten von Mustermonzel enthalten teilw. nicht nötige Daten
- TODO WhereGroup: Neues Einspielen anderer Demodaten und Einbindung von Daten mit Böschungen in den Demodienst

Dokumente: 
- Daten liegen im Wiki unter
- [https://github.com/postnas-suite/postnas-suite-mapserver/blob/main/mapserver/alkis_n/alkis_punktnummernuebersicht.map](https://github.com/postnas-suite/postnas-suite-mapserver/blob/main/mapserver/alkis_n/alkis_punktnummernuebersicht.map)
 
Derzeitige Probleme: 
- Angemerkt vom OBK: Alle Relationen nur in eine Richtung: ax_lagebezeichnungmithausnummer aus ax_gebaeude wird nicht angezeigt
 - in Bremen wird es per default dargestellt, da das Feld per David vermutlich automatisch korrekt gefüllt wird
- Füllung von integer_array schlägt teilweise fehl
 - Tabelle ax_bodenschaetzungen 
 - Spalten entstehungsartoderklimastufewasserverhaeltnisse und sonstieangaben
 - Bekannt: Wenn in der ersten nas-Datei, die eingeladen wird, kein Fall vorliegt, dann wird in den darauffolgenden Dateien kein Inhalt eingebunden - sollte ab Version 2.3 gefixt sein

### 2) Harmonisierung Postprocessing, Vereinheitlichung 

Stand der Buchauskunft: 
- Erbbaurecht bei Münster: 
 - Ansicht der tatsächlichen Eigentümer erst nach Einbindung eines fiktiven Blattes und nicht mehr auf einer Seite
 - Stand wurde geändert bei neuer Version: Flurstückauskunft wieder auf einer Seite und weniger verschachtelte Seiten

OBK Eigentümerabfragen: 
- Eigentümersuche per FME sauber gefüllt beim OBK
 - bei Interesse beim OBK melden
 - FME Workbench kann weitergeben werden
- keine fehlenden Daten festgestellt

### 3) Darstellungsregeln der ALKIS-Daten 

Einbindung der Übergänge ggf. über Projektauftrag (norBIT)?
- Vorschlag und Präsentation vor einiger Zeit, die Zoomstufen bei den Gemeindegrenzen zu optimieren
 - wurde bisher nicht angepasst/ nicht vorgesehen, durchaus sinnvoll bei großen Gebieten 
- Skalierung der Flurstücksnummern wäre wünschenswert (GeoInfoDok sieht feste Größen vor)
 - Hürde: die Bruchstrichlinie wird für die vorgesehene Textgröße generiert

Einbau Schalter in die AutoCAD-Schnittstelle (EDBSgen v. norBIT)?
- Symbole in AutoCAD nicht per Faktor änderbar
- anderer Pfad kann bei AutoCAD derzeit schon genutzt werden
 - für die Nutzung mehrerer Symbolordner nicht benutzerfreundlich
- Faktor bisher nicht eingebunden, wäre jedoch sinnvoll
 - z.B. alle Bilder um 0,3 größer
 - hilfreich auch bei Bildern mit unterschiedlicher Größe


### 4) ABK NRW 

Darstellung von Böschungen: 
- Stand Münster: 
 - ca. 100.000 Böschungen aus der Stadt-Topographie
- Probleme bei Sonderfällen, sehen sonst gut aus 
- Stand norBIT: Bereits gut gelöst, Start beim Anfang der Oberkante, nun müssen weitere Sonderregeln bei fehlerhaft erfassten Daten beachtet werden (unzureichende Regelbasis bei der Erfassung in diversen Systemen)
 - z.B. Begrenzung der Schraffen (Länge unklar) oder Verhalten bei nicht parallelen Ober- und Unterkanten bzw. fehlenden Unterkanten
 - wurde versucht über Regeln zu lösen: Schraffen dürfen sich nicht überschneiden, Maximallänge einer Schraffe, etc.
 - jede Regel bringt jedoch eigene Probleme mit sich (Welche Maximallänge sollte angesetzt werden ohne falsche Begrenzung zu setzen?)
- noch keine offiziellen Auszüge mit den Böschungen bisher
- ggf. Böschungen raus lösen aus dem Gesamt-ABK-Paket wurde nicht angesprochen

Aktueller Stand der ABK bei den Anwendern
- OBK
 - 41,5% ABK fertiggestellt
 - 4(13) Gemeinden komplett fertiggestellt


### 5) QGIS Plugin PostNAS Suche 

Neuigkeiten?
- keine Neuigkeiten


### 6) Performanzverbesserung 

Erfahrungen mit PostgreSQL 9.6: 
- Rückfrage zu Erfahrungen mit PostgreSQL 9.6
 - nicht getestet oder kein Unterschied festgestellt bzw. gute Erfahrungen
- Parameter  -ds_transaction wurde standardmäßig von norBIT eingebaut, liegen jedoch keine Erfahrungen zur Performanzverbesserung vor
- pgAdmin 4 in der aktuellsten Version (4.2) gut nutzbar, pgAdmin 4.0 nicht gut
 - pgAdmin 3 kann weiterhin eingeschränkt genutzt werden


### 7) QGIS Server mit ALKIS-Infoauskunft 

konfigurierbare FeatureInfo: 
- war gewünscht, derzeit keine OpenSource-Lösung
- JavaScript statt PHP als Basis bei den neuen Auskünften
- lohnt sich mit altem QGIS Server nicht mehr, warten auf die neue Version

### 8) Mapbender als WebGIS-Lösung  

Mapbender RIO: 
- Vorstellung der internen und externen Nutzung von Mapbender3 beim OBK
 - viele thematische und abteilungsbezogene Oberflächen
 - intern mehr Daten verfügbar, z.B. Luftbilder in hoher Auflösung
 - Absicherung von Daten, Funktionen und Anwendungen durch Rechte-Rollen-Konzept von Mapbender
 - Umstieg erfolgt 2017 auf die 3er Version 
- ALKIS: 
 - wöchentliche Updates nach außen
 - Intranet tägliche Updates ohne Historie
 - Auskunft läuft über david
- Eingebundener Dienst "ABK light" unter Basiskarten 
 - Böschungen über separate Berechnung für die Gemeinden (über geograph gelöst)
- Übergangslösung für ABK: 
 - Einbindung einer Fehlermeldung/ Roter Schraffur in Gebieten, bis alle Gemeinden übertragen wurden
- Ausdruck in A4 sind erlaubt
- Besonderes: 
 - Optimierte Feature Info-Dialoge
 - z.B. mit Sprung zu den Haltestellen und Fahrplanauskunft
 - piwik wurde als Monitoring Tool eingebunden und gibt Auskunft über Zugriffe (OpenSource [https://piwik.org/](https://piwik.org/))


### 9) Modellartenerweiterung 

Vorstellung verschiedener Erweiterungen beim OBK

ALKIS Straßen- und Gebäudemarker
- Markierung und Hervorhebung von fehlerhaften Geometrien und Daten
 - Fehler etc. fallen schnell durch Sichtkontrolle auf
 - z.b. Farbliche Hervorhebung von doppelten Hausnummern, Doppelbelegung Straßenschlüssel (Sonderung)
- bei Interesse an Vorlagen bitte beim OBK melden

ALKIS Info Nutzung
- alle Nutzungarten in einer Tabelle komprimiert
 - Einbindung FeatureInfo-Abfrage mit Angaben zur Nutzung
- bei Interesse an Vorlagen bitte beim OBK melden

Info Gebäude
- Ziel: Informationen, wie Geschosszahlen, ansprechend visualisieren
 - Einbindung FeatureInfo-Abfrage mit Angaben zum Gebäude
- Daten werden nicht immer mitgeliefert
- Besonderheit: 
 - grafische Gebäude seperat eingebunden 
- bei Interesse an Vorlagen bitte beim OBK melden

Weitere Erweiterungen
- ALKIS Themenkarte (Flächendifferenzen)
- Böschungen (vorläufige Lösung beim OBK)
- Bodenschätzung (Nutzung beim OBK) 
- bei Interesse an Vorlagen bitte beim OBK melden

### 10) Verschiedenes und Termine 

Termin für nächstes Anwendertreffen: 
- FOSSGIS 2018 von 21. - 23.März in Bonn
 - TODO WG: genauere Planung folgt noch
 - Organisation durch WhereGroup 
- danach in Bremen Richtung Oktober 




 

