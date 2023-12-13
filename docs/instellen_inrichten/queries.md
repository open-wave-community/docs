# Queries

Portaal beheerportaal-Nieuw. Tegel queries.

Screenidentifiers:

- MDLC_getQueriesList.xml
- MDDC_getQueryDetail.xml

De SQL-statements van deze tabel worden gebruikt:

- om opschriften te genereren voor tegels
- om bepaalde scherminformatie in detailschermen per blok (on)zichtbaar te maken
- om inhoud van schermattributen in detailschermen zoals labels of actions, context-afhankelijk te maken
- om blokken tekst in te voegen in een document gemaakt vanuit een sjabloon.
- om resultsets te genereren ten behoeve van merge bij documentsjablonen

Voor querybeheer moet de inlogger beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99 (of hoger).
Alle kolommen en knoppen zijn dan toegankelijk.

Een aantal query's in deze tabel is noodzakelijk voor het programma. Dit zijn de query's die het vakje systeem aangevinkt hebben staan.
De waarde van het systeem-aanvinkvakje kan niet worden gewijzigd met OpenWave. Aangevinkt betekent dat bij database-updates van OpenWave de bijbehorende query gewijzigd kan worden. Door gebruikers aangemaakte query's (met systeem = niet aangevinkt) zullen bij updates onaangetast blijven.

Aan de query worden de volgende eisen gesteld:

- het resultaat van een query (dus de evaluatie van het select-statement) mag maar uit één kolom bestaan
- EN de query moet met 'select' beginnen
- EN er mag GEEN puntkomma (';') in voorkomen (vanwege het gevaar voor SQL-injectie).

Een voorbeeld van een query is:

```sql
select
  'Aantal: ' | | count(*)
  from vwfrmomgorkestrator_adv
  where trim(dvadviesbehandelaar) = trim(:keyaccount)
```

Deze query geeft het aantal openstaande adviezen, waarvoor de inlogger de behandelaar is.

Bij query's kunnen twee variabelen worden gebruikt:

- :keyaccount zal worden vervangen door tbmedewerkers.dvcode van de inlogger
- {id} wordt:
  - vervangen met de dnkey van tbomgvergunning of tbhandhavingen of tbmilinrichtingen of tbovvergunningen of tbmilvergunningen wanneer de query gebruikt wordt op een zaak- of inrichtingsportaal als tegelopschrift
  - vervangen met de dnkey van de kaart die hoort bij de basistabel van het detailscherm van waaruit de query wordt aangeroepen als onderdeel van schermattributen bij de schermkolomdefinitie
  - vervangen met de dnkey van de kaart van de tabel waaruit een document wordt gecreëerd.

OpenWave heeft zelf een aantal functies op de database gedefinieerd - zoals fn_ddmaandjjjj() - die gebruikt kunnen worden in allerlei queries. Zie: [OpenWave database functies](/instellen_inrichten/openwave_database-functies.md).

De query heeft in de kolom dvcode een unieke, maar editbare, identifier, waarmee de query kan worden aangeroepen.

Tot slot KAN het evalueren van een query aan rechten worden gekoppeld.
Dat wordt per query geregeld met de velden _rechtentabelnaam_ en _rechtenkolomnaam_. De inlogger is via zijn rechtengroep verbonden met tbrechten of tbomgrechten, tbhorrechten, tbmilrechten, tbmilvergrechten, tbhhrechten, tbovrechten, tbinforechten. Dat zijn de mogelijke waardes van kolom _rechtentabelnaam_. De kolom _rechtenkolomnaam_ verwijst naar een van de veldnamen van die rechtentabellen. De waarde van die veldnaam is F of T. Indien F dan wordt de query niet uitgevoerd. En als deze kolommen worden leeggelaten is er dus geen extra restrictie en wordt de query altijd geëvalueerd.

De kijkrechten op de modules:

- Omgevingszaken: tbrechten en dlaomgvsb
- Handhavingen: tbrechten en dlahahvsb
- APV/Overige: tbrechten en dlaovvvsb
- Objecten/inrichtingen: tbrechten en dlamilinrvsb
- Milieu/gebruik: tbmilvergrechten en dlamilvergvsb

## Queries voor tegelopschrift

De aanroep van het SQL-statement vindt plaats via de tegeldefinitie van de tegel waarop het dynamische opschrift moet verschijnen door het vullen van de kolom _Tegelopschrift dynamisch met API gettilecontent_ (zie [Portal tegel](/instellen_inrichten/portaldefinitie/portal_tegel.md)). Een voorbeeld van een dynamisch tegelopschrift is de waarde `_getTileContent(omgeving_status,{id}.md)`. De codering _omgeving_status_ verwijst naar een uniek codering in de tabel tbqueries. Het SQL-statement dat aldaar staat zal worden gebruikt om het dynamische deel van het tegelopschrift te genereren.

Die parameter {id} kan gebruikt worden bij tegels op de zaakportals (dus niet bij opening of beheer). Deze wordt vervangen door de primary key van het betreffende zaakportaal (de identifier die opgenomen is in de URL van de portaalpagina).
Indien de resultaat set uit meerdere regels bestaat, zal OpenWave deze aan elkaar plakken gescheiden door een puntkomma, zodat elke regel ook een regel op de tegel wordt.

Met HTML-code kan die éne resultaatkolom van een query toch in twee regels op een tegel getoond worden door op de gewenste plek bijvoorbeeld in te voegen. Bovendien kunt u ook andere HTML-code gebruiken bijvoorbeeld kleur:

```sql
select
    '<p style="color:red">' | | dvstatus | |'</p>'
    | | '<br>startdatum: ' | | to_char(ddaanvraag,'dd-mm-yyyy')
    | | '<br>fatale/streefdatum: '
    | | to_char(ddfataledatum,'dd-mm-yyyy')
    | | case when ddingetrokken is not null
            then '<br>ingetrokken: ' | | to_char(ddingetrokken,'dd-mm-yyyy')
           else
             '<br>besluit: ' | | to_char(ddbesluitdatum,'dd-mm-yyyy')
           end
   from vwfrmomgvergunningen
   where dnkeyomgvergunning = {id}
```

Het resultaat als tegelopschrift is bijvoorbeeld:

![Tegel-query met kleur](../img/applicatiebeheer/instellen_inrichten/tegel_query_metkleur.png){ class="media" loading="lazy" alt="" width="200" }

Wanneer een query niet valide SQL-code gebruikt zal het programma - bij gebruik voor tegelopschrift - het resultaat vervangen door 'fout:xml': dat zal dan op de betreffende tegel verschijnen.

## Query's om blokken onzichtbaar te maken in detailscherm

```xml
<blok>
      <label>Hyperlink</label>
      <width>100</width>
      <height>40</height>
      <type>doorlopend</type>
      <notvisibleif>%query(omgeving_blokhyperlink)%</notvisibleif>
      <column value="dvhyperlink">
```

Zie [Scherminformatie voor detailschermen](/instellen_inrichten/schermdefinitie/scherminformatie_voor_detailschermen.md).
In de tags van een blok van een detailscherm kan (hoeft dus niet) de tag`<notvisibleif>`opgenomen worden (onder de tag <type>). De inhoud van de tag verwijst naar een bepaalde query. Zo zal _<notvisibleif>%query(omgeving_hyperlink)%</notvisibleif>_ verwijzen naar een rij in tbqueries met dvcode = _omgeving_hyperlink_.

De bijbehorende query wordt geëvalueerd. De uitkomst van de query moet 1 (het blok is NIET zichtbaar) of 0 (WEL zichtbaar) zijn.
Voorbeeld:

```sql
select case when (dlmappenhyperlink = 'F') then 1 else 0 end from tbrechten
           where dnkey = (select dnkeyrechten from tbmedewerkers where trim(dvcode) = trim(:keyaccount))
```

Indien wordt verwezen naar een niet bestaande query of het element is leeg of indien error bij evaluatie of uitkomst is <> 1 dan beschouwt het programma de uitkomst van de query als 0 (het blok is wel zichtbaar).

Indien in de aangeroepen query gebruik wordt gemaakt van de variabele {id} dan moet een tweede parameter worden toegevoegd aan de functie query() bestaande uit de string `%keypointer%`. Zie voorbeeld hieronder bij Query's voor contextafhankelijke attributen.

## Query's voor contextafhankelijke schermkolommen

Vooralsnog wordt een queryaanroep ondersteunt bij de tags label, edit, backcolor, fontcolor, visible en action en filter.

### Label

Een query kan worden gebruikt om de inhoud van de tag label contextgevoelig te maken.

Voorbeeld: wanneer in de schermkolomdefinitie van een detailscherm staat `<label>Datum %query(omg_labelbesluit)%</label>` zal het programma dynamisch het label samenstellen met de tekst 'Datum ' + daarachter het resultaat van de geëvalueerde query uit de tabel tbqueries met dvcode = _omg_labelbesluit_.

Indien de contextgevoeligheid is gebaseerd op andere informatie uit de kaart die getoond wordt (de query zal dan bestaan uit `select x from y where dnkey = {id}`) dan moet een tweede parameter `%keypointer%` meegegeven worden: `<label>Datum %query('omg_labelbesluit,%keypointer%)%</label>`. De variabele {id} uit de query zal vervangen worden met de primary key (dnkey) van de kaart waar je op staat.

Zie de voorbeelden hieronder bij [action](/instellen_inrichten/queries#action.md).

### Visible

Een query kan worden gebruikt om een kolom contextgevoelig in het scherm op te nemen. In de schermkolomdefinitie (zowel voor kolommen van een lijst- als die voor het detailscherm) kan tag `<visible>` opgenomen zijn. Indien deze optionele tag de waarde false of 0 heeft dan moet de betreffende kolom NIET worden opgenomen. Indien deze optionele tag de waarde true of 1 heeft, of indien de tag niet bestaat, dan wordt de kolom wel opgenomen.

Een query kan worden gebruikt om de inhoud van de tag contextgevoelig de waarde true of false te geven. Voorbeeld: wanneer in de schermkolomdefinitie van een detailscherm staat `<visible>%query(kolomXzichtbaar,%keypointer%)%</visible>` zal het programma de tag visible vullen met de waarde die komt uit de aangeroepen geëvalueerde query. Indien die waarde ongelijk aan 'true' is dan moet de kolom NIET worden opgenomen.

De query zal dan bestaan uit zoiets als `select case when x then 'true' else 'false' from y where dnkey = {id}`) waarbij `{id}` onder water wordt vervangen door de dnkey van kaart waar je op staat (de parameter `%keypointer%` in de aanroep).
Indien de query niet valide is, dan wordt de tag gevuld met 'false'.

Er bestaat een systeemquery met dvcode = _geefWaardeRechtenkolom_ die makkelijk toegang geeft tot het rechtensysteem van OpenWave en false of true retourneert. Voorbeeld is het zichtbaar zijn van de knop wijzig bevoegd gezag in het detailscherm van de omgevingszaak. In de schermkolomdefinitie is de tag visible als volgt:

`<visible>%query(geefwaarderechtenkolom,'tbomgrechten.dlbomgbevgezedt')%</visible>`

De query kijkt voor de betreffende inlogger naar de waarde van de kolom tbomgrechten.dlbomgbevgezedt.

### Edit

Een query kan worden gebruikt om de tag _edit_ contextgevoelig de waarde true of false te geven.

Voorbeeld: wanneer in de schermkolomdefinitie van een detailscherm staat `<edit>%query(omgeving_mddc_schermknopolo,%keypointer%)%</edit>` zal het programma het attribuut _edit_ vullen met de waarde die komt uit de aangeroepen geëvalueerde query.

De query zal dan bestaan uit zoiets als `select case when x then 'true' else 'false' from y where dnkey = {id}`, waarbij {id} onder water wordt vervangen door de dnkey van kaart waar je op staat (de parameter `%keypointer%` in de aanroep).
Indien de query niet valide is, dan wordt het attribuut _edit_ gevuld met 'false'.

Er bestaat een systeemquery met dvcode = _geefWaardeRechtenkolom_ die makkelijk toegang geeft tot het rechtensysteem van OpenWave en false of true retourneert. Zie hierboven bij visible: _geefwaarderechtenkolom_.

### Backcolor / Fontcolor

Een query kan worden gebruikt om de tags backcolor en fontcolor contextgevoelig de waarde true of false te geven.
Het resultaat van de query moet gevuld zijn met standaard html colorname ([https://www.w3schools.com/colors/colors_names.asp](https://www.w3schools.com/colors/colors_names.asp).md).

### Action

Een action kan in een schermkolomdefinitie worden gekoppeld aan een schermknop. Bijvoorbeeld een knop achter de kolom OLO-nummer in de omgevingsdetailkaart waarmee het OLO-loket met de juiste aanvraag wordt geopend afhankelijk van het OLO-nummer op de kaart: Of een knop die een pdok-kaart opent op basis van de coördinaten van het bijbehorende locatie adres.
Die action is dus contextgevoelig.

#### Voorbeeld 1: ga naar OLO-loket op juiste aanvraagnummer

De URL daartoe is: `https://www.omgevingsloket.nl/BevoegdGezag/bevoegdgezag/AanvraagTab/Aanvraag/?????/AanvraagGegevens`

Waarbij op de plaats van de vraagtekens een valide OLO-aanvraagnummer moet worden gevuld.
Dat lossen we op door:

- een knop te definiëren op het detailscherm van de omgevingszaak met een action waarin bovengenoemde URL wordt gedefinieerd
- in de URL een queryverwijzing te maken teneinde het juiste OLO-aanvraagnummer op te halen
- een query te maken die het gevraagde OLO-nummer retourneert.

De knop kan als volgt worden gedefinieerd:

```xml
<column>
     <regel>3</regel>
     <tagnaam/>
     <label/>
     <divwidth>20</divwidth>
     <divheight>30</divheight>
     <edit>true</edit>
     <showhint>false</showhint>
     <wavetype>schermknop</wavetype>
     <source></source>
     <filter>enable</filter>
     <refresh>false</refresh>
     <backcolor/>
     <fontcolor/>
     <nullable>true</nullable>
     <icoon>14</icoon>
     <align/>
     <pretext/>
     <posttext/>
     <hint>ga naar omgevingsloket</hint>
    <action>openTabPage(https://www.omgevingsloket.nl/BevoegdGezag/bevoegdgezag/AanvraagTab/Aanvraag/%query(omgeving_olonummer,%keypointer%)%/AanvraagGegevens)</action>
   </column>
```

Een action die begint met de functie _openTabPage_ laat het programma als het ware de inhoud van _openTabPage()_ intikken in de URL-editbox van de browser met als gevolg dat in een nieuw browsertabblad de gevraagde site wordt geopend. In de URL is het OLO-nummer opgenomen door een verwijzing naar een query met dvcode = _omgeving_olonummer_. Die query ziet er als volgt uit:

```sql
select dvlvoaanvraagnr from tbomgvergunning where dnkey = {id}
```

Aangezien in de query de variabele {id} is opgenomen die vervangen moet worden door de dnkey van de betreffende omgevingszaak, is de aanroep naar de query voorzien van een tweede parameter %keypointer% dus: _%query(omgeving_olonummer,%keypointer%)%_.

Stel het OLO-nummer is '123456' dan zal het uiteindelijke resultaat van het indrukken van de schermknop zijn het openen van de URL:

`https://www.omgevingsloket.nl/BevoegdGezag/bevoegdgezag/AanvraagTab/Aanvraag/123456/AanvraagGegevens`

#### Voorbeeld 2: ga naar ruimtelijke plannen op grond van adresgegevens

De URL daartoe is: `http://www.ruimtelijkeplannen.nl/web-roo/roo/bestemmingsplannen?xxxx&amp;amp;yyyy`
Waarbij op de plaats van de xxxx de tekst 'postcode='+ een valide postcode moet worden ingevoerd en op de plaats van de yyyy moet de tekst 'huisnummer=' + een huisnummer en eventueel een huisletter worden ingevoerd.

Dat lossen we op door:

- een knop te definiëren op het detailscherm van het locatie adres met een action waarin bovengenoemde URL wordt gedefinieerd
- in de URL een queryverwijzing te maken teneinde de tekst 'postcode=' + de gewenste postcode op te halen
- in de URL een queryverwijzing te maken teneinde de tekst 'huisnummer=' + een huisnummer en huisletter op te halen
- een query te maken die de gevraagde postcode informatie retourneert
- een query te maken die het gevraagde huisnummerinformatie retourneert.

De knop kan als volgt worden gedefinieerd:

```xml
 <column>
    <regel>1</regel>
    <tagnaam/>
    <label/>
    <divwidth>20</divwidth>
    <divheight>30</divheight>
    <edit>true</edit>
    <showhint>false</showhint>
    <wavetype>schermknop</wavetype>
    <source></source>
    <filter>enable</filter>
    <refresh>false</refresh>
    <backcolor/>
    <fontcolor/>
    <nullable>true</nullable>
    <icoon>14</icoon>
    <align/>
    <pretext/>
    <posttext/>
    <hint>ga naar ruimtelijke plannen</hint>
    <action>openTabPage(http://www.ruimtelijkeplannen.nl/web-roo/roo/bestemmingsplannen?%query(locatie_postcode,%keypointer%)%&amp;%query(locatie_huisnr,%keypointer%)%)</action>
 </column>
```

In de URL is het postcodegedeelte opgenomen door een verwijzing naar een query met dvcode = locatie_postcode. Die query ziet er als volgt uit:

```sql
select 'postcode='| | coalesce(dvpostcode,'') from tbperceeladressen where dnkey = {id}
```

Aangezien in de query de variabele {id} is opgenomen die vervangen moet worden door de dnkey van de betreffende locatie (tbperceeladressen), is de aanroep naar de query voorzien van een tweede parameter `%keypointer%`, dus: `%query(locatie_postcode,%keypointer%)%`.

In de URL is het huisnummergedeelte opgenomen door een verwijzing naar een query met dvcode = locatie_huisnr. Die query ziet er als volgt uit:

```sql
select 'huisnummer=' | | coalesce(trim(dvhuisnummer),'') | | coalesce(dvhuisletter,'') from tbperceeladressen where dnkey = {id}
```

Aangezien in de query de variabele {id} is opgenomen die vervangen moet worden door de dnkey van de betreffende locatie (tbperceeladressen), is de aanroep naar de query voorzien van een tweede parameter `%keypointer%`, dus: `%query(locatie_huismummer,%keypointer%)%`.

Stel de postcode van de locatiekaart waarvandaan de knop wordt aangesproken = 1074XK en het huisnummer = 41, dan zal een URL geopend worden met:

`http://www.ruimtelijkeplannen.nl/web-roo/roo/bestemmingsplannen?postcode=1074XK&amp;huisnummer=41`

#### Voorbeeld 3 Open een pdok-kaart op basis van een coördinatenpaar

De URL van bijvoorbeeld het x, y punt (168875,382535) op een PDOK-kaart is:

`https://kaart.pdok.nl/api/api.html?mloc=168875,382535&mt=mt3&loc=168875,382535&zoom=10&tekst=Locatie:%3C/BR%3E168875,382535`

De action:

`html4strictopentabpage(https://kaart.pdok.nl/api/api.html?mloc=%query(coordinaten,%keypointer%)%&amp;mt=mt3&amp;loc=%query(coordinaten,%keypointer%)%&amp;zoom=10&amp;tekst=Locatie:%3C/BR%3E%query(coordinaten,%keypointer%)%)`

De query _coördinaten_ moet dus als resultaat een x- en een y-coördinaat teruggeven (in rijksdriehoek) gescheiden door een komma.

### Filter

Een query kan worden gebruikt om de inhoud van de tag filter contextgevoelig te maken.

Voorbeeld: wanneer bij een processtap een extra invoerkolom is gedefinieerd van type dropdown, dan wordt de bijbehorende query voor het dropdownlijstje in het beheer bij de definitie van de procestap gedefinieerd. Deze wordt bij het binnenhalen van een proces vervolgens gekopieerd naar de tabel tbtermijnbewstappen om de kolom dvinvoerdropd aldaar met een dropdowwnlijstje te kunnen vullen. Om nu - dynamisch - het juiste dropdownlijstje te krijgen is de kolom dvinvoerdropd in de schermkolomdefinitie van het detailscherm van een processtap als volgt gedefinieerd (inclusief contextgevoelige zichtbaarheid en label):

```xml
<column value="dvinvoerdropd">
                <regel>3</regel>
                <tagnaam>dvinvoerdropd</tagnaam>
                <label>%query(termijnstappen_mddc_getinvoerlabeldropd,%keypointer%)%</label>
                <divwidth>400</divwidth>
                <divheight>30</divheight>
                <edit>true</edit>
                <showhint>false</showhint>
                <wavetype>keuzelijst</wavetype>
                <source>generalwithoutemptyline</source>
                <filter>%query(termijnstappen_mddc_getinvoerquerydropd,%keypointer%)%</filter>
                <refresh>false</refresh>
                <backcolor/>
                <fontcolor/>
                <nullable>true</nullable>
                <icoon/>
                <visible>%query(termijnstappen_mddc_isinvoerdropdvsb,%keypointer%)%</visible>
   </column>
```

### Nullable

Een query kan worden gebruikt om de inhoud van de tag nullable contextgevoelig te maken.

## Query's voor invoegen tekstblokken bij sjablonen

Zie ook kopje **Invoegen tekstblokken op basis van een query-aanroep naar tbqueries** bij [Documentsjablonen](/instellen_inrichten/documentsjablonen.md).
De query wordt in het documentsjabloon wordt aangeroepen door met de merge-codering `<%query(param1,param2)%>`.

Bijvoorbeeld: `<%query(apvoverig_tkstblk1,:keyvergunning)%>`.

> [!WARNING]
> **LET OP:** De hier gebruikte merge-codering zal niet door de spellingschecker heenkomen, voor een goede werking zal het sjabloon daarom opgeslagen moeten zijn zonder spellingschecker!

Param1 wordt opgezocht in de kolom dvcode van tbqueries. Die query wordt geëvalueerd waarbij de string {id} in de query - indien aanwezig - eerst wordt vervangen door de waarde van param2. Param2 is dus optioneel.

Param2 zal meestal gevuld worden met de dnkey van de kaart van waaruit het document wordt gecreëerd. In het sjabloon wordt dit opgegeven door param2 één van de volgende waardes te geven (er zijn geen andere mogelijkheden voor param2):

- :keyvergunning (staat voor de dnkey van een zaak: tbovvergunningen, tbomgvergunning, tbmilvergunningen, tbhandhavingen, tbbouwvergunningen, tbhorecavergunningen en tbinfoaanvragen)
- :keyadvies
- :keyinspectie
- :keyinspectiebezoek
- :keyinrichting (staat voor de dnkey van de inrichting)
- :keyadres (staat voor de dnkey van een aangewezen contactpersoon)
- :keybezwaarberoep
- :keylocatie (staat voor de dnkey van de locatie van de zaak/inrichting).

### Voorbeeld 1: invoegen tekst uit query zelf

De verwijzing in het sjabloon kan zijn: `<%query(apvoverig_tkstblk1,:keyvergunning)%>`.

De query uit tbqueries waarnaar wordt verwezen via apvoverig_tkstblk1 kan zijn:

```sql
select case when (select dvcodesoortovverg from tbovvergunningen where dnkey = {id}) = 'O'
              then  'Volgens artikel X van wet y zal de ontheffing ....'
              else ''::text
         end
```

Hetgeen betekent dat indien het zaaktype van de APV/Overige vergunning waar vandaan het document wordt gecreëerd van het soort 'O' is dat alleen dan de tekst _Volgens artikel X van wet y zal de ontheffing …._ zal worden ingevoegd.

### Voorbeeld 2: invoegen tekst uit de tabel tekstblokken via de query

```sql
select dvtekstblok from tbtekstblokken where lower(dvcode) =
               case when (select dvcodesoortovverg from tbovvergunningen where dnkey = {id}) = 'O'
                    then  'tkstblk_1'
                    when (select dvcodesoortovverg from tbovvergunningen where dnkey = {id}) = 'E'
                     then  'tkstblk_2'
               else 'xxx'
               end
```

Hetgeen betekent dat indien het zaaktype van de APV/Overige vergunning waar vandaan het document wordt gecreëerd van het soort 'O' is dat dan de inhoud van de kolom dvtekstblok uit de tabel tbtekstblokken (beheer) met dvcode = _tkstblk_1_ wordt afgedrukt.

Indien soort = 'E' wordt de inhoud van de kolom dvtekstblok met dvcode = _tkstblk_2_ afgedrukt. En anders niets.

Zie voor invoegen plaatjes op basis van query onder Kopje: _Invoegen plaatjes op basis van een query-aanroep naar tbqueries die verwijst naar tbimages_ bij [Documentsjablonen](/instellen_inrichten/documentsjablonen.md).

## Query's als vervanging voor formqueries en childqueries bij definitie document- en emailsjablonen

De inhoud van de kolommen van de formqueries en childqueries uit de definitie document- en emailsjablonen (beheer) kan ook bestaan uit een verwijzing naar een query in deze tabel tbqueries.

Hierdoor hoeft een query die in meerdere sjablonen gebruikt wordt maar eenmalig te worden gedefinieerd. De opmaak van de sjablonen wijzigt hierdoor niet. In tbqueries kan bovendien een select statement ingevoerd worden van onbeperkte grootte.

Zie het kopje _formquery en childquery-verwijzingen naar tbqueries_ bij [Documentsjablonen en Sjabloongroepen](/instellen_inrichten/documentsjablonen.md)
