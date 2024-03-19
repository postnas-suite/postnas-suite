## PostNAS-Suite und Mapbender

## Suchen

- über das Element Suche (Search-Router) können in Mapbender Suchen definiert werden 
- ALKIS-Suchen nach Flurstück, Eigentümer und Adresse können so angeboten werden

Dazu müssen folgende Schritte zur Vorbereitung erfolgen


1. ALKIS-Datenbank in Mapbender einbinden
   -  Einbinden der ALKIS Datenbank in Mapbender siehe https://doc.mapbender.org/en/customization/database.html

2. PostgreSQL-Views für die Suchen in der Datenbank erzeugen

3. Suchen-Element in die Anwendung einbinden
   -  siehe https://doc.mapbender.org/de/functions/search/search_router.html

Das Suchen-Element kann dann mit den folgenden YAML-Definitionen konfiguriert werden.

### PostgreSQL-Views für die Suchen in der Datenbank erzeugen

#### View Flurstückssuche

```
Drop view qry_mb3_ax_flurstueck_suche;
CREATE OR REPLACE VIEW public.qry_mb3_ax_flurstueck_suche AS 
 SELECT f.gml_id, f.gemarkungsnummer::text AS gemarkungsnummer, f.beginnt, f.endet, 
    g.bezeichnung as gemarkungsname, g.land,  f.flurnummer::text AS flurnummer,
    f.zaehler::text AS zaehler, f.nenner::text AS nenner, replace(f.flurstueckskennzeichen::text, '_'::text, ''::text) AS flurstueckskennzeichen,
    f.wkb_geometry AS the_geom_etrs
   FROM ax_flurstueck f
     LEFT JOIN ax_gemarkung g ON f.gemarkungsnummer::text = g.gemarkungsnummer::text
       WHERE f.endet IS NULL AND NOT (f.flurstueckskennzeichen IN ( SELECT ax_historischesflurstueck.flurstueckskennzeichen
           FROM ax_historischesflurstueck));
```

#### View Adresssuche

```
Drop view qry_mb3_adresse_suche;
 CREATE OR REPLACE VIEW public.qry_mb3_adresse_suche AS

  SELECT h.ogc_fid,replace(h.hausnummer::text, ' '::text, ''::text) AS hausnummer,h.gemeinde::text AS gemeinde,c.bezeichnung as gemeindename,
    h.kreis::text AS kreis,  g.wkb_geometry AS the_geom_etrs ,h.gml_id,  h.lage,   k.bezeichnung as strasse, c.regierungsbezirk
    FROM ax_lagebezeichnungmithausnummer h
      JOIN ax_gebaeude g ON ARRAY[h.gml_id] <@ g.zeigtauf AND g.endet IS NULL
      JOIN ax_lagebezeichnungkatalogeintrag k ON h.lage::text =k.lage::text AND h.gemeinde = k.gemeinde  and h.regierungsbezirk =k.regierungsbezirk AND h.kreis = k.kreis
     JOIN ax_gemeinde c ON h.regierungsbezirk = c.regierungsbezirk and h.gemeinde = c.gemeinde AND h.kreis = c.kreis;
```


#### View Eigentümersuche

```
CREATE OR REPLACE VIEW public.qry_mb3_eigentuemer_suche_union AS 
 SELECT foo.flurstueckskennzeichen, foo.flur, foo.fs_zaehler, foo.fs_nenner, foo.flaeche,
    foo.bezirkname, foo.gb_blatt,foo.blattart, foo.bvnr, foo.buchgsartwert, foo.buchgsart,
    foo.name_num, foo.nachname, foo.vorname ,  foo.geom
   FROM (  SELECT      f.flurstueckskennzeichen, f.flurnummer AS flur, f.zaehler AS fs_zaehler,  f.nenner AS fs_nenner, f.amtlicheflaeche AS flaeche, 
            b.bezeichnung AS bezirkname,      g.buchungsblattnummermitbuchstabenerweiterung AS gb_blatt, g.blattart,
            s.laufendenummer AS bvnr,        art.wert AS buchgsartwert,  art.bezeichner AS buchgsart,
            n.laufendenummernachdin1421 AS name_num,      p.nachnameoderfirma AS nachname, p.vorname, f.wkb_geometry AS geom
           FROM ax_person p
             JOIN ax_namensnummer n ON p.gml_id = n.benennt AND n.endet IS NULL             
	      JOIN ax_buchungsblatt g ON n.istbestandteilvon = g.gml_id  AND g.endet IS NULL 
             	JOIN ax_buchungsblattbezirk b ON g.land::text = b.land::text AND g.bezirk::text = b.bezirk::text  AND b.endet IS NULL             			
             JOIN ax_buchungsstelle s ON s.istbestandteilvon = g.gml_id  
		JOIN v_bs_buchungsart art ON s.buchungsart = art.wert AND s.endet IS NULL 			
	        JOIN ax_flurstueck f ON f.istgebucht = s.gml_id AND f.endet IS NULL 
        UNION
         SELECT     f.flurstueckskennzeichen, f.flurnummer AS flur, f.zaehler AS fs_zaehler,  f.nenner AS fs_nenner, f.amtlicheflaeche AS flaeche, 
            b.bezeichnung AS bezirkname,      g.buchungsblattnummermitbuchstabenerweiterung AS gb_blatt, g.blattart,
            s.laufendenummer AS bvnr,        art.wert AS buchgsartwert,  art.bezeichner AS buchgsart,
            n.laufendenummernachdin1421 AS name_num,      p.nachnameoderfirma AS nachname, p.vorname, f.wkb_geometry AS geom
           FROM ax_person p
             JOIN ax_namensnummer n ON p.gml_id = n.benennt AND n.endet IS NULL             
	      JOIN ax_buchungsblatt g ON n.istbestandteilvon = g.gml_id  AND g.endet IS NULL 
             	JOIN ax_buchungsblattbezirk b ON g.land::text = b.land::text AND g.bezirk::text = b.bezirk::text  AND b.endet IS NULL           			
             JOIN ax_buchungsstelle s ON s.istbestandteilvon = g.gml_id  
		JOIN v_bs_buchungsart art ON s.buchungsart = art.wert AND s.endet IS NULL 
             JOIN ax_buchungsstelle bs ON (bs.gml_id=ANY(s.an) OR bs.gml_id=ANY(s.zu)) 
	     JOIN ax_flurstueck f ON f.istgebucht = bs.gml_id AND f.endet IS NULL ) foo;
```
 
#### View Grundbuchsuche

```
CREATE OR REPLACE VIEW public.qry_mb3_grundbuch_suche AS
 SELECT foo.buchungsart, foo.bezirkname, foo.bezirk, foo.gb_blatt,
    foo.blattart, foo.flurstueckskennzeichen, foo.geom, foo.endet
   FROM ( SELECT s.buchungsart, b.bezeichnung AS bezirkname, b.bezirk,
            g.buchungsblattnummermitbuchstabenerweiterung AS gb_blatt, g.blattart,
            f.flurstueckskennzeichen, f.wkb_geometry AS geom, f.endet
           FROM  ax_buchungsblatt g
            JOIN ax_buchungsblattbezirk b ON g.land::text = b.land::text AND g.bezirk::text = b.bezirk::text  AND b.endet IS NULL
            JOIN ax_buchungsstelle s ON s.istbestandteilvon = g.gml_id
            JOIN v_bs_buchungsart art ON s.buchungsart = art.wert AND s.endet IS NULL
            JOIN ax_flurstueck f ON f.istgebucht = s.gml_id AND f.endet IS NULL
        UNION
         SELECT s.buchungsart, b.bezeichnung AS bezirkname, b.bezirk,
            g.buchungsblattnummermitbuchstabenerweiterung AS gb_blatt, g.blattart,
            f.flurstueckskennzeichen, f.wkb_geometry AS geom, f.endet
           FROM ax_buchungsblatt g
                JOIN ax_buchungsblattbezirk b ON g.land::text = b.land::text AND g.bezirk::text = b.bezirk::text  AND b.endet IS NULL
             JOIN ax_buchungsstelle s ON s.istbestandteilvon = g.gml_id
        JOIN v_bs_buchungsart art ON s.buchungsart = art.wert AND s.endet IS NULL
             JOIN ax_buchungsstelle bs ON (bs.gml_id=ANY(s.an) OR bs.gml_id=ANY(s.zu))
         JOIN ax_flurstueck f ON f.istgebucht = bs.gml_id AND f.endet IS NULL) foo;
```

### Konfiguration des Search-Routers

#### Flurstückssuche

```
class: Mapbender\CoreBundle\Component\SQLSearchEngine
class_options:
  connection: alkis
  relation: qry_mb3_ax_flurstueck_suche
  attributes:
    - gml_id
    - gemarkungsnummer
    - gemarkungsname
    - flurnummer
    - zaehler
    - nenner
    - flurstueckskennzeichen
  geometry_attribute: the_geom_etrs
form:
  gemarkungsnummer:
    type: text
    options:
      required: false
    compare: exact
  flurnummer:
    type: text
    options:
      label: Flur
      required: false
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: gemarkungsname
  zaehler:
    type: text
    options:
      label: Zähler
      required: true
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: gemarkungsname
  nenner:
    type: text
    options:
      label: Nenner
      required: false
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: gemarkungsname
results:
  view: table
  headers:
    flurnummer: Flur
    zaehler: Zähler
    nenner: Nenner
    gemarkungsnummer: Gemarkung
  callback:
    event: click
    options:
      buffer: 50
```

#### Adresssuche

```
class: Mapbender\CoreBundle\Component\SQLSearchEngine
class_options:
  connection: alkis
  relation: qry_mb3_adresse_suche
  attributes:
    - kreis
    - gemeindenummer
    - hausnummer
    - gemeindename
    - strasse
  geometry_attribute: the_geom_etrs
form:
  gemeindename:
    type: text
    options:
      required: false
  strasse:
    type: text
    options:
      label: Straße
      required: false
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: gemeindename
  hausnummer:
    type: text
    options:
      label: Hausnummer
      required: false
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: bezeichnung
results:
  view: table
  headers:
    strasse: Straße
    hausnummer: Hausnr.
    gemeindename: Ort
  callback:
    event: click
    options:
      buffer: 50
```

#### Eigentümersuche

```
class: Mapbender\CoreBundle\Component\SQLSearchEngine
class_options:
  connection: alkis
  relation: qry_mb3_eigentuemer_suche_union
  attributes:
    - gb_blatt
    - buchgsart
    - nachname
    - vorname
    - bezirkname
    - fs_zaehler
    - fs_nenner
    - flur
    - flurstueckskennzeichen
  geometry_attribute: geom
form:
  nachname:
    type: text
    options:
      label: Nachname
      required: false
    compare: ilike
  vorname:
    type: text
    options:
      label: Vorname
      required: false
    compare: ilike
  gb_blatt:
    type: text
    options:
      label: 'Grundbuchblattnummer (GB-NR)'
      required: false
    compare: exact
  bezirkname:
    type: text
    options:
      label: Bezirk
      required: false
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: flur
  flur:
    type: text
    options:
      label: Flur
      required: false
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: flur
  fs_zaehler:
    type: text
    options:
      label: Zähler
      required: false
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: flur
  fs_nenner:
    type: text
    options:
      label: Nenner
      required: false
      attr:
        data-autocomplete: 'on'
        data-autocomplete-distinct: 'on'
        data-autocomplete-using: flur
results:
  view: table
  headers:
    nachname: Nachname
    vorname: Vorname
    flurstueckskennzeichen: Flstk.
    gb_blatt: GB-NR
    bezirkname: Bezirk
    flur: Flur
  callback:
    event: click
    options:
      buffer: 40
      minScale: null
      maxScale: null
```

#### Grundbuchsuche

```
class: Mapbender\CoreBundle\Component\SQLSearchEngine
class_options:
  connection: alkis
  relation: qry_mb3_grundbuch_suche
  attributes:
    - gb_blatt
    - buchungsart
    - bezirk
    - bezirkname
    - ergebnis
    - gemarkungsname
  geometry_attribute: geom
form:
  gemarkungsname:
    type: Symfony\Component\Form\Extension\Core\Type\ChoiceType
    options:
      label: Gemarkung
      required: false
      placeholder: 'Bitte wählen Sie einen Gemarkung aus'
      choices:
        Ort1: Ort1
        Ort2: Ort2
        Ort3: Ort3
    compare: exact
  gb_blatt:
    type: Symfony\Component\Form\Extension\Core\Type\TextType
    label: 'Grundbuchblattnummer (GB-NR)'
    options:
      required: false
    compare: exact
  buchungsart:
    type: Symfony\Component\Form\Extension\Core\Type\TextType
    label: Buchungsart
    options:
      required: false
    compare: exact
results:
  view: table
  headers:
    gb_blatt: GB-NR
    buchungsart: Buchungsart
    ergebnis: Buchung/Flurstück
    gemarkungsname: Gemarkung
  callback:
    event: click
    options:
      buffer: 200
      minScale: null
      maxScale: null
  styleMap:
    default:
      strokeColor: '#FF0000'
      strokeOpacity: 0.4
      strokeWidth: 4
      fillColor: '#FF0000'
      fillOpacity: 0.4
      pointRadius: 10
    select:
      strokeColor: '#66D9FF' #
      strokeWidth: 4
      strokeOpacity: 0.9
      fillColor: '#66D9FF'
      fillOpacity: 0.7
      pointRadius: 10
    temporary:
      strokeColor: '#66FF33'
      strokeWidth: 4
      strokeOpacity: 0.9
      fillColor: '#66FF33'
      fillOpacity: 0.7
```



### Erweiterte Informationen via PHP-Auskunftsskripte 

TBD
