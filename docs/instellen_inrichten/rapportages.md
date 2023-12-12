# Rapportages

Portal beheerportaal-Nieuw. Tegel Rapport-definitie.

API(s):

  - getReportGroupList: [https://api.open-wave.nl/RemMethods/getRemMethod/391](https://api.open-wave.nl/RemMethods/getRemMethod/391.md)
    - getReportGroupDetail: [https://api.open-wave.nl/RemMethods/getRemMethod/392](https://api.open-wave.nl/RemMethods/getRemMethod/392.md)
    - getReportList: [https://api.open-wave.nl/RemMethods/getRemMethod/393](https://api.open-wave.nl/RemMethods/getRemMethod/393.md)
    - getReportDetail: [https://api.open-wave.nl/RemMethods/getRemMethod/394](https://api.open-wave.nl/RemMethods/getRemMethod/394.md)
    - getReportParamsList: [https://api.open-wave.nl/RemMethods/getRemMethod/395](https://api.open-wave.nl/RemMethods/getRemMethod/395.md)
    - getReportParamsDetail: [https://api.open-wave.nl/RemMethods/getRemMethod/396](https://api.open-wave.nl/RemMethods/getRemMethod/396.md)
    - getMyReportGroupList: [https://api.open-wave.nl/RemMethods/getRemMethod/401](https://api.open-wave.nl/RemMethods/getRemMethod/401.md)
    - getMyReportList: [https://api.open-wave.nl/RemMethods/getRemMethod/404](https://api.open-wave.nl/RemMethods/getRemMethod/404.md)

Screenidentifiers:

  - MDLC_getReportGroupList.xml (tbrapportgroep)
  - MDDC_getReportGroupDetail.xml (tbrapportgroep)
  - MDLC_getReportList.xml (vwfrmreports)
  - MDDC_getReportDetail.xml (vwfrmreports)
  - MDLC_getReportParamsList.xml (tbrapportparameters)
  - MDDC_getReportParamsDetail.xml (tbrapportprameters)

## Definiëren van rapportages

De inlogger moet beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99 (of hoger). Alle kolommen en knoppen op de schermen zijn dan toegankelijk.

## Rapportgroepen

Rapportages kunnen worden ingedeeld in groepen, waarbij een groep voorzien moet worden van een moduleletter.

  - A: Algemeen
  - M: Management
  - W: Omgeving
  - O: APV/Overig
  - H: Handhaving
  - I: Info
  - E: Milieu/gebruik (gedeeltelijk pre-wabo) + Inrichtingen/Vestigingen/Objectregistratie
  - C: Horeca
  - B: Bouw/Sloop (pre-wabo)

Deze moduleletters kunnen gebruikt worden om tegels te definiëren waarmee door een gebruiker een doorkieslijst van rapportagegroepen kan worden opgeroepen die een bepaalde moduleletter gemeen hebben. Bijvoorbeeld een portaltegel met action: *getFlexList(myReportGroupList,nil,nil,E)* toont een lijst van rapportagegroepen waarvoor geldt:

  - dat zij de moduleletter *E* gemeen hebben
  - ÉN waarvoor bovendien geldt dat de gebruiker die de tegel aanklikt op minimaal één van de onderliggende rapporten kijkrechten heeft: het rapportniveau van de medewerkerskaart van die gebruiker moet groter of gelijk zijn aan het vereist rapportageniveau bij de rapportdefinitie
  - EN die gebruiker moet een *Interne medewerker* zijn.

*getFlexList(myReportGroupList)* toont een doorkieslijst van alle rapportagegroepen (met dezelfde autorisatie-restrictie).

Tegels met rapportgroepen kunnen makkelijk worden ingedeeld in het daartoe bestemde portaal [Rapportageportaal](/docs/probleemoplossing/portalen_en_moduleschermen/rapportageportaal.md). Maar ze kunnen ook op andere portalen worden geplaatst…

Het doorklikken op een item van een groepslijst door de gebruiker opent een lijst van rapporten die de gebruiker kan openen (getMyreportList).

### Rapportdefinitie (rapportenlijst)

Per rapportgroep kunnen rapporten verwijderd worden (inclusief parameters en de verwijzing in screencolumns), nieuw aangemaakt en gekopieerd. Bij het maken van een kopie worden èn de parameters èn - indien van toepassing - de kaart in screencolumns mee gekopieerd.

## Rapportdefinitie (detailscherm)

### Kolommen

  - De kolom **ID** (dnkey) geeft de automatisch gegenereerde primary key weer van de rapportage in de tabel tbrapporten. Deze ID wordt gebruikt:
    - om tegels te definiëren - op wat voor portaal dan ook -, waarmee de gebruiker direct een rapportage kan starten. De action op een degelijke portaltegel is in basis: *startWizard(startReport,x)* waarbij die x staat voor een ID van een rapport (zie ook verderop voor meer mogelijkheden)
    - als *identifier rapport* in tbscreencolumns (beheertegel *Schermkolomdefinitie*) voor aanpassingen op de lay-out van het te tonen rapport die niet met de SQL alleen te maken zijn.
  - De **rapportagenaam** (dvnaam) moet gevuld zijn. **Let op**: in de omschrijving mogen geen komma's voorkomen!
  - Een gebruiker van rapportages ziet alleen rapporten waarvan het **vereist rapportageniveau** (dnvereistniveau) kleiner of gelijk is dan de medewerker eigenschap rapportageniveau (beheertegel *Medewerkers*).
  - Het aanvinken van de kolom **WMS** (dlwms) betekent dat de rapportage bedoeld is om als WMS_laag gepubliceerd te worden. Zie: [Rapportage als WMS-laag](/docs/instellen_inrichten/rapportage-publiceren_als_wms-laag.md).
  - De kolom **EPSG** (dvwms_epsg)kan vooralsnog alleen gevuld worden met 28992 (rijksdriehoek). Is dus alleen van belang als WMS aangevinkt is.
  - De kolom **Kopregels niet in Excel-export**. Indien aangevinkt worden de kopregels van het lijstscherm waarin het rapport wordt getoond niet meegenomen bij het exporteren naar Excel file (knopje linksonder op dat resultaatscherm). Het gaat hier niet om de kolom labels.
  - In de kolom **SQL-1** (dvquery) moet een valide SQL statement komen die de rapportage definieert beginnend met 'Select'. Daarbij geldt:
    - dat er GEEN commentaar in mag staan zoals: /*comment kan niet*/
    - dat een kolomnaam of kolom-alias alleen letters uit letters of cijfers of underscores mag bestaan. Dus geen spaties of slashes/backslashes e.d.
    - dat de alias niet ingepakt mag zijn met dubbele quootjes!!!
    - dat de substring %where% vervangen zal worden door de inhoud van SQL-2 (zo kan de query uit 8000 tekens bestaan)
    - dat Open_Wave functies gebruikt kunnen worden in de SQL zie [OpenWave database functies](/docs/instellen_inrichten/openwave_database-functies.md)
    - dat substrings met het masker %xxxx% anders dan %where% worden beschouwd als parameternamen (zie verderop). Het programma zal bij uitvoer van het rapport deze parameternamen vervangen door hun bedoelde waarde.
  - De kolom **SQL-2** (dvwhere) vervangt de substring %where% uit SQL-1. Is dus nodig wanneer het totale SQL-statement groter is dan de 4000 tekens die in SQL-1 passen. Dezelfde opmerkingen als hierboven bij SQL-1 gelden ook voor SQL-2 met uitzondering van de vervanging van de substring %where%.
  - De kolom **Action** (dvaction) kan gevuld worden met een action die wordt uitgevoerd op het moment dat de gebruiker dubbelklikt op een regel van een geopend rapport. Meest voor de hand liggende mogelijkheid is een doorverwijzing naar een bepaald zaak- of inrichtingsportaal dat correspondeert met de geselecteerde regel. Of naar een specifiek detailscherm. Dergelijke actions moeten als volgt gedefinieerd worden:
    - Portaal Inrichting: opentabpage(#inrichtingdetail/{id})
    - Portaal Omgeving: opentabpage(#omgevingdetail/{id})
    - Portaal Handhaving: opentabpage(#handhavingdetail/{id})
    - Portaal APV/Overig: opentabpage(#apvoverigdetail/{id})
    - Portaal Milieu/Gebruik: opentabpage(#milieugebruikdetail/{id})
    - Detailscherm Omgeving: getFlexDetail(TbOmgvergunning,{id},W)
    - Detailscherm Inrichting: getFlexDetail(TbMilinrichtingen,{id},V)
    - Detailscherm APV/Overig: getFlexDetail(Tbovvergunningen,{id},O)
    - Detailscherm Handhavingen: getFlexDetail(Tbhandhavingen,{id},H)
    - Detailscherm Milieu/Gebruik: getFlexDetail(Tbmilvergunningen,{id},E)
    - Ook rapport-parameters kunnen in de action gebruikt worden bijv. getFlexList(tbadviezen,tbovvergunningen,{id},%AofO%,O). Hier wordt de parameternaam *AofO* vervangen door de parameterwaarde (in dit geval hopelijk een A of een O).

Wanneer de action samengesteld moet worden op grond van de inhoud van regel (dus de action kan per regel verschillend zijn) kan een extra kolom in het rapport worden opgenomen, waarin die gewenste action wordt gedefinieerd. Bijvoorbeeld een kolom *DVgaNaarPortal* die in de rapportdefinitie de inhoud krijgt van bijv. 'opentabpage(#omgevingdetail/' | | dnkey | | ')' DvgaNaarPortal. In de editbox action moet dan komen te staan (bij afspraak) **column:**DVgaNaarPortal. Het programma weet dan dat de action voor dubbel klikken op de rapportregel gedefinieerd is in de kolom *DVgaNaarPortal*.

  -  De kolom **kolomnaam van keywaarde t.b.v. action** (dvkeykolom) geeft aan welke achterliggende waarde van welke kolomnaam uit de rapportage gebruikt moet worden door het programma om de variabele {id} uit de action te vervangen met de primary key van de module.

Zie verdere informatie over action: [Actions](/docs/instellen_inrichten/actions.md).

#### Triggers

In het menu opties rechtsboven. Zie ook [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie/README.md):

  - Maak schermdefinitie:
    - Zichtbaar en enabled indien er GEEN kaart bestaat in tbscreencolumns (beheertegel *Schermkolomdefinitie*) met *identifier rapport* (dnreportkey) = ID van het rapport. De trigger maakt een schermkolomdefinitie voor het rapport op basis van de SQL en opent deze pagina ter aanpassing.
  - Naar schermdefinitie:
    - Zichtbaar en enabled indien er WEL een kaart bestaat in tbscreencolumns (beheertegel *Schermkolomdefinitie*) met *identifier rapport* (dnreportkey) = ID van het rapport. De trigger opent de betreffende pagina.
  - Verwijder schermdefinitie:
    - Zichtbaar en enabled indien er WEL een kaart bestaat in tbscreencolumns (beheertegel *Schermkolomdefinitie*) met identifier rapport (dnreportkey) = ID van het rapport. De trigger verwijdert deze kaart in tbsceencolumns met als gevolg dat het rapport er in de defaultopmaak (alleen SQL-info) uitziet

Knoppen linksonder:

  - Met de knop **controleer SQL-statements** worden de gevulde query-kolommen gevalideerd. De betreffende kolomnamen worden zichtbaar met een groen bolletje indien ok en een rood bolletje indien het statement niet valide is.

### Parameters

De substrings in de SQL-1 of SQL-2 ingesloten door %-tekens (bijvoorbeeld %datumvanaf%) heten parameters. Deze worden bij het uitvoeren van het SQL-statement automatisch vervangen door een bedoelde waarde. Hoe dat gebeurt wordt gedefinieerd met de kolommen van de tabel tbparameters.

Een rapport kan 0 of meer parameters hebben.

Wanneer in de SQL van het rapport meerdere keren dezelfde parameter wordt aangeroepen zoals in onderstaand voorbeeld:

*select dvaanvraagnaam from tbomgvergunning where (ddbesluitdatum > %invoerdatum%) or (ddingetrokken > %invoerdatum%)* zal het programma bij het starten van het rapport, maar één keer om invoer vragen.

### Kolommen

  - In de kolom **parameternaam** (dvparameter) staat de naam van de parameter precies zoals die in de SQL-1 of SQL-2 kolom van het bijbehorende rapport staat, maar dan zonder %-tekens. In de parameternamen mogen alleen letters of cijfers voorkomen of een underscore. Dus geen spaties of slashes/backslashes e.d..
  - **Invulsoort** (dvinvulsoort). Moet ingevuld worden. Er zijn drie mogelijkheden:
    - (A)utomatisch. Dit wil zeggen dat Wave de parameter onder water automatisch vervangt met de actieve waarde van de kolom default waarde.
    - (I)nvoer. Invoer wil zeggen dat de gebruiker de gelegenheid krijgt om de parameter te vervangen door een waarde die hij zelf opgeeft met als default de actieve waarde van de kolom default waarde.
    - (L)ijst. Lijst wil zeggen dat de gebruiker de te vervangen parameterwaarde kan kiezen uit een lijst in een dropdown-box alvorens de rapportage gestart wordt. De lijst wordt samengesteld door de query die wordt opgegeven bij *lijst query* (zie opmerkingen aldaar).
  - In de kolom **label** (dvlabel) kan hier het label behorende bij de te maken editbox of dropdownlist worden ingevoerd indien de Invulsoort = (I)nvoer of (L)ijst.
  - **Type** (dvinvoerobject). Type geldt alleen wanneer de InvulSoort = (I)nvoer of (L)ijst.
    - Indien Invulsoort is (I)nvoer dan bepaalt het type het masker voor de in te vullen waarden. De volgende conventies gelden indien gevuld:
      - STRING (tekst): Het programma toont een normale editbox om de waarde in te voeren voor zowel cijfers als letters. Dus ook wanneer het om een in te voeren numerieke waarde gaat (zoals een bedrag) kan als type toch string worden gekozen.
      - DATUM: Laat datum kiezen uit een kalender.
      - INTEGER (getal): Het programma toont een normale editbox om de waarde in te voeren voor een getal.
    - Indien Invulsoort is (L)ijst dan geldt dat als de waarde van eerste kolom van de result-dataset van de query_bij_soort_is_lijst (zie hieronder) een
      - Integer of float is dan moet het type leeg zijn (maar mag ook string zijn)
      - String is dan moet bij type ook een string worden gekozen
      - Datum is dan moet bij het type ook een datum worden gekozen.
  - **Query_bij_soort_is_lijst** (dvlijstquery). Geldt alleen wanneer de Invulsoort = (L)ijst. In geval van (L)ijst komt het resultaat van de hier opgegeven query als dropdownlist alvorens de rapportage wordt gestart. Daarbij geldt dat de waarde van eerste kolom van de result-dataset van de query als de te vervangen parameter wordt beschouwd (maar niet zichtbaar in de dropdownlist). De tweede kolom vormt dus het zichtbare deel van de dropdownlist. Voorbeeld: *SELECT DvCode, DvOmschrijving from TbDossierverblijf order by DvOmschrijving*. Wilt u meer velden zien dan (in dit voorbeeld) Dvomschrijving, dan moet u die met de bekende | | aan elkaar plakken.  (N.B. met een alias). Dus bv *DVCODE, dvcode| |'-'| |DVOMSCHRIJVING* omschrijving. De query's die hier opgegeven kunnen worden kunnen verwijzen naar elke tabel of view van het database schema van OpenWave.
  - **Inputvolgordenummer** (dnregel). Geldt voor invulsoort (L)ijst of (I)nvoer. Hiermee kunt u de plek beïnvloeden van de editbox of lijst wanneer er meerdere parameters zijn. Mag leeg gelaten worden, maar dan is de volgorde van de gevraagde invoer willekeurig.
  - **Functie Defaultwaarde** (dvdefaultwaarde). Een – bij afspraak – geldende typering wat de standaard waarde moet zijn bij Invulsoort = (A)utomatisch en bij (I)nvoer De mogelijkheden zijn:
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
    - Huidige Gebruiker (Cinlogger) TbMedewerkers.DvCode van persoon die de rapportage draait
    - Identifier van powerportal (nportalid). Kan alleen gebruikt worden bij rapportages die gestart worden vanuit een zaakportaal of een inrichtingsportaal. De identifier is dan de primary key van de betreffende module voor dat portaal (zie voorbeeld hieronder bij *rapportage direct vanaf tegel starten*).
  - **Vaste Defaultwaarde** (dvdefaultvast). Een vaste default waarde bij bij Invulsoort = (A)utomatisch en bij (I)nvoer en (L)ijst. Indien Lijst (waarbij de default waarde dus verwijst naar een bepaalde regel van het dropdownlijstje bestaande uit de kolommen id en omschrijving), dan geldt bij afspraak dat de id en de omschrijving van deze default waarde gescheiden moeten zijn met een puntkomma. Is er geen puntkomma in de default dan gaat OpenWave er vanuit dat de default waarde op zowel de id als de omschrijving van toepassing is. Stel de drowplijst is gedefinieerd als *select '1' id, 'Teamleider - standaard' omschrijving union select '3' id , 'Afdelingshoofd' omschrijving* dan kan de vaste default waarde gedefinieerd zijn als *3;Afdelingshoofd*.
  - **Afwijkende invoerbreedte** (dninvoerwidth). Een invoer kolom type datum is standaard 93 pixels breed, een getal is 100 pixels en een string 500. Hier kan een afwijkende waarde worden ingevoerd.
  - **Afwijkende breedte dropdownlijst** (dndropdownwidth) Een invoer kolom type keuzelijst is standaard 150 pixels breed. Hier kan een afwijkende waarde worden ingevoerd.

### Overig

#### OpenWave database functies

OpenWave heeft zelf een aantal functies op de database gedefinieerd - zoals fn_ddmaandjjjj() -  die gebruikt kunnen worden in allerlei query's.
Zie: [OpenWave database functies](/docs/instellen_inrichten/openwave_database-functies.md).

#### Rapport export naar Excel

De rapportages kunnen worden geëxporteerd naar Excel. Dit kan in alleen in xlsx formaat.

> [!WARNING]
> **LET OP:** In de rapportnaam mogen geen komma's voorkomen. Indien er geen scherminformatie aan het rapport is gekoppeld zullen alle kolommen van het rapport standaard type Tekst hebben: ook in Excel.

Met scherminformatie kan bijvoorbeeld een datumkolom (wavetype datum) in het rapport ook door Excel als datumkolom worden opgepakt (met default excelformat: dd-mm-jjjj). De kolommen met numerieke waardes worden door Excel als Getal gezien indien het wavetype float of integer is.

Indien de kolom met numerieke waardes is gedefinieerd als wavetype string (bijvoorbeeld door de functie fn_bedrag) dan kan OpenWave deze toch als Excelgetal doorgeven mits aan de schermkolomdefinitie wordt toegevoegd de tag `<exceltype>float</exceltype>`.

Het gewenste formaat kan - en dit geldt overigens voor alle kolommen - doorgegeven worden met de tag `<excelformat>#,#0.00</excelformat>`. Het voorbeeld >#,#0.00 is van toepassing op een Getal, waarbij de decimaalscheidingstekens (met twee decimalen) als een komma moeten worden gerepresenteerd en een punt verwacht wordt voor de duizendtallen. Het format wordt dus door Excel gedefinieerd (Excel geeft ook foutmelding als dit niet goed is gedaan).

Zie [Scherminformatie voor lijstschermen en (dus ook) rapportages](/docs/instellen_inrichten/schermdefinitie/scherminformatie_voor_lijstschermen_en_rapportages.md) voor de juiste volgordeplek van de tags exceltype en excelformat binnen een schermkolomdefinitie.

#### Rapportage direct vanaf tegel starten

De action bij de portal-tegeldefinitie kan zijn *startWizard(startReport,x)* waarbij die x staat voor een ID van een rapport.

Het kan ook iets ingewikkelder wanneer een rapportage is gedefinieerd die gegevens opsomt die horen bij een specifieke zaak die op dat moment actief is. De dynamische primary key van een zaak- of inrichtingsportaal kan dan als parameter in het rapport ingebracht worden (invulsoort = automatisch) waarbij de parameter als defaultwaarde *nportalid* krijgt.

De actionaanroep op de tegel is in dat geval: startWizard(startReport,x,{id}) waarbij die x wederom staat voor een ID van een rapport en waarbij {id} vervangen wordt door de primary key van het portaal waarvandaan de rapportage wordt opgeroepen en die waarde wordt vervolgens gebruikt om de rapport-parameter van type *Identifier van powerportal* in de SQL-1 of SQL-2 van de query te vervangen.

Zie onderstaand uitgewerkt voorbeeld.

#### Voorbeeld

Onderstaand voorbeeld is een rapport dat lopende verleende APV/Overige vergunningen van soort HOR of EXP of SLU of SPE of TER opsomt bij een inrichting.
Het rapport wordt met een klik op de tegel gestart op het portaal van een inrichting:

![](/img/applicatiebeheer/instellen_inrichting/acthortegel.png){ class="media" loading="lazy" alt="" width="300" }

Klikken op de tegel (mits geautoriseerd) laat de rapportagelijst zien:

![](/img/applicatiebeheer/instellen_inrichting/acthorlijst.png){ class="media" loading="lazy" alt="" width="500" }

**De rapportdefinitie**
Eerst kolom SQL-1:

```sql
select
    dnkeyovvergunning key,
    dvovvergunningsnr zaakcode,
    dvsoortovvergunning soort,
    dvovomschrijving omschrjving
  from vwfrmovvergunningen
    where instr('HOREXPSLUSPETER',upper(trim(dvcodesoortovverg))) > 0
    and dlverleend = 'T'
    and ddnaverlingetrokken is null
    and (ddvervallen is null or ddvervallen > fn_vandaag(0))
    and (ddgeldigtotmet is null or ddgeldigtotmet > fn_vandaag(0))
    and %where%
  order by zaakcode
```

dam kolom SQL-2:

```sql
dnkeymilinrichtingen = %portalid%
```

**Action in rapportdefinitie**

Omdat in de resultset van de SQL ook de primary key van de APV/Overige is opgenomen onder de alias 'key' kan de gebruiker ook doorklikken naar de detailschermen van die APV/Overige zaken in de lijst. Dat komt door de action definitie bij het rapport:

![](/img/applicatiebeheer/instellen_inrichting/rapportaction.png){ class="media" loading="lazy" alt="" width="600" }

**De rapportparameter**

De parameter %portalid% uit SQL-2 is als volgt gedefinieerd:

![](/img/applicatiebeheer/instellen_inrichting/rapportparameter.png){ class="media" loading="lazy" alt="" width="600" }

(de kolom label is hier overigens zinloos ingevuld, want het is een automatische parameter)

**Tegeldefinitie**

Stel dat de dnkey van de rapportdefinitie (kolom ID) de waarde 3041 heeft dan krijgt de tegel die geplaatst wordt op het inrichtingsportaal de actionaanroep: startWizard(startReport,3041,{id}).

![](/img/applicatiebeheer/instellen_inrichting/acthorportaltile.png){ class="media" loading="lazy" alt="" width="600" }

De tegel nog wel even toekennen aan de gewenste personen…. en het rapportniveau van de medewerkerskaart van die personen moet nog steeds groter of gelijk zijn aan het vereist rapportageniveau bij de rapportdefinitie EN die personen moeten *Interne medewerkers* zijn.

**Berekening aantal op tegel**

Het opschrift op de tegel in het voorbeeld toont het aantal items dat de rapportage geeft voor de actieve inrichting (Aantal:5).
Bij de tegeldefinitie wordt hiertoe verwezen naar de query met code *inrichting_horeca*.
Die query lijkt natuurlijk veel op die van het rapport:

```sql
select 'Aantal: ' | | count(*)
  from vwfrmovvergunningen
  where instr('HOREXPSLUSPETER',upper(trim(dvcodesoortovverg))) > 0
  and dlverleend = 'T'
  and ddnaverlingetrokken is null
  and (ddvervallen is null or ddvervallen > fn_vandaag(0))
  and (ddgeldigtotmet is null or ddgeldigtotmet > fn_vandaag(0))
  and dnkeymilinrichtingen = {id}
```

