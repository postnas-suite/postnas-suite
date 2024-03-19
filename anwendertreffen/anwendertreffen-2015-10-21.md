## PostNAS-Suite Anwendertreffen am 21.10.2015 in Unna


- Termin: 21.10.2015 Kreishaus Unna
- Einladungsmail: [https://lists.osgeo.org/pipermail/nas/2015-June/000788.html](https://lists.osgeo.org/pipermail/nas/2015-June/000788.html)
- 16 TeilnehmerInnen

### Themen  
- Prüfung der Meilensteine vom letzten Treffen  [wiki:PostNASAnwendertreffen2015-04-21]
- Graustufendarstellung
- Verbesserung des Postprocessings
- Angleichung alkis_import und PostNAS-alt
- ABK - Amtliche Basiskarte
- ATKIS
- Demo QGIS Visualierung der ALKIS Hamburg Daten 
- Offline Projekt
- QGIS Server zum Aufbau des WMS
-  Mapbender Navigation / Stand Mapbender3 und PostNAS Suite
- Performance
- Wartungsvertrag
- Suchmodul QGIS Plugin 

### Graustufendarstellung 
- Stadt Münster hat Finanzierung gefördert
- liegt vor in alkis_import 2.0.3
- Liegt vor im QGIS ALKIS Plugin 2.0.1
- funktioniert gut. Das Modell kann zwischen Grau- und Farbstufen wechseln.

- Darstellung in Autocad Map 3D über ALKIS-Plugin
 - hier ebenfalls Darstellungen Farbe/Grau
 - Teilbereiche werden in AutoCad geladen, nicht das ganze Stadtgebiet. Daten werden als echte AutoCAD Geometrien geladen.
 - nicht OpenSource
 - (Info: in QGIS ist auch der dxf Export möglich)

### Postprocessing 
- Dateien liegen im alkis-import im Verzeichnis '''postprocessing.d''', diese Skripte werden dann nach dem Import ausgeführt, Münster hat gute Erfahrungen mit den '''alten PostNAS Suite SQLs''' gemacht.

'''alte Mapdateien'''
- laufen nun auch mit den über alkis_import importierten Daten, nachdem das Postprocessing ausgeführt wurde
- teilweise liegen über alkis_import noch andere Datentypen mancher Spalten vor 

### ABK Amtliche Basiskarte  
- Vorstellung durch Andreas Fischer
- Folgeprodukt der DGK, ABK soll bis 2019 umgesetzt werden
- Ausgabe im Maßstab 1:2500 1:5000 1:10000
- Bericht vom OBK hat mit Postnas Suite 0.8 ABK Light aufgebaut und eine map-Datei erstellt
 - Version ist komplett fertig
 - noch nicht im Internet verfügbar
 - Symbole -> wurden mit dem FontCreator erstellt
 - farbig: Nutzungsart in anderer Farbe
- Bericht vom Kreis Unna 
 - würde ABK gerne vorantreiben
 - Machbarkeit prüfen, Anforderungen herausarbeiten (würde Kreis Unna)
 - Jürgen Fischer schaut sich die Spezifikation an, hat automatisierte Skripte
 - Unna versorgt Jürgen mit Unterlagen
 - ggf. anschließend Funding anstoßen
 - Interesse beim RVR, Münster, Unna
 - bis zum nächsten Treffen werden die Rahmenbedingungen skizziert
- wie ist das mit den Varianten (Symbol oder Textdarstellung  - z.B. Spiepl. oder Symbol), Textpositionen können gesetzt werden
- ggf. Höhenlinien auf DGM automatisch ableiten?? nicht ganz klar


### ATKIS 
- Frage zum Datenmodell ATKIS / ABK - wo ist die Relevanz
- Andreas ATKIS relevanz macht sich schlau
- eher anderer Maßstabsbereich, eher interessant für Länder


### Demo QGIS Visualierung der ALKIS Hamburg Daten  
- Jelto Buurman
- die ALKIS Daten von Hamburg stehen zum Download zur Verfügung (siehe Demodaten [wiki:ALKISTestdaten])
- Darstellung schwarz-weiß oder farbig
- ebenso Import nach AutoCad, als AutoCAD Geometrien

### Offline Projekt 
- Offline Projekt kann erstellt werden - QGIS offline Plugin, Daten werden in eine SQLite DB übertragen
- Styling wird in das Offline-Projekt übernommen
- Filter muss in das Offline Projekt noch eingebaut werden, damit nicht die gesamten ALKIS Daten nach SQLite übernommen werden
- ggf. Index / Caching o.ä. in SQLite anpassen

### QGIS Server 
- Andreas Borgardt
- im Einsatz beim Landkreis Cuxhaven
- wurde mit QGIS 2.8.3 umgesetzt
- QGIS Server soll ArcGIS Server ersetzen
- WMS mit QGIS Server wurde erstellt, leichte Änderungen am QGIS Projekt erfolgten
- gute Performance
- Templates zu den Infoskripten von Frank Jäger können genutzt werden -> Angabe der Adresse (hier genauere Angabe von Andreas)
- Achtung
 - Datenpfade beachten

### Mapbender Navigation 
- nach alkis_import mit Postprocessing geht auch die Navigation

### Angleichung alkis_import und PostNAS-alt 
- teilweise werden doppelte Strukturen durch PP angelegt
- doppelte Strukturen sollten abgeschafft werden
- bei Nutzungsarten gibt es verschiedene Ansätze bei alkis_import und PostNAS-Jäger-Auskunftsskripten
 - Auskunft Verschneidung mit den Nutzungsflächen
- Norbit macht schon beim Import die Berechnung der Nutzungsanteile pro Flurstück, dies könnte für die Auskunft übernommen werden
- Views für Auskunft wurden von alkis_import angelegt 
- Views für Mapdatei wurden von alkis_import angelegt  
- Frank Jäger würde die Auskunftsskripte an die alkis_import Lösung anpassen und die Mapdatei fallen lassen, dafür QGIS Server verwenden
- QGIS Projekt orientiert sich an der amtlichen Darstellung, Bodenschätzung fehlt, Baulasten fehlen
- Diskussion über eine sinnvolle Präsentation
 - in der Übersicht/Startansicht sollten die Gemeinden angezeigt werden (ggf. Flur, Gemarkung in Gruppe Gebiete)
 - Norbit alkis_import -> könnte geprüft werden und entsprechend die Maßstabsstufen angepasst werden
- Norbert Dephoff (Stadt Münster) passt das QGIS Projekt an und schlägt eine sinnvolle kartographische Darstellung vor 
- beim nächsten Treffen wird diese Darstellung dann vorgestellt und ggf. noch angepasst


### Performance 
- Postprocessing wird von vielen Anwendern als zu langsam erachtet
 - Norbit Postprocessing dauert lange (Erstellung Hausnr, Flurstücksnummern dauert lange)
- Postprocessing ggf. das Generieren der Flächen Gemarkungen, Gemeinden nicht jedes Mal anstoßen, sondern bei Bedarf
- Lösungsansatz: 
 - ggf. nur die Objekte anpassen, die sich geändert haben. 
 - ggf. mit Triggern arbeiten. 
 - ggf. jedem Objekt die Info mitgeben, mit welchem es zusammenhängt, damit alte Objekte ggf. gelöscht werden können 
 - ggf. Vacuum analyze nach dem Datenimport und vor dem Postprocessing durchführen
 - ggf. mehrere Kerne verwenden 
 - mehrere Transaktionen parallel anstoßen, d.h. beim Postprocession mit mehreren Transaktionen arbeiten
 - Anpassung PostgreSQL work_mem [http://www.postgresql.org/docs/9.4/static/runtime-config-resource.html](http://www.postgresql.org/docs/9.4/static/runtime-config-resource.html)
 - ggf. Abfrage mit ANY anpassen
 - ggf. einzelne Kreise jeweils in ein DB-Schema importieren
 - kurzfristig sollte eine Verbesserung erreicht werden


### Wartungsvertrag 
- Vorschlag, dass jeder Nutzer einen Wartungsbetrag bezahlt und so dass Projekt eine finanzielle Grundlage hat
- NorBIT macht sich Gedanken, was eine Wartung insgesamt kosten könnte


### Suchmodul QGIS Plugin 
- Kreis Unna
- Ausbau, so dass historische Flurstücke auch gefunden werden können
- Ausbau Eigentümersuche
- Ausbau Hausnummernsuche
- Ausbau soll bis zur nächsten FOSSGIS erfolgen (Juli 2016)


### Mapbender3 
- ALKIS Suche, Navigation wurde schon in Projekten bei der WhereGroup umgesetzt
 - Suche wurde über Solr realisiert (Selectbox zur Auswahl der Suchen - Flurstückssuche, Eigentümersuche, Grundbuchsuche..)
 - Infoabfrage - auch im Mapbender
- klären, wie eine Finanzierung und Freischaltung realisiert werden könnte
- weitere Entwicklungen sind in Arbeit (Export csv von Treffermenge, Highlight von Objekten)
- ToDo Astrid Emde Screenshots, Stand rumschicken


### nächstes Treffen 
### nächstes Treffen 
- soll in einem halben Jahr stattfinden, weiteres Treffen ist auf der FOSSGIS 2016 (Juli 2016) geplant, Vortrag ist auf der FOSSGIS 2016 geplant
- Treffen im April in Unna geplant
- Treffen zukünftig auf der Webseite auch ankündigen
- auch über FOSSGIS-Talk ankündigen


