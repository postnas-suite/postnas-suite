## PostNAS-Suite Anwendertreffen am 21.03.2012 FOSSGIS Dessau


 - Moderation Olaf Knopp, Astrid Emde
 - Teilnehmer 21 Personen
 - http://postnas.org


Die KRZ-Demo wurde vorgestellt und der Status von PostNAS wurde erläutert. In letzter Zeit erfolgte der Feinschliff an der Navigation- und Auskunft. Es wurden diverse Bugs in GDAL/OGR gefixt und das Datenbankschema wurde verfeinert. Das NBA Verfahren kann nun angewandt werden.

Die Tickets finden Sie unter: https://trac.wheregroup.com/PostNAS/report/6

Schauen Sie sich die Demo einmal an: http://map.krz.de/mapwww/?Themen:ALKIS

Armin Retterath und Tobias Dick (Universität Trier) hielten auf der FOSSGIS den Vortrag "NAS - BasisDLM Aufbereitung mit gdal/PostNAS"
http://www.fossgis.de/konferenz/2012/programm/events/386.de.html



### Welchen Anforderungen haben wir an PostNAS? 

 - Feedback zeichnerischer konformer Anspruch ist nicht da und geht zu weit. Ist möglicherweise mit MapServer auch nicht umsetzbar. Aus den Daten müssten weitere Zeichnungsobjekte generiert werden (Böschungen usw.)
 - Sekundärdatenbestand
 - amtliche Auskunft erfolgt über andere Systeme
 - Informationsausgabe zu den Flurstücken soll ansprechend und übersichtlich sein und liegt mit der AUskunft von Frank Jäger in derartiger Form  vor
 - Fokus liegt auf der schnellen und ansprechenden Navigation und Auskunft
 - Personalisierter Zugriff muss möglich sein
 - Es ist noch zu prüfen, ob auch auch bei Eigentümerauskünften aus dem
Sekundärbestand der lesende Zugriff protokolliert werden muss.



### Code im SVN 

 - es sollte eine Bereinigung und Strukturierung im SVN erfolgen
 - es wurde kritisiert, dass die Dokumentation für Einsteiger zunächst unübersichtlich erschein. Eine Überarbeitung sollte erfolgen
 - derzeit liegen 0.5, 0.6 und 0.7 im trunk vor, sollten aber in Branches ausgelagert werden
 - dies wird von Frank Jäger, Astrid Emde und Jürgen Fischer diskutiert und umgesetzt

### Historisierung 
Bisher wurden historische Objekte immer direkt aus dem Sekundärbestand gelöscht.
(Siehe
http://trac.wheregroup.com/PostNAS/wiki/SchrittfuerSchritt#LadenderL%C3%B6sch-undReplacedatens%C3%A4tze)

Nach dem letzten Patch zur Verarbeitung von Replace/Update-Datensätzen (dies betrifft Branch 0.7) wird es auch möglich, historische Objekte weiter im Sekundärbestand zu belassen.
Das Feld "identifier" und das Feld für das "Ende des Lebenszeitintervalls" ist dazu in allen Tabellen des Schemas einzufügen. Jürgen Fischer steht hier als Ansprechpartner zur Verfügung. Der Patch muss noch in den Code im SVN eingefügt werden

Die derzeitigen Navigation- und Auskunftprogramme und die Mapfiles werten dies aber nicht aus, würden also untergegengene Objekte fälschlicherweise in die aktuellen Auskunfte einbeziehen.




### WMS ALKIS 
 - weitere Ausarbeitung des WMS könnte erfolgen
 - ALKIS Symbole liegen bereits vor (Ansprechpartnerin Astrid Emde)
 - Ziel sollte nicht die amtliche Darstellung sein, aber sicherlich könnten noch Verbesserungen erfolgen



### Wie kann die Unterstützung des Projektes erfolgen? 
 - die Dienstleister WhereGroup, Frank Jäger, Thomas Baschetti, Jürgen E. Fischer können direkt angesprochen und mit Aufträgen versehen werden. Der Code der Neuerung fließt dann zurück ins SVN und somit in das Projekt.
 - eine finanzielle Unterstützung wäre hilfreich

### Bitte um Feedback 
 - sofern noch Fehler beim Import der NAS Daten auftreten, melden Sie dies doch bitte über die PostNAS-Liste und/der legen Sie ein Ticket im Trac an
 - fehlt Ihnen noch etwas? Melden Sie dies bitte über die Liste, so dass eine Lösung gefunden werden kann
 - Sie haben etwas entwickelt - neue Symbole, Skripte, Layerdefinitionen? Schicken Sie doch den Code an die Liste, so dass dieser in das Projekt zurückfließen kann.

