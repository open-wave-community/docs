# Upload documenten naar fileshare

De volgende instellingen zijn noodzakelijk:

## Root

Allereerst moet de kolom _Tekst_ bij de instelling _Sectie: Documenten_ en _Item: DocumentRoot_ gevuld zijn met een UNC-map, bijvoorbeeld `[\\CORK\OpenWave\Documents](file://///CORK/OpenWave/Documents.md)`, die verwijst naar een map op de fileshare waarachter documenten vanuit OpenWave opgeslagen kunnen worden.

Deze root moet een substring zijn van de gedefinieerde mappen in de _Sectie: Aanmaakmappen_.

Vanuit een installatie in de Cloud van OpenWave zal het contact met een fileshare via de installatie van satellite lopen. De rootmap kan in de (lokaal geïnstalleerde) satellite-ini worden overschreven.

Op die rootmap (en daarmee op alle submappen) dient een gebruiker gedefinieerd te zijn met voldoende rechten die OpenWave gebruikt om documenten te plaatsen en te tonen.

Ook in het geval dat de zaak waar de documenten naar toe worden geüpload valt onder een compartiment (al of niet met satellite) geldt het bovenstaande.

## Authenticatie

- Indien de zaak waar de documenten naar toe worden geüpload NIET valt onder een compartiment (of wel, maar het compartiment gebruikt geen satellite) dan:
  - _Sectie: Documenten Item: OphalenViaFileserver_Username_. In kolom _Tekst_ komt de inlognaam die gebruikt wordt om:
    - indien de fileserver rechtstreeks zonder satellite (dus on premisse) wordt benaderd, de documenten op te slaan of te verwijderen achter de documentroot
    - indien de fileserver via satellite wordt benaderd, dan moet deze username overeenkomen met de tag api_name uit de lokaal geïnstalleerde satellite.ini. In de satelllite-ini zijn apart de credentials gedefinieerd die toegang geven tot de fileshare.
  - _Sectie: Documenten Item: OphalenViaFileserver_Password_. In kolom _Tekst_ komt het password dat hoort bij de OphalenViaFileserver_Username:
    - indien de fileserver rechtstreeks zonder satellite (dus on premisse) wordt benaderd is dit het password dat toegang geeft tot de fileshare
    - indien de fileserver via satellite wordt benaderd, dan moet deze userpass overeenkomen met de tag api_pass uit de lokaal geïnstalleerde satellite.ini.
- Indien de zaak waar de documenten naar toe worden geüpload WEL valt onder een compartiment en de kolom dlsatellite van dat compartiment is aangevinkt, dan zijn username en password bij het betreffende compartiment in het blok satellite opgeslagen (beheerportaal-Nieuw).

Zie ook: [2-way encryptie van externe wachtwoorden](../../../../instellen_inrichten/2way_encryptie_externe_wachtwoorden.md).

## Tracering

### Windows Internet Naming Service

Kolom _Tekst_ van _Sectie: Documenten Item: OphalenViaFileserver_Wins_ het IP-adres van de machine met de Windows Internet Naming Service.

### Het domein van de fileshare

- Indien de zaak waar de documenten naar toe worden geüpload NIET valt onder een compartiment (of wel, maar het compartiment gebruikt geen satellite) dan:
  - geen satellite (dus OpenWave is on premisse geïnstalleerd) dan de kolom _Tekst_ van _Sectie: Documenten en Item: OphalenViaFileserver_Domain_ In kolom _Tekst_ de domeinnaam waarin rechten van username en password geregeld zijn
  - wel satellite maar de zaak waar vanuit geüpload wordt valt NIET in een compartiment, dan de kolom _Tekst_ van _Sectie: Satellite Item: Domain_.
- Indien de zaak waar de documenten naar toe worden geüpload WEL valt onder een compartiment en de kolom dlsatellite van dat compartiment is aangevinkt dan de kolom _Domein_ op de detailkaart van het betreffende compartiment (beheerportaal-Nieuw) in het blok satellite.

## Protocol

Indien satellite (al of niet in combinatie met compartiment) dan staat het protocol waarmee de fileshare wordt benaderd in de lokaal geplaatste ini-file die hoort bij de satellite-installatie. Standaard vanaf 1.28 is SMBTWO.

Indien geen satellite dan is SMBTWO het leidende protocol.

## Satellite

Indien er verbinding vanuit de Cloud wordt gezocht met een fileserver dan is een installatie van een aparte OpenWave satellite-server binnen het LAN noodzakelijk. Het programma verwacht dat deze satellite-server aanwezig is indien:

- de zaak waar vanuit wordt geüpload NIET valt onder een compartiment en de kolom _Tekst_ van _Sectie: Documenten, Item: OphalenViaFileserver_ gevuld is met de waarde 'Satellite'
- de zaak waar vanuit wordt geüpload WEL valt onder een compartiment en de kolom _fileserver via Satellite_ op de detailkaart van het betreffende compartiment (beheerportaal-Nieuw) aangevinkt is.

Zie voor werking en overige instellingen: [Satellite t.b.v. benadering fileserver](../../../../instellen_inrichten/satellite_filesysteem.md) en zie voor ketenvoorbeeld: [Ketenvoorbeeld Upload vanuit Cloud](upload_document/ketenvoorbeeld_uplload_vanuit_cloud.md).

## Overschrijven of dupliceren onder nieuwe naam

Bij uploaden naar fileshare kijkt het programma of de file reeds bestaat. Indien:

- de zaak waar vanuit wordt geüpload NIET valt onder een compartiment
- en Indien _Getal1_ van de instelling: _Sectie: Documenten Item: OphalenViaFileserver_ de waarde = 1 heeft
- en de file bestaat reeds

OF indien:

- de zaak waar vanuit wordt geüpload WEL valt onder een compartiment
- en de kolom _bestaande files overschrijven_ van de detailkaart van het betreffende compartiment (beheerportaal-Nieuw) is NIET aangevinkt
- en de file bestaat reeds

dan wordt de file onder de een nieuwe naam geplaatst (het naamdeel van de filenaam wordt hiertoe uitgebreid met '(n)' bijvoorbeeld mijndocument(1).txt of mijndocument(12).txt.
n kan maximaal 999 keer worden opgehoogd.
Indien niet aan deze voorwaarden voldaan is - of de file wordt geüpload na bewerking in OnlyOffice -, dan wordt de bestaande file overschreven.

### Bijwerken geregistreerde documentenkaart

Indien de instelling _Sectie: DocumentRegistreren Item: BestaandeRegNegerenBijUploadPostfix_ is aangevinkt en er wordt een upload gedaan van een document naar fileshare waarbij dat document met een postfix (n) wordt opgeslagen en er blijkt een geregistreerde documentkaart te zijn onder de oorspronkelijke naam (dus in tbcorrespondentie) bij de betreffende zaak, dan wordt die geregistreerde documentkaart NIET bijgewerkt. Anders dus wel.

## Waarschuwen bij doublure in naam

Indien:

- er bij een zaak een file wordt geüpload naar een fileshare
- en de zaak speelt NIET in een compartiment
- en _Getal1_ van de instelling _Sectie: Documenten Item: OphalenViaFileserver_ is ongelijk aan 1

dan zal het programma controleren of er al een file bestaat met dezelfde naam bij die zaak en zo nodig een waarschuwing geven.

Indien _Getal1_ van bovengenoemde instelling de waarde 1 heeft, betekent dat er nooit doublures kunnen ontstaan omdat de filenaam in dat geval wordt uitgebreid met een tellertje: test.txt en test(1).txt.

## Mogelijke mappen

OpenWave moet eerst bepalen op welke map(pen) documenten geplaatst mogen worden.
OpenWave gaat er daarbij vanuit dat de documenten achter de vermelde Documentroot logisch ingedeeld zijn naar op zijn minst de hoofdzaakcodering.
Dit gebeurt op drie manieren.

### Op één van de (sub)mappen per zaak op basis van kolom dvhyperlink

Dit is het geval indien:

- de instelling _Sectie: Documenten Item: Autorisatiemappen_ aangevinkt is
- en de inlogger is lid van een rechtengroep die het recht _Toegang tot alle mappen en dvhyperlink (tbrechten.dlmappenhyperlink)_ aangevinkt heeft staan.

Wanneer de inlogger in deze situatie één of meer documenten aanwijst om up te loaden, kijkt het programma naar de kolom dvhyperlink van de hoofdzaak (dus die van tbomgvergunning, tbinfoaanvragen, tbmilinrichtingen etc.) en zoekt hier alle bestaande submappen bij op. Indien er meer dan één map in aanmerking komt, zal de inlogger een keuze moeten maken..

Deze mappen moeten fysiek bestaan!!! Ze worden dus niet automatisch aangemaakt.

Indien:

- de zaak waar vanuit wordt geüpload NIET valt onder een compartiment
- en de instelling _Sectie: Documenten Item: OphalenViaFileserver_ aangevinkt is
- en de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is

OF indien:

- de zaak waar vanuit wordt geüpload WEL valt onder een compartiment
- en de kolom _documenten opslag fileserver_ op de detailkaart van het betreffende compartiment (beheerportaal-Nieuw) aangevinkt is
- en de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is

dan zullen bij het aanmaken van een nieuwe zaak of inrichting automatisch de mappen genoemd in de rijen van _Sectie: Aanmaakmappen_ worden aangemaakt. Hierbij uitgezonderd zijn de mappen waarin de variabelen `%bezwaarnr%`, `%adviesnr%` en `%inspnr%` zijn opgenomen.

### Alleen op één van de expliciet toegekende (sub)mappen per zaak op rechtengroepniveau

Dit is het geval indien:

- de instelling _Sectie: Documenten Item: Autorisatiemappen_ aangevinkt is
- en de inlogger is GEEN lid van een rechtengroep die het recht _Toegang tot alle mappen en dvhyperlink (tbrechten.dlmappenhyperlink)_ aangevinkt heeft staan.

Wanneer de inlogger in deze situatie één of meer documenten aanwijst om up te loaden, kijkt het programma naar toegekende mappen (de kolom map tbrechtengroepmappen.dvmapfileshare) van de rechtengroep waar hij/zij lid van is (beheertegel _Functionele rechten_: lijst in detailscherm van rechtengroep). Het gaat daarbij om de niet vervallen rijen waarbij _upload_ aangevinkt is.
In deze kolom dvmapfileshare worden vervolgens de variabelen:

- `%zaakjaar%` vervangen door het jaar (jjjj) van de begindatum van de betreffende hoofdzaak (dus niet bij inrichting)
- `%zaakjaar%` vervangen door de jaarmaand (jjjjmm) van de begindatum zaak van de betreffende hoofdzaak (dus niet bij inrichting)
- `%zaaknr%` vervangen met de wavezaakcode van de betreffende hoofdzaak of inrichting
- `%inspnr%` met de wavezaakcode van de inspectiekaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een inspectiedetailkaart)
- `%adviesnr%` met de wavezaakcode van de advieskaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een adviesdetailkaart)
- `%bezwaarnr%` met de wavezaakcode van de bezwaar/beroep kaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een bezwaar/beroep detailkaart)

Het programma zoekt op basis van deze mappen alle bestaande (sub)mappen op de fileserver.
Indien er meer dan één map in aanmerking komt, zal de inlogger een keuze moeten maken..
Indien er geen map is toegekend, dan zal het programma zelf de basismap uit de kolom dvhyperlink van de hoofdzaak (dus die van tbomgvergunning, tbinfoaanvragen, tbmilinrichtingen etc.) toevoegen (zonder submappen).

Deze mappen moeten fysiek bestaan!!! Ze worden dus niet automatisch aangemaakt.

Indien:

- de zaak waar vanuit wordt geüpload NIET valt onder een compartiment
- en de instelling _Sectie: Documenten Item: OphalenViaFileserver_ aangevinkt is
- en de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is

OF indien:

- de zaak waar vanuit wordt geüpload WEL valt onder een compartiment
- en de kolom _documenten opslag fileserver_ op de detailkaart van het betreffende compartiment (beheerportaal-Nieuw) aangevinkt is
- en de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is

dan zullen bij het aanmaken van een nieuwe zaak of inrichting automatisch de mappen genoemd in de rijen van _Sectie: Aanmaakmappen_ worden aangemaakt. Hierbij uitgezonderd zijn de mappen waarin de variabelen, `%bezwaarnr%`, `%adviesnr%` en `%inspnr%` zijn opgenomen.

### Op één van de (sub)mappen per (deel)zaak zoals gedefinieerd in Sectie: Aanmaakmappen

Dit is het geval indien de instelling _Sectie: Documenten Item: Autorisatiemappen_ NIET aangevinkt is.

Het programma interpreteert bezwaar/beroep, adviezen en inspecties als deelzaken bij een hoofdzaak en kan zo nodig de bijbehorende documenten van de deelzaak op een aparte submap van de hoofdzaak plaatsten.

Het programma bepaalt welke mappen getoond kunnen worden op grond van de instellingen per module onder de _Sectie: AanmaakMappen_.

Als er bijvoorbeeld 5 mappen bestaan op de fileshare om documenten in te delen onder een bepaalde omgevingszaak dan worden er ook 5 regels gedefinieerd in OpenWave onder _Sectie: AanmaakMappen_ waarbij de kolom _Item_ begint met 'Omgeving\_'.

Bijvoorbeeld Omgeving_basis, Omgeving_OLO, Omgeving_adviezen en Omgeving_inspecties et cetera.

In de kolommen _Tekst_ van de betreffende regel komen de mappen van de fileshare te staan (in UNC-notatie). Zie ook voorbeeld verderop.

LET OP: al deze mappen moeten dus submappen zijn van de DocumentRoot (de documentroot moet wel onderdeel zijn van de map). Indien er sprake is van een compartiment met een eigen satellite dan wordt de documentroot on the fly overschreven met de documentroot van de satellite.

Het programma redeneert als volgt:

#### Bepaling modulemappen

Om te bepalen waarop de gebruiker de uploads kan plaatsen kijkt het programma naar de instellingen van

_Sectie: AanmaakMappen_.

_Item_ begint met:

- indien module = V dan 'Inrichting\_'
- indien module = W dan 'Omgeving\_'
- indien module = B dan 'Bouw\_'
- indien module = O dan 'Overige\_'
- indien module = H dan 'Handhaving\_'
- indien module = C dan 'Horeca\_'
- indien module = E dan 'MilGebr\_'
- indien module = I dan 'Info\_'

#### Bepaling submap(pen) per module

- indien de instelling _Sectie: Documenten_ en _Item: SpecialeUploadMappen_ aangevinkt is dan worden alleen de rijen meegenomen waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21)
- indien de tabel waar vanuit geüpload wordt anders is dan tbadviezen of tbinspecties of tbbezwaarberoep, dan worden alleen de rijen meegenomen waarin een '4' voorkomt in _Getal1_ (dus bijvoorbeeld _Getal1_ = 4 of 14)
- indien geüpload wordt vanuit tbadviezen, dan worden alleen de rijen meegenomen waarin een '1' voorkomt in _Getal1_
- indien geüpload wordt vanuit tbinspecties dan worden alleen de rijen meegenomen waarin een '2' voorkomt in _Getal1_
- indien geüpload wordt vanuit tbbezwaarberoep dan worden alleen de rijen meegenomen waarin een '5' voorkomt in _Getal1_.

#### Substitutie variabelen

Van de rijen uit de instellingen bij _Sectie: Aanmaakmappen_ die aan bovenstaande voldoen wordt de kolom _Tekst_ gebruikt in een hulprijtje. De kolom _Tekst_ bevat de echte map op de fileshare, maar OpenWave zal hierop eerst nog een substitutie uitvoeren op de volgende variabelen:

- `%zaakjaar%` door het jaar (jjjj) van de begindatum hoofdzaak (geldt niet voor de regels met _Getal1_ = 4 en waarvan kolom _Item_ begint met Inrichting\_).

Alleen in het geval van inspecties bij inrichtingen wordt `%zaakjaar%` bepaald op grond van startdatum (ddrappel)

- `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum hoofdzaak (geldt niet voor de regels met _Getal1_ = 4 en waarvan kolom _Item_ begint met Inrichting\_).

Alleen in het geval van inspecties bij inrichtingen wordt `%zaakjaar%` bepaald op grond van startdatum (ddrappel)

- `%zaaknr%` met de Wavezaakcode van de hoofdzaak (of met het inrichtingsnummer indien Inrichting)
- `%inspnr%` met de Wavezaakcode van de inspectiekaart (dus alleen bij _Getal1_ = 2)
- `%adviesnr%` met de Wavezaakcode van de advieskaart (dus alleen bij _Getal1_ = 1)
- `%bezwaarnr%` met de Wavezaakcode van de bezwaarberoepkaart (dus alleen bij _Getal1_ = 5).

Voorbeeld:
`[\\CORK\OpenWave\Documents\Omgeving](file://///CORK/OpenWave/Documents/Omgeving.md)\%zaakjaar%\%zaaknr%`

wordt na substitutie bijvoorbeeld

`[\\CORK\OpenWave\Documents\Omgeving\2012\2013RP0044](file://///CORK/OpenWave/Documents/Omgeving/2012/2013RP0044.md)\`

Uiteindelijk leveren deze instellingen dus een of meer fileshare-mappen op waar het programma documenten kan plaatsen bijvoorbeeld:

- `[\\CORK\OpenWave\Documents\Omgeving\2012\2013RP0044](file://///CORK/OpenWave/Documents/Omgeving/2012/2013RP0044.md)`
- `[\\CORK\OpenWave\Documents\Omgeving\2012\2013RP0044\Adviezen](file://///CORK/OpenWave/Documents/Omgeving/2012/2013RP0044/Adviezen.md)`
- `[\\CORK\OpenWave\Documents\Omgeving\2012\2013RP0044\Inspecties](file://///CORK/OpenWave/Documents/Omgeving/2012/2013RP0044/Inspecties.md)`
- `[\\CORK\OpenWave\Documents\Omgeving\2012\2013RP0044\OLO](file://///CORK/OpenWave/Documents/Omgeving/2012/2013RP0044/OLO.md)`

Indien dit rijtje bestaat uit 0 mappen dan gaat het uploaden niet door (het programma weet dan niet waar de upload te plaatsen).

Indien dit rijtje bestaat uit 1 map dan hoeft het programma niet aan de gebruiker een extra keuze te vragen uit de mogelijkheden.

Indien dit rijtje bestaat uit meer dan 1 map dan zal de gebruiker hieruit een extra keuze moeten maken.

Indien op de fileshare de map niet bestaat waarop het document geüpload moet worden, dan maakt het programma deze automatisch aan.

LET OP: indien instelling _Sectie: Documenten_ en _Item: SpecialeUploadMappen_ aangevinkt is en u wilt uploaden bijvoorbeeld vanuit inspecties bij een omgevingszaak, dan verwacht OpenWave dus minimaal één kaart bij _Sectie: AanmaakMappen_ en _Item_ begint met Omgeving\_ waarbij _Getal1_ de waarde 2 heeft (inspecties)
en _Getal2_ ook de waarde 2 (uploadmap), anders komt foutcode 706: ontbrekende instellingen.
