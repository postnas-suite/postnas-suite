## PostNAS-Suite Anwendertreffen am 03.05.2017 10 Uhr Stadthaus Münster

- Termin: 03.05.2017 10 Uhr Stadthaus Münster
- Moderation Norbert Dephoff, Johannes Brauner
- Anmeldung über: https://www.terminplaner.nrw.de/foodle.php?id=3hx82i8nb35q8bdm
- Einladungsmail: https://lists.osgeo.org/pipermail/nas/2017-March/000962.html
- Teilnehmer/-Innen: 22 Personen

### Themen

Beim 10. PostNAS Suite Anwendertreffen in Münster wurden viele Themen des letzten Treffens wieder aufgegriffen. Lesen Sie daher im Protokoll vom 7.12.2017 dem Diskussionsstand - ![PostNASAnwendertreffen 2017-10-25](./anwendertreffen-2017-10-25.md "PostNASAnwendertreffen 2017-10-25")


**Themen**
- Erweiterung des PostNAS ALKIS-Schemas
- Harmonisierung Postprocessing, Vereinheitlichung
- Skript Flächengenerierung
- Darstellungsregeln der ALKIS-Daten
- Symbole in QGIS/AutoCAD/MAP-File
- ABK NRW
- QGIS Plugin PostNAS Suche
- Performanzverbesserung
- Thema Kreisbögen
- QGIS Server mit ALKIS-Infoauskunft
- Mapbender3
- Modellartenerweiterung
- Bodenschätzung
- Verschiedenes
 - Bericht von der FOSSGIS 2017 in Passau
 - nächstes Anwendertreffen am 25.10. in Gummersbach beim OBK - siehe [wiki:PostNASAnwendertreffen2017-10-25]
 - zukünftige Vorträge / Workshops PostNAS

### Protokoll

#### Erweiterung des PostNAS ALKIS-Schemas
Aktuelle Notizen:
- den Anwesenden liegen derzeit keine Neuigkeiten zum Stand vor
- Die Firma norBIT steht im Gespräch mit den Ansprechpartnern vom GeoportalRLP und Dr. Korduan
- Einschätzung Herr Fischer u. Herr Buurman: das Datenmodell wird sich mit diesem Ansatz sehr vergrößern
- Rückmeldung der Anwesenden:
 - vielen Anwendern fehlen aus dem jetzigen Datenmodell keine Informationen
 - Frau Wirkus: ggf. Genauigkeit (wie wurden Daten erhoben, Zuverlässigkeit der Lage) fehlt – siehe Beitrag Punktauskunft unter Modellartenerweiterung
- Herr Borgardt: Punktauskunft wird von Vermessungsämtern gewünscht


#### Harmonisierung Postprocessing, Vereinheitlichung
- Herr Dephoff zeigt Screenshots der bestehenden Anwendung von Münster
  - aufwändige Symbole
  - Lösung bietet eine sehr änhnliche Darstellung in QGIS Server, MapServer mit SVG Dateien, AutoCAD Map 3D
  - Stadtgrundkarte wird im Intranet angeboten
  - aus QGIS wurde die MapServer map-Datei abgeleitet und angepasst
  - Hintergrund Münster: Darstellung enthält viele Städtische Daten / Kommunale Objekte der Topographiedatenbank - sehr spezielle Lösung der Stadt Münster
- Rückfrage an norBIT zur Darstellung der Böschungen: Derzeit noch nicht umgesetzt. 
  - ToDo: Die Möglichkeit zur Darstellung von Böschungen sollte von norBIT abgeschätzt werden (als EInzelposten unabhängig zur ABK) Nach der Abschätzung können dann ggf. Interessenten zur Finanzierung gesammelt werden. Lösung müsste in QGIS und MapServer abrufbar sein (Generierung der Böschungen in PostgreSQL/PostGIS)

- ab 1.1.2017 sind die ALKIS Daten in NRW OpenData
- Herr Scheper Feedback: ALKIS OpenData Daten vom Land - Fehlermeldung (Geometriefehler), ggf. Fehler in den Exporten vom Land
- Fehler abfangen mit skipfailure Option: Verlangsamt den Import
- skipfailure sollte nur auf eine Datei - mit den Katalogobjekten angewendet werden (sonst ist der Import insgesamt 3x langsamer)
- parallele Prozesse bringen sehr viel für die Performanz

Views Eigentümerabfrage
- siehe Mail 21.3.https://lists.osgeo.org/pipermail/nas/2017-March/000963.html
- sehr verschachtelte Abfrage
- Untererbbaurecht - Fälle eher in der Theorie. Taucht bei keinem der Nutzer auf

Stand Karte Kreis Unna:
- Stand ist im Vergleich zum letzten Anwendertreffen unverändert

Frage Richtung Buchauskunft: 
- bei Erbbaurecht/Teileigentum ist für die Auskunft in der neuen Maske ein weiterer Klick (recht unscheinbarer Link) notwendig. Hier wäre die Rückkehr zur Ansicht der alten Auskunft (Anzeige direkt auf einer Seite) gewünscht.
  - ToDo: Herr Jäger schaut sich das Skript an, ist wohl bei Umstieg auf die neue Struktur angepasst worden.

#### Skript Flächengenerierung
- keinen neuen Informationen

#### Darstellungsregeln der ALKIS-Daten
- politische Grenzen sollten schon ab 1:1000000 dargestellt werden- Vorschlag
- siehe Protokoll vom Treffen in Unna vom 25.05.2016  - [wiki:PostNASAnwendertreffen2016-05-25]
- Übergänge wurden an norBIT weitergeleitet
- ToDo NorBIT: Einbindung der Übergänge ggf. über Projektauftrag
- Anmerkung Herr Wagner: jeder hat eigene Anforderungen und dafür eigene Lösung (z.B. Nutzung der Gebäude darf in BW nicht ausgegeben werden – diese muss Herr Wagner immer entfernen) aufgebaut. Für das Projekt sollte geschaut werden, wo sinnvoll Geld investiert werden soll. Hier stellt sich die Frage, wie einfach soll für Neueinsteiger der Einstieg sein? Oder soll eher in andere Themen investiert werden?
- Anmerkung Herr Borgardt: QGIS Server: die Darstellung des Bruchstrichs beim Flurstückskennzeichen ist ab 1:500 zu groß -> Fehler in QGIS bei der Skalierung (ToDo Jürgen prüft, ob dieser Fehler  in der aktuelle Version noch auftritt)


#### Feedback zur Nutzung OpenDaten
- Münster hat erfolgreich die ALKIS Daten der Münsterland-Kreise importiert
- Frage Herr Schepers: gibt es Kontakte zum PostNAS Team? Weil Hinweis auf norBIT Import vorliegt.
- Straffer Zeitplan in 2016 bis zur Veröffentlichung. Nur 4 Monate bis ALKIS OpenData gestellt werden musste (als zip, AtomFeed)
- Es liegen 2 WFS für  ALKIS vor
  - ein WFS ist recht einfach, 1 WFS ist recht komplex
  - der einfache WFS lässt sich problemlos und in QGIS laden (gute Performanz, wenn in QGIS geladen)
- der komplexer WFS lässt sich mit Plugin von Jürgen Weichand laden http://www.weichand.de/2012/05/29/wfs-2-0-client-plugin-fur-qgis/


#### Symbole in QGIS/AutoCAD/MAP-File
- Vorschlag: Einbau eines Schalters - große und kleine Symbole (Steuerung wäre über Skalierung oder anderen Ordner denkbar)
- Todo norBIT: Lösungvorschlag prüfen

#### ABK NRW
- Rückfrage: seit dem letzten Treffen passierte nichts in Sachen Beauftragung oder Abschätzung
- 2019 soll ABK fertig sein
- RVR, Kreis Unna haben weiterhin Interesse
- OBK hat bereits 2 von 13 Gebieten fertiggestellt und abgenommen
- Münsterland - die meisten haben ca. 50 % fertig
- Kreis Unna wird im Laufe des Jahre Initiative ergreifen
- Frage zur konsequenten Umsetzung der Anforderung:
  - teilweise wird erst der grobe Aufbau umgesetzt und es kommt erst später zur  Verfeinerung
  - Rückfrage Herr Schepers zur Nutzung für Flächenvergleiche (Hintergrund: RVR führt Realnutzungkartierung (auf den Luftbildern) durch): wahrscheinlich noch nicht für Flächenvergleiche nutzbar, weil derzeit große Änderungen der Landnutzung erfolgen.
  - Land will über Satelittendaten LandNutzung/Landbedeckung ermitteln (Sentinal 2) - in Zusammenhang mit der GeoInfodok 7
- Strategie: wie gehen wir vor? Warten wir bis alle Daten da sind? Oder gehen wir das jetzt an?
- ToDo Marvin Kinberger vom Kreis Unna: spricht norBIT an zur Abschätzung der ABK Darstellung (ggf. Böschungen rauslösen aus dem Gesamt-ABK-Paket)


#### QGIS Plugin PostNAS Suche
- Keine Neuigkeiten

#### Performanzverbesserung
- Rückfrage zu Erfahrungen mit PostgreSQL 9.6? Bisher liegen keine Erfahrungen
- ogr2ogr Schalter  -ds_transaction sollte gesetzt werden
  - wurde von Herrn Fischer in GDAL eingebaut
  - wurde von Oliver Tonhofer angemerkt  siehe Mail Geometrietyp für Linien-Tabellen (12.01.2017)  https://lists.osgeo.org/pipermail/nas/2017-January/000954.html


{{{
ogr2ogr -append -update \
 -f PostgreSQL \
 -ds_transaction \
 -nlt CONVERT_TO_LINEAR \
 --config PG_USE_COPY YES
}}}

#### Thema Kreisbögen
- Rückmeldung Herr Fischer: Schweizer haben Kreisbögen eingebaut und rudern nun aber wieder zurück, weil Probleme auftreten
- Hintergrund: GDAL und QGIS unterstützen Kreisbögen, aber unabhängig voneinander. PostGIS unterstützt ebenfalls Kreisbögen.


#### #### QGIS Server mit ALKIS-Infoauskunft
- Wunsch QGIS Server konfigurierbare FeatureInfo Ausgabe
- ist bei MapServer und GeoServer möglich
- Angebot bei norBIT wurde angefragt von KRZ (11 / 2016). Bisher liegt die Abschätzung noch nicht vor
- Rückmeldung Herr Fischer: französische Firma Oslandia ist gerade sehr aktiv in Sachen QGIS Server
- Wunsch ist ggf. Thema für QGIS.DE Finanzierung (Frau Emde fragt nach)
- TODO NorBIT liefert bis zum nächsten Anwendertreffen eine Abschätzung
- Interessenten sind  Herr Wagner, KRZ, Bremen und viele andere


#### Mapbender3
- Dokumentation siehe http://trac.wheregroup.com/PostNAS/wiki/PostNASMapbender3
- Rückmeldung Frau Emde: es liegen keine neuen Entwicklungen zur Absicherung vor. Lösung über Absicherung durch die Session ist angedacht.
- Anmerkung Herr Schepers, Herr Kock: Lösung über LDAP wäre gewünscht, damit auch in QGIS WMS gesichert geladen werden kann
- Frage zur gesicherten Infoabfrage in Mapbender3: https://lists.osgeo.org/pipermail/nas/2017-April/000971.html
- ToDo Frau Emde: Lösung oder Abschätzung bis zum nächsten treffen. Herr Baschetti bietet unterstützung an.

#### Modellartenerweiterung
##### Punktauskunft
Die ALKIS Daten enthalten diverse Vermessungspunkte. Diese werden bisher noch nicht dargestellt. Die Auskunft über die Genauigkeit und Herkunft der Punkte ist aber für verschiedene Bereiche von Interesse.
Marina Kühn vom Oberbergischen Kreis stellt eine Lösung zur Darstellung der Vermessungspunkte vor.
Das Datenmodell wurde um verschiedene Tabellen/Spalten erweitert (ax_punktortag, ax_punktortau, ax_punktortta, ax_besonderergebaeudepunkt, ax_aufnahmepunkt, ax_sicherungspunkt, ax_sonstigervermessungspunkt, ax_besonderertopographischerpunkt, ax_grenzpunkt) – siehe http://trac.wheregroup.com/PostNAS/browser/trunk/import/punktnummernuebersicht
Anschließend sollten  auch dies Tabelle beim Import von NAS Daten gefüllt werden.
Die Daten enthalten u.a. die Punktkennung, Informationen zur Genauigkeit der Daten, Vermessungsart sowie relative Höhe.
Durch ein Postprocessing werden die Daten in die Tabelle pp_punktnummernuebersicht überführt, die anschließend für die Darstellung und Beauskunftung verwendet wird.
Es wurde außerdem eine MapServer Mapdatei zur Darstellung und Beauskunftung der Punkte erstellt. Diese Darstellung wurde beim Treffen vorgestellt und bekam eine positive Rückmeldung.
Die SQLs und MapServer Dateien finden sich nun im svn. In Kürze werden die Daten auch in der PostNAS-Demo dargestellt.
- MapServer http://trac.wheregroup.com/PostNAS/browser/trunk/umn/alkis_n/alkis_punktnummernuebersicht.map
- PostgreSQL http://trac.wheregroup.com/PostNAS/browser/trunk/import/punktnummernuebersicht
- https://demo.postnas.org/application/alkis_demo
- Anfrage: Das allgemeine Datenschema sollte um die fehlenden Spalten erweitert werden, so dass der Import dieser Spalten bei allen Anwendern erfolgt.
- Workflow: sofern fehlende Spalten auffallen, sollte eine Mail an die Mailingliste geschickt und an Herrn Fischer weitergeleitet werden. Herr Fischer kann dann das Datenmodell erweitern.

#### Bodenschätzung
- siehe Mail Mailingliste 20.9.2016 Bodenschätzung - Schema und Ableitung  https://lists.osgeo.org/pipermail/nas/2016-September/000932.html
- Bodenschätzung - Schema und Ableitung https://lists.osgeo.org/pipermail/nas/2017-April/000970.html
- Linienbegleitende Signaturen mit Bodenzahlen. Ziel: Visualisierung und Auskunft. Visualisierung siehe GeoInfo
- Stadt Münster hat die Darstellung derzeit aus dem IBR Dienst herausgezogen - nicht über PostNAS
- ToDO Herr Jäger schaut sich das einmal an über prüft den Layer
- ToDO Ertragsmesszahlen – Itebo hat ein Berechnungsskript und hat den Einbau in die Auskunft durchgeführt (Frau Wiegand schickt die Skript an Frank Herrn Jäger)

#### Verschiedenes
- Einladung zum Geonetzwerk Münsterland GeoTag nach Münster
- Mittwoch 17.5. in Münster
- http://www.geonetzwerk-muensterland.de/

Nächstes Treffen
- Marina Frau Kühn und Jutta Frau Lusebrink laden zum nächsten PostNAS Anwendertreffen nach Gummersbach im Kreishaus des Oberbergischen Kreises ein.
- Das Treffen ist für den 25. Oktober 2017 geplant - anwendertreffen-2017-10-27.md. 
- Beginn des Treffens: 11 Uhr

anvisierte Treffen
- ggf. dann im Zuge der FOSSGIS 2018 im März 2018 in Bonn
- Treffen in Bremen, Norden wären ebenfalls möglich


