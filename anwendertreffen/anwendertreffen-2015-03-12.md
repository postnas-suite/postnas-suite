## PostNAS-Suite Anwendertreffen am 120.3.2015 auf der FOSSGIS in Münster


- Moderation: 
- Teilnehmer: über 35 Personen
- FOSSGIS 2015 Programm: http://www.fossgis.de/konferenz/2015/programm/events/790.de.html

Auf der FOSSGIS 2015 gab es ein PostNAS Anwendertreffen, das mit mehr als 35 Teilnehmern sehr gut besucht war. Bei dem Treffen wurden Erfahrungen ausgetauscht. Die Anwender konnten von sehr guten Erfahrungen berichten. Dennoch können noch Bereiche verbessert werden. Es wurden außerdem Themen diskutiert, die zukünftig angegangen werden könnten. Die Themen wurden gesammelt und sollen auf dem nächsten Anwendertreffen am 21.4. 2015 in Münster weiter erörtert werden.

### Themen 

#### ATKIS
- ATKIS - Armin Retterath arbeitet derzeit an einer neuen Version der ATKIS Darstellung. Diese neue Version des Mapfiles wird vom Geoportal RLP in Kürze bereitgestellt.
- http://www.geoportal.rlp.de/

#### ogr2ogr beschleunigter Import 
- Hinweis: der Import via ogr2ogr kann beschleunigt werden. Dabei muss ein weiterer Parameter gesetzt werden:
- siehe http://www.gdal.org/ogr2ogr.html

ogr2ogr:

    -ogr2ogr mit Parameter -gt 


- Codelisten demnächst Online: Armin Retterath weitere Infos


### Themen für das Treffen in Münster am 21.4.2015 
Beim PostNAS Anwendertreffen wurde über ein weiteres Treffen diskutiert. Dieses zweites Anwendertreffen für die zwischenzeitlich freie norBIT ALKIS-Lösung und PostNAS soll am 21.4. 2015 im Stadthaus in Münster stattfinden. Für dieses Treffen steht ein ganzer Tag zur Verfügung. Auf dem Anwendertreffen auf der FOSSGIS wurde Themen für dieses Treffen gesammelt.

Das Treffen in Münster am 21.4.2015 wird auf der folgenden Seite protokolliert: [wiki:PostNASAnwendertreffen2015-04-21]

- ABK Amtliche Basiskarte kommt
 - Ziel: Visualisierung der ABK, Aufbau eines WMS zur Darstellung
 - Hintergrund: DGK5 wird von der ABK abgelöst. Es handelt sich dabei um ein amtliches Produkt, das von den Kunden angefordert werden wird
 - MapServer WMS: 
  - ähnliche Darstellung wie ALKIS mit zusätzlichen topographischen Elementen. Darüberhinaus kommenn noch neue Objekte in der Darstellung hinzu. 
 - diverse Modelle stehen in der NAS-Datei: so gibt es auch ein ABK Modell - (die Modelle werden in der Version 0.8  nun als Array geführt)
  

- QGIS Server
 - wäre Alternative zum MapServer
 - klären: Infoabfrage - wie ist diese anpassbar? (Bernhard Ströbl kann dazu gefragt werden)
 - neu: Python Plugins im Server -> klären, ob wir Skripte über Infoabfrage aufrufen können


- Postprocessing nach dem Import angleichen
 - Norbit + PostNAS Postprocessing sollte zusammengebracht werden. Derzeit müssen nach dem Import mit Norbit Import noch weitere SQLs ausgeführt werden, damit auch der WMS/Navigation/Infoabfrage von PostNAS funktionieren.


- Norbit WMS: 
 - gut wäre es, wenn die Infoabfrage an die PostNAS Skripte weitergeleitet werden könnte
 - im WMS sollten Gruppen eingebaut zur Strukturierung eingebaut werden (siehe PostNAS WMS)

- WMS Graustufendarstellung 
 - derzeit: farbige Dartellung der ALKIS Daten  --> Ziel: Graustufendarstellung der ALKIS Daten, um andere farbige Daten gemeinsam zu visualisieren
 - Kombination mit der AutoCAD Lösung 
 - GeoInfoDoc hat auch ein SW-Katalog - dieser könnte umgesetzt werden
 - ggf. auch bunte Darstellung - gelb rot ..


- QGIS Verbesserung der Flurstückssuche
 - Kreis Unna hat ein Plugin geschrieben
 - Integration in das derzeitige QGIS Plugin ist angestrebt


- NBA - Transaction
 - wenn es zu Fehlern kommt beim NBA Import ist es schwer, den Fehler zu finden
 - kann hier was verbessert werden? 
 - ogr2ogr --> schwer den Punkt zu finden
 - vielleicht PostGIS Memento nutzen -> siehe Vortrag von eben
 - Gefahr ist eine inkonsistente DB, die wir vermeiden wollen
 - Lösungsansatz: ggf. über die ALKIS Dateien, den Status prüfen

- Nachprozessierung
 - Problem: dauert teilweise lange, derweil ist der lesende Zugriff auf die Daten nicht möglich
 - Lösungansatz: Prozess beschleunigen, indem nur die Daten nachprozessiert werden, die neu hinzugekommen sind

- Highlighting im WebGIS Bereich und die selektierten im Druck ausgeben


