# Externe Link

De knop *Externe Link* kan voorkomen in:

* de zaakportalen bij de knoppen rechtsboven
* het detailscherm van inspecties bij de knoppen linksonder.

## Instellingen

De knop is zichtbaar en enabled indien:

* de instelling *Sectie: ExterneLink* en *Item: modulenaam* aangevinkt is. Voor modulenaam zijn de volgende waarden toegestaan:
  * Omgeving
  * ApvOverig
  * Handhaving
  * MilieuGebruik
  * Inrichting
  * Inspecties
  * BouwSloop
  * Info
  * Horeca
* EN het recht *starten van hyperlink vanuit portaal* aangevinkt is bij de rechtengroep van de inlogger voor de betreffende module
* EN de kolom *Tekst* van bovengenoemde instelling gevuld is met een URL.

## Variabelen

Het programma construeert dan de hyperlink met die URL
Die variabelen die gebruikt kunnen worden in de kolom *Tekst* van de instelling zijn:

* `%zaakjaar%` wordt vervangen met het jaar (yyyy) van de aanvraagdatum
* `%zaakjaar%`  met met de jaarmaand (yyyymm) van de aanvraagdatum
* `%zaaknr%`  met de OpenWave zaakcode
* `%dmsnr%` met het externe zaaknummer (dvintzaakcode)
* `%postcode%` met de postcode van het locatie-adres
* `%huisnummer%` met het huisnummer/huisletter/toevoeging van het locatie-adres
* `%olonr%` met OLO-aanvraagnummer (alleen bij omgevingszaken en milieu/gebruik zaken).

## Voorbeelden

**Voorbeeld 1 zaakpagina van een DMS**

```
https://docs.ecm2.nl/share/page/repository#filter=path%7C%2FOpenWave%2FOmgeving%2F%zaakjaar%%2F%zaaknr%&page=1
```

wordt bij het uitvoeren van de link bijvoorbeeld omgezet in:

`[https://docs.ecm2.nl/share/page/repository#filter=path%7C%2FOpenWave%2FOmgeving%2F](https://docs.ecm2.nl/share/page/repository#filter=path%7C%2FOpenWave%2FOmgeving%2F.md)**2016**%2F**2016W0074**&page=1`

**Voorbeeld 2 zaakpagina van een DMS**

`[http://dms-test.onegov.nl:40081/_layouts/15/qnh.dms.modules.openwave/documents.aspx/z/%dmsnr%](http://dms-test.onegov.nl:40081/_layouts/15/qnh.dms.modules.openwave/documents.aspx/z/%dmsnr%.md)`
wordt bij het uitvoeren van de link bijvoorbeeld omgezet in:

`[http://dms-test.onegov.nl:40081/_layouts/15/qnh.dms.modules.openwave/documents.aspx/z/](http://dms-test.onegov.nl:40081/_layouts/15/qnh.dms.modules.openwave/documents.aspx/z/.md)**1200023**`

**Voorbeeld 3 naar map op fileshare**

Werkt waarschijnlijk alleen met Internet Explorer/Edge EN indien fileshare binnen bereik EN open-wave.nl is bij Internetopties/beveiliging aangewezen als betrouwbare site (trusted).

Is dit het geval dan kan ook naar een plek op het filesysteem worden verwezen, waarbij Explorer op de gewenste map opstart. De constructie in de instelling moet dan iets dergelijks zijn als:

```
file://///URANUS/Organisatie/Wave/%zaakjaar%/%zaaknr%
```

**Let op:** na file volgen de 5 slashes.
Zie ook toepassing via kolom hyperlink ([Hyperlink](/docs/instellen_inrichten/hyperlink.md)).
