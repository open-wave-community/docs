# Upload document

Met de knop _Upload_ op de detailschermen van omgeving, inrichting, APV/overig en handhaving, alsmede vanuit de advies en inspectie detailschermen kunnen met een wizard een of meer documenten aangewezen worden en vervolgens geüpload naar fileshare of DMS.

De uploadfunctie kan ook door een apparaat of automatisch proces worden aangeroepen (bijlagen van OLO). Zie [Upload vanuit automatisch proces](/probleemoplossing/programmablokken/upload_vanuit_automatisch_proces.md).

De uploadfunctie kan ook worden aangeroepen vanuit de [Toon documenten en download](/probleemoplossing/programmablokken/toon_documenten_en_download.md) met de **VerplaatsNaarDMS-knop**. Zichtbaar en enabled in de hybride situatie dat zowel van de fileserver gebruikt wordt gemaakt als van een DMS onder StUF zaak/DMS. De inlogger kan een document dat op de fileserver staat en waar de gele balk op staat, met deze knop - na invulling van verplichte metadata - in het DMS plaatsen (mits de bovenliggende zaak een zaakidentificatienummer heeft). Het betrokken fileserver-document daarbij wordt verplaatst naar een kopiemap: zie instelling kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS en Item: MapKopieVerplaatsteFiles_.

De bestandnamen van de up te loaden files mogen **niet groter dan 500 tekens** zijn.

## Rechten

- De gebruiker moet lid zijn van een rechtengroep die het recht: _uploaden en creëren van documenten_ heeft voor de betreffende module (omgeving, APV/overig, inrichting, bouw/sloop, handhaving en milieu/gebruik), en
- de zaak of inrichting mag niet geblokkeerd zijn:
  - voor uploads vanuit een advieskaart en vanuit een bezwaar/beroepskaart geldt hierbij dat gekeken wordt naar de blokkering van de onderliggende zaak
  - voor uploads vanuit een inspectiekaart geldt dat de zaak geblokkeerd is indien één van onderstaande items waar is:
    - de afgerond datum van de inspectietrajectkaart is gevuld
    - de instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ is NIET aangevinkt (of bestaat niet) en de blokkering van de onderliggende zaak is WEL gevuld.

### Upload waar naartoe?

- Indien de zaak/inrichting, waarbij de upload plaatsvindt, NIET valt onder een [compartiment](/instellen_inrichten/compartimenten.md) dan:
  - indien de instelling _Sectie: Documenten_ en _Item: OphalenViaFileserver_ aangevinkt is en ook de instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_ aangevinkt is dan zal de uploadwizard aan de gebruiker vragen waar de upload geplaatst moet worden (fileshare OF DMS). Indien er maar één van deze instellingen is aangevinkt wordt deze vraag niet gesteld
  - indien _OphalenViaDMS_ aangevinkt is, dan moet ook de instelling aangevinkt staan met _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ en _Tekst = StUF-ZAKEN 310 of CMIS 1.0_.
- Indien de zaak/inrichting WEL valt onder een compartiment dan:
  - indien de kolom _documenten opslag fileserver_ op de betreffende compartimentskaart (beheerportaal-Nieuw) aangevinkt is en ook de kolom _documenten opslag DMS_ aangevinkt is dan zal de uploadwizard aan de gebruiker vragen waar de upload geplaatst moet worden (fileshare OF DMS). Indien er maar één van deze instellingen is aangevinkt wordt deze vraag niet gesteld
  - indien de kolom _documenten opslag DMS_ aangevinkt is, dan moet ook de de kolom _dms methode_ op die compartimentskaart gevuld zijn met StUF-ZAKEN 310 of CMIS 1.0.

Zie schema [Schema Upload naar welke mappen/endpoints](/probleemoplossing/programmablokken/upload_document/schema_welke_mappen_endpoints.md).

### Is aanvullende (meta)-informatie verplicht per geüpload document?

Onderstaande gegevens zijn vooralsnog alleen zinvol bij opslag in een DMS met StUF-ZAKEN 310 (zaak/DMS koppeling).

- Indien de zaak/inrichting, waarbij de upload plaatsvindt, NIET valt onder een compartiment dan:
  *het verplichten per uploaddocument van een documenttype is afhankelijk van het aangevinkt zijn van de instelling *Sectie: KoppelingDOCNAARDMS* en*Item: DocumenttypeVerplicht\*
  - het verplichten per uploaddocument van een **Titel** is afhankelijk van het aangevinkt zijn van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: TitelVerplicht_
    *het verplichten per uploaddocument van een **Status** is afhankelijk van het aangevinkt zijn van de instelling *Sectie: KoppelingDOCNAARDMS* en*Item: StatusVerplicht\*
  - het verplichten per uploaddocument van een **Vertrouwelijkheidsduiding** is afhankelijk van het aangevinkt zijn van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: VertrouwelijkheidVerplicht_
  - het verplichten per uploaddocument van een **Auteur** is afhankelijk van het aangevinkt zijn van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: AuteurVerplicht_.
- Indien de zaak/inrichting, waarbij de upload plaatsvindt, WEL valt onder een compartiment dan:
  *het verplichten per uploaddocument van een **Documenttype** is afhankelijk van het aangevinkt zijn van de kolom*Documenttype verplicht bij upload\* op de betreffende compartimentskaart (beheerportaal-Nieuw)
  - het verplichten per uploaddocument van een **Titel** is afhankelijk van het aangevinkt zijn van de kolom _Titel verplicht bij upload_ op de betreffende compartimentskaart (beheerportaal-Nieuw)
    *het verplichten per uploaddocument van een **Status** is afhankelijk van het aangevinkt zijn van de kolom*Status verplicht bij upload\* op de betreffende compartimentskaart (beheerportaal-Nieuw)
  - het verplichten per uploaddocument van een **Vertrouwelijkheidsduiding** is afhankelijk van het aangevinkt zijn van de kolom _Vertrouwelijkheid verplicht bij upload_ op de betreffende compartimentskaart (beheerportaal-Nieuw)
  - het verplichten per uploaddocument van een **Auteur** is afhankelijk van het aangevinkt zijn van de kolom _Auteur verplicht bij upload_ op de betreffende compartimentskaart (beheerportaal-Nieuw).
- **Er kan eventueel een richting worden meegegeven in het stuf bericht naar DMS** (wordt niet naar compartiment gekeken). Indien zo ingesteld, zal een blok extraElementen worden toegevoegd met attribuutnaam Richting en als waarde uitgaand of inkomend of intern:
  - hiervoor moet bij de handmatige upload, in de wizard een Richting worden gekozen. Zichtbaar indien _Sectie: Documentregistreren_ en _DvDocrichting_ staat aan
  - de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: RichtingalsExtraElement_ moet bestaan en aangevinkt zijn
  - de instelling _Sectie: DocumentRegistreren_ en _Item: AlleHandmatigeUploads_ moet bestaan en aangevinkt zijn
  - _Getal1_ van instelling _Sectie: Documenten_ en _Item: Documentregistratie_ heeft de waarde 1

Voor de documenttypes laat het programma de gebruiker per document kiezen uit de gekoppelde documenttypes per OpenWave zaaktype: zie beheerportaal _Zaakbeheer_

- zaaktypes omgeving
- zaaktypes handhaving,
- zaaktypes APV/overig,
- soorten inspectietrajecten,
- soorten bezwaar/beroep,

en de brontabel documenttypen.

Zijn er geen koppelingen bij het betreffende zaaktype gedefinieerd of het gaat om een upload bij een inrichting dan kiest de gebruiker rechtstreeks uit de brontabel documenttypen (Beheer). Indien de inlogger tot een compartiment behoort, zal er bij documenttypen alleen gekozen kunnen worden uit de documenttypen waarvoor in beheer is aangegeven dat deze op compartiment van de inlogger van toepassing zijn.

Status en titel moeten met de hand per document worden ingevuld. Vertrouwelijkheid komt uit een vast dropdownlijstje (beheertegel _Vertrouwelijkheid_). De auteur wordt bij het uploaden van een aangewezen document gevuld met de vaste waarde 'Onbekend'. Indien het gaat om een zojuist gecreëerd document op basis van een sjabloon dan wordt de auteur gevuld met de medewerkerscode van de inlogger.

### Overige metadata meegeven bij handmatige upload

Er kan naast de bovengenoemde metadata die wordt meegegeven aan het DMS, ook gekozen worden om aanvullende metadata te kunnen opgeven bij handmatige upload ten behoeve van de documentregistratie (tbcorrespondentie). Dit staat los van of men met fileshare of DMS werkt (kan beiden). N.B. Deze aanvullende metadata (richting- uitzondering zie kopje hierboven _Is aanvullende (meta)-informatie verplicht per geüpload document?_, definitief) wordt dus niet meegenomen in het Stuf-bericht (in geval van DMS). Eerder was deze metadata alleen mee te geven bij het aanvinken per document door de gebruiker en de wizard voor handmatig registreren van documenten te doorlopen.

### Automatische registratie van document

Indien de zaak speelt in een compartiment dan kijkt OpenWave naar of de kolom _Handmatige uploads registreren_ (tbcompartiment.dldocregallehandmuploads) aangevinkt is bij het betreffende compartiment onder de tegel compartimentsrechten in beheerportaal-Nieuw, kolom _Gebruikers_. Indien de zaak NIET speelt in een compartiment dan kijkt OpenWave naar de instelling _Sectie: Documentregisteren_ en _Item: AlleOLODSOUploads_. Aangevinkt dan worden in de wizard voor upload documenten ook de velden getoond om metadata op te geven zoals aangegeven met de instellingen bij de documentregistratie. De programmatuur kijkt als volgt naar de instellingen (dus alleen als handmatig upload registreren aan staat!):

- **Documenttype** hiervoor geldt bovengenoemde instelling voor DMS en/OF instelling _Sectie: Documentregistreren_ en _Item:DvDoctype_ staat aan
- **Titel/Korte omschrijving** hiervoor geldt bovengenoemde instelling voor DMS en/OF _Sectie: Documentregistreren_ en _DvOmschrijving_ staat aan
- **Vertrouwelijkheid** hiervoor geldt bovengenoemde instelling voor DMS en/OF _Sectie: Documentregistreren_ en _DvVertrouwelijkheid_ staat aan
- **Richting** (uitgaand, binnenkomend, intern). Zichtbaar indien _Sectie: Documentregistreren_ en _DvDocrichting_ staat aan
- **Definitief** (ja, nee). Zichtbaar indien _Sectie: Documentregistreren_ en _DvStatus_ staat aan. Is niet hetzelfde als status bij koppelingdocnaardms: daar is het de status die meegegeven wordt in het uitgaande Stuf-bericht. Voor de documentregistratie wordt met dvstatus bedoelt of het om een document gaat met status definitief ja of nee
- **Ontvangstdatum** zichtbaar indien _Sectie: Documentregistreren_ en _DdOntvangstdatum_ staat aan.

### Uploaden van geregistreerd document

Indien _Getal2_ van instelling _Sectie: Documenten en Item: DocumentRegistratie_ de waarde 1 heeft dan zal bij het uploaden van een document dat reeds voorkomt bij de betreffende zaak in tbcorrespondentie (geregistreerde documenten) de kolom dvdocplaats gewijzigd worden in server, ddgewijzigd in vandaag en dvcoderegistreerder met de inlogger. De controle vindt plaats op pad (niet bij stuf zaak/DMS) + documentnaam. De view-kolom dvkanbewerken (het kleurenbolletje van de lijst geregistreerde documenten) wordt daarmee groen mits het document de status uitgaand heeft en nog niet is verstuurd.

### Overige Instellingen

- De instelling _Sectie: Documenten_ en _Item: MultipleUpload_ moet aangevinkt zijn.
- In _Getal1_ van _Sectie: OWB_ en _Item: MaxUploadMbGrootte_ kan de maximale **toegestane bestandsgrootte** voor multiple uploads en downloads worden ingegeven in Mb (default 50Mb). LET OP: Deze instelling is niet van toepassing op documenten die van buiten naar OpenWave worden binnengeschoten (OLO, DSO, RVO): daar geldt een restrictie die in de PHP.ini staat, waar functioneel beheer NIET bij kan.
- In de kolom _tekst_ van instelling _Sectie: OWB_ en _Item: TussenMapUploadFiles_ moet de mapnaam op de webserver die gebruikt wordt als **uploadmap** : het tussenstation tussen DMS/fileshare en het device van de gebruiker. Deze mapnaam MOET eindigen op de karakterreeks: '/openwave/upload/' en beginnen met een '/'.
- In _Getal1_: (default: 24) van _Sectie: OWB_ en _Item: MaxUurUpload_ staat het aantal uur waarna de programmatuur zelf de file zal verwijderen. Files ouder dan het aantal uur dat is ingesteld in kolom _Getal1_ van bovengenoemde instelling worden automatisch verwijderd.
- Indien _Sectie: Documenten_ en _Item: StartAutomUploadSchermNaUpload_ aangevinkt is dan wordt na het aanwijzen van de te uploaden documenten met de knop 'uitvoeren' automatisch het scherm _toon uploads bij deze zaak_ getoond. Het uploaden (afhankelijk van grootte en aantal documenten) kan nog onder water bezig zijn, zodat de kleurbolletjes bij de eerder aangewezen documenten nog op oranje staan (ben bezig). Onderaan het scherm is daarom een refreshknop geplaatst.
- Indien _Getal1_ van _Sectie: OWB_ en _Item: VertragingMilSecUploadFile_ gevuld is, dan wordt deze waarde beschouwd als het aantal milliseconden dat het programma moet wachten na elke file die moet worden geüpload. De ontvangende server kan een probleem hebben met het gelijktijdig ontvangen van berichten.
- Indien _Getal1_ van _Sectie: OWB_ en _Item: MaxLengteUploadBestandsnaam_ is gevuld dan kan geen file aangewezen worden waarvan de bestandsnaam inclusief extensie qua lengte groter is dan de waarde van _Getal1_.

Indien de upload vanuit de tabel **adviezen** wordt gedaan dan geldt nog het volgende:

- aan de kolom **uploadlog** van de betreffende advieszaak wordt een regel met systeemdatum + medewerkerscode en upgeloade filenaam toegevoegd
- indien de instelling _Sectie: Adviezen_ en _Item: DateringDoorUpload_ aangevinkt is en de kolom _datering advies_ (tbadviezen.ddadvdatering) is leeg dan wordt deze gevuld met de datum van upload
- indien de instelling _Sectie: Adviezen_ en _Item: DateringDoorUpload_ aangevinkt is en de kolom _adviesdatum_ (tbadviezen.ddadvadvies) is leeg dan wordt deze gevuld met de datum van upload.

Zie voor verdere specifieke instellingen bij de paragrafen:

- [Upload documenten naar fileshare](/probleemoplossing/programmablokken/upload_document/upload_naar_fileshare.md)
- [Upload documenten met StUF zaak/DMS](/probleemoplossing/programmablokken/upload_document/upload_naar_stuf_zaak_dms.md)
- [Upload documenten met CMIS](/probleemoplossing/programmablokken/upload_document/upload_met_cmis.md)
