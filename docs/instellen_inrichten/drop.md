# Drop

## Inleiding

De DROP staat voor Decentrale Regelgeving Officiële Publicaties. DROP is daartoe een online functionaliteit die geleverd wordt door KOOP (Kennis- en exploitatiecentrum Officiële Overheidspublicaties).

Zaken in OpenWave uit de modules omgeving, horeca, APV/overig en milieu/gebruik kunnen automatisch aangeleverd worden voor publicatie vanuit OpenWave. Een en ander moet wel ingeregeld worden met de digi-koppelaar, waarbij o.a. een certificaat (per gemeente!) moet worden aangeleverd en geplaatst.

Een publicatie wordt getriggerd door het gevuld zijn van een publicatietype: een aanvraagdatum, een afgehandelddatum een ontwerpbesluitdatum, een ingetrokkendatum, een verdaagddatum, een verlengdvanafdatum en een opschortdatum, mits dat publicatietype gedefinieerd is bij een combinatie van gemeente en zaaktype (beheerportaal Zaakbeheer bij definitie zaaktypes).

Bij een combinatie van zaaktype, publicatietype en gemeente kunnen ook één of meer publicatiedoelen zijn opgegeven te weten: gemeenteblad, gemeenschapsblad, waterschapsblad, provincieblad en Staatscourant. Indien geen medium wordt opgegeven dan wordt er alleen online gepubliceerd, hetgeen betekent dat de zaak onder het publicatietype wordt klaargezet in DROP, waarna een medewerker van het bevoegd gezag deze zaak in de DROP-omgeving alsnog kan publiceren in één of meer bladen.

### Instellingen configuratietabel

Noodzakelijke instellingen: zie [Sectie DROPPUBLICATIES](./configuratie/sectie_droppubliceren.md).

### Instellingen gemeentetabel

Voor elke gemeente waarvoor de OpenWave implementatie kan publiceren moet in de beheertabel tb33gemeente in het blok *DROP-publicatie* het endpoint bij de digi-koppelaar worden weergegeven: bijvoorbeeld `https://acceptatie.overheidsservicebus.com/opentunnel/00000099130854102053/drop/3epas](https://acceptatie.overheidsservicebus.com/opentunnel/00000099130854102053/drop/3epas`.

Indien zo ingeregeld dat het benodigde certificaat tussen OpenWave en de digi-koppelaar wordt geplaatst, dan dient hier certificaatnaam, type en password opgegeven te worden. Het certificaat wordt dan op de server van OpenWave geplaatst. Indien zo ingeregeld dat het benodigde certificaat tussen de digi-koppelaar en KOOP wordt geplaatst dan hoeft hier alleen het endpoint te worden opgegeven.

### Publiceren voor bevoegd gezag

Het publiceren voor overige bevoegde gezagen (provincies/waterschappen) gaat als volgt:

  - Voer het gezag op in de beheertabel *Gemeentes*,
  - Voer een dummy gemeenteID op bij het gezag,
  - Koppel het gemeenteID aan het bevoegde gezag in de beheertabel *OIN-nummers*,
  - Vul het bevoegde gezag op bij de zaak die gepubliceerd moet worden.

### Koppelen van de gemeente(s) aan een zaaktype, een publicatiedoel en gewenste medium

In het beheerportaal *Zaakbeheer*, onder de kolom *Zaaktypes* kunnen zaaktypes worden gekozen waarvoor gepubliceerd dient te worden.

Let op: de zaaktypes die gekozen kunnen worden vallen binnen de modules:

  - Omgeving
  - APV/overig
  - Horeca
  - Milieu/gebruik

In het detailscherm van een gekozen zaaktype, kunnen in het blok *DROP publiceren* gemeente(s) worden gekoppeld aan dat zaaktype. Per gemeente kan aangevinkt worden welke publicatiedoelen aan de orde zijn voor het betreffende zaaktype:

  - Aanvraag. Mogelijk voor alle modules en wordt getriggerd door de aanvraagdatum mits groter dan hier opgegeven de publicatiedatum vanaf en kleiner dan vandaag (dus tot en met gisteren).
  - Ontwerpbesluit. Alleen mogelijk voor omgevingszaken en wordt getriggerd door de ontwerpbesluitdatum (ddontwerpbesldatum) mits groter dan hier opgegeven de publicatiedatum vanaf en kleiner dan vandaag.
  - Verlengen (verdagen). Alleen mogelijk voor omgevingszaken en wordt getriggerd door de verdaagdvanafdatum (tbomgvergunning.ddverdaagdvanaf) mits groter dan hier opgegeven de publicatiedatum vanaf en kleiner dan vandaag. Let op: de kolom ddverdaagdvanaf is alleen zichtbaar indien bij het betreffende zaaktype de kolom Verlengen/Opschorten via blokken in detail(tbsoortomgverg.dlblokkenopschort) is aangevinkt.
  - Opschorten. Alleen mogelijk voor omgevingszaken en wordt getriggerd door de opschortenvanafdatum (tbomgvergunning.ddopschortingvanaf) mits groter dan hier opgegeven de publicatiedatum vanaf en kleiner dan vandaag. Let op: de kolom ddopschortingvanaf is alleen zichtbaar indien bij het betreffende zaaktype de kolom Verlengen/Opschorten via blokken in detail(tbsoortomgverg.dlblokkenopschort) is aangevinkt.
  - Besluit. Mogelijk voor alle modules en wordt getriggerd door de besluit/afgehandelddatum mits groter dan hier opgegeven de publicatiedatum vanaf en kleiner dan vandaag.
  - Ingetrokken. Ingetrokken door aanvrager tijdens behandeling. Mogelijk voor alle modules en wordt getriggerd door de ingetrokkendatum (ddingetrokken) mits groter dan hier opgegeven de publicatiedatum vanaf en kleiner dan vandaag.
  - Verlengen (verlengd2). Alleen mogelijk voor omgevingszaken en wordt getriggerd door de verlengdvanafdatum (tbomgvergunning.ddverlengdvanaf) mits groter dan hier opgegeven de publicatiedatum vanaf en kleiner dan vandaag. Let op: de kolom ddverlengdvanaf is alleen zichtbaar indien bij het betreffende zaaktype de kolom Verlengen/Opschorten via blokken in detail(tbsoortomgverg.dlblokkenopschort) is aangevinkt.

Op dezelfde regel kunnen voor de combinatie zaaktype/ gemeente en publicatietypes één of meer media (publicatiedoelen) worden opgegeven:

  - gemeenteblad. In de regel zal alleen dit medium worden gebruikt.
  - gemeenschapsblad
  - waterschapsblad
  - provincieblad
  - Staatscourant

Indien geen medium wordt opgegeven dan wordt er alleen online gepubliceerd, hetgeen betekent dat de zaak onder het publicatietype wordt klaargezet in DROP, waarna een medewerker van het bevoegd gezag deze zaak in de DROP-omgeving alsnog kan publiceren in één of meer bladen.

### Documentsjablonen aanmaken en vullen met inhoud.xml

De publicatieberichten - elke combinatie van zaak, publicatietype en publicatiedoel is een zelfstandig xml-bericht - richting KOOP bevatten een onderdeel (de tag inhoud.zip) waarmee de opmaak van de publicatie is te beïnvloeden. Deze tag inhoud.zip wordt gevuld met een xml-string (en vervolgens gezipt en gebased64). De xml-string heeft de naam inhoud.xml en deze moet opgenomen worden bij de OpenWave document-sjabloondefinities bij de groep met

  - Codering: *DROP*
  - Groepsnaam: *DROP xml sjablonen*
  - Van toepassing op modules: leeglaten (dus niks invullen)

In deze groep DROP kunnen één of meer sjablonen worden gedefinieerd. In ieder geval één voor elk gedefinieerd publicatietype. Deze zullen fungeren als de standaardsjablonen voor de publicaties.

De Naam/Omschrijving van de default sjablonen moeten de volgende zijn:

  - Default_Aanvraag
  - Default_Ontwerp
  - Default_Besluit
  - Default_Verlenging    (van toepassing bij verdagen op grond van tbomgvergunning.ddverdaagdvanaf)
  - Default_Ingetrokken
  - Default_Opschorten
  - Default_Verlengd2     (van toepassing bij verlengen op grond van tbomgvergunning.ddverlengdvanaf)

Dus indien het publicatiedoel Opschorten is aangevinkt bij een bepaald omgevingszaaktype voor één of meer gemeentes, dan MOET er een sjabloon zijn met de naam *Default_Opschorten* waarbij het sjabloon zelf (een xml-file met de naam inhoud.xml) is geüpload.

Deze inhoud.xml moet conform het volgende voorbeeld opgemaakt zijn:

```xml
<inhoud>
    <al><nadruk type="vet">Locatie: </nadruk>'t Boske 301 , Aalten</al>
    <al><nadruk type="vet">Omschrijving: </nadruk>Reguliere procedure</al>
    <al><nadruk type="vet">Registratienummer: </nadruk>2018W0081</al>
    <al><nadruk type="vet">Publicatiedatum: </nadruk>03-09-2021</al>
    <al><nadruk type="vet">Datum aanvraag: </nadruk>01-09-2021</al>
    <al/>
     <al>U kunt de ingediende aanvraag inzien bij de publieksbalie van het stadskantoor.
         U kunt geen bezwaar maken tegen een aangevraagde vergunning. Dit is pas mogelijk
         nadat de vergunning is verleend.</al>
  </inhoud>
```

Dus een blok`<inhoud>`waarbinnen één of meer regels`<al>`kunnen zijn opgenomen.\

OpenWave zal binnen een regel`<al>`de variabelen ingesloten door %% vervangen -door de variabele-naam op te zoeken in de view vwfrmzakentepubliceren- door de achterliggende waarde uit de database.

De regel `<al><nadruk type="vet">Locatie: </nadruk>%dvobjadres%, %dvobjplaats%</al>` zal OpenWave voor publicatie omzetten in bijv. `<al><nadruk type="vet">Locatie: </nadruk>'t Boske 301 , Aalten</al>`.

De mogelijke te gebruiken variabelen zijn:

  - dvmodule. W indien de te publiceren zaak uit tbomgvergunning komt, E indien uit tbmilvergunningen, C indien uit tbhorecavergunningen en O indien uit tbovvergunningen.
  - dnkeyverg. Primary key van de zaak in tbomgvergunning bij dvmodule = W, in tbmilvergunningen bij dvmodule = E, in tbhorecavergunningen bij dvmodule = C, in tbovvergunningen bij dvmodule = O.
  - ddstartdatum. Aanvraagdatum van te publiceren zaak.
  - ddbesluitdatum. Besluit/afhandeldatum van onderliggende zaak.
  - ddontwerpbesldatum. Datum ontwerpbesluit van onderliggende zaak (alleen bij omgevingszaken).
  - ddfataledatum. Uiterlijke datum dat zaak behandeld moet zijn.
  - ddpublexport. Laatste datum dat een poging gedaan is om de zaak onder het publicatietype te publiceren.
  - dvpublfout. Foutcode die door DROP is geretourneerd bij de laatste keer dat een poging gedaan is om de zaak onder het publicatietype te publiceren.
  - dvzaakcode. De OpenWave zaakcode.
  - dvzaaktypeoms. Zaaktype omschrijving.
  - dvgemeenteid. De gemeente-id van de locatie waar de zaak aan gekoppeld is.
  - dvbetreft. Korte omschrijving van de zaak. Zie ook hieronder bij tag <titel>.
  - dvgemeentenaam. De gemeentenaam van de locatie waar de zaak aan gekoppeld is.
  - dvobjplaats. Woonplaatsnaam van de locatie waar de zaak aan gekoppeld is.
  - dvobjstraat. Straatnaam van de locatie waar de zaak aan gekoppeld is.
  - dvobjhuisnummer. Huisnummer van de locatie waar de zaak aan gekoppeld is.
  - dvobjhuisletter. Huisletter van de locatie waar de zaak aan gekoppeld is.
  - dvobjhuisnrtoevoeg. Huisnummertoevoeging van de locatie waar de zaak aan gekoppeld is.
  - dnxcoordinaat. x-coördinaat van de locatie waar de zaak aan gekoppeld is, tenzij null, dan de eerste x van dvgmlpolygoon van dvbron.
  - dnycoordinaat. y-coördinaat van de locatie waar de zaak aan gekoppeld is, tenzij null, dan de eerste y van dvgmlpolygoon van dvbron.
  - dnkeycompartiment. De primary key van tbcompartiment indien de combinatie gemeente/zaaktype daaraan gekoppeld is.
  - dvbron. tbomgvergunning, tbovvergunningen, tbhorecavergunningen of tbmilvergunningen.
  - dvaardbesluit. De resultaat-omschrijving van het besluit bijv. verleend, gedeeltelijk geweigerd, afgehandeld.
  - dvid. DvModule | | dnkeyverg. Dus unieke waarde voor elke rij.
  - dvobjadres. Samengestelde kolom van straat en huisnummergegevens.
  - dvlvoaanvraagnr. OLO of DSO-nummer van de zaak (alleen omgevingszaak en milieu/gebruik).
  - ddverzenddatum. Verzenddatum (alleen omgevingszaak en APV/Overig).
  - dvzaakdomeinoms. Domeinomschrijving, (alleen omgevingszaak).
  - dvaanvraagoms. Nadere omschrijving van de zaak.
  - ddingetrokken. Intrekdatum tijdens behandeling van de zaak.
  - ddopschortingvanaf. Opschortingsdatum vanaf artikel 415 (alleen omgevingszaak).
  - ddverdaagdvanaf. Verlengingsdatum vanaf bij verdagen  (alleen omgevingszaak).
  - dvonderdelen. Bestaat uit een opsomming in een string van de - niet ingetrokken - onderdelen uit tbtoestemmingen (alleen omgevingszaak).
  - ddverlengdvanaf. Alleen bij omgevingszaken.
  - dnverlengddagen. Alleen bij omgevingszaken: aantal dagen verlengd met ingang van ddverlengdvanaf.

### Titel

De tag`<titel>`van de publicatie wordt default gevuld met de inhoud van de kolom dvbetreft. Daarvan wordt afgeweken indien de eerste query van het sjabloon (dvformquery) een goede waarde oplevert. De query kan gebruik maken van bovengenoemde kolommen van de vwfrmzakentepubliceren. Om de juiste rij te bepalen luistert OpenWave naar de constructie `where dvid = :idzakentepubliceren`.

Een voorbeeld van een query die in de kolom dvformquery moet worden geplaatst om de titel te bepalen is:

```sql
select dvbetreft | | ' in ' | | dvobjstraat | | ' te ' | | dvgemeentenaam from vwfrmzakentepubliceren where dvid = :idzakentepubliceren
```

![Formquery DROP titel](../img/applicatiebeheer/instellen_inrichten/formquery_1_droptitel.png){ class="media" loading="lazy" alt="" width="700" }

**Velden buiten de view vwfrmzakentepubliceren**

Het is ook mogelijk om data op te nemen van velden buiten de view vwfrmzakentepubliceren. Dit doet men door queries op te nemen in het inhoud.xml sjabloon.
Dit kan op twee manieren:

  - %query(codevanquery)%
  - %query(codevanquery, :idzakentepubliceren)%

Er geldt dat er per query één waarde kan worden meegegeven. Dit betekent dat het niet mogelijk is om meerdere velden op te nemen in één query. Wel kunnen er meerdere queries opgenomen worden in het sjabloon.

De *codevanquery* verwijst naar de codering van een zelf te maken query in de tabel tbqueries in het beheer van OpenWave. Een voorbeeld van een query voor het opnemen van de startdatum van een zaak in de publicatie zou er zo uit komen te zien:

```sql
select fn_ddmaandjjjj(ddstartdatum) from vwfrmzakentepubliceren where dvid = '{id}'
of
     select
     case when substr('{id}',1,1) = 'W'
        then (select fn_ddmaandjjjj(ddaanvraag) from tbomgvergunning
     where dnkey = (select dnkeyverg from vwfrmzakentepubliceren where dvid = '{id}' ))
        when  substr('{id}',1,1) = 'O'
        then (select fn_ddmaandjjjj(ddontvangstdatum) from tbovvergunningen
     where dnkey = (select dnkeyverg from vwfrmzakentepubliceren where dvid = '{id}' ))
        when  substr('{id}',1,1) = 'C'
        then (select fn_ddmaandjjjj(ddaanvraagdatum) from tbhorecavergunningen
     where dnkey = (select dnkeyverg from vwfrmzakentepubliceren where dvid = '{id}' ))
        when  substr('{id}',1,1) = 'E'
        then (select fn_ddmaandjjjj(ddontvangstdatum) from tbmilvergunningen
     where dnkey = (select dnkeyverg from vwfrmzakentepubliceren where dvid = '{id}' ))
     end
```

Ook hier geldt dat OpenWave luistert naar de constructie `where dvid = :idzakentepubliceren` om de juiste rij te bepalen.

### Documentsjablonen per gemeente / publicatiedoel / zaaktype

Bovengenoemde default-sjablonen dienen altijd aanwezig te zijn.
Desgewenst kunnen ook sjablonen per combinatie gemeente/publicatietype worden gemaakt en zelf sjablonen per combinatie gemeente/publicatietype/zaaktype. Waarbij in de sjabloonnaam gebruikt wordt gemaakt van de gemeente-id en de dnkey van het zaaktype.

Stel dat de te publiceren zaak gaat om het publicatietype Aanvraag en dat het gaat om een zaak in gemeente Aalten (zoals geschreven in de beheertabel tb33gemeente) en de dnkey van het betreffende omgevingszaaktype = 100 (dus de dnkey uit de beheertabel tbsoortomgverg).

dan redeneert OpenWave bij het publiceren als volgt:

  - Eerst wordt gezocht naar het documentsjabloon (in de groep DROP) met de naam: Aalten_Aanvraag_100.
  - Indien niet gevonden dan wordt gezocht naar Aalten_Aanvraag
  - Indien niet gevonden dan wordt gezocht naar Default_Aanvraag_100
  - en tenslotte naar de verplicht aanwezige Default_Aanvraag

### Tegel Te publiceren zaken (DROP) openingsportaal

De tegel is als volgt gedefinieerd:

  - Vast opschrift: Te publiceren zaken (DROP)
    - Actie: getFlexList(SysStandardList,nil,nil,G,opening_drop)
    - Actief: aangevinkt

#### Lijstscherm Te publiceren zaken

De tegel triggert een lijst met zaken waarvoor één of meer publicaties klaar staan op grond van publicatiedoel en datum, aangevuld met zaken waarvoor eerdere publicaties mislukt zijn (om wat voor reden dan ook) en die om die reden alsnog gepubliceerd moeten worden.

De basis view voor deze lijst is vwfrmzakentepubliceren. De view kijkt naar de tabel tbdroppublicaties om te zien of een bepaalde publicatie reeds heeft plaatsgevonden.

Elke zaak heeft default een kolom dltepubliceren met de waarde T. Op zaakniveau (detailscherm) of met de knop *Niet publiceren op deze lijst* kan deze kolom op F worden gezet, waarna de zaak niet meegenomen wordt in de view. Alleen medewerkers met het publicatierecht kunnen de lijst zien en de knoppen daarvan gebruiken. Het publicatierecht (*mag drop publiceren: tbmedewerkers.dlmagpubliceren*) is aan te vinken in het detailscherm van de medewerkerstabel op het beheerportaal-Nieuw. De lijst houdt rekening met compartiment van de inlogger.

Onderaan de lijst vier knoppen:

  - Ga naar zaakportaal
  - Deze zaak niet publiceren (haal uit lijst). Deze knop zet de kolom dltepubliceren van de betreffende zaak (dus die van de gele balk) op F, waardoor de zaak uit de lijst valt en niet meetelt voor publicaties. Deze kolom is ook te muteren op de detailpagina van de betreffende zaak.
  - Publiceer lijst in DROP. Met deze knop worden alle zaken van de lijst per publicatiedoel/medium aangeboden aan DROP ter publicatie. Dit gebeurt onder water. Als deze knop gestart wordt vanuit het detailscherm (dubbel klik op regel) dan zal alleen die ene zaak worden gepubliceerd.
  - Refresh. De lijst wordt opnieuw uitgeschreven. Met de refreshknop:
    - worden nieuwe zaken opgehaald die gepubliceerd kunnen worden
    - worden succesvol gepubliceerde zaken uit de lijst gehaald
    - worden zaken waarvoor een publicatie mislukt is voorzien van een foutcode

Indien de instelling *Sectie: Droppublicaties en Item: Messagelog* is aangevinkt worden alle dropberichten en antwoord (succes of fout) gelogd in de Messagelogtabel (beheerportaal-Nieuw).

#### Detailscherm te publiceren zaak

Dubbel klikken op een item van de lijst laat een detailscherm zien van de betreffende zaak waarin alle kolommen zijn opgenomen die ook in de opmaak van de inhoud.xml gebruikt kunnen worden voor de substitutie van variabelen (zie hierboven).

Onderaan het detailscherm is een lijst opgenomen van de klaargezette publicatietypes en publicatiedoelen bij de betreffende zaak. Elke regel van dit lijstje is een zelfstandige publicatie in DROP. Dit lijstje is gebaseerd op de views:

  - vwfrmmilvergdetailstepubliceren indien de zaak valt onder de module milieu/gebruik
  - vwfrmomgdetailstepubliceren indien de zaak valt onder de module omgeving
  - vwfrmovdetailstepubliceren indien de zaak valt onder de module APV/overig
  - vwfrmhordetailstepubliceren indien de zaak valt onder de module horeca

De knop Publiceer zaak in DROP triggert de aanmaak van droppublicaties voor die ene zaak. Resultaat wordt altijd in de messagelog opgenomen ongeacht de instelling.

#### Automatisch vullen van tbdroppublicaties

Indien een droppublicatie (= een publicatietype voor een bepaald publicatiedoel) wordt verzonden is het resultaat een foutmelding of een succesmelding. In beide gevallen wordt een kaart aangemaakt of overschreven in tbdroppublicaties bij de betreffende zaak. Deze tabel droppublicaties is terug te vinden in een lijstje onderaan het detailscherm van een zaak (mits de instelling instelling *Sectie: DROPPubliceren en Item: Omgeving* aangevinkt (of item: Apvoverig, horeca, milieugebruik)).

In dit publicatielijstje bij een zaak is per publicatietype en publicatiedoel te zien wanneer er gepoogd is de publicatie te doen, of de publicatie succesvol is: in dat geval is de kolom *Dossiernummer Drop* gevuld, of mislukt: in dat geval is de kolom error gevuld. Een publicatie die een error oplevert wordt opnieuw aangeboden ter publicatie via de lijst Te publiceren (DROP). De betreffende regel in tbdroppublicaties wordt na de nieuwe publicatiepoging overschreven (met dossiernummer bij succes en met nieuwe errorcode indien mislukt).

### Testen van de verbinding

Voor het testen van een verbinding met DROP moet (indien deze nog niet bestaat) een tegel worden gemaakt (in servicecentrum-portaal onder kolom Informatie) met de action *startWizard(isalive,DropPublicaties)*. Bijvoorbeeld:

  - Vast opschrift: isAliveDrop
  - Actie: startWizard(isalive,DropPublicaties)
  - Actief: aangevinkt

De actie triggert een bericht naar DROP om te zien of een verbinding open staat. Dat wordt gedaan op het endpoint gedefinieerd in de kolom *Tekst* van de instelling *Sectie: DropPublicaties Item: Endpoint_isAlive*.
Let op: ook hiervoor heeft de inlogger het recht nodig om te mogen publiceren (tbmedewerkers.dlmagpubliceren).

#### Messagelog

De verzonden publicaties uit de lijst *Te Publiceren (DROP)*  worden opgenomen in de messagelog (beheerportaal-Nieuw) mits de instelling *Sectie: Droppublicaties en Item: Messagelog* aangevinkt staat. Indien slechts een zaak wordt gepubliceerd (vanuit de detailpagina achter de lijst *Te Publiceren (DROP)* wordt altijd de messagelog gevuld.

Het verzonden bericht van OpenWave naar KOOP bestaat uit metadata (goed leesbaar in de xml). De inhoud van de publicatie is de file inhoud.xml die gezipt en base64 gecodeerd in de tag InhoudZip staat.
Om deze leesbaar te maken het volgende: plak en knip de inhoud van deze tag InhoudZipin in een tekstbestandje (bijv. test.txt). Gebruik een online base64 decoder die een file kan decoden (dus niet als string in een tekstvak plakken, maar die test.txt aanwijzen). Bij succes wordt de gedecodeerde test.txt onder een andere naam gedownload. Dat is een zipfile. De inhoud van de zipfile is de leesbare inhoud.xml bijvoorbeeld:

```xml
<?xml version="1.0" encoding="utf-8"?>
  <aanlevering xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="http://technische-documentatie.oep.overheid.nl/repository/schemas/gvop_zakelijke_mededeling_3ePAS_content-only/2013-10-  08/xsd/gvop_zakelijke_mededeling_3epas_content-only_2013-10-08.xsd">
    <zakelijke-mededeling>
        <kop>
            <titel>testingtest</titel>
        </kop>
        <zakelijke-mededeling-tekst>
            <inhoud>
                <al><nadruk type="vet">Locatie: </nadruk>'t Boske 301 , Aalten</al>
                <al><nadruk type="vet">Omschrijving: </nadruk>Reguliere procedure</al>
                <al><nadruk type="vet">Registratienummer: </nadruk>2018W0081</al>
                <al><nadruk type="vet">Publicatiedatum: </nadruk>03-09-2021</al>
                <al><nadruk type="vet">Datum aanvraag: </nadruk>01-09-2021</al>
                <al/>
                <al>U kunt de ingediende aanvraag inzien bij de publieksbalie van het stadskantoor.
                    U kunt geen bezwaar maken tegen een aangevraagde vergunning. Dit is pas mogelijk
                    nadat de vergunning is verleend.</al>
            </inhoud>
        </zakelijke-mededeling-tekst>
    </zakelijke-mededeling>
  </aanlevering>
```

#### Testomgeving DROP

Voor toegang tot de testomgeving van de DROP dient een e-mail gestuurd te worden naar de Servicedesk van KOOP op <drop@koop.overheid.nl>. Deze omgeving wordt de ETO-omgeving genoemd. Als het gaat om de ETO, dan is het voldoende om aan te geven op welke naam het account aangemaakt moet worden en het e-mailadres. Wanneer het account aangemaakt is dan kan ingelogd worden in de web interface van DROP op de ETO om daar de resultaten van de tests in te kunnen zien.

Testomgeving: `https://drop-eto.overheid.nl/Start/Login`.

Na inloggen kan bijvoorbeeld met het *dossiernummer* uit het responseblok van de messagelog de DROP publicatie opgezocht worden.

#### Productieomgeving DROP

Voor de Productie omgeving is een wat formelere route. Hier mag de aanvraag alleen gedaan worden door de contactpersoon van een gemeente. Eventueel kan men bij de Servicedesk navragen wie dat is. Om een Productie account aan te vragen, moet er een formulier ingevuld worden en naar de Servicedesk gestuurd worden. Dit formulier is op te vragen bij de Servicedesk van KOOP of bij wavesupport.

#### Modelkennisgeving voorbeeld

Het ministerie van Binnenlandse Zaken en Koninkrijksrelaties heeft opdracht gegeven om tot modelkennisgevingen te komen. Deze modelkennisgevingen zijn opgesteld met als doel om de inwoners voldoende inhoudelijke informatie te geven op begrijpelijke wijze zonder het gebruik van formele en ambtelijke taal. De modelkennisgevingen zijn getoetst door taalkundige en juridische experts bij de decentrale overheden, Genootschap Onze Taal en burgers via Stichting ABC. Een voorbeeldtekst van een modelkennisgeving dat aangeboden wordt door het ministerie voor een aanvraag omgevingsvergunning reguliere procedure is:

> Aanvraag vergunning voor [omschrijving activiteit] aan [locatie activiteit]
> [Lidwoord en naam decentrale overheid] heeft een aanvraag voor een omgevingsvergunning ontvangen. De vergunning is aangevraagd voor [omschrijving activiteit] aan [locatie activiteit]. [Mogelijke toelichting en uitleg over activiteit].
>
> Waarom publiceert [lidwoord en type decentrale overheid] dit bericht?
> Een omgevingsvergunning wordt bij [lidwoord en type decentrale overheid] aangevraagd om toestemming te krijgen om iets te bouwen, verbouwen, slopen, kappen of aan te leggen. Met dit bericht laat [lidwoord en type decentrale overheid] u weten dat er misschien iets verandert in uw omgeving. Dan kunt u op tijd reageren als u het hier niet mee eens bent.
>
> Wanneer neemt [lidwoord en type decentrale overheid] een besluit over de aanvraag van de vergunning?
> [Lidwoord en type decentrale overheid] heeft de aanvraag voor een vergunning ontvangen op [ontvangstdatum aanvraag vergunning]. [Lidwoord en type decentrale overheid] neemt daarover waarschijnlijk [uiterlijke datum beslistermijn vergunning] een besluit. Als de vergunning wordt verleend, publiceert [lidwoord en type decentrale overheid] een nieuw bericht. Vanaf dat moment kunt u de documenten met informatie over de vergunning bekijken en hierop reageren. U kunt nu nog niet reageren.
>
> Heeft u vragen over de aanvraag van de vergunning?
> U kunt nu alvast de aanvraag van de vergunning bekijken en hierover vragen stellen. Hiervoor kunt u bellen met [lidwoord en type decentrale overheid]. Dit kan via het telefoonnummer [telefoonnummer].
>
>
> De inhoud van de file inhoud.xml is aan te passen naar de tekst van de modelkennisgeving voorbeelden zoals die worden aangeboden door het ministerie. Wanneer het bovenstaande voorbeeld verwerkt zou worden in het inhoud.xml sjabloon voor een gemeente dan zou dat er als volgt uit kunnen zien:

```xml
<inhoud>
      <al><nadruk type="vet">Aanvraag vergunning voor %dvbetreft% aan %dvobjadres%, %dvobjpostcode% in %dvgemeentenaam%</nadruk></al>
      <al>De gemeente %dvgemeentenaam% heeft een aanvraag voor een omgevingsvergunning ontvangen.
          De vergunning is aangevraagd voor %dvbetreft% aan %dvobjadres%. [Mogelijke toelichting en uitleg over activiteit].
          </al>
      <al><nadruk type="vet">Waarom publiceert de gemeente dit bericht?</nadruk></al>
      <al>Een omgevingsvergunning wordt bij de gemeente aangevraagd om toestemming te krijgen om iets te bouwen, slopen,
          kappen of aan te leggen. Met dit bericht laat de gemeente u weten dat er misschien iets verandert in uw omgeving.
          Dan kunt u op tijd reageren als u het hier niet mee eens bent.
          </al>
      <al><nadruk type="vet">Wanneer neemt de gemeente een besluit over de aanvraag van de vergunning?</nadruk></al>
      <al>De gemeente heeft de aanvraag voor een vergunning ontvangen op %ddstartdatum%. De gemeente neemt daarover waarschijnlijk [uiterlijke datum
          beslistermijn vergunning] een besluit. Als de vergunning wordt verleend, publiceert de gemeente een nieuw bericht.
          Vanaf dat moment kunt u de documenten met informatie over de vergunning bekijken en hierop reageren.
          U kunt nu nog niet reageren.
          </al>
      <al><nadruk type="vet">Heeft u vragen over de aanvraag van de vergunning?</nadruk></al>
      <al>U kunt nu alvast de aanvraag van de vergunning bekijken en hierover vragen stellen.
          Hierover kunt u bellen met de gemeente. Dit kan via het telefoonnummer [telefoonnummer].
          </al>
  </inhoud>
```

### Preview van de publicatie

Indien het configuratie-item:

  - Sectie: *DROPPUBLICATIES*,
  - Item: *ToonDROPPreview* is aangevinkt,

dan zal bij het publiceren van een enkele zaak vanuit het publicatiedetailscherm eerst een preview getoond worden. De wizard waarmee men het publiceren van de zaak start, zal uitgebreid zijn met een tweede scherm waar de preview te zien is.

#### Opmaak

De preview is slechts een weergave van het gevulde XML bestand dat REM aanlevert aan de DROP. Er is geen opmaak van dit voorbeeld mogelijk.

### Geo gegevens van de publicatie

Open wave vult bij de publicatie bij de geodata op; grond van punt of vlak of lijn

Onderstaande tekening toont een stroomschema van het algoritme. Wanneer het sluitpaar van een polygoon ongelijk is aan het beginpaar wordt het vlak als lijn (linestring) behandeld.

![Polygoonenvlak in DROP](../img/applicatiebeheer/instellen_inrichten/polygoonenvlakindrop.png) { class="media" loading="lazy" alt="" width="800" }

Overigens is het polygoon op hoofdzaakniveau (bijv. tbomgvergunning.dvgmlpolygoon) alleen zichtbaar en muteerbaar indien de instelling *Sectie: Programma en Item: VlakNietOpZaakniveau* NIET aangevinkt is. Indien wel aangevinkt dan is zowel het blok onzichtbaar als de menu optie teken vlak op kaart.
