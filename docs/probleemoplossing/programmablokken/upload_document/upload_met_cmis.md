# Upload documenten met CMIS

De volgende instellingen zijn hierbij noodzakelijk:

## Endpoint

Het eindpoint van de DMS-server die de CMIS berichten verwerkt

* *Sectie: KoppelingDOCNAARDMS*
* *Item: Ontvangstadres_cmis*

In de kolom *Tekst*: het endpoint (bijvoorbeeld: `[https://doc.mijndms.nl/alfresco/cmisatom](https://doc.mijndms.nl/alfresco/cmisatom.md)`).

### Loginnaam

De loginnaam die OpenWave moet gebruiken voor toegang tot de DMS-server met rechten om mappen te maken/verwijderen en documenten te plaatsen/verwijderen.

* *Sectie: KoppelingDOCNAARDMS*
* *Item: Login_cmis*
* *Tekst*: de loginnaam

### Password

Het password dat OpenWave moet gebruiken voor toegang tot de DMS-server

* *Sectie: KoppelingDOCNAARDMS*
* *Item: Pass_cmis*
* *Tekst*: het password

Zie ook: [2-way encryptie van externe wachtwoorden](/docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md).

## Mogelijke mappen met CMIS-protocol

OpenWave moet eerst bepalen op welke map(pen) van het DMS documenten geplaatst mogen worden.
OpenWave gaat er daarbij vanuit dat de documenten achter de vermeldde repository (de centrale plaats) logisch ingedeeld zijn naar op zijn minst de hoofdzaakcodering.
Dit gebeurt op drie manieren.

### Op de basismap van een hoofdzaak

Dit is het geval indien:

* de instelling *Sectie: Documenten Item: Autorisatiemappen* aangevinkt is
* EN de inlogger is lid van een rechtengroep die het recht *Toegang tot alle mappen en dvhyperlink (tbrechten.dlmappenhyperlink)* aangevinkt heeft staan.

Wanneer de inlogger in deze situatie één of meer documenten aanwijst om up te loaden, kijkt het programma naar de kolom *Info* van de instelling *Sectie: Hyperlink_basis en Item: Omgeving* (of Overige of Handhaving of Inrichting of Info of Horeca of Milgebr of Bouw).

In deze kolom *Tekst* worden vervolgens de variabelen:

* `%zaakjaar%` vervangen door het jaar (jjjj) van de begindatum van de betreffende hoofdzaak (dus niet bij inrichting)
* `%zaakjaar%` vervangen door de jaarmaand (jjjjmm) van de begindatum zaak van de betreffende hoofdzaak (dus niet bij inrichting)
* `%zaaknr%` vervangen met de wavezaakcode van de betreffende hoofdzaak of inrichting.

De inlogger kan dus niet kiezen: er is maar één map die in aanmerking komt.

### Alleen op één van de expliciet toegekende (sub)mappen per zaak op rechtengroepniveau

Dit is het geval indien:

* de instelling *Sectie: Documenten Item: Autorisatiemappen* aangevinkt is
* EN de inlogger is GEEN lid van een rechtengroep die het recht *Toegang tot alle mappen en dvhyperlink (tbrechten.dlmappenhyperlink)* aangevinkt heeft staan.

Wanneer de inlogger in deze situatie één of meer documenten aanwijst om up te loaden, kijkt het programma naar toegekende mappen (de kolom map tbrechtengroepmappen.dvmapcmis) van de rechtengroep waar hij/zij lid van is (beheertegel *Functionele rechten*: lijst in detailscherm van rechtengroep). Het gaat daarbij om de niet vervallen rijen waarbij *upload* aangevinkt is.
In deze kolom dvmapcmis worden vervolgens de variabelen:

* `%zaakjaar%` vervangen door het jaar (jjjj) van de begindatum van de betreffende hoofdzaak (dus niet bij inrichting)
* `%zaakjaar%`  vervangen door de jaarmaand (jjjjmm) van de begindatum zaak van de betreffende hoofdzaak (dus niet bij inrichting)
* `%zaaknr%`  vervangen met de wavezaakcode van de betreffende hoofdzaak of inrichting
* `%inspnr%`  met de wavezaakcode van de inspectiekaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een inspectiedetailkaart)
* `%adviesnr%`  met de wavezaakcode van de advieskaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een adviesdetailkaart)
* `%bezwaarnr%` met de wavezaakcode van de bezwaar/beroep kaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een bezwaar/beroep detailkaart)

Indien er meer dan één map in aanmerking komt, zal de inlogger een keuze moeten maken..

### Op één van de (sub)mappen per (deel)zaak zoals gedefinieerd in Sectie Aanmaakmappen

Dit is het geval indien de instelling *Sectie: Documenten Item: Autorisatiemappen* NIET aangevinkt is.

Het programma interpreteert bezwaar/beroep, adviezen en inspecties als deelzaken bij een hoofdzaak en kan zo nodig de bijbehorende documenten van de deelzaak op een aparte submap van de hoofdzaak plaatsten.

OpenWave gaat er met het CMIS-protocol van uit dat de documenten in het DMS logisch ingedeeld worden naar op zijn minst zaakcodering in een mappenstructuur achter de repository (de centrale plaats).

#### Bepaling modulemap

Om de mogelijke mappen te bepalen waarop de gebruiker de uploads kan plaatsen kijkt het programma naar de instellingen van *Sectie: AanmaakMappen* en *Item:* begint met:

* indien module = V dan 'Inrichting_'
* indien module = W dan 'Omgeving_'
* indien module= B dan 'Bouw_'
* indien module = O dan 'Overige_'
* indien module = H dan 'Handhaving_'
* indien module = C dan 'Horeca_'
* indien module = E dan 'MilGebr_'
* indien module = I dan 'Info_'

##### Bepaling submap(pen) bij module

* indien de instelling *Sectie: Documenten* en *Item: SpecialeUploadMappen* aangevinkt is dan worden alleen de rijen meegenomen waarin een '2' voorkomt in *Getal2* (dus bijvoorbeeld *Getal2* = 2 of 21).
* indien de tabel van waaruit geüpload wordt anders is dan tbadviezen, tbbezwaarberoep of tbinspecties dan worden alleen de rijen meegenomen waarin een '4' voorkomt in *Getal1* (dus bijvoorbeeld *Getal1* = 4 of 14)
* indien geüpload wordt vanuit tbadviezen dan worden alleen de rijen meegenomen waarin een '1' voorkomt in *Getal1*
* indien geüpload wordt vanuit tbinspecties dan worden alleen de rijen meegenomen waarin een '2' voorkomt in *Getal1*
* indien geüpload wordt vanuit tbbezwaarberoep dan worden alleen de rijen meegenomen waarin een '5' voorkomt in *Getal1*.

##### Substitutie variabelen

Van de rijen uit de instellingen bij *Sectie: Aanmaakmappen* die aan bovenstaande voldoen wordt de kolom *Info* gebruikt in een hulprijtje. De kolom *Info* bevat de echte map in het DMS, maar OpenWave zal hierop eerst nog een substitutie uitvoeren op de volgende variabelen:

* `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie (geldt niet voor de regels met *Getal1* = 4 EN waarvan kolom *Item* begint met Inrichting_)
* `%zaakjaar%`  door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie (geldt niet voor de regels met *Getal1* = 4 EN waarvan kolom *Item* begint met Inrichting_)
* `%zaaknr%`  met de Wavezaakcode van de hoofdzaak (of met het inrichtingsnummer indien Inrichting)
* `%inspnr%`  met de Wavezaakcode van de inspectiekaart (dus alleen bij *Getal1* = 2)
* `%adviesnr%`  met de wavezaakcode van de advieskaart (dus alleen bij *Getal1* = 1)
* `%bezwaarnr%` met de wavezaakcode van de bezwaar/beroepkaart (dus alleen bij *Getal1* = 5).

**Voorbeeld**
OpenWave\Omgeving\%zaakjaar%\%zaaknr%

wordt na substitutie bijvoorbeeld

OpenWave\Omgeving\2012\2013RP0044\

Uiteindelijk leveren deze instellingen dus een of meer DMS-mappen op waar het programma documenten kan plaatsen bijvoorbeeld:

* OpenWave\Omgeving\2012\2013RP0044\
* OpenWave\Omgeving\2012\2013RP0044\Adviezen
* OpenWave\Omgeving\2012\2013RP0044\Inspecties

Indien dit rijtje bestaat uit 0 mappen dan gaat het uploaden niet door (het programma weet dan niet waar de upload te plaatsen).

Indien dit rijtje bestaat uit 1 map dan hoeft het programma niet aan de gebruiker een extra keuze te vragen uit de mogelijkheden.

Indien dit rijtje bestaat uit meer dan 1 map dan zal de gebruiker hieruit een extra keuze moeten maken.

Indien in het DMS de map niet bestaat waarop het document geüpload moet worden, dan maakt het programma deze automatisch aan.

**LET OP**: indien instelling *Sectie: Documenten* en *Item: SpecialeUploadMappen* aangevinkt is en u wilt uploaden bijvoorbeeld vanuit inspecties bij een omgevingszaak, dan verwacht OpenWave dus minimaal één kaart bij *Sectie: AanmaakMappen* en *Item* begint met Omgeving_ waarbij *Getal1* de waarde 2 heeft (inspecties)
en *Getal2* ook de waarde 2 (uploadmap), anders komt foutcode 706: ontbrekende instellingen.
