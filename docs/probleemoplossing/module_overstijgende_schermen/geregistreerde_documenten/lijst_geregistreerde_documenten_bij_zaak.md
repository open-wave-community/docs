# Lijst Geregistreerde Documenten bij een zaak

De schermidentifier is: MDLC_getGeregistreerdeDocumentenList.xml.
Zie voor verzendstroom, collegiale toetsing, bijlages, ondertekening: [Documenten/Verzendstroom](../programmablokken/documenten_verzendstroom.md).

## Hoe zichtbaar te maken

Dit scherm kan worden aangeroepen:

- vanuit de tegel **Geregistreerde documenten** op het zaakportaal van Omgeving, Handhavingen, Bouw/sloop, Milieu/gebruik, APV/Overig, Horeca, Inrichting of Info-aanvragen. Deze tegel is standaard zichtbaar indien de instelling _Sectie: Documenten en Item: Documentregistratie_ NIET is aangevinkt
- vanuit de knop _Docs_ boven aan de zaakportalen indien de instelling _Sectie: Documenten en Item: Documentregistratie_ WEL is aangevinkt. Indien niet aangevinkt toont de knop _Docs_ de documentlijst van alle aanwezige documenten bij een zaak in het DMS of fileserver
- vanuit de knop _Docs_ linksonder op de detailpagina's van een zaak of deelzaak indien de instelling _Sectie: Documenten en Item: Documentregistratie_ WEL is aangevinkt. Indien niet aangevinkt toont de knop _Docs_ de documentlijst van alle aanwezige documenten bij een zaak/deelzaak in het DMS of fileserver
- vanuit het item _Toon geregistreerde documenten_ uit het menu _Opties_ op de detailpagina's van een advies, een inspectietraject of een bezwaar/beroep.

De gebruiker dient wel het recht _Inzien geregistreerde documenten_ voor de betreffende module te hebben (bijv. tbomgrechten.dlcomgcorregvsb).

De lijst toont in de eerste twee gevallen de gegevens uit vwfrmcorrespondentie behorend bij de actieve hoofdzaak of inrichting (inclusief de geregistreerde documenten die geregistreerd zijn vanuit een deelzaak: advies, bezwaarberoep of inspectie). Dit is ook het geval wanneer de lijst wordt aangeroepen vanuit de knop _Docs_ op de detailpagina van een hoofdzaak/inrichting.

Wanneer de lijst wordt aangeroepen vanuit het menu item _Toon geregistreerde documenten_ of vanuit de knop _Docs_ op detailpagina van een deelzaak worden alleen de geregistreerde documenten getoond die vanuit dat specifieke advies, inspectie of bezwaarberoep zijn geregistreerd.

De view is gebaseerd op de tabel tbcorrespondentie.

## Hoe te registreren

De gebruiker (of OpenWave zelf) kan op de volgende manieren een bestaand document registreren: dat wil zeggen toevoegen aan de tabel tbcorrespondentie

- Vanuit de bestaande documentenlijst die kijkt naar alle documenten op fileserver c.q. DMS (zie: [Toon documenten en download](../programmablokken/toon_documenten_en_download).md) met de knop _Registreer aangevinkte documenten_. Zichtbaar en enabled indien de gebruiker het _Wijzigen metadata van geregistreerde documenten_- recht heeft bij de betreffende module.
- Vanzelf vanuit het creëren van een document dat automatisch wordt opgeslagen op basis van een sjabloon mits _Getal1_ van _Sectie: Documenten en Item: Documentregistratie_ de waarde 1 heeft.
- Vanzelf bij het uploaden van een document mits de instelling _Sectie: DocumentRegistreren en Item: AlleHandmatigeUploads_ is aangevinkt.
- Vanzelf bij het automatisch plaatsen van een OLO/DSO document mits de instelling _Sectie: DocumentRegistreren en Item: AlleOLODSOUploads_ aangevinkt is.

Het programma zal bij het registreren het document altijd koppelen aan de hoofdzaak/inrichting. Daarnaast wordt de registratie ook gekoppeld aan een deelzaak (een advies, inspectie of bezwaar/beroep) indien:

- het document werd aangemaakt met een sjabloon vanuit een advies of een inspectie of een bezwaar/beroep (bij document vanuit inspectiebezoek wordt ook dnkeyinspectiebezoek opgeslagen). Bij inspectie geldt nog het volgende:
  - Indien het inspectietraject zowel gekoppeld is aan een omgevingzaak als aan een handhavingzaak dan kijkt OpenWave naar de kolom _Tekst_ van instelling _Sectie: DocumentRegistreren en Item: InspectiebijZowelOmgEnHandh_. Indien hier de waarde _H_ zal bij het (automatisch) registreren van een document bij dat inspectietraject in de registratie (tbcorrespondentie) de dnkey van de handhavingzaak worden gevuld en anders die van de omgevingzaak.
- het document wordt geregistreerd vanuit de algemene documentenlijst opgeroepen vanuit een advies, inspectie of bezwaar/beroep.

Indien het te registreren document een **email is (.eml bestand)** dan worden onderstaande velden als volgt gevuld bij registratie:

- **Definitief** is JA
- **Datum verstuurd** wordt gevuld met datum van vandaag
- **Verzendwijze** is Per email
- **Digitaal ondertekend** is false
- Het blok **Adressering** wordt gevuld met gegevens van de gekozen ontvanger
- **Richting** is Uitgaand.

Voor de kolommen **eerste registratie en laatste registratie** geldt het volgende:
Deze velden worden automatisch gevuld door de programmatuur bij aanmaken/wijzigen van het document.

## Muteer- en compartimentsrechten

Een kolom in de geregistreerde documenten lijst (of detail) kan worden gemuteerd indien:

- de inlogger lid is van een rechtengroep die _Wijzigen metadata van geregistreerde documenten_ heeft bij van de betrokken module
- EN de bovenliggende zaak niet is geblokkeerd
- EN - indien het gaat om de lijst - in de schermkolomdefinitie (beheer) is de eigenschap _lijst automatisch in editmode_ aangevinkt
- EN de kolom heeft de tag`<edit>`op true staan in de schermkolomdefinitie
- EN - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de bovenliggende zaak bevatten en de gemeente waar die zaak speelt. Indien de documenten aan een inspectietraject of een bezwaar/beroep deelzaak zijn gekoppeld, dan geldt ook nog dat de compartiments-eigenschap inclusief inspecties c.q. bezwaar/beroep aangevinkt moet staan
- EN - indien de inlogger GEEN lid is van een compartimenten de documenten die getoond worden horen bij een adviesdeelzaak of bij een hoofdzaak - dan mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt in geen enkel compartiment voorkomen
- EN - de inlogger GEEN lid is van een compartiment en de documenten die getoond worden horen bij een inspectietraject c.q. bezwaar/beroepzaak - dan mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt ook in geen enkel compartiment voorkomen, tenzij de compartiments-eigenschap inclusief inspecties c.q. bezwaar/beroep NIET aangevinkt staat
- EN de editschuif aan staat.

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie [Scherm(kolom)definitie](../../../instellen_inrichten/schermdefinitie).md) die niet valide is
- de inlogger geen kijkrechten heeft op de documenten bij betreffende hoofdzaak.

### Betekenis kolom rood/groen balletje (kolom dvanbewerken)

Indien de bovenliggende zaak is geblokkeerd dan rood. Anders, Indien de kolom _Getal2_ van de instelling _Sectie: Documenten en Item: Documentregistratie_ ongelijk 1 is, dan is de kleurbol wit en heeft de kolom geen betekenis. Indien de waarde 1 is, dan wordt het kleurenballetje rood of groen. Groen geeft aan dat het document nog bewerkt kan worden Een document kan nog bewerkt worden indien:

- Locatie is (file)server (dvdocplaats = 'S'). Hiermee wordt aangegeven dat het document niet ter bewerking is gekopieerd naar een lokale device
- EN datum verstuurd (ddbriefdatum) is leeg. Hiermee wordt bedoeld datum verstuurd naar aanvrager
- EN het gaat om een uitgaand of intern document (dvdocrichting = 'U' of 'I') in tegenstelling tot Binnenkomend document
- EN het gaat om een NIET definitief document (dvdefinitief = 'N')

Als de kleurenbol aangeeft dat het document NIET bewerkt kan worden (rood), dan zal het document bij het openen in OnlyOffice in read-only modus staan en bij het downloaden naar de device van de gebruiker gerendered worden naar pdf-formaat in zoverre het gaat om de extensies: ods, odt, doc, docx, xls, xlsx,txt en xml. Indien de kleurenbol aangeeft dat het document WEL bewerkt kan worden (groen\_, dan zal het document bij het downloaden niet gerendered worden, maar krijgen de kolommen dvdocplaats, dvcoderegistreerder en ddgewijzigd wel automatisch een nieuwe waarde.

### Documentfase

Heeft twee componenten in het lijstscherm geregistreerde documenten: de kolom Fase en de regel Documentfase in de filter Typering. Deze componenten zijn zichtbaar indien instelling _Sectie: DocumentRegistreren en Item: Documentfase_ is aangevinkt. Documentfasen kunnen worden ingesteld in het beheer onder de tegel: _Documentfasen_ in het zaakbeheerportaal onder kolom: Afhandeling.

### Roepnaam / filenaam

Er kan voor gekozen worden om in plaats van de documenttitel (vwfrmcorrespondentie.dvfilenaam) het veld tbcorrespondentie.dvroepnaam te tonen. Dit veld wordt gevuld met de dvfilenaam, minus de voorloop getallen van OLO of DSO documenten en is alleen zichtbaar indien de instelling _Sectie: Documenten, Item: RoepnaamIpvTitelInDoclijst_ is aangevinkt.

Het volgnummer van DSO documenten wordt hierbij wel overgenomen, aangezien dit van belang is om te weten of het document een aanvulling is. Als bijvoorbeeld bij een zaak een DSO-bijlage bestaat die de titel 123036-1643797388113-000-BijlageDSO.docx heeft, dan zal met deze instelling het veld dvroepnaam gevuld worden met 000-BijlageDSO.docx.

Let op: Het betreft een nieuw veld, wat inhoudt dat dvroepnaam niet met terugwerkende kracht gevuld wordt. Dit betekent dat de voorloop-getallen weg zijn vanaf het moment dat de instelling aan staat, maar de documenten die voor die tijd al bestonden zullen wel voorloop-getallen hebben.

De vwfrmcorrespondentie.dvfilenaam wordt bij OLO-documenten berekend op grond van de tbcorrespondentie.dvdocfilenaam (de echte documentnaam en bij opslag op fileserver voorafgegaan door het volledige pad), door slechts het gedeelte vanaf de laatste slash c.q. backslash te laten zien. Dus de echte documentnaam is bijvoorbeeld _mijnservernaam/2023/2023W0034/OLO/8103577/basisset_aanvraag/8103577_1696421488416_publiceerbareaanvraag.pdf_, maar de gebruiker ziet: _8103577_1696421488416_publiceerbareaanvraag.pdf_

### Openen opgeslagen document

Zie hieronder _triggers in lijstscherm_ voor het starten van de hyperlink vanuit de kolom dvurl.

In alle andere gevallen zal OpenWave door te klikken op een actieve regel volgens onderstaand schema te werk gaan:

![Openen opgeslagen document](/img/applicatiebeheer/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/openenopgeslagendocument.png){ class="media" loading="lazy" alt="" width="600" }

**Ad 1. Check op bestaan en vertrouwelijkheid**

Met het klikken op de regel zal het programma het document openen c.q. downloaden. Indien het document niet bestaat wordt een 404 melding zichtbaar. Verder moet het vertrouwelijkheidsniveau van het geregistreerde document lager of gelijk zijn met hetgeen opgegeven is bij de rechtengroep van de inlogger (beheer). Is dat niet het geval dan komt de mededeling onder in scherm: geen rechten.

**Ad 2. Kan document op fileserver geopend worden als hyperlink naar explorer met Firefox**

Indien vertrouwelijkheid OK en het aangewezen document van de fileserver komt, dan:

- Indien de inlogger kijkrechten heeft op de map (anders komt melding _U heeft geen rechten op deze bewerking_)
- EN het IP-adres van de huidige sessie (tbsessions) van de gebruiker voldoet aan het masker gedefinieerd in de kolom _IpRange_ van een van de regels van de tabel tbipranges, waarbij de kolom dlhyperlink aangevinkt is
- EN kolom _Getal2_ van _Sectie: Documenten en Item: OphalenViaFileserver_ heeft de waarde 1 (waarmee wordt aangegeven dat de mensen die binnen de genoemde IP-range vallen ook Firefox als standaardbrowser hebben waarin OpenWave als trusted (firefox-policy) is gedefinieerd)
- EN
  - OF de kolom _Getal2_ van de instelling _Sectie: Documenten en Item: Documentregistratie_ heeft NIET de waarde 1
  - OF deze kolom heeft WEL waarde 1, maar het document kan WEL bewerkt worden (zie hierboven betekenis rood/groen bolletje)

DAN wordt het document - zonder rendering en zonder verandering van de kolommen _Status_ en _Bij wie_ en _Gewijzigd_ - via een hyperlink geopend: dat wil zeggen via openTabPage(file:///' + map + documentnaam + extensie + ')' waarbij alle backslashes omgezet zijn in forwardslashes. Indien echter bovenstaande het geval is, maar de [satellite](../../../instellen_inrichten/satellite_filesysteem.md) staat aan, dan werkt dit alleen indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Documentroot_ gelijk is aan dezelfde instelling van de configuratiefile van de geïnstalleerde satellite.

In dit verband geldt nog wel het volgende:

- indien de inlogger een medewerker is van de host organisatie dan moet het document zich bevinden op de fileserver va de host
- indien de inlogger een medewerker is van het compartiment dan moet het document zich bevinden op de fileserver van het compartiment (te benaderen met satellite).

Zo niet, - dus een medewerker van de host vraagt een document van een compartiment, of omgekeerd - dan zal het document of via OnlyOffice benaderd worden, of worden gedownload naar het device van de inlogger.

**Ad 3. Kan document op fileserver met lokale MS Word of MS-Excel via Office URI-scheme geopend worden**

Indien vertrouwelijkheid OK en het aangewezen document van de fileserver komt, dan:

- Indien de inlogger kijkrechten heeft op de map (anders komt melding _U heeft geen rechten op deze bewerking_)
- EN het IP-adres van de huidige sessie (tbsessions) van de gebruiker voldoet aan het masker gedefinieerd in de kolom _IpRange_ van een van de regels van de tabel tbipranges, waarbij de kolom dlhyperlink aangevinkt is
- EN kolom _Getal2_ van _Sectie: Documenten en Item: OphalenViaFileserver_ heeft de waarde 2 (bij een compartiment dat gebruik maakt van een satellite op de lokale fileserver kijkt OpernWave naar de kolom tbcompartiment.dldocsfileshareofficeuri, die moet aangevinkt zijn)
- EN
  - OF de kolom _Getal2_ van de instelling _Sectie: Documenten en Item: Documentregistratie_ heeft NIET de waarde 1
  - OF deze kolom heeft WEL waarde 1, maar het document kan WEL bewerkt worden (zie hierboven betekenis rood/groen bolletje)

DAN wordt het document - zonder rendering en zonder verandering van de kolommen _Status_ en _Bij wie_ en _Gewijzigd_ - via Office URI-scheme geopend: bijvoorbeeld `ms-word:ofe| u |file:/zuurstof/user/pdeboer/Paultest.docx`.

Indien echter bovenstaande het geval is, maar de [satellite](../../../instellen_inrichten/satellite_filesysteem.md) staat aan, dan werkt dit alleen indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Documentroot_ gelijk is aan dezelfde instelling van de configuratiefile van de geïnstalleerde satellite.

In dit verband geldt nog wel het volgende:

- indien de inlogger een medewerker is van de host organisatie dan moet het document zich bevinden op de fileserver va de host
- indien de inlogger een medewerker is van het compartiment dan moet het document zich bevinden op de fileserver van het compartiment (te benaderen met satellite).

Zo niet, - dus een medewerker van de host vraagt een document van een compartiment, of omgekeerd - dan zal het document of via OnlyOffice benaderd worden, of worden gedownload naar het device van de inlogger.

**Ad 4. Openen aangewezen document van fileserver OF DMS met OnlyOffice**

Indien:

- vertrouwelijkheid OK
- EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand via een hyperlink met IE/Edge te openen
- EN de instelling _Sectie: Documenten en Item: OnlyOffice_ aangevinkt is
- EN de extensie van dat document komt voor in de kolom _Tekst_ van deze instelling (extensies gescheiden door puntkomma, dus bijv. docx;xslsx;pdf)
- EN de instelling _Sectie: OWB en Item: TussenMapOnlyOfficeDownloadFiles_ bestaat en de kolom _Tekst_ eindigt op _onlyoffice/download_/
- EN de instelling _Sectie: OWB en Item: TussenMapOnlyOfficeUploadFiles_ bestaat en de kolom _Tekst_ eindigt op _onlyoffice/upload_/

dan zal het document als serverdocument worden geopend met OnlyOffice (mits geïnstalleerd).

Indien:

- de bovenliggende zaak is geblokkeerd
- EN/OF
  - de kolom _Getal2_ van de instelling _Sectie: Documenten en Item: Documentregistratie_ heeft de waarde 1
  - EN het geregistreerde document staat gemarkeerd als _Mag niet bewerkt worden_ (rood bolletje)

dan zal OnlyOffice in readonly modus worden geopend.

Indien het document wel bewerkt kan worden (groen balletje) maar de instelling _Sectie: OnlyOffice en Item: eenbewerkertegelijk_ is aangevinkt dan zal OpenWave:

- op de registratiekaart de dvdocplaats veranderen in L (lokaal), waarmee voor andere mensen het document alleen in readonly modus geopend kan worden
- het document in de wijzigmodus openen. Per definitie kan dit maar één persoon zijn
- na sluiting van het document de dvdocplaats veranderen in S (server) waarmee het document weer wordt vrijgegeven voor de eerstvolgende gebruiker.

**Ad 5. Download aangewezen document naar device van gebruiker, maar direct openen met browser**

Indien:

- vertrouwelijkheid OK
- EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand via een hyperlink met Firefox te openen
- EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand via een Office URI-scheme te openen
- EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand met OnlyOffice te openen

dan - mits de extensie van het document voorkomt in de kolom _Tekst_ van de instelling _Sectie: OWB en Item: DocumentBrowser_ zal de default browser het document trachten te openen. De opgesomde extensies van de instelling moeten gescheiden zijn door een puntkomma dus bijv. _pdf;png;jpg_.

**Ad 6. Download aangewezen document van fileserver OF DMS naar device gebruiker**

Indien:

- vertrouwelijkheid OK
- EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand via een hyperlink met IE te openen
- EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand via een Office URI-scheme te openen
- EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand met OnlyOffice te openen
- EN de instellingen zijn dusdanig dat het programma GEEN poging doet het net gedownloade bestand direct met de browser te openen

dan:

- Indien de kolom _Getal2_ van de instelling _Sectie: Documenten en Item: Documentregistratie_ heeft WEL de waarde 1, dan:
  - indien het document kan NIET bewerkt kan worden (zie hierboven betekenis rood bolletje) zal het downloaden van het geselecteerde document in alleen lezen modus gebeuren. Dat wil zeggen dat het document gerendered wordt als pdf indien het gaat om de extensies ods, odt, doc, docx, xls, xlsx,txt en xml
  - indien het document WEL bewerkt kan worden, dan wordt het document gedownload, waarbij de dvdocplaats in tbcorrespondentie verandert in LOKAAL en wordt de kolom dvcoderegistreerder gevuld met de code van de betrokken medewerker
  - anders (de kolom _Getal2_ van de instelling _Sectie: Documenten en Item: Documentregistratie_ heeft NIET de waarde 1 dan wordt het document gedownload zonder rendering en zonder aanpassing van de kolommen _Status_ en _Bij wie_ en _Gewijzigd_.

Het renderen van documenten met de extensies ods, odt, doc, docx, xls, xlsx,txt en xml kan alleen indien de kolom _Tekst_ van de instelling _Sectie: Koppeling Converter en Item: EndpointClassDocument_ gevuld is met een valide endpoint van de converter. bijv: _<http://localhost:9763/services/nl.rem.docconv.manager.published.Documents.nl.rem.docconv.manager.published.DocumentsHttpsSoap11Endpoint/>\*\*Cursieve> tekst_

### Hernoem (wijzig metadata) of verwijder document

Deze functies zijn toegankelijk via wizardknop linksonder. Verwijderen kan alleen voor documenten die zich op een fileshare bevinden. Hernoemen (wijzig metadata) kan voor documenten die zich in een DMS (dat benaderd wordt via stuf zaak/DMS) bevinden of op een fileshare staan.

Voor documenten die op de fileshare staan is het alleen mogelijk de documentnaam te wijzigen. Voor documenten die zich in een DMS (dat benaderd wordt via stuf zaak/DMS) staan zijn titel (dvomschrijving), documenttype, creatiedatum, ontvangstdatum, vertrouwelijkheid en verzenddatum aan te passen en - mits de instelling _Sectie: KoppelingDOCNaarDMS en Item: RichtingAlsExtraElement_ is aangevinkt - wordt via ExtraElementen ook de richting doorgegeven EN is deze zichtbaar/aanpasbaar in de wizard.

Indien DMS via StUF EN:

- er geen sprake is van een compartiment
- EN de instelling _Sectie: KoppelingDOCNAARDMS Item: SynchroniseerVanuitDMS_ is aangevinkt en _Getal1_ heeft de waarde 1

OF

- er wel sprake is van een compartiment
- EN de kolom tbcompartiment.dlsynchroniseervanuitdms is aangevinkt
- EN de kolom tbcompartiment.dlautosynchroniseervanuitdms is ook aangevinkt

dan zal het geregistreerde document eerst automatisch - onder water - worden gesynchroniseerd vanuit het DMS (DMS is de baas) alvorens er nieuwe waarden ingebracht kunnen worden. Dit gebeurt op basis van geefLijstZaakDocument.

De wizardknop is zichtbaar en enabled indien:

- de zaak waar de geregistreerde documenten aan verbonden zijn NIET is geblokkeerd
- EN compartimentsrechten OK
- EN de gebruiker het recht
  - _Verwijderen registratie inclusief fysiek document_ voor de betreffende hoofdzaak aangevinkt heeft staan (bijv. tbomgrechten.dlcomgcordocdel)
  - EN/OF _Hernoemen, wijzigen metadata document_ aangevinkt heeft staan (bijv. tbomgrechten.dlcomgcorreghnm).

Voor het hernoemen en verwijderen van een document op de fileshare geldt:

- EN – indien de bovenliggende zaak NIET speelt in een compartiment - dan moet _Sectie: Documenten en Item: Ophalenviafileserver_ aangevinkt staan
- EN - indien de bovenliggende zaak WEL speelt in een compartiment - dan moet kolom _dlfileserver_ aangevinkt zijn bij het betreffende compartiment.

Voor het hernoemen van een document in het DMS geldt extra dat het actieve geregistreerde document voorzien is een externe zaakidentifier en documentidentifier (blok _zaak/DMS_ van detailpagina) EN

Indien:

- de bovenliggende zaak NIET speelt in een compartiment dan:
  - moet de instelling _Sectie: KoppelingDocnaarDMS en Item: MagDocMetadataUpdaten_ aangevinkt zijn
  - EN de instelling _Sectie: KoppelingDocNaarDms en Item: Methode_ is aangevinkt en kolom _Tekst_ heeft waarde StUF-ZAKEN 310
- Wanneer de bovenliggende zaak WEL speelt in een compartiment dan:
  - moet de kolom _dldmsupdatemetazaakdoc_ van het betreffende tbcompartiment aangevinkt zijn
  - EN de kolom _dvdmsmethode_ van het betreffende tbcompartiment moet de waarde _STUF-ZAKEN 310_ hebben
  - EN de kolom _dldms_ van het betreffende tbcompartiment moet aangevinkt zijn.

### Triggers

#### triggers in lijstscherm

- schermknop **hyperlink op grond van gevulde dvurl** (achter de kolom roepnaam met leeg label)
  - zichtbaar en enabled indien:
    - de instelling _sectie: Documenten item:HyperlinkOpdvUrlZichtbaar_ aangevinkt is
    - EN indien de kolom dvurl is gevuld met een extene hyperlink zoals bijv. _<https://corsa-as1-a/Corsa/web/index.html#search/q=Rommeldam20230918113151515>_

#### triggers linksonder

- **knop Open detailscherm registratie**:
  - zichtbaar en enabled indien:
    - de inlogger het recht _Wijzigen metadata van geregistreerde documenten_ heeft bij betreffende hoofdzaak
    - de lijst gevuld is.
- **knop Verwijder registratie** (verwijdert alleen de registratie van de aangevinkte documenten en niet de documenten zelf):
  - zichtbaar en enabled indien:
    - compartimentsrecht OK
    - EN de inlogger het recht _Verwijderen registratie zonder verwijderen fysiek document_ heeft bij betreffende hoofdzaak bijv. tbomgrechten.dlcomgcordel)
    - EN de lijst gevuld is.
- **knop Toon documentenlijst**:
  - zichtbaar en enabled indien:
    - de instelling _Sectie: Documenten en Item: Documentregistratie_ is aangevinkt
    - EN de gebruiker het recht _Inzien documenten buiten registratie om_ aangevinkt heeft staan voor de betreffende module (bijv. tbomgrechten.dlcomgcorvsb).
- **knop Creëer document**:
  - zichtbaar en enabled indien:
    - compartimentsrecht OK:
    - de inlogger het recht _creëren van documenten_ heeft bij betreffende hoofdzaak
    - de bovenliggende zaak niet is geblokkeerd
    - de instelling _Sectie: Documenten en Item: Documentregistratie_ is aangevinkt.
- **knop Zend email bericht naar bevoegd gezag** (downloadlink). Zie: [Email secretariaat bevoegd gezag vanuit geregistreerde documenten](../programmablokken/email_secretariaat_bg.md)
  - zichtbaar en enabled indien:
    - kolom _Tekst_ van de instelling*Sectie: Documenten Item: Documentregistratie* gevuld met de string _bgdownloadlink_
    - en de inlogger heeft het recht _Registreren en wijzigen metadata van geregistreerde documenten_ voor de betreffende hoofdzaak bijv. tbomgrechten.dlcomgcoredt.
- **Excelknop**:
  - zichtbaar en enabled inden Excel knop aangevinkt is in de de schermkolomdefinitie (beheerportaal-Nieuw) bij identifier MDLC_getGeregistreerdeDocumentenList.xml.
- **knop Hernoem of verwijder document op fileshare**:
  - zichtbaar en enabled: zie hierboven bij kopje _Hernoem of verwijder document_.
- **knop Download**:
  - zichtbaar en enabled indien de gebruiker het recht _Toelaten geforceerde download geregistreerd document_ aangevinkt heeft staan voor de betreffende module (bijv. tbomgrechten.dlcomgcorregdwl). Met de knop kan het aangewezen document worden gedownload zonder bijlagen (de downloadknop op het detailscherm is een download inclusief bijlagen).
- **knop Download aangevinkte documenten zonder bijlages**:
  - zichtbaar en enabled indien de gebruiker het recht _Toelaten geforceerde download geregistreerd document_ aangevinkt heeft staan voor de betreffende module (bijv. tbomgrechten.dlcomgcorregdwl). Met de knop worden de aangevinkte documenten gedownload zonder bijlagen als zipfile (de downloadknop op het detailscherm is een download inclusief bijlagen). De naam van die zipfile is: DownloadOpenWave_datum_tijstip.zip (bijv. DownloadOpenWave_20201126_093926.zip).
  - Er kan een afwijkende zipfilenaam worden geconstrueerd indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Downloadzipfilenaam_ gevuld is met een tekststring langer dan 5 tekens en eindigend op .zip. In dat geval is de naam van de zipfile de waarde van deze kolom _Tekst_ waarbij de variabele (let op case sensitive):
    - %date% vervangen wordt door TimeStamp
    - %login% wordt vervangen door de medewerkerscode van de inlogger
    - %hoofdzaaknr% wordt vervangen door de wavezaakcode
    - %hoofddmsnr% wordt vervangen door de externe zaak/DMS code
    - %adres% wordt vervangen door het adres + de woonplaats.
- **knop Upload document** Let op: het feitelijke uploaden gebeurt via een separaat proces zonder userinterface (open wave is soms afhankelijk van derden bijv. een DMS). De inlogger zal de refresh knop moeten gebruiken om het resultaat te zien.
  - zichtbaar en enabled indien:
    - compartimentsrecht OK:
    - de inlogger het recht _uploaden van documenten_ heeft bij betreffende hoofdzaak
    - de bovenliggende zaak niet is geblokkeerd.
    - de instelling _Sectie: Documenten en Item: Documentregistratie_ is aangevinkt.
- **knop Synchroniseer met DMS** De synchronisatie vindt plaats op alle geregistreerde documenten van de zaak die voorzien zijn van een externe documentidentificatiecode op de kolommen titel (dvomschrijving in tbcorrespondentie), documenttype, verzenddatum, ontvangstdatum, creatiedatum. Het DMS is dus leidend. De metadata worden opgehaald met vraagbericht: geefLijstZaakdocumenten_ZakLv01 (zie opmerking dct.omschrijving (documenttype) bij [Toon documenten met StUF zaak/DMS](../programmablokken/toon_documenten_en_download/ophalen_met_stuf_zaak_dms).md)
  - zichtbaar en enabled indien:
    - indien geen compartiment dan:
      *moet *Sectie: Documenten Item: OphalenviaDMS* aangevinkt staan
      - EN de instelling _Sectie: Koppeling ZAAK_ en _Item: Methode_ en de kolom _Tekst = StUF-ZAKEN 310_ bestaat en is ook aangevinkt
      - EN de instelling *Sectie: KoppelingDOCNAARDMS Item: SynchroniseerVanuitDMS\* is aangevinkt
    - indien wel compartiment dan:
      _moet kolom dldms aangevinkt zijn bij betreffende compartiment
      _ EN dvdmsmethode moet de waarde _STUF-ZAKEN 310_ hebben \* EN de kolom dlsynchroniseervanuitdms moet aangevinkt zijn
    - EN de Zaak mag niet geblokkeerd zijn
    - EN gebruiker moet rechten op compartiment hebben indien aanwezig
    - EN de zaak moet een externe zaakidentificatie hebben (dvintzaakcode).
- **knop Refresh lijst**:
  - altijd zichtbaar en enabled.
- **knop Vul vervaldatum geselecteerde registraties**:
  - zichtbaar en enabled indien:
    - compartimentsrecht OK:
    - de inlogger het recht _Registreren en wijzigen metadata van geregistreerde documenten_ heeft bij betreffende hoofdzaak
    - de bovenliggende zaak niet is geblokkeerd
