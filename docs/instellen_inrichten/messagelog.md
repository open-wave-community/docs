# MessageLog

Portaal Servicecentrum. Tegel _MessageLog_.

Screenidentifiers:

- MDLC_getMessageLogList.xml
- MDDLC_getMessageLogDetail.xml

In deze tabel tbmessagelog worden de verzonden en ontvangen berichten gelogd.

Deze lijst wordt alleen gevuld indien de instelling aangevinkt is van _Sectie: OWB_ en _Item: MessageLog_.

In kolom _Getal1_ van deze instelling staat het aantal dagen dat de loggingskaarten bewaard moeten blijven. Default is dat 31.

Om de lijst te kunnen zien moet de inlogger beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99. Alle knoppen zijn dan enabled.

De items van deze lijst kunnen niet gemuteerd worden!

## Triggers

### Trigger op lijstscherm

- Linksonder de refreshknop: De lijst wordt opnieuw opgehaald
- Rechtsboven de filteropties. Het aantal berichten in de messagelogtabel is met de toepassingen vanuit de taskscheduler enorm toegenomen. Er is om die reden een filter toegevoegd op datum/tijd , op bericht vanuit taskscheduler ja/nee en op rubriek.

De rubrieken worden door OpenWave automatisch toegekend aan het bericht. In de filter zijn alleen rubrieken zichtbaar en aanvinkbaar die daadwerkelijk in de messageloglist voorkomen, dus onder meer afhankelijk van de werkende koppelingen.

De rubrieksbenamingen spreken voor zich met twee uitzonderingen:
_De rubriek interne aanroep betekent dat een interne API-call met uitwisseling van gegevens heeft plaatsgevonden (en gelogd) zonder verkeer naar of van buiten.
_ De rubriek die toegekend wordt bij het exporteren van een zipfile naar een FTP-site door de reportcontainer. (toepassingen: inspectieview, i-go). Deze rubrieksnaam is op het detailscherm in te voeren bij de betreffende container (portaal: beheerportaal-nieuw, kolom: Werkbeheer, tegel: Container exportrapportages). Indien niets is opgegeven neem REM als rubriek de tekst: exportreportcontainer exporteren.

### Trigger op detailscherm

- Indien de cursor in het vak staat van het xml-bericht zelf, kan met de F11 toets een groot scherm worden geopend (en weer gesloten).
- In het menu opties de lijstknoppen download hoofd- en antwoordbericht als file. De filenaam wordt daarbij samengesteld met de de kolommen datum/tijdstip, berichtsoort, soapaction met als extensie het berichtformaat.

## De volgende berichtsoorten worden gelogd

### Ingekomen OLO-berichten

- vrgDi01AanvragenVooroverleg
- omvDi01AanbiedenAanvraag
- omvDu01LeverenAanvraag
- vrgDi01IndienenAanvulling
- vrgDi01VoegAdviesToe
- vrgDi01IntrekkenAanvraag
- vrgDi01VerwijderenAanvraag
- vrgDi01WijzigGemachtigde
- wwvDi01AanbiedenAanvraag
- wwvDu01LeverenAanvraag
- vrgDu01LeverenOrganisatieGegevens (deze worden wel gelogd, maar niet verwerkt)
- vrgDi01AanvragenAdvies (deze worden wel gelogd, maar niet verwerkt

### Uitgaande OLO-berichten

- vrgDi01KoppelZaakAanAanvraag

### Uitgaande Stuf zaak/DMS berichten

- genereerZaakidentificatie_Di02
- genereerDocumentidentificatie_Di02
- creeerZaak_Lk01
- voegZaakdocumentToe_Lk01
- actualiseerZaakstatus_Lk01
- geefLijstZaakDocument_Lv01
- geefZaakDocumentLezen_Lv01
- updateZaak_Lk01
- updateZaakDocument_Di02

### Ingekomen StuFZaken berichten

- zakLk01 (deze worden wel gelogd, maar alleen verwerkt indien tag <mutatiesoort> de waarde T heeft)
- zakLK02 (deze worden wel gelogd, maar alleen verwerkt indien tag <mutatiesoort> de waarde T heeft)

### Uitgaande StufBAG berichten

- tgoLv01 (vraag naar verblijfsobject en coördinaten op grond van woonplaatsnaam, openbareruimtenaam , huisnummer, huisletter en huisnummertoevoeging en dvgemeenteid)
- wplLv01 (vraag naar woonplaatsidentificatie op grond van woonplaatsnaam en gemeenteid)
- oprLv01 (vraag naar openbareruimteidentificatie op grond van openbareruimtenaam en woonplaatsidentificatie)

### Uitgaande soapbericht naar kadaster opvragen lijst maandmutaties

Het opvragen van de lijst met maandmutaties kan gelogd worden in de messagelog mits de instelling _Sectie: KadasterBag en Item: Messagelog_ aangevinkt is.

### Uitgaande StufBRP berichten

- npsLv01 (vraag naar personen op grond van BSN, postcode, adres)

### Uitgaande StufNHR berichten

Er wordt alleen gelogd indien - naast de algemene instelling - de instelling _Sectie: koppelingNHR en Item: Messagelog_ bestaat en is aangevinkt.

- vesLv01 (vraag naar bedrijven op grond van KvK, vestigingsnummer, postcode, adres)

### Uitgaande CompententBRP bericht

Er wordt alleen gelogd indien - naast de algemene instelling - de instelling _Sectie: koppelingBPR en Item: Messagelog_ bestaat en is aangevinkt.

- stelGbavVraag (vraag naar personen op grond van BSN, postcode, adres)

### Uitgaande CompententNHR bericht

Er wordt alleen gelogd indien - naast de algemene instelling - de instelling _Sectie: koppelingNHR en Item: Messagelog_ bestaat en is aangevinkt.

- ophalenVestiging (vraag naar vestiging op grond van KvK of vestigingsnummer)

### berichten naar Telecomprovider

Uitgaande berichten naar Telecomprovider die bericht (2-factor inloggen) omzet in sms.

### Uitgaande JSON-berichten naar Digitale checklisten

- GET user-id
- POST locatie
- POST dossier
- POST checklist
- GET answer

### Uitgaande API-berichten naar OpenWave Satellite

Uitgaande API-berichten naar OpenWave Satellite om vanuit de Cloud een fileshare te kunnen benaderen t.b.v. documenten.

Er wordt alleen gelogd indien - naast de algemene instelling - het volgende geldt:

- indien de zaak waar de documenten onder vallen behoort bij een compartiment, dan moet de kolom _Messagelog_ op de betreffende compartimentskaart (beheerportaal-Nieuw) aangevinkt zijn
  *indien de zaak NIET valt onder een compartiment, dan moet de instelling *Sectie: Satellite en Item: Messagelog\* bestaan en aangevinkt zijn. Het gaat om de volgende methodes:
- deletemap
- fileExist
- getFileList (geef lijst met aanwezige documenten)
- putfile
- getfile
- makedir
- movecopydelfile

### Ophalen en verplaatsen OLO-documenten vanaf fileserver

Interne API-berichten bij het verplaatsen van documenten van een fileshare naar de machine waar de WSAS op draait al vanwaar de documenten naar de plaats van bestemming worden geredigeerd. Er wordt alleen gelogd indien - naast de algemene instelling - de instelling _Sectie: InboxmapOLO en Item: Messagelog_ bestaat en is aangevinkt.

- uploadFile (upload file op basis van OLO-nummer)

### Documentconverter

Uitgaande API-berichten naar de documentconverter om documenten met de extensies doc, docx, xs, xlsx , odt, ods en xml en txt te renderen als pdf-document.
Er wordt alleen gelogd indien - naast de algemene instelling - de instelling _Sectie: Koppeling Converter en Item: Messagelog_ bestaat en is aangevinkt.

- GET convertDocument

### Erkende Maatregelen

Uitgaande vraagberichten naar RVO voor ophalen meldingen erkende maatregelen.
Er wordt alleen gelogd indien - naast de algemene instelling - de instelling _Sectie: ErkendeMaatregelen Item: Messagelog_ bestaat en is aangevinkt.

- vraagGegevensIndividueleInrichtingRequest
- vraagLijstInrichtingIDsRequest

### Inkomende DSO Stamberichten

Er wordt alleen gelogd indien - naast de algemene instelling - de instelling _Sectie: DSO Item: Messagelog_ bestaat en is aangevinkt.

- Triggerbericht
- Verzoekbericht

Indien _Getal1_ de waarde 1 heeft worden alle berichten die binnenkomen op het https:POST endpoint servernaam/DSO/Verzoek/ gelogd.

### Uitgaande DSO berichten

(gerelateerde zaken, gemiste verzoeken, wijzig bevoegd gezag)

Er wordt alleen gelogd indien - naast de algemene instelling - de instelling _Sectie: DSO-Verzoekafhandelen_ en _Item: MessageLog_ bestaat en is aangevinkt.

### Samenwerkingsfunctionaliteit

De operation voor het ophalen van openstaande inkomende actieverzoeken wordt alleen gelogd indien de instelling _Sectie: SWF en Item: MessageLog_InkomendeActieverzoeken_ is aangevinkt. Dit is namelijk niet altijd nodig en bovendien verzwarend, vandaar deze instelling.

Uitgaande berichten naar samenwerkingsfunctionaliteit (nieuwe samenwerkingsruimte, nieuwe actieverzoek, uploaden en downloaden van documenten, synchroniseren van notificaties) vanuit de tegel _Samenwerkingsruimte_ bij een omgevingszaak, worden wel altijd gelogd in de tabel tbmessagelog.

### DROP

De uitgaande dropberichten worden gelogd indien de instelling _Sectie: DROPPUBLICATIES en Item: MessageLog_ is aangevinkt. Indien niet aangevinkt en de DROP wordt aangeroepen vanuit één specifieke zaak (detailpagina van één item van de lijst DROP op openingsportaal) wordt toch gelogd.

### Export reportcontainer

De uitgaande zipfiles richting FTP-site worden gelogd indien - naast de algemene instelling - ook de op de betreffende kaart van tbreportcontainer de kolom dlmessagelog aangevinkt is.

### Ophalen ontbrekende OLO-documenten van FTP-site en ophalen ontbrekende DSO-documenten via DSO rest API verzoeken

De uitgaande berichten worden gelogd indien - naast de algemene instelling - ook de instelling _Sectie: koppeling OLO en Item: FTP-messagelog_ aangevinkt is.

### Uitgaande REV JSon berichten

- wijzigen / toevoegen GebouwenOfLokaties
- wijzigen / toevoegen /ophalen LocatieEvActiviteiten

De Json-berichten (post en put) voor register externe veiligheid worden gelogd indien - naast de algemene instelling - ook de instelling _Sectie: REV en Item: Messagelog_ aangevinkt is.

### Uitgaande Xential

- impersonate
- getusubletemplates
- createTicket
- logout

De Json-berichten (post en get) voor Xential worden gelogd indien - naast de algemene instelling - ook de instelling _Sectie: Xential en Item: Messagelog_ aangevinkt is.
