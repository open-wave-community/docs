# Geo-WMS/WFS lagen

Portaal beheerportaal-Nieuw. Tegel _Geo Kaartlagen_.

API(s):

- getStandardList: [https://api.open-wave.nl/RemMethods/getRemMethod/415](https://api.open-wave.nl/RemMethods/getRemMethod/415.md)
- getStandardDetail: [https://api.open-wave.nl/RemMethods/getRemMethod/416](https://api.open-wave.nl/RemMethods/getRemMethod/416.md)

Screenidentifiers:

- MDLC_getVwfrmGeoWmsList.xml
- MDDC_getVwfrmGeoWmsDetail.xml

## Definiëren van externe kaartlagen

De inlogger moet beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99.
Alle kolommen en knoppen zijn dan toegankelijk.

### De betekenis van de kolommen

- URL van de service die de kaartlaag levert (dvsourcelink): bijvoorbeeld: `[https://geodata.nationaalgeoregister.nl/bag/wms](https://geodata.nationaalgeoregister.nl/bag/wms.md)?`
- Naam van de kaartlaag (dvlaagnaam): Naam van de kaartlaag in de service (LET OP: case sensitive). Bijvoorbeeld _pand_
- Label in OpenWave (dvlabel): Label waaronder de laag in OpenWave is aan/uit te klikken. Bijvoorbeeld _BAG pand contouren_
- Volgnummer (dnvolgnr). Geeft aan in welke volgorde de kaartlagen in de legenda getoond worden
- Direct zichtbaar bij starten kaart (dlvisible). Aangevinkt betekent dat die laag in OpenWave direct bij het openen van het scherm getoond wordt
- Doorzichtigheid (dnopacity) is Percentage doorzichtigheid (geldt niet voor basislagen). Geen 0 invoeren!
- Vervaldatum (ddvervallen). Indien gevuld dan is de laag niet zichtbaar in de legenda van OpenWave-kaarten
- dlisbasislaag. Indien aangevinkt dan gaat het om een niet-transparante ondergrondkaart. Een van de basislagen dient de _direct zichtbaar optie_ aangevibkt te hebben
- WMS?. Indien aangevinkt dan wordt de laag geïnterpreteerd als WMS-laag (defaultwaarde), anders als WFS-laag
- Inloggegevens niet-openbare kaartlagen - Gebruikersnaam. Gebruikersnaam voor het inloggen op de niet-openbare kaartlaag
- Inloggegevens niet-openbare kaartlagen - Wachtwoord. Wachtwoord voor het inloggen op de niet-openbare kaartlaag. Het wachtwoord zal door de programmatuur encrypt worden en niet zichtbaar zijn in het detailscherm.
- Icoon WFS. Indien het een WFS kaartlaag betreft kan hier aangeven worden met welk icoon de punten op de kaart worden getoond. Keuze uit vierkant, rondje (default) of driehoek
- Kleur WFS. Indien het een WFS kaartlaag betreft kan hier aangeven worden met welke kleur de punten op de kaart worden getoond. Keuze uit alle mogelijke CSS kleuren uit de kleurenlijst. Via de schermknop naast dit veld kan genavigeerd worden naar de CSS-kleurlijst. Op deze pagina zijn voorbeelden te vinden van de mogelijke kleuren en hoe deze heetten. Indien het kleurveld leeggelaten wordt, zal de default kleurwaarde worden gebruikt: geel.

In de tabel zijn ook niet-transparante basislagen opgenomen:

- URL: `[https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0](https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0.md)`
  - layer: 'standaard'
  - label: 'BRT'
- URL: `[https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0](https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0.md)`
  - layer: 'grijs'
  - label: 'BRT Grijs'
- URL: `[https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0](https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0.md)`
  - layer: 'pastel'
  - label: 'BRT Pastel'
- URL: `[https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0](https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0.md)`
  - layer: 'water'
  - label: 'BRT Water'
- URL: `[https://service.pdok.nl/hwh/luchtfotorgb/wmts/v1_0](https://service.pdok.nl/hwh/luchtfotorgb/wmts/v1_0.md)`
  - layer: 'Actueel_ortho25'
  - label: 'Luchtfoto\'s'

De URL kan afwijken van bovenstaande.

### Waar zijn openbare WMS kaartlagen te vinden en hoe vindt men de URL?

Een van die plekken is het nationaal register: [http://nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/home](http://nationaalgeoregister.nl/geonetwork/srv/dut/catalog.search#/home.md).

Aan de hand van een voorbeeld wordt de procedure duidelijk. Aangezien hieronder niet onze eigen website beschreven wordt, kan het mogelijk in de praktijk iets anders gaan. Zoeken op bijvoorbeeld waterwegen.

In de rij mogelijkheden zoeken naar WMS-services. Een daarvan is bijvoorbeeld _NWB-vaarwegen PDOK_.
Doorklikken.

Nu verschijnen de mogelijkheden die de service biedt: zie de URL in onderstaand voorbeeld:

`[https://geodata.nationaalgeoregister.nl/nwbvaarwegen/wms](https://geodata.nationaalgeoregister.nl/nwbvaarwegen/wms.md)?`

### Hoe de kaartlaagnamen bij een URL te vinden?

Daarvoor plakt men de URL in de browser en zet direct daarachter _request=getCapabilities_.
In bovenstaand voorbeeld wordt dat: `[https://geodata.nationaalgeoregister.nl/nwbvaarwegen/wms?request=getCapabilities](https://geodata.nationaalgeoregister.nl/nwbvaarwegen/wms?request=getCapabilities.md)`.
Het resultaat is een xml-file met de ins en outs van de service.
Daarin zoekt men naar de ingang _Layer_. Die is vaak onderverdeeld in (sub)layers: (nog een laag layer binnen de eerste laag layer). Het gaat om layers met attribuut _queryable="1"_.
In het bovenstaande voorbeeld zouden twee mogelijkheden zichtbaar moeten zijn: kies bijvoorbeeld voor de Name _kmmarkeringen_. Dit is dus naam van de kaartlaag.

Gevonden URL en Kaartlaagnaam opnemen in OpenWave GeoKaartlagen en de waarde voor het OpenWave-label zelf bepalen, bijvoorbeeld: _Vaarwegen: Kilometermarkeringen_.

Start het kaartje en zoom in op een grote rivier en zet de laag aan. Voilà.

Andere voorbeelden (naam en URL):
kadastralekaart [https://geodata.nationaalgeoregister.nl/kadastralekaartv3/ows](https://geodata.nationaalgeoregister.nl/kadastralekaartv3/ows.md)?
pand [https://geodata.nationaalgeoregister.nl/bag/wms](https://geodata.nationaalgeoregister.nl/bag/wms.md)?

### OpenWave rapportage als kaartlaag

Zie [Rapportage publiceren als WMS laag](/docs/instellen_inrichten/rapportage-publiceren_als_wms-laag.md).
