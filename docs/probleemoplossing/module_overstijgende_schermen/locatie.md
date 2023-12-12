# Locatie detailscherm

Screenidentifier: MDDC_geefLokatieAdres.xml.

Detailpagina van Locatie op basis van vwfrmlokaties.

Kan worden aangeroepen vanuit de tegel _Locaties_ op het openingsportaal en met de knoppen _Locatie_ op de zaakportalen, het archiefportaal en het inrichtingsportaal en bijbehorende detailschermen.

## Error

Het scherm geeft een foutmelding indien:

- er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/instellen_inrichten/schermdefinitie/README.md)) die niet valide is
- de inlogger behoort tot een rechtengroep die geen kijkrechten heeft op locaties (locatieadressen zichtbaar bij hoofdrechtengroep).

### Muteren

De kolommen van de view afkomstig van de tabel tbperceeladressen kunnen gemuteerd worden indien:

- de inlogger behoort tot een rechtengroep die wijzigrechten heeft op locaties (locatieadressen zichtbaar bij hoofdrechtengroep)
- en de editschuif aan staat
- en - indien de inlogger lid is van een [compartiment](/instellen_inrichten/compartimenten.md) - dan moet de betreffende gemeente in dat compartiment vallen. Let op: een gemeente kan in meerdere compartimenten voorkomen.

Uitzondering is de kolom **Verificatiedatum BAG** die automatisch gevuld/leeggemaakt wordt door de trigger _synchroniseer met BAG_ of vanuit de operations (portaal Operations) Import BAG-extract en Import BAG-mutaties.

De kolommen _straat, woonplaats en gemeente_ zijn afkomstig van andere tabellen en kunnen hier niet worden gemuteerd.

### Triggers knoppen linksonder

- Toon kaart:
  - is altijd zichtbaar
  - is disabled indien de puntcoördinaten op het locatiescherm leeg zijn.
- Synchroniseer met BAG (zie [BAG bevraging](/probleemoplossing/programmablokken/bag_bevraging.md)):
  - is zichtbaar en enabled indien:
    - de instelling _Sectie: KoppelingBAG_ en _Item: Methode_ en _Tekst = StUF-310_ bestaat en is aangevinkt
    - en de inlogger behoort tot een rechtengroep die BAG-rechten heeft op locaties (locatieadressen BAG bij hoofdrechtengroep: tbrechten.dldpclbag)
    - en de instelling _Sectie: KoppelingBAG_ en _Item: Ontvangstadres_ bestaat en kolom _Tekst_ is gevuld met het endpoint voor beantwoordensynchronevraag
    - en de instelling _Sectie: KoppelingBAG_ en _Item: HTTPSoapAction_tgoLv01_ bestaat en kolom _Tekst_ is gevuld met `[http://www.egem.nl/StUF/sector/bg/0310/tgoLv01](http://www.egem.nl/StUF/sector/bg/0310/tgoLv01.md)`
    - en de stuurgegevens (kolom _Tekst_) bij _Sectie: KoppelingBAG op Items: ontvanger_applicatie en ontvanger_organisatie en zender_applicatie en zender_organisatie_ zijn gevuld
    - en - indien de inlogger lid is van een compartiment - dan moet de betreffende gemeente in dat compartiment vallen.

### Triggers rechtsboven in menu opties

- Teken vlak op kaart:
  - Zichtbaar en enabled indien:
    - de inlogger behoort tot een rechtengroep die wijzigrechten heeft op locaties (locatieadressen zichtbaar bij hoofdrechtengroep)
    - en indien de kolom waarin de polygoon coördinaten worden opgeslagen nog leeg is
    - en - indien de inlogger lid is van een compartiment - dan moet de betreffende gemeente in dat compartiment vallen.
- Wijs x- en y-coördinaat aan op kaart:
  - Zichtbaar en enabled indien:
    - de inlogger behoort tot een rechtengroep die wijzigrechten heeft op locaties (locatieadressen zichtbaar bij hoofdrechtengroep)
    - en indien de kolommen x- en y-coördinaat beide nog leeg zijn
    - en - indien de inlogger lid is van een compartiment - dan moet de betreffende gemeente in dat compartiment vallen.

### Triggers in scherm

- Knop **Ga naar ruimtelijke plannen** ([http://www.ruimtelijkeplannen.nl](http://www.ruimtelijkeplannen.nl.md)) op grond van adresgegevens (dus niet op grond van het bestemmingsplannummer of naam):
  - Altijd zichtbaar en enabled.

### De betekenis van de belangrijkste kolommen

- **identificatiecode** (dvidentificatiecode): Deze kolom wordt zowel gebruikt voor de (BAG) verblijfsobject-identificatie als voor ligplaats- en standplaatsidentificatie. Deze identificatiecode bestaat uit de viercijferige gemeentecode volgens GBA tabel 33, gevolgd door een tweecijferige objecttypering en een voor de registrerende gemeente 10-cijferig uniek volgnummer (met voorloopnullen). De objecttypering kan zijn:
  - 01 - verblijfsobject (LET OP: Bij BAG-verificatie wordt altijd gevraagd naar verblijfsobject!!!)
  - 02 - ligplaats
  - 03 - standplaats
  - 10 - pand
  - 20 - nummeraanduiding
  - 30 - openbare ruimte
- **Pand-identificatie** (dvbagidentcode_2). Kan worden gevuld bij Operations (portaal Operations) _Import BAG-Extract_ en _Import BAGmutaties_ indien het gaat om een verblijfsobject.
- **Nummeraanduiding-identificatie** (dvbagidentcode_3). Wordt gevuld bij Operations (portaal Operations) _Import BAG-Extract_ en _Import BAGmutaties_
- **BAG-verificatiedatum** (ddcontrolebag): Wordt gevuld met de datum van handeling wanneer een BAG-verificatie gelukt is. Wordt leeggemaakt wanneer een BAG-verificatie mislukt
- **Vervaldatum** (ddvervaldatum). Indien gevuld dan kan het adres niet meer als locatie worden gekozen bij het aanmaken van een nieuwe zaak of inrichting. Kan worden gevuld bij Operations (portaal Operations) _Import BAG-Extract_ en _Import BAGmutaties_
- **X- en Y-coördinaat**. Invoer in rijksdriehoekcoördinaten in gehele getallen
- **Polygoon**. Wordt op twee manieren ondersteund:
  - invoer als multipoint in paren van x-y coördinaten (rijksdriehoek), waarbij x en y worden gescheiden door een komma. Het scheidingsteken tussen twee paren is een spatie (bijvoorbeeld: _145601,424980 145594,424975 145601,424980)_
  - invoer als PosList van LineairRing x-y-z coördinaten (rijksdriehoek). Alle waarden gescheiden door spatie (bijv. _145601.935 424980.489 0.0 145594.922 424975.594 0.0 145601.935 424980.489 0.0_)
- **Bestemmingplan**. De dropdownlist toont een lijst uit tbbestemmingsplannen (portaal Zaakbeheer) die niet vervallen zijn en waarbij de gemeente-id leeg is OF overeenkomt met die van het het locatieadres. Bij geldend worden alleen die bestemmingsplannen getoond met de eigenschap dlinvoorbereiding = 'F'
- **Onbekend adres? (Aangevinkt dan wordt adres gebruikt voor zaken op onbekend BAG-adres)**. Het veld geeft aan of de locatie als een onbekend adres moet worden gezien. Daarmee wordt bedoelt het perceeladres/locatie die (vaak per openbareruimte/straat) gezien wordt als het adres om zaken/inrichtingen op aan te maken die niet op een specifiek huisnummer plaatsvinden. Voor de aangemaakte omgevings- en handhavingszaken en inrichtingen op deze locatie kan er in het betreffende portaal een hoofdprojectlocatie worden aangemaakt via de tegel _Projectlocaties\ Kadastrale percelen_ om de locatie nader te duiden met coördinaten of adresbeschrijving. In de koptekst van het zaak/inrichtingportaal zal dan de omschrijving van de hoofdprojectlocatie te zien zijn (kopregel 3) in plaats van de reguliere adresgegevens.
