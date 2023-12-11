Sectie Programma
================

Hieronder de instellingen uit de
`configuratietabel </docs/instellen_inrichten/configuratie.md>`__
(tbinitialisatie) van de *Sectie: Programma* gerangschikt op item.

Items Configuratietabel
-----------------------

+--------------------------+--------------+--------------------------+
| Item                     | Kolom        | Omschrijving             |
+==========================+==============+==========================+
| AanhefContactpersonen    | Tekst        | Hetgeen hier wordt       |
|                          |              | gevuld vervangt bij de   |
|                          |              | berekening van de        |
|                          |              | briefaanhef              |
|                          |              | (contacten-detailscherm) |
|                          |              | het woordje 'Geachte'.   |
+--------------------------+--------------+--------------------------+
| AdresrolViaZaaktype      | Aanvinkvakje | Indien aangevinkt zal    |
|                          |              | bij het handmatig        |
|                          |              | aanmaken van een nieuwe  |
|                          |              | zaak gekeken worden naar |
|                          |              | de kolom *verplichte     |
|                          |              | adresrol* (bijv.         |
|                          |              | tbsoortom                |
|                          |              | gverg.dvadressoortverpl) |
|                          |              | bij de                   |
|                          |              | zaaktypedefinitie.       |
|                          |              | Indien die rol gevuld    |
|                          |              | dan zal een              |
|                          |              | contactpersoon onder die |
|                          |              | rol moeten worden        |
|                          |              | toegevoegd. Indien die   |
|                          |              | rol leeg is dan hoeft    |
|                          |              | geen contactpersoon te   |
|                          |              | worden toegevoegd.       |
+--------------------------+--------------+--------------------------+
| Afzemaildefvolg          | Tekst        | 1, 2 of 3. Indien 1 dan  |
|                          |              | wordt default het        |
|                          |              | emailadres               |
|                          |              | (tbmedewerkers.dvemail)  |
|                          |              | van de verzender         |
|                          |              | voorgesteld als          |
|                          |              | afzender, indien 2 dan   |
|                          |              | het niet persoonlijke    |
|                          |              | emailadres               |
|                          |              | (dvnietperemail) van de  |
|                          |              | verzender en 3 dan kolom |
|                          |              | *Tekst* van de           |
|                          |              | instelling *Sectie:      |
|                          |              | Programma en Item:       |
|                          |              | NoReplyEmailAdres.* Bij  |
|                          |              | een compartiment kan     |
|                          |              | deze default ook         |
|                          |              | ingesteld worden in de   |
|                          |              | kolom dvafzemaildefvolg. |
+--------------------------+--------------+--------------------------+
| Apv                      | Aanvinkvakje | Indien aangevinkt dan    |
| AantCollegToetsZichtbaar |              | zijn drie kolommen       |
|                          |              | m.b.t. uitstaande en     |
|                          |              | geretourneerde           |
|                          |              | collegiale toetsen extra |
|                          |              | zichtbaar in de lijst    |
|                          |              | met openstaande          |
|                          |              | APV/Overige zaken:       |
|                          |              | dnaantalctuitstaand,     |
|                          |              | dnaantalctretour en      |
|                          |              | dnaantalctgezien.        |
+--------------------------+--------------+--------------------------+
| BezwaarberoepDesktop     | Aanvinkvakje | Deprecated. Indien       |
|                          |              | aangevinkt kijkt het     |
|                          |              | programma voor het       |
|                          |              | plaatsen van het         |
|                          |              | weegschaalicoontje op de |
|                          |              | #zi zakenlijst niet naar |
|                          |              | de tabel                 |
|                          |              | tbbezwaarberoep, maar    |
|                          |              | naar de kolommen         |
|                          |              | ddindieningbezwaar of    |
|                          |              | ddrbindieningberoep van  |
|                          |              | de hoofdzaak (die ook    |
|                          |              | deprecated zijn).        |
+--------------------------+--------------+--------------------------+
| B                        | Aanvinkvakje | Indien aangevinkt zijn   |
| eperkteKolommenChecklist |              | de kolommen *Groep* en   |
|                          |              | *Volgnummer* NIET        |
|                          |              | zichtbaar bij het        |
|                          |              | overzicht van            |
|                          |              | checklistitems.          |
+--------------------------+--------------+--------------------------+
| BezwaarberoepIsZaak      | Aanvinkvakje | Indien aangevinkt zijn   |
|                          |              | de externe zaak/DMS      |
|                          |              | kolommen bij             |
|                          |              | bezwaarberoep zichtbaar  |
|                          |              | en operationeel.         |
+--------------------------+--------------+--------------------------+
| CBSZ                     | Aanvinkvakje | Indien aangevinkt zal    |
| ichtbaarNegeerZaakstatus |              | OpenWave bij het afwegen |
|                          |              | of de                    |
|                          |              | omgevingszaak/vergunning |
|                          |              | voldoet aan de           |
|                          |              | voorwaarden of er een    |
|                          |              | W011/CBS kaart moet      |
|                          |              | worden aangemaakt, niet  |
|                          |              | meer kijken naar de      |
|                          |              | besluitdatum en de       |
|                          |              | status van de zaak.      |
|                          |              | Heeft dus invloed op de  |
|                          |              | zichtbaarheid van het    |
|                          |              | CBS icoon in             |
|                          |              | Omgevingdetailscherm en  |
|                          |              | de CBS tegel in het      |
|                          |              | OmgevingsportaalVoor de  |
|                          |              | volledige voorwaarden    |
|                          |              | CBS zie kopje *CBS bij   |
|                          |              | triggers linksonder in   |
|                          |              | scherm* bij              |
|                          |              | `Detailscherm            |
|                          |              | Om                       |
|                          |              | gevingszaak </docs/probl |
|                          |              | eemoplossing/portalen_en |
|                          |              | _moduleschermen/zaakport |
|                          |              | aal_omgeving/detailscher |
|                          |              | m_omgevingszaken.md>`__. |
+--------------------------+--------------+--------------------------+
| Collation                | Aanvinkvakje | Indien aangevinkt zal    |
|                          |              | OpenWave - op het moment |
|                          |              | dat een gebruiker op een |
|                          |              | label van een lijst      |
|                          |              | klikt - de lijst         |
|                          |              | sorteren volgens de      |
|                          |              | ingevoerde collation in  |
|                          |              | kolom *Tekst*. Het gaat  |
|                          |              | hierbij om het sorteren  |
|                          |              | op een (enkel)           |
|                          |              | stringveld. Dus de       |
|                          |              | collation wordt niet     |
|                          |              | toegepast op integer,    |
|                          |              | float en datumvelden.    |
|                          |              | OpenWave kijkt naar de   |
|                          |              | betreffende kolomnaam:   |
|                          |              | in de tabel of view: die |
|                          |              | moet beginnen met dv. De |
|                          |              | collation wordt NIET     |
|                          |              | toegepast op de lijst    |
|                          |              | gebaseerd op             |
|                          |              | vwfrminitialisatie (van  |
|                          |              | de configuratietabel     |
|                          |              | zelf).                   |
+--------------------------+--------------+--------------------------+
|                          | Tekst        | In de kolom *Tekst* de   |
|                          |              | gewenste collation. Niet |
|                          |              | alle collation zijn      |
|                          |              | daarvoor geschikt. Wel   |
|                          |              | dus de default           |
|                          |              | "fr-FR-x-icu". Deze      |
|                          |              | default zorgt voor een   |
|                          |              | case-insensitive         |
|                          |              | sortering waarbij        |
|                          |              | accenten e.d. worden     |
|                          |              | genegeerd. De collation  |
|                          |              | moet hier genoteerd      |
|                          |              | worden inclusief de      |
|                          |              | dubbele                  |
|                          |              | aanhalingstekens.        |
+--------------------------+--------------+--------------------------+
| ComplexGereedAlleZaken   | Aanvinkvakje | Indien aangevinkt zal    |
|                          |              | OpenWave de              |
|                          |              | functionaliteit *Complex |
|                          |              | gereedmelden* via het    |
|                          |              | scherm *Alle zaken* ook  |
|                          |              | van toepassing zijn voor |
|                          |              | niet-complexe zaken:     |
|                          |              | voorwaarde is dat het    |
|                          |              | omgevingszaken zijn met  |
|                          |              | openstaande              |
|                          |              | werkzaamheiddatum(s)     |
|                          |              | voor activiteiten waarop |
|                          |              | eigenschap Complex       |
|                          |              | gereedmelden van         |
|                          |              | toepassing is.           |
+--------------------------+--------------+--------------------------+
| Defaultkeyovertreding    | Getal1       | *Getal1* verwijst naar   |
|                          |              | een dnkey van            |
|                          |              | tbhandhovertreding die   |
|                          |              | gebruikt wordt als       |
|                          |              | default overtreding bij  |
|                          |              | de aanmaak van een       |
|                          |              | nieuwe handhavingszaak.  |
+--------------------------+--------------+--------------------------+
| Defbehbijvervolgzaak     | Aanvinkvakje | Indien aangevinkt zal de |
|                          |              | defaultbehandelaar bij   |
|                          |              | het aanmaken van een     |
|                          |              | vervolgzaak (dus vanuit  |
|                          |              | een processtap) uit de   |
|                          |              | definitie van het        |
|                          |              | zaaktype worden          |
|                          |              | opgehaald. Zo niet, dan  |
|                          |              | is de inlogger de        |
|                          |              | defaultbehandelaar.      |
|                          |              | Alleen indien de         |
|                          |              | instelling *Sectie:      |
|                          |              | Programma en Item:       |
|                          |              | Ni                       |
|                          |              | euweZaakKiesBehandelaar* |
|                          |              | ook aangevinkt is, zal   |
|                          |              | de inlogger kunnen       |
|                          |              | kiezen uit               |
|                          |              | dropdownlijst.           |
+--------------------------+--------------+--------------------------+
| DSO                      | Aanvinkvakje | Indien aangevinkt dan    |
| PortaalZonderVooroverleg |              | zal OpenWave niet tegel  |
|                          |              | *Mijn DSO projecten*     |
|                          |              | tonen in het             |
|                          |              | Openingsportaal maar de  |
|                          |              | tegel *Mijn DSO          |
|                          |              | projecten (zonder        |
|                          |              | vooroverleg)*. Dit houdt |
|                          |              | in dat de DSO projecten  |
|                          |              | waarvoor alleen een      |
|                          |              | Vooroverleg-zaak         |
|                          |              | aanwezig is, niet        |
|                          |              | zichtbaar zijn in de     |
|                          |              | lijst met DSO projecten  |
|                          |              | waarvan de medewerker 1  |
|                          |              | van de actieve           |
|                          |              | behandelaars is.         |
+--------------------------+--------------+--------------------------+
| Exportmapdsometadata     | Tekst        | Het gewenste             |
|                          |              | documenttype van de      |
|                          |              | geëxporteerde            |
|                          |              | documenten. Zie `Export  |
|                          |              | DSO-Documenten naar DMS  |
|                          |              | van bevoegd              |
|                          |              | gezag </docs/probleemo   |
|                          |              | plossing/programmablokke |
|                          |              | n/export_documenten_bij_ |
|                          |              | dso_zaak_van_map_naar_dm |
|                          |              | s_bevoegd_gezxag.md>`__. |
+--------------------------+--------------+--------------------------+
|                          | Info         | De gewenste              |
|                          |              | vertrouwelijkheid.       |
+--------------------------+--------------+--------------------------+
| Expor                    | aanvinkvakje | Indien aangevinkt is de  |
| tdocvanmapnaarbevoegdgez |              | kolom ddexportdocbevgez  |
|                          |              | zichtbaar in het         |
|                          |              | detailscherm van         |
|                          |              | omgevingskaart in het    |
|                          |              | blok Afhandeling. Zie    |
|                          |              | `Export DSO-Documenten   |
|                          |              | naar DMS van bevoegd     |
|                          |              | gezag </docs/probleemo   |
|                          |              | plossing/programmablokke |
|                          |              | n/export_documenten_bij_ |
|                          |              | dso_zaak_van_map_naar_dm |
|                          |              | s_bevoegd_gezxag.md>`__. |
+--------------------------+--------------+--------------------------+
|                          | Tekst        | Hierin kan een opsomming |
|                          |              | staan van OIN-nummers.   |
|                          |              | Indien een een           |
|                          |              | omgevingszaak een        |
|                          |              | DSO-zaak is en de        |
|                          |              | besluitdatum is gevuld   |
|                          |              | en de kolom              |
|                          |              | ddexportdocbevgez is     |
|                          |              | leeg en het OIN van het  |
|                          |              | bevoegd gezag komt voor  |
|                          |              | in deze *Tekst*, dan     |
|                          |              | komen deze               |
|                          |              | omgevingszaken in de     |
|                          |              | lijst achter de tegel    |
|                          |              | *Exportlijst docs naar   |
|                          |              | bev. gezag* op het       |
|                          |              | hoofdportaal.            |
+--------------------------+--------------+--------------------------+
|                          | Info         | De tekst in kolom *Info* |
|                          |              | wordt gebruikt voor de   |
|                          |              | koptekst in het          |
|                          |              | lijstscherm achter de    |
|                          |              | tegel *Exportlijst docs  |
|                          |              | naar bev. gezag*. Hierin |
|                          |              | kunnen de gemeentenamen  |
|                          |              | opgesomd worden die      |
|                          |              | horen bij de kolom       |
|                          |              | *Tekst*.                 |
+--------------------------+--------------+--------------------------+
|                          | Toelichting  | De map per zaak waar de  |
|                          |              | de te exporteren         |
|                          |              | documenten staan. Deze   |
|                          |              | moeten genoteerd worden  |
|                          |              | inclusief documentroot   |
|                          |              | dus bijvoorbeeld         |
|                          |              | ``\\N                    |
|                          |              | itro\\Wave\\Omgeving\%za |
|                          |              | akjaar%\%zaaknr%\DMS\``, |
|                          |              | waarbij de variabelen    |
|                          |              | ``%zaaknr%`` en          |
|                          |              | ``%zaakjaar%`` door      |
|                          |              | OpenWave on the fly      |
|                          |              | worden vervangen.        |
+--------------------------+--------------+--------------------------+
| ExportItp                | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | de export - itp datum    |
|                          |              | (tbomgvergunning.dditp)  |
|                          |              | met bijbehorende knop    |
|                          |              | zichtbaar in het         |
|                          |              | detailscherm van een     |
|                          |              | omgevingszaak. Zie       |
|                          |              | verdere uitleg bij       |
|                          |              | `Detailscherm            |
|                          |              | Om                       |
|                          |              | gevingszaak </docs/probl |
|                          |              | eemoplossing/portalen_en |
|                          |              | _moduleschermen/zaakport |
|                          |              | aal_omgeving/detailscher |
|                          |              | m_omgevingszaken.md>`__. |
+--------------------------+--------------+--------------------------+
| Extra_zaakinformatie     | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | in het detailscherm van  |
|                          |              | de zaak (omgeving en     |
|                          |              | handhaving) het blok     |
|                          |              | *Extra informatie*       |
|                          |              | zichtbaar. Hier vindt    |
|                          |              | men extra informatie     |
|                          |              | over de zaak zoals       |
|                          |              | bestuurlijk              |
|                          |              | gevoeligheid, domein van |
|                          |              | de zaak en kan aangeven  |
|                          |              | worden wat de            |
|                          |              | moeilijkheidscategorie   |
|                          |              | is indien het gaat om    |
|                          |              | een bezwaar/beroep zaak. |
+--------------------------+--------------+--------------------------+
| Hah                      | Aanvinkvakje | Indien aangevinkt dan    |
| AantCollegToetsZichtbaar |              | zijn drie kolommen       |
|                          |              | m.b.t. uitstaande en     |
|                          |              | geretourneerde           |
|                          |              | collegiale toetsen extra |
|                          |              | zichtbaar in de lijst    |
|                          |              | met openstaande          |
|                          |              | handhavingszaken:        |
|                          |              | dnaantalctuitstaand,     |
|                          |              | dnaantalctretour en      |
|                          |              | dnaantalctgezien.        |
+--------------------------+--------------+--------------------------+
| Handhaving uit inspectie | Aanvinkvakje | Indien aangevinkt en een |
| genereren                |              | inspectiekaart nog niet  |
|                          |              | is gekoppeld aan een     |
|                          |              | handhavingszaak en de    |
|                          |              | module ongelijk aan      |
|                          |              | Handhavingen is en de    |
|                          |              | inlogger lid is van een  |
|                          |              | rechtengroep die         |
|                          |              | insert-rechten heeft op  |
|                          |              | Handhavingen DAN is de   |
|                          |              | knop op het detailscherm |
|                          |              | van een inspectietraject |
|                          |              | toegankelijk waarmee van |
|                          |              | een traject een          |
|                          |              | handhavingszaak kan      |
|                          |              | worden gemaakt.          |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien de waarde 1 dan   |
|                          |              | is de actieve            |
|                          |              | behandelaar van de       |
|                          |              | nieuwe handhavingszaak   |
|                          |              | gelijk aan de ingestelde |
|                          |              | defaultbehandelaar van   |
|                          |              | de gekozen soort zaak.   |
|                          |              | Anders is de behandelaar |
|                          |              | gelijk aan de inlogger.  |
+--------------------------+--------------+--------------------------+
|                          | Getal2       | Indien de waarde 1 dan   |
|                          |              | wordt het                |
|                          |              | inspectietraject (en     |
|                          |              | bezoeken en              |
|                          |              | overtredingen)           |
|                          |              | gekopieerd naar de       |
|                          |              | nieuwe handhavingszaak.  |
|                          |              | Anders wordt het         |
|                          |              | bestaande                |
|                          |              | inspectietraject alleen  |
|                          |              | gekoppeld aan de nieuwe  |
|                          |              | handhavingszaak.         |
+--------------------------+--------------+--------------------------+
|                          | Tekst        | Indien *Getal2* = 1 en   |
|                          |              | de kolom *Tekst* bevat   |
|                          |              | als waarde een ID        |
|                          |              | (dnkey) van de           |
|                          |              | beheertabel              |
|                          |              | tbinspresultaat, dan     |
|                          |              | wordt na het dupliceren  |
|                          |              | het oude traject         |
|                          |              | afgesloten met de        |
|                          |              | verwijzing van deze      |
|                          |              | dnkey op de              |
|                          |              | systeemdatum.            |
+--------------------------+--------------+--------------------------+
|                          | Info         | Indien kolom *Info* van  |
|                          |              | de instelling *Sectie:   |
|                          |              | Programma Item:          |
|                          |              | Handhaving* uit          |
|                          |              | inspectie genereren de   |
|                          |              | waarde tbinsponrechtm    |
|                          |              | heeft, dan kan de        |
|                          |              | inlogger t.b.v. de       |
|                          |              | hoofdovertreding waarop  |
|                          |              | de handhavingszaak wordt |
|                          |              | aangemaakt alleen kiezen |
|                          |              | uit de overtredingen die |
|                          |              | in de tabel              |
|                          |              | tbinsponrechtm zijn      |
|                          |              | opgenomen bij het        |
|                          |              | betreffende              |
|                          |              | inspectietraject. Echter |
|                          |              | indien de waarde van de  |
|                          |              | kolom *Info*             |
|                          |              | t                        |
|                          |              | binsponrechtm_openstaand |
|                          |              | heeft dan kan de         |
|                          |              | inlogger alleen kiezen   |
|                          |              | uit de openstaande       |
|                          |              | overtredingen die in de  |
|                          |              | tabel tbinsponrechtm     |
|                          |              | zijn opgenomen bij het   |
|                          |              | betreffende              |
|                          |              | inspectietraject. Voor   |
|                          |              | beide gevallen geldt dat |
|                          |              | als die lijst leeg is    |
|                          |              | dan kan rechtstreeks     |
|                          |              | gekozen worden uit de    |
|                          |              | items van tabel          |
|                          |              | tbhandhovertreding       |
|                          |              | (beheerportaal           |
|                          |              | *Zaakbeheer*).           |
+--------------------------+--------------+--------------------------+
| Handhaving in groep      | Aanvinkvakje | Indien vanuit een        |
| genereren                |              | inspectietraject een     |
|                          |              | handhavingszaak wordt    |
|                          |              | gegenereerd, dan wordt   |
|                          |              | de nieuwe                |
|                          |              | handhavingszaak          |
|                          |              | verbonden in een groep   |
|                          |              | aan de basiszaak van het |
|                          |              | inspectietraject.        |
+--------------------------+--------------+--------------------------+
| Hoo                      | Aanvinkvakje | Indien aangevinkt dan    |
| fdprojlocatieAlleModules |              | wordt voor               |
|                          |              | Projectlocatie           |
|                          |              | omschrijving bij het     |
|                          |              | aanmaken van een nieuw   |
|                          |              | kadastraal               |
|                          |              | perceel/projectlocatie   |
|                          |              | (of het wijzigen van een |
|                          |              | bestaande) niet alleen   |
|                          |              | van die module de al     |
|                          |              | bestaande                |
|                          |              | Hoofdprojectlocaties     |
|                          |              | getoond, maar ook van de |
|                          |              | andere modules (mits de  |
|                          |              | zaak/inrichting op       |
|                          |              | hetzelfde perceeladres   |
|                          |              | afspeelt als de          |
|                          |              | zaak/inrichting waar men |
|                          |              | nieuwe projectlocatie    |
|                          |              | aanmaakt).               |
+--------------------------+--------------+--------------------------+
| Hor                      | Aanvinkvakje | Indien aangevinkt dan    |
| AantCollegToetsZichtbaar |              | zijn drie kolommen       |
|                          |              | m.b.t. uitstaande en     |
|                          |              | geretourneerde           |
|                          |              | collegiale toetsen extra |
|                          |              | zichtbaar in de lijst    |
|                          |              | met openstaande          |
|                          |              | horecazaken:             |
|                          |              | dnaantalctuitstaand,     |
|                          |              | dnaantalctretour en      |
|                          |              | dnaantalctgezien.        |
+--------------------------+--------------+--------------------------+
| Inf                      | Aanvinkvakje | Indien aangevinkt dan    |
| AantCollegToetsZichtbaar |              | zijn drie kolommen       |
|                          |              | m.b.t. uitstaande en     |
|                          |              | geretourneerde           |
|                          |              | collegiale toetsen extra |
|                          |              | zichtbaar in de lijst    |
|                          |              | met openstaande          |
|                          |              | infoaanvraagzaken:       |
|                          |              | dnaantalctuitstaand,     |
|                          |              | dnaantalctretour en      |
|                          |              | dnaantalctgezien.        |
+--------------------------+--------------+--------------------------+
| I                        | Aanvinkvakje | Standaard aangevinkt.    |
| nwerkingsdatumAutoVullen |              | Indien deze instelling   |
|                          |              | UIT wordt gezet, dan zal |
|                          |              | niet meer automatisch de |
|                          |              | in werking datum worden  |
|                          |              | gevuld bij het zetten    |
|                          |              | van de verzenddatum voor |
|                          |              | omgevingszaken van type  |
|                          |              | Regulier en Uitgebreid.  |
|                          |              | Deze instelling heeft    |
|                          |              | geen invloed op het      |
|                          |              | automatisch vullen van   |
|                          |              | de in werking datum bij  |
|                          |              | het zetten van de        |
|                          |              | verzenddatum voor de     |
|                          |              | overige modules          |
|                          |              | (handhaving, APV/overig  |
|                          |              | etc.).                   |
+--------------------------+--------------+--------------------------+
| JavaWIN1252              | Aanvinkvakje | Standaard uit. Vanaf     |
|                          |              | 1.29 is de OpenWave      |
|                          |              | database in karakterset  |
|                          |              | UTF-8. Dit betekent dat  |
|                          |              | de database een groter   |
|                          |              | aantal tekens aan kan    |
|                          |              | dan voorheen. Het        |
|                          |              | voorheen filteren van    |
|                          |              | tekens die niet konden   |
|                          |              | worden opgeslagen in de  |
|                          |              | OpenWave database is     |
|                          |              | daarom niet meer van     |
|                          |              | toepassing. Indien in    |
|                          |              | uitzonderlijke geval het |
|                          |              | toch gewenst is dat      |
|                          |              | OpenWave de oude         |
|                          |              | filtering toepast van    |
|                          |              | tekens op de             |
|                          |              | binnenkomende berichten  |
|                          |              | via JAVA, dan dient men  |
|                          |              | deze instelling aan te   |
|                          |              | vinken. Instelling aan   |
|                          |              | betekent dat alle tekens |
|                          |              | boven ASCII-waarde 127   |
|                          |              | in de binnenkomende      |
|                          |              | berichten worden omgezet |
|                          |              | (ë naar e etcetera). De  |
|                          |              | te verwerken             |
|                          |              | binnenkomende berichten  |
|                          |              | via JAVA waar het om     |
|                          |              | gaat is berichtverkeer   |
|                          |              | met BRP/NHR en Digitale  |
|                          |              | Checklisten.             |
+--------------------------+--------------+--------------------------+
| Kaa                      | Tekst        | Deze waarde wordt        |
| rtCsscolornameInrichting |              | gebruikt voor een vlak   |
|                          |              | op de interne kaart voor |
|                          |              | het grondgebied van een  |
|                          |              | inrichting. Default =    |
|                          |              | *Salmon*. De kleur moet  |
|                          |              | een CSS colorname zijn:  |
|                          |              | zie                      |
|                          |              | http://www.w3schools.c   |
|                          |              | om/cssref/css_colors.asp |
|                          |              | .                        |
+--------------------------+--------------+--------------------------+
| Ka                       | Tekst        | Deze waarde wordt        |
| artCsscolornameHoofdzaak |              | gebruikt voor een vlak   |
|                          |              | op de interne kaart voor |
|                          |              | het grondgebied van een  |
|                          |              | hoofdzaak. Default =     |
|                          |              | *Salmon*. De kleur moet  |
|                          |              | een CSS colorname zijn:  |
|                          |              | zie                      |
|                          |              | http://www.w3schools.c   |
|                          |              | om/cssref/css_colors.asp |
|                          |              | .                        |
+--------------------------+--------------+--------------------------+
| KaartCsscolornamePerceel | Tekst        | Deze waarde wordt        |
|                          |              | gebruikt voor een vlak   |
|                          |              | of marker op de interne  |
|                          |              | kaart om een             |
|                          |              | perceeladres te duiden.  |
|                          |              | Default = *Red*. De      |
|                          |              | kleur moet een CSS       |
|                          |              | colorname zijn: zie      |
|                          |              | http://www.w3schools.c   |
|                          |              | om/cssref/css_colors.asp |
|                          |              | .                        |
+--------------------------+--------------+--------------------------+
| KadastrgemSortering      | Getal1       | Indien de waarde 1 dan   |
|                          |              | worden de dropdowns voor |
|                          |              | het kiezen van een       |
|                          |              | kadastrale gemeente      |
|                          |              | gesorteerd op            |
|                          |              | gemeentenaam en in alle  |
|                          |              | andere gevallen op       |
|                          |              | kadastrale gemeente      |
|                          |              | code.                    |
+--------------------------+--------------+--------------------------+
| KopieerHahKolommen       | Tekst        | De kolom *Tekst* kan     |
|                          |              | gevuld worden kolomnamen |
|                          |              | uit tbhandhavingen die   |
|                          |              | gebruikt worden bij het  |
|                          |              | kopiëren van een         |
|                          |              | handhavingzaak (vanuit   |
|                          |              | processtap). De          |
|                          |              | kolomnamen moeten        |
|                          |              | gescheiden zijn door een |
|                          |              | puntkomma (zonder        |
|                          |              | spaties). De kolomnamen  |
|                          |              | moeten ONGELIJK zijn aan |
|                          |              | dnkey,                   |
|                          |              | dnkeygroepvergunning en  |
|                          |              | dnkeysoorthhzaak,        |
|                          |              | dnkeyperceeladressen,    |
|                          |              | dvomsbouwerk,            |
|                          |              | ddverzoekdatum ( =       |
|                          |              | startdatum in openwave), |
|                          |              | dvaanschrijfnr (=        |
|                          |              | zaakcode in OpenWave) ,  |
|                          |              | ddfataledatum,           |
|                          |              | dnkeyoinbevgez.          |
+--------------------------+--------------+--------------------------+
| KopieerOmgKolommen       | Tekst        | De kolom *Tekst* kan     |
|                          |              | gevuld worden kolomnamen |
|                          |              | uit tbomgvergunning die  |
|                          |              | gebruikt worden bij het  |
|                          |              | kopiëren van een         |
|                          |              | omgevingszaak (vanuit    |
|                          |              | processtap). De          |
|                          |              | kolomnamen moeten        |
|                          |              | gescheiden zijn door een |
|                          |              | puntkomma (zonder        |
|                          |              | spaties). De kolomnamen  |
|                          |              | moeten ONGELIJK zijn aan |
|                          |              | dnkey,                   |
|                          |              | dnkeygroepvergunning en  |
|                          |              | dnkeysoortomgverg,       |
|                          |              | dnkeyperceeladressen,    |
|                          |              | dvaanvraagnaam,          |
|                          |              | ddaanvraag, dvzaakcode,  |
|                          |              | ddfataledatum.           |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien een zaak wordt    |
|                          |              | gekopieerd waarbij de    |
|                          |              | kolom                    |
|                          |              | dvlvoaanvraagnummer is   |
|                          |              | opgenomen in kolom       |
|                          |              | *Tekst* dan redeneert    |
|                          |              | het programma als volgt  |
|                          |              | bij het maken van de     |
|                          |              | nieuwe zaak: Indien      |
|                          |              | *Getal1* van die         |
|                          |              | instelling de waarde 1   |
|                          |              | heeft, dan wordt het     |
|                          |              | OLO/DSO-nummer           |
|                          |              | (dvlvoaanvraagnr) van de |
|                          |              | zaak die gekopieerd      |
|                          |              | wordt voorzien van de    |
|                          |              | postfix underscore + 1   |
|                          |              | (indien \_1 al bestaat   |
|                          |              | dan_2 en zo verder met   |
|                          |              | maximum van 100). Anders |
|                          |              | (dus *Getal1* is         |
|                          |              | ongelijk aan 1) dan      |
|                          |              | wordt de nieuwe          |
|                          |              | gekopieerde kaart        |
|                          |              | voorzien van die         |
|                          |              | postfix. Dit laatste is  |
|                          |              | nodig om de uniciteit    |
|                          |              | van de kolom             |
|                          |              | dvlvoaanvraagnr te       |
|                          |              | behouden in verband met  |
|                          |              | opvangen van aanvullende |
|                          |              | documenten van het       |
|                          |              | OLO/DSO. Wanneer het de  |
|                          |              | bedoeling is dat         |
|                          |              | aanvullende              |
|                          |              | (OLO)-documenten bij de  |
|                          |              | oorspronkelijke zaak     |
|                          |              | terechtkomen dan moet    |
|                          |              | *Getal1* leeg blijven.   |
|                          |              | Indien het de bedoeling  |
|                          |              | is dat de aanvullende    |
|                          |              | documenten bij de nieuwe |
|                          |              | zaak terechtkomen dan    |
|                          |              | moet *Getal1* de waarde  |
|                          |              | 1 hebben.                |
+--------------------------+--------------+--------------------------+
| KoppelZaa                | Aanvinkvakje | Indien aangevinkt, dan   |
| kInrichtingAanHandhaving |              | zal bij het genereren    |
|                          |              | van een handhavingzaak   |
|                          |              | vanuit een               |
|                          |              | inspectietraject,        |
|                          |              | hangende aan een zaak    |
|                          |              | (module W,H,C,B of O),   |
|                          |              | een gekoppelde           |
|                          |              | inrichting opgenomen     |
|                          |              | worden in de nieuwe      |
|                          |              | handhavingzaak.          |
+--------------------------+--------------+--------------------------+
| NieuweInrichtin          | Aanvinkvakje | Indien aangevinkt zal na |
| gGaNaarInrichtingPortaal |              | het handmatig aanmaken   |
|                          |              | van een nieuwe           |
|                          |              | inrichting automatisch   |
|                          |              | door genavigeerd worden  |
|                          |              | naar het betreffende     |
|                          |              | inrichtingsportaal.      |
+--------------------------+--------------+--------------------------+
| NieuweZaakBijInrichting  | Aanvinkvakje | Indien aangevinkt en     |
|                          |              | rechten inlogger OK, is  |
|                          |              | de wizard voor het       |
|                          |              | aanmaken van een nieuwe, |
|                          |              | aan de inrichting        |
|                          |              | gekoppelde omgevingszaak |
|                          |              | benaderbaar vanuit het   |
|                          |              | detailscherm van een     |
|                          |              | inrichting (`zie         |
|                          |              | Dokuwiki </docs/prob     |
|                          |              | leemoplossing/portalen_e |
|                          |              | n_moduleschermen/inricht |
|                          |              | ingen_portaal/detailsche |
|                          |              | rm_inrichtingen.md>`__). |
+--------------------------+--------------+--------------------------+
| NieuweZaakGeenBAGSync    | Aanvinkvakje | Indien aangevinkt zal    |
|                          |              | bij het handmatig        |
|                          |              | aanmaken van een nieuwe  |
|                          |              | zaak of inrichting,      |
|                          |              | gekeken worden of het    |
|                          |              | opgegeven huisnummer     |
|                          |              | voorkomt in het veld     |
|                          |              | *Tekst*. Zo ja, dan      |
|                          |              | wordt er geen BAG        |
|                          |              | synchronisatie           |
|                          |              | uitgevoerd. Zo nee, dan  |
|                          |              | wordt er wel             |
|                          |              | gesynchroniseerd met de  |
|                          |              | BAG.                     |
+--------------------------+--------------+--------------------------+
|                          | Tekst        | Huisnummers waarvoor BAG |
|                          |              | synchronisatie           |
|                          |              | overgeslagen moet worden |
|                          |              | zijn hier op te geven    |
|                          |              | gescheiden met een       |
|                          |              | puntkomma. Bijvoorbeeld  |
|                          |              | als voor huisnummers 0   |
|                          |              | en 9999 geen BAG         |
|                          |              | synchronisatie plaats    |
|                          |              | moet vinden dan is de    |
|                          |              | waarde van tekst:        |
|                          |              | 0;9999.                  |
+--------------------------+--------------+--------------------------+
| Ni                       | Aanvinkvakje | Indien aangevinkt zal    |
| euweZaakExtraContactInfo |              | bij het handmatig        |
|                          |              | aanmaken van een nieuwe  |
|                          |              | zaak indien er een       |
|                          |              | nieuwe contact           |
|                          |              | gedefinieerd wordt, de   |
|                          |              | volgende extra gegevens  |
|                          |              | voor het contactpersoon  |
|                          |              | opgegeven kunnen worden: |
|                          |              | voorletters,             |
|                          |              | voorvoegsel, geslacht,   |
|                          |              | telefoonnummer en        |
|                          |              | e-mailadres.             |
+--------------------------+--------------+--------------------------+
| Nie                      | Aanvinkvakje | Indien aangevinkt zal na |
| uweZaakGaNaarZaakPortaal |              | het handmatig aanmaken   |
|                          |              | van een nieuwe zaak      |
|                          |              | automatisch door         |
|                          |              | genavigeerd worden naar  |
|                          |              | het betreffende          |
|                          |              | zaakportaal, tenzij de   |
|                          |              | zaak is aangemaakt       |
|                          |              | vanuit een processtap    |
|                          |              | (dan keert de gebruiker  |
|                          |              | terug naar het proces).  |
+--------------------------+--------------+--------------------------+
| N                        | Aanvinkvakje | Indien aangevinkt zal    |
| ieuweZaakKiesBehandelaar |              | bij het handmatig        |
|                          |              | aanmaken van een nieuwe  |
|                          |              | zaak voor de             |
|                          |              | dossierbehandelaar een   |
|                          |              | keuze gemaakt kunnen     |
|                          |              | worden uit de            |
|                          |              | medewerkerslijst (met    |
|                          |              | default de waarde zoals  |
|                          |              | ingesteld bij het        |
|                          |              | zaaktype). Niet          |
|                          |              | aangevinkt berekent dat  |
|                          |              | de dossierbehandelaar    |
|                          |              | gelijk wordt aan die van |
|                          |              | de inlogger.             |
+--------------------------+--------------+--------------------------+
| Nieuwe                   | Aanvinkvakje | Indien aangevinkt en     |
| ZaakUitvoerendeInstantie |              | kolom *Tekst* is gevuld  |
|                          |              | met een geldig           |
|                          |              | OIN-nummer dan zal bij   |
|                          |              | het handmatig aanmaken   |
|                          |              | van een nieuwe           |
|                          |              | Omgevingszaak voor deze  |
|                          |              | zaak de Uitvoerende      |
|                          |              | instantie gevuld worden. |
+--------------------------+--------------+--------------------------+
|                          | Tekst        | OIN-nummer dat bij het   |
|                          |              | aanmaken van een nieuwe  |
|                          |              | Omgevingszaak gebruikt   |
|                          |              | zal worden voor het      |
|                          |              | zetten van de            |
|                          |              | Uitvoerende instantie    |
|                          |              | voor deze zaak.          |
+--------------------------+--------------+--------------------------+
| NoReplyEmailAdres        | Tekst        | Algemeen email adres     |
|                          |              | voor no reply berichten. |
|                          |              | Bij compartiment kijkt   |
|                          |              | OpenWave naar            |
|                          |              | tbcompartim              |
|                          |              | ent.dvNoReplyEmailAdres. |
+--------------------------+--------------+--------------------------+
| Omg                      | Aanvinkvakje | Indien aangevinkt dan    |
| AantCollegToetsZichtbaar |              | zijn drie kolommen       |
|                          |              | m.b.t. uitstaande en     |
|                          |              | geretourneerde           |
|                          |              | collegiale toetsen extra |
|                          |              | zichtbaar in de lijst    |
|                          |              | met openstaande          |
|                          |              | omgevingszaken:          |
|                          |              | dnaantalctuitstaand,     |
|                          |              | dnaantalctretour en      |
|                          |              | dnaantalctgezien.        |
+--------------------------+--------------+--------------------------+
| OmgAc                    | Aanvinkvakje | Indien aangevinkt dan    |
| tiviteitLocatieOvernemen |              | zal bij het aanmaken van |
|                          |              | een nieuwe omgevingszaak |
|                          |              | via een vervolgactie     |
|                          |              | (actie achter            |
|                          |              | processtap) bij een      |
|                          |              | omgevingszaak, de        |
|                          |              | onderdelen/activiteiten  |
|                          |              | en projectlocaties van   |
|                          |              | de originele             |
|                          |              | omgevingszaak worden     |
|                          |              | overgenomen bij de nieuw |
|                          |              | aangemaakte zaak.        |
+--------------------------+--------------+--------------------------+
| OmgDMScodeAlsGroepnaam   | Aanvinkvakje | Indien aangevinkt wordt  |
|                          |              | bij het aanmaken van de  |
|                          |              | groep niet de            |
|                          |              | zaakomschrijving maar    |
|                          |              | het DMS-nummer van de    |
|                          |              | originele zaak als       |
|                          |              | waarde gepakt.           |
+--------------------------+--------------+--------------------------+
| Openstaande              | Aanvinkvakje | Indien aangevinkt dan    |
| overtredingen            |              | zullen (bij het          |
|                          |              | genereren van een        |
|                          |              | handhavingszaak vanuit   |
|                          |              | een inspectietraject)    |
|                          |              | alleen de openstaande    |
|                          |              | overtredingen worden     |
|                          |              | meegenomen naar de       |
|                          |              | nieuwe handhavingszaak.  |
|                          |              | Dit wil zeggen dat bij   |
|                          |              | deze overtredingen het   |
|                          |              | veld *Datum opgelost*    |
|                          |              | leeg is of groter dan    |
|                          |              | vandaag.                 |
+--------------------------+--------------+--------------------------+
| Omg                      | Aanvinkvakje | Indien aangevinkt is in  |
| DvFatalePeriodeZichtbaar |              | het detailscherm van de  |
|                          |              | omgevingszaak in het     |
|                          |              | blok afhandeling de      |
|                          |              | kolom Ber.wijze          |
|                          |              | fat.termijn              |
|                          |              | (dnkeyfataletermijnen)   |
|                          |              | zichtbaar, waarmee voor  |
|                          |              | die zaak de default      |
|                          |              | fatale periode           |
|                          |              | (dnfataleperiode) uit    |
|                          |              | tbsoortomgverg kan       |
|                          |              | worden overschreven met  |
|                          |              | een keuze uit de tabel   |
|                          |              | tbfataletermijnen        |
|                          |              | (gekoppeld aan           |
|                          |              | bettreffende zaaktype).  |
+--------------------------+--------------+--------------------------+
| Opsch                    | Getal1       | Het aantal dagen dat     |
| onenmissingconfiguration |              | kaarten in de tabel      |
|                          |              | tbmissingconfiguration   |
|                          |              | bewaard moeten blijven   |
|                          |              | (default 30).            |
+--------------------------+--------------+--------------------------+
| RapportCSVKolomOmhuld    | Tekst        | Hier geeft men het       |
|                          |              | karakter/teken op        |
|                          |              | waarmee bij uitdraai van |
|                          |              | een rapport naar .csv    |
|                          |              | (momenteel alleen van    |
|                          |              | toepassing bij de        |
|                          |              | FisExport mits zelf      |
|                          |              | ingesteld), de waarde in |
|                          |              | een kolom omhult moeten  |
|                          |              | worden. Let op: mag niet |
|                          |              | hetzelfde teken zijn als |
|                          |              | bij instelling           |
|                          |              | R                        |
|                          |              | apportCSVKolomScheiding! |
+--------------------------+--------------+--------------------------+
| RapportCSVKolomScheiding | Tekst        | Hier geeft men het       |
|                          |              | karakter/teken op        |
|                          |              | waarmee bij uitdraai van |
|                          |              | een rapport naar .csv    |
|                          |              | (momenteel alleen van    |
|                          |              | toepassing bij de        |
|                          |              | FisExport mits zelf      |
|                          |              | ingesteld), de kolommen  |
|                          |              | gescheiden moeten        |
|                          |              | worden. Let op: mag niet |
|                          |              | hetzelfde teken zijn als |
|                          |              | bij instelling           |
|                          |              | RapportCSVKolomOmhuld!   |
+--------------------------+--------------+--------------------------+
| Roeb                     | Aanvinkvakje | Indien aangevinkt wordt  |
|                          |              | het blok *ROEB* (waarin  |
|                          |              | berekening vastgestelde  |
|                          |              | kosten wordt geregeld)   |
|                          |              | zichtbaar in het         |
|                          |              | detailscherm van een     |
|                          |              | onderdeel/activiteit     |
|                          |              | (tbtoestemmingen) bij    |
|                          |              | een omgevingszaak.       |
|                          |              | Indien de zaak speelt in |
|                          |              | een compartiment, dan    |
|                          |              | wordt i.p.v. naar deze   |
|                          |              | instelling, gekeken naar |
|                          |              | de kolom dlroeb van dat  |
|                          |              | compartiment.            |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien de waarde 1 dan   |
|                          |              | krijgt de berekende      |
|                          |              | roebkostenkolom          |
|                          |              | (vwfrmtoestem            |
|                          |              | mingen.dflegesvastgroeb) |
|                          |              | voor de vaststelling van |
|                          |              | het uitgangsbedrag bij   |
|                          |              | de legesberekening       |
|                          |              | voorrang boven de        |
|                          |              | handmatig ingestelde     |
|                          |              | kolom dflegesvastgbasis  |
+--------------------------+--------------+--------------------------+
| Samen                    | Aanvinkvakje | Indien aangevinkt dan    |
| voegenTabellenMetLetters |              | verwacht het programma   |
|                          |              | bij het samenvoegen van  |
|                          |              | tabeldata in een         |
|                          |              | sjabloon geen coderingen |
|                          |              | met cijfers, maar met    |
|                          |              | letters. Dus niet {1} en |
|                          |              | {2}, maar {a} en {b}.    |
|                          |              | Dit kan noodzakelijk     |
|                          |              | zijn i.v.m. de           |
|                          |              | verwerking van Open      |
|                          |              | Document Format files.   |
+--------------------------+--------------+--------------------------+
| Slu                      | Aanvinkvakje | Indien aangevinkt en er  |
| itOpenInspbijSluitenZaak |              | zijn openstaande         |
|                          |              | inspectietrajecten en    |
|                          |              | inspecties zijn geen     |
|                          |              | externe zaken (DMS) dan  |
|                          |              | zal bij de zaak sluiten  |
|                          |              | via wizard *SluitZaak*   |
|                          |              | gevraagd worden om de    |
|                          |              | openstaande              |
|                          |              | inspectietrajecten (en   |
|                          |              | onderliggende bezoeken   |
|                          |              | en overtredingen) af te  |
|                          |              | sluiten.                 |
+--------------------------+--------------+--------------------------+
| Slui                     | Aanvinkvakje | Indien aangevinkt en er  |
| tProductenbijSluitenZaak |              | zijn openstaande         |
|                          |              | producten dan zal bij    |
|                          |              | het sluiten van de zaak  |
|                          |              | via wizard *SluitZaak*   |
|                          |              | gevraagd worden om de    |
|                          |              | openstaande producten te |
|                          |              | voorzien van een         |
|                          |              | opleverdatum.            |
+--------------------------+--------------+--------------------------+
| Sluitzaakresultbekend    | Aanvinkvakje | Indien aangevinkt en het |
|                          |              | aard besluit is al       |
|                          |              | bekend bij de zaak       |
|                          |              | (bijv. via processtap)   |
|                          |              | dan zal de wizard        |
|                          |              | *SluitZaak* niet         |
|                          |              | toestaan dat het aard    |
|                          |              | besluit overschreven     |
|                          |              | wordt.                   |
+--------------------------+--------------+--------------------------+
| Toonkaart                | Getal2       | Het zoomlevel waarmee de |
|                          |              | interne OpenWave kaart   |
|                          |              | opstart. Indien een      |
|                          |              | externe kaartviewer      |
|                          |              | wordt gebruikt is dit    |
|                          |              | een verplicht veld.      |
+--------------------------+--------------+--------------------------+
|                          | Info         | Indien deze kolom een    |
|                          |              | gevulde waarde heeft dan |
|                          |              | beschouwt OpenWave die   |
|                          |              | gevulde waarde als een   |
|                          |              | URL van een externe      |
|                          |              | kaartviewer die geopend  |
|                          |              | moet worden als de       |
|                          |              | gebruiker op de *Toon    |
|                          |              | kaart* knop klikt vanuit |
|                          |              | een detailscherm of een  |
|                          |              | portal. Wanneer die      |
|                          |              | kolom *Info* niet is     |
|                          |              | gevuld, dan wordt de     |
|                          |              | standaardkaart (interne  |
|                          |              | kaartviewer) van         |
|                          |              | OpenWave aangeroepen. In |
|                          |              | die URL-string zal       |
|                          |              | OpenWave eerst de        |
|                          |              | variabelen: %x%          |
|                          |              | vervangen door de        |
|                          |              | x-coördinaat van het     |
|                          |              | bijbehorende locatie     |
|                          |              | adres, %y% vervangen     |
|                          |              | door de y-coördinaat van |
|                          |              | het bijbehorende locatie |
|                          |              | adres, %zoom% vervangen  |
|                          |              | door *Getal2*.           |
+--------------------------+--------------+--------------------------+
|                          | Aanvinkvakje | Indien aangevinkt kan de |
|                          |              | interne of externe kaart |
|                          |              | worden gebruikt met de   |
|                          |              | *Toon kaart* knop vanuit |
|                          |              | een detailscherm of een  |
|                          |              | portal.                  |
+--------------------------+--------------+--------------------------+
| VlakNietOpZaakniveau     | Aanvinvakje  | Indien aangevinkt dan is |
|                          |              | het blok met het         |
|                          |              | getekende vlak           |
|                          |              | (dvgmlpolygoon) op de    |
|                          |              | detailschermen van       |
|                          |              | omgeving en handhaving   |
|                          |              | niet zichtbaar. Ook is   |
|                          |              | de optie *teken vlak* in |
|                          |              | het menu op deze         |
|                          |              | detailschermen dan       |
|                          |              | uitgeschakeld.           |
+--------------------------+--------------+--------------------------+
| ZaaktypeW                | Aanvinkvakje | Indien aangevinkt dan    |
| ijzigenProcessenWijzigen |              | zal in het detailscherm  |
|                          |              | van Omgeving-,           |
|                          |              | Handhaving- en           |
|                          |              | APV/Overige zaken het    |
|                          |              | wijzigen van zaaktype    |
|                          |              | verlopen via een Wizard  |
|                          |              | (i.p.v. bekende          |
|                          |              | keuzelijst). Via deze    |
|                          |              | wizard zijn naast het    |
|                          |              | wijzigen van het         |
|                          |              | zaaktype, optioneel ook  |
|                          |              | de processen te          |
|                          |              | wijzigen. Indien         |
|                          |              | hiervoor gekozen wordt   |
|                          |              | zullen de automatisch    |
|                          |              | aan te maken processen   |
|                          |              | bij het gekozen zaaktype |
|                          |              | de huidige processen bij |
|                          |              | de zaak vervangen.       |
+--------------------------+--------------+--------------------------+
| ZaaktypeWijz             | Aanvinkvakje | Indien aangevinkt dan    |
| igenProductenVerwijderen |              | zal bij het wijzigen van |
|                          |              | het zaaktype de (evt.)   |
|                          |              | gekoppelde product(en)   |
|                          |              | verwijderd worden. Dit   |
|                          |              | geldt voor zowel de      |
|                          |              | situatie maximaal 1      |
|                          |              | product per zaak (bijv.  |
|                          |              | tbom                     |
|                          |              | gvergunning.dnkeyproduct |
|                          |              | en dnkeysubproduct       |
|                          |              | worden leeggemaakt) als  |
|                          |              | meerdere producten per   |
|                          |              | zaak (rijen in           |
|                          |              | tbzaakproducten voor de  |
|                          |              | zaak worden verwijderd). |
|                          |              | Dit gebeurd zonder       |
|                          |              | melding/waarschuwing     |
|                          |              | TENZIJ het zaaktype      |
|                          |              | gewijzigd wordt via een  |
|                          |              | Wizard (zie instelling   |
|                          |              | *ZaaktypeWijz            |
|                          |              | igenProcessenWijzigen*). |
|                          |              | In dat geval zal er      |
|                          |              | gevraagd worden aan de   |
|                          |              | gebruiker of de          |
|                          |              | product(en) verwijderd   |
|                          |              | moeten worden bij het    |
|                          |              | wijzigen van het         |
|                          |              | zaaktype.                |
+--------------------------+--------------+--------------------------+
