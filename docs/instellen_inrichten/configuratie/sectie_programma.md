# Sectie Programma

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de _Sectie: Programma_ gerangschikt op item.

## Items Configuratietabel

| Item | Kolom | Omschrijving |
| --------------------- | ------------ | ------------ |
| AanhefContactpersonen | Tekst | Hetgeen hier wordt gevuld vervangt bij de berekening van de briefaanhef (contacten-detailscherm) het woordje 'Geachte'. |
| AdresrolViaZaaktype | Aanvinkvakje | Indien aangevinkt zal bij het handmatig aanmaken van een nieuwe zaak gekeken worden naar de kolom _verplichte adresrol_ (bijv. tbsoortomgverg.dvadressoortverpl) bij de zaaktypedefinitie. Indien die rol gevuld dan zal een contactpersoon onder die rol moeten worden toegevoegd. Indien die rol leeg is dan hoeft geen contactpersoon te worden toegevoegd. | Indien deze instelling niet is aangevinkt geldt dat bij alle type hoofdzaken een contactpersoon met de rol AVR moet worden toegevoegd (uitzondering: bij handhavingszaken is dit HPC). |
| Afzemaildefvolg | Tekst | 1, 2 of 3. Indien 1 dan wordt default het emailadres (tbmedewerkers.dvemail) van de verzender voorgesteld als afzender, indien 2 dan het niet persoonlijke emailadres (dvnietperemail) van de verzender en 3 dan kolom _Tekst_ van de instelling _Sectie: Programma en Item: NoReplyEmailAdres._ Bij een compartiment kan deze default ook ingesteld worden in de kolom dvafzemaildefvolg. |
| ApvAantCollegToetsZichtbaar | Aanvinkvakje |Indien aangevinkt dan zijn drie kolommen m.b.t. uitstaande en geretourneerde collegiale toetsen extra zichtbaar in de lijst met openstaande APV/Overige zaken: dnaantalctuitstaand, dnaantalctretour en dnaantalctgezien. |
| BezwaarberoepDesktop | Aanvinkvakje |Deprecated. Indien aangevinkt kijkt het programma voor het plaatsen van het weegschaalicoontje op de #zi zakenlijst niet naar de tabel tbbezwaarberoep, maar naar de kolommen ddindieningbezwaar of ddrbindieningberoep van de hoofdzaak (die ook deprecated zijn). |
| BeperkteKolommenChecklist | Aanvinkvakje | Indien aangevinkt zijn de kolommen _Groep_ en _Volgnummer_ NIET zichtbaar bij het overzicht van checklistitems. |
| BezwaarberoepIsZaak | Aanvinkvakje | Indien aangevinkt zijn de externe zaak/DMS kolommen bij bezwaarberoep zichtbaar en operationeel. |
| CBSZichtbaarNegeerZaakstatus | Aanvinkvakje | Indien aangevinkt zal OpenWave bij het afwegen of de omgevingszaak/vergunning voldoet aan de voorwaarden of er een W011/CBS kaart moet worden aangemaakt, niet meer kijken naar de besluitdatum en de status van de zaak. Heeft dus invloed op de zichtbaarheid van het CBS icoon in Omgevingdetailscherm en de CBS tegel in het OmgevingsportaalVoor de volledige voorwaarden CBS zie kopje _CBS bij triggers linksonder in scherm_ bij [Detailscherm Omgevingszaak](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken.md). |
| Collation | Aanvinkvakje | Indien aangevinkt zal OpenWave - op het moment dat een gebruiker op een label van een lijst klikt - de lijst sorteren volgens de ingevoerde collation in kolom _Tekst_. Het gaat hierbij om het sorteren op een (enkel) stringveld. Dus de collation wordt niet toegepast op integer, float en datumvelden. OpenWave kijkt naar de betreffende kolomnaam: in de tabel of view: die moet beginnen met dv. De collation wordt NIET toegepast op de lijst gebaseerd op vwfrminitialisatie (van de configuratietabel zelf). |
| | Tekst |In de kolom _Tekst_ de gewenste collation. Niet alle collation zijn daarvoor geschikt. Wel dus de default "fr-FR-x-icu". Deze default zorgt voor een case-insensitive sortering waarbij accenten e.d. worden genegeerd. De collation moet hier genoteerd worden inclusief de dubbele aanhalingstekens. |
|ComplexGereedAlleZaken | Aanvinkvakje | Indien aangevinkt zal OpenWave de functionaliteit _Complex gereedmelden_ via het scherm _Alle zaken_ ook van toepassing zijn voor niet-complexe zaken: voorwaarde is dat het omgevingszaken zijn met openstaande werkzaamheiddatum(s) voor activiteiten waarop eigenschap Complex gereedmelden van toepassing is. |
| Defaultkeyovertreding | Getal1 |_Getal1_ verwijst naar een dnkey van tbhandhovertreding die gebruikt wordt als default overtreding bij de aanmaak van een nieuwe handhavingszaak. |
| Defbehbijvervolgzaak | Aanvinkvakje |Indien aangevinkt zal de defaultbehandelaar bij het aanmaken van een vervolgzaak (dus vanuit een processtap) uit de definitie van het zaaktype worden opgehaald. Zo niet, dan is de inlogger de defaultbehandelaar. Alleen indien de instelling _Sectie: Programma en Item: NieuweZaakKiesBehandelaar_ ook aangevinkt is, zal de inlogger kunnen kiezen uit dropdownlijst. |
| DSOPortaalZonderVooroverleg | Aanvinkvakje | Indien aangevinkt dan zal OpenWave niet tegel _Mijn DSO projecten_ tonen in het Openingsportaal maar de tegel _Mijn DSO projecten (zonder vooroverleg)_. Dit houdt in dat de DSO projecten waarvoor alleen een Vooroverleg-zaak aanwezig is, niet zichtbaar zijn in de lijst met DSO projecten waarvan de medewerker 1 van de actieve behandelaars is. |
| Exportmapdsometadata | Tekst |Het gewenste documenttype van de geëxporteerde documenten. Zie [Export DSO-Documenten naar DMS van bevoegd gezag](/docs/probleemoplossing/programmablokken/export_documenten_bij_dso_zaak_van_map_naar_dms_bevoegd_gezxag.md). |
| | Info |De gewenste vertrouwelijkheid. |
| Exportdocvanmapnaarbevoegdgez | aanvinkvakje |Indien aangevinkt is de kolom ddexportdocbevgez zichtbaar in het detailscherm van omgevingskaart in het blok Afhandeling. Zie [Export DSO-Documenten naar DMS van bevoegd gezag](/docs/probleemoplossing/programmablokken/export_documenten_bij_dso_zaak_van_map_naar_dms_bevoegd_gezxag.md). |
| | Tekst |Hierin kan een opsomming staan van OIN-nummers. Indien een een omgevingszaak een DSO-zaak is en de besluitdatum is gevuld en de kolom ddexportdocbevgez is leeg en het OIN van het bevoegd gezag komt voor in deze _Tekst_, dan komen deze omgevingszaken in de lijst achter de tegel _Exportlijst docs naar bev. gezag_ op het hoofdportaal. |
| | Info |De tekst in kolom _Info_ wordt gebruikt voor de koptekst in het lijstscherm achter de tegel _Exportlijst docs naar bev. gezag_. Hierin kunnen de gemeentenamen opgesomd worden die horen bij de kolom _Tekst_. |
| | Toelichting |De map per zaak waar de de te exporteren documenten staan. Deze moeten genoteerd worden inclusief documentroot dus bijvoorbeeld `\\Nitro\\Wave\\Omgeving\%zaakjaar%\%zaaknr%\DMS\`, waarbij de variabelen `%zaaknr%` en `%zaakjaar%` door OpenWave on the fly worden vervangen. |
| ExportItp | Aanvinkvakje | Indien aangevinkt dan is de export - itp datum (tbomgvergunning.dditp) met bijbehorende knop zichtbaar in het detailscherm van een omgevingszaak. Zie verdere uitleg bij [Detailscherm Omgevingszaak](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken.md). |
| Extra_zaakinformatie | Aanvinkvakje | Indien aangevinkt dan is in het detailscherm van de zaak (omgeving en handhaving) het blok _Extra informatie_ zichtbaar. Hier vindt men extra informatie over de zaak zoals bestuurlijk gevoeligheid, domein van de zaak en kan aangeven worden wat de moeilijkheidscategorie is indien het gaat om een bezwaar/beroep zaak. |
| HahAantCollegToetsZichtbaar | Aanvinkvakje |Indien aangevinkt dan zijn drie kolommen m.b.t. uitstaande en geretourneerde collegiale toetsen extra zichtbaar in de lijst met openstaande handhavingszaken: dnaantalctuitstaand, dnaantalctretour en dnaantalctgezien. |
|Handhaving uit inspectie genereren| Aanvinkvakje |Indien aangevinkt en een inspectiekaart nog niet is gekoppeld aan een handhavingszaak en de module ongelijk aan Handhavingen is en de inlogger lid is van een rechtengroep die insert-rechten heeft op Handhavingen DAN is de knop op het detailscherm van een inspectietraject toegankelijk waarmee van een traject een handhavingszaak kan worden gemaakt. |
| | Getal1 | Indien de waarde 1 dan is de actieve behandelaar van de nieuwe handhavingszaak gelijk aan de ingestelde defaultbehandelaar van de gekozen soort zaak. Anders is de behandelaar gelijk aan de inlogger. |
| | Getal2 | Indien de waarde 1 dan wordt het inspectietraject (en bezoeken en overtredingen) gekopieerd naar de nieuwe handhavingszaak. Anders wordt het bestaande inspectietraject alleen gekoppeld aan de nieuwe handhavingszaak. |
| | Tekst | Indien _Getal2_ = 1 en de kolom _Tekst_ bevat als waarde een ID (dnkey) van de beheertabel tbinspresultaat, dan wordt na het dupliceren het oude traject afgesloten met de verwijzing van deze dnkey op de systeemdatum. |
| | Info | Indien kolom _Info_ van de instelling _Sectie: Programma Item: Handhaving_ uit inspectie genereren de waarde tbinsponrechtm heeft, dan kan de inlogger t.b.v. de hoofdovertreding waarop de handhavingszaak wordt aangemaakt alleen kiezen uit de overtredingen die in de tabel tbinsponrechtm zijn opgenomen bij het betreffende inspectietraject. Echter indien de waarde van de kolom _Info_ tbinsponrechtm_openstaand heeft dan kan de inlogger alleen kiezen uit de openstaande overtredingen die in de tabel tbinsponrechtm zijn opgenomen bij het betreffende inspectietraject. Voor beide gevallen geldt dat als die lijst leeg is dan kan rechtstreeks gekozen worden uit de items van tabel tbhandhovertreding (beheerportaal _Zaakbeheer_). |
|Handhaving in groep genereren| Aanvinkvakje |Indien vanuit een inspectietraject een handhavingszaak wordt gegenereerd, dan wordt de nieuwe handhavingszaak verbonden in een groep aan de basiszaak van het inspectietraject. |
| HoofdprojlocatieAlleModules | Aanvinkvakje |Indien aangevinkt dan wordt voor Projectlocatie omschrijving bij het aanmaken van een nieuw kadastraal perceel/projectlocatie (of het wijzigen van een bestaande) niet alleen van die module de al bestaande Hoofdprojectlocaties getoond, maar ook van de andere modules (mits de zaak/inrichting op hetzelfde perceeladres afspeelt als de zaak/inrichting waar men nieuwe projectlocatie aanmaakt). |
| HorAantCollegToetsZichtbaar | Aanvinkvakje |Indien aangevinkt dan zijn drie kolommen m.b.t. uitstaande en geretourneerde collegiale toetsen extra zichtbaar in de lijst met openstaande horecazaken: dnaantalctuitstaand, dnaantalctretour en dnaantalctgezien. |
| InfAantCollegToetsZichtbaar | Aanvinkvakje |Indien aangevinkt dan zijn drie kolommen m.b.t. uitstaande en geretourneerde collegiale toetsen extra zichtbaar in de lijst met openstaande infoaanvraagzaken: dnaantalctuitstaand, dnaantalctretour en dnaantalctgezien. |
| InwerkingsdatumAutoVullen | Aanvinkvakje | Standaard aangevinkt. Indien deze instelling UIT wordt gezet, dan zal niet meer automatisch de in werking datum worden gevuld bij het zetten van de verzenddatum voor omgevingszaken van type Regulier en Uitgebreid. Deze instelling heeft geen invloed op het automatisch vullen van de in werking datum bij het zetten van de verzenddatum voor de overige modules (handhaving, APV/overig etc.). |
| JavaWIN1252 | Aanvinkvakje | Standaard uit. Vanaf 1.29 is de OpenWave database in karakterset UTF-8. Dit betekent dat de database een groter aantal tekens aan kan dan voorheen. Het voorheen filteren van tekens die niet konden worden opgeslagen in de OpenWave database is daarom niet meer van toepassing. Indien in uitzonderlijke geval het toch gewenst is dat OpenWave de oude filtering toepast van tekens op de binnenkomende berichten via JAVA, dan dient men deze instelling aan te vinken. Instelling aan betekent dat alle tekens boven ASCII-waarde 127 in de binnenkomende berichten worden omgezet (ë naar e etcetera). De te verwerken binnenkomende berichten via JAVA waar het om gaat is berichtverkeer met BRP/NHR en Digitale Checklisten. |
| KaartCsscolornameInrichting | Tekst |Deze waarde wordt gebruikt voor een vlak op de interne kaart voor het grondgebied van een inrichting. Default = _Salmon_. De kleur moet een CSS colorname zijn: zie [http://www.w3schools.com/cssref/css_colors.asp](http://www.w3schools.com/cssref/css_colors.asp.md) . |
| KaartCsscolornameHoofdzaak | Tekst |Deze waarde wordt gebruikt voor een vlak op de interne kaart voor het grondgebied van een hoofdzaak. Default = _Salmon_. De kleur moet een CSS colorname zijn: zie [http://www.w3schools.com/cssref/css_colors.asp](http://www.w3schools.com/cssref/css_colors.asp.md) . |
| KaartCsscolornamePerceel | Tekst |Deze waarde wordt gebruikt voor een vlak of marker op de interne kaart om een perceeladres te duiden. Default = _Red_. De kleur moet een CSS colorname zijn: zie [http://www.w3schools.com/cssref/css_colors.asp](http://www.w3schools.com/cssref/css_colors.asp.md) . |
| KadastrgemSortering | Getal1 |Indien de waarde 1 dan worden de dropdowns voor het kiezen van een kadastrale gemeente gesorteerd op gemeentenaam en in alle andere gevallen op kadastrale gemeente code. |
| KopieerHahKolommen | Tekst |De kolom _Tekst_ kan gevuld worden kolomnamen uit tbhandhavingen die gebruikt worden bij het kopiëren van een handhavingzaak (vanuit processtap). De kolomnamen moeten gescheiden zijn door een puntkomma (zonder spaties). De kolomnamen moeten ONGELIJK zijn aan dnkey, dnkeygroepvergunning en dnkeysoorthhzaak, dnkeyperceeladressen, dvomsbouwerk, ddverzoekdatum ( = startdatum in openwave), dvaanschrijfnr (= zaakcode in OpenWave) , ddfataledatum, dnkeyoinbevgez.|
| KopieerOmgKolommen | Tekst |De kolom _Tekst_ kan gevuld worden kolomnamen uit tbomgvergunning die gebruikt worden bij het kopiëren van een omgevingszaak (vanuit processtap). De kolomnamen moeten gescheiden zijn door een puntkomma (zonder spaties). De kolomnamen moeten ONGELIJK zijn aan dnkey, dnkeygroepvergunning en dnkeysoortomgverg, dnkeyperceeladressen, dvaanvraagnaam, ddaanvraag, dvzaakcode, ddfataledatum. |
| | Getal1 |Indien een zaak wordt gekopieerd waarbij de kolom dvlvoaanvraagnummer is opgenomen in kolom _Tekst_ dan redeneert het programma als volgt bij het maken van de nieuwe zaak: Indien _Getal1_ van die instelling de waarde 1 heeft, dan wordt het OLO/DSO-nummer (dvlvoaanvraagnr) van de zaak die gekopieerd wordt voorzien van de postfix underscore + 1 (indien \_1 al bestaat dan_2 en zo verder met maximum van 100). Anders (dus _Getal1_ is ongelijk aan 1) dan wordt de nieuwe gekopieerde kaart voorzien van die postfix. Dit laatste is nodig om de uniciteit van de kolom dvlvoaanvraagnr te behouden in verband met opvangen van aanvullende documenten van het OLO/DSO. Wanneer het de bedoeling is dat aanvullende (OLO)-documenten bij de oorspronkelijke zaak terechtkomen dan moet _Getal1_ leeg blijven. Indien het de bedoeling is dat de aanvullende documenten bij de nieuwe zaak terechtkomen dan moet _Getal1_ de waarde 1 hebben. |
| KoppelZaakInrichtingAanHandhaving | Aanvinkvakje |Indien aangevinkt, dan zal bij het genereren van een handhavingzaak vanuit een inspectietraject, hangende aan een zaak (module W,H,C,B of O), een gekoppelde inrichting opgenomen worden in de nieuwe handhavingzaak. |
| NieuweInrichtingGaNaarInrichtingPortaal | Aanvinkvakje |Indien aangevinkt zal na het handmatig aanmaken van een nieuwe inrichting automatisch door genavigeerd worden naar het betreffende inrichtingsportaal. |
| NieuweZaakBijInrichting | Aanvinkvakje |Indien aangevinkt en rechten inlogger OK, is de wizard voor het aanmaken van een nieuwe, aan de inrichting gekoppelde omgevingszaak benaderbaar vanuit het detailscherm van een inrichting ([zie Dokuwiki](/docs/probleemoplossing/portalen_en_moduleschermen/inrichtingen_portaal/detailscherm_inrichtingen.md)). |
| NieuweZaakGeenBAGSync | Aanvinkvakje | Indien aangevinkt zal bij het handmatig aanmaken van een nieuwe zaak of inrichting, gekeken worden of het opgegeven huisnummer voorkomt in het veld _Tekst_. Zo ja, dan wordt er geen BAG synchronisatie uitgevoerd. Zo nee, dan wordt er wel gesynchroniseerd met de BAG. |
| | Tekst | Huisnummers waarvoor BAG synchronisatie overgeslagen moet worden zijn hier op te geven gescheiden met een puntkomma. Bijvoorbeeld als voor huisnummers 0 en 9999 geen BAG synchronisatie plaats moet vinden dan is de waarde van tekst: 0;9999. |
| NieuweZaakExtraContactInfo | Aanvinkvakje |Indien aangevinkt zal bij het handmatig aanmaken van een nieuwe zaak indien er een nieuwe contact gedefinieerd wordt, de volgende extra gegevens voor het contactpersoon opgegeven kunnen worden: voorletters, voorvoegsel, geslacht, telefoonnummer en e-mailadres. |
| NieuweZaakGaNaarZaakPortaal | Aanvinkvakje |Indien aangevinkt zal na het handmatig aanmaken van een nieuwe zaak automatisch door genavigeerd worden naar het betreffende zaakportaal, tenzij de zaak is aangemaakt vanuit een processtap (dan keert de gebruiker terug naar het proces). |
| NieuweZaakKiesBehandelaar | Aanvinkvakje |Indien aangevinkt zal bij het handmatig aanmaken van een nieuwe zaak voor de dossierbehandelaar een keuze gemaakt kunnen worden uit de medewerkerslijst (met default de waarde zoals ingesteld bij het zaaktype). Niet aangevinkt berekent dat de dossierbehandelaar gelijk wordt aan die van de inlogger. |
| NieuweZaakUitvoerendeInstantie | Aanvinkvakje |Indien aangevinkt en kolom _Tekst_ is gevuld met een geldig OIN-nummer dan zal bij het handmatig aanmaken van een nieuwe Omgevingszaak voor deze zaak de Uitvoerende instantie gevuld worden. |
| | Tekst | OIN-nummer dat bij het aanmaken van een nieuwe Omgevingszaak gebruikt zal worden voor het zetten van de Uitvoerende instantie voor deze zaak. |
| NoReplyEmailAdres | Tekst |Algemeen email adres voor no reply berichten. Bij compartiment kijkt OpenWave naar tbcompartiment.dvNoReplyEmailAdres. |
| OmgAantCollegToetsZichtbaar | Aanvinkvakje |Indien aangevinkt dan zijn drie kolommen m.b.t. uitstaande en geretourneerde collegiale toetsen extra zichtbaar in de lijst met openstaande omgevingszaken: dnaantalctuitstaand, dnaantalctretour en dnaantalctgezien. |
| OmgActiviteitLocatieOvernemen | Aanvinkvakje |Indien aangevinkt dan zal bij het aanmaken van een nieuwe omgevingszaak via een vervolgactie (actie achter processtap) bij een omgevingszaak, de onderdelen/activiteiten en projectlocaties van de originele omgevingszaak worden overgenomen bij de nieuw aangemaakte zaak. |
| OmgDMScodeAlsGroepnaam | Aanvinkvakje |Indien aangevinkt wordt bij het aanmaken van de groep niet de zaakomschrijving maar het DMS-nummer van de originele zaak als waarde gepakt. |
|Openstaande overtredingen| Aanvinkvakje |Indien aangevinkt dan zullen (bij het genereren van een handhavingszaak vanuit een inspectietraject) alleen de openstaande overtredingen worden meegenomen naar de nieuwe handhavingszaak. Dit wil zeggen dat bij deze overtredingen het veld _Datum opgelost_ leeg is of groter dan vandaag. |
| OmgDvFatalePeriodeZichtbaar | Aanvinkvakje |Indien aangevinkt is in het detailscherm van de omgevingszaak in het blok afhandeling de kolom Ber.wijze fat.termijn (dnkeyfataletermijnen) zichtbaar, waarmee voor die zaak de default fatale periode (dnfataleperiode) uit tbsoortomgverg kan worden overschreven met een keuze uit de tabel tbfataletermijnen (gekoppeld aan bettreffende zaaktype). |
| Opschonenmissingconfiguration | Getal1 |Het aantal dagen dat kaarten in de tabel tbmissingconfiguration bewaard moeten blijven (default 30). |
| RapportCSVKolomOmhuld | Tekst |Hier geeft men het karakter/teken op waarmee bij uitdraai van een rapport naar .csv (momenteel alleen van toepassing bij de FisExport mits zelf ingesteld), de waarde in een kolom omhult moeten worden. Let op: mag niet hetzelfde teken zijn als bij instelling RapportCSVKolomScheiding! |
| RapportCSVKolomScheiding | Tekst |Hier geeft men het karakter/teken op waarmee bij uitdraai van een rapport naar .csv (momenteel alleen van toepassing bij de FisExport mits zelf ingesteld), de kolommen gescheiden moeten worden. Let op: mag niet hetzelfde teken zijn als bij instelling RapportCSVKolomOmhuld! |
| Roeb | Aanvinkvakje |Indien aangevinkt wordt het blok _ROEB_ (waarin berekening vastgestelde kosten wordt geregeld) zichtbaar in het detailscherm van een onderdeel/activiteit (tbtoestemmingen) bij een omgevingszaak. Indien de zaak speelt in een compartiment, dan wordt i.p.v. naar deze instelling, gekeken naar de kolom dlroeb van dat compartiment. |
| |Getal1| Indien de waarde 1 dan krijgt de berekende roebkostenkolom (vwfrmtoestemmingen.dflegesvastgroeb) voor de vaststelling van het uitgangsbedrag bij de legesberekening voorrang boven de handmatig ingestelde kolom dflegesvastgbasis|
| SamenvoegenTabellenMetLetters | Aanvinkvakje |Indien aangevinkt dan verwacht het programma bij het samenvoegen van tabeldata in een sjabloon geen coderingen met cijfers, maar met letters. Dus niet {1} en {2}, maar {a} en {b}. Dit kan noodzakelijk zijn i.v.m. de verwerking van Open Document Format files. |
| SluitOpenInspbijSluitenZaak | Aanvinkvakje |Indien aangevinkt en er zijn openstaande inspectietrajecten en inspecties zijn geen externe zaken (DMS) dan zal bij de zaak sluiten via wizard _SluitZaak_ gevraagd worden om de openstaande inspectietrajecten (en onderliggende bezoeken en overtredingen) af te sluiten. |
| SluitProductenbijSluitenZaak | Aanvinkvakje |Indien aangevinkt en er zijn openstaande producten dan zal bij het sluiten van de zaak via wizard _SluitZaak_ gevraagd worden om de openstaande producten te voorzien van een opleverdatum. |
| Sluitzaakresultbekend | Aanvinkvakje |Indien aangevinkt en het aard besluit is al bekend bij de zaak (bijv. via processtap) dan zal de wizard _SluitZaak_ niet toestaan dat het aard besluit overschreven wordt. |
| Toonkaart | Getal2 | Het zoomlevel waarmee de interne OpenWave kaart opstart. Indien een externe kaartviewer wordt gebruikt is dit een verplicht veld. |
| | Info |Indien deze kolom een gevulde waarde heeft dan beschouwt OpenWave die gevulde waarde als een URL van een externe kaartviewer die geopend moet worden als de gebruiker op de _Toon kaart_ knop klikt vanuit een detailscherm of een portal. Wanneer die kolom _Info_ niet is gevuld, dan wordt de standaardkaart (interne kaartviewer) van OpenWave aangeroepen. In die URL-string zal OpenWave eerst de variabelen: %x% vervangen door de x-coördinaat van het bijbehorende locatie adres, %y% vervangen door de y-coördinaat van het bijbehorende locatie adres, %zoom% vervangen door _Getal2_. |
| | Aanvinkvakje | Indien aangevinkt kan de interne of externe kaart worden gebruikt met de _Toon kaart_ knop vanuit een detailscherm of een portal. |
| VlakNietOpZaakniveau | Aanvinvakje |Indien aangevinkt dan is het blok met het getekende vlak (dvgmlpolygoon) op de detailschermen van omgeving en handhaving niet zichtbaar. Ook is de optie _teken vlak_ in het menu op deze detailschermen dan uitgeschakeld. |
| ZaaktypeWijzigenProcessenWijzigen | Aanvinkvakje |Indien aangevinkt dan zal in het detailscherm van Omgeving-, Handhaving- en APV/Overige zaken het wijzigen van zaaktype verlopen via een Wizard (i.p.v. bekende keuzelijst). Via deze wizard zijn naast het wijzigen van het zaaktype, optioneel ook de processen te wijzigen. Indien hiervoor gekozen wordt zullen de automatisch aan te maken processen bij het gekozen zaaktype de huidige processen bij de zaak vervangen. |
| ZaaktypeWijzigenProductenVerwijderen | Aanvinkvakje |Indien aangevinkt dan zal bij het wijzigen van het zaaktype de (evt.) gekoppelde product(en) verwijderd worden. Dit geldt voor zowel de situatie maximaal 1 product per zaak (bijv. tbomgvergunning.dnkeyproduct en dnkeysubproduct worden leeggemaakt) als meerdere producten per zaak (rijen in tbzaakproducten voor de zaak worden verwijderd). Dit gebeurd zonder melding/waarschuwing TENZIJ het zaaktype gewijzigd wordt via een Wizard (zie instelling _ZaaktypeWijzigenProcessenWijzigen_). In dat geval zal er gevraagd worden aan de gebruiker of de product(en) verwijderd moeten worden bij het wijzigen van het zaaktype. |