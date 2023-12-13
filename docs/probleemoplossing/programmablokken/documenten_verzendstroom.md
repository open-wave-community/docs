# Documenten/Verzendstroom

Op deze pagina wordt een mogelijke stroom weergegeven vanaf het creëren van een document m.b.t.

- aanwijzen van bijlages
- uitzetten van collegiale toetsen
- afkeuren van definitieve uitgaande documenten
- pdf maken van document
- ondertekenen van definitieve documenten
- versturen van definitieve uitgaande documenten inclusief bijlages

## Gebruik van geregistreerde documenten

De beschreven situaties zijn van toepassing indien gebruik wordt gemaakt van geregistreerde documenten (tbcorrespondentie). De documenten en bijlagen die verstuurd gaan worden moeten een kaart hebben in deze tabel, waarin de status van een document en overige metadata wordt bijgehouden.

**De lijst geregistreerde documenten bij een zaak kan op twee verschillende manieren worden benaderd:**

- Onder een tegel op de diverse zaakportalen: in dat geval moet:
  - de instelling _Sectie: Documenten en Item: documentregistratie_ NIET aangevinkt zijn
  - en moet de tegel toegekend zijn aan de medewerkers.
- Vanuit de knop _DOCS_ boven aan de portaalschermen of onderaan in het detailscherm van een zaak. In dat geval moet:
  - de instelling _Sectie: Documenten en Item: Documentregistratie_ WEL aangevinkt zijn.

**Qua rechten op geregistreerde documenten geldt het volgende:**

- Om de lijst en detailpagina van een geregistreerde document te mogen inzien, moet de medewerker het recht _Inzien geregistreerde documenten_ hebben voor de betreffende module (bijv. tbomgrechten.dlcomgcorregvsb). Het onderliggende document zelf is hiermee ook op te halen.
- Om metadata te veranderen (geldt ook voor collegiale toetsen en toevoegen/verwijderen van bijlages) moet de medewerker het recht _Registreren en wijzigen metadata van geregistreerde documenten_ (bijv. dlcomgcoredt) hebben. Dit recht is ook nodig om een document wat nog niet geregistreerd is alsnog te registreren.
- Om een document - al of niet inclusief bijlages - te kunnen downloaden is het recht _Toelaten geforceerde download geregistreerd document_ (bijv. dlcomgcorregdwl) van toepassing.

### Automatische registratie

- Alle documenten die op basis van een sjabloon gecreëerd worden, mits _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft.
- Alle documenten die met de uploadknop naar OpenWave worden gebracht, mits de instelling _Sectie: Documentregisteren Item: AlleHandmatigeUploads_ is aangevinkt.
- Alle OLO/DSO documenten, mits de instelling _Sectie: Documentregisteren Item: AlleOLODSOUploads_ aangevinkt is. Indien er voor het binnengekomen document een corresponderend record bestaat in vwfrmoloberichten, zal de hier gevonden omschrijving worden opgenomen in het veld _Korte omschrijving_ bij de documentregistratie. Tevens wordt veld _(O)LO,(D)SO,(S)WF?_ voor OLO documenten gevuld met **O** om aan te geven dat het om een OLO document gaat en voor DSO documenten met **D** om aan te geven dat het om een DSO document gaat.
- Alle geselecteerde SWF documenten (dus alleen die gebruiker zelf selecteert bij de SWF documentenlijst van een SWF ruimte), mits de instelling _Sectie: Documentregisteren Item: AlleGeselecteerdeSWFUploads_ aangevinkt is. Voor deze registraties zal het unieke SWF documentid worden opgeslagen zodat bij de SWF documentenlijst zichtbaar is welke documenten al geregistreerd zijn. Tevens wordt veld _(O)LO,(D)SO,(S)WF?_ gevuld met **S** om aan te geven dat het om een SWF document gaat.

Het programma zal bij het registreren het document altijd koppelen aan de hoofdzaak/inrichting.

### Handmatige registratie

Dit kan alleen vanuit de documentenlijst die kijkt naar alle documenten op fileserver c.q. DMS. Deze algemene lijst is zichtbaar onder de knop _DOCS_ bovenaan in de portalen en link onderaan in het detailscherm van een zaak mits:

- de gebruiker het recht _Inzien documenten buiten registratie om_ (bijv. tbomgrechten.dlcomgcorvsb) heeft
- en de instelling _Sectie: Documenten Item: Documentregistratie_ NIET is aangevinkt. |

Vanuit deze lijst kan de gebruiker een of meer documenten registreren. De documenten voorzien van het potloodicoontje, zijn reeds geregistreerd. Om te registreren moet de gebruiker het recht _Registreren en wijzigen metadata van geregistreerde documenten_ (bijv. dlcomgcoredt) hebben.

## De statussen

In zijn algemeenheid geldt voor de blokken **adressering** en **status** dat de kolommen hierin alleen muteerbaar zijn indien de verstuurddatum (tbcorrespondentie.ddbriefdatum) nog leeg is. Voor de kolom **verstuurd** zelf geldt dit dan weer niet.
Voor een geregistreerd document is een aantal statussen van belang:

- De **richting**. (U)itgaand is een voorwaarde om opgenomen te worden in de Taaklijsten _Te ondertekenen_ en _Te versturen_. Bij documenten die gecreëerd zijn op basis van een sjabloon en automatisch geregistreerd worden, is Uitgaand de standaard richting. De kolom mag NIET gemuteerd worden als de registratie status definitief heeft, en/OF de verstuurd datum is gevuld en/OF er bij de sjabloondefinitie waarop het document gebaseerd is aanstaat dat het document per post verstuurd moet worden.
- **Definitief**. Definitief = Ja is een voorwaarde om opgenomen te worden in de Taaklijsten _Te ondertekenen_ en _Te versturen_. Indien op Ja gezet wordt _Brief moet aangepast?_, dan wordt definitief automatisch uitgevinkt. Met de knop _PDF_ (zie hieronder) wordt de status automatisch op Definitief gezet.
- **Moet dig. ondertekend worden?**. Is een eigenschap de hoort bij het sjabloon, maar overgenomen wordt in het geregistreerde document (dlmoetdigondertekenen) dat op basis van dat sjabloon is gemaakt. Alleen een medeweker met de eigenschap tbmedewerkers.dlmagmoetdiotaanpassen mag deze kolom muteren.

Indien de kolom dlmoetdigondertekenen aangevinkt is terwijl de kolom _Digitaal ondertekend?_ niet is aangevinkt, dan wordt het document opgenomen in de Taaklijst _Te ondertekenen_.

- **Digitaal ondertekend?**. Alleen muteerbaar door een inlogger met de eigenschap magdigitaalondertekenen (in de medewerkerstabel) voor Definitieve en Uitgaande documenten. Is een voorwaarde -mits _Moet digitaal ondertekend worden_ ook aangevinkt is- om opgenomen te worden in de Taaklijst _Te versturen_. Indien _Is digitaal ondertekend_ is aangevinkt worden mutaties op de collegiale toetsen en bijlages geblokkeerd en wordt een dergelijk document alleen readonly geopend.
- Lege **verstuurd datum** is een voorwaarde om opgenomen te worden in de Taaklijst _Te versturen_. Indien verstuurd is gevuld worden mutaties op de collegiale toetsen en bijlages geblokkeerd en wordt een dergelijk document alleen readonly geopend.
- **Brief moet aangepast ?**. Alleen muteerbaar door een inlogger met de eigenschap _magdigitaalondertekenen_ (in de medewerkerstabel) voor Definitieve en Uitgaande documenten, die nog niet digitaal ondertekend zijn. Indien aangevinkt wordt Definitief automatisch op Nee gezet. Aangevinkt zijn is een voorwaarde om opgenomen te worden in de Taaklijst _Aan te passen documenten_. Om het veld uit te vinken moet Definitief op Ja worden gezet.
- **Locatie** van document. Hier wordt alleen naar gekeken indien _Getal2_ van de instelling _Sectie: Documenten en Item: Documentregistratie_ de waarde 1 heeft. Als dit het geval is kan een document nog bewerkt worden mits de locatie de waarde (S) heeft (en nog niet verstuurd is en nog niet digitaal ondertekend is). Een andere waarde dan S suggereert namelijk dat het document lokaal is gedownload ter bewerking. Het openen van een dergelijk document is dan readonly.
- **Post of Email**. Indien de registratie automatisch is aangemaakt vanuit het creëren van een document op basis van een documentsjabloon, en tijdens het creëren is de keuze gemaakt voor _Per Post_, dan is deze keuze hier overgenomen en NIET Muteerbaar (onder water heeft de onzichtbare kolom _tbcorrespondentie.dlperpostvastbijaanmaak_ in dat geval de waarde T gekregen).

De kolom is ook niet meer muteerbaar indien Definitie = Ja en richting is Uitgaand.
Indien per mail dan is onderaan de pagina een email-knop zichtbaar (kijk hieronder bij verzenden per mail voor overige condities), waarmee een standaard email verstuurd kan worden met het document (en alle bijlages die bij het document horen) als bijlage bij die mail. Die mail wordt ook naar alle cc's verstuurd.

## Aanwijzen van te versturen bijlages bij creëren van document

Indien:

- de instelling _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft (hetgeen betekent dat gecreëerde documenten automatisch worden opgeslagen in geregistreerde documenten (tbcorrespondentie))
- en bij het documentsjabloon is de eigenschap _Bijlages aanwijzen uit geregistreerde documenten_ aangevinkt (tbdocumenten.dlbijlagesregdoc)

dan komt er een nieuwe pagina in de wizard _Creëer Document_, waarbij de inlogger één of meer andere geregistreerde documenten kan aanwijzen die horen bij dezelfde zaak als waarvoor het document wordt gecreëerd.

Indien de instelling _Sectie: DocumentRegistreren_ en _Item: BijlagenAlleenDefinitief_ is aangevinkt dan kunnen alleen geregistreerde documenten met de eigenschap dvdefinitief = J worden aangewezen als bijlage.

Deze bijlages komen in een nieuwe tabel tbcorrespbijlages die gekoppeld is aan het geregistreerde document (zie detailpagina van dat document).

Voor het opnemen van een verwijzing naar de bijlages in het gecreëerde document zie kopje _Speciale childquery: Opsommen aangewezen bijlages_ van [Documentsjablonen en Sjabloongroepen](../../../instellen_inrichten/documentsjablonen.md).

### Bijlages bij te versturen document

Aan een geregistreerd document kunnen één of meer bijlages worden toegevoegd uit de lijst met de overige geregistreerde (definitieve) documenten bij dezelfde zaak. De lijst is zichtbaar vanuit het detailscherm van een document.

Indien de instelling _Sectie: DocumentRegistreren_ en _Item: BijlagenAlleenDefinitief_ is aangevinkt dan kunnen alleen geregistreerde documenten met de eigenschap dvdefinitief = J worden aangewezen als bijlage.

De bijlages kunnen al toegewezen zijn tijdens het creëren van een document. Zolang het moederdocument niet is verstuurd of digitaal ondertekend, kunnen bijlages worden bijgevoegd of verwijderd, mist de inlogger het recht _Registreren en wijzigen metadata van geregistreerde documenten_ (bijv. tbomgrechten.dlcomgcoredt) voor de betreffende module heeft.

Indien er geen insert mogelijkheden meer zijn is de plusknop disabled.

Wanneer een inlogger het recht _Toelaten geforceerde download geregistreerd document_ (bijv. tbomgrechten dlcomgcorregdwl) dan is onderaan het detailvenster van een geregistreerd document een downloadknop zichtbaar met de betekenis: download document inclusief bijlagen.

Indien er bijlagen zijn, dan worden deze met het hoofddocument gedownload in een zipfile naar de device van de inlogger. De naam van die file is: DownloadOpenWave_datum_tijstip.zip bijv. DownloadOpenWave_20201126_093926.zip.

Indien er GEEN bijlagen zijn, dan worden alleen het hoofddocument gedownload naar de device van de inlogger.

### Aanwijzen en beheren van cc's bij creëren van document

Indien:

- de instelling _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft (hetgeen betekent dat gecreëerde documenten automatisch worden opgeslagen in geregistreerde documenten (tbcorrespondentie))
- en de eigenschap _Contactpersoon verplicht_ bij het sjabloon is aangevinkt (tbdocumenten.dlcontactverplicht = T)
- en bij het creëren van het document kiest de gebruiker voor de richting Uitgaand

dan komt er een nieuwe pagina in de wizard _Creëer Document_, waarbij de inlogger één of meer cc's uit de lijst van contactpersonen van de bovenliggende zaak kan aanwijzen (maar andere dan de hoofdcontactpersoon).

Deze cc's komen in een nieuwe tabel tbcorafschriften die gekoppeld is aan het geregistreerde document (zie detailpagina van dat document).

### Muteren cc's

Dubbel klikken op een cc-regel opent de adreskaart, waar mutaties op kunnen plaatsvinden (mits geautoriseerd).
De insertknop en deleteknop voor de cc's zijn enabled indien de gebruiker kijkrechten heeft op adressen. De aangeroepen wizards kijken ook of:

- de compartimentsrechten ok zijn
- en de correspondentie-edit rechten ok zijn. (bijv. tbomgrechten.dlcomgcoredt)
- en de blokkering van de bovenliggende zaak nog leeg is
- en de verstuurddatum van de bovenliggende correspondentiekaart moet leeg zijn en nog niet digitaalondertekend.

Indien de instelling _Sectie: DocumentRegistreren en Item Inrichtingcontactpersonen_ aangevinkt is kan de gebruiker bij het opvoeren van cc’s of bcc’s ook kiezen uit de contacten die horen bij de inrichting die aan de hoofdzaak is gekoppeld.

De gebruiker kan voor de cc’s, bcc’s in principe alleen maar kiezen uit personen die geen hoofdgeadresseerde zijn (de hoofdgeadresseerde wordt gekozen in de wizard bij het aanmaken van het te versturen document en staat in het blok adressering van het geregistreerde document) behalve als Per Post verzenden is aangevinkt (dlmoetperpost = T) op de correspondentiekaart: dan mag ook de hoofdgeadresseerde worden opgevoerd als cc of bcc. Die krijgt in dat geval zowel een brief per post als een document per email.

In het lijstscherm van de cc’s bij een geregistreerd document kan bcc of cc in het aanvinkvakje op de regel worden aangepast. De defaultwaarde van dit vakje is cc, maar indien de instelling _Sectie: DocumentRegistreren en Item: Emailccalsbcc_ is aangevinkt dan bcc.

### Emailknop bij cc's

De emailknop onderaan de lijst van cc's, bcc's kan gebruikt kan worden als - onder meer - het document definitief is en/of _datum verstuurd_ gevuld is.
Met het indrukken van die knop:

- wordt dat document (+ bijlages) als cc of bcc verstuurd naar de aangewezen contactpersonen voor die rijen waarvan de kolom **verzonden** (_tbcorafschriften.ddemailverzonden_) nog leeg is
- wordt dat document (+ bijlages) verstuurd naar het emailadres van de gebruiker (inlogger) zelf als hoofdgeadresseerde
- wordt bij succes de kolom _ddemailverzonden_ gevuld van de aangewezen contactpersonen met timestamp.

Met het indrukken van de knop zal het programma een vaste email (het onderwerp in kolom _Tekst_ van instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstAanhef_ en de body in kolom _Tekst_ c.q. _Toelichting_ van instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstBody_) verzenden naar het emailadres van de betrokken cc's, bcc's. Het bijbehorende document en ook de documenten die als bijlage daaraan zijn gelinkt worden als bijlage bij die email opgenomen. De kolom _Toelichting_ van de instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstBody_ gaat boven de kolom _Tekst_ (dvtoelichting is veel groter)..

### Collegiale toetsing bij geregistreerde documenten

Bij een geregistreerd document kunnen een of meer collegiale toetsen (tbcorrespcollegtoets) worden uitgezet (zie lijstje collegiale toetsing bij een detailscherm van een geregistreerd document).

Voor de wijzig- en insert- en deleterechten op een collegiale toets is het recht _Registreren en wijzigen metadata van geregistreerde documenten_ (bijv. tbomgrechten.dlcomgcoredt) nodig. Mutaties zijn geblokkeerd indien het _moederdocument_ digitaal ondertekend is of verstuurd.

Bij de collegiale toetsing horen de volgende tegels die opgenomen zijn in de portaaltegels bij het openingsscherm onder kolom _Mijn taken_, maar die de applicatiebeheerder nog zelf moet toekennen aan medewerkers:

- Tegel **Mijn uitgezette collegiale toetsen** (die nog niet zijn getoetst). De tegel geeft toegang tot een lijst van collegiale toetsen waarvoor geldt dat de toets datum nog leeg is (dddatumgetoetst) en de aanvrager van die toets is de inlogger en het bovenliggende document is nog niet verstuurd en niet digitaal ondertekend.
- Tegel **Mijn uit te voeren collegiale toetsen**. De tegel geeft toegang tot een lijst van collegiale toetsen waarvoor geldt dat de toets datum nog leeg is (dddatumgetoetst) en de toetser (dvcodemwvoorwie) is gevuld met de inlogger en het bovenliggende document is nog niet verstuurd en niet digitaal ondertekend.
- Tegel **Aan mijn geretourneerde collegiale toetsen**. De tegel geeft toegang tot een lijst van collegiale toetsen waarvoor geldt dat de toets datum (dddatumgetoetst) gevuld is, maar de kolom dlgezien is niet aangevinkt en de aanvrager van die toets is de inlogger en het bovenliggende document is nog niet verstuurd en niet digitaal ondertekend.
- Tegel **Team uit te voeren collegiale toetsen**. De tegel geeft toegang tot een lijst van collegiale toetsen waarvoor geldt dat de toets datum nog leeg is (dddatumgetoetst) en de collegiale toets op een team (dnkeyteamsverantw) staat waar de inlogger lid van is en het bovenliggende document is nog niet verstuurd en niet digitaal ondertekend.

Voor de bovenstaande vier lijsten geldt de extra restrictie dat het document wat getoetst moet worden, een lege (of gevuld maar met datum in de toekomst) vervaldatum heeft.

Dubbel klikken op een item van die lijst zorgt ervoor dat de inlogger op de detailkaart van het geregistreerde document komt, waar de collegiale toets bij hoort. De knop linksonder zorgt ervoor dat het bijbehorende zaakportaal waar het geregistreerde document onder valt, wordt geopend.

De medewerker die de toetsen heeft uitgezet zal dus bij retournering zelf het aanvinkvakje _Gezien_ (dlgezien) moeten aanvinken om de toets uit de lijst _aan mij geretourneerde toetsen_ te halen.

Ook in de lijsten met openstaande zaken zijn kolommen met aantallen uitstaande, geretourneerde en geziene toetsen zichtbaar te maken. Als voorbeeld bij openstaande omgevingszaken door de instelling _Sectie: Programma en Item: OmgAantCollegToetsZichtbaar_ aan te vinken. Navenant voor _Item: HahAantCollegToetsZichtbaar en Item: HorAantCollegToetsZichtbaar en Item: APVAantCollegToetsZichtbaar en Item: InfAantCollegToetsZichtbaar_.

### Collegiale Toets informatie op Zaakportalen

Op de zaakportalen zijn tegels met collegiale Toetsen gedefinieerd onder de kolom _BehandelingProces_ (maar NIET automatisch toegekend aan medewerkers). De tegel opent een lijst met alle collegiale toetsen bij die zaak. Met doorklikken wordt de detailpagina van het geregistreerde document geopend, die bij de toets hoort.

### Ondertekenen of afkeuren van geregistreerde documenten

De kolom _Moet dig. ondertekend worden?_. Deze eigenschap van het sjabloon komt mee met het creëren van een document. De kolom is aanpasbaar indien:

- de gebruiker het recht _Mag kolom moet digitaal ondertekend worden aanpassen_ heeft (tbmedewerkers.dlmagmoetdiotaanpassen)
- de documentrichting van de kaart Uitgaand is
- de verstuurd datum van het document nog leeg is.

De kolom **richting** (uitgaand, intern of binnenkomend) kan niet meer gemuteerd worden indien definitief = Ja.

De kolom **Digitaal ondertekend?** is alleen muteerbaar indien:

- de inlogger de eigenschap _Mag digitaal ondertekenen_ aangevinkt heeft staan op de medewerkerskaart
- en de status definitief = (J)a
- en de richting van het document = (U)itgaand.

Alleen de digitale ondertekenaar kan een klaargezet document (dus Definitief en Uitgaand) afkeuren door het vakje _Brief moet aangepast?_ aan te vinken en eventueel een reden te vullen. Hiermee wordt automatisch de kolom _Definitief_ op (N)ee gezet.
Wanneer de kolom _Definitief_ weer op (J)a wordt gezet, zal het aanvinkvakje _Brief moet aangepast?_ automatisch leeggemaakt worden. De reden blijft staan.

Er zijn twee Taaklijsten opgenomen in de portaaltegels bij het openingsscherm onder kolom _Mijn taken_, maar die de applicatiebeheerder nog zelf moet toekennen aan medewerkers:

- Tegel **Te ondertekenen**. De tegel geeft toegang tot een lijst van te ondertekenen documenten waarvoor geldt dat:
  - **Verstuurd datum** leeg is
  - en **Definitief** = 'J'
  - en **Moet dig. ondertekend worden?** is aangevinkt
  - en **Digitaal ondertekend?** is niet aangevinkt
  - en de inlogger _mag digitaal ondertekenen_ (eigenschap van de medewerker in medewerkerstabel)
  - en de vervaldatum van het document is niet gevuld of groter dan vandaag.
- Tegel **Mijn aan te passen documenten**. De tegel geeft toegang tot een lijst van afgekeurde documenten waarvoor geldt dat:
  - **Brief moet aangepast?** aangevinkt is
  - en de inlogger is de actieve dossierbehandelaar van de zaak waar document bij hoort
  - en de vervaldatum van het document is niet gevuld of groter dan vandaag.

Dubbel klikken op een item van die lijst zorgt ervoor dat de inlogger op de detailkaart van het betreffende geregistreerde document komt. De knop linksonder zorgt ervoor dat het bijbehorende zaakportaal waar het geregistreerde document onder valt, wordt geopend.

### Maak PDF

Vooralsnog uitdrukkelijk bedoeld voor documenten die zich op een fileshare bevinden. Kan getriggerd worden door de PDF-knop onderaan het detailscherm of na digitale ondertekening.

Na digitale ondertekening mits

- het betreffende document nog geen PDF is( de extensie van upper(dvdocfilenaam) <> ‘PDF’)
- en dat document bevindt zich op de server (en niet lokaal): dvdocplaats moet de waarde S hebben.
- en de instelling _Sectie: DocumentRegistreren en Item: MaakPDFbijOndertekening_ is aangevinkt

De knop PDF wordt zichtbaar op het detailscherm van een geregistreerd document indien:

- de instelling _Sectie: DocumentRegistreren en Item: KnopMaakPDFZichtbaar_ is aangevinkt
- en de geregistreerde documentkaart muteerbaar is (en niet geblokkeerd). Dus de medeweker heeft het recht _Registreren en wijzigen metadata van geregistreerde documenten_ (bijv. dlcomgcoredt)
- en de extensie van het document = ods, odt, odf, doc, docx, xls,xlsx of txt of xml
- en de plaats (locatie) van het document = (S) erver (dat betekent dat het document dus NIET gemarkeerd staat als _wordt lokaal bewerkt_).
- en het document nog niet verstuurd is (ddbriefdatum is leeg).

De PDF-knop wordt echter alsnog onzichtbaar indien

- het document digitaal ondertekend met worden (vwfrmcorrespondentie.dlmoetdigondertekenen = T)
- en de instelling _Sectie: DocumentRegistreren en Item: MaakPDFbijOndertekening_ is aangevinkt
- en kolom _Getal1_ van de instelling _Sectie: DocumentRegistreren en Item: KnopMaakPDFZichtbaar_ heeft waarde 1

Met het indrukken van de knop of digitale ondertekening wordt een actie gestart waarbij het document omgezet wordt naar PDF en opgeslagen op de plek waar het document vandaan kwam. Deze pdf behoud dezelfde registratie in de geregistreerde documenten (alleen de extensie van de filenaam verandert en eventueel de externe documentidentificatiecode bij opslag in DMS). De registratie van het oorspronkelijke document wordt dus vervangen door de PDF. Het fysieke oorspronkelijke document zelf wordt dus niet verwijderd, maar is niet meer via de geregistreerde documenten terug te vinden. De eigenschap Definitief op de registratiekaart van de nieuwe pdf wordt op (J)a gezet (een voorwaarde voor digitale ondertekening).

Als de knop zichtbaar is, is direct ook de knop refresh scherm zichtbaar. Dit komt omdat het programma niet weet wanneer de omzetting naar PDF afgerond is (externe schijven c.q. extern DMS). Met de refreshknop wordt het scherm opnieuw uitgeschreven en zullen de knoppen verdwijnen en zal de extensie .pdf zichtbaar worden.

Indien _Getal1_ van _Sectie: Documenten en Item: ConverteerPDF_ de waarde 1 heeft dan worden documenten geconverteerd naar PDF via de OnlyOffice installatie (mits aanwezig). Indien deze instelling niet bestaat of _Getal1_ heeft een andere waarde, dan wordt geconverteerd met LibreOffice. In dat laatste geval moet de kolom _Tekst_ van de instelling _Sectie: Koppeling Converter en Item: EndpointClassDocument_ gevuld zijn met een valide endpoint van de converter. Bijvoorbeeld: `http://localhost:9763/services/nl.rem.docconv.manager.published.Documents.nl.rem.docconv.manager.published.DocumentsHttpsSoap11Endpoint/`

## Readonly en blokkeren van wijzigingen

Wanneer een document hier digitaal ondertekend is OF wanneer de verstuurd datum gevuld is dan wordt daarmee het document readonly en kunnen geen bijlages en/of cc's en/of collegiale toetsen worden toegevoegd.

## Verzenden per email

Een email-knop onderaan de pagina is zichtbaar indien aan de volgende condities is voldaan:

- verzendwijze = email (tbcorrespondentie.dlmoetperpost = ‘F‘)
- en de richting is uitgaand (tbcorrespondentie.dvdocrichting = ‘U’)
- en Definitief is Ja (tbcorrespondentie.dvdefinitief = ‘J’)
- en het document is nog niet verstuurd (tbcorrespondentie.ddbriefdatum is null)
- en het document wordt niet lokaal bewerkt (tbcorrespondentie.dvdocplaats = ‘S’)
- en – indien het document digitaal ondertekend moet zijn -, dan moet tbcorrespondentie.dlisdigondertekend de waarde T hebben
- en de kolom _Tekst_ van instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstAanhef_ moet gevuld zijn
- en de kolom _Tekst_ OF de kolom _Toelichting_ van instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstBody_ moet gevuld zijn. Indien beide gevuld kijkt OpenWave naar de kolom _Toelichting_ (dvtoelichting), waarin 2000 karakters kunnen staan i.p.v. 255 van de kolom _Tekst_.

Met het indrukken van de knop zal het programma een vaste email (het onderwerp in kolom _Tekst_ van instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstAanhef_ en de body in kolom _Tekst_ c.q. _Toelichting_ van instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstBody_) verzenden naar het emailadres op de correspondentiekaart. Het bijbehorende document en ook de documenten die als bijlage daaraan zijn gelinkt worden als bijlage bij die email opgenomen. De email wordt ook verzonden naar alle cc’s, bcc's die bij dat document geregistreerd zijn (in tabel tbcorafschriften) en waarvoor geldt dat de kolom _ddemailverzonden_ nog leeg is. De kolom _Toelichting_ van de instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstBody_ gaat boven de kolom _Tekst_ (dvtoelichting is veel groter)..

Het programma controleert eerst of:

- Compartiment OK is
- en of de gebruiker het recht heeft: _Registreren en wijzigen metadata van geregistreerde documenten_ (bijv. dlcomgcoredt)
- en of de kolom email van de inlogger bij de medewerkerstabel is gevuld zijn met een valide emailadres
- en of de webmailinstellingen kloppen [E-mail SMTP instellingen](../../../instellen_inrichten/email.md)
- en of de te maken bijlage(s) wel allemaal pdf zijn.

In het onderwerp en de body kunnen variabelen zijn gedefinieerd die het programma on the fly substitueert:

- %zaaknaam% met de zaakomschrijving (aanvraagnaam)
- %soortvergunning% met de zaaktype omschrijving
- %zaakcode% met de Openwave zaakcode
- %lokatie% met straat + huisnummer + plaats (van waar de zaak speelt)
- %olonummer% met OLO c.q. DSO-nummer
- %startdatum% met de startdatum van de zaak
- %inlogger% met de volledige naam van de inlogger met achternaam eerst (Boer, P. de)
- %dossierbehandelaar% met de volledige naam van de actieve dossierbehandelaar met achternaam eerst (Boer, P. de)
- %inloggervoluit% met de volledige naam van de inlogger met voorletters, tussenvoegsel, achternaam (P. de Boer)
- %dossierbehandelaarvoluit % met de volledige naam van de actieve dossierbehandelaar met voorletters, tussenvoegsel, achternaam (P. de Boer)

Indien de instelling _Sectie: DocumentRegistreren en Item: MailAlleenPdf_ aangevinkt is, zal de wizard controleren of alle mee te sturen documenten wel van het formaat pdf zijn. Het daadwerkelijk versturen van de email gebeurt in een runnable (het ophalen en plaatsen van de bijlages kan anders een time-out veroorzaken). De inlogger krijgt een cc van de verstuurde email - of, - wanneer er iets fout gaat - een tekst in de mail met de reden waarom de verzending niet is doorgegaan. Bij succes wordt de verstuurddatum (tbcorrespondentie.ddbriefdatum) automatisch gevuld en wordt ook bij elke cc, bcc de datum*ddemailverzonden* gevuld.

Er is nog een instelling waar het programma naar kijkt: De grootte van de te versturen email in MB’s inclusief bijlages mag niet _Getal1_ van de instelling _Sectie: DocumentRegistreren en Item: Maxgrootteemail_ te boven komen. Zo ja, dan ziet de inlogger in de mail dat de verzending om deze reden niet gelukt is.

### Te versturen documenten (per post)

Er is een Taaklijst die opgenomen is in de portaaltegels bij het openingsscherm onder kolom _Mijn taken_, maar die de applicatiebeheerder nog zelf moet toekennen aan medewerkers:

Tegel **Te versturen documenten**. De tegel geeft toegang tot een lijst van te versturen documenten waarvoor geldt dat:

- **Verstuurd datum** leeg is
- en **Definitief** = 'Ja
- en **(U)itgaand**
- en **Verzendwijze per post** (dlmoetperpost = T)
- en Vervaldatum is leeg of ligt in de toekomst
- en:
  - OF **Moet dig. ondertekend worden?** is aangevinkt en **Digitaal ondertekend?** is aangevinkt
  - OF **Moet dig. ondertekend worden?** is niet aangevinkt.

Dubbel klikken op een item van die lijst zorgt ervoor dat de inlogger op de detailkaart van het betreffende geregistreerde document komt. De knop linksonder zorgt ervoor dat het bijbehorende zaakportaal waar het geregistreerde document onder valt, wordt geopend.

Het vullend van de verstuurd datum zelf is een handmatige actie van de degene die daadwerkelijk documenten verstuurd.

Voor het downloaden van een document inclusief bijlages zie hierboven bij kopje _bijlages_.

Aangetekend en track- en tracecode: zie kopje _Blok Aangetekend_ bij [Detailscherm Geregistreerd Document](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/detailscherm_geregistreerd_document.md).
