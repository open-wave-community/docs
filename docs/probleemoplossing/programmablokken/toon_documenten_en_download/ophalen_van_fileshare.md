# Ophalen van fileshare

Voor het openen van een document dat op de fileserver staat via hyperlink of OnlyOffice: zie de betreffende kopjes bij [Toon documenten en download](/probleemoplossing/programmablokken/toon_documenten_en_download.md).

## Instellingen

De volgende instellingen zijn hierbij onontbeerlijk.

Allereerst moet de kolom _Tekst_ bij de instelling _Sectie: Documenten_ en _Item: DocumentRoot_ gevuld zijn met een UNC-map, bijvoorbeeld [\\WORK\OpenWave\Documents](file://///WORK/OpenWave/Documents.md), die verwijst naar een map op de fileshare waarachter alle documenten zijn opgeslagen die vanuit OpenWave opgehaald kunnen worden. Ook in geval dat de communicatie met de fileshare via een satellite verloopt die een eigen documentroot kan hebben, is bovenstaande toch verplicht (dus invullen alsof er geen satellite is gedefinieerd).

Ook in het geval dat de zaak waar de documenten naar toe worden geüpload valt onder een compartiment (al of niet met satellite) geldt het bovenstaande.

### Authenticatie

- Indien de zaak waarvandaan de documenten worden opgehaald NIET valt onder een compartiment (of wel, maar het compartiment gebruikt geen satellite) dan:
  - _Sectie: Documenten Item: OphalenViaFileserver_Username_ In kolom _Tekst_ komt de inlognaam die gebruikt wordt om:
    - indien de fileserver rechtstreeks zonder satellite (dus on premisse) wordt benaderd, de documenten op te halen achter de documentroot
    - indien de fileserver via satellite wordt benaderd, dan moet deze username overeenkomen met de tag api_name uit de lokaal geïnstalleerde satellite.ini. In de satelllite-ini zijn apart de credentials gedefinieerd die toegang geven tot de fileshare.
  - _Sectie: Documenten Item: OphalenViaFileserver_Password_. In kolom _Tekst_ komt het password dat hoort bij de _OphalenViaFileserver_Username_.
    - indien de fileserver rechtstreeks zonder satellite (dus on premisse) wordt benaderd is dit het password dat toegang geeft tot de fileshare
    - indien de fileserver via satellite wordt benaderd, dan moet deze userpass overeenkomen met de tag api_pass uit de lokaal geïnstalleerde satellite.ini.
- Indien de zaak waarvandaan de documenten worden opgehaald WEL valt onder een compartiment en de kolom dlsatellite van dat compartiment is aangevinkt, dan zijn username en password bij het betreffende compartiment in het blok satellite opgeslagen (beheerportaal-Nieuw).

Zie ook: [2-way encryptie van externe wachtwoorden](/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md).

## Protocol

Indien satellite (al of niet in combinatie met compartiment) dan staat het protocol waarmee de fileshare wordt benaderd in de lokaal geplaatste ini-file die hoort bij de satellite-installatie.

Indien geen satellite dan is het standaardprototcol JCofs. Echter, indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: OphalenViaFileserver_ gevuld is met 'SMBTWO' dan wordt het SMB2 protocol gebruikt )of SMB3…"de instelling van de server is hierin leidend).

### Tracerings-instellingen

_Sectie: Documenten_
_Item: OphalenViaFileserver_Wins_. In de kolom _Tekst_: het IP-adres van de machine met de windows internet naming service, waarmee de volgende instelling gelokaliseerd kan worden.

**Het domein van de fileshare**.

- Indien de zaak waarvandaan de documenten worden opgehaald NIET valt onder een compartiment (of wel, maar het compartiment gebruikt geen satellite) dan:
  - geen satellite (dus openwave is on premisse geïnstalleerd) dan de kolom _Tekst_ van _Sectie: Documenten en Item: OphalenViaFileserver_Domain_ In kolom _Tekst_ de domeinnaam waarin rechten van username en password geregeld zijn
  - wel satellite maar de zaak waar vanuit geüpload wordt valt NIET in een compartiment, dan de kolom _Tekst_ van _Sectie: Satellite Item: Domain_.
- Indien de zaak waarvandaan de documenten worden opgehaald WEL valt onder een compartiment en de kolom dlsatellite van dat compartiment is aangevinkt dan de kolom _Domein_ op de detailkaart van het betreffende compartiment (beheerportaal-Nieuw) in het blok satellite.

### Satellite

Indien er verbinding vanuit de Cloud wordt gezocht met een fileserver dan is een installatie van een aparte Open Wave Satellite-server binnen het LAN noodzakelijk. Het programma verwacht dat deze satellite-server aanwezig is indien:

- de zaak waar vanuit wordt geüpload NIET valt onder een compartiment en de kolom _Tekst_ van _Sectie: Documenten, Item: OphalenViaFileserver_ gevuld is met de waarde 'Satellite'.
- de zaak waar vanuit wordt geüpload WEL valt onder een compartiment en de kolom de kolom _fileserver via Satellite_ op de detailkaart van het betreffende compartiment (beheerportaal-Nieuw) aangevinkt is.

Zie voor werking en overige instellingen: [Satellite t.b.v. benadering fileserver](/instellen_inrichten/satellite_filesysteem.md).

## Welke mappen?

OpenWave moet eerst bepalen van welke map(pen) de documenten getoond kunnen worden.

OpenWave gaat er daarbij vanuit dat de documenten achter de vermelde Documentroot logisch ingedeeld zijn naar op zijn minst de hoofdzaakcodering.

Het bepalen van welke mappen de inlogger mag zien gebeurt op drie manieren.

### Alle (sub)mappen van een hoofdzaak

Dit is het geval indien:

- de instelling _Sectie: Documenten Item: Autorisatiemappen_ aangevinkt is
- en de inlogger is lid van een rechtengroep die het recht _Toegang tot alle mappen en dvhyperlink (tbrechten.dlmappenhyperlink)_ aangevinkt heeft staan
- en de instelling _Sectie: documenten, Item: OphalenNaMapkeuze_ is aangevinkt
- en de instelling _Sectie: documenten, Item: OphalenViaDms_ NIET is aangevinkt.

Wanneer de inlogger in deze situatie op de knop _Docs_ drukt, kijkt het programma naar de kolom dvhyperlink van de hoofdzaak (dus tbomgvergunning, tbmilinrichtingen, tbinfoaanvragen etc.).
Ook de submappen achter de gevonden hoofdzaakmap worden meegenomen.

LET OP: indien de map gedefinieerd in kolom dvhyperlink GEEN submap is van de documentroot, dan wordt er niets getoond.

### Alleen expliciet toegekende (sub)mappen per zaak op rechtengroepniveau

Dit is het geval indien:

- de instelling _Sectie: Documenten Item: Autorisatiemappen_ aangevinkt is
- en de inlogger is GEEN lid van een rechtengroep die het recht _Toegang tot alle mappen en dvhyperlink (tbrechten.dlmappenhyperlink)_ aangevinkt heeft staan
- en de instelling _Sectie: Documenten, Item: OphalenNaMapkeuze_ is aangevinkt
- en de instelling _Sectie: Documenten, Item: OphalenViaDms_ NIET is aangevinkt.

Wanneer de inlogger in deze situatie op de knop _Docs_ drukt, kijkt het programma naar toegekende mappen (de kolom map tbrechtengroepmappen.dvmapfileshare) van de rechtengroep waar hij/zij lid van is (Beheertegel _Functionele rechten_: lijst in detailscherm van rechtengroep). Het gaat daarbij om de niet vervallen rijen waarbij _download_ aangevinkt is.
In deze kolom dvmapfileshare worden vervolgens de variabelen:

- `%zaakjaar%` vervangen door het jaar (jjjj) van de begindatum van de betreffende hoofdzaak (dus niet bij inrichting)
- `%zaakjaar%` vervangen door de jaarmaand (jjjjmm) van de begindatum zaak van de betreffende hoofdzaak (dus niet bij inrichting)
- `%zaaknr%` vervangen met de wavezaakcode van de betreffende hoofdzaak of inrichting
- `%inspnr%` met de wavezaakcode van de inspectiekaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een inspectiedetailkaart)
- `%adviesnr%` met de wavezaakcode van de advieskaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een adviesdetailkaart)
- `%bezwaarnr%` met de wavezaakcode van de bezwaar/beroepkaart (krijgt alleen waarde indien de documentenknop is ingedrukt vanaf een bezwaar/beroepdetailkaart)

Ook de submappen achter de toegekende mappen worden meegenomen.

Ook hier geldt dat de autorisatiemappen een submap van de documentroot moeten zijn.

### Alle (sub)mappen per (deel)zaak zoals gedefinieerd in Sectie: Aanmaakmappen

Dit is het geval indien:

- de instelling _Sectie: Documenten Item: Autorisatiemappen_ NIET aangevinkt is
- OF de instelling _Sectie: Documenten, Item: OphalenNaMapkeuze_ is NIET aangevinkt.

Het programma interpreteert bezwaar/beroep, adviezen en inspecties als deelzaken bij een hoofdzaak en kan zo nodig alleen de documenten van de deelzaak tonen.

Het programma kijkt niet naar aparte document inzienrechten: Indien de inlogger een basiskaart kan zien, dan kan hij/zij ook de documenten die daarbij horen inzien.

Het programma bepaalt welke mappen getoond kunnen worden op grond van de instellingen per module onder de _Sectie: AanmaakMappen_.

Als er bijvoorbeeld 5 mappen bestaan op de fileshare om documenten in te delen onder een bepaalde omgevingszaak dan worden er ook 5 regels gedefinieerd in OpenWave onder _Sectie: AanmaakMappen_ waarbij de kolom _Item_ begint met 'Omgeving\_'.

Bijvoorbeeld Omgeving_basis, Omgeving_OLO, Omgeving_adviezen en Omgeving_inspecties et cetera.

In de kolommen _Tekst_ van de betreffende regel komen de mappen van de fileshare te staan (in UNC-notatie). Zie ook voorbeeld verderop.

LET OP: al deze mappen moeten dus submappen zijn van de DocumentRoot (de documentroot moet wel onderdeel zijn van de map).

De kolom _Item_ begint dus afhankelijk van de module met:

- indien module = V dan 'Inrichting\_'
- indien module = W dan 'Omgeving\_'
- indien module = B dan 'Bouw\_'
- indien module = O dan 'Overige\_'
- indien module = H dan 'Handhaving\_'
- indien module = C dan 'Horeca\_'
- indien module = E dan 'MilGebr\_'
- indien module = I dan 'Info\_'

OpenWave redeneert verder als volgt:

#### Zaak/Inrichting

Indien documenten worden opgevraagd vanuit het zaakportal of het detailscherm van een zaak of inrichting, dan zoekt OpenWave naar de mappen op de fileshare die genoemd staan in de kolom _Tekst_ van de configuratie instellingen onder _Sectie: AanmaakMappen_ bij de betreffende module (d.w.z. waarvan de kolom _Item_ begint met 'Omgeving*' of 'Inrichting*' of 'Handhaving' of ….) en waarbinnen de kolom _Getal1_ de waarde 4 voorkomt (bijvoorbeeld 4 of 14 of 42).

Ook de daadwerkelijk bestaande submappen hierachter worden meegenomen (die hoeven dus niet in de _Sectie: AanmaakMappen_ voor te komen).
Bepaalde submappen kunnen echter worden uitgesloten met de instelling _Sectie: Documenten Item: geensubmapmetsubstring1_ (en ook _geensubmapmetsubstring2_ en _geensubmapmetsubstring3_). Met de waarde in kolom _Tekst_ van deze instellingen worden submappen waarin deze waarde voorkomt, overgeslagen.

#### Advies

Indien documenten worden opgevraagd vanuit het adviesdetailscherm van een zaak dan zoekt OpenWave naar de mappen op de fileshare die genoemd staan in de kolom _Tekst_ van de configuratie instellingen onder _Sectie: AanmaakMappen_ bij de betreffende module (d.w.z. waarvan de kolom _Item_ begint met 'Omgeving*' of 'Inrichting*' of 'Handhaving' of ….) en waarbinnen het _Getal1_ de waarde 1 voorkomt (bijvoorbeeld 1 of 12 of 41).

Ook de submappen hierachter worden meegenomen. Bepaalde submappen kunnen echter worden uitgesloten met de instelling _Sectie: Documenten Item: geensubmapmetsubstring1_ (en ook _geensubmapmetsubstring2_ en _geensubmapmetsubstring3_). Met de waarde in kolom _Tekst_ van deze instellingen worden submappen waarin deze waarde voorkomt, overgeslagen.

#### Bezwaar/beroep

Indien documenten worden opgevraagd vanuit het bezwaar/beroepdetailscherm van een zaak dan zoekt OpenWave naar de mappen op de fileshare die genoemd staan in de kolom _Tekst_ van de configuratie instellingen onder _Sectie: AanmaakMappen_ bij de betreffende module (d.w.z. waarvan de kolom _Item_ begint met 'Omgeving*' of 'Inrichting*' of 'Handhaving' of ….) en waarbinnen het _Getal1_ de waarde 5 voorkomt (bijvoorbeeld 5 of 52 of 51).

Ook de submappen hierachter worden meegenomen. Bepaalde submappen kunnen echter worden uitgesloten met de instelling _Sectie: Documenten Item: geensubmapmetsubstring1_ (en ook _geensubmapmetsubstring2_ en _geensubmapmetsubstring3_). Met de waarde in kolom _Tekst_ van deze instellingen worden submappen waarin deze waarde voorkomt, overgeslagen.

#### Inspectie

Indien documenten worden opgevraagd vanuit het inspectiedetailscherm van een zaak of bij een inrichting dan zoekt OpenWave naar de mappen op de fileshare die genoemd staan in de kolom _Tekst_ van de configuratie instellingen onder _Sectie: AanmaakMappen_ bij de betreffende module (d.w.z. waarvan de kolom _Item_ begint met 'Omgeving*' of 'Inrichting*' of 'Handhaving' of ….) en waarbinnen het _Getal1_ de waarde 2 voorkomt (bijvoorbeeld 2 of 12 of 42).

Ook de submappen hierachter worden meegenomen. Bepaalde submappen kunnen echter worden uitgesloten met de instelling _Sectie: Documenten Item: geensubmapmetsubstring1_ (en ook _geensubmapmetsubstring2_ en _geensubmapmetsubstring3_). Met de waarde in kolom _Tekst_ van deze instellingen worden submappen waarin deze waarde voorkomt, overgeslagen.

Wil je vanuit de basiskaart van een zaak ook alle documenten zien die horen bij de adviezen of inspecties van die zaak, dan moet je zorgen dat de adviezen en inspecties in de mappenstructuur op de fileshare als submap achter die van de hoofdzaak komen.

#### Variabelen

In de mappen zoals die in kolom _Tekst_ zijn gedefinieerd zal OpenWave eerst nog een substitutie uitvoeren op de volgende variabelen:

- `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie (geldt niet voor de regels met _Getal1_ = 4 en waarvan kolom _Item_ begint met Inrichting\_)
- `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie (geldt niet voor de regels met _Getal1_ = 4 en waarvan kolom _Item_ begint met Inrichting\_)
- `%zaaknr%` met de wavezaakcode van de hoofdzaak (of met het inrichtingsnummer indien Inrichting)
- `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen bij _Getal1_ = 2)
- `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen bij _Getal1_ = 1)
- `%bezwaarnr%` met de wavezaakcode van de bezwaar/beroepkaart (dus alleen bij _Getal1_ = 5).

Voorbeeld:
`[\\WORK\OpenWave\Documents\Omgeving](file://///WORK/OpenWave/Documents/Omgeving.md)\%zaakjaar%\%zaaknr%` wordt na substitutie bijvoorbeeld `[\\WORK\OpenWave\Documents\Omgeving\2012\2013RP0044](file://///WORK/OpenWave/Documents/Omgeving/2012/2013RP0044.md)\`

Uiteindelijk leveren deze instellingen dus een aantal mappen op waar het programma gaat kijken naar documenten bijvoorbeeld:

- [\\WORK\OpenWave\Documents\Omgeving\2012\2013RP0044](file://///WORK/OpenWave/Documents/Omgeving/2012/2013RP0044.md)\
- [\\WORK\OpenWave\Documents\Omgeving\2012\2013RP0044\Adviezen](file://///WORK/OpenWave/Documents/Omgeving/2012/2013RP0044/Adviezen.md)
- [\\WORK\OpenWave\Documents\Omgeving\2012\2013RP0044\Inspecties](file://///WORK/OpenWave/Documents/Omgeving/2012/2013RP0044/Inspecties.md)
- [\\WORK\OpenWave\Documents\Omgeving\2012\2013RP0044\OLO](file://///WORK/OpenWave/Documents/Omgeving/2012/2013RP0044/OLO.md)

Afhankelijk van of de instelling _Sectie: documenten, Item: OphalenNaMapkeuze_ is aangevinkt (zie vorige pagina [Toon documenten en download](/probleemoplossing/programmablokken/toon_documenten_en_download.md)) zal de gebruiker eerst uit deze mogelijke mappen een keuze kunnen maken.
Van de overgebleven mappen worden vervolgens alle documenten op de toon-documentenlijst geplaatst en kunnen eventueel gedownload worden.
Verborgen bestanden en het bestand thumbs.db worden hierbij overgeslagen.
