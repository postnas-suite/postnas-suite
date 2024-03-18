## PostNAS-Suite Anwendertreffen am 15.3.2023 Berlin Adlershof 


- Termin: Mittwoch 15.3.2023 FOSSGIS 2023 Berlin Adlershof
- Ankündigung: https://pretalx.com/fossgis2023/talk/LZQ7HA/
- Einladungsmail:
- Teilnehmer/-Innen: +- 30 Personen


### Protokoll 

Protokoll: Anna-Lena Grimm, Astrid Emde

 
Der Raum auf der FOSSGIS 2023 war gut gefüllt. Es stand eine Stunde für den Austausch zur Verfügung.

Folgende Fragen wurden diskutiert und Wünsche/Probleme geäußert.


### Ist es mal wieder Zeit für ein Anwendertreffen? 
Ja, da letztes Treffen außerhalb der FOSSGIS war 2019. Das nächste Treffen sollte ganztägig mit festgelegten TOPs sein. Am Besten wäre ein Termin nach den Sommerferien oder im Herbst. Der Ort ist vakant.
Können evtl. Fördermittel über FOSSGIS e.V. beantragt werden? Dies ist zu klären. Anfrage erfolgt muss erfolgen, sobald ein Termin feststeht.
Der Termin sollte dann über die Mailingliste und andere Kanäle beworben werden.


### GeoInfoDok 7
Der nächster Meilenstein ist die Umstellung auf GeoInfoDok 7. Diese soll Umstellung voraussichtlich zum Ende 2023 erfolgen. Von den Anwensenden wurde gemeldet, dass bisher (Stand März 2023) noch keine Testdaten zur Verfügung stehen.


**Wer nutzt PostNAS-Suite?**

Im Raum nutzen nahezu alle Anwesenden den Konverter. Nutzer, die den Konverter erst neu entdeckt hatten berichteten von ihren überaus guten Erfahrungen und lobten die PostNAS-Suite.                

Stimmen der Anwender*innen:
- LV RLP: nutzt PostNAS-Suite und hat konvertierte Testdaten getestet.
- LV TH: hat Testobjekte für eine Gemarkung künstlich auf Basis von GeoInfoDok 7 hergestellt.
- LGL BW: Will bis Ende des Jahres auf GeoInfoDok 7 umstellen. Testdaten mit Version 7.1.1 sind vorhanden.
- Regionalverband Ruhr: nutzen PostNAS-Suite und arbeiten mit anderen Kreisen in einem Geonetzwerk zusammen.
- Recklinghausen: stellen auf PostNAS-Suite um. Testdaten zu GeoInfoDok 7 gibt es noch nicht, da Validierung noch erfolgen muss.
- LV HE: Haben erfolgreich auf Postgres 13 und PostGIS 3 umgestellt.


**Was muss im Zuge von GeoInfoDok 7 noch angepasst werden?**

Jürgen Fischer der Entwickler von norGIS-ALKIS-Import (https://www.norbit.de/68/) und Betreuer der OGR-Unterstützung für NAS berichtet, dass der Code für die GeoInfoDok7 bereits vorliegt (siehe Branch gid7 https://github.com/norBIT/alkisimport/tree/gid7).

Neuer Konverter für GeoInfoDok 7 inkl. Signaturenkatalog wird erstellt. „Alter Konverter“ (für GID6) soll aber weiterhin vorhanden bleiben. OSGeo4G bietet dann zwei Versionen des Konverter an.

Aus Mangel an Testdaten konnte diese Entwicklung allerdings noch nicht eingehend geprüft werden.
Derzeit werden Daten von GID6 nach GID7 konvertiert, um testen zu können. Hierbei liegen allerdings für die neuen Objektklassen noch keine Daten vor.

Für den maschinenlesbaren Signaturenkatalog muss noch ein Parser erstellt werden.

QGIS-Plugin zur Darstellung muss auf GID7 umgestellt werden bzw. beide Versionen unterstützen.


### Wünsche & Probleme

- Die Ausgabe des Datum zur Aktualität der ALKIS-Daten soll am besten mit ausgegeben werden, da je nach Bundesland OpenData anders gelebt wird. Es wäre sinnvoll diese Information in der Postgres-Datenbank zu hinterlegen.
- ATKIS & AFIS sollte aufgenommen werden (auch als mapfile)

Probleme
- ALKIS Mapfile kann nicht mehr gedruckt werden. Letzter Eintrag zum Mapfile von Frank Jäger aus 2021.


Umzug von trac nach github
- Daten, Doku, Projekte nach Github übertragen
- alter Server soll entfallen
- Todo für Astrid Emde

Problem: QGIS-Projekt: Layernamen sind nicht OGC-konform
- Frage: Kann dies im Konverter direkt umgesetzt werden?
- Ist wahrscheinlich nicht trivial.

PostNAS-Förderung
- wäre eine Förderung des QGIS-Plugin durch den QGIS.DE-Verein möglich?
