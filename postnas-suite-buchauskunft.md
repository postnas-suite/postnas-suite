## ALKIS Buchauskunft

### Erweiterte Informationen via PHP-Auskunftsskripte

#### PHP-Auskunftsskripte
- die PHP-Auskunftsskripte befinden sich im github [https://github.com/postnas-suite/postnas-suite-php-info](https://github.com/postnas-suite/postnas-suite-php-info)
- die PHP-Auskunftsskripte werden in einen aufrufbaren Ordner kopiert, z.B. mapbender/web/info
- sie können im Mapserver-Template der Flurstücke verlinkt werden [https://github.com/postnas-suite/postnas-suite-mapserver/tree/main/mapserver/alkis_n/templates](https://github.com/postnas-suite/postnas-suite-mapserver/tree/main/mapserver/alkis_n/templates)

Beispiel:

'''
(function() {
	var selParcel = "[gml_id]";
	var link = "http://alkis.mapbender3.org/mapbender3/web/info/alkis/alkisausk.php?gkz=xxx&gmlid=" 
        + encodeURI(selParcel);
	window.open(link,'','left=0,top=20,width=600,height=800,resizable=yes,menubar=no,toolbar=no,
        location=no,status=no,scrollbar=yes');
})();
'''   

![Suche und FeatureInfo im Mapbender](../images/PMapbender_Integration_von_Auskunftsskripten.png)
![Buchauskunft: Flurstück mit Eigentümer](../images/PHP_Auskunftsskript_Flurstueck_Eigentuermer.png)
![Buchauskunft: Flurstück mit Gebäude](../images/PHP_Auskunftsskript_Flurstueck_Gebaeude.png)

