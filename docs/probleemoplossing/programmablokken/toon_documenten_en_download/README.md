# Toon documenten en bewerk/download

Met de knop _Docs_ op de detail- en portalschermen van omgeving, inrichting, APV/overig, bouw/sloop, horeca, infoaanvragen en handhaving alsmede vanuit de advies, bezwaarberoep en inspectie detailschermen kan een lijst getoond worden van documenten bij een zaak. Indien de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt zal de lijst bestaan uit de geregistreerde documenten (uit tbcorrespondentie) zie: [Geregistreerde Documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md).
Staat deze instelling uit dan worden alle documenten bij de zaak getoond worden die op dat moment worden aangetroffen in het DMS of op de fileserver.

## Rechten

De gebruiker moet kijkrechten hebben bij de betreffende module (omgeving, inrichting, horeca, milieu/gebruik, APV/overig, bouw/sloop en handhaving).

Indien echter de documenten worden opgehaald vanuit een inspectiezaak geldt dat het programma kijkt naar de inspectiekijkrechten van de betreffende module. Zo ook voor adviezen: het programma kijkt naar de advieskijkrechten van de betreffende module. Zo ook voor bezwaarberoep: het programma kijkt naar de bezwaarberoep kijkrechten van de betreffende module.

Daarnaast geldt dat indien de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt de gebruiker het recht _Inzien geregistreerde documenten_ moet hebben voor de betreffende module (bijv. tbomgrechten.dlcomgcorregvsb).

Indien deze instelling NIET is aangevinkt dan moet de gebruiker het recht _Inzien documenten buiten registratie om_ hebben voor de betreffende module (bijv. tbomgrechten.dlcomgcorvsb).

## Compartimentsrecht (zie hieronder bij triggers)

Het compartimentsrecht is OK indien:

- de inlogger lid is van een compartiment dan moet het betreffende compartiment het zaaktype van de bovenliggende zaak bevatten en de gemeente waar die zaak speelt. Indien de documenten aan een inspectietraject of een bezwaar/beroep deelzaak zijn gekoppeld, dan geldt ook nog dat de compartiments-eigenschap _inclusief inspecties c.q. bezwaar/beroep_ aangevinkt moet staan
- de inlogger GEEN lid is van een compartiment en de documenten die getoond worden horen bij een adviesdeelzaak of bij een hoofdzaak, dan mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt in geen enkel compartiment voor komen
- de inlogger GEEN lid is van een compartiment en de documenten die getoond worden horen bij een inspectietraject c.q. bezwaar/beroepzaak dan mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt ook in geen enkel compartiment voorkomen, tenzij de compartiments-eigenschap _inclusief inspecties c.q. bezwaar/beroep_ NIET aangevinkt staat.

## OLO-bijlagen verplaatsen van fileshare

Het kan zijn dat OpenWave eerst moet zorgen dat - indien de documenten worden opgevraagd bij een omgevingszaak- OLO-bijlagen eerst op de juiste plek moeten worden gestald. Dit geldt alleen voor de situatie dat OpenWave via een digi-koppelaar rechtstreeks berichten ontvangt van het OLO waarbij de OLO-bijlagen door die digi-koppelaar op een vooraf afgesproken verplaatsmap op een fileshare worden geplaatst (de andere mogelijkheid is namelijk dat de digi-koppelaar de bijlagen aan de OpenWave uploadservice aanbiedt: zie [Upload document vanuit automatisch proces](upload_vanuit_automatisch_proces).md).

OpenWave gaat onderzoeken of er OLO-bijlagen zijn indien de kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS en Item: InboxmapOLO_ een gevuld waarde heeft en aangevinkt is.

De waarde van _Item: InboxmapOLO_ is bijvoorbeeld '/mnt/openwave'. Op serverniveau wordt deze map gereroot naar de bedoelde fileshare map bijvoorbeeld //server/open/wave/olo/. Op serverniveau worden hiertoe credentials ingesteld: dus niet in OpenWave.

Bij afspraak worden door de DIGI-koppelaar achter deze map submappen gemaakt op OLO-nummer. Op die mappen en op submappen achter die OLO-nummermappen worden vervolgens door de DIGI-koppelaar de bijlagen geplaatst bijv.:

```
//server/open/wave/olo/1234
//server/open/wave/olo/1234/submap_A
//server/open/wave/olo/1234/submap_B
```

Zowel op de map 1234 als op de submappen submap_A en Submap_B kunnen één of meer bijlagen staan.

Bij het opvragen van de documentenlijst bij een OpenWave zaak (omgeving) waarbij het OLO-nummer is gevuld (EN - indien het DMS met StUF/Zaak wordt benaderd - de DMS-zaakcode (dvintzaakcode) gevuld is), zal het programma de OLO-bijlagen die aangetroffen worden op en achter de bijbehorende verplaatsmap verplaatsen naar het DMS of naar een andere map op de fileshare. Dit gebeurt doordat het programma intern haar eigen uploadfile-API aanroept.
Bij plaatsing van de OLO-bijlage via STUF Zaken kijkt het programma:

- wat betreft het documenttype naar kolom _Tekst_ van instelling _Sectie: KoppelingDOCNAARDMS en Item: OloDocType_ (defaultwaarde 'OLO')
- wat betreft metadata vertrouwelijkheid naar kolom _Tekst_ van instelling _Sectie: KoppelingDOCNAARDMS en Item: OloVertrouwelijkheid_ (defaultwaarde 'OPENBAAR')
- wat betreft auteur: deze krijgt de waarde onbekend.

Het programma maakt daarna de verplaatsmap (inbox + OLO-nummer) leeg.

Daarna pas wordt de reguliere Toon-Documentenlijst getoond waarin dan ook de OLO-bijlagen zichtbaar zouden moeten zijn. Op het moment dat deze lijst wordt getoond kan het echter zo zijn dat nog niet alle bijlagen reeds zijn aangekomen op plaats van bestemming (bijv. bij stuf zaak/DMS gaat het om asynchrone verwerking). De gebruiker zou dan een tweede keer om de lijst moeten vragen.
Wanneer het verplaatsen is mislukt dan zijn de niet verplaatste bijlages zichtbaar via de beheertegel _Mislukte OLO-bijlages_.

Het verplaatsen van de documenten op de fileshare naar de machine waar de WSAS op draait (al vanwaar de documenten naar de plaats van bestemming worden geredigeerd) kan nog eens extra gemonitord worden via de messagelog door de instelling _Sectie: InboxmapOLO en Item: Messagelog_ aan te vinken.

### Waarvandaan

Zie ook: [Schema welke documenten worden opgehaald?](toon_documenten_en_download/schema_welke_documenten.md).

De documenten bij een zaak worden gehaald uit het DMS en/of de fileshare.

- Indien de zaak valt onder een compartiment dan kijkt OpenWave naar de betrokken compartimentskaart (beheertegel _Compartimentsrechten_) om te achterhalen DMS/fileserver en met welke DMS methode. Indien hier is ingesteld dat het compartiment een stuf zaak/DMS koppeling heeft dan staan credentials en stuurgegevens en endpoint in de beheertabel tb33gemeente bij de betreffende gemeentes van dat compartiment.
- Indien geen compartiment dan:
  - uit het DMS indien de instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_ aangevinkt staat
  - vanaf de fileshare indien de instelling _Sectie: Documenten_ en _Item: OphalenViaFileserver_ aangevinkt staat. Deze instellingen kunnen beiden aan staan.
- Indien het gaat om het DMS dan moet de instelling met _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ aangevinkt staan. De waarde van kolom _Tekst_ moet zijn:
  - 'StUF-ZAKEN 310'
  - OF 'CMIS 1.0'

De instelling StUF-ZAKEN 310 kan door het programma worden overruled naar CMIS 1.0 (in de hybride situatie dat er zowel documenten via CMIS als stuf zaak/DMS zijn op te halen) mits:
*de kolom *Tekst* van de instelling *Sectie: koppelingDOCNAARDMS en Item: Ontvangstadres_cmis* is gevuld met een CMIS-endpoint
- EN de kolom dvintzaakcode (externe zaakcode) van de zaak leeg is.

Indien fileshare dan kan het zijn dat de gebruiker eerst een **keuze moet maken uit één of meer mappen**. De documenten die getoond worden in de lijst zijn die van de aangevinkte mappen + alle documenten van eventuele submappen. Bepaalde submappen kunnen echter worden uitgesloten met de instelling _Sectie: Documenten Item: geensubmapmetsubstring1_ (en ook _geensubmapmetsubstring2_ en _geensubmapmetsubstring3_). Met de waarde in kolom _Tekst_ van deze instellingen worden submappen waarin deze waarde voorkomt, overgeslagen.

Het scherm met aan te vinken mappen wordt getoond indien:

- de instelling _Sectie: Documenten, Item: OphalenNaMapkeuze_ is aangevinkt
- EN - indien geen compartiment - dan moet _Sectie: Documenten Item: OphalenViaFileserver_ aangevinkt zijn
- EN - indien geen compartiment - dan moet _Sectie: Documenten Item: OphalenViaDms_ NIET aangevinkt zijn
- EN - indien WEL compartiment - dan moet de kolom _ophalen fileserver_ van het betreffende compartiment aangevinkt zijn
- EN - indien WEL compartiment - dan moet de kolom _ophalen dms_ van het betreffende compartiment NIET aangevinkt zijn
- EN _Sectie: Documenten Item: MultipleDownload_ is aangevinkt.
- Indien _Getal1_ van _Sectie: Documenten, Item: OphalenNaMapkeuze_ de waarde 1 heeft, dan blijft het wizardscherm mapkeuze openstaan (dus bij het verlaten van de documentlijst krijgt dit scherm weer de focus).
- Indien er geen of maar één map is met documenten, dan wordt het mapkeuzescherm niet getoond.
- Indien er geen mapkeuze wordt gemaakt, dan worden alle documenten van alle mappen opgehaald.

Met _Getal2_ van _Sectie: Documenten, Item: OphalenNaMapkeuze_ kan aangegeven worden welk gedeelte van de mapnaam (die nogal lang kunnen zijn) getoond moet worden in het mapkeuzeschermpje. Met _Getal2_ wordt aangegeven hoeveel onderdelen van die mapnaam gerekend van achter naar voor getoond moet worden (een onderdeel is een submap ingesloten door backslashes).

Voorbeeld:

- _Getal2_ = 2 en de mapnaam = 'bijlage/omgeving/2017W993/' dan wordt die naam verkort tot '/omgeving/2017W993/'
  - _Getal2_ = 1 en de mapnaam = 'bijlage/omgeving/2017W993/' dan wordt die naam verkort tot '/2017W993/'.

Heeft _Getal2_ geen waarde of 0 of het aantal is groter dan het aantal onderdelen in de mapnaam dan geldt dat de mapnaam ongewijzigd blijft.

Indien fileshare zie verder bij [Ophalen van fileshare](toon_documenten_en_download/ophalen_van_fileshare.md).
Indien StUF-ZAKEN 310 zie verder bij [Ophalen met stuf zaak dms](toon_documenten_en_download/ophalen_met_stuf_zaak_dms.md).

Indien CMIS 1.0 zie verder bij [Ophalen met CMIS](toon_documenten_en_download/ophalen_met_cmis.md).

## Openen van document

Door te klikken op een actieve regel zal OpenWave volgens onderstaand schema te werk gaan:

[<img src="/_media../../img/applicatiebeheer/probleemoplossing/programmablokken/openenopgeslagendocument.png?w=600&amp;tok=9523b3" class="media" loading="lazy" alt="" width="600" />](/_detail../../img/applicatiebeheer/probleemoplossing/programmablokken/openenopgeslagendocument.png?id=docs%3Aapplicatiebeheer%3Aprobleemoplossing%3Aprogrammablokken%3Atoon_documenten_en_download.md)

**Ad 1. Check op registratie en vertrouwelijkheid**

Indien de kolom van het registratievakje van het document is gevuld met een potloodicoontje (dat wil zeggen dat het document is geregistreerd) EN
de instelling _Getal2_ van _Sectie: Documenten en Item: Documentregistratie_ heeft de waarde 1, dan volgt een mededeling dat het document onder mutatievoorwaarden is geregistreerd en alleen via de lijst geregistreerde documenten kan worden benaderd.

Indien het document in OpenWave is geregistreerd (tbcorrespondentie), dan zal het programma eerst een check doen op **vertrouwelijkheidsrechten**. Voor een inlogger om een document te kunnen openen dient het vertrouwlijkheidsniveau van het geregistreerde document hoger dan of gelijk te zijn aan het opgegeven vertrouwelijkheidsniveau op de medewerkerskaart van de inlogger. Is dat niet het geval dan komt de mededeling onder in scherm: geen rechten.

**Ad 2. Kan document geopend worden via aanroep explorer (alleen indien browser = Firefox)**

Indien vertrouwelijkheid OK dan:

- indien het aangewezen document van de filserver komt
- EN het IP-adres van de huidige sessie (tbsessions) van de gebruiker voldoet aan het masker gedefinieerd in de kolom IpRange van een van de regels van de tabel tbipranges, waarbij de kolom dlhyperlink aangevinkt is
- EN kolom _Getal2_ van _Sectie: Documenten Item: OphalenViaFileserver_ heeft de waarde 1 (waarmee wordt aangegeven dat de mensen die binnen de genoemde IP-range vallen ook Firefox als standaardbrowser hebben waarin OpenWave als trusted (firefox-policy) is gedefinieerd)

DAN wordt het document via een hyperlink geopend: dat wil zeggen via openTabPage(file:///' + map + documentnaam + extensie + ')' waarbij alle backslashes omgezet zijn in forwardslashes. Indien echter bovenstaande het geval is, maar de [satellite](../../../../instellen_inrichten/satellite_filesysteem.md) staat aan, dan werkt dit alleen indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Documentroot_ gelijk is aan dezelfde instelling van de configuratiefile van de geïnstalleerde satellite.

**Ad 3. Kan document geopend worden met lokale MS Word of MS-Excel via Office URI-scheme**

Indien vertrouwelijkheid OK dan:

- indien het aangewezen document van de fileserver komt
- EN het IP-adres van de huidige sessie (tbsessions) van de gebruiker voldoet aan het masker gedefinieerd in de kolom IpRange van een van de regels van de tabel tbipranges, waarbij de kolom dlhyperlink aangevinkt is
- EN kolom _Getal2_ van _Sectie: Documenten Item: OphalenViaFileserver_ heeft de waarde 2 (bij een compartiment dat gebruikt van een satellite op de lokale fileserver kijkt OpenWave naar de kolom tbcompartiment.dldocsfileshareofficeuri, die moet aangevinkt zijn)
- EN de bovenliggende zaak is niet geblokkeerd

DAN wordt het document via Office URI-scheme geopend: bijvoorbeeld `ms-word:ofe| u |file:/zuurstof/user/pdeboer/Paultest.docx`. Indien echter bovenstaande het geval is, maar de [satellite](../../../../instellen_inrichten/satellite_filesysteem.md) staat aan, dan werkt dit alleen indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Documentroot_ gelijk is aan dezelfde instelling van de configuratiefile van de geïnstalleerde satellite.

In dit verband geldt nog wel het volgende:

- indien de inlogger een medewerker is van de host organisatie dan moet het document zich bevinden op de fileserver va de host
- indien de inlogger een medewerker is van het compartiment dan moet het document zich bevinden op de fileserver van het compartiment (te benaderen met satellite).

Zo niet, - dus een medewerker van de host vraagt een document van een compartiment, of omgekeerd - dan zal het document of via OnlyOffice benaderd worden, of worden gedownload naar het device van de inlogger.

In dit verband geldt nog wel het volgende:

- indien de inlogger een medewerker is van de host organisatie dan moet het document zich bevinden op de fileserver va de host
- indien de inlogger een medewerker is van het compartiment dan moet het document zich bevinden op de fileserver van het compartiment (te benaderen met satellite).

Zo niet, - dus een medewerker van de host vraagt een document van een compartiment, of omgekeerd - dan zal het document of via OnlyOffice benaderd worden, of worden gedownload naar het device van de inlogger.

**Ad 4. Kan document geopend worden met OnlyOffice**

Indien vertrouwelijkheid OK en de instellingen zijn dusdanig dat het programma geen poging doet het bestand via een hyperlink met firefox of Office URI-scheme te openen dan:

- indien de instelling _Sectie: Documenten Item: OnlyOffice_ aangevinkt is
- EN de extensie van dat document komt voor in de kolom _Tekst_ van deze instelling (extensies gescheiden door puntkomma, dus bijv. docx;xslsx;pdf)
- EN de instelling _Sectie: OWB Item: TussenMapOnlyOfficeDownloadFiles_ bestaat en de kolom _Tekst_ eindigt op _onlyoffice/download_/
- EN de instelling _Sectie: OWB Item: TussenMapOnlyOfficeUploadFiles_ bestaat en de kolom _Tekst_ eindigt op _onlyoffice/upload_/

dan zal het document als serverdocument worden geopend met OnlyOffice (mits geïnstalleerd).

Indien de bovenliggende zaak is geblokkeerd, dan wordt OnlyOffice in readonly modus geopend.

**Ad 5 Het aangewezen document wordt gedownload maar direct geopend met browser**

Indien vertrouwelijkheid OK en de instellingen zijn dusdanig dat het programma geen poging doet het bestand via een hyperlink met IE of Office URI-scheme of via OnlyOffice te openen dan - mits de extensie van het document voorkomt in de kolom _Tekst_ van de instelling _Sectie: OWB en Item: DocumentBrowser_ zal de default browser het document trachten te openen.
De opgesomde extensies van de instelling moeten gescheiden zijn door een puntkomma dus bijv. _'pdf;png;jpg'_

**Ad 6. Het document wordt gedownload naar device van gebruiker**

Indien vertrouwelijkheid OK, dan zal in alle andere gevallen (geen OnlyOffice, geen IE, Office URI-scheme) het programma reageren op het dubbelklikken op een regel alsof er één document is aangevinkt en de downloadknop wordt gebruikt.

Dat wil zeggen dat het document wordt gedownload naar de device van de gebruiker. De instellingen van MS-Windows explorer op grond van de extensie van het document bepalen vervolgens of en met welk pakket het document automatisch geopend wordt.

## Hernoemen (wijzigen metadata) van document

Deze functie is toegankelijk via wizardknop linksonder. Hernoemen kan voor documenten die zich in een DMS (dat benaderd wordt via stuf zaak/DMS) bevinden of op een fileshare staan. Hernoemen of synchroniseren van een document dat geregistreerd is (dus in tbcorrespondentie opgenomen) kan alleen via de lijst _Geregistreerde documenten_.

Indien het document op een fileshare staat kan alleen de documentnaam worden gewijzigd. Indien het document in een DMS staat (dat benaderd wordt via stuf zaak/DMS) kunnen titel, vertrouwelijkheid, documenttype en creatiedatum worden aangepast. Indien de instelling _Sectie: koppelingDOCNAARDMS_ en _Item: RichtingalsExtraElement_ aan staat zal ook de richting van het document aangepast kunnen worden.

## Triggers

De wizardknop linksonder is zichtbaar en enabled indien:

- de zaak waar de geregistreerde documenten aan verbonden zijn NIET is geblokkeerd
- EN compartimentsrechten OK
- EN de gebruiker het recht _Wijzigen metadata (hernoemen) van ongeregistreerde documenten_ voor de betreffende hoofdzaak aangevinkt heeft staan (bijv. tbomgrechten.dlcomgcorwmo).

Voor het hernoemen van een document op de fileshare geldt:

- EN – indien de bovenliggende zaak NIET speelt in een compartiment - dan moet _Sectie: Documenten, Item: Ophalenviafileserver_ aangevinkt staan
- EN - indien de bovenliggende zaak WEL speelt in een compartiment - dan moet kolom _dlfileserver_ aangevinkt zijn bij het betreffende compartiment.

Voor het hernoemen van een document in het DMS geldt:

Indien:

- de bovenliggende zaak NIET speelt in een compartiment dan:
  - moet de instelling _Sectie: KoppelingDocnaarDMS, Item: MagDocMetadataUpdaten_ aangevinkt zijn
  - EN de instelling _Sectie: KoppelingDocNaarDms en Item: methode_ is aangevinkt en kolom _Tekst_ heeft waarde StUF-ZAKEN 310
- wanneer de bovenliggende zaak WEL speelt in een compartiment dan
  - moet de kolom _dldmsupdatemetazaakdoc_ van het betreffende tbcompartiment aangevinkt zijn
  - EN de kolom _dvdmsmethode_ van het betreffende tbcompartiment moet de waarde = 'STUF-ZAKEN 310' hebben
  - EN de kolom _dldms_ van het betreffende tbcompartiment moet aangevinkt zijn.

### Knoppen linksonder

**Downloadknop**

Indien de instelling _Sectie: Documenten_ en _Item: MultipleDownload_ aangevinkt is zal de documentenlijst voorzien worden van multiselect vakjes aan de voorkant van de rijen en een **knop download_de_geselecteerde_items** linksonder. Indien geen multiple download dan wordt een document geselecteerd t.b.v. downloaden door er dubbel op te klikken.

Indien er meer dan één document is aangevinkt dan worden deze met het indrukken van de download-knop gezipt in DownloadOpenWave' + Timestamp + '.zip'. De (zip)file mag niet groter zijn dan (in Megabyte) de waarde van kolom _Getal1_ van instelling bij _Sectie: OWB en Item: MaxUploadMbGrootte_ van tbinitialisatie (defaultwaarde = 50Mb). Maximaal 10 files met dezelfde naam kunnen worden opgenomen in de zipfile. Het programma voorziet deze zelf van een nummer (test1.txt en test2.txt).

Indien er maar één document gedownload wordt dan gebeurt dit onder zijn eigen documentfilenaam. Wel dezelfde restrictie op MaxUploadMbGrootte. Het lijkt er op dat met Internet Explorer er een maximum bestaat van 19 files in de zipfile.

Er kan een afwijkende zipfilenaam worden geconstrueerd indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Downloadzipfilenaam_ gevuld is met een tekststring langer dan 5 tekens en eindigend op .zip

In dat geval is de naam van de zipfile de waarde van deze kolom Tekst waarbij de variabelen (let op case sensitive):

- %date% vervangen wordt door TimeStamp
- %login% wordt vervangen door de medewerkerscode van de inlogger
- %hoofdzaaknr% wordt vervangen door de wavezaakcode
- %hoofddmsnr% wordt vervangen door de externe zaak/DMS code
- %adres% wordt vervangen door het adres + de woonplaats

Verder moet de downloadmap op de webserver bekend zijn: het tussenstation tussen DMS/fileshare en het device van de gebruiker.
Kolom _Tekst_ van de _Sectie: OWB en Item: TussenMapDownloadFiles_.
Deze downloadMapnaam moet eindigen op '/openwave/download/' en ook beginnen met een '/'.

Tenslotte zal de programmatuur zelf deze downloadmap op de webserver regelmatig opschonen. Files ouder dan het aantal uur dat is ingesteld in kolom _Getal1_ van de instelling _Sectie: OWB Item: MaxUurDownload_ worden automatisch verwijderd. Defaultwaarde = 24 uur.

**Refreshknop**

Indien:

- De documenten worden opgevraagd vanuit een omgevingszaak
- EN instelling _Sectie: KoppelingDOCNAARDMS Item: InboxmapOLO_ is aangevinkt (het programma verplaatst bij het opvragen OLO-bijlagen naar de plek waar zij horen: zie hierboven)

OF

- de instelling _Sectie: Documenten Item: StartAutomUploadSchermNaUpload_ bestaat niet of is UITgevinkt

dan is een refreshknop zichtbaar en enabled, waarmee nogmaals de documentenlijst kan worden opgehaald. De tijdspanne die nodig is om de OLO-bijlagen bijvoorbeeld in het DMS te stallen OF uploads op hun juiste plek te brengen heeft OpenWave namelijk niet altijd in de hand.

**Registreerknop**

Zichtbaar en enabled indien:

- de gebruiker het _'Wijzigen metadata van geregistreerde documenten'_- recht heeft bij de betreffende module
- EN het compartimentsrecht is OK.
- EN de bovenliggende zaak NIET is geblokkeerd

Met deze knop worden de geselecteerde documenten geregistreerd, nadat zij voorzien zijn in een wizardscherm van de nodige metadata met betrekking tot vertrouwelijkheid, documenttype en richting. Welke metadata in de wizard van een waarde kunnen worden voorzien is afhankelijk van de van het aangevinkt zijn van instellingen bij [Sectie: DocumentRegistreren](../../../../instellen_inrichten/configuratie/sectie_documentregistreren.md). Het gaat hier om de Items: ddontvangsdatum, dvdocrichting , dvdoctype, dvomschrijving, dvstatus en dvvertrouwelijkheid, dlnaarregdoc en dlnaarbevoegdgezag. De laatste twee hebben sinds versie 1.21 geen betekenis meer in de programmatuur. dlnaarbevoegdgezag zou nog gebruikt kunnen worden in de deprecated functie: _Email secretariaat bevoegd gezag/DIV vanuit geregistreerde documenten_ indien het detailscherm geregistreerde documenten wordt aangepast.
Bij het registreren (= een kaart aanmaken in tbcorrespondentie) wordt de inlogger als registreerder geboekt. Zie verder [Lijst geregistreerde documenten bij een zaak](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/lijst_geregistreerde_documenten_bij_zaak.md).

De gebruiker dient ook nog correspondentie wijzigrechten te hebben (bijv. tbomgrechten.dlcomgcoredt). LET OP: indien een lijst wordt getoond vanuit een inspectietraject kijkt het programma naar de correspondentie-wijzigrechten van de module. Het kan echter zijn dan een inspectietraject zowel gekoppeld is aan bijvoorbeeld een inrichting als aan een handhavingszaak (als vanuit het traject een handhaving is gemaakt met de daartoe bestemde functie). In dat laatste geval prevaleert het correspondentie-wijzigrecht van de handhavingszaak (tbhhrechten.dlchahcoredt), dus ook wanneer de documentlijst van het traject wordt bekeken vanuit een inrichting. Indien de rechten niet kloppen is de knop wel enabled, maar gebruik zal leiden tot een foutmelding.

**Uploadknop**
Zichtbaar indien:

- bovenliggende zaak niet is geblokkeerd
- de instelling _Sectie: Documenten, Item: OphalenViaDms_ EN/OF de instelling _Sectie: Documenten, Item: OphalenViaFileserver_ is aangevinkt (of in geval van compartiment de kolommen _ophalen fileserver/DMS_)
  - indien OphalenViaDms aangevinkt dan moet de kolom _Tekst_ bij instelling _Sectie: KoppelingDocnaardms Item: Methode_ de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben en aangevinkt staan (of in geval van compartiment dan met de kolom _dmsmethode_ deze waarde hebben)
  - EN - alleen in geval van StUF-ZAKEN 310 – dan moet de externe zaak/DMS code (dvintzaakcode) in de bovenliggende zaak gevuld zijn.
- Compartimentsrechten OK

Enabled indien de inlogger het _uploadrecht van documenten_ heeft.

**VerplaatsNaarDMS-knop**

Zichtbaar en enabled indien:

- compartimentsrecht OK
- EN in de hybride situatie dat zowel van de fileserver gebruikt wordt gemaakt als van een DMS onder StUF zaak/DMS.

Dat betekent dat zowel de instelling _Sectie: Documenten Item: OphalenViaFileserver_ aangevinkt moet zijn als de instelling _Sectie: Documenten Item: OphalenViaDMS_ waarbij de instelling _Sectie: Koppeling ZAAK_ en _Item: Methode_ en _Tekst = StUF-ZAKEN 310_ (en ook is ook aangevinkt).

De inlogger kan het actieve document (die met de gele balk) met deze knop - na invulling van verplichte metadata - in het DMS plaatsen (uploaden). Het programma controleert daarbij of het document wel op de fileserver staat en of de bovenliggende zaak een zaakidentificatienummer heeft).

Het betrokken fileserver-document daarbij wordt ook verplaatst naar een kopiemap: zie instelling kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS en Item: MapKopieVerplaatsteFiles_.

Wat betreft de verplichte metadata: indien in de documentnaam de substring '\_DCT=' voorkomt, dan zal het programma de tekst vanaf deze substring tot aan de punt van de extensie beschouwen als het documenttype. Voorbeeld: het documenttype bij de filenaam: 20181013_OW1298_Brandweer_DCT=Advies.docx zal zijn _Advies_. Indien de substring '\_DCT=' niet wordt aangetroffen en documenttype is wel verplicht bij DMS. dan zal de gebruiker deze moeten aanwijzen.

Indien de documentnaam inderdaad de substring '\_DCT=…..' bevat dan zal deze substring er weer vanaf worden gehaald wanneer het document wordt verzonden naar het DMS. Dat geldt ook voor de naam van het document dat op de _MapKopieVerplaatsteFiles_ wordt geplaatst. Dus in bovengenoemd voorbeeld zou dan 20181013_OW1298_Brandweer.docx in het DMS en op de kopiemap worde geplaatst.

**Wizardknop Hernoemen van document**

Zie hierboven onder kopje _Hernoemen van Document_.
