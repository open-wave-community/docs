# Externe Link

De knop _Externe Link_ kan voorkomen in:

- de zaakportalen bij de knoppen rechtsboven
- het detailscherm van inspecties bij de knoppen linksonder.

## Instellingen

De knop is zichtbaar en enabled indien:

- de instelling _Sectie: ExterneLink_ en _Item: modulenaam_ aangevinkt is. Voor modulenaam zijn de volgende waarden toegestaan:
  - Omgeving
  - ApvOverig
  - Handhaving
  - MilieuGebruik
  - Inrichting
  - Inspecties
  - BouwSloop
  - Info
  - Horeca
- en het recht _starten van hyperlink vanuit portaal_ aangevinkt is bij de rechtengroep van de inlogger voor de betreffende module
- en de kolom _Tekst_ van bovengenoemde instelling gevuld is met een URL.

## Variabelen

Het programma construeert dan de hyperlink met die URL
Die variabelen die gebruikt kunnen worden in de kolom _Tekst_ van de instelling zijn:

- `%zaakjaar%` wordt vervangen met het jaar (yyyy) van de aanvraagdatum
- `%zaakjaar%` met met de jaarmaand (yyyymm) van de aanvraagdatum
- `%zaaknr%` met de OpenWave zaakcode
- `%dmsnr%` met het externe zaaknummer (dvintzaakcode)
- `%postcode%` met de postcode van het locatie-adres
- `%huisnummer%` met het huisnummer/huisletter/toevoeging van het locatie-adres
- `%olonr%` met OLO-aanvraagnummer (alleen bij omgevingszaken en milieu/gebruik zaken).

## Voorbeelden

**Voorbeeld 1 zaakpagina van een DMS**

`https://docs.ecm2.nl/share/page/repository#filter=path%7C%2FOpenWave%2FOmgeving%2F%zaakjaar%%2F%zaaknr%&page=1`

wordt bij het uitvoeren van de link bijvoorbeeld omgezet in:

`https://docs.ecm2.nl/share/page/repository#filter=path%7C%2FOpenWave%2FOmgeving%2F2016%2F2016W0074&page=1`

**Voorbeeld 2 zaakpagina van een DMS**

`http://dms-test.onegov.nl:40081/_layouts/15/qnh.dms.modules.openwave/documents.aspx/z/%dmsnr%`
wordt bij het uitvoeren van de link bijvoorbeeld omgezet in:

`http://dms-test.onegov.nl:40081/_layouts/15/qnh.dms.modules.openwave/documents.aspx/z/1200023`

**Voorbeeld 3 naar map op fileshare**

Werkt waarschijnlijk alleen met Internet Explorer/Edge en indien fileshare binnen bereik en open-wave.nl is bij Internetopties/beveiliging aangewezen als betrouwbare site (trusted).

Is dit het geval dan kan ook naar een plek op het filesysteem worden verwezen, waarbij Explorer op de gewenste map opstart. De constructie in de instelling moet dan iets dergelijks zijn als:

`file://///URANUS/Organisatie/Wave/%zaakjaar%/%zaaknr%`

> [!WARNING]
> **Let op:** na file volgen de 5 slashes. Zie ook toepassing via kolom hyperlink ([Hyperlink](./hyperlink.md)).
