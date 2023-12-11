# Lijst Alle zaken

Dit scherm kan worden aangeroepen vanuit het openingsportaal (zie hieronder voor de tegeldefinitie). De lijst toont alle zaken die in OpenWave bekend zijn.

### Werking van de filters in deze lijst

Met behulp van de filter  bovenin het scherm kan het resultaat van de lijst gefilterd worden op Locatie, Status en Datum (periodes). Default zijn alle modules aangevinkt. Toelichting van de drie filters:

* **Locatie**: deze filter geeft de gebruiker de mogelijkheid om alleen alle zaken binnen een gemeente, woonplaats en/of straat te zien. Nieuw is ook toegevoegd om zaken op projectlocatie te filteren: dit zijn alle zaken met dezelfde hoofdprojectlocatie (tbzaakkadperc.dlhoofdprojectlocatie is true) en geldt dus alleen voor handhaving/omgevingszaken waaronder projectlocaties/kadastrale percelen zijn opgegeven. Voor gebruik van de Locatie filters geldt dat men eerst op gemeente filtert, daarna op woonplaats, daarna op straat en daarna eventueel op projectlocatie. Dit omdat de te kiezen waardes van deze filters afhankelijk zijn van de gekozen waarde voor de filter erboven.
* **Module/Status**: deze filter bestaat uit drie sub filters:
  * Geblokkeerd/Niet geblokkeerd: de optie voor het wel of niet filteren op geblokkeerde zaken. Het aanzetten van *Geblokkeerd* resulteert in het alleen tonen van geblokkeerde zaken. Het aanzetten van filter *Niet geblokkeerd* resulteert in het alleen tonen van niet geblokkeerde zaken. Beiden aanvinken geeft geen resultaat (een zaak kan niet wel en niet geblokkeerd zijn), beiden uitzetten geeft als resultaat dat er niet gekeken wordt naar de blokkeerdatum bij ophalen van de zaken (zowel geblokkeerde als niet geblokkeerde zaken worden getoond).
  * Module: de gebruiker kan hier de modules aan-/uit te zetten waarop gefilterd moet worden. Default zijn alle modules aangevinkt.
  * Status: de statussen waarop de gebruiker kan filteren zijn hier aan-/uit te zetten. Als alle mogelijke statusfilters uitstaan dan zal het programma niet filteren op status. Dit geldt ook voor de filter module. Beide filters zijn zogenaamde multi-keuzenfilters.
* **Datums**: deze filter geeft de gebruiker de mogelijkheid om alleen zaken te laten zien die in periodes vallen qua startdatum, einddatum en/of blokkeerdatum.
* **Zaaktypes**: met deze filter kan de gebruiker een of meer keuzes te maken uit de (niet vervallen) zaaktypes bij omgevingzaken en handhavingzaken.

## Definitie

* Voor de definitie van de lijst en knoppen zie beheertegel *Tabellen standaardapi* (tbsysstandardtable.dvcode = opening_allezaken)/
* De lijst-schermidentifier is: MDLC_getAlleZakenList.xml (zie beheertegel *Schermkolomdefinitie tabellen standaard-api*)/
* De onderliggende view is: vwfrmalleAanvragen/
* De schermidentifier van de filterblokken is: MDFC_getAlleZakenList.xml (zie beheertegel *Schermkolomdefinitie tabellen standaard-api*)/

### Error

Het scherm geeft een foutmelding, indien:

* er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
* de inlogger geen kijkrechten heeft op omgevingszaken.

### Bijzondere kolommen

* de eerste kolom wordt gevuld met een stop/blokkeericoontje indien de betreffende zaak is geblokkeerd
* de tweede kolom wordt gevuld met het ketenicoontje indien de zaak is verbonden met een of meer andere zaken in een groep (zie tegel *Verbonden aan groep* op het zaakportaal van de zaak)
* de derde kolom wordt gevuld met het monumenticoontje indien het locatie adres van de zaak aangeduid is als een monument
* de tiende kolom wordt gevuld met een soort-zaak-icoontje. Per zaaktype kan deze worden gekozen in dropdownlijstje icoon (beheertegels *Zaaktypes omgeving, APV/overig, bouw/sloop, handhaving, milieu/gebruik en infoaanvraag*). De zaaktypes bij de oude bouw/sloopzaken hebben allemaal dezelfde icoon (fabriek). Zo ook die van Info-aanvragen (een *I*) en zo ook die van Horeca (een bierpul).
* de kolom Straatnaam/Projectlocatie wordt in principe gevuld met de openbareruimtenaam uit tbperceeladressen  tenzij bij dat perceeladres de kolom dlonbekendadres is aangevinkt EN er een hoofdprojectlocatie opgegeven is onder de tegel Projectlocaties/Kadastrale percelen. In dat laatste geval zal de opgegeven hoofdprojectlocatieomschrijving (de kolom tbzaakkadperc.dvstraatnaam) van de zaak/inrichting getoond worden.

### Triggers

Dubbel klikken op een regel opent het portaalscherm van de zaak. Altijd enabled.

#### Triggers linksonder

* Nieuwe zaak (insert-knop):
  * Zichtbaar indien inlogger insert-rechten heeft voor aanmaken van zaken voor tenminste een van de modules.
* Nieuwe zaak op deze straat (insert-knop):
  * Zichtbaar indien inlogger insert-rechten heeft voor aanmaken van zaken voor tenminste een van de modules.
* Verwijder zaak (deleteknop):
  * Zichtbaar indien inlogger verwijderrechten heeft op de zaakmodule van betreffende zaak.
* Toon kaart:
  * Zichtbaar indien inlogger het recht heeft locatie-adressen zichtbaar.
  * Opent de kaartviewer van de geselecteerde zaak (indien kolom Info van *Sectie: Programma Item: Toonkaart* een gevulde waarde heeft dan beschouwt OpenWave die gevulde waarde als een URL van een externe kaartviewer die geopend moet worden, anders wordt de standaardkaart (interne kaartviewer) van Openwave aangeroepen. Zie verder [Kaart](/docs/probleemoplossing/module_overstijgende_schermen/kaart.md))
* Locatie-adres:
  * Zichtbaar indien inlogger het recht heeft locatie-adressen zichtbaar.
  * Opent de detailkaart met gegevens van het locatie-adres.
* Detailscherm:
  * Zichtbaar indien inlogger het recht heeft omgevingskaarten zichtbaar.
  * Opent het detailscherm van de geselecteerde zaak.
* Memo:
  * Zichtbaar indien inlogger het recht heeft memo omgevingskaarten zichtbaar
  * Opent de memo van de geselecteerde zaak.

### Aanmaken van nieuwe zaak bij insert

Er kan gekozen worden voor **Nieuwe zaak op deze straat** of **Nieuwe zaak**. Beide knoppen starten de wizard *MaakNieuweZaak*. Indien gekozen wordt voor zaak aanmaken op deze straat, dan zal het programma het adres overnemen van de zaak in het lijstscherm waarop men staat bij klikken op knop *Nieuwe zaak op deze straat*. Indien gekozen voor knop *Nieuwe zaak* dan zal de gebruiker in de wizard *MaakNieuweZaak* eerst de locatie moeten doorgeven voor de nieuw aan te maken zaak. Voor meer informatie over aanmaken van zaken: zie [Aanmaken van nieuwe zaak](/docs/probleemoplossing/programmablokken/maak_nieuwe_zaak.md).

### Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Openingsportaal*
* Kolom: *Hoofdzaken*
* Kopregel: *Alle zaken*
* Dynamisch tegelopschrift:
* Actie: *getFlexList(SysStandardList,nil,nil,G,opening_allezaken)*

Indien men de lijst wilt aanroepen waarbij alleen de zaken voor het compartiment van de gebruiker getoond moeten worden dan is de tegeldefinitie als volgt:

* Portaal: *Openingsportaal*
* Kolom: *Hoofdzaken*
* Kopregel: *Alle zaken;(Compartiment)*
* Dynamisch tegelopschrift:
* Actie: *getFlexList(SysStandardList,nil,nil,G,opening_allezakencompartiment)*
