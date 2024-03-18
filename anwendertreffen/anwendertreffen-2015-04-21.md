## PostNAS-Suite Anwendertreffen am 21.4.2015 in Münster


- Termin: 21.4.2015 Stadthaus Münster
- Teilnehmer: Bestätigung der Teilnahme über doodle: http://doodle.com/x54smfdgg3sd4be4
- Einladungsmail: http://lists.osgeo.org/pipermail/nas/2015-March/000768.html


### Themen 

#### ABK Amtliche Basiskarte 
 - Ziel: Visualisierung der ABK, Aufbau eines WMS zur Darstellung
 - Hintergrund: DGK5 wird von der ABK abgelöst (Einführung bis 2019). Es handelt sich dabei um ein amtliches Produkt, das von den Kunden angefordert werden wird. DGK5 wird für Bereich für die die ABK aktiv ist, nicht mehr fortgeführt.
 - MapServer WMS: 
  - ähnliche Darstellung wie ALKIS mit zusätzlichen topographischen Elementen (z.B. Böschungen). Darüberhinaus kommenn noch neue Objekte in der Darstellung hinzu. 
 - diverse Modelle stehen in der NAS-Datei: so gibt es auch ein ABK Modell - (die Modelle werden in der Version 0.8  nun als Array geführt)
 - Frage nach Interesse an der ABK 
  - OBK, wird schon in ALKIS derzeit erfasst, geplant ist die Map-Datei selbst aufzubauen
  - Kreis Unna
  - Bielefeld Lösung über Rasterdaten 
 - '''Todo Kreis Unna / OBK''' Vorschlag: Vertagt auf das nächste Treffen, Kreis Unna / OBK recherchiert den Aufwand für selbst umsetzen bzw. Beauftragung
 

 
#### WMS über QGIS Server 
 - wäre Alternative zum MapServer
 - Aufruf der Auskunftskripte: gml-ID könnte im featureInfo übergeben werden (laut Jürgen Fischer)
 - '''Todo NorBIT''': in QGIS Server einbinden und FeatureInfo auf die Navigationsskripte von PostNAS verweisen
 

#### Postprocessing nach dem Import angleichen 
 - Norbit + PostNAS Postprocessing sollte zusammengebracht werden. Derzeit müssen nach dem Import mit Norbit Import noch weitere SQLs ausgeführt werden, damit auch der WMS/Navigation/Infoabfrage von PostNAS funktionieren.
 - Jürgen Fischer hat bereits Views angelegt, die die PostNAS Tabellen/Views abbilden, so dass die Auskunfts-Skripte von PostNAS aufgerufen werden könnten.
 - QGIS Server WMS -> Infoskripte könnten über den FeatureInfo aufgerufen werden über Maptip oder Weiterleitung an andere Skripte
 - Nutzung fehlt noch in Norbit-Lösung: Prostprocessing von Frank Jäger könnte übernommen werden
  - siehe https://trac.wheregroup.com/PostNAS/browser/trunk/import/nutzungsart_definition.sql
  - https://trac.wheregroup.com/PostNAS/browser/trunk/import/nutzungsart_metadaten.sql
  - siehe https://trac.wheregroup.com/PostNAS/browser/trunk/import/nutzungsart_laden.sql
 - Priorisierung: zuerste WebGIS (QGIS Server, MapServer) dann Desktop
 - bei Entwicklung beachten, dass es Anwender gibt, die nur lokal arbeiten und eine Auskunft benötigen
 - '''Todo NorBIT'''


#### Norbit WMS 
 - gut wäre es, wenn die Infoabfrage an die PostNAS Skripte weitergeleitet werden könnte
 - im WMS sollten Gruppen eingebaut zur Strukturierung eingebaut werden (siehe PostNAS WMS)
 - '''Todo NorBIT'''


#### WMS Graustufendarstellung 
 - derzeit: farbige Darstellung der ALKIS Daten  --> Ziel: Graustufendarstellung der ALKIS Daten, um andere farbige Daten gemeinsam zu visualisieren
 - Kombination mit der AutoCAD Lösung 
 - GeoInfoDoc hat auch ein SW-Katalog - dieser könnte umgesetzt werden (eigene Ableitungsregel mit eigenen Symbolen für die SW-Ansicht)
 - ggf. auch bunte Darstellung - gelb rot ..
 - Umsetzung für AutoCAD (native Umsetzung in AutoCAD als dwg)
  - dann würde die WMS Darstellung und QGIS Darstellung als Abfallprodukt abfallen
 - Todo '''Münster''' wird wahrscheinlich von der Stadt Münster angestoßen, Umsetzung erfolgt dann durch die Firma '''NorBIT'''


#### QGIS Verbesserung der Flurstückssuche 
 - Kreis Unna hat ein Plugin geschrieben
 - Teile der Flurstücksnummer kann eingegeben werden, 1-n Flurstücke können selectiert werden, dann zoom auf Extent und Hervorhebung der Treffer, Treffer werden auf einem eigenen Layer "Suchergebnis" ausgegeben.
 - Wenn Flurstücke nicht mehr vorliegen, wird auf den Bereich gezoomt, in dem das Flurstück wahrscheinlich einmal vorlag
 - Integration in das derzeitige QGIS Plugin wäre möglich
 - (Norbit Lösung verfügt bereits über einfache Suche)
 - '''Todo Kreis Unna''' Das neue Plugin wird im QGIS Plugin Repository referenziert https://plugins.qgis.org


#### NBA - Transaction 
 - wenn es zu Fehlern kommt beim NBA Import ist es schwer, den Fehler zu finden
 - kann hier was verbessert werden? 
 - ogr2ogr --> schwer den Punkt zu finden
 - vielleicht pgmomentum nutzen -> siehe Vortrag von eben
 - Gefahr ist eine inkonsistente DB, die wir vermeiden wollen
 - Lösungsansatz: ggf. über die ALKIS Dateien, den Status prüfen


#### Nachprozessierung 
 - Problem: dauert teilweise lange, derweil ist der lesende Zugriff auf die Daten nicht möglich
 - Lösungansatz: Prozess beschleunigen, indem nur die Daten nachprozessiert werden, die neu hinzugekommen sind
 - Lösung vom Kreis Unna liegt vor (Marvin Brandt) - Konsolidierung mit der NorbitALKIS-Lösung
 - '''Todo Kreis Unna''' gibt die Anpassung -TRUNCATE statt DELETE- an '''Todo Jürgen Fischer NorBIT''' weiter 

### Frage: Kann PostNAS Vollhistorie? 
 - PostNAS - ja je nach Trigger
 - Norbit ALKIS - ja immer


### ALKIS Kreisbögen 
 - GDAL kann nun Kreisbögen
 - Parameter angeben CONVERT_TO_LINEAR (Starting with GDAL 2.0, CONVERT_TO_LINEAR can be used to to convert non-linear geometries types into linear geometries by approximating them. can be used to to convert non-linear geometries types into linear geometries by approximating them.)
 - http://gdal.org/ogr2ogr.html
 - Information: für PostNAS wird nicht mehr der GDAL trunk benötigt, GDAL 1.11 kann verwendet werden


### Beschleunigter Aufruf 
 - Parameter -gt
 - '''Todo Andreas Borgardt''' testet diesen Parameter und gibt Feedback über die Mailingliste


### Highlighting im WebGIS Bereich und die selektierten im Druck ausgeben 
 - Mapbender 2.x addvendorspecific
 - Mapbender3 neue Suche highlighted Treffer automatisch und gibt diese im Druck aus
 - '''Todo Astrid Emde''' - Beschreibung der Lösung über addvendorspecific

### Mapdatei aus Norbit ALKIS Plugin 
 - Mapfile sollte noch Metadaten und Kontaktangaben und mehr enthalten, was konfigurierbar sein sollte
 - include wird vom MapScript aufgelöst, daher nicht sinnvoll
 - '''Todo Andreas Borgardt/ Jürgen Fischer''' Analysiert die Mapdateien und deren Unterschiede


### Frage Zusammenführung des Codes / Wiki sowie Norbit ALKIS / PostNAS 
 - Vorschlag Umzug des PostNAS Codes aus dem svn nach GitHub
 - Zusammenführung wird nicht als sehr wichtig angesehen, gemeinsame Dokumentation im PostNAS-Wiki


### Übersicht welche Komponenten liegen vor und wer ist involviert 
 - als Tabelle
 - als Grafik
 - '''Todo: Andeas Borarth''' erstellt eine Übersicht im Wiki der Seite - siehe [wiki:Komponenten]


### Name der Projektes ändern 
 - es kam der Vorschlag auf, den Namen des Projektes zu ändern. Nach einer kurzen Diskussion einigten sich die Anwesenden auf den Namen '''PostNAS Suite'''
 - Über ein Scaubild soll verdeutlich werden, welche Komponenten zur Suite gehören. Dieses Schaubild / Information sollte zentral auf der PostNAS Seite platziert werden.
 - '''Todo Astrid''' Bekanntgabe über die Mailingliste und Beschreibung im Wiki


### Trac/SVN Zugriff zum Editieren erweitern 
 - Jürgen Fischer editieren trac ermöglichen


### Vorträge auf diversen Veranstaltungen 
 - Intergeo, FOSSGIS oder andere Veranstaltungen könnten für Vorträge interessant sein
 - '''Todo Astrid Emde, Jelto Buurman'''
 - Vortrag auf der Intergeo und FOSSGIS


### PSC 
 - Frage - wollen wir ein PSC gründen?
 - Anregung: eher regelmäßige Treffen in diesem Kreis. 
  - Treffen auf der FOSSGIS sind eher nur kurz und informativ für Neueinsteiger. Sollten weiterhin stattfinden.
  - Auf längeren Treffen können Themen intensiver diskutiert werden.


### nächstes Treffen 
 - Soll in Unna beim Kreis Unna stattfinden
 - '''Todo Andreas Fischer''' schlägt 3 Termine vor, über doodle erfolgt anschließend die Abstimmung
