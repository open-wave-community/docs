# Creëer email

Vanuit het detailscherm van een omgevingszaak, handhavingszaak of van een inspectiebezoek of advies, is de mogelijkheid om linksonder in het scherm de wizard maak email te starten via de knop **Creëer email**. De gebruiker kies eerst een sjabloongroep en vervolgens een sjabloon, waarna een aantal aanvullende vragen kunnen volgen. Indien er bij het sjabloon is aangegeven dat de body en/of onderwerp te wijzigen is, kan de medewerker de inhoud van de mail dan wel het onderwerp aanpassen in deze wizard. De wizard maak email is ook te starten vanuit het Opties menu bij de bovengenoemde schermen.

Er kan alleen een email worden verstuurd als er tenminste één contactpersoon bij de zaak/inrichting is met een gevuld mailadres. Ook dient de ingelogde gebruiker een gevuld mailadres te hebben in de medewerkerskaart. Er wordt bij opstellen van de email 1 geadresseerde gekozen en er kunnen meerdere CC-contacten gekozen worden. Uiteraard afhankelijk van het aantal aanwezige contactpersonen met gevuld mailadres bij de zaak/inrichting.

> [!WARNING] **LET OP:**
> Uiteraard moet er wel vanuit OpenWave gemaild kunnen worden. Hiervoor bestaan standaard mailinstellingen. Indien er al gemaild wordt naar de BAG en/of adviesinstanties, dan zijn deze instellingen al goed ingeregeld.
> Zie ook [sectie webmail](/instellen_inrichten/configuratie/sectie_web.mail.md).

## Adviesinstantie als contactpersoon

Indien de wizard gestart wordt vanaf een _Advies_, dan zal de lijst met te kiezen contactpersonen (en/of CC) eventueel uitgebreid worden met de adviesinstantie:

- alleen indien de adviesinstantie een gekoppeld contact heeft (verwijzing naar tbcontactadressen): zie veld _ID contactadres_ in het detailscherm van de adviesinstantie (beheertegel _Adviesinstanties_)
- en er een mailadres is opgegeven bij de adviesinstantie.

De lijst met te kiezen contactpersonen krijgt dan een extra kolom _Adviesinstantie_ waarin de naam van de instantie zichtbaar is.

> [!WARNING] **LET OP:**
> Indien de adviesinstantie als contactpersoon kan worden gekozen dient men hier bij de sjabloondefinitie rekening mee gehouden te worden. Gegevens over het contact in de body van de mail zullen moeten gehaald worden uit adviezen (en niet uit bijvoorbeeld omgevingscontacten tabel). en zijn dus beperkter dan dat men mailt naar een contactpersoon gekoppeld aan de hoofdzaak. Ook is verwijzing _:keyadres_ niet functioneel: deze zal altijd vervangen worden door een contactadres ID bij de hoofdzaak. en een adviesinstantie hoeft niet gekoppeld te zijn aan de hoofdzaak als contactpersoon waardoor _:keyadres_ leeg zal zijn.

## Rechten

- De gebruiker moet lid zijn van een rechtengroep die het recht: _uploaden en creëren van documenten_ heeft voor de betreffende module (omgeving, APV/overig, horeca, inrichting en handhaving, milieu/gebruik)
- en de zaak of inrichting mag niet geblokkeerd zijn:
  - Voor documentcreatie vanuit een inspectiebezoek geldt dat de zaak geblokkeerd is indien tenminste één van onderstaande items waar is:
    - de afgerond datum van de inspectietrajectkaart is gevuld
    - de instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ is NIET aangevinkt (of bestaat niet) en de blokkering van de onderliggende zaak is WEL gevuld.

### Keuzelijst met emailsjablonen

Deze wordt als volgt samengesteld uit tbemailsjabloon (beheertegel _Emailsjablonen_):

- alleen mailsjablonen waarvoor geldt dat de vervaldatum leeg is
- en waarvoor geldt dat de kolom _benaderbaar vanuit tabel_ (tbemailsjabloon.dvvanuittabel) gelijk is aan de tabel waarvandaan de optie creëer email is gekozen (mogelijkheden hier zijn voor nu alleen nog: tbomgvergunning, tbhandhavingen en tbinspbezoeken, tbadviezen)
- en waarvoor geldt dat kolom _Voor module_ (tbemailsjabloon.dvvantoepop) leeg is of gelijk aan de moduleletter van de bovenliggende zaak of inrichting (W=Omgeving, H=Handhaving, E=Milieu/gebruik en Inrichting, O=APV/overige, I = Infoaanvragen)
- en waarvoor geldt dat de kolom _Alleen gemeentes_ (tbemailsjabloon.dvalleengemeentes):
  - is leeg
  - OF de gemeente-id van de bovenliggende Locatie (dus waar de zaak speelt) + ';' komt voor in de inhoud van deze kolom.

Indien de inlogger lid is van een [compartiment](/instellen_inrichten/compartimenten.md), dan geldt de restrictie dat alleen uit die mailsjablonen gekozen kan worden die gekoppeld zijn aan datzelfde compartiment.

Omgekeerd geldt dat indien de inlogger GEEN lid is van een compartiment, dat alleen uit die mailsjablonen gekozen kan worden die NIET gekoppeld zijn aan een compartiment.

### Te genereren documentnaam

Indien de gecreëerde mail zal moeten worden opgeslagen, zal er een document van gemaakt worden (tekstbestand met als extensie .eml). Het document zal gecreëerd worden onder een naam. Het programma stelt een defaultnaam voor op basis van het volgende:

- Indien de sjabloonkolom _Te genereren documentnaam zonder extensie_ (dvtemplate) gevuld is dan wordt die naam gekozen waarbij de substrings
  - %date% vervangen moet worden door 'yyyymmdd' van vandaag
  - %login% vervangen moet worden door de medewerkerscode van de inlogger
  - %hoofdzaaknr% vervangen moet worden door de wave zaakcode van de hoofdzaak
  - %deelzaaknr% vervangen moet worden door de wave zaakcode van de deelzaak dus die van een specifiek advies, inspectie of bezwaarberoep
  - %hoofddmsnr% vervangen moet worden door zaakcode waarmee de hoofdzaak is verbonden met een extern zaaksysteem
  - %deeldmsnr% vervangen moet worden door zaakcode waarmee de deelzaak is verbonden met een extern zaaksysteem. Dus die van een specifiek advies, inspectie of bezwaarberoep
  - %teller% vervangen wordt met een automatische teller die gegenereerd wordt op basis van de (aangevinkte) instelling _Sectie: Documenten en Item: WaveBriefNummer_, waarbij de kolom _Tekst_ gevuld is met een vast deel van de teller (bijv. WV), _Getal2_ met de lengte van het ophogende deel (bijv. 3) en _Getal1_ van deze instelling wordt door het algoritme gebruikt om het ophogende deel steeds opnieuw op te slaan wanneer deze is uitgetrokken bij een documentcreatie. Stel Getal1 is 23, Tekst = WV en Getal2 is 5 dan wordt als teller de waarde WV00023 gegenereerd.

De teller kan ook in het document zelf worden opgenomen indien in het sjabloon de string <%teller%> is opgenomen.

- anders (dvtemplate niet gevuld) dan wordt de documentnaam de waarde van de kolom _omschrijving_.

De extensie wordt door het programma bepaald (altijd .eml).

Indien:

- _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft
- en het document is na creatie automatisch opgeslagen

dan vindt een controle plaats in de geregistreerde documenten (tbcorrespondentie) op het voorkomen van de naam (pad + naam + extensie) in de kolom dvdocfilenaam. Zo ja, dan krijgt de gebruiker een melding en de mogelijkheid deze naam aan te passen.

### Afzender

Er zijn drie mogelijkheden: het email-adres van de inlogger (tbmedewerkers.dvemail), het niet-persoonlijke emailadres van de inlogger (tbmedewerkers.dvnietpersemail) en het algemene (noreply) adres van de organisatie. Dit laatste adres is -indien de zaak GEEN compartimentszaak is - de kolom _Tekst_ van de instelling _Sectie: Programma en Item: NoReplyEmailadres_. In het geval dat de zaak WEL een compartimentszaak is, dan kijkt het programma naar de kolom _dvnoreplyemailadres_ van het betreffende compartiment.

Er kan ook ingesteld worden wat de default (voorkeur) moet zijn van deze mogelijkheden. Indien geen compartiment is dat ingesteld in de kolom _Tekst_ van _Sectie: Programma en Item: AfzEmailDefVolg_. In geval van compartiment is dat de kolom _dvafzemaildefvolg_. De waarde moet zijn:

- 1 (tevens defaultwaarde) betekent het mailadres van de inlogger. Deze is per definitie gevuld anders kan er geen email gemaakt worden
- 2 betekent het het niet-persoonlijke mailadres van de inlogger
- 3 betekent het algemene no reply mailadres.

OpenWave redeneert verder als volgt:

Indien ingestelde voorkeur is 2, maar geen tbmedewerkers.dvnietpersemail gevuld bij de inlogger dan wordt de default 1 (en kan optie 2 niet gekozen worden).

Indien voorkeur is 3, maar geen algemene no reply email-adres gevuld dan wordt de default 1 (en kan optie 3 niet gekozen worden).

Tot slot geldt dat - ook wanneer als afzender gekozen is voor het niet-persoonlijke emailadres van de inlogger of voor het algemene noreply-adres - , dat de inlogger een kopie krijgt als bcc (op zijn/haar persoonlijke emailadres) mits het aanvinkvakje _afschrift naar 'inlognaam van inlogger'_ aangevinkt is. Dit vakje is default aangevinkt indien de instelling _sectie: Documenten: Item EmailafschriftnaarInlogger_ ook aangevinkt is.

### Automatische opslag in DMS/fileshare

Of het gecreëerde document automatisch moet worden opgeslagen is afhankelijk van het ingestelde in het mailsjabloon onder de kolommen _Automatische Opslag Fileshare/Cmis_. Indien hier de kolom _Autom. Upload_ is aangevinkt dan is dat het geval (ook voor StUF zaak/DMS koppeling).

In geval van CMIS of fileshare kan in het mailsjabloon de specifieke map worden aangewezen: te selecteren uit de mogelijkheden zoals gedefinieerd in _Sectie: AanmaakMappen_.

In geval van StUF zaak/DMS moet wel het externe zaak/DMS nummer bij de zaak gevuld zijn van waaruit het document wordt gecreëerd. Is dat niet geval dan wordt het gecreëerde document NIET automatisch opgeslagen.

Wanneer het mailsjabloon ingesteld is op dat het document automatisch moet worden opgeslagen kijkt het programma naar de instellingen _Sectie: Documenten_ en _Item: OphalenViaFileserver_ en naar de instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_. Indien beide aangevinkt staan, dan zal de inlogger een keuze voor een van de twee moeten maken (of alsnog de keuze niet opslaan). Indien er maar één van deze twee instellingen is aangevinkt dan moet de inlogger de automatische opslag bevestigen.

Voor de**metadata** bij automatische opslag (alleen zinvol bij DMS) geldt een aantal voorwaarden. Of de inlogger metadata moet invullen is afhankelijk van het aangevinkt zijn van de volgende instellingen:

- _Sectie: KoppelingDOCNAARDMS_ en _Item: DocumenttypeVerplicht_. Indien aangevinkt komt de waarde documenttype uit de sjabloonkolom _Documentype DMS_ (dvdmsdoctype) en kan alleen dynamisch worden overschreven indien de sjabloonkolom leeg is.
- _Sectie: KoppelingDOCNAARDMS_ en _Item: TitelVerplicht_. Indien aangevinkt dan zal de inlogger een titelkolom moeten vullen.
- _Sectie: KoppelingDOCNAARDMS_ en _Item: StatusVerplicht_. Indien aangevinkt dan zal de inlogger een statuskolom moeten vullen.
- _Sectie: KoppelingDOCNAARDMS_ en _Item: VertrouwelijkheidVerplicht_. Indien aangevinkt komt de waarde vertrouwelijkheid uit de sjabloonkolom _Vertrouwlijkheid DMS_ (dvdmsvertrouwlijkheid) en kan alleen dynamisch worden overschreven indien de sjabloonkolom leeg is.
- Indien _Sectie: KoppelingDOCNAARDMS_ en _Item: AuteurVerplicht_ is aangevinkt dan wordt de Auteur gevuld met de medewerkerscode van de inlogger.
- Indien _Sectie: KoppelingDOCNAARDMS_ en _Item: VerzenddatumSturen_ is aangevinkt dan wordt de Verzenddatum gevuld met systeemdatum _(yyyymmdd)_.

> [!WARNING] > **Let op:** indien een document wordt gecreëerd bij een zaak die geen extern zaak/DMS nummer heeft, dan worden bovenstaande metadata niet gevraagd (en het document wordt ook niet aan het DMS aangeboden).

Bovenstaande instellingen zijn van toepassing op situatie GEEN compartiment. Indien WEL compartiment dan wordt gekeken naar de instellingen voor DMS bij de compartimentdefinitie. Hier is ook de default Documenttype en Vertrouwelijkheid aan te geven.

### Automatisch aanmaak regel geregistreerde documenten (tbcorrespondentie) na creëren

Indien:

- _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft
- en het document is na creatie automatisch opgeslagen

dan wordt automatisch een regel aangemaakt of - indien de registratie al bestond: overschreven - in tbcorrespondentie ([Geregistreerde Documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md)).

Indien:

- Opslag op fileserver dan:
  - wordt de kolom dvdocfilenaam gevuld met map (van fileserver) + filenaam
- Opslag via cmis dan:
  - wordt de kolom dvdocfilenaam gevuld met map (van DMS) + filenaam
  - wordt de kolom dvintdoccode gevuld met de unieke documentidentifier uitgetrokken door het DMS
- Opslag via stuf zaken/DMS dan:
  - wordt de kolom dvdocfilenaam gevuld met filenaam
  - wordt de kolom dvintdoccode gevuld met de unieke documentidentifier uitgetrokken door het DMS
  - wordt de kolom dvintzaakcode gevuld met de unieke zaakidentifier waaronder het document is opgeslagen.

In alle gevallen wordt de verzenddatum _(ddbriefdatum)_ van de geregistreerde email gevuld met de systeemdatum _(yyyymmdd)_.

De controle op of een registratie al bestaat vindt plaats op de kolom dvdocfilenaam (is pad + documentnaam inclusief extensie).

### Briefnummer en gecrypte waardes

Zie: [Emailsjablonen](/instellen_inrichten/emailsjablonen.md).

#### Bijlagen

In de definitie van het emailsjabloon kan aangegeven worden of de uiteindelijke verzender de mogelijkheid krijgt om bijlages aan te wijzen.
Indien de kolom _bijlagen toevoegen_ bij dat sjabloon is aangevinkt, zal de verzender kunnen kiezen uit één of meer niet-vervallen geregistreerde documenten bij die zaak.

> [!WARNING] > **Let op:** overleg met de juiste personen in uw organisatie of het versturen van documenten per email toegestaan is alvorens u bijlagen in de email in de sjabloon toestaat.
