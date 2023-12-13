# Lijst met te exporteren CBS-gegevens (vwfrmcbsexport)

Lijst met hierin de te exporteren CBS-gegevens (onderliggende view is vwfrmcbsexport). De lijst wordt gevuld met behulp van de lijstknoppen. De lijst is zo opgesteld dat gebruikers alleen de regels uit vwfrmcbsexport zien die aan de voor hun geldende compartimentsrechten voldoen. Dit geldt ook voor de acties achter de knoppen op het lijstscherm: afhankelijk van de ingelogde gebruiker, hebben de acties effect op alleen de voor die gebruiker beschikbare CBS-gegevens. Een gebruiker zal dus niet voor een ander compartiment de CBS export kunnen uitvoeren.

De lijst is zichtbaar indien de inlogger lid is van een rechtengroep die op overkoepelend niveau het recht _CBS exporteren (tbrechten.dlcextcbs11disk)_ aan heeft staan (zie beheertegel _Functionele rechten_, blok _Overig_ in het detailscherm van de rechten).

## Definitie

- Voor de definitie van de lijst en knoppen: zie beheertegel _Tabellen Standaardapi_ (tbsysstandardtable.dvcode = operations_vwfrmcbsexport)
- De lijst-schermidentifier is: MDLC_getVwfrmCBSExportList.xml (zie beheertegel _Schermkolomdefinitie tabellen standaard-api_)
- De onderliggende view is: vwfrmcbsexport

## Bijzondere kolommen

- de eerste kolom is een kleurbol die aangeeft of de onderliggende zaak van de CBS-regel wel een **Verleende vergunning** betreft. Indien de kleurbol wit is dan betekent het dat de zaak een gevulde besluitdatum heeft en status _Verleend_. Is de kleurbol oranje dan is aan een van deze condities niet voldaan. Dit kan voorkomen indien de instelling aan staat (of aan heeft gestaan) _Sectie: Programma Item: CBSZichtbaarNegeerZaakstatus_. Is dat het geval dan mogen namelijk ook CBS-regels worden aangemaakt in OpenWave voor vergunningen waarvan de besluitdatum nog niet gevuld is en/of het aardbesluit niet verleend is. Er kan bij de export aangegeven worden of men de oranje regels toch mee wilt nemen in het exportbestand (default worden alleen de witte (en dus valide) CBS-regels meegenomen in de export)
- de kolom **Gem.nr** (tbcbsexport.dvgemeentevolgnr) bevat het door de programmatuur samengestelde Gemeentenummer. Dit is het viercijferige gemeenteid van de gekozen gemeente waarop de lijst gebaseerd is, aangevuld met voorloopnullen en/OF aangevuld met de waarde van kolom _Tekst_ (waarde mag maximaal twee cijfers zijn) van instelling _Sectie: CBS en Item:`<gemeentecode>`(bijvoorbeeld '0228')_ tot 6 cijfers. Het Gemeentenummer van iedere CBS-exportregel dient volgens de handleiding van het CBS uit 6 cijfers te bestaan, vandaar dat de programmatuur deze gaat berekenen. Indien men bijvoorbeeld gekozen heeft voor gemeente Ede (gemeenteid = 0228) bij het opstellen van de exportlijst, dan zal het Gemeentenummer default de waarde _000228_ hebben. Bestaat er echter de instelling _Sectie: CBS en Item: 0228_ met _Tekst_ = 02 (fictief voorbeeld), dan is het Gemeentenummer _022802_
- de kolom **Uw volgnr** bevat de waarde van:
  - indien instelling _Sectie: CBS Item: DMScode_ aangevinkt staat en er is een gevulde DMS zaakcode voor de onderliggende omgevingszaak van de CBS regel, dan de DMS zaakcode (tbomgvergunning.dvintzaakcode)
  - anders de door Openwave gegenereerde wavezaakcode van de onderliggende omgevingszaak van de CBS regel (tbomgvergunning.dvzaakcode). In het daadwerkelijke exportbestand mag deze waarde maar 20 tekens lang zijn van het CBS: is het volgnummer langer dan wordt het afgekapt in het exportbestand om aan de toegestane limiet te voldoen
- de kolom **Gem. id zaak** (tbcbsexport.dvgemeenteid) bevat de gemeenteid van de onderliggende omgevingszaak van de CBS-regel: dit is de gemeentecode die hoort bij de woonplaats waarin de zaak zich afspeelt. Het kan zo zijn dat het gemeentid van de zaak verschilt van het gemeenteid van de gekozen gemeente bij het opstellen van de lijst: dit is het geval indien het bevoegd gezag van de zaak gevuld is en van de gekozen gemeente is maar de zaak zich in een andere gemeente dan het bevoegd gezag afspeelt. Is dit het geval dan ziet u een verschil met kolom **Gem. nr** waarin het gemeenteid van de gekozen gemeente tijdens het opstellen van de lijst is opgenomen

### Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie [Scherm(kolom)definitie](../../../../instellen_inrichten/schermdefinitie/README.md)) die niet valide is
- de inlogger heeft geen recht om CBS te exporteren (tbrechten.dlcextcbs11disk).

![](../../img/applicatiebeheer/instellen_inrichten/probleemoplossing/programmablokken/cbslijstexportgegevens.png){ class="media" loading="lazy" alt="" width="1000" }

### Triggers

Dubbel klikken op een regel opent het detailscherm van de CBS-exportregel. Altijd enabled. Op het detailscherm kan men geen gegevens wijzigen maar wel indien gewenst een opmerking noteren die opgenomen zal worden in het exportbestand. In het blok _Vergunning gegevens_ bevindt zich naast het veld _Uw volgnummer_ een doorverwijsknop naar de onderliggende omgevingszaak.

### Vraagtekenknop: Is er een proces bezig?

De knop ![](../../img/applicatiebeheer/instellen_inrichten/instellen_inrichten/schermdefinitie/vraagteken.jpg){ class="media" loading="lazy" title="vraagteken.jpg" alt="vraagteken.jpg" width="20" } geeft antwoord op vraag of een andere medewerker op dat moment al bezig is een CBS-exportproces uit te voeren. Bij het samenstellen van de lijst en ook bij het opstellen van het exportbestand wordt in de configuratietabel _Getal1_ van de rij met _Sectie: Operations en Item: ExportCBS_ op 1 gezet. Daarmee wordt voorkomen dat twee processen tegelijk kunnen starten. OpenWave zet deze waarde automatisch weer op 0 als een proces wordt beëindigd.

### Verversknop

Zowel het samenstellen van de lijst als het opstellen van het exportbestand gebeurt door een zogenaamd runnable programma. Dat betekent dat de gebruiker nadat het proces is gestart door kan gaan met andere werkzaamheden. Onder water voert de runnable zijn taken uit. Dat betekent ook dat de wijzigingen in de lijst niet voortdurend door die runnable worden uitgeschreven. Met deze knop ![]../../img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/refresh_2.jpg){ class="media" loading="lazy" alt="" width="20" } kan de lijst ververst worden. De gebruiker kijkt naar de dan naar de actuele situatie mits de vraagtekenknop meldt dat er geen proces meer loopt.

### Wizard: Genereer nieuwe exportlijst

Met de knop ![](../../img/applicatiebeheer/instellen_inrichten/instellen_inrichten/schermdefinitie/start_wizard2.jpg){ class="media" loading="lazy" alt="" width="20" } _Genereer nieuwe exportlijst_ wordt een scherm getoond waarbij de gemeente gekozen moet worden waarvoor men de CBS-gegevens wilt exporteren. Er kan gekozen worden uit gemeentes waarvoor in beheer bij de _OIN-tabel_ de eigenschap **Opnemen in keuzelijst maken CBS-exportlijst** aangevinkt staat.

Het programma zal de CBS regels (tbcbs_gegevens_w011) doorlopen en toevoegen aan de lijst met te exporteren CBS-gegevens (tbcbsexport). Op de te doorlopen CBS regels zijn de volgende condities van toepassing:

- indien de inlogger niet gelieerd is aan een compartiment, mag de inlogger alleen kiezen uit gemeentes die niet onder een compartiment vallen
- indien de inlogger wel gelieerd is aan een compartiment, mag de inlogger alleen kiezen uit gemeentes die onder het eigen compartiment vallen. De regels die aan de lijst worden toegevoegd zullen dnkeycompartiment krijgen van de inlogger
- de onderliggende zaak van de CBS regels (tbcbs_gegevens_w011) dient voor de gekozen gemeente te zijn. Dit houdt in dat:
  - indien het bevoegd gezag is gevuld voor de zaak, de CBS regel wordt meegenomen als het bevoegd gezag overeenkomt met gekozen gemeente tijdens genereren van de lijst (tboin.dvgemeenteid is gekozen gemeenteid). **Let op:** in dit geval kijkt het programma dus niet naar de locatie van de zaak!
  - indien het bevoegd gezag niet gevuld is voor de zaak dan wordt de CBS regel meegenomen als de zaak zich afspeelt in de gekozen gemeente (op basis van tbperceeladressen)
- verstuurdatum van de CBS regel (tbcbs_gegevens_w011.ddverstuurd) is **niet gevuld**

### Verwijderknop

Met de knop ![](../../img/applicatiebeheer/instellen_inrichten/instellen_inrichten/schermdefinitie/delete.jpg){ class="media" loading="lazy" title="some colspan" alt="some colspan" "width="20" } kan de inlogger de actieve CBS-exportregel uit de lijst verwijderen. Dit betekent niet dat de onderliggende CBS-regel verwijderd wordt! Alleen de regel in tbcbsexport.

### Wizard: Exporteer items in deze lijst (exportbestand wordt gemaakt)

Met de knop ![](../../img/applicatiebeheer/instellen_inrichten/instellen_inrichten/schermdefinitie/factuur3.jpg){ class="media" loading="lazy" alt="" width="20" } wordt op basis van de lijst met te exporteren CBS-gegevens, een exportbestand opgesteld waarvoor geldt dat:

- het compartiment overeenkomt met dat van de inlogger
- de kleurbol van de regel wit is (tenzij in de wizard gekozen voor ook meenemen van de niet Verleende vergunningen: dan worden de regels met oranje kleurbol ook meegenomen in de export).

Na het genereren van het exportbestand wordt de lijst met te exporteren CBS-regels volledig leeggemaakt (dus ook regels met oranje kleurbol die niet standaard opgenomen worden in het exportbestand) indien er bij de export gekozen is voor optie _Definitief_. Is er voor optie _Test_ gekozen dan blijft de lijst gevuld en kan het genereren van het exportbestand voor de lijst herhaald worden.

### Lijstknop: Exportbestanden (via deze lijst kan gewenste exportbestand gedownload worden)

Met de knop ![](../../img/applicatiebeheer/instellen_inrichten/instellen_inrichten/schermdefinitie/lijst2.jpg){ class="media" loading="lazy" alt="" width="20" } wordt een lijstscherm geopend waarin de logging terug te vinden is van het genereren van de exportbestanden. Iedere keer als een exportbestand gegenereerd wordt, zal een nieuwe regel in het dit scherm verschijnen. Het exportbestand zelf ligt opgeslagen in de logging regel en is te downloaden in het lijstscherm via de downloadknop: download het exportbestand achter de actieve (geel gearceerde) regel. Men kan ook doorklikken naar het detailscherm van de logging en daar het bestand downloaden.
