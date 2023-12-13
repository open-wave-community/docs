# Aanmaken van nieuwe inrichting

Vanuit het archiefportaal \*Zaken/**inrichtingen\*** en vanaf scherm _Alle inrichtingen_ kan met de insertknop een nieuwe inrichting aangemaakt worden op de straat die op dat moment actief is.

## Rechten

**Recht op insert inrichting.**
De inlogger moet lid zijn van een rechtengroep met insertrechten op inrichtingen (tbmilrechten.Dlbmilinrins). Indien de inlogger lid is van een [compartiment](../../../instellen_inrichten/compartimenten.md) moeten er bedrijfsoorten aan dat compartiment zijn toegekend (en een inrichting kan in dat geval alleen worden aangemaakt binnen een gemeente die toegekend is aan dat compartiment).

**Recht op aanmaak nieuw locatie:**
Na keuze van de module waarvoor een nieuwe inrichting aangemaakt moet worden kan de inlogger de locatie aanwijzen binnen de gegeven straat.
Het kan zijn dat daarbij een huisnummer wordt ingetikt, waardoor het programma een nieuwe locatie (in tbperceeladressen) moet aanmaken.
De rechtengroep van de inlogger moet hiervoor op het hoofdscherm rechten het recht: _locatieadressen nieuw_ (tbrechten.dldpclins) aangevinkt hebben.

### Keuze bedrijfsoort

Indien de inlogger lid is van een compartiment dan moet er een bedrijfsoort worden gekozen. De mogelijke bedrijfsoorten zijn toegekend in het compartiment. Eventueel eigen masker en lengte voor het bepalen van het inrichtingnummer zijn per bedrijfsoort te definiëren/gedefinieerd in het compartimentsdetailscherm.

### Controle met BAG

Deze kan automatisch worden uitgevoerd met een StUF-BG bevraging indien de instelling _Sectie: KoppelingBAG Item: Methode en Tekst: StUF-310_ aangevinkt is.
De verplichte instellingen hierbij voor de opmaak en adressering van de stuf-berichten zijn (zie [BAG bevraging](bag_bevraging.md)):

_Sectie: KoppelingBAG_

- Item: _HTTPSoapAction_tgoLv01_. In de kolom _Tekst_ hier de waarde `[http://www.egem.nl/StUF/sector/bg/0310/tgoLv01](http://www.egem.nl/StUF/sector/bg/0310/tgoLv01.md)`
  - _Item: Ontvangstadres_. In de kolom _Tekst_ het endpoint waar het vraagbericht naar toe moet
  - _Item: Zender_Applicatie_. De kolom _Tekst_ met de applicatie
  - _Item: Zender_Organisatie_. De kolom _Tekst_ met de organisatie
  - _Item: Ontvanger_Applicatie_. De kolom _Tekst_ met de applicatie
  - _Item: Ontvanger_Organisatie_. De kolom _Tekst_ met de organisatie

Indien het adres niet wordt aangetroffen in de BAG, dan wordt de identificatie van het locatie adres leeggemaakt.
Wel gevonden: dan worden Datum BAG, identificatie en puntcoördinaten gevuld.

_Opmerking:_ indien gewenst kunnen bepaalde huisnummers uitgesloten worden van controle/synchronisatie met BAG. Zie de instelling _NieuweZaakGeenBAGSync_ bij
[Sectie Programma](../../../instellen_inrichten/configuratie/sectie_programma.md).

### Automatisch aanmaken mappen of fileshare

Indien:

- de inrichting NIET valt onder een compartiment
  - de instelling _Sectie: Documenten Item: OphalenViaFileserver_ aangevinkt is
  - en de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is

OF indien:

- de inrichting WEL valt onder een compartiment
  - de kolom _Ophalen via fileserver_ op de detailkaart van het betreffende compartiment is aangevinkt
  - en de kolom _Automatisch aanmaken mappen_ (dlautoaanmaakmappen) aangevinkt is bij het betreffende compartiment

dan zullen bij het aanmaken van een nieuwe inrichting automatisch de mappen genoemd in de rijen van _Sectie: Aanmaakmappen_ worden aangemaakt waarvan item begint met 'Inrichting\_'. Hierbij uitgezonderd zijn de mappen waarin de variabele `%inspnr%` is opgenomen.
Indien OpenWave in de cloud draait, dan moet wel de [satellite](../../../instellen_inrichten/satellite_filesysteem.md) geïnstalleerd zijn.

### Automatisch vullen van kolom dvhyperlink

Zie: [Hyperlink](../../../instellen_inrichten/hyperlink.md).
