# Kaart

## Verplichte instellingen

- De instelling _Sectie: Programma_ en _Item: ToonKaart_ moet aangevinkt zijn. Indien een externe kaartviewer wordt gebruikt moet in _Getal2_ van deze instelling de opstart zoomwaarde genoteerd worden. Bij de standaardkaart is dit optioneel (defaultwaarde = 14).
- _Getal2_ van _Sectie: WaSe-Publicatielijst_ en _Item: Map_def_lat_ moet gevuld zijn met de y-coördinaat (in rijksdriehoek) van het centrum waaromheen de kaart moet starten indien dit gegeven niet uit de locatiegegevens gehaald kan worden en uit de facultatieve instellingen hieronder.
- _Getal2_ van _Sectie: WaSe-Publicatielijst_ en _Item: Map_def_lon_ moet gevuld zijn met de x-coördinaat (in rijksdriehoek) van het centrum waaromheen de kaart moet starten indien dit gegeven niet uit de locatie gegevens gehaald kan worden en uit de facultatieve instellingen hieronder.

### Algemene Kaart

De algemene kaart is een interne kaart oproepbaar vanuit de tegel _Kaart_ op het openingsscherm ([Tegel Kaart](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_kaart.md)).

De kaart wordt gecentreerd rond de ingestelde Map_def_Lon en Map_def_lat (zie hierboven verplichte instellingen).

Op deze kaart kunnen externe WMS/WFS lagen getoond worden, waaronder kaartlagen die met OpenWave Rapportages zijn gemaakt. Zie:
[Geo-WMS/WFS lagen](/instellen_inrichten/geowms-lagen.md) en [Rapportage als WMS-laag](/instellen_inrichten/rapportage-publiceren_als_wms-laag.md).

De punten op deze kaart kunnen worden geselecteerd (aangewezen met de muis) waarna in een box de informatie die bij het punt hoort zichtbaar wordt.

Met de combinatie Ctrl-toets en Muis-slepen kan een rechthoek om één of meer punten worden getrokken, waarvan de informatie van al deze punten rechtsonder in een box wordt getoond.

## Zaak/locatie gebonden kaart: Interne of Externe kaartviewer

De zaak/locatie gebonden kaarten die oproepbaar zijn met de kaartknop op diverse schermen, worden gecentreerd rondom het locatie adres van de betrokken zaak, inrichting of projectlocatie (tbzaakkadperc).

Indien kolom _Info_ van _Sectie: Programma Item: Toonkaart_ een gevulde waarde heeft dan beschouwt OpenWave die gevulde waarde als een URL van een externe kaartviewer die geopend moet worden als de gebruiker op de _toon-kaart_ knop klikt vanuit een detailscherm of een portal.

Wanneer die kolom _info_ niet is gevuld, dan wordt de standaardkaart (interne kaartviewer) van OpenWave aangeroepen.

### Zaak/locatie gebonden kaart: Externe kaartviewer

Indien kolom _Info_ van _Sectie: Programma Item: Toonkaart_ een gevulde waarde heeft dan beschouwt OpenWave die gevulde waarde als een URL die geopend moet moet worden als de gebruiker op de toon-kaart knop klikt vanuit een detailscherm of een portal. In die URL-string zal OpenWave eerst de variabelen:

- %x% vervangen door de x-coördinaat van het bijbehorende locatie adres
- %y% vervangen door de y-coördinaat van het bijbehorende locatie adres
- %zoom% vervangen door _Getal2_ van _Sectie: Programma Item: Toonkaart_.

Voorbeeld:

Indien kolom _Info_ van _Sectie: Programma Item: Toonkaart_ is gevuld met:

<https://kaart.pdok.nl/api/api.html?mloc=%x%,%y%&mt=mt3&loc=%x%,%y%&zoom=%zoom%&tekst=Locatie:%3C/BR%3E%x%,%y%>
en de kolom _Getal2_ van die instelling heeft de waarde 12

en de gebruiker staat op op een zaak met locatie adres coördinaten 172706, 449311

dan zal OpenWave de volgende URL in een nieuw tabblad openen:

<https://kaart.pdok.nl/api/api.html?mloc=172706,449311&mt=mt3&loc=172706,449311&zoom=12&tekst=Locatie:%3C/BR%3E172706,449311>

### Zaak/locatie gebonden kaart: Interne kaartviewer (standaardkaart) kleuren en layers

De gegevens die worden getoond bij de interne standaardkaart zijn afhankelijk vanuit welke situatie de knop _Toon Kaart_ wordt aangeroepen:

Een polygoon wordt als lijn getoond indien het beginpaar (x,y) niet overeenkomt met het eindpaar.

De kleuren moeten opgegeven worden conform de CSS benamingen. Zie `[http://www.w3schools.com/cssref/css_colors.asp](http://www.w3schools.com/cssref/css_colors.asp.md)`
**LAYER 1** (staat default aangevinkt): locatie zaak/inrichting/object.

- Vanuit een locatie (tbperceeladressen):
  - punt en polygoon van locatie adres in de CSS-kleur gedefinieerd door kolom _tekst_ van de instelling _Sectie: Programma en Item: KaartCsscolornamePerceel_. Default: rood.
- Vanuit een zaakportaal of detailscherm van een zaak:
  - punt en polygoon van onderliggende locatie adres (kleur zie hierboven). In legenda onder aanvinkvak: locatie zaak/inrichting
  - polygoon van zaak zelf in de CSS-kleur gedefinieerd door kolom _tekst_ van de instelling _Sectie: Programma en Item: KaartCsscolornameHoofdzaak_ Default: Salmon.
  - punt en polygoon van de hoofdprojectlocatie (alleen omgeving en handhavingen) wanneer de punt/polygoon van de locatie (tbperceeladressen) ontbreken. Kleur conform die van bovenliggende zaak.
- Vanuit een projectlocatie (tbzaakkadperc):
  - punt en polygoon van de projectlocatie adres in rood.
- Vanuit een inrichting portaal of detailscherm van een inrichting:
  - punt en polygoon van onderliggende locatie adres (kleur zie hierboven).
  - polygoon van inrichting zelf in de CSS-kleur gedefinieerd door kolom _tekst_ van de instelling _Sectie: Programma en Item: KaartCsscolornameInrichting_ Default: Salmon. In legenda onder aanvinkvak: locatie zaak/inrichting)
- Vanuit een detailscherm van een objectregistratie bij een inrichting
  - punt en polygoon van bovenliggende locatie adres (kleur zie hierboven).
  - polygoon van inrichting zelf (kleur zie hierboven).
  - Indien vanuit tabel:
    - tbmilopslag
      *vlak en punt met de kleur gedefinieerd in tbmilrubriek (*beheer: inrichtingenbeheer, kolom: Kenmerken, tegel: Milieurubrieken*) waaraan de opslag/voorz. kaart is gekoppeld. Default: Purple.
      - gevaar/hindercirkel met de kleur gedefinieerd in tbmilomsradius (_beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieucirkels_) waaraan de opslag/voorz. kaart is gekoppeld. Default: Purple.
    - tbmilemwater
      *vlak en punt met de kleur gedefinieerd in tbmilrubriek (*beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieurubrieken*) waaraan de waterlozingskaart via de codetabel tbmilsrtlozing (*Inrichtingenbeheer, tegel: Soort waterlozing*) is gekoppeld. Default: Aqua.
      - gevaar/hindercirkel met de kleur gedefinieerd in tbmilomsradius (_beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieucirkels_) waaraan de waterlozingskaart is gekoppeld. Default: Aqua.
    - tbmilstal
      *vlak en punt met de kleur gedefinieerd in tbmilrubriek (*beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieurubrieken*) waaraan de stal is gekoppeld. Met de kolom *Tekst* van de instelling *Sectie: Inrichtingen en Item: DefaultCodeRubriekStal* kan een default rubriek worden toegekend aan een stal. De *Tekst* verwijst hier naar de kolom dvcode van tbmilrubriek. Defaultkleur: Green.
      - gevaar/hindercirkel met de kleur gedefinieerd in tbmilomsradius (_beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieucirkels_) waaraan de stalkaart is gekoppeld. Default: Green.
    - tbmilemlucht
      *vlak en punt met de kleur gedefinieerd in tbmilrubriek (*beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieurubrieken*) waaraan de luchtemissiekaart is gekoppeld. Met de kolom *Tekst* van de instelling *Sectie: Inrichtingen en Item: DefaultCodeRubriekLucht* kan een default rubriek worden toegekend aan een luchtemissiepunt. De *Tekst* verwijst hier naar de kolom dvcode van tbmilrubriek. Defaultkleur: Blue.
       - gevaar/hindercirkel met de kleur gedefinieerd in tbmilomsradius (_beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieucirkels_) waaraan de luchtemissiekaart is gekoppeld. Default: Blue.
    - tbhorontheffingen (mist dddatum groter of gelijk vandaag)
      *vlak en punt met de kleur gedefinieerd in tbmilrubriek (*beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieurubrieken*) waaraan de ontheffingskaart is gekoppeld. Defaultkleur: Purple.
       - gevaar/hindercirkel met de kleur gedefinieerd in tbmilomsradius (_beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieucirkels_) waaraan de ontheffingskaart is gekoppeld. Default: Purple.
    - tbmilasbest
      *vlak en punt met de kleur gedefinieerd in tbmilrubriek (*beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieurubrieken*) waaraan de asbestkaart is gekoppeld. Met de kolom *Tekst* van de instelling *Sectie: Inrichtingen en Item: DefaultCodeRubrieAsbest* kan een default rubriek worden toegekend aan de asbestkaart. De *Tekst* verwijst hier naar de kolom dvcode van tbmilrubriek. Defaultkleur: Goldenrod.
       - gevaar/hindercirkel met de kleur gedefinieerd in tbmilomsradius (_beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieucirkels_) waaraan de asbestkaart is gekoppeld. Default: Goldenrod.
    - tbmildiversen
      *vlak en punt met de kleur gedefinieerd in tbmilrubriek (*beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieurubrieken*) waaraan de diversen-kaart via de codetabel tbmilsrtdivers (*Inrichtingenbeheer, tegel: Milieu gegevenssoort*) is gekoppeld. Default: Purple.
      - gevaar/hindercirkel met de kleur gedefinieerd in tbmilomsradius (_beheer: Inrichtingenbeheer, kolom: Kenmerken, tegel: Milieucirkels_) waaraan de diversen-kaart is gekoppeld. Default: Purple.
    - tbmilopslagevcontour (REV: kan gevuld zijn indien de bovenliggende opslagkaart een REV: referentiecontour is).
    - vlak en punt met de kleur gedefinieerd in tbrevevcontour (_beheer: Inrichtingenbeheer, kolom: REV, tegel: ev-contouren_) waaraan de evcontour-kaart is gekoppeld. Default: Purple.
    - gevaar/hindercirkel idem dito. Default: Purple.
    - tbmilbklkwetsbgebloc (REV: kan gevuld zijn indien de bovenliggende inrichting een REV: locatieactiviteit is).
      - vlak (alleen vlak, geen punt of cirkel) met de kleur gedefinieerd in tbrevkwestbgebloc (*beheer: Inrichtingenbeheer, kolom: REV, tegel: Kwetsbare gebouwen/locaties\*) waaraan de gebouw/locatie-kaart is gekoppeld. Default: Silver.

**LAYER 2** (staat default NIET aangevinkt): alle punten en vlakken (lijnen) van opslag/voorz- en stal- en kwetsbare gebouwen bij de geselecteerde inrichting.

**LAYER 3** (staat default NIET aangevinkt): alle overige emissiepunten/vlakken bij de geselecteerde inrichting.

**LAYER 4** (staat default NIET aangevinkt): alle hinder- en gevaarcirkels bij de geselecteerde inrichting.

**LAYER 5** (staat default NIET aangevinkt): alle kwetsbare gebouwen en kwetsbare locaties bij de geselecteerde inrichting.

Indien de instelling **Sectie: Inrichtingen Item: Kaartlayers2en3** is aangevinkt en de gebruiker start de kaart vanuit een inrichting, dan worden
laag e en laag 3 automatisch aangevinkt.

Polygonen worden op drie manieren ondersteund (LET OP: de kaart wordt altijd gecentreerd rondom het punt, dus als het polygoon niet zichtbaar is, is deze mogelijk te ver verwijderd van de x en y van het punt):

^ Invoer als LineString (lijn): het beginpaar van de coördinatenreeks is ongelijk aan het eindpaar.

- Invoer als multi-point in paren van x-y coördinaten (rijksdriehoek), waarbij x en y worden gescheiden door een komma. Het scheidingsteken tussen twee paren is een spatie (bijvoorbeeld: 145601,424980 145594,424975 145601,424980). Begin- en eindpaar zijn gelijk.
- Invoer als PosList van LineairRing x-y-z coördinaten (rijksdriehoek). Alle waarden gescheiden door spatie (bijv. 145601.935 424980.489 0.0 145594.922 424975.594 0.0 145601.935 424980.489 0.0). Begin- en eindpaar zijn gelijk.
  Naast de Geo-gegevens uit OpenWave zelf kunnen ook lagen uit andere Geo-gegevensbronnen als lagen op de kaart worden geprojecteerd. Deze lagen moeten worden gedefinieerd in de beheertabel tbgeowms zie [Geowms-lagen](/instellen_inrichten/geowms-lagen.md).

#### Facultatieve instellingen bij standaardkaart

- _Getal2_ van _Sectie: WaSe-Publicatielijst_ en _Item: Map*def_lat + '*' + gemeenteid_ moet gevuld zijn met de **y-coördinaat** (in rijksdriehoek) van het centrum van bedoelde **gemeente** waaromheen de kaart moet starten indien dit gegeven niet uit de locatie gegevens gehaald kan worden. Voorbeeld: met Item = Map_def_lat_0450 wordt dus aangegeven dat het gaat om de y-coördinaat van het centrum van Uitgeest.
- _Getal2_ van _Sectie: WaSe-Publicatielijst_ en _Item: Map*def_lon + '*' + gemeenteid_ moet gevuld zijn met de**x-coördinaat** (in rijksdriehoek) van het centrum van bedoelde **gemeente** waaromheen de kaart moet starten indien dit gegeven niet uit de locatie gegevens gehaald kan worden. Voorbeeld: met Item = Map_def_lon_0450 wordt dus aangegeven dat het gaat om de x-coördinaat van het centrum van Uitgeest.
- _Getal1_ van _Sectie: OWB_ en _Item: Kaartgrootte_ kan de waarde 1 (default) of 2 bevatten. Bij 2 worden de kaarten in opgestart met maximale schermgrootte. Bij 1 met de minimale afmetingen.
- _Aanvinkvakje_ van _Sectie: Inrichtingen en Item: Kaartlayers2en3_. Indien aangevinkt zijn bij het opstarten van de interne kaart vanuit de inrichtingstabel de layers 2 en 3 direct geopend (opslag, stallen en overige emissiepunten).

#### Triggers bij standaardkaart

- De legenda knop rechtsboven opent een schermpje waarmee interne kaartlagen aan- en uitgevinkt kunnen worden. Onder de noemer overlay worden de externe kaartlagen opgesomd.
- Een muisklik op een punt, vlak of cirkel - indien het gaat om Geodata uit OpenWave (en dus niet om een externe kaartlaag) - opent een ballonnetje met summiere informatie over dat Geo-object.
