## PostNAS Suite - Übersicht über die Komponenten

Die PostNAS Suite besteht aus verschiedenen Komponenten. Die folgende Tabelle soll eine Übersicht bieten.


### PostNAS Suite - ALKIS Konverter

| Komponente		| Aufgabe					| Referenz							| Beteiligte				|
|---------------|-----------------|-----------------------|-------------------|
| [norGIS ALKIS-Import](http://www.norbit.de/68/)	| Konvertierung der ALKIS-Daten aus dem NBA-Verfahren mit Bedienoberfläche oder Shellskript für ogr2ogr mit norBIT-Datenbankschema in PostGIS-Datenbanken	| [https://github.com/norBIT/alkisimport/](https://github.com/norBIT/alkisimport/) 						| Jürgen Fischer norBIT [http://www.norbit.dev](http://www.norbit.de) 			| 
| postNAS ALKIS-Import		| Konvertierung der ALKIS-Daten aus dem NBA-Verfahren per Shellscript für ogr2ogr mit postNAS-Datenbankschema für PostGIS-Datenbanken.	| TBD					| Astrid Emde WhereGroup [https://wheregroup.com](https://wheregroup.com)	, ehemals Frank Jäger | 
| GDAL/OGR-Bibliothek		| Import der ALKIS-Daten über die in ogr2ogr integrierte NAS-Schnittstelle in verschiedene Formate		| [https://gdal.org](https://gdal.org) ,  NAS Treiber 	[https://gdal.org/drivers/vector/nas.html](https://gdal.org/drivers/vector/nas.html)	| Entwicklungen NAS-Schnittstelle Jürgen Fischer, Erstimplementation durch Frank Warmerdam		|
| xmi2db		| Werkzeug zur Erzeugung von SQL-Schema und GFS-Datei aus den offiziellen XMI-Schemata			| [http://github.com/pkorduan/xmi2db](http://github.com/pkorduan/xmi2db)						| Peter Korduan GDI-Service Rostock [http://gdi-service.de/](http://gdi-service.de/) 		|
| Vollständiges SQL-Schema		| generiertes SQL-Schema für den Import mit ogr2ogr mit vollständiger Informationen über die Feature-Strukturen im ALKIS-Datenmodell                	| [https://raw.githubusercontent.com/norBIT/alkisimport/master/alkis-schema.sql](https://raw.githubusercontent.com/norBIT/alkisimport/master/alkis-schema.sql)				| generiert mit [https://github.com/norBIT/xmi2db](https://github.com/norBIT/xmi2db)		|
| Vollständige GFS-Vorlage		| generiertes GFS-Datei für den Import mit ogr2ogr mit vollständiger Informationen über die Feature-Strukturen im ALKIS-Datenmodell	| [https://raw.githubusercontent.com/norBIT/alkisimport/master/alkis-schema.gfs](https://raw.githubusercontent.com/norBIT/alkisimport/master/alkis-schema.gfs)			| generiert mit [https://github.com/norBIT/xmi2db](https://github.com/norBIT/xmi2db)		|
| PostgreSQL		| Datenbankserver als Datenhaltungskomponente für die konvertierten ALKIS-Daten			| [http://www.postgresql.org/](http://www.postgresql.org/)							| PostgreSQL Global Development Group			|
| PostGIS		| Datenbankerweiterung für PostgreSQL zur Speicherung räumlicher Daten			| [http://postgis.net/](http://postgis.net/)							| PostGIS Project Steering Committee			| 


### PostNAS Suite - ALKIS WebGIS

| Komponente	| Aufgabe			| Referenz			| Beteiligte	|
|---------------|-----------------|-----------------------|-------------------|
| Mapbender	| WebGIS zur Darstellung Client mit Benutzerverwaltung		|  [https://rio.obk.de/mapbender3/app.php/application/RIO_PostNAS_Demo](https://rio.obk.de/mapbender3/app.php/application/RIO_PostNAS_Demo) , [https://mapbender.org](https://mapbender.org)	| Mapbender-Projekt, WhereGroup	|  
| MapServer	| MapServer zur kartografischen Darstellung des ALKIS-Mapfiles in Mapbender	| RIO-PostNAS Demo des Oberbergischen Kreises [https://rio.obk.de/mapbender3/app.php/application/RIO_PostNAS_Demo](https://rio.obk.de/mapbender3/app.php/application/RIO_PostNAS_Demo) 	| [https://mapserver.org/](https://mapserver.org/)	|
| PostNAS-ALKIS-Mapfile	| Mapfile für Mapserver			| source:trunk/umn/atkis [[http://map.krz.de/?Themen:ALKIS|Demo der KRZ Lemgo Mapbender2]]	| Frank Jäger, Astrid Emde	|
| PostNAS-Navigation	| Suche nach Straßen, Namen, Flurstücken und Grundbüchern in Mapbender-WebGIS	|TBD	| Astrid Emde WherGroup, ehemals Frank Jäger	| 
| PostNAS-Infoabfrage	| Templates für das FeatureInfo-Werkzeug. Anzeige von Flur- und Eigentümerdaten	| [https://github.com/postnas-suite/postnas-suite-php-info](https://github.com/postnas-suite/postnas-suite-php-info)			| Connor Härtl, Astrid Emde, ehemals Frank Jäger	| 
| PostNAS-ATKIS-Mapfile	| Mapfile für Mapserver zur ATKIS Darstellung		| TBD , ATKIS Darstellung Geoportal RLP http://www.geoportal.rlp.de/portal/karten.html 	| Armin Retterath	|
| QGIS-Server	| FCGI-Mapserver zur Visualisierung von QGIS-Projekten als WMS/WFS und WCS	| https://docs.qgis.org/3.34/en/docs/server_manual/	|	|
| QGIS-WebClient | WebGIS-Client für QGIS-Server | http://www.qgis.org/de/site/about/features.html#qgis-web-client https://github.com/qgis/QGIS-Web-Client	|	|


### PostNAS Suite - ALKIS Desktop

| Komponente	| Aufgabe						| Referenz		| Beteiligte	|
|---------------|-----------------|-----------------------|-------------------|
| QGIS	| Desktop GIS für Linux, Windows und Macintosh					| http://www.qgis.org/de/site/		| OSGeo, QGIS-Entwicklerteam	|
| norGIS ALKIS-Erweiterung	| QGIS-Erweiterung zur ALKIS-Dateneinbindung, Signaturierung nach !GeoInfoDok, Suchfunktion zu Eigentümer, Flurstücknummer, Adresse und zur Erzeugung eines Mapserver6/7-Mapfiles	| http://www.norbit.de/75/		| Jürgen Fischer	|
| PostNAS-Suche	| QGIS-Erweiterung zur Flurstücksuche					| https://github.com/Kreis-Unna/PostNAS_Search	| Marvin Kinberger |
