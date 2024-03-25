## PostNAS-Suite Anwendertreffen am Freitag 15.12.2023 Online


- Termin: Freitag 15.12.2023 Online
- Einladungsmail: [https://lists.osgeo.org/pipermail/nas/2023-December/001339.html](https://lists.osgeo.org/pipermail/nas/2023-December/001339.html)
- Teilnehmer/-Innen: 20 Personen Online



### Themen

- Austausch zum Thema Umstellung von GID6 auf GID7 und PHP-Auskunftskripte
- Aufbau neues Github Projektes
- Historisierung
- Anwendertreffen


### Protokoll 

#### Austausch zum Thema Umstellung von GID6 auf GID7

Über die PostNAS-Liste gab es bislang sporadischen Austausch zum Thema Umstellung von GID6 auf GID7. Zum Anwendertreffen wurde eingeladen, um einmal gebündelt die bisherigen Erfahrungen und den Wissensstand auszutauschen:
- Funktioniert der Import mit dem norGIS-Importer?
- Haben alle Nutzer der ALKIS-Auskunftsskripte dieselben Fehlermeldungen?

Der Import der ALKIS- Daten (mindestens die Testdaten aus verschiedenen Bundesländern) funktioniert weitgehend fehlerfrei, jedenfalls wurden hier keine Probleme gemeldet.
Testdaten gibt es u.a. hier [http://trac.wheregroup.com/PostNAS/wiki/ALKISTestdaten](http://trac.wheregroup.com/PostNAS/wiki/ALKISTestdaten), [https://postnas-suite.github.io/postnas-suite/testdaten.html](https://postnas-suite.github.io/postnas-suite/testdaten.html)

**Stadt Münster – Uwe Kock**
- Die Stadt befindet sich gerade noch in der Umstellung von GID6 auf GID7
- Die Auskunftsskripte sind soweit ok bis auf einige SQL-Fehler (s.u.).

**ITEBO GmbH – Martina Weyand**
- Import war soweit auch erfolgreich, dieselben SQL-Fehler bei der Auskunft

**OBK – Marina Kühne**
- Beim OBK läuft gerade die Umstellung auf GID7, Erfahrungen mit Testdaten waren erfolgreich. In den nächsten Tagen bekommt das Team die ersten offiziellen Daten für PostNAS.
- Der OBK nutzt die Auskunft zwar nicht, Marina Kühn gibt aber eine Rückmeldung, wenn die ersten Echtdaten importiert wurden. Gegebenenfalls kann sie etwas zu den SQL-Fehlern sagen.

**Stadt Recklinghausen – Marvin Kinberger**
-Auch hier läuft gerade die Umstellung.


##### Wer nutzt die Auskunftsskripte produktiv?
- Stadt Minden (Thomas Schüttenberg)
- ITEBO GmbH (Martina Weyand)
- Stadt Münster (Uwe Kock)
- WhereGroup (Astrid Emde)

SQL-Fehler treten in den Auskunftsskripten auf bei den Themen:
- Nutzungsarten
- Bodenschätzung

- Die Tabelle alkis-elemente fehlt, ebenso ax_kulturart_bodenschaetzung
- Fehler gibt es auch zu den Angaben Gebäude: 'FEHLER: Spalte g.objekthoehe existiert nicht'

Ansonsten funktionieren die meisten Auskunftsskripte, z.B. bzgl. Eigentümer, Grundbuch etc.

**Aufgabe: Es muss ein Abgleich der Daten nach GID6 zu GID7 geben.**

Dazu Casten Rensch:
„Es gibt auf der ADV-Online-Homepage eine Datei mit dem Namen "AAA-7.1.2.qea" zum Download, die man mit dem Programm "Enterprise Architect" der Firma "Sparx Systems" öffnen kann. Das hat zumindest uns sehr weitergeholfen im neuen 7.1-Datenmodell zurechtzufinden.“
Link: [https://www.adv-online.de/icc/extdeu/broker.jsp?uMen=a0070978-8c4f-4941-e0d8-2db572e13d63](https://www.adv-online.de/icc/extdeu/broker.jsp?uMen=a0070978-8c4f-4941-e0d8-2db572e13d63)

Auch auf der Seite des LGLN gibt es eine Excel-Datei zum Download, die eine Änderungsübersicht enthält.
Link: [https://www.lgln.niedersachsen.de/startseite/geodaten_karten/afis_alkis_atkis/aaa_datenmodell/umstellung-auf-das-aaa-anwendungsschema-7-1-2-220070.html](https://www.lgln.niedersachsen.de/startseite/geodaten_karten/afis_alkis_atkis/aaa_datenmodell/umstellung-auf-das-aaa-anwendungsschema-7-1-2-220070.html)

ITEBO (Martin Weyand, Connor Härtel) schaut sich die Datei nochmal an. Über die Liste kann ein fachlicher Austausch stattfinden (u.a. Uwe Kock). Alle Infos sind willkommen.
ITEBO wird dann versuchen, die Auskunftsskripte anzupassen.

#### Aufbau neues Github Projektes
Astrid Emde: Aufbau neues Git Projekt und Austausch über die Liste


#### Historisierung
Bei dem Treffen waren auch Interessierte anwesend, die noch keine Erfahrung mit dem Import von ALKIS-Daten hatten. Es wurde gefragt, was beim Import von Daten von Schleswig-Holstein zu beachten ist.
GID7 startet mit einem Erstimport des Grunddatensatzes, Stand 01.01.2022, Historie aus GID6 geht damit verloren.
Daniel Cebulla (KITT Jena) hatte Kontakt mit Jürgen Fischer. Dieser sieht hier nicht die Rolle des Konverters.


#### Anwendertreffen

Das nächste Anwendertreffen findet auf der FOSSGIS 21.03.2024 in Hamburg statt.

[https://postnas-suite.github.io/postnas-suite/postnas-suite-anwendertreffen.html](https://postnas-suite.github.io/postnas-suite/postnas-suite-anwendertreffen.html)

