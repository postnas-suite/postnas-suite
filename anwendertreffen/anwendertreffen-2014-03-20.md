## PostNAS-Suite Anwendertreffen am 20.03.2014 FOSSGIS in Berlin


- Moderation: Astrid Emde
- Teilnehmer +-30 Personen
- FOSSGIS 2014 Programm: http://www.fossgis.de/konferenz/2014/programm/track/Anwendertreffen/758.de.html

Am 20.03.2014 fand im Rahmen der FOSSGIS 2014 das PostNAS Anwendertreffen statt. Nach dem Vortragsprogramm trafen sich etwa 50 Anwender und Interessierte, um sich über Ihre Erfahrungen auszutauschen.

Bis auf eine Ausnahme, bei der ALKIS-Daten nach ORACLE importiert werden, setzen alle Anwender PostNAS für den Import der Daten nach PostgreSQL ein. Der Import erfolgt zuverlässig, so dass viele Anwender nun an der Aufbereitung und Weiterverarbeitung der arbeiten. Der Erstimport von Daten ist erfolgreich, ebenso der Import von Fortführungsdaten, sofern keine Historie berücksichtigt wird.

Probleme wurden beim Import von großen Daten nach ORACLE festgestellt. Hierbei kann es vorkommen, dass Daten nicht importiert werden, was aber voraussichtlich auf den OCI-Treiber zurückzuführen ist und nicht auf ogr2ogr. 

Der Erstimport von Daten ist erfolgreich, ebenso der Import von Fortführungsdaten, sofern keine Historie berücksichtigt wird.


### Vorstellung der Erweiterungen der Firma NorBIT 
Die Firma NorBIT stellte auf dem Treffen ihre aktuellen Entwicklungen vor. So wurde ein Plugin für QGIS entwickelt, über das ALKIS Daten auf Basis von PostgreSQL einfach geladen und in Anlehnung an die konforme Ausgestaltung dargestellt werden können. Außerdem wurde ein OGC WMS auf Basis des UMN MapServers erstellt, der ALKIS Symbole als SVG Dateien verwendet und sich näher an der amtlichen Darstellung bewegt, als der bisher im Projekt vorliegende WMS. Außerdem stellt der NorBIT WMS nur die Themen dar, die tatsächlich in den Daten vorliegen.

NoBIT möchte diese Lösungen nach der Refinanzierung der Entwicklungen Open Source stellen und sucht noch Investoren. 

- Präsentation siehe http://www.fossgis.de/w/images/6/69/Intergeo_2013_ALKIS_norBIT_GmbH.pdf


### kvwmap als APK light 
Dr. Peter Korduan stellte eine zukünftige Entwicklung auf Basis des WebGIS-Clients kvwmap vor. So soll kvwmap zukünftig als APK light (Auskunfts- und Präsentationskomponente) genutzt werden können. Peter Korduan wird Neuerungen über die PostNAS Mailingliste verkünden.


### Mapbender3 und PostNAS
Astrid Emde stellte die Integration der PostNAS Informationsausgabe und Suche in Mapbender3 vor. Die von Frank Jäger aufgebaute Informationsausgabe zu Flurstücken kann leicht in Mapbender3 integriert werden. Die Suche kann über die Mapbender3 Komponenten SearchRouter (SQL Suchmodul) oder SimpleSearch (Solr Suche) realisiert werden. 

Beim Anwendertreffen wurde die Suche anhand der Anwendung des Kreises Ostprignitz Ruppin vorgeführt. In dieser Anwendung kommt eine Solr Suche zum Einsatz, die sich durch ihre Schnelligkeit und flexible Suchmöglichkeit auszeichnet. 

Informationen zur Umsetzung mit Mapbender3 finden sich im PostNAs Wiki unter:

![Mapbender3](../postnas-suite-mapbender.md)

### Sammlung von ALKIS Demodaten
Es kam der Wunsch auf, eine Übersicht der ALKIS Demodaten der Bundesländer zu erstellen. Andreas Borgardt war so freundlich, nach Demodaten zu recherchieren, so dass die Sammlung bereits im PostNAS-Wiki vorliegt. Sofern jemand über weitere Demodaten verfügt, die verlinkt werden könnten, können diese gerne in der Liste ergänzt werden. Eine Mail an die Mailingliste reicht aus.

http://trac.wheregroup.com/PostNAS/wiki/ALKISTestdaten


### PostNAS Community

Auch im nächsten Jahr soll es auf der FOSSGIS 2015 in Münster (demnächst unter http://fossgis.de/konferenz/2015/) ein PostNAS Anwendertreffen geben. Reservieren Sie sich den Termin schon im Kalender!

Wenn Sie nehr über PostNAS erfahren möchten oder sich zum Thema austauschen möchten, können Sie sich gerne in die Mailingliste eintragen. 

http://lists.osgeo.org/mailman/listinfo/nas



