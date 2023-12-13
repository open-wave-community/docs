# Scherm(kolom)definitie

Portal beheerportaal-NIEUW, onder kolom _Scherm- en Tegelbeheer_, tegels Schermkolomdefinitie.

Screenidentifiers:

- MDLC_getScreenColumnsRapportageList.xml en MDDC_getScreenColumnsRapportageDetail.xml
- MDLC_getScreenColumnsTabellenStandaardApiList.xml en MDDC_getScreenColumnsTabellenStandaardApiDetail.xml
- MDLC_getScreenColumnsTabellenOWApiList.xml en MDDC_getScreenColumnsTabellenOWApiDetail.xml

## Waar komt de kolominformatie van OpenWave lijst- filter en detail schermen vandaan

Elke lijst- filter-of detailscherm of standaardinsert-scherm heeft een eigen identifier. Voor de lijst- en detailschermen is deze identifier zichtbaar wanneer rechtsonder in het scherm op het in zacht grijs weergegeven regeltje met de versie-informatie wordt geklikt. Er verschijnt een ballonnetje met drie gegevens: screensource (aar of tbscreencolumns) en screenidentifier (een unieke xml-benaming voor elke scherm, bijv:_MDDC_getMilCodeBwlDetail.xml_) en de api-soort (sysstandaard of anderszins). Wanneer aan de voorkant een lijst binnen een blok van een detailscherm is opgenomen dan verschijnt rechtsonder in dat blok een info-icoontje waarmee de schermidentifier voor dat specifieke lijstje kan worden opgehaald. Screensource kan drie waarden hebben:

- **aar**. In dat geval komt de schermkolominformatie uit de api-zelf. Dit is het geval wanneer het programma constateert dat er geen gevuld afwijkend scherm (de kolom dvscreenxml) in de tabel tbscreencolumns is gevonden bij de getoonde screenidentifier. De waarde van die identifier zoekt het programma in de kolom dvscreenfilename van die tabel tbscreencolumns. Deze tabel wordt bij database-updates vanzelf van de mogelijke screenidentifiers voorzien. De gebruiker ziet het scherm zoals door Rem standaard uitgeleverd
- **tbscreencolumns**. De beheerder heeft zelf een scherm aangepast. In dit geval komt de schermkolominformatie wel uit de kolom dvscreenxml van tbscreencolumns waarbij de waarde van de kolom dvscreenfilename overeenkomt met de getoonde identifier. Deze kolom dvscreenxml is gevuld met een xml-string waarin alle kolommen en labels van het scherm zijn gedefinieerd (daarover gaat de rest van deze hoofdstukken). De gebruiker ziet een aangepast scherm. Ook als bij een update Rem zelf een gewijzigd scherm meelevert in de aar is dat niet zichtbaar: het zelf aangepaste scherm prevaleert.
- **fileserver**. Deze situatie kan alleen voorkomen in het lab van Rem Automatisering. Het programma zoekt op de fileserver naar een xml-file met de naam van de identifier indien zoeken binnen tbscreencolumns niets heeft opgeleverd. Deze xml-file bevat de scherminformatie op dezelfde manier als hierboven. De kolom _Tekst_ van instelling _Sectie: OWB en Item: FlexRootmap_ moet hiertoe gevuld zijn met een valide root en moet aangevinkt zijn. Voor rechten zie [Ophalen van fileshare](/probleemoplossing/programmablokken/toon_documenten_en_download/ophalen_van_fileshare.md).

Indien deze informatie wordt opgevraagd bij een **rapportlijst** dan zijn er twee mogelijkheden:

- De maker van het rapport heeft geen apart scherm gedefinieerd - dus de lijst is de exacte representatie van de SQL die aan het rapport ten grondslag ligt. In dat geval wordt als screensource de tekst _Automatisch gegenereerd_ getoond en als screenidentifier de groeps-en rapportnaam.
- Als er wel een scherm is gedefinieerd bij het definiëren van een rapport, dan bestaat er een kaart in tbscreencolumns met initieel in de kolom dvscreencolumns.dvdescription de naam van het rapport. In dit geval wordt als screensource de tekst _screencolumns_ getoond en als screenidentifier ook de groeps-en rapportnaam.

De screenidentifier voor de filteropties bij een lijst heeft dezelfde naam als die van de lijst met uitzondering van de prefix. Bij een lijst is dat MDLC*en bij de definitie van het filter MDFC*.

De screenidentifier voor een standaardinsert-of kopieerscherm begint in ieder geval met de prefix 'MDWC\_' en eindigt met '.xml'. Maar de exacte naam moet gezocht worden in de knopdefinitie bij de insertknop bij de betreffende tabeldefinitie (beheertegel _Tabellen Standaardapi_). Wanneer de action bij die insertknop is gedefinieerd als _startWizard_ en de eerste parameter heeft de waarde _insertSysStandardRow_ of _kopieerSysStandardRow_ dan staat in de tweede parameter de naam van het scherm dat gebruikt wordt voor de insert.

Paging voor de lijstschermen wordt geregeld door de instelling _Getal1_ van _Sectie: Paging en Item: Page_Size_ (defaultwaarde = 100).

## Aanpassen van standaard OpenWave schermen

De inlogger moet beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99 om de tabel met scherminformatie tbscreencolumns te benaderen.

In deze tabel zijn alle lijst-filter- en detailschermen gedefinieerd met een unieke scherm-identifier: de kolom dvscreenfilename. De uitgeleverde standaardversies van de schermen kunnen alhier desgewenst aangepast worden.
Aan de voorkant kan op dus op elk scherm rechtsonder de screenidentifier en `de klasse zichtbaar gemaakt worden. Indien:

- de klasse = systandard dan kan de screenidentifier opgezocht worden in het (nieuwe) beheerportaal onder de kolom _Scherm- en Tegelbeheertegel_ achter de tegel: _Schermkolomdefinitie tabellen standaard-api_. Bij de klasse systandard zijn alleen schermen met apinaam getsysstandardList, getsysstandardDetail, insertsysstandardrow of getSysStandardFilter gedefinieerd.
- anders, bij een andere waarde van de klasse, moet de screenidentifier opgezocht worden achter de tegel _schermkolomdefinitie tabellen OW-api_ Hier zijn veel verschillende apinamen mogelijk.

Naast alles lijst- en detail- en filter en insertschermen kunnen in deze tabel - maar hoeft niet - voor één of meer rapportages kaarten aangemaakt zijn teneinde de kolommen van die rapportage beter op te kunnen maken. Zie trigger _maak schermdefinitie_ bij [Rapportages](../rapportages.md). De rapportageschermen bevinden zich achter de tegel _Schermkolomdefinitie rapportages_. Alle schermen zijn hier van de klasse Reports met de api getReportResultList.

De tabel is en wordt gevuld met de updatescripts van databasewijzigingen. Schermen onder de SysStandard-klasse (lijst, detail, filter en insertscheremn) kunnen door functioneel beheerders worden aangemaakt: in dat geval moet het scherm opgeslagen worden in de kolom _Kolominformatie (dvscreenxml)_. Naar schermen die de klasse SysStandard hebben wordt verwezen vanuit de tabel tbsysstandardtable of vanuit tbsysstandardbutton. Onderaan de lijst van schermen bij klasse SysStandard is een wizardknop zichtbaar: _verwijder niet gekoppelde scherminformatie_. Hiermee wordt een lijst opgebouwd van schermen die 'zweven', dus die geen connectie hebben in een kaart van tbsysstandardtable of tbsysstandardbutton (tegel Tabellen Standaard-api).

Bestaande schermen (ongeacht de klasse) kunnen aangepast worden door met de knop _Haal Origineel_ onderaan het detailscherm van de schermdefinitie de schermopmaak binnen te halen in de kolom _Kolominformatie (dvscreenxml)_. Indien deze kolom dvscreenxml is gevuld, dan gaat die schermopmaak boven de oorspronkelijke aangeleverde schermopbouw in de AAR.. In de overzichtslijsten van de schermen is dit zichtbaar in het aangevinkt zijn van de kolom afwijkend scherm.

## De betekenis van de kolommen

Alle kolommen (behalve de niet muteerbare: zie hieronder) en knoppen zijn dan toegankelijk.

- **systeemcategorie**. Codetabel tbsysstandardcategorie (beheertegel _Sysstandaard categorieën_) om schermen naar eigen goeddunken in te delen.
- **Systeem**. Niet aanpasbaar. Indien aangevinkt dan kan Rem bij een systeemupdate het scherm overschrijven.
- **Klasse**. Niet muteerbaar. Is categorie ten behoeve van de indeling van de schermen. Loopt gelijk met de indeling van de API's.
- **API** Niet muteerbaar. Is de naam van de API die de scherminformatie verzamelt en verwerkt in een standaard gestructureerde xml-file richting front/end webserver die de pagina's verder opmaakt.
- **View/tabel**. Niet muteerbaar. De view- of tabelnaam die de data levert voor het scherm. Deze kolom is leeg indien het gaat om een rapportage. De data van een rapportage komen per definitie uit een zelf gedefinieerd SQL-statement.
- **Identifier scherm**. Niet muteerbaar. Dit is de unieke id van het scherm uitgedrukt als een betekenisvolle (xml)-filenaam. Ook deze is leeg indien het gaat om een rapportage.
- **Identifier rapport**. Niet muteerbaar. Een rapportage wordt geïdentificeerd door de dnkey van de tabel tbrapportages.
- **Toelichting** Vrij in te voeren. Wordt soms ook gevuld aangeleverd bijvoorbeeld in die situaties dat er meerdere schermvarianten zijn voor een bepaalde invoer-toepassing op grond van rechten of instellingen: zoals contactadressen.
- **Zoekkolommen**. Is alleen van toepassing voor lijstschermen. Indien het lijstscherm een zoekbox onderin vertoont, dan is het defaultgedrag van die zoekbox dat de ingevoerde waarde gezocht wordt op alle stringkolommen van de bijbehorende view/tabel. Dat zijn de kolommen waarvan de kolomnaam begint met 'dv'. Hier kan daarvan afgeweken worden door exact de string-kolommen te definiëren waarop gezocht mag worden. De kolommen moeten gescheiden worden door een puntkomma. Dus bijvoorbeeld: dvachternaam;dvvoorletters; Indien het wenselijk is dat ook op een datumkolom kan worden gezocht dan moet deze ook worden opgenomen. Een datumkolom begint met 'dd'. Een voorbeeld is dan _ddfataldatum;dvaanvraagnaam;dvobjstraat;dvobjplaats_.
- **Lijst automatisch in editmode** (dleditlist). Indien aangevinkt zal de lijst editable zijn voor die kolommen die zelf de tag `<edit>` op true hebben staan. De applicatie kan hier op inbreken indien de rechten niet toereikend zijn.
- **Excelknop onderaan lijst**. Indien aangevinkt zal linksonder op de betreffende lijst een Excel knop verschijnen, waarmee de hele lijst naar Excel kan worden geëxporteerd.
- **Default sortering**. Is alleen van toepassing voor lijstschermen. Een valide SQL sorteringsstatement kan hier worden opgegeven. De lijst wordt bij het opstarten hierop gesorteerd. Bijvoorbeeld 'ddfataledatum DESC'.
- **Detailscherm openen na insert**. Dit geldt alleen voor bepaalde schermen die door de interne OW-API worden benaderd. Het al of niet automatisch openen van een detailscherm na een insert bij een systandaardtabel is geregeld bij de definitie van de standaardtabel. Indien aangevinkt en het scherm is hieronder genoemd, dan zal na een insert het detailscherm automatisch openen.
  - nieuwe activiteit bij een omgevingzaak: tbscreencolumns.dvscreenfilename = _mdlc_geefomgactiviteitenoverzichtl.xml_
  - nieuwe overtreding bij een inspectietraject: tbscreencolumns.dvscreenfilename = _mdlc_geefonrechtmatighedenoverzicht.xml_
  - nieuwe bezwaar/beroep (deelzaak) : tbscreencolumns.dvscreenfilename = _mdlc_getbezwaarberoeplist.xml_
  - nieuwe SWF-ruimte: tbscreencolumns.dvscreenfilename = _mdlc_getswfruimtelist.xml_
  - nieuw inspectiebezoek bij een inspectietraject: tbscreencolumns.dvscreenfilename = _mdlc_geefinspbezoekoverzicht.xml_
  - nieuwe legesregel : tbscreencolumns.dvscreenfilename = _mdlc_geeflegesoverzicht.xml_
  - nieuwe projectlocatie : tbscreencolumns.dvscreenfilename = _mdlc_getzaakkadpercList.xml_
  - nieuw inspectietraject: tbscreencolumns.dvscreenfilename = _mdlc_geefinsptrajectoverzicht.xml_
  - nieuw advies: tbscreencolumns.dvscreenfilename = _mdlc_geefadviezenoverzicht.xml_
- **Editschuif automatisch aan**. Is alleen van toepassing voor detailschermen. Indien aangevinkt zal het openen van het betreffende scherm gebeuren met de editschuif op AAN ongeacht de default instelling (zie: [Edit-schuif](../editschuif.md)), tenzij de inlogger geen wijzigrechten heeft op dat scherm.
- **Blokvolgorde** Alleen van toepassing op detailschermen. Zonder de opmaak-xml van het scherm te veranderen (dus bij lege kolom dvscreenxml) kan hier een afwijkende volgorde van de blokken worden opgegeven. Zie hieronder onder kopje _blokvolgorde_
- **sql kopregel1, kopregel2** en **kopregel3**. Indien gevuld met een valide SQL-statement worden de resultaten van die statements gebruikt voor de drie kopregels van het scherm (de bestaande waardes worden hiermee overschreven). Aan de queries worden de volgende eisen gesteld:
  - het resultaat van een query ( dus de evaluatie van het select-statement) mag maar uit één kolom en één rij bestaan.
  - en de query moet met 'select' beginnen
  - en er mag GEEN puntkomma (';') in voorkomen (vanwege het gevaar voor SQL-injectie). In de statements kunnen twee variabelen worden gebruikt:
    - _:keyaccount_ zal worden vervangen door tbmedewerkers.dvcode van de inlogger
    - _{id}_ wordt vervangen met de dnkey van tbomgvergunning of tbhandhavingen of tbmilinrichtingen of tbovvergunningen of tbmilvergunningen wanneer het statement gebruikt wordt op achterliggende schermen van een zaak- of inrichtingportaaltegel en/of door de primary key van de lijst waar vanuit een detailscherm wordt aangeroepen.
- **Kolominformatie** (dvscreenxml). Indien gevuld wordt de informatie in deze kolom gebruikt om een afwijkend scherm op te maken. Met de trigger _Haal Origineel_ kan altijd het standaard uitgeleverde scherm worden opgehaald uit de aar (de openwave programmatuur) teneinde deze dus als afwijkend scherm aan te passen. Indien deze kolom leeg is, dan gebruikt het programma altijd de standaardversie van het scherm of rapport. Met F11 wordt de kolom weergegeven in een groot scherm met ondersteuning voor de xml-syntax. Met F11 kan nadien ook weer teruggekeerd worden naar normale modus. Voor de betekenis en gebruik van de xml-structuur in deze kolom zie:
  - [Scherminformatie voor lijstschermen en (dus ook) rapportages](./scherminformatie_voor_lijstschermen_en_rapportages.md)
  - [Scherminformatie voor detailschermen](./scherminformatie_voor_detailschermen.md).
  - [Scherminformatie voor filterblokken op lijstschermen](./scherminformatie_voor_filterblokken.md)
  - [Scherminformatie voor standaard insert- en kopieer](./scherminfomatie_voor_standaard_insertschermen.md)

## Blokvolgorde detailscherm

Achter de kolom blokvolgorde kan een afwijkende volgorde van de blokken van een detailscherm worden opgegeven. Op bloktitel gescheiden door een #. OpenWave kijkt hier alleen naar indien er voor het betreffende scherm GEEN afwijkend scherm is gedefinieerd in de kolominformatie (dvscreenxml).

### Een voorbeeld

Het detailscherm met identifier: MDDC_geefOmgActiviteitDetail.xml (onderdelen/activiteiten bij een omgevingzaak) kent standaard de volgende volgorde van bloktitels:

- Onderdeel
- DSO; identifiers
- Gebouw- en; gebruik;gegevens
- Voortgang
- Geldigheid
- Kosten
- ROEB
- DSO Specificaties

**LET OP:** indien een bloktitel twee of meer regels beslaat dan kan het zijn dat de werkelijke titel is voorzien van puntkomma's op de plek van een gedwongen regeleinde. Maar dat hoeft dus niet. Ook in het geval dat de titel te lang is voor de blokbreedte zal OpenWave een spatie gebruiken als regeleinde. De werkelijke titels zijn (vooral als het gaat over een titel die twee of meer regels beslaat) op te halen via de knop _haal originele scherminformatie_ op het detailscherm van een schermkolomdefinitie (beheerportaal): vergeet dan niet de ingelezen xml weer te verwijderen, anders is er sprake van een afwijkend scherm.

Om nu het blok DSO Specificaties niet als achtste, maar als tweede te tonen, waarbij de overige blokken hun plaats behouden, moet de kolom blokvolgorde (tbscreencolumns.dvblokvolgordedetail) gevuld worden met: _Onderdeel#DSO Specificaties_. Om alleen het blok DSO; identifiers niet als tweede, maar als achtste te tonen, moet de kolom blokvolgorde gevuld worden met: _Onderdeel#Gebouw- en; gebruik;gegevens#Voortgang#Geldigheid#Kosten#ROEB#DSO Specificaties#DSO; identifiers_.
De titels moeten gescheiden worden door een hekje: #
Verschrijvingen in de bloktitels worden genegeerd (het blok kan namelijk niet gevonden worden).

### Trigger linksonder

Met de knop _Haal Origineel_ op het detailscherm van een schermdefinitie kan indien:

- het gaat om een lijst- of detailscherm, of een filterscherm of een standaardinsert-scherm de in de programmatuur vastgelegde schermopbouw worden opgehaald.
- het gaat om een rapportage, de in de rapportdefinitie vastgelegde kolomvolgorde en benaming worden opgehaald.

In beide gevallen wordt de kolom _Kolominformatie (dvscreenxml)_ hiermee overschreven.

Met de wizardknop _verwijder niet gekoppelde scherminformatie_ (alleen bij schermen van klasse SysStandard) wordt een lijst opgebouwd van schermen die 'zweven', dus die geen connectie hebben in een kaart van tbsysstandardtable of tbsysstandardbutton (tegel Tabellen Stanaard-api) en dus nooit gebruikt zullen worden. Met de wizard kan de lijst opgeschoond worden.

## Meer informatie Scherm(kolom)definitie

- [Iconenlijst](./iconenlijst.md)
- [Scherminformatie voor getFlexTree schermen](./scherminfomatie_voor_getflextree_schermen.md)
- [Scherminformatie voor standaard insert- en kopieer](./scherminfomatie_voor_standaard_insertschermen.md)
- [Scherminformatie voor detailschermen](./scherminformatie_voor_detailschermen.md)
- [Scherminformatie voor filterblokken op lijstschermen](./scherminformatie_voor_filterblokken.md)
- [Scherminformatie voor lijstschermen en (dus ook) rapportages](./scherminformatie_voor_lijstschermen_en_rapportages.md)
- [Sorteren van lijstschermen](./sorteren_van_lijstschermen.md)
- [Verversen en Positioneren](./verversen_en_positioneren.md)
