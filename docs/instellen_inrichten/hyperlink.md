# Hyperlink

Wanneer een fileserver wordt gebruikt om aanvullende informatie of documenten bij een zaak of inrichting op te slaan kan het handig zijn om vanuit OpenWave zichtbaar te hebben, waar deze zaak-documenten op de fileserver staat. De kolom dvhyperlink op de zaakpagina's van de verschillende modules kan hiervoor automatisch worden gevuld bij het aanmaken van een zaak.

### Hyperlink-definitie

Via het portal beheerportaal-Nieuw kunnen in de tabel tbinitialisatie (tegel *Configuratie*) één of meer rijen worden aangemaakt met *Sectie: Hyperlink_basis*
De kolom *Item* kan daarbij gevuld worden met:

* Omgeving
* Inrichting
* Bouw
* Overige
* Horeca
* Info
* Handhaving
* MilGebr

In  de kolom *Tekst* kan vervolgens de basismap worden opgegeven (ALS UNC-PAD !!!) die hoort bij de zaak, waarbij het programma dynamisch:

* de substring `%zaakjaar%` vervangt door de vier cijfers van het jaar van de ontvangst/aanvraagdatum van de Wave-zaak (dit kan dus niet bij inrichting)
* de substring  `%zaakjaar%`  vervangt door de vier cijfers van het jaar + de twee cijfers van de maand van de ontvangst/aanvraagdatum van de Wave-zaak (dit kan dus ook niet bij inrichting)
* de substring  `%zaaknr%`  vervangt door de Wave-zaakcode van de zaak. Of het inrichtingsnummer bij een inrichting.

`[\\URANUS\Organisatie\Wave](file://///URANUS/Organisatie/Wave.md)\%zaakjaar%\%zaaknr%`.

**Let op:** De basismap moet beginnen met de documentroot (kolom *Tekst* van de instelling *Sectie: Documenten, Item: Documentroot*).

### Automatisch vullen van kolom dvhyperlink bij aanmaken zaak

Indien bij het aanmaken van een zaak het programma bij de desbetreffende module ziet dat bovengenoemde instelling bestaat en is gevuld dan wordt de kolom dvhyperlink bij de nieuwe zaak of inrichting automatisch gevuld met de basismap, waarbij de variabelen zaakjaar, zaakjaarmaand en zaaknr zijn vervangen met de waardes van de nieuwe kaart.

`[\\URANUS\Organisatie\Wave](file://///URANUS/Organisatie/Wave.md)\%zaakjaar%\%zaaknr%` zou dus in de kolom dvhyperlink bij de betreffende zaak kunnen worden: `[\\URANUS\Organisatie\Wave\2018\2018RV00089](file://///URANUS/Organisatie/Wave/2018/2018RV00089.md)`.

De kolom dvhyperlink komt voor in tbomgvergunning, tbbouwvergunningen, tbovvergunningen, tbmilvergunningen, tbhandhavingen, tbinfoaanvragen, tbhorecavergunningen en tbmilinrichtingen.

In geval dat de zaak behoort bij een compartiment, dan zal ook de kolom dlautoaanmaakmappen van het betreffende compartiment aangevinkt moeten zijn. De documentroot zal bij een compartiment in de basismap door OpenWave on the fly worden vervangen door de inhoud van de kolom *Documentroot in satellite.ini* (dvsateldocroot) van het betreffende compartiment (beheerportaal-Nieuw).

Indien de instelling *Sectie: Koppeling OLO en Item: Aanmaakmappen* aangevinkt is zal de kolom dvhyperlink ook gevuld worden bij het automatisch verwerken van een OLO of DSO-bericht. In geval echter dat de zaak behoort bij een compartiment, dan zal de kolom dloloautoaanmaakmappen van het betreffende compartiment aangevinkt moeten zijn.

### Zichtbaar maken van kolom dvhyperlink indien gerechtigd

Bij de rechtengroepen (beheertegel *Functionele rechten*) kan per rechtengroep aangevinkt worden of de inlogger geautoriseerd is voor hyperlink gebruik: toegang tot alle mappen en hyperlink (kolom: dlmappenhyperlink).

Op basis van dit recht kan de kolom dvhyperlink en bijbehorende ga-naar-knop in het detailscherm zichtbaar of onzichtbaar worden gemaakt. De kolom dvhyperlink (en de ga-naar-schermknop: zie hieronder) kan opgenomen worden in een apart blok in het detailscherm van de zaak/inrichting. Dit blok kan onzichtbaar zijn voor niet geautoriseerde op grond van een conditie gebaseerd op bovengenoemd recht. Zie hiertoe het voorbeeld onder het kopje *Queries om blokken onzichtbaar te maken in detailscherm* bij [Queries](/docs/instellen_inrichten/queries.md)).

### Koppelen van de dvhyperlink aan actions met schermknop

Achter de kolom dvhyperlink kunnen drie schermknoppen zichtbaar zijn:

* ga naar
* zet hyperlink in klembord
* verplaats mappen/documenten

#### Ga Naar (**DEPRECATED!**)

Met deze knop wordt de de inhoud van de kolom hyperlink omgezet in de URL-vorm file:**/xxx/xxx zodat de verkenner wordt gestart op de gewenste map.

Dit werkt alleen indien IE, vandaar deprecated. De knop heeft als action `<action>openTabPage(file:*/%query(omgeving_kolomhyperlink,%keypointer%)%)</action>*`.

#### Zet hyperlink in klembord

Met deze knop wordt de inhoud van de kolom dvhyperlink in het klembord geplaatst.

#### verplaats mappen/documenten

Met deze knop (alleen zichtbaar indien de gebruiker het recht *verplaatsen documenten in documentenTree* (bijv. tbomgrechten.dlcomgcorverplaats) heeft) kan de gebruiker binnen een flexTree scherm van OpenWave, mappen en documenten vanaf de hyperlink beheren. Zie [Verplaatsen van bestanden in OpenWave (fileshare)](/docs/probleemoplossing/programmablokken/verplaatsen_bestanden_fileshare.md).

### Daadwerkelijk aanmaken van mappen op de fileserver

Bij het maken van een nieuwe zaak kijkt het programma:

* indien de zaak NIET behoort bij een compartiment of
  * de instelling *Sectie: Documenten, Item: OphalenViaFileserver* aangevinkt is
  * EN de instelling *Sectie: Documenten Item: AutomAanmaakFileservermappen* aangevinkt is
* indien de zaak WEL behoort bij een compartiment of
  * de de kolom dlautoaanmaakmappen van het betreffende compartiment aangevinkt is
  * EN de kolom fileserver via satellite (dlfileserver) van het betreffende compartiment aangevinkt is (beheerportaal-Nieuw)

Is dat het geval dan zullen bij het aanmaken van een nieuwe zaak of inrichting automatisch de mappen genoemd in de rijen van *Sectie: Aanmaakmappen* worden aangemaakt. Hierbij uitgezonderd zijn de mappen waarin de variabelen, `%bezwaarnr%`,  `%adviesnr%`  en  `%inspnr%`  zijn opgenomen.

Ook hier geldt dat in het geval dat de zaak behoort bij een compartiment, dat het documentroot-gedeelte in de aan te maken mappen door OpenWave on the fly worden vervangen door de inhoud van de kolom *Documentroot in satellite.ini* (dvsateldocroot) van het betreffende compartiment (beheerportaal-Nieuw).
