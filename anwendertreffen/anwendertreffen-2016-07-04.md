## PostNAS-Suite Anwendertreffen am 04.07.2016 auf der FOSSGIS in Salzburg


- Termin: 4.07.2016 18:30 Uhr FOSSGIS Konferenz Salzburg
- [https://fossgis-konferenz.de/2016/programm/Programm_FOSSGIS-2016.pdf](https://fossgis-konferenz.de/2016/programm/Programm_FOSSGIS-2016.pdf)
- Einladungsmail: [https://lists.osgeo.org/pipermail/nas/2016-May/000847.html](https://lists.osgeo.org/pipermail/nas/2016-May/000847.html)
- +-20 TeilnehmerInnen

Seit einigen Jahren führen wir ein Anwendertreffen auf der FOSSGIS Konferenz durch. Dieses Treffen fand auch 2016 auf der FOSSGIS in Salzburg statt. 

Die FOSSGIS wurde 2016 gemeinsam mit der AGIT veranstaltet.
 - [http://www.fossgis-konferenz.de/2016/](http://www.fossgis-konferenz.de/2016/)
 - [http://www.agit.at/](http://www.agit.at/)

Auf der FOSSGIS gab es außerdem einen Vortrag über die PostNAS-Suite:

***Vortrag: PostNAS-Suite - Lösungen für den ALKIS Datenimport, die Darstellung, Informationsausgabe und Suche***
 - Mittwoch 6.7.2016 11:30 Uhr
 - Astrid Emde und Jelto Buurman
 - [Videoaufzeichnung](https://www.youtube.com/watch?v=hQGiUbHmCwA)
 - [Videos](https://www.fossgis-konferenz.de/2016/videos/)
 


### Themen 
- Peter Korduan: Bericht zum Aufbau eines vollständiges Datenmodell für den PostNAS Konverter auf der Basis des Implementierungsschemas des AAA Modells
- QGIS Plugin ALKIs Suche (Marvin Brandt, Kreis Unna)
- Performanceverbesserung bei Postprocessing - es werden Sponsoren gesucht


###  Aufbau eines vollständiges Datenmodell für PostNAS 
- Peter Korduan
- [Folien](https://trac.wheregroup.com/PostNAS/export/371/trunk/anwendertreffen/Korduan_Projektstand_PostNAS-Erweiterung_2016-07-04.pdf)

Auf dem Anwendertreffen hat Peter Korduan, Geschäftsführer der Firma GDI-Service Rostock das Vorhaben zur Erweiterung des OGR Datenmodells vorgestellt.

Zunächst wurde die Problemstellung mit dem unvollständigen OGR-Modell sowie den doppelt vorkommenden und abgeschnittenen Attributnamen dargelegt. Die daraus resultierende Aufgabenstellung wurde vom Landkreis Vorpommern-Rügen, dem Landesamt für Vermessung und Geobasisinformation Rheinland-Pfalz und dem Landeamt für Vermessung, Geoinformation und Landentwicklung des Saarlandes beauftragt. Sie umfasst folgende Punkte:

- 1. Umwandlung des AAA-UML-Modells in das AAA-Implementierungsschemas mit ShapeChange
- 2. Einlesen der aus Enterprise Architekt exportierten xmi-Datei in eine Postgres-Datenbank
- 3. Transformation dieses Meta-Modells in ein Schema, welches die GML-Klassen abbildet
- 4. Ableitung des Datenschemas für OGR durch „flach machen“ des objektorientierten Klassenschemas und Anwendung von generischen Umbenennungsregeln sowie länder-, bzw. anwendungsspezifischer Filterung
- 5. Erstellung eines Scripts zur Umbenennung von verschachtelten GML-Elementen in einzulesenden NAS-Dateien

Zum Zeitpunkt des Treffens war der Punkt 3 praktisch umgesetzt und Punkt 4 konzeptioniert. In der Diskussion wurden Varianten der Umbenennung von Attributen beim „flach machen“ des Objektmodells und die Auswirkungen die Änderungen an dem bestehenden Modell haben können besprochen. Es wurde ein Konsens darüber erzielt, dass zunächst Schritt 4 nach dem Konzept des generischen Ansatzes von GDI-Service umgesetzt wird und das fertige „flache“ und vollständige OGR Modell auf der Web-Site des PostNAS Projektes noch mal zur Diskussion gestellt wird. Des Weiteren wurde vereinbart, dass das Endresultat des Projektes schließlich auf dem nächsten Anwendertreffen in Münster im Dezember präsentiert wird.


----


### QGIS Plugin PostNAS-Suche  
- Marvin Brandt
- Neuigkeiten zu der QGIS-Erweiterung
- [QGIS Plugin PostNAS Suchfunktionen](https://plugins.qgis.org/plugins/PostNAS_Search/)
- eine Vorstellung des Suchmoduls mit Screenshots erfolgt in dem Vortrag PostNAS-Suite (Folien und Video siehe oben)

#### Folgende Funktionen bietet unsere Erweiterung mittlerweile: 

***Flurstücksuche***

Hierzu gehören aktuelle sowie historische Flurstücke. Bei den historischen muss man unterscheiden zwischen historischen ohne nachvollziehbarer Geometrie und historischen Flurstücken mit Geometrie. Seit der Einführung von ALKIS wird die historische Geometrie in den Daten geführt. Vorher wurden nur Sachinformationen über die Nachfolger eines Flurstückes geführt und somit kann nur die etwaige Position ermittelt werden. Hier wird nur eine BBOX als Suchergebnis angezeigt.

***Adresssuche***
- Alle Hausnummern sind über die Suche auffindbar


***Eigentümersuche***

Alle Flurstücke eines Eigentümers können visualisiert werden. Besonders hilfreich bei Abfragen wie z.B. welche Grundstücke gehören dem Landwirt Müller.

- deutliche Performancesteigerung durch vorprozessierte Volltextsuche
		
Diese kann über das Menü Datenbank -> PostNAS-Suche -> Volltextindex erstellen angestoßen werden. Die Suche ist jedoch auch ohne diese Indextabelle möglich. Dann ist diese jedoch bei größeren Datenbeständen sehr langsam.

*** Zugriffssteuerung anhand des Benutzernamens***

Eine Zugriffssteuerung über den angemeldeten Benutzernamen (Windows-Benutzer) wurde implementiert. Gerade bei größeren Institutionen ist dies hilfreich, um ein Zugriff auf die Eigentümerdaten einzuschränken.

Marvin Brandt und der Kreis Unna haben folgende Punkte noch für die nächsten Wochen für die Fertigstellung geplant:
- 1. 	Protokollierung der Zugriffe auf die Eigentümerdaten
- 2.	Unterscheidung der Darstellung für Normaleigentum und Erbbaurecht sowie anteilige Flurstücke (genaue Umsetzung noch nicht geplant)
- 3.	Informationen zu Eigentumsart und Eigentumsanteil in den Objektinformationen der Suchergebnisse („i-Button" auf den Layer Suchergebnisse)


----
### Performanz Postprozessing  
- Dieses Thema wurde kurz angesprochen. Das Postprozessing nach dem Einspielen von NBa Dateien kann sehr lange dauern. Daher wird noch finanzielle Unterstützung gesucht, um das Thema anzugehen.


----
### Umsetzung der Amtlichen Basiskarte   
- Aufgabe besteht scheinbar nur in NRW. Für die Anwesenden aus anderen Bundesländern war dieses Thema nicht bekannt bzw. steht nicht auf der Agenda.



