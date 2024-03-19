## PostNAS-Suite Anwendertreffen am 07.12.2016 10 Uhr Stadthaus Münster


- Termin: 07.12.2016 10 Uhr Stadthaus Münster
- Moderation Norbert Dephoff
- Einladungsmail: [https://lists.osgeo.org/pipermail/nas/2016-October/000935.html](https://lists.osgeo.org/pipermail/nas/2016-October/000935.html) 
- Teilnehmer/-Innen: 20 

### Themen aus letzter Sitzung 

Peter Korduan: 
- Bericht zum Aufbau eines vollständiges Datenmodell für den PostNAS Konverter auf der Basis des Implementierungsschemas des AAA Modells 
- war am 25.5.2016 nicht anwesend, Vortrag auf einem der nächsten Anwendertreffen erwünscht

- Umstellung der ALKIS-Nutzungsdaten auf das norBIT-DBSchema
 - keine weitere Nutzung der ursprünglichen/ klassischen Mapfiles

- Modellarterweiterung
 - Abstimmung mit Peter Korduan auf der FOSSGIS
 - Genauigkeit von Vermessungspunkten (Integration/ Schemaerweiterung durch NorBIT)
 - Bodenschätzung
 - kommunale Objekte
 - adminstrative Einheiten (Gemarkungen, Fluren als Flächenobjekten)

- Skript Flächengenerierung
 - Gemarkungen- und Gemeindegrenzen 
 - bis jetzt keine saubere Flächendeckung/ Löcher
 - wird erst einmal nicht weiterverfolgt

- Darstellungsregeln der ALKIS-Daten
 - Orientierung an SLD von Münster (s.o.)
 - einheitliche Anpassung und Einbindung in QGIS Plugin in Diskusion 

- ABK
 - ABK muss bis 2019 (NRW) realisiert werden
 - Realisierung mit hohem Arbeitsaufwand verbunden
 - Einwand RVR:  Eher David WMS/ IBR WMS nutzen?
  - Problem AutoCAD, da hier keine David-WMS-Einbindung möglich ist
  - David ist maßstabsstufenabhängig und stark spezialisiert auf bestimmte Ansprüche und Zoomstufen
  - Datenüberarbeitung vor ABK Erstellung nötig

- Performanzverbesserung: 
 - RVR: bessere Performanz gewünscht, Termin für einen Test steht noch nicht fest
- Einsatz von QGIS-Server/ QGIS-WMS mit ALKIS-Infoauskunft:
 - Erweiterung von QGIS Server:  wird immer wieder stetig aber langsam verbessert, Performanz nicht optimal, 
 - FeatureInfo: nur HTML-FeatureInfo
 - Interesse wurde genannt im Zusammenhang mit dem Einsatz von norBIT und Kartenpublikation über QGIS Server 


### Themen 


### Erweiterung des PostNAS ALKIS-Schema 

Projekt zur Erweiterung des PostNAS ALKIS-Schemas um alle Elemente des ALKIS Modells (Peter Kordulan)

- aktueller Stand 2016-12-29: [https://gdi-service.de/xmi2db/sql/schema_aaa_ogr_2016-12-29.sql](https://gdi-service.de/xmi2db/sql/schema_aaa_ogr_2016-12-29.sql)
- Skript [https://github.com/pkorduan/xmi2db/blob/master/converter/rename_nas.rb](https://github.com/pkorduan/xmi2db/blob/master/converter/rename_nas.rb)
 - Zum Einlesen in das Modell müssen Tags in den NAS-Dateien vorher umbenannt werden
 - Umbenennungen: [http://gdi-service.de/xmi2db/listings/umbenennungsliste.php](http://gdi-service.de/xmi2db/listings/umbenennungsliste.php) 
- Themen: Änderungen, Filtern und Kompromisse

- Auf dem PostNAS Anwendertreffen auf der FOSSGIS 2016-07-04 stellte Peter Korduan, Geschäftsführer der Firma GDI-Service Rostock, das Vorhaben zur Erweiterung des OGR Datenmodells vor.
 - [Folien](http://trac.wheregroup.com/PostNAS/export/371/trunk/anwendertreffen/Korduan_Projektstand_PostNAS-Erweiterung_2016-07-04.pdf)
 - siehe auch Protokoll vom Anwendertreffen der FOSSGIS in Salzburg ![PostNASAnwendertreffen 2016-07-04](./anwendertreffen-2016-07-04.md)
 -  [[wiki:PostNASAnwendertreffen2016-07-04]]

GeoportalRLP (der Auftraggeber dieser Lösung) äußert den Wunsch, dass dieses Modelle für alle nutzbar wird, nicht nur für die Auftraggeber.

Herr Korduan bemerkte, dass der Quellcode offen ist. Fragen können in einem gewissen Rahmen von Herrn Korduan beantwortet werden.
Dieses Projekt könnte Grundlage sein, für ein weiteres Projekt, um Ergebnisse in den OGR Treiber zu implementieren.
Das jetztige Projekt war dazu da, um zu sehen, welche Daten es gibt, welche Attribute und Spalten/Tabellen umbenannt werden müssen

Herr Buurman schlug vor, das Thema beim nächsten Treffen noch einmal zu diskutieren: Wie kann ein Projekt für die Implementierung angestoßen werden.
Dann könnte auch eine Rückwärtsimplementierung der Attribute, die Umbenennung von Tabellen und der Migrationsweg weiter besprochen werden. 

Herr Korduan schlug vor, dass statt OGR auch ein objektbasiertes Modell diskutiert werden könnte.

Geoportal RLP war wichtig, dass alle Daten des XML nutzbar gemacht werden können. Die Verwendung in PostgreSQL ist entscheidend.


### Harmonisierung Postprocessing, Vereinheitlichung 
- Anpassung der Mapdatei an die norGIS Struktur.

Vorstellung der Karte der Stadt Münster:
-  Beim Erstellen der Karte der Stadt Münster ist aufgefallen, dass die Lage der Symbole nicht korrekt ist (z.B. Ampel).
- Das Problem könnte gelöst werden, indem in der Mapdatei ANCHORPOINT verwendet wird.
Viele Symbole gehören eher in eine Stadtgrundkarte als in die Katasterkarte. Einige Symbole wie Baum, Fahrradständer, Böschungen müssen bearbeitet werden.
- Es wurde angefügt, dass es möglichst eine gemeinsame Lösung geben sollte, sonst funktioniert die PostNAS-Gemeinschaft nicht mehr.

Vorstellung der Karte Kreis Unna:
- Die Legende wurde bearbeitet, es wurden KEYIMAGEs verwendet. 
- Die SVG-Symbole mussten bearbeitet werden, damit die Farben im Ausdruck und auf dem Bildschirm ähnlich aussehen, Farbwerte wurden bearbeitet.
- Die Buchauskunft wurde von Herrn Jäger angepasst. Aufgefallen war, dass sich die Anzeige des Erbbaurechts geändert hat. Herr Jäger schaut sich das nochmal an.


### Skript Flächengenerierung 
Es fiel auf, dass bei der Generierung von Gemarkungs- und Gemeindeflächen 'Löcher' entstehen.
Der Fehler liegt häufig in der ungenauen Fortführung der Daten.
Wenn die Kreise sich nicht absprechen, kann es bei Änderungen an Flurstücken an Kreisgrenzen zu Fehlern kommen.
### Darstellungsregeln der ALKIS-Daten 

- Wunsch nach maßstabsabhängiger Darstellung von Grenzen
 - Die Darstellung der Grenzen von Münster wurde bereits beim Anwendertreffen in Unna im April 2016 vorgestellt.
- **Todo norBIT: Plugin müsste erweitert werden, Herr Fischer signalisiert Bereitschaft**

- Die Erweiterung der KOM OK (Kommunale Symbole) ist in Münster jetzt verfügbar.
 - [http://www.bezreg-koeln.nrw.de/brk_internet/geobasis/liegenschaftskataster/alkis/vorgaben/index.html](http://www.bezreg-koeln.nrw.de/brk_internet/geobasis/liegenschaftskataster/alkis/vorgaben/index.html)
 - Es wurde der Wunsch geäußert, dass Böschungen aus ALKIS dargestellt werden.
- Die Priorisierung der Layer ist bei der Darstellung von ALKIS nicht immer korrekt (z.B. von Verkehrswegen oder Industrieflächen)
 - Herr Fischer:  Objekte haben eine Darstellungspriorität. Durch die Layerstruktur, kann es vorkommen, dass Symbole verdeckt werden, die eigentlich eine höhere Darstellungspriorität hätten.

#### Anmerkungen:
- Stadtplanwerk 2.0 Ruhrgebiet kommt (auf der Basis von ALKIS/ABK- und OSM-Daten)
 - [https://geonetzwerk.metropoleruhr.de/de/aktuelles/stadtplanwerk-2-0](https://geonetzwerk.metropoleruhr.de/de/aktuelles/stadtplanwerk-2-0)
- Open Data 
 - Hamburg: Kostenloser Download von ALKIS-Daten möglich
 - In Rheinland-Pfalz in Bearbeitung
 - NRW ab 1.1.2017  [https://open.nrw/de/dat_kat](https://open.nrw/de/dat_kat)

### Symbole in QGIS/AutoCAD/MAP-File 
- Symbole sollen in AutoCAD halb so klein dargestellt werden wie in QGIS
- Wunsch über QGIS Oberfläche Größe steuern. 
- **Todo: Herr Fischer könnte einen Skalierfaktor hinzufügen.**

### ABK NRW 
- Es wurde der Wunsch geäußert, dass sich mehrere Parteien für eine Auftrag an norBIT zusammenschließen.
 - norBIT: wenn sich 4 Parteien zusammenschließen, könnte es ca. 2.500€ pro Partei kosten. 
- Idee: Über die PostNAS-Liste anfragen, ob weitere Parteien Interesse haben.

### QGIS Plugin PostNAS Suche 
- siehe Protokoll von PostNAS Anwendertreffen in Salzburg
 - [wiki:PostNASAnwendertreffen2016-07-04]

### Performanzverbesserung 

- Aufgefallen ist, dass das Einspielen von Daten länger dauert als vor einem Jahr bei ähnlicher Datenmenge (z.B. Hausnummern)
- Herr Fischer benötigt eine Ko*nkretisierung, an welcher Stelle es länger dauert (im Postprocessing)
- Bremer Erfahrung: OGR ist langsamer geworden
- schnellere Umsetzung und paralleler Import, insbesondere Interesse beim Land RLP und Kommunaler Dienstleister, die große Daten importieren müssen.
- Vorschlag Frau Emde: Zum Testen der Geschwindigkeit, Auslastung in Postgresql 9.6 pg_sta_statement-Extention verwenden! Es kann z.B. eingesehen werden, welche SQLs wielange benötigen
 - [https://www.postgresql.org/docs/9.6/static/pgstatstatements.html](https://www.postgresql.org/docs/9.6/static/pgstatstatements.html)

### Thema Kreisbögen 
-  GDAL 2.x unterstützt Kreisbögen. Der Konverter kann sie auslesen. PostgreSQL hat damit Probleme, diese korrekt umzusetzen.

### QGIS Server mit ALKIS-Infoauskunft 

- QGIS Server Feature Info: noch nicht umgesetzt.
- Gut wären templates wie beim MapServer. Ist im QGIS Server bisher nicht möglich.
- Mit Redirekt auf vorhandene Templates zugreifen, ist möglich.
- Mittelfristige Lösung mit Templates wünschenswert.


### Mapbender3 
- Vorgestellt wurde ein ALKIS Demo Projekt im Mapbender3
 - Karte mit Legende
 - Buchauskunft über php-Skripte
 - Suche über den Search Router möglich
- [wiki:PostNASMapbender3]


### Modellartenerweiterung 
- Wunsch nach Genauigkeit von Vermessungspunkten (Integration, Schemaerweiterung durch norBIT)
- Vorschlag OBK: Sie könnten ihr Schema für Vermessungspunkte Herrn Fischer zur Verfügung stellen.
- **Todo: Spalten müssten in das Datenmodell eingefügt werden.**


### Verschiedenes 

- FOSSGIS:  Mi. 22.- Fr. 25. März 2017 in Passau
- Anwendertreffen soll nicht stattfinden
- Vortrag? 
 - Herr Buurmann und Frau Emde
 - RLP: ggf.?

- Vorschlag: Präsentation von PostNAS auf der Integeo in Berlin

- Termin und Ort für das nächste Anwendertreffen:
 - in Münster nach Ostern 2017




