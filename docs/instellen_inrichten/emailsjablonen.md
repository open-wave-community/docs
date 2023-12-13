# Emailsjablonen

Portaal beheerportaal-nieuw. Tegel *Emailsjablonen*.

Screenidentifiers:

  - MDLC_getEmailGroupList.xml (tbemailsoorten)
  - MDDC_getEmailGroupDetail.xml (tbemailsoorten)
  - MDLC_getEmailParamsList.xml (tbemailparameters)
  - MDDC_getEmailSjabloonDetail.xml (vwfrmemailsjabloon)
  - MDLC_getEmailSjabloonList.xml (vwfrmemailsjabloon)
  - MDDC_getEmailParamsDetail.xml (tbemailparameters)

Met deze tegel kunnen mailsjablonen worden gedefinieerd. In deze mailsjablonen kunnen merge-coderingen zijn opgenomen die dynamisch worden gevuld met gegevens uit de database. De uiteindelijk gecreëerde email zal opgeslagen kunnen worden als een platte tekst file (.txt). Een sjabloon wordt opgeroepen met de menu-optie *Creëer email* op het detailscherm van een omgevingszaak OF op het detailscherm van een inspectiebezoek (alle modules), mits de gebruiker documentcreatie-rechten heeft voor de betreffende module.

Voor de sjabloondefinitie moet de inlogger beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99.

Alle kolommen en knoppen op de sjabloonschermen zijn dan toegankelijk.

## Sjabloongroepen

De sjablonen kunnen worden ingedeeld in groepen, waarbij een groep toegekend kan worden aan één of meer modules door middel van hun moduleletters. Daar waar de gebruiker een menuoptie *Creëer email* tot zijn beschikking heeft is dus deze moduleletter bepalend voor de inhoud van de radiobuttonlist: kies sjabloonsoort.

  - W: Omgeving
  - O: APV/Overig
  - H: Handhaving
  - I: Info
  - E: Inrichtingen/Vestigingen/Objectregistratie
  - V: Milieu/gebruik (gedeeltelijk pre-wabo)
  - C: Horeca
  - B: Bouw/Sloop (pre-wabo)

Vervallen sjabloongroepen zijn niet zichtbaar voor de gebruiker bij de wizard *MaakEmail*.
Let op: de sjablonen zijn te maken voor alle modules. Voor alsnog is het creëren van mails alleen mogelijk bij inspectiebezoeken, collegiale toetsen en adviezen (alle modules waar deze zijn aan te maken) en via het detailscherm van een omgevings-, en handhavingszaak. In de toekomst zal het creëren van mails mogelijk zijn op alle plekken waar nu ook creëer document mogelijk is.

### Sjabloondefinitie (emailsjablonenlijst)

Per sjabloongroep kunnen emailsjablonen verwijderd (inclusief parameters), nieuw aangemaakt en gekopieerd worden. Bij het maken van een kopie worden de parameters mee gekopieerd.

### Sjabloondefinitie (detailscherm)

#### Triggers linksonder

  - Met de knop **controleer SQL-statements** worden de gevulde query-kolommen gevalideerd. De betreffende kolomnamen worden zichtbaar met een groen bolletje indien OK en met een rood bolletje indien het statement niet valide is.

#### Triggers rechtsonder

  - Met het aanvinkvakje (default aangevinkt) vervallen kaarten zichtbaar, kan de lijst gefilterd worden op alleen niet-vervallen sjablonen.

### Kolommen

  - De kolom **ID** (dnkey) geeft de automatisch gegenereerde primary key weer van het sjabloon in de tabel tbemailsjabloon.
  - **Naam/beschrijving** (dvomschrijving). Vrij in te voeren naam voor het sjabloon, zoals die voor gebruikers zichtbaar worden in een lijst, wanneer de gebruiker de wizard *MaakEmail* aanroept.
  - **Is sjabloon voor standaardmail naar adviesinstantie?**. Indien aangevinkt dan zal dit sjabloon gebruikt worden bij de standaard email naar adviesinstantie bij een advies. Kan alleen aangevinkt worden als veld **Benaderbaar vanuit tabel** waarde *tbadviezen* heeft. Ook mag er per module maar 1 adviessjabloon zijn. Indien er al een sjabloon is met dit vinkje aan EN zelfde waarde voor veld *Voor module*, dan zal bij aanvinken in ander sjabloon het vinkje automatisch uitgezet worden bij het eerste sjabloon. Indien men gebruik wilt maken van sjablonen voor de standaard email aan adviesinstanties zal men dus per module een sjabloon moeten maken. Indien er geen sjabloon is met vinkje aan dan zal het programma terugvallen op de configuratie instelling voor standaard mail aan adviesinstantie.
  - **Is sjabloon voor standaardmail naar collegiale toetser?**. Dit vinkje is alleen zichtbaar wanneer de instelling Sectie: Documenten, Item: CtMail aan staat. Indien aangevinkt dan zal dit sjabloon gebruikt worden bij de eenmalige email naar de collegiale toetser bij een geregistreerd document. Hiervoor moet het veld **Benaderbaar vanuit tabel** de waarde *tbcorrespcollegtoets* hebben. Ook mag er per module maar 1 sjabloon voor de mail naar collegiale toetser zijn.
  - **Compartiment** (dnkeycompartiment). Indien het sjabloon hier wordt toegekend aan een [compartiment](/instellen_inrichten/compartimenten.md) kan dit sjabloon alleen worden gebruikt door iemand die lid is van dat compartiment. Omgekeerd: de inloggers die geen lid zijn van een compartiment zien enkel sjablonen die ook niet zijn toegekend aan een compartiment.
  - **Bijlagen toevoegen?** (dlbijlagesregdoc). Indien aangevinkt dan zal in de wizard die het maken van de uitgaande email regelt een extra pagina worden toegevoegd die de gebruiker laat kiezen uit één of meer geregistreerde documenten, die vervolgens als bijlagen aan de email worden toegevoegd. De lijst van geregistreerde documenten wordt beperkt tot de documenten die als plaats (S)erver hebben: dat wil zeggen dat zij NIET op dat moment lokaal bewerkt worden.
  - Met het **Volgordenummer** kan de volgorde van de sjabloonnamen bepaald worden zoals die voor gebruikers zichtbaar worden in een lijst, wanneer de gebruiker de wizard *MaakEmail* aanroept.
  - **Vervaldatum**. Vervallen mailsjablonen zijn niet zichtbaar voor de gebruiker bij de wizard *Maakemail*.
  - **Sjabloongroep**. Naam van de sjabloongroep waartoe sjabloon behoort. Sjabloongroep kan hier gewijzigd worden om het sjabloon aan een andere bestaande sjabloongroep te hangen.
  - **Contactpersoon verplicht**. Deze is altijd aangevinkt. Immers een email zal altijd aan iemand gericht zijn en verstuurd moeten worden. Bij het creëren van de email zal er een keuze gemaakt moeten worden uit de contactpersonen gekoppeld aan de zaak/inrichting. Er kan alleen gekozen worden uit contactpersonen waarvan een mailadres bekend is. De dnkey van deze contactpersoon wordt gebruikt om de variabele :keyadres uit de SQL-statements te vullen.
  - **Voor module**. Lijkt dubbelop i.v.m. *benaderbaar vanuit tabelnaam*, maar zowel voor klachten, adviezen, collegiale toetsen, en inspecties en bezwaar/beroep geldt dat zij vanuit verschillende modules oproepbaar zijn. Dus als een document wordt gebruikt bij een inspectie waarbij gegevens uit de bijbehorende omgevingszaak worden gebruikt dan is de tabelnaam: tbinspecties en de moduleletter: W.

 Mogelijk zijn W: Omgeving O: APV/Overig, H: Handhaving, I: Info, E: Milieu/gebruik (gedeeltelijk pre-wabo) + Inrichtingen/Vestigingen/Objectregistratie, C: Horeca en B: Bouw/Sloop (pre-wabo).

  - **Te genereren documentnaam** (dvtemplate). Bij het samenvoegen in de wizard *MaakEmail* van sjabloon en databasevelden wordt een email samengesteld. Indien aangegeven is dat de email moet worden opgeslagen wordt er een nieuw document gecreëerd (.txt). Hier kan de gewenste documentnaam worden ingevuld (zonder extensie). Indien deze kolom is gevuld dan geldt het volgende: de nieuwe documentnaam is de waarde van deze kolom met als extensie .txt De variabelen:
    -  %date% in dvtemplate wordt door de applicatie vervangen door 'yyyymmdd' van de systeemdatum
    -  %login% in dvtemplate wordt vervangen door de medewerkerscode van de inlogger.
    -  %hoofdzaaknr% in dvtemplate wordt vervangen door de wavezaakcode van de hoofdzaak c.q. inrichting
    -  %deelzaaknr% in dvtemplate wordt vervangen door de wavezaakcode van de deelzaak (dus advies, inspectie of bezwaar/beroep)
    -  %hoofddmsnr% in dvtemplate wordt vervangen door de externe zaak/dmscode (dvintzaakcode) van de hoofdzaak c.q. inrichting
    -  %deeldmsnr% in dvtemplate wordt vervangen door de externe zaak/dmscode (dvintzaakcode) van de de deelzaak (dus advies, inspectie of bezwaar/beroep)
    -  %teller% in dvtemplate wordt vervangen door uniek briefnummer dat gegenereerd wordt op moment van aanmaken van brief mits de instelling *Sectie: Documenten en Item: WaveBriefNummer* bestaat en is aangevinkt
    - %adres% in dvtemplate wordt vervangen door het adres + de woonplaats van de hoofdzaak/inrichting
    -  %ExtDocIdent% (hoofdlettergevoelig!) in dvtemplate wordt vervangen door de externe documentidentifier die verkregen wordt door een Stuf Zaak/DMS genereerdocumentidentificatie-bericht. Alleen van toepassing indien automatische opslag in een DMS via Stuf Zaak/DMS. Wanneer OpenWave geen externe documentidentifier kan bemachtigen, blijft de tag %ExtDocIdent% staan in de documentnaam. Indien kolom dvtemplate leeg is dan geldt als te genereren documentnaam de waarde van de naam van het sjabloon.
  - **Documenttype DMS**. Deze kolom is noodzakelijk indien het te genereren document direct wordt doorgezet met een zaak/DMS koppeling (*autom upload (dlautoupload)* is aangevinkt EN indien GEEN compartiment dan de kolom *Tekst* van instelling *Sectie: KoppelingDOCNAARDMS* en *Item: Methode* heeft de waarde *StUF-ZAKEN 310*, indien WEL compartiment dan *Documenten opslag in DMS* aangevinkt en veld *DMS-Methode* heeft de waarde *Stuf-zaken 310* bij compartimentdefinitie) naar een extern DMS, waarbij documenttype verplicht is. Wordt ook gebruikt bij documentregistratie in OpenWave (tbcorrespondentie) indien na het creëren van een document het document automatisch opgeslagen wordt en een regel in tbcorrespondentie wordt aangemaakt. Dit is het geval indien *Getal1* van *Sectie: Documenten Item: Documentregistratie* de waarde 1 heeft. De documenttypen keuzelijst bestaat in principe uit de niet vervallen rijen van beheertabel tbdocumenttypes waarbij geldt dat als er een compartiment gekozen is bij de sjabloondefinitie, de rijen beperkt zijn uit tbdocumenttypes voor gekozen compartiment. Indien er geen compartiment gekozen is bij de sjabloondefinitie bestaat de keuzelijst uit alle niet vervallen rijen EN geen gevulde dnkeycompartiment uit tbdocumenttypes.
  - **Aanduiding vertrouwelijkheid**. Deze kolom is alleen noodzakelijk indien de email als document direct dient te worden doorgezet met een zaak/DMS koppeling (*autom upload (dlautoupload)* is aangevinkt EN de kolom *Tekst* van instelling *Sectie: KoppelingDOCNAARDMS* en *Item: Methode* heeft de waarde StUF-ZAKEN 310) naar een extern DMS, waarbij het metadata gegeven vertrouwelijkheidsaanduiding verplicht is. Wordt ook gebruikt bij documentregistratie in OpenWave (tbcorrespondentie) indien na het creëren van een document het document automatisch opgeslagen wordt en een regel in tbcorrespondentie wordt aangemaakt. Dit is het geval indien *Getal1* van *Sectie: Documenten Item: Documentregistratie* de waarde 1 heeft.
  - **Benaderbaar vanuit tabel**. Deze kolom is verplicht en wordt onder meer gebruikt om de query variabelen :keyvergunning, :keyinrichting, :keyinspectie, :keyinspbezoek en :keyadvies en :keyklacht en :keyadres en :keylocatie en :keybezwaarberoep met de juiste contextuele waarde te vullen (zie hieronder query-variabelen). Niet alle tabelnamen zijn zinvol. Indien gevuld met waarde **tbadviezen** dan kan men het veld niet wijzigen als ook aangevinkt staat veld *Is sjabloon voor standaardmail naar adviesinstantie?*.
    -  In deze versie zijn alleen tbomgvergunning (indien een email wordt samengesteld op basis van de data uit de actieve kaart in tbomgvergunning) en tbinspbezoeken (:keyinspbezoek) actief in gebruik. Dit zijn tevens de plekken waar de gebruiker (mits geautoriseerd) de mogelijkheid heeft om de wizard *Maakemail* aan te roepen.
    - Indien gewenst kunnen er wel al sjablonen gedefinieerd worden voor toekomstige versies. Er kan dan gekozen worden voor de waarden: tbhandhavingen, tbovvergunningen, tbmilinrichtingen, tbmilvergunningen, tbbouwvergunningen en tbinfoaanvragen (zijn zinvol m.b.t. de variabele :keyvergunning en :keylocatie) en verder de tabel tbinspecties m.b.t. de variabele :keyinspectie, tbmilinrichtingen m.b.t. :keyinrichting en tbadviezen m.b.t. :keyadvies en tbcontactadressen m.b.t. :keyadres en tbklachten m.b.t. :keyklacht en tot slot tbbezwaarberoep m.b.t. :keybezwaarberoep.
  - **Alleen gemeentes**. Alleen indien deze kolom gevuld is heeft dat consequenties voor de lijst met sjablonen die de gebruiker kan kiezen met de wizard *Maakemail*. De kolom kan gevuld worden met de gemeentelijke identificatiecoderingen uit de tabel33 (bijv. 0197 = Aalten) gescheiden door een puntkomma. Indien gevuld zal het sjabloon alleen benaderbaar zijn indien de gemeente van de locatie waar de zaak, inrichting c.q. inspectie of advies zich afspeelt voorkomt in deze rij gemeente-identificaties.
  - **Naam sjabloon** (dvemailnaam). Deze kolom bevat de naam van de email. Indien de email als document moet worden opgeslagen en de kolom *Te genereren documentnaam* is niet gevuld, zal de documentnaam de hier ingevulde waarde krijgen.
  - **Autom. upload** (dlautoupload). Indien aangevinkt heeft dat als consequentie dat het programma na aanmaken en versturen van de email, een .txt file genereert en deze direct gaat opslaan: Indien
    - de kolom *Tekst* van instelling *Sectie: KoppelingDOCNAARDMS* en *Item: Methode* de waarde *StUF-ZAKEN 310* heeft EN de externe zaakcode is gevuld EN de instelling *Sectie: Documenten* en *Item: OphalenViaDMS* is aangevinkt, dan wordt het document doorgegeven met de zaak/DMS services. Zie [Upload documenten met StUF zaak/dms](/probleemoplossing/programmablokken/upload_document/upload_naar_stuf_zaak_dms.md)
    - de kolom *Tekst* van instelling *Sectie: KoppelingDOCNAARDMS* en *Item: Methode* de waarde *CMIS 1.0* heeft EN de instelling *Sectie: Documenten, Item: OphalenViaDMS* is aangevinkt EN de kolom *Item* van *Sectie: Aanmaakmappen* verwijst naar een kaart in tbinitialisatie met de juiste cmis-mapinformatie, dan wordt het document doorgegeven met CMIS. Zie: [Upload documenten met CMIS](/probleemoplossing/programmablokken/upload_document/upload_met_cmis.md)
    - de instelling *Sectie: Documenten, Item: OphalenViaFileserver* is aangevinkt EN de kolom *Item* van *Sectie: Aanmaakmappen* verwijst naar een kaart in tbinitialisatie met de juiste fileshare-mapinformatie, dan wordt het document geplaatst op de fileshare. Zie: [Upload documenten naar fileshare](/probleemoplossing/programmablokken/upload_document/upload_naar_fileshare.md).
  - **Item van Sectie Aanmaakmappen**. Deze kolom is alleen zinvol indien *Autom upload* is aangevinkt en die automatische upload van het gegenereerde document moet naar de fileshare of via CMIS in een DMS. Hier wordt verwezen naar de instellingskaart kaart met *Sectie: Aanmaakmappen* waarin exact wordt verwezen onder welke map het document geplaatst moet worden. Zie: [Upload document](/probleemoplossing/programmablokken/upload_document.md).
  - **Onderwerp mag gewijzigd worden bij aanmaken e-mail?**. Indien aangevinkt dan mag het onderwerp van de email gewijzigd worden in de wizard *Maakemail*.
  - **Onderwerp van email**. In deze kolom wordt de waarde van het onderwerp van de email gevuld. Bij het creëren van de mail zal er dus als onderwerp deze waarde worden meegegeven. Indien gewenst kunnen net als in de body van email, ook in het onderwerp tags voorkomen die verwijzen naar op te halen waardes uit de formqueries en kan men verwijzen naar een query uit de tbqueries tabel.
  - **Body mag gewijzigd worden bij aanmaken e-mail?**. Indien aangevinkt dan mag de body van de email gewijzigd worden in de wizard *Maakemail*.
  - **Body van email**. In deze kolom wordt de inhoud van de email gedefinieerd. Dit komt zo goed als overeen met de tekst die men bij documentsjablonen in de sjabloonfile zet. Met als uitzondering dat er geen tabel neergezet kan worden: dit veld is alleen platte tekst. Hierin zet u de tekst waaruit de email moet bestaan en zet u tags (zoals <101>) op de plekken waar deze vervangen moeten worden door waarden opgehaald in de Formqueries.
  - **Queries**. Er zijn 10 formqueries (queries waarvan het resultaat van het SQL-statement uit maar één regel mag bestaan) en 12 childqueries (de resultaatsets van deze SQL-statements mogen wel meer dan één regel bevatten). In deze versie zal er nog maar 1 rij per childquery geëvalueerd kunnen worden. Er kan in de body van de email verwezen worden naar de childquery door op de gewenste plekken tags te zetten als {1}, {2} etc. Zie kopjes formquery en childquery. De views waarvan de naam begint met ‘VwFrm’ zijn de views die goed gedocumenteerd zijn en door Rem bij updates worden beschermd. Het is dus raadzaam alleen deze views als onderlaag van de queries te gebruiken. Zie [https://www.open-wave.nl/community/online/datadictionary/Index.html](https://www.open-wave.nl/community/online/datadictionary/Index.html.md).

#### Formquery

Het resultaat van een formquery wordt gebruikt om merge-coderingen in de vorm van <1> of <301> in de body van de email te vervangen met waardes uit de database.

Een eenvoudig sjabloonvoorbeeld van een ontvangstbevestiging:

```txt
<101>
  <102>
  <103>
  <104>
  Onderwerp:
  Ontvangst aanvraag omgevingsvergunning <1> <2>
  <105>,
  Op <5> heeft u een omgevingsvergunning aangevraagd (zaakcode: <6>).
  Deze brief is een ontvangstbevestiging. Uw aanvraag betreft <4> op het adres <1> in <2>. In deze brief leest u meer over de procedure.
  Wij toetsen binnenkort of uw aanvraag genoeg gegevens bevat
  Welke gegevens voor een aanvraag nodig zijn staat in de Ministeriële regeling omgevingsrecht. Als uw aanvraag te weinig gegevens bevat, krijgt u daarover   schriftelijk bericht. U krijgt dan de mogelijkheid uw aanvraag verder aan te vullen. Als aanvullingen nodig zijn, kan de beslistermijn langer worden.
  Onze brieven en andere documenten ontvangt u per e-mail
  Als u dit niet wilt, laat het ons dan per brief weten.
  Neem contact op als u vragen heeft
  U kunt daarvoor bellen met de afdeling Vergunningen, telefoonnummer
  06 11 11 11 11. Mailen kan ook naar vergunningen@..............nl. Schrijft u een brief of een e-mail aan ons, noem daarin dan dit zaaknummer: <6>
  U kunt de zaak volgen met code <%strEncrypt(:dnkey)%> op
  http://tracktrace.demo3.open-wave.nl/TrackNTraceOmgBasis/
  Met vriendelijke groet,
  <204>,
  namens deze
  <201>
  <202>
  <203>
  <204>
```

Bij het samenvoegen van een sjabloon met gegevens uit de database geldt het volgende:

De resultaat set van een formquery moet dus bestaan uit één rij. Als de query meer rijen oplevert wordt alleen de eerste rij gebruikt.
De waardes uit de kolommen van die rij worden samengevoegd met merge-coderingen uit de bijbehorende dotx/odt/docx-file. OpenWave beschouwt elk getal tussen een “groter dan teken” (>) en een “kleiner dan teken” (<) als een te vervangen merge-code, bijv. <1> of <201> of <531>.

  - De merge-coderingen met nummers 1 - 100 verwijzen naar de kolomnummers van de resultaat set die door de query Form Query wordt bepaald.
  - De coderingen 101-200 verwijzen naar de kolomnummers van Form Query-2.
  - De coderingen 201-300 verwijzen naar de kolomnummers van Form Query-3.
  - De coderingen 301-400 verwijzen naar de kolomnummers van Form Query-4.
  - De coderingen 401-500 verwijzen naar de kolomnummers van Form Query-5.
  - De coderingen 501-600 verwijzen naar de kolomnummers van Form Query-6.
  - De coderingen 601-700 verwijzen naar de kolomnummers van Form Query-7.
  - De coderingen 701-800 verwijzen naar de kolomnummers van Form Query-8.
  - De coderingen 801-900 verwijzen naar de kolomnummers van Form Query-9.
  - De coderingen 901-1300 verwijzen naar de kolomnummers van Form Query-10.

Wanneer de samenvoegfunctie van OpenWave dus in de body van de email de merge-code <304> tegenkomt zal hij deze merge-code vervangen door de waarde van de 4e kolom van de resultaat set van formquery-4.

De merge-code <6> zal hij vervangen door de waarde van de 6e kolom van de resultaat set uit formquery-1.

In bovenstaand voorbeeld worden coderingen gebruikt uit groep formquery-1, formquery-2 en formquery-3.

Formquery-1 zou de volgende kunnen zijn (de aliassen - vanwege < en > tussen dubbele quootjes - verwijzen naar de merge-codering in het sjabloon. Niet verplicht wel handig):

```sql
SELECT
  a.dvobjadres x1,
  a.dvobjplaats x2,
  a.dvobjpostcode x3,
  a.dvaanvraagnaam x4,
  a.ddaanvraag x5,
  a.dvzaakcode x6
  FROM
  vwfrmomgvergunningen a
  where a.dnkeyomgvergunning = :keyvergunning
```

Formquery-2:

```sql
SELECT
  DVAVRBEDRIJF "<101>",
  DVAVRTAV "<102>",
  DVAVRADRES "<103>",
  DVAVRPOSTCODE | | ' ' | | DVAVRWOONPLAATS "<104>",
  DVAVRBRIEFAANHEF "<105>"
  FROM VWFRMOMGAVRCONTACTEN
  WHERE DNKEYOMGVERGUNNINGEN = :keyvergunning
```

Formquery-3:

```sql
Select
  case when a.DVGESLACHT='M' then 'dhr.'
       when a.DVGESLACHT='V' then 'mevr.'
       else 'dhr./mevr.' end "<201>",
   a.DVTELEFOON ,
   a.DVTUSSENVOEGSEL,
   a.DVVOORLETTERS,
   a.DVIBBNAAMMW,
   a.DVEMAIL
   from VWFRMACTIEFINBEHBIJ a
   WHERE a.DNKEYOMGVERGUNNINGEN = :keyvergunning
```

### Query-variabelen

  - Bij afspraak geldt de variabele **:keyvergunning** – indien mogelijk - in een form- of childquery door OpenWave gevuld wordt met het betreffende waarde van de keykolom van de actieve Omgevingsvergunning, Handhaving, Bouw/sloopvergunning, APV/Overige vergunning, Horeca-vergunning, Bestemmingsplan of Infoaanvraag, Milieu-gebruiksinrichting/vergunning/melding.
  - De variabele **:keyadvies** zal – indien mogelijk - in een SQL-query door OpenWave gevuld worden met de betreffende waarde van de sleutelkolom van de actieve kaart uit de Adviezentabel. Handig wanneer vanuit het adviezenscherm een document wordt aangemaakt.
  - De variabele **:keyinspectie** zal – indien mogelijk - in een SQL-query door OpenWave gevuld worden met de betreffende waarde van de sleutelkolom van de actieve kaart uit de Inspectietabel (inspectie-traject).
  - De variabele **:keyinspectiebezoek** zal – indien mogelijk - in een SQL-query door de OpenWave gevuld worden met de betreffende waarde van de sleutelkolom van de actieve kaart uit de Inspectiebezoektabel. Handig wanneer vanuit het inspectiebezoekscherm een document wordt aangemaakt.
  - De variabele **:keyklacht** zal – indien mogelijk - in een SQL-query door de OpenWave gevuld worden met de betreffende waarde van de sleutelkolom van de actieve kaart uit de klachten bij een inrichting. Handig wanneer vanuit het klachtenscherm een document wordt aangemaakt.
  - De variabele **:keyinrichting** zal – indien mogelijk - in een SQL-query door OpenWave gevuld worden met de betreffende waarde van de sleutelkolom van de de Inrichting die te herleiden is vanuit de tabel waarvandaan het document wordt gecreëerd: de hoofdzaken (tbomgvergunning, tbhandhaving e.d.) kunnen namelijk gekoppeld zijn aan een inrichting. Zo ook de Inspecties en Inspectiebezoeken en Klachten.
  -  De variabele **:keyadres** zal – indien mogelijk - in een SQL-query door OpenWave gevuld worden met de betreffende waarde van de sleutelkolom van de actieve kaart uit de tbcontactadressen, om bijvoorbeeld een brief te maken vanuit een aangewezen contactpersoon. Wanneer vanuit een andere tabel het document wordt gecreëerd en de inlogger een contactpersoon heeft aangewezen (indien contactpersoon verplicht bij het documentsjabloon is aangevinkt) zal deze waarde gebruikt worden.
  - De variabele **:keybezwaarberoep** zal – indien mogelijk - in een SQL-query door de OpenWave gevuld worden met de betreffende waarde van de sleutelkolom van de actieve kaart van tbbezwaarberoep (dus indien een document vanuit bezwaar/beroep wordt gecreëerd).
  - De variabele **:keylocatie** zal – indien mogelijk - in een SQL-query door OpenWave gevuld worden met de betreffende waarde van de sleutelkolom van de locatie (tbperceeladressen) die te herleiden is vanuit de tabel waarvandaan het document wordt gecreëerd.
  - De variabele **:keysjabloon** zal – indien mogelijk - in een SQL-query door OpenWave gevuld worden met de betreffende waarde van sjabloon-naam (tbmailsjabloon)
  - De variabele **:keydsoproject** zal – indien mogelijk - in een SQL-query door OpenWave gevuld wordt met de betreffende dnkey van het dso-project dat aan een omgevingzaak verbonden kan zijn.

#### OpenWave database functies

OpenWave heeft zelf een aantal functies op de database gedefinieerd - zoals fn_ddmaandjjjj() - die gebruikt kunnen worden in allerlei query's.
Zie:[OpenWave database functies](/instellen_inrichten/openwave_database-functies.md).

#### Childquery

Het resultaat van een childquery wordt gebruikt om merge-coderingen in de vorm van een getal tussen accolades (zoals {1} en {2}) binnen de body van een mailsjabloon te vervangen met waardes uit de database. Voor nu is het mogelijk om maar 1 rij per childquery weer te geven. Overige rijen zal het programma nog niet naar kijken.

Het eenvoudige voorbeeld van een ontvangstbevestiging is hieronder uitgebreid met verwijzingen naar de childquery waarin het de bedoeling is dat daar de onderdelen van de omgevingszaak worden opgesomd:

```
<101>
  <102>
  <103>
  <104>
  Onderwerp:
  Ontvangst aanvraag omgevingsvergunning <1> <2>
  <105>,
  Op <5> heeft u een omgevingsvergunning aangevraagd (zaakcode: <6>).
  Deze brief is een ontvangstbevestiging. Uw aanvraag betreft <4> op het adres <1> in <2>. In deze brief leest u meer over de procedure.
  Het onderdeel dat van toepassing is {1} met de daarbij horende activiteit is {2}
  Wij toetsen binnenkort of uw aanvraag genoeg gegevens bevat
  Welke gegevens voor een aanvraag nodig zijn staat in de Ministeriële regeling omgevingsrecht. Als uw aanvraag te weinig gegevens bevat, krijgt u daarover
  schriftelijk bericht. U krijgt dan de mogelijkheid uw aanvraag verder aan te vullen. Als aanvullingen nodig zijn, kan de beslistermijn langer worden.
  Onze brieven en andere documenten ontvangt u per e-mail
  Als u dit niet wilt, laat het ons dan per brief weten.
  Neem contact op als u vragen heeft
  U kunt daarvoor bellen met de afdeling Vergunningen, telefoonnummer
  06 11 11 11 11. Mailen kan ook naar vergunningen@..............nl. Schrijft u een brief of een e-mail aan ons, noem daarin dan dit zaaknummer: <6>
  U kunt de zaak volgen met code <%strEncrypt(:dnkey)%> op
  http://tracktrace.demo3.open-wave.nl/TrackNTraceOmgBasis/
  Met vriendelijke groet,
  <204>,
  namens deze
  <201>
  <202>
  <203>
  <204>
```

De childquery-1 kan er als volgt uitzien:

```sql
select
  dvtoestemmingnaam,
  dvwerkzaamheden
  from vwfrmtoestemmingen
  where
  vwfrmtoestemmingen.dnkeyomgvergunningen = :keyvergunning
  and vwfrmtoestemmingen.ddvervallen is null
```

### Speciale childquery: samenvoegen met externe bron

Het is mogelijk om delen van een sjabloon samen te voegen met gegevens uit een externe bron in plaats van met gegevens uit de OpenWave database. Dat kan vooralsnog alleen bij childqueries.

OpenWave zal bij een childquery zoeken naar speciale gevallen die worden herkend aan een vaste formulering in die childquery. Momenteel zijn daartoe enkel de volgende mogelijkheden:

  - Opsomming van afgekeurde items uit digitale checklist. De tekst in de bijbehorende childquery moet zijn: *JSON_DigitaleChecklisten_Controle_brief_1
*. Zie hiertoe het kopje *Instellingen voor overnemen van afgekeurde checklist-items in document* bij [Digitale checklisten](/probleemoplossing/programmablokken/digitale_checklijsten.md).

## Invoegen tekstblokken op basis van een query-aanroep naar tbqueries

Er kan in de body van de email een speciale vorm van merge-codering worden opgenomen die verwijst naar een kaart in tbqueries. In dat geval wordt die aangeroepen query geëvalueerd en het resultaat wordt op de bewuste plek in de email ingevoegd. Een dergelijke verwijzing ziet er als volgt uit:

  - <%query(codevanquery)%>
  - of <%query(codevanquery,:keyvergunning)%>

Hier dus geen verwijzing naar een formquery of childquery bij de body, maar een verwijzing naar een kaart in tbqueries.

Op grond van de eerste parameter (codevanquery in bovenstaand voorbeeld) wordt in tbqueries de kaart met dvcode = *codevanquery* gezocht en de bijbehorende query geëvalueerd, waarbij de variabele {id} in de query wordt vervangen door de tweede parameter (indien aanwezig). Die tweede parameter moet één van de bovenvermelde query-variabelen zijn (zoals :keyinrichting, :keyadvies, :keyvergunning) en is dus afhankelijk van de tabel van waaruit het sjabloon benaderd wordt.
Stel: de tabel is tbomgvergunning. Dan zal de tweede parameter :keyvergunning dus vervangen worden door de dnkey van tbomgvergunning van waaruit de email wordt gecreëerd.

Voorbeeld: de aangeroepen query met dvcode = *omgeving_tkstblk_1* op grond van de aanroep *<%query(omgeving_tkstblk_1,:keyvergunning)%>*
kan de volgende inhoud hebben:

```sql
select case when (select dvsoortproc from vwfrmomgvergunningen where dnkeyomgvergunning = {id}) = 'M'
              then 'Dit is ten gevolge van artikel x van wet y'
              else ''::text end
```

Hetgeen wil zeggen dat indien het zaaktype van de omgevingszaak waar je op staat van het type M (melding) is, druk dan de tekst *Dit is ten gevolge van artikel x van wet y* af. Anders, is het type anders dan M, druk dan niets af.

Datzelfde kan ook met hergebruik van blokken tekst door een verwijzing in de query naar tbtekstblokken:

```sql
select case when (select dvsoortproc from vwfrmomgvergunningen where dnkeyomgvergunning = {id}) = 'M'
              then  dvtekstblok
              else ''::text end
         from tbtekstblokken where lower(dvcode) = 'tkstblk_1'
```

Hetgeen wil zeggen dat indien het zaaktype van de omgevingszaak waar je op staat van het type M (melding) is, druk dan de waarde van de kolom dvtekstblok van de tabel tbtekstblokken af waarbij dvcode = *tkstblk_1*. Anders, is het type anders dan M, druk dan niets af. Die kolom dvtekstblok kan gevuld zijn met een tekst van maximaal 4000 tekens.

In de tabel tbtekstblokken (beheertegel *Tekstblokken*) kunnen deze tekstblokken gedefinieerd worden die op bovenstaande wijze in meerdere sjablonen op conditie kunnen worden aangeroepen. Zie ook: [Queries](/instellen_inrichten/queries.md).

### Tonen Wave briefnummer

(indien instelling *Sectie: Documenten, Item: WaveBriefNummer* is aangevinkt)

Indien gewenst kan er met de juiste instellingen een uniek briefnummer door OpenWave gecreëerd worden bij aanmaken van de email. Als je dit nummer in het sjabloon wilt tonen dan kan dit door in de body van de email de verwijzing <%teller%> te zetten op de plek waar je het briefnummer wilt tonen.
Voorbeeld: stel de instellingen zijn als volgt WaveBriefnummer staat aan, *Getal1* = 78, *Getal2* = 5 en *Tekst* = 'OW'. Het unieke briefnummer waarmee <%teller%> in de email vervangen zal worden is 'OW00079'.

### Tonen gecrypte versie van een kolomwaarde

Verder kan de encryptiemethode worden aangeroepen vanuit het emailsjabloon. De string <%strEncrypt(:columnname)%> in een sjabloon wordt bij het creëren van een email als volgt geïnterpreteerd. Het programma zal columnname interpreteren als een kolomnaam uit de hoofdtabel van het sjabloon. De waarde van die kolom wordt gecrypt volgens de ingestelde methode (zie: [2-way encryptie van externe wachtwoorden](/instellen_inrichten/2way_encryptie_externe_wachtwoorden)) en deze gecrypte waarde wordt in de email opgenomen op de betreffende plaats. Voorbeeld: <%strEncrypt(:dnkey.md)%>.

## Sjabloon-parameters

De substrings in de formqueries ingesloten door %-tekens (bijvoorbeeld %datumvanaf%) heten parameters. Deze worden bij het uitvoeren van het SQL-statement automatisch vervangen door een bedoelde waarde. Hoe dat gebeurt wordt gedefinieerd met de kolommen van de tabel tbemailparameters.

Uitzondering hierop is de string <%query(codevanquery)%> : Zie hierboven bij het sub lemma *Invoegen Tekstblokken*. Elke query kan 0 of meer parameters hebben.

### Parameterkolommen

  - In de kolom **parameternaam** (dvparameter) staat de naam van de parameter precies zoals die in de querie(s) van het bijbehorende sjabloon staat, maar dan zonder %-tekens. In de parameternamen mogen alleen letters of cijfers voorkomen of een underscore. Dus geen spaties of slashes/backslashes e.d..
  - **Invulsoort** (dvinvulsoort). Moet ingevuld worden. Er zijn drie mogelijkheden:
    - (A)utomatisch. Dit wil zeggen dat OpenWave de parameter onder water automatisch vervangt met de actieve waarde van de kolom default waarde.
    - (I)nvoer. Invoer wil zeggen dat de gebruiker de gelegenheid krijgt om de parameter te vervangen door een waarde die hij zelf opgeeft met als default de actieve waarde van de kolom default waarde.
    - (L)ijst. Lijst wil zeggen dat de gebruiker de te vervangen parameterwaarde kan kiezen uit een lijst in een dropdown-box alvorens het document wordt gegenereerd. De lijst wordt samengesteld door de query die wordt opgegeven bij *lijst query* (zie opmerkingen aldaar).
  - In de kolom **label** (dvlabel) kan hier het label behorende bij de te maken editbox of dropdownlist worden ingevoerd indien de Invulsoort = (I)nvoer of (L)ijst.
  - **Type** (dvinvoerobject). Type geldt alleen wanneer de InvulSoort = (I)nvoer of (L)ijst.
    - Indien Invulsoort is (I)nvoer dan bepaalt het type het masker voor de in te vullen waarden. De volgende conventies gelden indien gevuld:
      - STRING (tekst): Het programma toont een normale editbox om de waarde in te voeren voor zowel cijfers als letters. Dus ook wanneer het om een in te voeren numerieke waarde gaat (zoals een bedrag) kan als type toch string worden gekozen
      - DATUM: Laat datum kiezen uit een kalender
      - INTEGER (getal): Het programma toont een normale editbox om de waarde in te voeren voor een getal.
    - Indien Invulsoort is (L)ijst dan geldt dat als de waarde van eerste kolom van de result-dataset van de query_bij_soort_is_lijst (zie hieronder) een
      - Integer of float is dan moet het type leeg zijn (maar mag ook string zijn)
      - String is dan moet bij type ook een string worden gekozen
      - Datum is dan moet bij het type ook een datum worden gekozen.
  - **Query_bij_soort_is_lijst** (dvlijstquery). Geldt alleen wanneer de Invulsoort = (L)ijst. In geval van (L)ijst komt het resultaat van de hier opgegeven query als dropdownlist alvorens de rapportage wordt gestart. Daarbij geldt dat de waarde van eerste kolom van de result-dataset van de query als de te vervangen parameter wordt beschouwd (maar niet zichtbaar in de dropdownlist). De query mag maar twee kolommen bevatten genaamd id en omschrijving. Voorbeeld: *SELECT DvCode id, DvOmschrijving omschrijving from TbMedewerkers where ddvervaldatum is null order by omschrijving*. Het veld dat als id wordt omschreven, komt in het document te staan. Dus in bovenstaand voorbeeld komt het veld DvCode in het document, met *SELECT DvOmschrijving id, DvCode omschrijving from TbMedewerkers where ddvervaldatum is null order by omschrijving* komt het veld DvOmschrijving in het document en kunt u kiezen uit de codes. De queries die hier opgegeven kunnen worden kunnen verwijzen naar elke tabel of view van het database schema van Wave.
  - **Inputvolgordenummer** (dnregel). Geldt voor invulsoort (L)ijst of (I)nvoer. Hiermee kunt u de plek beïnvloeden van de editbox of lijst wanneer er meerdere parameters zijn. Mag leeg gelaten worden, maar dan is de volgorde van de gevraagde invoer willekeurig.
  - **Functie Defaultwaarde** (dvdefaultwaarde). Een – bij afspraak – geldende typering wat de standaard waarde moet zijn bij Invulsoort = (A)utomatisch en bij (I)nvoer. De mogelijkheden zijn:
    - Begin van dit jaar (DbeginJaar)
    - Eind van dit jaar (Deindjaar)
    - Vandaag (Dvandaag)
    - Vandaag minus 1 maand (Dmin1Maand)
    - Vandaag plus 1 maand (Dplus1Maand)
    - Vandaag minus 2 maanden (Dmin2Maand)
    - Vandaag plus 2 maanden (Dplus2Maand)
    - Vandaag minus 1 jaar (Dmin1Jaar)
    - Vandaag plus 1 jaar (Dplus1Jaar)
    - Vandaag minus 6 maanden (Dmin6Maand)
    - Vandaag plus 6 maanden (Dplus6Maand)
    - Huidige Gebruiker (Cinlogger) TbMedewerkers.DvCode van persoon die het sjabloon start
    - Identifier van powerportal (nportalid). Kan alleen gebruikt worden bij sjablonen die gestart worden vanuit een zaakportaal of een inrichtingsportaal. De identifier is dan de primary key van de betreffende module voor dat portaal.
  - **Vaste Defaultwaarde** (dvdefaultvast). Een vaste default waarde bij bij Invulsoort = (A)utomatisch en bij (I)nvoer en (L)ijst. Indien Lijst (waarbij de default waarde dus verwijst naar een bepaalde regel van het dropdownlijstje bestaande uit de kolommen id en omschrijving), dan geldt bij afspraak dat de id en de omschrijving van deze default waarde gescheiden moeten zijn met een puntkomma. Is er geen puntkomma in de default dan gaat OpenWave er vanuit dat de default waarde op zowel de id als de omschrijving van toepassing is. Stel de dropdownlijst is gedefinieerd als *select '1' id, 'Teamleider - standaard' omschrijving union select '3' id , 'Afdelingshoofd' omschrijving* dan kan de vaste default waarde gedefinieerd zijn als *3;Afdelingshoofd*.

#### Voorbeeld gebruik verschillende soorten (types) parameters

Stel: een sjabloon ziet er als volgt uit:

```
Rommeldam, <1>
  Betreft: <2>
  Hier volgt een aantal invoerparameters:
  Een code uit een medewerkerslijst <3>
  Een invoerdatum omgezet naar tekst <4>
  Een invoer getal (integer): <5>
  Een invoer van een getal (float) omgezet naar een bedrag <6>
  en de invoer van zomaar een string <7>
```

en de bijbehorende formquery als volgt:

```sql
Select
   fn_ddmaandjjjj(fn_vandaag(0)) "<1>"
   a.DVSOORTAANVRAAG "<2>",
   %Medewerker% "<3>",
   fn_ddmaandjjjj(to_date(%Zomaardatum%,'yyyy-mm-dd')) "<4>",
   %Zomaareeninteger% "<5>",
   fn_bedrag(cast(%Zomaareenfloat% as double precision)) "<6>",
   %Zomaareenstring% "<7>"
  from
  VWFRMOMGVERGUNNINGEN a
  WHERE	DNKEYOMGVERGUNNING = :keyvergunning
```

**LET HIER OP DAT:**

  - een integer of string inputparameter zonder quootjes of extra functie in de query kan worden opgenomen: zoals %Zomaareeninteger%
  - een floatparameter alleen ingebracht kan worden als type string en dat die dan gecast wordt naar float
  - een datumparameter gecast moet worden naar datum met bijv. to_date functie waarbij de ingevoerde datum wordt aangeleverd als yyyy-mm-dd

Er zijn dus 5 invoerparameters:

![](/img/applicatiebeheer/instellen_inrichten/invoerparameters2.png){ class="media" loading="lazy" alt="" width="600" }

Dat resulteert bij het genereren van de email tot een invoerscherm:

![](/img/applicatiebeheer/instellen_inrichten/parameters2.png){ class="media" loading="lazy" alt="" width="400" }

En de te genereren email ziet er dan zo uit:

```
Rommeldam, 01 mei 2017
  Betreft: reguliere procedure
  Hier volgt een aantal invoerparameters:
  Een code uit een medewerkerslijst MDH
  Een invoerdatum omgezet naar tekst 21 april 2017
  Een invoer getal (integer): 34
  Een invoer van een getal (float) omgezet naar een bedrag 123,69
  en de invoer van zomaar een string altijd is Kortjakje ziek
```

## formquery en childquery-verwijzingen naar tbqueries

De inhoud van de kolommen van de formqueries en childqueries kan ook bestaan uit een verwijzing naar een query in de beheertabel tbqueries. Zie: [Queries](/instellen_inrichten/queries.md)

Hierdoor hoeft een query die in meerdere sjablonen gebruikt wordt maar eenmalig te worden gedefinieerd.  De opmaak van de sjablonen wijzigt hierdoor niet.
Zie voorbeeld onder het kopje *formquery en childquery-verwijzingen naar tbqueries* bij [Documentsjablonen en Sjabloongroepen](/instellen_inrichten/documentsjablonen.md)

