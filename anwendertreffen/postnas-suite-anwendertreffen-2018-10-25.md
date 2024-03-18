## PostNAS-Suite Anwendertreffen am 25.10.2018 in Bremen


- Moderation Andreas Borgardt
- Anmeldung über: Mail an andreas.borgardt at geo.bremen.de
- Einladungsmail: https://lists.fossgis.de/pipermail/fossgis-talk-liste/2018-September/009517.html
- Teilnehmer/-Innen: 19 Personen


## Themen
- Vorschläge und Beiträge zur Tagesordnung per gingen per Mail an andreas.borgardt at geo.bremen.de

**Tagesordnung**
- TOP1:    Begrüßung (GeoInformation Bremen)
- TOP2:    Protokoll der letzten Sitzung (GeoInformation Bremen)

Mittagsessen und Gruppenfoto

- TOP3:    PostNAS bei GeoInformation Bremen (GeoInformation Bremen)
- TOP4:    GekoS-Schnittstelle <-> ALKIS (Mapbender) (Oliver Rennemann, Landkreis Cuxhaven)
- TOP5:    Clipping von ALKIS-Daten (Norbert Dephoff, Stadt Münster)
- TOP6:    Protokollierungsfunktion für Eigentümeraufrufe (Thomas Schüttenberg, Stadt Minden)
- TOP7:    Quo Vadis PostNAS-Suite  (GeoInformation Bremen)


## Anreise

Ort: GeoInformation Bremen, 3.Etage Raum 30.51, Lloydstr.4, 28217 Bremen

## Protokoll

Protokoll: Astrid Emde (WhereGroup)


### TOP1 Begrüßung 
  
Der Sitzungssaal war bis auf den letzten Platz belegt. Die Begrüßung und Moderation des Treffens erfolgte durch Andreas Borgardt (GeoInformation Bremen).

Begrüßung durch die Abteilungsleiterin Frau Dr.Tesmer der GeoInformation Bremen


### TOP2:    Protokoll der letzten Sitzung 

- Moderation Andreas Borgardt (GeoInformation Bremen)

Das letzte 1-tägige Treffen fand am 25.10.2017 in Gummersbach statt.

MIt Hilfe des Protokolls wurde der Status der besprochenen Punkte festgehalten und diskutiert.

Protokoll Treffen Gummersbach 25.10.2017
- http://trac.wheregroup.com/PostNAS/wiki/PostNASAnwendertreffen2017-10-25

#### Stand Release Punkttabellen
- Code liegt vor
- GDAL 2.3.3 liegt vor
- Modell ist jetzt komplett
- Hintergrund: Punktstatus ist relevat, um zu wissen, ob Messungen genau sind (Information über Punktauskunft)
- siehe svn
 - http://trac.wheregroup.com/PostNAS/browser/trunk/import/punktnummernuebersicht
 - http://trac.wheregroup.com/PostNAS/browser/trunk/umn/alkis_n/alkis_punktnummernuebersicht.map


#### WebGIS-Demos
- liegen derzeit nicht vor - Demos der WhereGroup wurden wegen DSGVO abgestellt
- Punktnummernauskunft - Demo mit Mustermonzel derzeit abgeschaltet
- Todo Astrid Emde: Demos wieder freischalten
- TODO Marina Kühn: ggf. Demo mit Daten des OBK zu Punktnummernauskunft oder anderen Daten

#### 1. Probleme 

1.1 Alle Relationen nur in eine Richtung: ax_lagebezeichnungmithausnummer aus ax_gebaeude wird nicht angezeigt 
- bezieht sich auf bei ax_gebaeude ist nicht gefüllt

1.2 Füllung von integer_array schlägt teilweise fehl 
- tritt in RLP auf: Workaround aus int[] wird varchar[] dann geht es
- TODO Jürgen Fischer & G. Schaffrath: Übergabe eine Beispieldatensatzes zum Testen


#### 2. Harmonisierung Postprocessing, Vereinheitlichung

2.0 norbitALKIS Import Tabellenbestand
- OBK berichtet, dass in der Tabelle bestand bei der Nr der führende Buchstabe verloren geht
- TODO Jürgen Fischer prüft, Marvin Kinberger schickt Beispieldatensatz

2.1 Stand der Buchauskunft - Erbbaurecht für Münster
- ist erledigt, aktuelle Skripte sind im svn
- laut Frank Jäger erledigt

2.2 OBK Eigentümerabfragen - Eigentümersuche per FME sauber gefüllt beim OBK 
- bei Interesse bitte beim OBK melden

#### 3. Darstellungsregeln der ALKIS-Daten 

3.1 Vorschlag und Präsentation vor einiger Zeit, die Zoomstufen bei den Gemeindegrenzen zu optimieren 
- ein Extramodell wurde angelegt: norgis Modell 
- Bericht Jürgen Fischer
- dieses Zeigt die Grenzen extra an

3.2 Skalierung der Flurstücksnummern wäre wünschenswert 
- allerdings sieht GeoInfoDok feste Größen vor) 
- noch offen
- Hintergrund: Flurstücks-Bruchstriche sind Linien, die vorberechnet werden
- Interesse der Stadt Bremen, finanzielle Mittel könnten bereitgestellt werden
- ggf. Übersteuern der Darstellung, flexibel Eingabe über die Maske im Importer 
- Einschätzung Jürgen Fischer: kleinere Umsetzung
- TODO Jürgen Fischer: Test mit Bremen-Schnoor, Abstimmung mit Andreas Borgardt zur Finanzierung

3.3 Einbau Schalter in die AutoCAD-Schnittstelle (EDBSgen v. norBIT)?
- Symbole in AutoCAD nicht per Faktor änderbar
- Meldung durch Münster
- Vorschlag Auswahl: kleine / große Symbole
- bisher noch nicht umgesetzt

#### 4. ABK NRW 

4.1 Darstellung von Böschungen:
- erledigt - werden dargestellt


#### 5. QGIS Plugin PostNAS Suche
- Marvin Kinberger
- läuft nun auch auf QGIS 3.x
- herzlichen Dank


#### 6. Performanzverbesserung
- 9.6 und 10.x wurde getestet
- Clustern - nach dem Import zur Performanzsteigerung
- TODO Andeas Borgardt verschickt die Beitrag zu Clustering


#### 7. QGIS-Server mit ALKIS-Infoauskunft
- Lösung über QGIS-Server und QGIS-WebClient 
- Benutzerverwaltung von Sourcepole wurde integriert
- Eigene Auskunftsformulare wurden von norBIT erstellt
- derzeit keine Open-Source-Lösung
- WMS-seitige Lösung zur Ansteuerung der Infoabfrage wäre sinnvoll (siehe Maptip bei LizMap)

#### 8. Mapbender als WebGIS-Lösung
- OBK ist sehr zufrieden mit der Lösung

#### 9. Modellartenerweiterung
- liegt in der master Version (norgis-alkis-dev) vor mit GDAL 2.3.x
- legt etwa 570 Tabellen an, bestehende Datenbank kann verwendet werden und wird erweitert
- erfolgte Änderungen sind für Darstellung nicht relevant
- TODO ALLE: Test und Feedback zur master-Version
- TODO Marina Kühn: nächstes Treffen Vorstellung des Fullschemas 

#### 10. Bodenschätzung
- TODO Marina Kühn: SQL und Map wird vom OBK im svn bereitgestellt
- TODO Andreas Borgardt: Feedback

#### 11. Import
- Feedbacl: viele Logmeldungen zu Vaccum. Machen Auswertung Log sehr unübersichtlich
- TODO Frank Jäger: Schickt log-Datei an Jürgen Fischer zur Klärung


### TOP3:    PostNAS bei GeoInformation Bremen
- Andreas Borgardt (GeoInformation Bremen)
- Dank an Entwicker 


Vorstellung der Anwendung Bauluecken
- https://www.bauluecken.bremen.de
- Basiskarte wird mit PostNAS via QGIS Server gerendert und in MapProxy gecached. Aktualisierung über PostNAS Import.
- Komplexe Straßenführung im Bereich Eduard-Schopf-Allee

Punktübersicht
- Intern
- QGWC Extended
- Benutzeranmeldung
- Sachdaten Ausgabe


GIS4Geo
- intern
- Projekt, das Lösungen mit OS vorstellt

ALKIS
- eigener Objektartenkatalog

PostNAS als WMS
- Linkbase - Archivsystem
- Liegenschaftskarte: WebGISClient - für Sachbearbeiter zur Erfassung
- Basiskarte - wie ABK light, QGIS Server und MapProxy


### TOP4:    GekoS-Schnittstelle <-> ALKIS (Mapbender
- Oliver Rennemann (Landkreis Cuxhaven)
- GekoS - Fachanwendung Bauamt für Baugenehmigngsverfahren
- QGIS im Desktop Bereich, Mapbender3 und QGWC
- Informix-DB

- Koordinatenermittlung zur Übergabe an Gekos erfolgt über ein eigenes Mapbender-Element, das die Klickposition aus Mapbender abgreift und die Koordinate an GekoS liefert
- bei neuen Datensätzen wird nun immer die Koordinate mitgespeichert
- Nutzung der Informix_FDW-Extension (ForeignDataWrapper) - SDK-Client für Informix wird benötigt
- Daten werden über FDW nach ProstgreSQL übertragen und über WMS angezeigt
- In Infoabfrage werden zusätzlich die GeoKos-Infos angezeigt
 - ggf. Georeferenzierung über fwd und Aktualisierung der Informix-Daten
 - FDW PostgreSQL ermöglicht den lesenden und teilweise schreibenden Zugriff 
 - https://wiki.postgresql.org/wiki/Foreign_data_wrappers
 - liegt vor für z.B. Oracle, Ms SQL, ODBC, ogr

### TOP5:    Clipping von ALKIS-Daten Stadt Münster
- Norbert Dephoff
- Auszug aus ALKIS von einem kleineren Bereich soll weitergegeben werden können
- Clipping - wäre sinnvoll z.B. bei großen Flurstücken
- Hinweis Jelto über QGIS: Speichern als geopackage
- AutoCAD Schnittstelle: Lösung sollte hier integrierbar sein
- QGIS: nur für einen best. Bereich die ALKIS Daten lesen
 - Definition zum Clipping muss erfolgen

### TOP6:    Protokollierungsfunktion für Eigentümeraufrufe ===
- Thomas Schüttenberg, Stadt Minden
- durch DSGVO wurde Zugriff restriktiver
- Tabelle PostNAS_search_logging - hier muss das Feld aktenzeichen vorliegen (Tabelle von Kreis Unna). In QGIS kann dann ein Feld für den Grund der Eigentümerabfrage erzeugt werden.
- Haben andere auch Bedarf an dieser Funktion?
- Idee: Erlaubte Gründe zur Validierung. Derzeit kann irgendwas eingegeben werden
- Ist beim Kreis Unna schon seit einiger Zeit im Einsatz
- WebGIS Client Lippe (Detmold Lösung ist bei der Stadt Lippe im Einsatz) - macht Fenster auf zur Abfrage

- Angabe von Gründen wäre auch für das Web interessant
 - Rückmeldung Astrid Emde. Sollte leicht in die Auskunftsskripte von Frank Jäger eingebaut werden können
- Bremen: ÖBVIs - haben eigenen Zugang und Aktion wird an Auftragsnummer gebunden
- Rückmeldung OBK: Laut Vorgabe muss stichprobenartige Kontrolle erfolgen
- Feedback Süddeutschland - wird hier weniger berücksichtigt

- TODO Thomas Schüttenberg: 
- QGIS Protokollierung sollte im Wiki dokumentiert werden
 - Anpassung Code, damit bisherige Fehler abgefangen werden
 - ToDO Jürgen Fischer + Marvin Kinberger: Einbau der Abfrage, ob Protokollierung genutzt werden soll oder nicht (Prüfung wer die Tabelle anlegt - hier als Feld aktenzeichen als default einbauen und ggf. Abfrage per Checkbox, ob Nutzung erfolgen soll)


### TOP7:    Quo Vadis PostNAS-Suite

Vor der Diskussion Quo Vadis PostNAS lud Andreas Borgardt alle TeilnehmerInnen zu einem Rundgang entlang der Weser ein. 


Hier wies Andreas Borgardt auf die aus den Medien bekannte einsturzgefährdete Stephanibruecke hin: 

(siehe auch Beitrag Extra3)
https://www.ndr.de/fernsehen/sendungen/extra_3/Realer-Irrsinn-Sperrmassnahmen-auf-der-Stephanibruecke,extra13240.html

Kurzer Exkurs nach Lemgo (auch in Lemgo ist das Leben durch den Geysir in der Fußgängerzone gefährlich geworden)
https://www.ndr.de/fernsehen/sendungen/extra_3/Realer-Irrsinn-Der-Geysir-von-Bad-Salzuflen-,extra10166.html 

Danach gab es eine rege Diskussion zum Stand der PostNAS-Suite. Wo steht das Projekt? Ist es abgeschlossen? 
Was sind die nächsten Herausforderungen?

Die Anwesenden waren sich einig, dass das Projekt noch lange nicht oder auch vielleicht nie abgeschlossen sein wird.

Zukünftige Themen sind:
- Modell für ATKIS 
- GeoInfoDok 7 
 - Hintergrund: derzeit ist noch GeoInfoDok 6.0.1 im Einsatz
 - GeoInfoDok 7 - wer hat die schon auf dem Schirm?
  - RLP Einschätzung nicht vor 2020
 - welche Auswirkungen stehen dann an
  - Änderung tatsächliche Nutzung (Landcoverage - Landuse)
  - 3D-Bereich LoD2 (Level of Detail 2) 
 - TODO Alle: Know-How zu zu GeoInfo-Doc aufbauen
- Modell für Stadtgrundkarte
 - es gibt ein DB Schema (diverse sk_Tabellen werden angelegt)


Idee - ggf. Förderanträge stellen bei 
- FOSSGIS e.V.
- QGIS DE


Stadtgrundkarte
- Vorerstellung Bremen Andreas Borgarth
- nur Flurstücke und Stadtvermessungsdaten (Mobiliar. Bushaltestellen, Hydranten, Sinkkästen, etc.)


## nächste Treffen

### FOSSGIS 2019 in Dresden
- Anwendertreffen 
- Fokus : Neueinsteiger ansprechen
- Live-Demo: vom Import zum Desktop GIS / WebGIS
- TODO Astrid Emde, Marina Kühn: Wiki-Seite erstellen, Einreichung CfP FOSSGIS, Ablauf abstimmen
- TODO FOSSGIS: ggf. Vortrag einreichen?

### Treffen im Herbst 
- 1-tägiges Treffen im Herbst 2019
- Ort muss noch gefunden werden

## Dateien zum Treffen 
- http://trac.wheregroup.com/PostNAS/browser/trunk/anwendertreffen/2018-10-25-Bremen

## Dank 
Herzlichen Dank an Andreas Borgardt für die fabelhafte Organisation des Treffen und an alle Beteiligten für die Beiträge und die rege Diskussion


## Impressionen 

[[Image(http://trac.wheregroup.com/PostNAS/export/414/trunk/anwendertreffen/2018-10-25-Bremen/20181025_postnas_anwendertreffen_gruppenfoto.jpg)]]
[[Image(http://trac.wheregroup.com/PostNAS/export/414/trunk/anwendertreffen/2018-10-25-Bremen/20181025_143532.jpg)]]
[[Image(http://trac.wheregroup.com/PostNAS/export/414/trunk/anwendertreffen/2018-10-25-Bremen/20181025_143536.jpg)]]

[[Image(http://trac.wheregroup.com/PostNAS/export/414/trunk/anwendertreffen/2018-10-25-Bremen/postnas-treffen-bremen-2018-10-25-2.jpg)]]
[[Image(http://trac.wheregroup.com/PostNAS/export/414/trunk/anwendertreffen/2018-10-25-Bremen/postnas-treffen-bremen-2018-10-25-3.jpg)]]
[[Image(http://trac.wheregroup.com/PostNAS/export/415/trunk/anwendertreffen/2018-10-25-Bremen/postnas-treffen-bremen-2018-10-25-1.jpg)]]thekla.wirkus	LW!6201053

