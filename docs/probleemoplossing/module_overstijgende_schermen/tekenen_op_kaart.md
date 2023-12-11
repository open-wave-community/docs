# Tekenen op Kaart

Vanuit de detailschermen van de locatie, inrichting, omgeving, handhaving, milieu/gebruik, horeca en APV/Overig, en ook vanuit de detailschermen van de inrichting registratie-onderdelen als vee, opslag, asbest, geluid e.d. kan in het lijstmenu gekozen worden voor **Tekenen op kaart**.
Er zijn twee mogelijkheden: Indien op de betreffende detailkaart de kolom polygoon leeg is, dan verschijnt in het lijstmenu de optie: _Teken vlak op kaart_. Als de puntcoördinaten X, Y leeg zijn dan verschijnt in het lijstmenu de optie: _wijs X- en Y-coördinaat op kaart aan_. Beide opties tegelijk zijn ook mogelijk.

Het programma opent de kaart. Er is geen Geo-informatie zichtbaar van Geo-objecten die bij de betreffende zaak/inrichting/object horen. Wel is het menu met Geo-WMS-lagen te gebruiken. Indien:

- **Aanwijzen van punt**. De inlogger kan het blauwe aanwijsbolletje fixeren door te klikken. Het punt wordt geel. Indien daarna op de knop _Opslaan_ onder aan de pagina wordt geklikt dan zullen de x- en de y-coördinaat in de betreffende kolommen van de detailkaart worden opgeslagen.
- **Teken lijn op kaart**. Alleen bij de opslagkaarten bij inrichtingen. Met het blauwe bolletje kan een lijn getekend worden in rechte gele lijnen, die geen gesloten vlak vormen. Dubbelklik op eerste punt van de lijn, en dubbelklik op laatste punt van de lijn om af te sluiten. Indien daarna op de knop _Opslaan_ onder aan de pagina wordt geklikt dan worden de lijn-coördinaten in de betreffende kolom van de detailkaart opgeslagen.
- **Tekenen van vlak**. De inlogger ziet onderaan een radiobutton-optie: _pand selecteren_ of _vlak tekenen_. De radiobutton staat ingesteld op de waarde van _Getal1_ van de instelling _Sectie: OWB en Item: SelecteerVlakInKaart_. De waarde 1 (default instelling) betekent pand selecteren, 2 betekent zelf tekenen. Het vlak wordt opgeslagen als string van paren van x-, y-coördinaten (rijksdriehoek), waarbij x en y worden gescheiden door een komma. Het scheidingsteken tussen twee paren is een spatie (bijvoorbeeld: _145601,424980 145594,424975 145601,424980)._
  - **Pand selecteren**. Hiervoor moet een (WFS) laag met BAG-panden aangezet worden. Zie [Geo-WMS/WFS lagen](/docs/instellen_inrichten/geowms-lagen.md). Slimmer is om deze laag default aan te zetten. De inlogger kan op een pand klikken en:
    - onderaan het scherm wordt direct de oppervlakte zichtbaar.
    - Indien daarna op de knop _Opslaan_ onder aan de pagina wordt geklikt dan worden de polygoon-coördinaten van het pand in de betreffende kolom van de detailkaart opgeslagen.
  - **Zelf tekenen**. Met het blauwe bolletje kan een vlak getekend worden in rechte blauwe lijnen door op de hoekpunten te klikken. Door het vlak te sluiten worden de blauwe lijnen zichtbaar als gele lijnen.
    - Onderaan het scherm wordt direct de oppervlakte zichtbaar.
    - Indien daarna op de knop _Opslaan_ onder aan de pagina wordt geklikt dan worden de polygoon-coördinaten van het getekende vlak in de betreffende kolom van de detailkaart opgeslagen.

Indien vanuit inrichting of onderliggende tabellen (stallen, opslag) gekozen wordt voor tekenen van punt of vlak op
kaart, dan laat het OpenWave-kaartje– als steun- het punt van het locatieadres zien en – indien aanwezig – de contour van de inrichting.
