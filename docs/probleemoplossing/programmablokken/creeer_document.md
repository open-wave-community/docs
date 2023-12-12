# Creëer document

Vanuit detailschermen van een omgevingszaak, handhavingszaak, APV/overige zaak, bouw/sloopzaak, inrichting, info of milieu/gebruik alsmede vanuit de detailschermen van een advies, inspectietraject en een inspectiebezoek, bezwaar/beroep en vanuit het overzichtslijstje van contacten bij een zaak/inrichting is de mogelijkheid om in het menu opties het item creëer document te kiezen. In de regel gebeurt dit met het menu-item _creëer document_ (menu opties rechtsboven in betreffende scherm). De gebruiker kies eerst een sjabloongroep en vervolgens een sjabloon, waarna een aantal aanvullende vragen kunnen volgen.

Het is echter ook mogelijk om een specifiek documentsjabloon direct te starten vanuit een tegel of een (scherm)knop. De action die daarbij gedefinieerd moet worden heeft de volgende vorm: _startWizard(maakDocument,1234,tbdocumenten;;tbomgvergunning;{id},W)_ hetgeen betekent: start het sjabloon gedefinieerd in de tbdocumenten met dnkey (ID) = 1234 en de uitgangssituatie is de kaart in tbomgvergunning waar je op dat moment op staat (dat is die {ID}). Zie voorbeeld [Scherminformatie voor detailschermen](/instellen_inrichten/schermdefinitie/scherminformatie_voor_detailschermen.md). Het mag duidelijk zijn dat in dit voorbeeld die schermknop geplaatst moet zijn op het detailscherm van een omgevingszaak.

Een document kan ook gestart worden vanuit een processtap: zie hiertoe: [Termijnstappen](/instellen_inrichten/inrichting_processen/termijnstappen.md)

## Rechten

- de gebruiker moet lid zijn van een rechtengroep die het recht: _uploaden en creëren van documenten_ heeft voor de betreffende module (omgeving, APV/overig, inrichting en handhaving, milieu/gebruik)
- en de zaak of inrichting mag niet geblokkeerd zijn:
  - Voor documentcreatie vanuit een advieskaart of bezwaar/beroep geldt hierbij dat gekeken wordt naar de blokkering van de onderliggende zaak.
  - Voor documentcreatie vanuit een inspectiekaart of inspectiebezoek geldt dat de zaak geblokkeerd is indien tenminste één van onderstaande items waar is
    - de afgeronddatum van de inspectietrajectkaart is gevuld
    - de instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ is NIET aangevinkt (of bestaat niet) en de blokkering van de onderliggende zaak is WEL gevuld.

### Keuzelijst met documentsjablonen

De gebruiker zal eerst een keuze kunnen maken uit de **sjabloongroepen** (tbdocumentsoorten) die behoren bij de betreffende module van de zaak. Deze lijst van groepen kan beperkt worden:

- doordat in het beheerportaal _Zaakbeheer_ bij het betreffende zaaktype een of meer sjabloongroepen zijn gekoppeld: alleen die groepen zijn dan zichtbaar. Indien aan het zaaktype geen sjabloongroepen zijn gekoppeld, dan zijn hier alle groepen zichtbaar.
- doordat alleen de sjabloongroepen getoond worden die voldoen aan het compartiment: Indien de zaak aan een compartiment is verbonden, dan worden alleen die groepen getoond waarvan een of meer documentsjablonen aan dat compartiment zijn verbonden. Omgekeerd: indien de zaak niet is gekoppeld aan een compartiment dan worden alleen die groepen getoond waarvan een of meer documentsjablonen niet aan een compartiment zijn verbonden.
- doordat alleen sjabloongroepen getoond worden die bij een gemeente horen. De groep wordt getoond indien een of meer documentsjablonen de kolom _alleen voor gemeente_ niet gevuld hebben of - indien die kolom wel is gevuld - dat die waarde (een gemeenteid) overeenkomt met de gemeente waar de zaak speelt (loacatieadres).

Na de sjabloongroepkeuze kan de gebruiker het sjabloon zelf aanwijzen.

Deze **lijst van sjablonen** wordt als volgt samengesteld uit tbdocumenten (beheertegel _Documentsjablonen_):

- alleen de sjablonen die horen bij de gekozen groep
- en alleen documentsjablonen waarvoor geldt dat de vervaldatum leeg is
- en waarvoor geldt dat de kolom _benaderbaar vanuit tabel_ (tbdocumenten.dvvanuittabel) gelijk is aan de tabel waarvandaan de optie creëer document is gekozen: (mogelijkheden hier zijn: tbomgvergunning, tbovvergunningen, tbhandhavingen, tbinfoaanvragen, tbadviezen, tbinspecties, tbinspbezoeken en tbmilinrichtingen en tbmilvergunningen, tbbouwvergunningen en tbcontactadressen en tbbezwaarberoep)
- en waarvoor geldt dat kolom _Voor module_ (tbdocumenten.dvvantoepop) leeg is of gelijk aan de moduleletter van de bovenliggende zaak of inrichting (W = Omgeving, H = Handhaving, E = Milieu/gebruik en Inrichting, O = APV/overige, I = Infoaanvragen)
- en waarvoor geldt dat de kolom _Alleen gemeentes_ (tbdocumenten.dvalleengemeentes):
  - is leeg
  - OF de gemeente-id van de bovenliggende Locatie (dus waar de zaak speelt) + ';' komt voor in de inhoud van deze kolom.

Indien de inlogger lid is van een [compartiment](/instellen_inrichten/compartimenten.md), dan geldt de restrictie dat alleen uit die documenten gekozen kan worden die gekoppeld zijn aan datzelfde compartiment.

Omgekeerd geldt dat indien de inlogger GEEN lid is van een compartiment, dat alleen uit die documenten gekozen kan worden die NIET gekoppeld zijn aan een compartiment.

### Te genereren documentnaam

Het document zal gecreëerd worden onder een naam. Het programma stelt een defaultnaam voor op basis van het volgende:

- Indien de sjabloonkolom _Te genereren documentnaam zonder extensie_ (dvtemplate) gevuld is dan wordt die naam gekozen waarbij de substrings
  - %date% vervangen moet worden door 'yyyymmdd' van vandaag
  - %login% vervangen moet worden door de medewerkerscode van de inlogger
  - %hoofdzaaknr% vervangen moet worden door de wave zaakcode van de hoofdzaak
  - %deelzaaknr% vervangen moet worden door de wave zaakcode van de deelzaak dus die van een specifiek advies, inspectie of bezwaarberoep
  - %hoofddmsnr% vervangen moet worden door zaakcode waarmee de hoofdzaak is verbonden met een extern zaaksysteem
  - %deeldmsnr% vervangen moet worden door zaakcode waarmee de deelzaak is verbonden met een extern zaaksysteem. Dus die van een specifiek advies, inspectie of bezwaarberoep
  - %teller% vervangen wordt met een automatische teller die gegenereerd wordt op basis van de (aangevinkte) instelling _Sectie: Documenten en Item: WaveBriefNummer_, waarbij de kolom _Tekst_ gevuld is met een vast deel van de teller (bijv. WV), _Getal2_ met de lengte van het ophogende deel (bijv. 3) en _Getal1_ van deze instelling wordt door het algoritme gebruikt om het ophogende deel steeds opnieuw op te slaan wanneer deze is uitgetrokken bij een documentcreatie. Stel _Getal1_ is 23, _Tekst_ = WV en _Getal2_ is 5 dan wordt als teller de waarde WV00023 gegenereerd.

De teller kan ook in het document zelf worden opgenomen indien in het sjabloon de string <%teller%> is opgenomen

- anders (dvtemplate niet gevuld) dan wordt de documentnaam de waarde van de kolom _UNC-pad + naam sjabloon_ zonder mapgedeelte en extensie.

De extensie wordt door het programma bepaald: docx of odt of basis van het filenaamgedeelte van die kolom _UNC-pad + naam sjabloon_ waarbij de extensie .dotx vervangen wordt door .docx .

Of de voorgestelde defaultnaam overschreven kan worden door de persoon die het document creëert, is afhankelijk van een eigenschap van het sjabloon: Voorgestelde documentnaam wijzigbaar (tbdocumenten.dlnaammuteerbaar).

Indien:

- _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft
- en het document is na creatie automatisch opgeslagen

dan vindt een controle plaats in de geregistreerde documenten (tbcorrespondentie) op het voorkomen van de naam (pad + naam + extensie) in de kolom dvdocfilenaam. Zo ja, dan krijgt de gebruiker een melding en de mogelijkheid deze naam aan te passen.

### Aangewezen documentsjabloon en Xential

Indien de kolom _Naam sjabloon in Xential_ (dvnaaminexternsjablprog) gevuld is in de sjabloondefinitie (beheertabel tbdocumenten), dan zal OpenWave Xential aanroepen om een document te genereren. Zie [Xential](/probleemoplossing/programmablokken/xential.md).

### Automatische opslag in DMS/fileshare

Of het gecreëerde document automatisch moet worden opgeslagen is afhankelijk van het ingestelde in het documentsjabloon onder de kolommen _Automatische Opslag Fileshare/Cmis_. Indien hier de kolom _Autom. Upload_ is aangevinkt dan is dat het geval (ook voor StUF zaak/DMS koppeling).

In geval van CMIS of fileshare kan in het documentsjabloon de specifieke map worden aangewezen: te selecteren uit de mogelijkheden zoals gedefinieerd in _Sectie: AanmaakMappen_.

In geval van StUF zaak/DMS moet wel het externe zaak/DMS nummer bij de zaak gevuld zijn van waaruit het document wordt gecreëerd. Is dat niet geval dan wordt het gecreëerde document NIET automatisch opgeslagen.

Wanneer het documentsjabloon ingesteld is op dat het document automatisch moet worden opgeslagen kijkt het programma naar de instellingen _Sectie: Documenten_ en _Item: OphalenViaFileserver_ en naar de instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_. Indien beide aangevinkt staan, dan zal de inlogger een keuze voor een van de twee moeten maken (of alsnog de keuze niet opslaan). Indien er maar één van deze twee instellingen is aangevinkt dan moet de inlogger de automatische opslag bevestigen.

Voor de**metadata** bij automatische opslag (alleen zinvol bij DMS) geldt het volgende:
Of de inlogger metadata moet invullen is afhankelijk van het aangevinkt zijn van de instellingen:

- _Sectie: KoppelingDOCNAARDMS_ en _Item: DocumenttypeVerplicht_ Indien aangevinkt komt de waarde documenttype uit de sjabloonkolom _Documentype DMS_ (dvdmsdoctype) en kan alleen dynamisch worden overschreven indien de sjabloonkolom leeg is.
- _Sectie: KoppelingDOCNAARDMS_ en _Item: TitelVerplicht_. Indien aangevinkt dan zal de inlogger een **titelkolom** moeten vullen.
- _Sectie: KoppelingDOCNAARDMS_ en _Item: StatusVerplicht_. Indien aangevinkt dan zal de inlogger een **statuskolom** moeten vullen.
- _Sectie: KoppelingDOCNAARDMS_ en _Item: VertrouwelijkheidVerplicht_. Indien aangevinkt komt de waarde **vertrouwelijkheid** uit de sjabloonkolom _Vertrouwlijkheid DMS_ (dvdmsvertrouwlijkheid) en kan alleen dynamisch worden overschreven indien de sjabloonkolom leeg is.

Indien _Sectie: KoppelingDOCNAARDMS_ en _Item: AuteurVerplicht_ is aangevinkt dan wordt de **Auteur** gevuld met de medewerkerscode van de inlogger.

LET OP: indien een document wordt gecreëerd bij een zaak die geen extern zaak/DMS nummer heeft, dan worden bovenstaande metadata niet gevraagd (en het document wordt ook niet aan het DMS aangeboden).

Bovenstaande instellingen zijn van toepassing op situatie GEEN compartiment. Indien WEL compartiment dan wordt gekeken naar de instellingen voor DMS bij de compartimentdefinitie. Hier is ook de default Documenttype en Vertrouwelijkheid aan te geven.

### Richting, Verzendwijze

Bij **richting** kan gekozen worden voor Uitgaand of Intern (in de sjabloondefinitie kan de defaultwaarde hiervoor opgegeven worden). Deze eigenschap wordt overgenomen (in de kolom dvdocrichting) indien het gecreëerde document automatisch geregistreerd wordt in tbcorrespondentie. Deze waarde wordt ook doorgezet naar het DMS mits de instelling _Sectie: KoppelingDOCNaarDMS en Item: RichtingAlsExtraElement_ is aangevinkt - via ExtraElementen.

**Verzendwijze** Per Post of Per Email. Deze eigenschap wordt overgenomen indien het gecreëerde document automatisch geregistreerd wordt in tbcorrespondentie (in de kolom dlmoetperpost). Indien bij de definitie van het sjabloon is aangevinkt: _alleen per post_ dan zal de gebruiker dit gegeven NIET kunnen wijzigen (en ook niet in het geregistreerde document).

**Aangetekend** Deze eigenschap wordt overgenomen indien het gecreëerde document automatisch geregistreerd wordt in tbcorrespondentie (in de kolom dlaangetekend) mits de verzendwijze ook per post is. Indien men geen gebruik maakt van het Aangetekend versturen van post kunnen de betreffende keuzemogelijkheden in de Maakdocument wizard onzichtbaar worden gemaakt. Hiervoor maakt men zelf de instelling _Sectie: Documenten en Item: Postnooitaangetekend_ aan en zet deze op 'aan'.

### Contactpersoon

Wanneer het documentsjabloon ingesteld is op 'Contactpersoon verplicht' dan zal de inlogger een contactpersoon moeten aanwijzen (dat zijn de contactpersonen die gedefinieerd zijn bij de hoofdzaak. Alleen bij Bezwaar/beroep geldt dat gekozen moet worden uit de contactpersonen die horen bij de bezwaar/beroep kaart. De dnkey (de unieke identifier) van de gekozen contactpersoon zal bij het samenstellen van het document gebruikt worden om de variabele :keyadres uit de SQL-statements te vullen.

Indien de contactpersoon in de lijst is voorzien van een rood kleurenbolletje, dan is het contactadres vervallen en/of heeft de contactpersoon een gevulde overlijdensdatum.

### Bijlages

Indien:

- de instelling _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft (hetgeen betekent dat gecreëerde documenten automatisch worden opgeslagen in geregistreerde documenten (tbcorrespondentie)
- en bij het documentsjabloon is de eigenschap _Bijlages aanwijzen uit geregistreerde documenten_ aangevinkt (tbdocumenten.dlbijlagesregdoc)

dan komt er een nieuwe pagina in de wizard Creëer Document, waarbij de inlogger één of meer andere niet-vervallen geregistreerde documenten kan aanwijzen die horen bij dezelfde zaak met de bedoeling dat deze meegestuurd worden met het oorspronkelijke document. De gebruiker kan een bijlage zoeken op de kolommen dvfilenaam, dvomschrijving en dvdoctype_oms.

Deze bijlages komen in de tabel tbcorrespbijlages die gekoppeld is aan het geregistreerde document (zie detailpagina van dat geregistreerde document).

Indien de instelling _Sectie: DocumentRegistreren_ en _Item: BijlagenAlleenDefinitief_ is aangevinkt dan kunnen alleen geregistreerde documenten met de eigenschap dvdefinitief = J worden aangewezen als bijlage.

### cc's

Wanneer

- het documentsjabloon ingesteld is op 'Contactpersoon verplicht'
- en er is qua richting gekozen voor Uitgaand
- en de instelling _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft (hetgeen betekent dat gecreëerde documenten automatisch worden opgeslagen in geregistreerde documenten (tbcorrespondentie)

dan kan de inlogger een of meer contactpersonen aanwijzen (dat zijn de contactpersonen die gedefinieerd zijn bij de hoofdzaak) die bij het geregistreerde document als cc worden opgeslagen.

Deze cc's worden in ieder geval gebruikt bij verzendwijze = email.

Indien de contactpersoon in de lijst is voorzien van een rood kleurenbolletje, dan is het contactadres vervallen en/of heeft de contactpersoon een gevulde overlijdensdatum.

Indien de gebruiker heeft aangegeven dat het document per post verstuurd mag worden, dan mag de hoofgeadresseerde opgenomen worden in de lijst met cc's (deze krijgt dan zowel de brief per post als per mail).

Indien per mail, dan kan de hoofdgeadresseerde niet ook nog een opgenomen worden in de cc’s.

### Aanmaak kaart in geregistreerde documenten

Indien _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft, dan krijgt het document dat gecreëerd is (en opgeslagen op fileserver of in DMS) automatisch een verwijzing in een kaart van tbcorrespondentie bij de betreffende hoofdzaak. Voor een document dat onder een compartimentszaak aangemaakt wordt geldt dat OpenWave hiertoe kijkt naar de kolom _Handmatige uploads registreren_ (tbcompartiment.dldocregallehandmuploads): tegel Compartimentsrechten in beheerportaal-Nieuw, kolom Gebruikers.

### Automatisch openen als hyperlink na creëren (alleen firefox ) bij opslag fileserver

Indien:

- tbdocumenten.dlrepeat = F (dit is in OpenWave default het geval)
- en het IP-adres van de huidige sessie (tbsessions) van de gebruiker voldoet aan het masker gedefinieerd in de kolom _IpRange_ van een van de regels van de tabel tbipranges, waarbij de kolom dlhyperlink aangevinkt is
- en kolom _Getal2_ van _Sectie: Documenten Item: OphalenViaFileserver_ heeft de _waarde 1_ (waarmee wordt aangegeven dat de mensen die binnen de genoemde IP-range vallen ook Firefox als standaardbrowser hebben waarin OpenWave als trusted (firefox-policy) is gedefinieerd)
- en het document is na creatie automatisch opgeslagen op de fileshare (dus niet stufzaken of CMIS)

DAN het word document dat gecreëerd is via een hyperlink geopend: dat wil zeggen dat de wizard afgesloten wordt met een vervolgaction: `'openTabPage(file:/' +  map + documentnaam + extensie + ')`' waarbij alle backslashes omgezet zijn in forwardslashes.

Indien echter bovenstaande het geval is, maar de de [satellite](/instellen_inrichten/satellite_filesysteem.md) staat aan, dan werkt dit alleen indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Documentroot_ gelijk is aan dezelfde instelling van de configuratiefile van de geïnstalleerde satellite.

Voor overige instellingen voor het uploaden van een document zie [Upload documenten](/probleemoplossing/programmablokken/upload_document.md)

en voor de definitie van de sjablonen zelf zie: [Documentsjablonen](/instellen_inrichten/documentsjablonen.md).

### Automatisch openen met MS-Word via Office URI-scheme na creëren bij opslag fileserver

Indien:

- tbdocumenten.dlrepeat = F (dit is in OpenWave default het geval)
- en het IP-adres van de huidige sessie (tbsessions) van de gebruiker voldoet aan het masker gedefinieerd in de kolom _IpRange_ van een van de regels van de tabel tbipranges, waarbij de kolom dlhyperlink aangevinkt is
- en kolom _Getal2_ van _Sectie: Documenten Item: OphalenViaFileserver_ heeft de _waarde 2_ (bij een compartiment dat gebruikt van een satellite op de lokale fileserver kijkt OpenWave naar de kolom tbcompartiment.dldocsfileshareofficeuri. Die moet aangevinkt zijn)
- en het document is na creatie automatisch opgeslagen op de fileshare (dus niet stufzaken of cmis)

DAN wordt het document in een vervolgaction van de wizard geopend via Office URI-scheme, bijvoorbeeld: `ms-Word:ofe| u |file:/zuurstof/user/pdeboer/Paultest.docx`.

Indien echter bovenstaande het geval is, maar de de [satellite](/instellen_inrichten/satellite_filesysteem.md) staat aan, dan werkt dit alleen indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Documentroot_ gelijk is aan dezelfde instelling van de configuratiefile van de geïnstalleerde satellite.

Voor overige instellingen voor het uploaden van een document zie [Upload documenten](/probleemoplossing/programmablokken/upload_document.md).

en voor de definitie van de sjablonen zelf zie: [Documentsjablonen](/instellen_inrichten/documentsjablonen.md)
DAN wordt het document via Office URI-scheme geopend: bijvoorbeeld bijv. `ms-word:ofe| u |file:/zuurstof/user/pdeboer/Paultest.docx`.

### Automatisch openen met OnlyOffice na creëren

Indien:

- tbdocumenten.dlrepeat = F (dit is in OpenWave default het geval)
- en het document is na creatie automatisch opgeslagen op de fileshare of in een DMS (met cmis of met stuf zaak/DMS)
- en - indien fileserver - geen office URL scheme mogelijkheid/instelling
- en de instelling _Sectie: Documenten Item: OnlyOffice_ is aangevinkt
- en de extensie van het gecreëerde document +’;’ komt voor in de kolom _Tekst_ van deze instelling
- en _Getal1_ van deze instelling is ongelijk aan 1

dan wordt het opgeslagen en gecreëerde document direct met OnlyOffice geopend.

Aangezien het stallen van een document in een DMS via stuf zaak/DMS asynchroon is kan het zijn dat OnlyOffice dat document opvraagt bij het DMS terwijl dat document nog niet verwerkt is. Daarom de instelling _Getal1_ = 1: het aangemaakte document wordt dan niet automatisch geopend.

### Automatische download op download map van device van gebruiker

Er zijn twee vervolgacties mogelijk na het creëren van een document:

- openen met OnlyOffice
- openen als hyperlink bij opslag op fileserver.

Indien er GEEN vervolgactie van toepassing is dan wordt het document gedownload op de downloadmap op de device van de gebruiker. Ook wanneer het document is opgeslagen in het DMS of op een fileshare. Die download in de laatste situatie (dus het document wordt ook al op fileserver of DMS opgeslagen) kan voorkomen worden door de instelling _Sectie: Documenten en Item: geendownloadnaardevice_ aan te vinken.

### Automatisch aanmaak regel geregistreerde documenten (tbcorrespondentie) na creëren

Indien:

- _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft
- en het document is na creatie automatisch opgeslagen

dan wordt automatisch een regel aangemaakt of - indien de registratie al bestond: overschreven - in tbcorrespondentie ([Geregistreerde Documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md)).

Indien:

- Opslag op fileserver dan:
  - wordt de kolom dvdocfilenaam gevuld met map (van fileserver) + filenaam
- Opslag via CMIS dan:
  - wordt de kolom dvdocfilenaam gevuld met map (van DMS) + filenaam
  - wordt de kolom dvintdoccode gevuld met de unieke documentidentifier uitgetrokken door het DMS
- Opslag via stuf zaken/DMS dan:
  - wordt de kolom dvdocfilenaam gevuld met filenaam
  - wordt de kolom dvintdoccode gevuld met de unieke documentidentifier uitgetrokken door het DMS
  - wordt de kolom dvintzaakcode gevuld met de unieke zaakidentifier waaronder het document is opgeslagen.

De controle op of een registratie al bestaat vindt plaats op de kolom tbcorresondentie.dvdocfilenaam (is pad + documentnaam inclusief extensie).

### KIX

Post.nl maakt bij de sortering van post gebruik van een streepjescode: de KIX (KlantIndeX). De KIX-code is een streepjescode die adresgegevens bevat. Zo kunnen zij de post automatisch verwerken. Verzenders van partijenpost die deze KIX gebruiken bij de adressering van hun post kunnen in aanmerking komen voor een korting op de tarieven. Hiervoor is een apart lettertype vereist: KIX-font Windows True Type (kixbrg_ttf).

De KIX bevat het bestemmingsadres bestaande uit de postcode in combinatie met het huis-, postbus- of antwoordnummer en een eventuele huisnummertoevoeging. Bij een toevoeging en/of huisletter moet er en X tussen het huisnummer als afscheidingsteken. Er is een speciaal font beschikbaar. Deze fonts zijn schaalbaar, maar moeten altijd op 10 punts grootte worden afgedrukt om aan de specificaties te voldoen: eventueel te downloaden op [https://www.postnl.nl/klantenservice/bestellen-en-downloaden/documentatie-downloaden/kix-code/](https://www.postnl.nl/klantenservice/bestellen-en-downloaden/documentatie-downloaden/kix-code/.md).

De expressie in de query bij een brief is bij een Omgevingsvergunning:

![kix-query](/docs/img/applicatiebeheer/probleemoplossing/programmablokken/kix.w.500_tok.579bb3.jpeg){ width=500px loading=lazy class="media" }

### Briefnummer en gecrypte waardes

Zie: [Documentsjablonen en Sjabloongroepen](/instellen_inrichten/documentsjablonen.md).
