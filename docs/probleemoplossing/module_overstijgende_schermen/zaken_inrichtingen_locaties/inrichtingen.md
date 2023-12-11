# Lijst Alle inrichtingen

Dit scherm kan worden aangeroepen vanuit het openingsportaal (zie tegeldefinitie hieronder). De lijst toont alle inrichtingen die in OpenWave bekend zijn. Met behulp van de filter bovenin het scherm kan het resultaat van de lijst gefilterd worden.

## Werking filters in deze lijst

Er zijn drie algemene filtermogelijkheden in het scherm *Alle inrichtingen*:

* **Locatie**: deze filter geeft de gebruiker de mogelijkheid om alleen alle inrichtingen binnen een gemeente, woonplaats en/of straat te zien. Nieuw is ook toegevoegd om inrichtingen op projectlocatie te filteren: dit zijn alle inrichtingen met dezelfde hoofdprojectlocatie (tbzaakkadperc.dlhoofdprojectlocatie is true) en geldt dus alleen voor inrichtingen waaronder projectlocaties/kadastrale percelen zijn opgegeven. Voor gebruik van de Locatie filters geldt dat men eerst op gemeente filtert, daarna op woonplaats, daarna op straat en daarna eventueel op projectlocatie. Dit omdat de te kiezen waardes van deze filters afhankelijk zijn van de gekozen waarde voor de filter erboven.
* **Status**: deze filter bestaat uit twee sub filters:
  * Geblokkeerd/Niet geblokkeerd: de optie voor het wel of niet filteren op geblokkeerde inrichtingen. Het aanzetten van Geblokkeerd resulteert in het alleen tonen van geblokkeerde inrichtingen. Het aanzetten van filter Niet geblokkeerd resulteert in het alleen tonen van niet geblokkeerde inrichtingen. Beiden aanvinken geeft geen resultaat (een inrichting kan niet wel en niet geblokkeerd zijn), beiden uitzetten geeft als resultaat dat er niet gekeken wordt naar de blokkeerdatum bij ophalen van de inrichtingen (zowel geblokkeerde als niet geblokkeerde inrichtingen worden getoond).
  * Status: de statussen waarop de gebruiker kan filteren zijn hier aan-/uit te zetten. Als alle mogelijke statusfilters uitstaan dan zal het programma niet filteren op status. Dit type filter is een zogenaamde multi-keuzenfilter.
* **Overig**: de gebruiker kan hier op overige eigenschappen van inrichtingen filteren. Zo kan hier op de eigenschap Complex, Dochter, en Moeder-inrichting gefilterd worden door de vakjes aan-/uit te vinken. Uit betekent dat het programma niet kijkt naar of de eigenschap waar is. Er wordt dan niet gefilterd op de eigenschap.

## Definitie

* Voor de definitie van de lijst en knoppen zie beheertegel *Tabellen standaardapi* (tbsysstandardtable.dvcode = opening_alleinrichtingen).
* De lijst-schermidentifier is: MDLC_getAlleInrichtingenList.xml (zie beheertegel *Schermkolomdefinitie tabellen standaard-api*).
* De onderliggende view is: vwfrmmilinrichtingen.
* De schermidentifier van de filterblokken is: MDFC_getAlleInrichtingenList.xml (zie beheertegel *Schermkolomdefinitie tabellen standaard-api*).

## Bijzonere kolommen

* de eerste kolom wordt gevuld met een stop/blokkeericoontje indien de betreffende inrichting is geblokkeerd
* de dertiende kolom wordt gevuld met het check-icoontje indien de inrichting gekoppeld is aan een complexititeitsaanduiding
* de veertiende kolom wordt gevuld met het check-icoontje indien de inrichting een dochterinrichting is van een andere moederinrichting
* de vijftiende kolom wordt gevuld met het aantal dochters indien de inrichting zelf een moederinrichting is.
* de kolom Straatnaam/Projectlocatie wordt in principe gevuld met de openbareruimtenaam uit tbperceeladressen  tenzij bij dat perceeladres de kolom dlonbekendadres is aangevinkt EN er een hoofdprojectlocatie opgegeven is onder de tegel Projectlocaties/Kadastrale percelen. In dat laatste geval zal de opgegeven hoofdprojectlocatieomschrijving (de kolom tbzaakkadperc.dvstraatnaam) van de zaak/inrichting getoond worden.

### Error

Het scherm geeft een foutmelding, indien:

* er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
* de inlogger geen kijkrechten heeft op inrichtingen.

### Triggers

Dubbel klikken op een regel opent het portaalscherm van de inrichting. Altijd enabled.

#### Triggers linksonder

* Nieuwe inrichting (insert-knop):
  * Zichtbaar indien inlogger rechten heeft voor aanmaken van inrichtingen.
* Nieuwe inrichting op deze straat (insert-knop):
  * Zichtbaar indien inlogger rechten heeft voor aanmaken van inrichtingen.
* Verwijder inrichting (deleteknop):
  * Zichtbaar indien inlogger verwijderrechten heeft voor inrichtingen.
* Toon kaart:
  * Zichtbaar indien inlogger het recht heeft locatie-adressen zichtbaar.
  * Opent de kaartviewer van de geselecteerde zaak.
* Locatie-adres:
  * Zichtbaar indien inlogger het recht heeft locatie-adressen zichtbaar.
  * Opent de detailkaart met gegevens van het locatie-adres.
* Detailscherm:
  * Zichtbaar indien inlogger het recht heeft op inzien van inrichting.
  * Opent het detailscherm van de geselecteerde inrichting.
* Memo:
  * Zichtbaar indien inlogger het recht heeft om memo in te zien bij inrichtingen.
  * Opent de memo van de geselecteerde inrichting.
* Voeg samen met andere inrichting uit dezelfde straat:
  * Zichtbaar indien inlogger het recht heeft om inrichtingen samen te voegen.
  * Start de wizard voor samenvoegen van inrichtingen.

### Aanmaken van nieuwe inrichting bij insert

Er kan gekozen worden voor **Nieuwe inrichting op deze straat** of **Nieuwe inrichting**. Beide knoppen starten de wizard *maakNieuweInrichting*. Indien gekozen wordt voor inrichting aanmaken op deze straat, dan zal het programma het adres overnemen van de inrichting in het lijstscherm waarop men staat bij klikken op knop *Nieuwe inrichting op deze straat*. Indien gekozen voor knop *Nieuwe inrichting* dan zal de gebruiker in de wizard *maakNieuweInrichting* eerst de locatie moeten doorgeven voor de nieuw aan te maken inrichting. Voor voor meer informatie over aanmaken van inrichtingen: zie [Aanmaken van nieuwe inrichting](/docs/probleemoplossing/programmablokken/maak_nieuwe_inrichting.md).

### Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Openingsportaal*
* Kolom: *Hoofdzaken*
* Kopregel: *Alle inrichtingen*
* Dynamisch tegelopschrift:
* Actie: *getFlexList(SysStandardList,nil,nil,G,opening_alleinrichtingen)*
