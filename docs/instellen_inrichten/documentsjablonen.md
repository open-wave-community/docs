# Documentsjablonen en Sjabloongroepen

Portaal beheerportaal-Nieuw. Tegels **Documentsjablonen** en **Sjabloongroepen**.

Screenidentifiers:

- MDLC_getVwfrmDocumentenList.xml (vwfrmdocumenten)
- MDLC_getStencilGroupList.xml (tbdocumentsoorten)
- MDDC_getStencilGroupDetail.xml (tbdocumentsoorten)
- MDLC_getStencilList.xml (vwfrmdocumenten)
- MDDC_getStencilDetail.xml (vwfrmdocumenten)
- MDLC_getStencilParamsList.xml (tbrapportparameters)
- MDDC_getStencilParamsDetail.xml (tbrapportparameters)
- MDLC_getVwfrmKopDocAanDocSoortList.xml (vwfrmkopdocaandocsoort)

Vanaf versie 1.23 is het beheer van documentsjablonen gesplitst in het beheer van **Sjabloongroepen** (tbdocumentsoorten) en **Documentsjablonen** (tbdocumenten). De oude tegel _Documentsjablonen_ is hernoemd naar **Sjabloongroepen** en zal worden gebruikt voor het beheer van sjabloongroepen. De (nieuwe) tegel _Documentsjablonen_ is bedoelt voor het beheer van de documentsjablonen: het aanmaken van nieuwe sjablonen en het wijzigen ervan plus het koppelen aan sjabloongroepen.

Sjablonen zijn .odt of .dotx/.docx files waarin merge-coderingen zijn opgenomen die dynamisch worden gevuld met gegevens uit de database. Een sjabloon wordt opgeroepen met de menuoptie _Creëer document_ op diverse plekken in de applicatie, mits de gebruiker documentcreatie-rechten heeft voor de betreffende module. Voor de sjabloondefinities en groep definities inzien en wijzigen moet de inlogger beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99.

Alle kolommen en knoppen op de sjabloonschermen zijn dan toegankelijk.

## Sjabloongroepen

De sjablonen kunnen worden gekoppeld aan 1 of meerdere groepen, waarbij een groep toegekend kan worden aan één of meer modules door middel van hun moduleletters. Daar waar de gebruiker uiteindelijk een menuoptie _Creëer document_ tot zijn beschikking heeft is dus deze moduleletter bepalend voor de inhoud van de radiobuttonlist: kies sjabloonsoort.

- A: Algemeen
- M: Management
- W: Omgeving
- O: APV/Overig
- H: Handhaving
- I: Info
- E: Milieu/gebruik (gedeeltelijk pre-wabo) + Inrichtingen/Vestigingen/Objectregistratie
- C: Horeca
- B: Bouw/Sloop (pre-wabo)

Vervallen sjabloongroepen zijn niet zichtbaar voor de gebruiker bij de wizard creëer document.
In het detailscherm van een sjabloongroep, wordt de lijst met gekoppelde sjablonen getoond. Door middel van de plus- dan wel de min-knop, kunnen sjablonen gekoppeld/ontkoppeld worden aan de sjabloongroep. Er valt alleen te kiezen uit sjablonen die qua module overeenkomen met de toebedeelde modules aan de sjabloongroep. Ook zijn altijd zichtbaar de sjablonen die al gekoppeld zijn (ongeacht of deze sjablonen later vervallen zijn/ de module gewijzigd is waardoor logischerwijs het sjabloon niet opnieuw te kiezen is bij de sjabloongroep). Het daadwerkelijk aanmaken/verwijderen van sjablonen gebeurd bij de sjablonenlijst.

### Sjabloondefinitie (documentsjablonenlijst)

In de lijst met documentsjablonen kunnen documentsjablonen verwijderd worden (inclusief parameters), nieuw aangemaakt en gekopieerd worden. Bij het maken van een kopie worden de parameters mee gekopieerd. Ook kan er op de lijst gefilterd en gezocht worden.

### Sjabloondefinitie (detailscherm)

In het detailscherm van een documentsjabloon kan men het sjabloon na aanmaken vervolgens koppelen aan de gewenste sjabloongroep(en) via het blok **Sjabloongroep(en)**. Hierbij valt er te kiezen uit sjabloongroepen die niet vervallen zijn en waarvan de module van het sjabloon waar men op staat voorkomt in de modules van de sjabloongroep.
Voor bestaande sjablonen kan via het detailscherm op dezelfde manier de koppeling aan sjabloongroepen gewijzigd worden. Met de komst van dit blok is het veld _Sjabloongroep_ komen te vervallen.

## Triggers

### Triggers in het menu opties rechtsboven

- **Toon uploads** bij deze sjabloonfile. Hiermee wordt de uploadgeschiedenis getoond van het documentsjabloon zelf in de kolom dvtemplatebase64. Zie [Upload Lijst](../probleemoplossing/module_overstijgende_schermen/uploads_lijst.md)
- **Verwijder upgeloade sjabloon**. Hiermee wordt de kolom dvtemplatebase64 leeggemaakt. Zichtbaar doordat het aanvinkvakje voor het label _Sjabloon is upgeload in tabel_ leeggemaakt wordt.

### Triggers linksonder

- Met de knop **controleer SQL-statements** worden de gevulde query-kolommen gevalideerd. De betreffende kolomnamen worden zichtbaar met een groen bolletje indien ok en met een rood bolletje indien het statement niet valide is.
- Met de knop **upload sjabloonfile** kan één document (met extensie .odt of .dotx of .docx) aangewezen worden, dat vervolgens met base64 opgeslagen wordt in de kolom dvtemplatebase64. Zichtbaar doordat het aanvinkvakje voor het label _Sjabloon is upgeload in tabel_ gevuld is. Indien de kolom _(UNC-pad) + naam sjabloon_ een lege waarde had, dan wordt deze gevuld met de naam van het zojuist geüploade document.

**LET OP:** indien de gebruikte merge-coderingen waarden bevatten die niet door de spellingchecker heenkomen, dan moet het sjabloon opgeslagen zijn zonder spellingchecker!!!

- De knop **download sjabloonfile** is alleen enabled indien de kolom dvtemplatebase64 gevuld is (zichtbaar doordat het aanvinkvakje voor het label _Sjabloon is geüpload in tabel_ gevuld is) EN indien de kolom _(UNC-pad) + naam sjabloon_ een gevulde waarde heeft. Indien deze laatste kolom zowel een UNC-pad heeft als een filenaam, dan wordt de file gedownload onder de filenaam op de standaard downloadmap.
- De knop **bewerk opgeslagen sjabloon** is alleen enabled indien de kolom dvtemplatebase64 gevuld is (zichtbaar doordat het aanvinkvakje voor het label _Sjabloon is geüpload in tabel_ gevuld is) EN indien de kolom _(UNC-pad) + naam sjabloon_ een gevulde waarde heeft. De knop is enabled indien
  - de instelling _Sectie: Documenten Item: OnlyOffice_ is aangevinkt (en dus OnlyOffice is geïnstalleerd).
  - EN de extensie van de sjabloonnaam (dvtemplatebase64) komt voor in de kolom _Tekst_ van deze instelling (waarbij in kolom _Tekst_ de mogelijke extensies gescheiden zijn door een puntkomma, dus bijvoorbeeld docx;xslsx;).

### Triggers rechtsonder

- Met het aanvinkvakje (default aangevinkt) vervallen kaarten zichtbaar, kan de lijst gefilterd worden op alleen niet-vervallen sjablonen.

## Kolommen van sjabloon

- De kolom **ID** (dnkey) geeft de automatisch gegenereerde primary key weer van het sjabloon in de tabel tbdocumenten.
- **Naam/beschrijving** (dvomschrijving). Vrij in te voeren naam voor het sjabloon, zoals die voor gebruikers zichtbaar worden in een lijst, wanneer de gebruiker de wizard _Maakdocument_ aanroept.
- **Naam van sjabloon in Xential** (dvnaaminexternsjablprog). Moet alleen gevuld worden indien het OpenWave sjabloon doorgeefluik is naar een Xentail-sjabloon. Zie: [Xential](../probleemoplossing/programmablokken/xential.md).
- **Compartiment** (dnkeycompartiment). Indien het sjabloon hier wordt toegekend aan een [compartiment](./compartimenten.md) kan dit sjabloon alleen worden gebruikt door iemand die lid is van dat compartiment. Omgekeerd: de inloggers die geen lid zijn van een compartiment zien enkel sjablonen die ook niet zijn toegekend aan een compartiment.
- Met het **Volgordenummer** kan de volgorde van de sjabloonnamen bepaald worden zoals die voor gebruikers zichtbaar worden in een lijst, wanneer de gebruiker de wizard _Maakdocument_ aanroept via optie _Creëer document_.
- **Vervaldatum**. Vervallen documentsjablonen zijn niet zichtbaar voor de gebruiker bij de wizard _Maakdocument_.
- **Te genereren documentnaam** (dvtemplate). Bij het samenvoegen in de wizard _Maakdocument_ van sjabloon en databasevelden wordt een nieuw document gecreëerd. Hier kan de gewenste documentnaam worden ingevuld (zonder extensie). Indien deze kolom is gevuld dan geldt het volgende: de nieuwe documentnaam is de waarde van deze kolom met het extensiegedeelte (inclusief punt) uit de kolom _(uncpad) + naam sjabloon_ (dvdocumentnaam) waarbij de extensie .dotx wordt omgezet naar .docx. De variabelen:
  - %date% in dvtemplate wordt door de applicatie vervangen door 'yyyymmdd' van de systeemdatum
  - %login% in dvtemplate wordt vervangen door de medewerkerscode van de inlogger
  - %hoofdzaaknr% in dvtemplate wordt vervangen door de wavezaakcode van de hoofdzaak c.q. inrichting
  - %deelzaaknr% in dvtemplate wordt vervangen door de wavezaakcode van de deelzaak (dus advies, inspectie of bezwaar/beroep)
  - %hoofddmsnr% in dvtemplate wordt vervangen door de externe zaak/DMS code (dvintzaakcode) van de hoofdzaak c.q. inrichting
  - %deeldmsnr% in dvtemplate wordt vervangen door de externe zaak/DMS code (dvintzaakcode) van de de deelzaak (dus advies, inspectie of bezwaar/beroep)
  - %teller% in dvtemplate wordt vervangen door uniek briefnummer dat gegenereerd wordt op moment van aanmaken van brief mits de instelling _Sectie: Documenten en Item: WaveBriefNummer_ bestaat en is aangevinkt
  - %adres% in dvtemplate wordt vervangen door het adres + de woonplaats van de hoofdzaak/inrichting
  - %ExtDocIdent% (hoofdlettergevoelig!) in dvtemplate wordt vervangen door de externe documentidentifier die verkregen wordt door een Stuf Zaak/DMS genereerdocumentidentificatie-bericht. Alleen van toepassing indien automatische opslag in een DMS via Stuf Zaak/DMS. Wanneer OpenWave geen externe documentidentifier kan bemachtigen, blijft de tag %ExtDocIdent% staan in de documentnaam. Indien kolom dvtemplate leeg is dan geldt als te genereren documentnaam de waarde van de kolom _(UNC-pad) + naam sjabloon_ (dvdocumentnaam) exclusief het eventuele UNC-pad. Ook hier wordt .dotx omgezet naar .docx.

dvtemplate heeft de waarde _vraagaanvulling\_%date%_ en de _(UNC-pad) + naam sjabloon_ (dvdocumentnaam) heeft de waarde: _Beleefde vraag aanvulling.dotx_, dan wordt de te genereren documentnaam: _vraagaanvulling_20170420.docx_

- **Benaderbaar vanuit tabel**. Deze kolom is verplicht en wordt onder meer gebruikt om de query variabelen :keyvergunning, :keyinrichting, :keyinspectie, :keyinspectiebezoek :keyadvies en :keyklacht en :keyadres en :keylocatie en :keybezwaarberoep met de juiste contextuele waarde te vullen (zie hieronder query-variabelen). Niet alle tabelnamen zijn zinvol. Alleen tbomgvergunning (indien een document wordt gevormd op basis van de data uit de actieve kaart in tbomgvergunning), tbhandhavingen, tbovvergunningen, tbmilinrichtingen, tbmilvergunningen, tbbouwvergunningen en tbinfoaanvragen zijn zinvol m.b.t. de variabele :keyvergunning en :keylocatie. En verder de tabel tbinspecties m.b.t. de variabele :keyinspectie en de tabel tbinsbezoeken m.b.t. :keyinspectiebezoek, tbmilinrichtingen m.b.t. :keyinrichting en tbadviezen m.b.t. :keyadvies en tbcontactadressen m.b.t. :keyadres en tbklachten m.b.t. :keyklacht en tot slot tbbezwaarberoep m.b.t. :keybezwaarberoep. Dit zijn tevens de plekken waar de gebruiker (mits geautoriseerd) de mogelijkheid heeft om de wizard _Maakdocument_ aan te roepen
- **Voor module**. Lijkt dubbelop i.v.m. _benaderbaar vanuit tabelnaam_, maar zowel voor klachten, adviezen en inspecties en bezwaar/beroep geldt dat zij vanuit verschillende modules oproepbaar zijn. Dus als een document wordt gebruikt bij een inspectie waarbij gegevens uit de bijbehorende omgevingszaak worden gebruikt dan is de tabelnaam: tbinspecties en de moduleletter: W.
  Mogelijkheden zijn W: Omgeving O: APV/Overig, H: Handhaving, I: Info, E: Milieu/gebruik (gedeeltelijk pre-wabo) + Inrichtingen/Vestigingen/Objectregistratie, C: Horeca en B: Bouw/Sloop (pre-wabo)
- **Documenttype DMS**. Deze kolom is noodzakelijk indien het te genereren document direct wordt doorgezet met een zaak/DMS koppeling (_autom upload (dlautoupload)_ is aangevinkt EN indien GEEN compartiment dan de kolom _Tekst_ van instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ heeft de waarde StUF-ZAKEN 310, indien WEL compartiment dan Documenten opslag in DMS aangevinkt en veld DMS-Methode heeft de waarde Stuf-zaken 310 bij compartimentdefinitie) naar een extern DMS, waarbij documenttype verplicht is. Wordt ook gebruikt bij documentregistratie in OpenWave (tbcorrespondentie) indien na het creëren van een document het document automatisch opgeslagen wordt en een regel in tbcorrespondentie wordt aangemaakt. Dit is het geval indien _Getal1_ van _Sectie: Documenten en Item: Documentregistratie_ de waarde 1 heeft. De documenttypen keuzelijst bestaat in principe uit de niet vervallen rijen van beheertabel tbdocumenttypes waarbij geldt dat als er een compartiment gekozen is bij de sjabloondefinitie, de rijen beperkt zijn uit tbdocumenttypes voor gekozen compartiment. Indien er geen compartiment gekozen is bij de sjabloondefinitie bestaat de keuzelijst uit alle niet vervallen rijen EN geen gevulde dnkeycompartiment uit tbdocumenttypes
- **Aanduiding vertrouwelijkheid**. Deze kolom is alleen noodzakelijk indien het te genereren document direct wordt doorgezet met een zaak/DMS koppeling (_autom upload (dlautoupload)_ is aangevinkt EN de kolom _Tekst_ van instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ heeft de waarde StUF-ZAKEN 310) naar een extern DMS, waarbij het metadata gegeven vertrouwelijkheidsaanduiding verplicht is. Wordt ook gebruikt bij documentregistratie in OpenWave (tbcorrespondentie) indien na het creëren van een document het document automatisch opgeslagen wordt en een regel in tbcorrespondentie wordt aangemaakt. Dit is het geval indien _Getal1_ van _Sectie: Documenten en Item: Documentregistratie_ de waarde 1 heeft
- **Alleen gemeentes**. Alleen indien deze kolom gevuld is heeft dat consequenties voor de lijst met sjablonen die de gebruiker kan kiezen met de wizard _Maakdocument_. De kolom kan gevuld worden met de gemeentelijke identificatiecoderingen uit de tabel33 (bijv. 0197 = Aalten) gescheiden door een puntkomma. Indien gevuld zal het sjabloon alleen benaderbaar zijn indien de gemeente van de locatie waar de zaak, inrichting c.q. inspectie of advies zich afspeelt voorkomt in deze rij gemeente-identificaties
- **Moet dig. ondertekend worden** (dllmoetdigondertekenen). Indien aangevinkt zal een geregistreerd document op basis van dit sjabloon ook geregistreerd staan als _moet digitaal ondertekend worden_
- **Contactpersoon kiezen** (dlcontactverplicht). Indien aangevinkt dan zal de inlogger bij het creëren van een document gevraagd worden een contactpersoon te kiezen. De keuze is beperkt tot de contactpersonen die bij de hoofdzaak/inrichting gedefinieerd zijn. De bezwaar/beroep tabel heeft haar eigen contactpersonen. De dnkey van deze contactpersoon wordt gebruikt om de variabele :keyadres uit de SQL-statements te vullen
- **Bijlages aanwijzen uit geregistreerde documenten** (dlbijlagesregdoc). Indien aangevinkt en de instelling _Getal1_ van _Sectie: Documenten en Item: Documentregistratie_ de waarde 1 heeft (hetgeen betekent dat gecreëerde documenten automatisch worden opgeslagen in geregistreerde documenten (tbcorrespondentie), dan zal de inlogger bij het creëren van een document gevraagd worden een of meer andere geregistreerde documenten aan te wijzen behorende bij dezelfde zaak die opgeslagen worden in de tabel tbcorrespbijlages als dochter van het aan te maken (geregistreerde) document
- **Voorgestelde documentnaam overschrijfbaar?** (dlnaammuteerbaar). Indien aangevinkt zal de voorgestelde documentnaam alsnog te wijzigen zijn bij het creëren van het document
- **Document mag alleen per post verzonden worden** (dlmoetperpost). Indien aangevinkt dan zal de gebruiker bij het creëren van een document op basis van dit sjabloon dit gegeven NIET kunnen wijzigen. Het gevolg is ook dat bij een automatische registratie van een document op grond van dit sjabloon de kolom tbcorrespondentie.dlmoetperpost ook de waarde T krijgt en NIET muteerbaar is. indien niet aangevinkt dan kan de gebruiker bij de creatie van een document wel de keuze maken per post of per email
- **Richting** (dvdocrichting). Uitgaand of Intern. Deze geldt als default voor de waarde die de gebruiker kan opgeven tijdens de creatie van het document op basis van dit sjabloon. Deze eigenschap wordt overgenomen in de automatische registratie van het document (tbcorrespondentie) indien dat zo is ingesteld
- **(UNC-pad) + naam sjabloon** (dvdocumentnaam). Deze kolom moet in ieder geval een filenaam bevatten met extensie .dotx, docx of .odt. Indien de filenaam voorafgegaan wordt door een UNC-pad EN de kolom dvtemplatebase64 is NIET gevuld (zichtbaar indien _Sjabloon is upgeload in tabel_ leeg is: leeg te maken via de menu optie),dan zal het programma proberen het sjabloon van de fileshare op te halen. Dan moeten ook de kolommen*Tekst*bij de instellingen _Sectie: Documenten_ en de _Items: OphalenViaFileserver_Domain, OphalenViaFileserver_Password, OphalenViaFileserver_Username en OphalenViaFileserver_Wins_ gevuld zijn. Indien de kolom dvtemplatebase64 WEL is gevuld (zichtbaar indien*Sjabloon is upgeload in tabel* aangevinkt is) dan zal het programma voor het samenvoegen de sjabloon uit deze kolom halen. Er is dan geen toegang tot de fileshare nodig (behalve indien het gegenereerde document daarop automatisch geplaatst moet worden)
- **Sjabloon is upgeload in tabel** (dvtemplatebase64 is wel/niet gevuld). Zie hierboven en bij de triggers upload/download sjabloon
- **autom upload** (dlautoupload). Indien aangevinkt heeft dat als consequentie dat het programma het te genereren document direct gaat opslaan: Indien
  - de kolom _Tekst_ van instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ de waarde _StUF-ZAKEN 310_ heeft EN de externe zaakcode is gevuld EN de instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_ is aangevinkt, dan wordt het document doorgegeven met de zaak/DMS services. Zie [Upload documenten met StUF zaak/dms](../probleemoplossing/programmablokken/upload_document/upload_naar_stuf_zaak_dms.md)
  - de kolom _Tekst_ van instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ de waarde _CMIS 1.0_ heeft EN de instelling _Sectie: Documenten, Item: OphalenViaDMS_ is aangevinkt EN de kolom _Item_ van _Sectie: Aanmaakmappen_ verwijst naar een kaart in tbinitialisatie met de juiste CMIS map-informatie, dan wordt het document doorgegeven met CMIS. Zie: [Upload documenten met CMIS](../probleemoplossing/programmablokken/upload_document/upload_met_cmis.md)
  - de instelling _Sectie: Documenten, Item: OphalenViaFileserver_ is aangevinkt EN de kolom _Item_ van _Sectie: Aanmaakmappen_ verwijst naar een kaart in tbinitialisatie met de juiste fileshare-mapinformatie, dan wordt het document geplaatst op de fileshare. Zie: [Upload documenten naar fileshare](../probleemoplossing/programmablokken/upload_document/upload_naar_fileshare). Indien sprake is van een hybride situatie van zowel opslag mogelijk op fileserver als in DMS kan een voorkeur opgegeven worden met de instelling _Sectie: Documenten Item: BriefAutoOpslaan_. Indien _Getal1_ wordt gevuld met 1 dan zal OpenWave bij het creëren van een brief op basis van een sjabloon als default de fileserver voorstellen. Bij 2 wordt DMS voorgesteld en bij 3 de optie Nee (hetgeen betekent: niet automatisch opslaan). Deze instelling geldt alleen voor de Host. Indien namelijk sprake is van een compartiment wordt deze zelfde informatie opgehaald uit de nieuwe kolom met label _Default brieven opslaan_ (tbcompartiment.dnAutoopslaan.md)
- **Item Sectie Aanmaakmappen**. Deze kolom is alleen zinvol indien _autom upload_ is aangevinkt en die automatische upload van het gegenereerde document moet naar de fileshare of via CMIS in een DMS. Hier wordt verwezen naar de instellingskaart kaart met _Sectie : Aanmaakmappen_ waarin exact wordt verwezen onder welke map het document geplaatst moet worden. Zie: [Upload document](../probleemoplossing/programmablokken/upload_document.md)
- **Queries**. Er zijn 10 formqueries (queries waarvan het resultaat van het SQL-statement uit maar één regel mag bestaan) en 12 childqueries (de resultaatsets van deze SQL-statements mogen wel meer dan één regel bevatten). In het .odt of .dotx of .docx sjabloon worden childqueries gebruikt om tabellen te vullen en formqueries voor één op één merge-coderingen. Zie kopjes formquery en childquery. De views waarvan de naam begint met ‘VwFrm’ zijn de views die goed gedocumenteerd zijn en door Rem bij updates worden beschermd. Het is dus raadzaam alleen deze views als onderlaag van de queries te gebruiken. Zie [https://www.open-wave.nl/community/online/datadictionary/Index.html](https://www.open-wave.nl/community/online/datadictionary/Index.html.md).

=====Queries voor merge =====
Queries worden gebruikt om een documentsjabloon te mergen met gegevens uit de database.

In het geval dat het OpenWave sjabloon een doorgeefluik is naar een Xential sjabloon (kolom dvnaaminexternsjablprog is dan gevuld), worden de resultsets van de queries gebruikt om een xml te construeren die Xential gebruikt om te mergen. Zie voor deze toepassing: [Xential](../probleemoplossing/programmablokken/xential.md).

====Formquery ====

Het resultaat van een formquery wordt gebruikt om merge-coderingen in de vorm van <1> of <301> in een sjabloon te vervangen met waardes uit de database.

**LET OP:** Zorg dat de spellingchecker uit staat EN zorg dat de coderingen in het sjabloon zonder opmaak zijn (dus echt elke code selecteren en opmaak wissen uitvoeren)

Een eenvoudig sjabloonvoorbeeld van een ontvangstbevestiging:
<code>
<101>
<102>
<103>
<104>
Rommeldam, <7>
Betreft: <5>
<105>,
Hierbij kan ik u mededelen dat uw aanvraag betreffende een omgevingsvergunning voor <1> op <2> te <3>,
in goede orde is ontvangen op <4>.
De aanvraag wordt behandeld onder zaakcode <6>.
Wij hopen de zaak binnen <8> dagen afgerond te hebben.
Hoogachtend,
Burgemeester en wethouders van Gemeente Rommeldam,
namens dezen,
hoofd afdeling Vergunningen,
<201> <204> <203> <205>
Email: <206>
Tel: <202>
</code>

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
- De coderingen 801.1300 verwijzen naar de kolomnummers van Form Query-9.
- De coderingen 901.1300 verwijzen naar de kolomnummers van Form Query-10.

</wrap>

Wanneer de samenvoegfunctie van OpenWave dus in de dotx/docx/odt-file de merge-code <304> tegenkomt zal hij deze merge-code vervangen door de waarde van de 4e kolom van de resultaat set van formquery-4. De merge-code <6> zal hij vervangen door de waarde van de 6e kolom van de resultaat set uit formquery-1.

In bovenstaand voorbeeld worden coderingen gebruikt uit groep formquery-1, formquery-2 en formquery-3.

Formquery-1 zou de volgende kunnen zijn (de aliassen - vanwege < en > tussen dubbele quootjes - verwijzen naar de merge-codering in het sjabloon. Niet verplicht wel handig):

```sql
Select
  a.DVAANVRAAGNAAM "<1>",
  a.DVOBJADRES "<2>",
  a.DVOBJPLAATS "<3>",
  a.DDAANVRAAG "<4>",
  a.DVSOORTAANVRAAG "<5>",
  a.DVZAAKCODE "<6>",
  fn_ddmaandjjjj(fn_vandaag(0)) "<7>"
  from
  VWFRMOMGVERGUNNINGEN a
  WHERE DNKEYOMGVERGUNNING = :keyvergunning
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
       else '' end "<201>",
   a.DVTELEFOON ,
   a.DVTUSSENVOEGSEL,
   a.DVVOORLETTERS,
   a.DVIBBNAAMMW,
   a.DVEMAIL
   from VWFRMACTIEFINBEHBIJ a
   WHERE a.DNKEYOMGVERGUNNINGEN = :keyvergunning
```

### Query-variabelen

- Bij afspraak geldt de variabele **:keyvergunning** – indien mogelijk - in een form- of childquery door OpenWave gevuld wordt met het betreffende waarde van de keykolom van de actieve Omgevingsvergunning, Handhaving, Bouw/sloopvergunning, Overige vergunning, Horecavergunning, Bestemmingsplan of Infoaanvraag, Milieu-gebruiksinrichting/vergunning/melding.
- De variabele **:keyadvies** zal – indien mogelijk - in een SQL-query door OpenWave gevuld wordt met de betreffende waarde van de sleutelkolom van de actieve kaart uit de Adviezentabel. Handig wanneer vanuit het adviezenscherm een document wordt aangemaakt.
- De variabele **:keyinspectie** zal – indien mogelijk - in een SQL-query door OpenWave gevuld wordt met de betreffende waarde van de sleutelkolom van de actieve kaart uit de Inspectietabel (inspectie-traject).
- De variabele **:keyinspectiebezoek** zal – indien mogelijk - in een SQL-query door de OpenWave gevuld wordt met de betreffende waarde van de sleutelkolom van de actieve kaart uit de Inspectiebezoektabel. Handig wanneer vanuit het inspectiebezoekscherm een document wordt aangemaakt.
- De variabele **:keyklacht** zal – indien mogelijk - in een SQL-query door de OpenWave gevuld wordt met de betreffende waarde van de sleutelkolom van de actieve kaart uit de klachten bij een inrichting. Handig wanneer vanuit het klachtenscherm een document wordt aangemaakt.
- De variabele **:keyinrichting** zal – indien mogelijk - in een SQL-query door OpenWave gevuld wordt met de betreffende waarde van de sleutelkolom van de de Inrichting die te herleiden is vanuit de tabel waarvandaan het document wordt gecreëerd: de hoofdzaken (tbomgvergunning, tbhandhaving e.d.) kunnen namelijk gekoppeld zijn aan een inrichting. Zo ook de Inspecties en Inspectiebezoeken en Klachten.
- De variabele **:keyadres** zal – indien mogelijk - in een SQL-query door OpenWave gevuld wordt met de betreffende waarde van de sleutelkolom van de actieve kaart uit de tbcontactadressen, om bijvoorbeeld een brief te maken vanuit een aangewezen contactpersoon. Wanneer vanuit een andere tabel het document wordt gecreëerd en de inlogger een contactpersoon heeft aangewezen (indien contactpersoon verplicht bij het documentsjabloon is aangevinkt) zal deze waarde gebruikt worden.
- De variabele **:keybezwaarberoep** zal – indien mogelijk - in een SQL-query door de OpenWave gevuld wordt met de betreffende waarde van de sleutelkolom van de actieve kaart van tbbezwaarberoep (dus indien een document vanuit bezwaar/beroep wordt gecreëerd).
- De variabele **:keylocatie** zal – indien mogelijk - in een SQL-query door OpenWave gevuld wordt met de betreffende waarde van de sleutelkolom van de de locatie (tbperceeladressen) die te herleiden is vanuit de tabel waarvandaan het document wordt gecreëerd.
- De variabele **:keysaangewezenbijlages** : zie hieronder bij speciale childqueries: Opsommen aangewezen bijlages.
- De variabele **:keysjabloon** zal – indien mogelijk - in een SQL-query door OpenWave gevuld wordt met de betreffende naam van het gebruikte sjabloon (tbdocumenten).
- De variabele **:keydsoproject** zal – indien mogelijk - in een SQL-query door OpenWave gevuld wordt met de betreffende dnkey van het DSO-project dat aan een omgevingzaak verbonden kan zijn.

#### OpenWave database functies

OpenWave heeft zelf een aantal functies op de database gedefinieerd - zoals fn_ddmaandjjjj() - die gebruikt kunnen worden in allerlei queries.
Zie:[OpenWave database functies](./openwave_database-functies.md).

### Childquery

Het resultaat van een childquery wordt gebruikt om merge-coderingen in de vorm van een getal tussen accolades (zoals {1} en {2}) binnen tabellen van een sjabloon te vervangen met waardes uit de database. Van boven naar beneden zullen de {1} en {2} merge-coderingen van de eerste tabel in het sjabloon vervangen worden door childquery-1 en de merge-coderingen van de tweede tabel met die van childquery2 en zo verder.
De tabel(len) in de sjabloonfile moeten uit twee regels bestaan: de eerste regel is voor de vaste labels en in de tweede regel komen dan de merge-coderingen.
Het aantal regels dat de tabel uiteindelijk in het te genereren document gaat innemen is afhankelijk van het aantal rijen uit de resultaat set.

Het eenvoudige .docx voorbeeld van een ontvangstbevestiging is hieronder uitgebreid met een tabel waarin het de bedoeling is dat daar de onderdelen van de omgevingszaak worden opgesomd:

![](../img/applicatiebeheer/instellen_inrichten/sjabloonmettabel.png){ class="media" loading="lazy" alt="" width="600" }

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

**LET OP:** Bij gebruik van .odt-sjablonen met Libre Office moeten in plaats van cijfers, letters gebruikt worden. Dus de notatie in een cel is dan {a}, {b} etc. Hiervoor moet ook een extra programma-instelling aangemaakt worden en aangevinkt: _Sectie: Programma_ en _Item: SamenvoegenTabellenMetLetters_.

In de tabellen mogen meerdere merge-coderingen per cel gebruikt worden al of niet in combinatie met tekst:

![](../img/applicatiebeheer/instellen_inrichten/tabelmettekstencodering.png){ class="media" loading="lazy" alt="" width="600" }

LET OOK OP: Indien in het sjabloon een tabel is opgenomen in de header of footer dan geldt het volgende:

- in die headertabel mogen alleen merge-coderingen gebruikt worden die naar formqueries verwijzen, dus <1> of <203>). Dus niet: {1} of {201}
- de tabel in de header telt wel mee in de tellingen van het aantal tabellen. Dus stel dat in de header één tabel staat en in de body staat ook één tabel, dan verwijst de tabel van de body naar childquery2.

### Speciale childquery: samenvoegen met externe bron

Het is mogelijk om delen van een sjabloon samen te voegen met gegevens uit een externe bron in plaats van met gegevens uit de OpenWave database. Dat kan vooralsnog alleen bij childqueries.
OpenWave zal bij een childquery zoeken naar speciale gevallen die worden herkend aan een vaste formulering in die childquery.
Momenteel zijn daartoe enkel de volgende mogelijkheden:

- Opsomming van afgekeurde items uit digitale checklist. De tekst in de bijbehorende childquery moet zijn: _JSON_DigitaleChecklisten_Controle_brief_1
  _. Zie hiertoe het kopje _Instellingen voor overnemen van afgekeurde checklist-items in document_ bij [Digitale checklisten](../probleemoplossing/programmablokken/digitale_checklijsten.md).

### Speciale childquery: Opsommen aangewezen bijlages

De variabele **:keysaangewezenbijlages** kan gebruikt worden om in een childquery een resultaat set te verkrijgen van kaarten uit tbcorrespondentie (geregistreerde documenten) die de gebruiker heeft aangewezen als bijlages. De variabele :keysaangewezenbijlages worden door OpenWave on the fly vervangen door een opsomming van de dnkeys uit tbcorrespondentie die als bijlage zijn aangewezen gescheiden door een komma en tussen twee haakjes.
De childquery is bijvoorbeeld als volgt gedefinieerd: _select dvfilenaam, dvkenmerk from vwfrmcorrespondentie where dnkey in :keysaangewezenbijlages_. OpenWave vervangt :keysaangewezenbijlages in de query door de opsomming zodat de geëvalueerde query bijvoorbeeld wordt: _select dvfilenaam, dvkenmerk from vwfrmcorrespondentie where dnkey in (1208231,1207836)_. Indien geen bijlages aangewezen dan wordt :keysaangewezenbijlages vervangen door (null).

De query kan dan ook zijn:

```sql
select
  'geen bijlage'
  where not exists
  (select 1 from vwfrmcorrespondentie where dnkey in (:keysaangewezenbijlages ))

 Union

select
  dvfilenaam
  from vwfrmcorrespondentie
  where dnkey in (:keysaangewezenbijlages)
```

## Invoegen tekstblokken op basis van een query-aanroep naar tbqueries

Er kan in het sjabloon een speciale vorm van merge-codering worden opgenomen die verwijst naar een kaart in tbqueries. In dat geval wordt die aangeroepen query geëvalueerd en het resultaat wordt op de bewuste plek in het sjabloon ingevoegd. Een dergelijke verwijzing ziet er als volgt uit:

- <%query(codevanquery)%>
- of <%query(codevanquery,:keyvergunning)%>
- of <%query(codevanquery,:keylocatie)%>
- of <%query(codevanquery,:keyinrichting)%>

Hier dus geen verwijzing naar een formquery of childquery bij het sjabloon, maar een verwijzing naar een kaart in tbqueries.

LET OP: De hier gebruikte merge-codering zal niet door de spellingchecker heenkomen, voor een goede werking zal het sjabloon daarom opgeslagen moeten zijn zonder spellingchecker!!!

Op grond van de eerste parameter (codevanquery in bovenstaand voorbeeld) wordt in tbqueries de kaart met dvcode = _codevanquery_ gezocht en de bijbehorende query geëvalueerd, waarbij de variabele {id} in de query wordt vervangen door de tweede parameter (indien aanwezig). Die tweede parameter moet één van de bovenvermelde query-variabelen zijn (dus :keyvergunning of :keylocatie of :keyinrichting) en is dus afhankelijk van de tabel van waaruit het sjabloon benaderd wordt.
Stel: de tabel is tbomgvergunning. Dan zal de tweede parameter :keyvergunning dus vervangen worden door de dnkey van tbomgvergunning van waaruit het document wordt gecreëerd.

Voorbeeld: de aangeroepen query met dvcode = _omgeving_tkstblk_1_ op grond van de aanroep _<%query(omgeving_tkstblk_1,:keyvergunning)%>_
kan de volgende inhoud hebben:

```sql
select case when (select dvsoortproc from vwfrmomgvergunningen where dnkeyomgvergunning = {id}) = 'M'
              then  'Dit is ten gevolge van artikel x van wet y'
              else ''::text end
```

Hetgeen wil zeggen dat indien het zaaktype van de omgevingszaak waar je op staat van het type M (melding) is, druk dan de tekst _Dit is ten gevolge van artikel x van wet y_ af. Anders, is het type anders dan M, druk dan niets af.

Datzelfde kan ook met hergebruik van blokken tekst door een verwijzing in de query naar tbtekstblokken:

```sql
select case when (select dvsoortproc from vwfrmomgvergunningen where dnkeyomgvergunning = {id}) = 'M'
              then  dvtekstblok
              else ''::text end
         from tbtekstblokken where lower(dvcode) = 'tkstblk_1'
```

Hetgeen wil zeggen dat indien het zaaktype van de omgevingszaak waar je op staat van het type M (melding) is, druk dan de waarde van de kolom dvtekstblok van de tabel tbtekstblokken af waarbij dvcode = _tkstblk_1_. Anders, is het type anders dan M, druk dan niets af.
Die kolom dvtekstblok kan gevuld zijn met een tekst van maximaal 4000 tekens.

In de tabel tbtekstblokken (beheertegel _Tekstblokken_) kunnen deze tekstblokken gedefinieerd worden die op bovenstaande wijze in meerdere sjablonen op conditie kunnen worden aangeroepen.
Zie ook: [Queries](./queries.md).

### Invoegen plaatje op basis van een query-aanroep naar tbqueries die verwijst naar tbimages

Er kan in het sjabloon een speciale vorm van merge-codering worden opgenomen die verwijst naar een kaart in tbqueries t.b.v. opnemen plaatjes. In dat geval wordt die aangeroepen query geëvalueerd en het resultaat van die query MOET verwijzen naar een unieke dvcode uit de tabel tbimages. Het plaatsje uit tbimages wordt op de bewuste plek in het sjabloon ingevoegd. Een dergelijke verwijzing ziet er als volgt uit:

- <%imagequery(codevanquery)%>
- of <%imagequery(codevanquery,:keyvergunning)%>
- of <%imagequery(codevanquery,:keylocatie)%>
- of <%imagequery(codevanquery,:keyinrichting)%>

LET OP: De hier gebruikte merge-codering zal niet door de spellingchecker heenkomen, voor een goede werking zal het sjabloon daarom opgeslagen moeten zijn zonder spellingchecker!!!

Op grond van de eerste parameter (codevanquery in bovenstaand voorbeeld) wordt in tbqueries de kaart met dvcode = _codevanquery_ gezocht en de bijbehorende query geëvalueerd, waarbij de variabele {id} in de query wordt vervangen door de tweede parameter (indien aanwezig). Die tweede parameter moet één van de bovenvermelde query-variabelen zijn (dus :keyvergunning of :keylocatie of :keyinrichting) en is dus afhankelijk van de tabel van waaruit het sjabloon benaderd wordt.

Een voorbeeld van een query met dvcode = _image_handtekening_ bij de sjabloonaanroep <%imagequery(image_handtekening,:keyvergunning)%>

```sql
select
   case when dvgemeenteid = '0363' then 'HandtekeningY'
        else 'HandtekeningX'
  end
  from vwfrmomgvergunningen
  where dnkeyomgvergunning = {id}
```

De uitkomst van deze query waarbij _{id}_ eerst is gesubstitueerd door de dnkey van de omgevingszaak levert dus een verwijzing naar een specifieke dvcode van tbimages op (beheer), namelijk of wel de image met dvcode = _HandtekeningY_ ofwel dvcode = _HandtekeningX_. Aldaar moeten de twee gewenste plaatje geüpload zijn EN voorzien van de juiste hoogte en breedte in pixels.

Als er geen case when nodig is, dus als een bepaald plaatje er altijd onvoorwaardelijk in moet, dan is _<%imagequery(codevanquery)%>_ voldoende, en in die codevanquery staat dan bijvoorbeeld: _select 'ABC'_ als ABC de naam van de image is.

LET OP: de <%imagequery(xxxxx)%> moet in het MS-Word-sjabloon in de hoofdtekst staan, dus niet in een tekstblok of tabel of header of footer.
LET OP 2: De regelafstand van het onderdeel <%imagequery …%> moet op ‘Enkel’ moet staan.

## Tonen Wave briefnummer

(indien instelling _Sectie: Documenten, Item: WaveBriefNummer_ is aangevinkt)

Indien gewenst kan er met de juiste instellingen een uniek briefnummer door OpenWave gecreëerd worden bij aanmaken van de brief. Als je dit nummer in het sjabloon wilt tonen dan kan dit door in het sjabloon de verwijzing <%teller%> te zetten op de plek waar je het briefnummer wilt tonen.

Voorbeeld: stel de instellingen zijn als volgt WaveBriefnummer staat aan, _Getal1_ = 78, _Getal2_ = 5 en _Tekst_ = 'OW'. Het unieke briefnummer waarmee <%teller%> in het document vervangen zal worden is 'OW00079'.

Indien _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft, dan wordt het gecreëerde document op basis van dit sjabloon automatisch op geslagen in de geregistreerde documenten (tbcorrespondentie), waarbij de kolom dvbriefcode de waarde van deze teller krijgt (ongeacht of deze teller in het sjabloon is opgenomen).

## Tonen externe documentidentifier

De string <%ExtDocIdent%> (let op kamelennotatie) zal worden vervangen door de externe documentidentifier die verkregen wordt door een Stuf Zaak/DMS genereerdocumentidentificatie-bericht. Alleen van toepassing indien automatische opslag in een DMS via stufzaak/DMS. Wanneer OpenWave geen externe documentidentifier kan bemachtigen, wordt de string <%ExtDocIdent%> vervangen door een lege string.

## Tonen gecrypte versie van een kolomwaarde

Verder kan de encryptiemethode worden aangeroepen vanuit het documentsjabloon. De string <%strEncrypt(:columnname)%> in een sjabloon wordt bij het creëren van een document als volgt geïnterpreteerd. Het programma zal columnname interpreteren als een kolomnaam uit de hoofdtabel van het sjabloon. De waarde van die kolom wordt gecrypt volgens de ingestelde methode (zie: [2-way encryptie van externe wachtwoorden](./2way_encryptie_externe_wachtwoorden)) en deze gecrypte waarde wordt in het document opgenomen op de betreffende plaats. Voorbeeld: <%strEncrypt(:dnkey.md)%>.

## Sjabloon-parameters

De substrings in de formqueries ingesloten door %-tekens (bijvoorbeeld %datumvanaf%) heten parameters. Deze worden bij het uitvoeren van het SQL-statement automatisch vervangen door een bedoelde waarde. Hoe dat gebeurt wordt gedefinieerd met de kolommen van de tabel tbdocparameters.

Uitzondering hierop zijn de hierboven behandelde strings <%query(codevanquery)%>, <%iamgequery(codevanquery)%>, <%Teller%> en <%strEncrypt(:dnkey)%>. Elke query kan 0 of meer parameters hebben.

### Parameterkolommen

- In de kolom **parameternaam** (dvparameter) staat de naam van de parameter precies zoals die in de querie(s) van het bijbehorende sjabloon staat, maar dan zonder %-tekens. In de parameternamen mogen alleen letters of cijfers voorkomen of een underscore. Dus geen spaties of slashes/backslashes e.d..
- **Invulsoort** (dvinvulsoort). Moet ingevuld worden. Er zijn drie mogelijkheden:
  - (A)utomatisch. Dit wil zeggen dat Wave de parameter onder water automatisch vervangt met de actieve waarde van de kolom default waarde
  - (I)nvoer. Invoer wil zeggen dat de gebruiker de gelegenheid krijgt om de parameter te vervangen door een waarde die hij zelf opgeeft met als default de actieve waarde van de kolom default waarde
  - (L)ijst. Lijst wil zeggen dat de gebruiker de te vervangen parameterwaarde kan kiezen uit een lijst in een dropdown-box alvorens het document wordt gegenereerd. De lijst wordt samengesteld door de query die wordt opgegeven bij _lijst query_ (zie opmerkingen aldaar).
- In de kolom **label** (dvlabel) kan hier het label behorende bij de te maken editbox of dropdownlist worden ingevoerd indien de Invulsoort = (I)nvoer of (L)ijst.
- **Type** (dvinvoerobject). Type geldt alleen wanneer de InvulSoort = (I)nvoer of (L)ijst.
  - Indien Invulsoort is (I)nvoer dan bepaalt het type het masker voor de in te vullen waarden. De volgende conventies gelden indien gevuld:
    - STRING (tekst): Het programma toont een normale editbox om de waarde in te voeren voor zowel cijfers als letters. Dus ook wanneer het om een in te voeren numerieke waarde gaat (zoals een bedrag) kan als type toch string worden gekozen
    - DATUM: Laat datum kiezen uit een kalender
    - INTEGER (getal): Het programma toont een normale editbox om de waarde in te voeren voor een getal.
  - Indien Invulsoort is (L)ijst dan geldt dat als de waarde van eerste kolom van de result-dataset van de query_bij_soort_is_lijst (zie hieronder) een:
    - Integer of float is dan moet het type leeg zijn (maar mag ook string zijn)
    - String is dan moet bij type ook een string worden gekozen
    - Datum is dan moet bij het type ook een datum worden gekozen.
- **Query_bij_soort_is_lijst** (dvlijstquery). Geldt alleen wanneer de Invulsoort = (L)ijst. In geval van (L)ijst komt het resultaat van de hier opgegeven query als dropdownlijst alvorens de rapportage wordt gestart. Daarbij geldt dat de waarde van eerste kolom van de result-dataset van de query als de te vervangen parameter wordt beschouwd (maar niet zichtbaar in de dropdownlijst). De query mag maar twee kolommen bevatten genaamd id en omschrijving. Voorbeeld: _SELECT DvCode id, DvOmschrijving omschrijving from TbMedewerkers where ddvervaldatum is null order by omschrijving_. Het veld dat als id wordt omschreven, komt in het document te staan. Dus in bovenstaand voorbeeld komt het veld DvCode in het document, met _SELECT DvOmschrijving id, DvCode omschrijving from TbMedewerkers where ddvervaldatum is null order by omschrijving_ komt het veld DvOmschrijving in het document en kunt u kiezen uit de codes. De queries die hier opgegeven kunnen worden kunnen verwijzen naar elke tabel of view van het database schema van Wave.
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
- **Vaste Defaultwaarde** (dvdefaultvast). Een vaste default waarde bij bij Invulsoort = (A)utomatisch en bij (I)nvoer en (L)ijst. Indien Lijst (waarbij de default waarde dus verwijst naar een bepaalde regel van het dropdownlijstje bestaande uit de kolommen id en omschrijving), dan geldt bij afspraak dat de id en de omschrijving van deze default waarde gescheiden moeten zijn met een puntkomma. Is er geen puntkomma in de default dan gaat OpenWave er vanuit dat de default waarde op zowel de id als de omschrijving van toepassing is. Stel de dropdownlijst is gedefinieerd als _select '1' id, 'Teamleider - standaard' omschrijving union select '3' id, 'Afdelingshoofd' omschrijving_ dan kan de vaste default waarde gedefinieerd zijn als _3;Afdelingshoofd_.

### Voorbeeld gebruik verschillende soorten (types) parameters

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
  WHERE DNKEYOMGVERGUNNING = :keyvergunning
```

LET HIER OP DAT:

- een integer of string inputparameter zonder quootjes of extra functie in de query kan worden opgenomen: zoals %Zomaareeninteger%
- een floatparameter alleen ingebracht kan worden als type string en dat die dan gecast wordt naar float
- een datumparameter gecast moet worden naar datum met bijv. to_date functie waarbij de ingevoerde datum wordt aangeleverd als yyyy-mm-dd.

Er zijn dus 5 invoerparameters:

![](../img/applicatiebeheer/instellen_inrichten/invoerparameters2.png){ class="media" loading="lazy" alt="" width="600" }

Dat resulteert bij het genereren van het document tot een invoerscherm:

![](../img/applicatiebeheer/instellen_inrichten/parameters2.png){ class="media" loading="lazy" alt="" width="400" }

En het te genereren document ziet er dan zo uit:

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

De inhoud van de kolommen van de formqueries en childqueries kan ook bestaan uit een verwijzing naar een query in de beheertabel tbqueries. Zie: [Queries](./queries.md)

Hierdoor hoeft een query die in meerdere sjablonen gebruikt wordt maar eenmalig te worden gedefinieerd. De opmaak van de sjablonen wijzigt hierdoor niet.

formmquery_1 is bijvoorbeeld:

select dvzaakcode, dvaanvraagnaam from tbomgvergunning where dnkey = :keyvergunning
en formquery_2 is bijvootrbeeld

select dvbedrijfsnaam, dvachternaam from tbcontactadressen where dnkey = :keyadres
Deze twee select statements kunnen nu vervangen worden door de volgende:

De inhoud van formquery_1 wordt dan

%query(sjabloon_zaakgegevens,:keyvergunning)%
en die van formquery_2 wordt dan

%query(sjabloon_geadresseerdegegevens,:keyadres)%

In de tabel tbqueries dienen vervolgens twee kaarten aangemaakt te worden:

Eén met de naam _sjabloon_zaakgegevens_ met de inhoud:

select dvzaakcode, dvaanvraagnaam from tbomgvergunning where dnkey = {id}
en één met de naam _sjabloon_geadresseerdegegevens_ met als inhoud

select dvbedrijfsnaam, dvachternaam from tbcontactadressen where dnkey = {id}
