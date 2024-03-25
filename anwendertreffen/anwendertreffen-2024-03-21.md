## PostNAS-Suite Anwendertreffen am Donnerstag 21.3.2024 FOSSGIS 2024 Hamburg


- Termin: Donnerstag 21.3.2024 FOSSGIS 2024 Hamburg
- Ankündigung: [https://pretalx.com/fossgis2024/talk/TSJM9V/](https://pretalx.com/fossgis2024/talk/TSJM9V/)
- Einladungsmail: [https://lists.osgeo.org/pipermail/nas/2024-January/001357.html](https://lists.osgeo.org/pipermail/nas/2024-January/001357.html)
- Teilnehmer/-Innen: 13 Personen vor Ort auf der FOSSGIS, 12 Teilnehmende Online



### Themen

- Darstellung und Information zu historischen Daten
- Erstausstattung
- PHP-Auskunftskripte - Möglichkeit der Bereitstellung der Informationen in QGIS
- PHP-Auskunftskripte - korrekte Ausgabe von Informationen zu allen Eigentümervarianten
- Webseite
- SQLs
- Anwendertreffen


### Protokoll 

Nach einer kleinen Vorstellungsrunde der Personen vor Ort, diskutierten wir die gesammelten Themen.


#### Darstellung und Information zu historischen Daten
Es wurde der Wunsch geäußert auch historische Daten darzustellen und Informationen abfragbar zu machen. Hier stand die Anzeige in QGIS im Vordergrund. Denkbar wäre ein Zeitschieber, über den der gewünschte Zeitpunkt ausgewählt werden könnte. Bei der Umsetzung wäre die konforme Darstellung nicht relevant.

Es wurde diskutiert inwieweit die Umsetzung in das bestehende QGIS ALKIS Plugin einfließen könnte. Jürgen Fischer zeigte sich offen für das Einfließen in das bestehende QGIS ALKIS Plugin. Die Informationen könnten aus den Gebäuden und Flurstücken über die Angaben unter beginnt und endet entnommen werden.

Der anwesende Vertreter der Stadt Jena steht mit Jürgen Fischer bereits in Kontakt und wird an einer Lösung arbeiten.

Es wurde ein Ticket für diese Aufgabe erstellt:


#### Erstausstattung
Bei dem Treffen waren auch Interessierte anwesend, die noch keine Erfahrung mit dem Import von ALKIS-Daten hatten. Es wurde gefragt, was beim Import von Daten von Schleswig-Holstein zu beachten ist.

Hier ein paar Tipps für den Import
- Es sollten langfristig Fortführungsdaten genutzt werden. Nach dem Erstimport können dann die Änderungsdatensätze importiert werden
- Der Import sollte via sh-Skript erfolgen, nicht über die graphische Oberfläche. Das sh-Skript unterstützt parallele Prozesse.
- Es sollte ausreichend Speicherplatz bereitgestellt werden.
   - Beispiel: In Rheinland-Pfalz nehmen die gezippten Dateien allein schon 10-11 GB ein. Beim Import werden die Dateien einzeln entpackt und nach dem Import der Datei wieder gelöscht.
   - Die Datenbank für Rheinland-Pfalz ist etwa 180 GB groß.
- Der Import kann einige Stunden benötigen. Die Nachprozessierung nimmt ebenfalls einige Stunden in Anspruch.

Fragen können gerne an die Mailingliste gestellt werden.


#### PHP-Auskunftskripte - Möglichkeit der Bereitstellung der Informationen in QGIS

Im PostNAS-Suite-Projekt liegen Skripte zur Auskunft vor. Diese sind beschrieben und die PHP-Skripte stehen zum Download bereit. Die Skripte wurden bereits für GID7 angepasst.

- [https://postnas-suite.github.io/postnas-suite/postnas-suite-buchauskunft.html](https://postnas-suite.github.io/postnas-suite/postnas-suite-buchauskunft.html)

Es wurde der Wunsch geäußert, bestimmte Informationen, die die PHP-Skriipte ausgeben auch in QGIS bereitzustellen. Die bisherige QGIS-Auskunft bildet manche Fragestellungen derzeit nicht ab.

Jürgen Fischer zeigte sich offen für das Einfließen in das bestehende QGIS ALKIS Plugin. Thomas Schüttenberg wird die Aufgabe übernehmen, die entsprechenden Fragestellungen und SQLs aus den Skripten herauszusuchen.

Es wurde ein Ticket für diese Aufgabe erstellt:



#### PHP-Auskunftskripte - korrekte Ausgabe von Informationen zu allen Eigentümervarianten

Oliver Schmidt sprach an, dass bei ausgefallenen Eigentümervarianten (wie Teileigentum, Erbengemeinschaften), die Auskunft keine korrekten Ergebnisse liefert. Hier sollte nachgebessert werden.

Es wurde ein Ticket für diese Aufgabe erstellt:


#### Webseite

Es gibt eine neue PostNAS-Suite Webseite unter [https://postnas-suite.github.io/postnas-suite/](https://postnas-suite.github.io/postnas-suite/). Die Seite löst die bestehende Seite [http://trac.wheregroup.com/PostNAS](http://trac.wheregroup.com/PostNAS) ab. Inhalte wurden soweit es sinnvoll erschien übernommen.

Die neuen Seiten werden auf GitHUb im Repository [https://github.com/postnas-suite/postnas-suite](https://github.com/postnas-suite/postnas-suite) erstellt. Und stehen dann direkt auf der Webseite bereit.

Alle sind herzlich eingeladen zu der Seite beizutragen. Es wird ein Zugriff über den GitHub-Account benötigt. Der Zugriff kann gerne bei Astrid Emde astrid (dot) emde (at) wheregroup (dot) com angefragt werden.

Es wurde von den Anwesenden nicht als notwendig erachtet, wieder die Domain postnas.org zu aktivieren.


#### SQLs und Mapdateien

Oliver Schmidt sprach an, dass er über einige hilfreiche SQLs (Abstandsberechnungen) und auch Mapdateien (z.B. zu Wasserrecht) verfügt, die auch für andere interessant sein könnten.

Für die SQLs soll ein eigenes Repository erstellt werden. Dies erfolgt in Abstimmung mit Astrid Emde und wird über die Mailingliste kommuniziert.

Die Mapdateien sollen in das bereits vorliegende Repository eingebunden werden.
- [https://github.com/postnas-suite/postnas-suite-mapserver](https://github.com/postnas-suite/postnas-suite-mapserver)


#### Anwendertreffen

Wann soll das nächste Treffen stattfinden? Die Einladung nach Münster steht noch im Raum. Hier wird nachgefragt, ob im Laufe des Jahres ein Treffen stattfinden soll.

[https://postnas-suite.github.io/postnas-suite/postnas-suite-anwendertreffen.html](https://postnas-suite.github.io/postnas-suite/postnas-suite-anwendertreffen.html)


