# Detailscherm Bezwaar/beroep

De schermidentifier is: Indien de instelling *Sectie: Programma en Item: BezwaarberoepIsZaak* is aangevinkt dan de file: MDDC_getBezwaarBeroepDetail_Z.xml en anders MDDC_getBezwaarBeroepDetail.xml.

Dit scherm kan worden aangeroepen vanuit de *Lijst Bezwaar/beroep* bij een zaak.

## Error

Het scherm geeft een foutmelding, indien:

* er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
* de inlogger geen kijkrechten heeft voor bezwaar/beroep bij betreffende hoofdzaak.

## Muteren

De kolommen kunnen gemuteerd worden indien:

* de inlogger wijzigrechten heeft op bezwaar/beroep bij betreffende hoofdzaak
* EN in het blok *Keten* is de einddatum/blokkeerdatum NIET gevuld
* EN die bovenliggende hoofdzaak niet is geblokkeerd
* EN de editschuif aan staat
* EN - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de hoofdzaak bevatten en de gemeente waar de hoofdzaak speelt EN dan moet de eigenschap *inclusief bezwaarberoep* bij dat zaaktype in het compartiment zijn aangevinkt
* EN - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar de hoofdzaak speelt in geen enkel compartiment voorkomen tenzij de eigenschap *inclusief bezwaarberoep* bij dat zaaktype in het compartiment NIET is aangevinkt. |

Een voorbeeld met betrekking tot compartimentsrechten: stel de bezwaar/beroepzaak hoort bij een omgevingszaak. Dan geldt:

* dat vwfrmomgvergunningen.dnkeycompartiment (van de betreffende omgevingszaak) gevuld moet zijn EN gelijk moet zijn aan tbmedewerkers.dnkeycompartiment (van de inlogger) EN dat vwfrmomgvergunningen.dlinclbezwaarberoep de waarde 'T' moet hebben
* OF dat tbmedewerkers.dnkeycompartiment (van de inlogger) leeg is EN vwfrmomgvergunningen.dnkeycompartiment (van de betreffende omgevingszaak) is ook leeg
* OF dat tbmedewerkers.dnkeycompartiment (van de inlogger) leeg is EN vwfrmomgvergunningen.dnkeycompartiment (van de betreffende omgevingszaak) is gevuld, maar dat vwfrmomgvergunningen.dlinclbezwaarberoep de waarde 'F' heeft.

Voor de dropdownlijst met **verantwoordelijke jurist** geldt het volgende:

* de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
* en de medewerker moet in dienst zijn
* en het vakje *interne medewerker* moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap: *overrule compartiment* aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

### Extern zaak/DMS nummer

Hieronder komt het begrip externe zaak/DMS nummer voor. Daarmee wordt bedoeld de kolom externe zaak/dms (dvintzaakcode) die voor kan komen op de bezwaar/beroepkaart zelf en/of bij de bovenliggende hoofdzaak. Het programma kijkt naar de bezwaar/beroepkaart zelf indien de instelling *Sectie: Programma en Item: BezwaarberoepIsZaak* is aangevinkt.

In alle andere gevallen (niet aangevinkt of instelling bestaat niet) dan komt het externe zaak/DMS nummer uit de hoofdzaak van de betreffende module.

### Zichtbaarheid blokken

Het blok **Keten** is alleen zichtbaar indien de instelling instelling *Sectie: Programma en Item: BezwaarberoepIsZaak* is aangevinkt.

### Contactadressen

Aan elke bezwaar/beroepzaak kunnen één of meer contacten worden toegevoegd.
Zie lijst en detailscherm bij [ContactenLijst](/docs/probleemoplossing/module_overstijgende_schermen/contactenlijst.md).

## Triggers in het scherm zelf achter kolommen

### Bepaal uitspraak datum en besluit achter de kolom uitspraakdatum

* Zichtbaar en enabled indien:
  * de inlogger wijzigrechten heeft op de bezwaar/beroepkaart voor de betreffende module
  * EN de eindedatum in blok *Keten* is NIET gevuld.

Indien de uitspraakdatum gevuld is dan worden - na een waarschuwing - zowel die datum als het (soort)besluit leeggemaakt. Bij het vullen van de datum MOET een soort besluit worden gekozen.

### Maak Zaak in zaak/DMS achter de kolom zaak/DMS code in blok Keten

* Zichtbaar en enabled indien:
  * de inlogger muteerrechten heeft op bezwaar/beroep
  * EN de einddatum zaak/dms (dddmsafgehandeld) moet leeg zijn
  * EN externe zaak/dms nummer (dvintzaakcode) een **lege waarde** heeft
  * EN de bovenliggende zaak niet is geblokkeerd
  * EN - indien de bezwaarberoepzaak NIET onder een compartiment valt - de instelling *Sectie: Koppeling Zaak* en *Item: Methode* en *Tekst: StUF-ZAKEN 310* staat aangevinkt
  * EN - indien de bezwaarberoepzaak WEL onder een compartiment valt - dan moet de kolom *dmsmethode* van het betreffende compartiment in het beheerportaal-Nieuw gevuld zijn met *StUF-Zaken 310*
  * EN de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan (bijvoorbeeld dlcomgbezwdms)
  * EN - indien de bezwaarberoepzaak NIET onder een compartiment valt - dan moet de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: ZaaktypeBezwaarBeroep* gevuld zijn (en aangevinkt)
  * EN - indien de hoofdzaak WEL onder een compartiment valt - dan moet de kolom *zaaktype zaak/dmssysteem (dvdmszaaktypebezwaarberoep)* van het betreffende compartiment in beheerportaal-Nieuw gevuld zijn
  * EN het bezwaar/beroep een zelfstandige zaak is in externe zaaksysteem:  de instelling *Sectie: Programma en Item: BezwaarBeroepIsZaak* is aangevinkt
  * EN er minimaal één contactpersoon is bij de bezwaar/beroepkaart zijn met de rol IND (indiener).

### Sluit of heropen zaak in zaak/DMS systeem

Achter einddatum/blokkeerdatum van zaak/DMS nummer in het blok *Keten*.

* Zichtbaar en enabled indien:
  * de inlogger muteerrechten heeft op de bezwaar/beroep
  * EN externe zaak/dms nummer (dvintzaakcode) een **gevulde** waarde heeft
  * EN de bovenliggende zaak niet is geblokkeerd
  * EN - indien de bezwaarberoepzaak NIET onder een compartiment valt - de instelling *Sectie: Koppeling Zaak* en *Item: Methode* en *Tekst: StUF-ZAKEN 310* staat aangevinkt
  * EN - indien de bezwaarberoepzaak WEL onder een compartiment valt - dan moet de kolom *dmsmethode* van het betreffende compartiment in beheerportaal-Nieuw gevuld zijn met *StUF-Zaken 310*
  * EN de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan (bijvoorbeeld dlcomgbezwdms)
  * EN - voor het heropenen - de inlogger is lid van rechtengroep die het recht wijzigen (DMS) afgehandeld datums bij betreffende module/inrichting aangevinkt heeft staan (zoals tbomgrechten.dlbomgafsedt)
  * EN bezwaar/beroep een zelfstandige zaak is in externe zaaksysteem: de instelling *Sectie: Programma en Item: BezwaarBeroepIsZaak* is aangevinkt
  * EN het resultaat zoals dat doorgegeven moet worden aan het zaak/DMS gevuld is (zie beheertegel *Uitspraak bezwaarberoep* (tbaardbeslbezwaar)). Deze wordt gevuld door het vullen van de uitspraakdatum.

## Triggers rechtsboven in menu opties

### Toon geregistreerde documenten (bij dit bezwaarberoep)

Zie [Geregistreerde Documenten](/docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten.md).

* Zichtbaar en enabled indien:
  * de instelling *Sectie: Documenten en Item: Documentregistratie* is aangevinkt
  * EN de gebruiker het recht *Inzien geregistreerde documenten bij de betreffende module* aangevinkt heeft staat  (bijv. tbomgrechten.dlcomgcorregvsb).

#### Creëer document

Zie [Creëer document](/docs/probleemoplossing/programmablokken/creeer_document.md).

* Zichtbaar indien:
  * de inlogger lid is van een rechtengroep die bij hoofdzaak het recht creëren van documenten heeft
  * EN compartiment OK.
* De knop is disabled indien de bovenliggende zaak geblokkeerd is.

### Toon uploads bij dit bezwaar/beroep

Zie [Upload Lijst](/docs/probleemoplossing/module_overstijgende_schermen/uploads_lijst.md).

* Zichtbaar en enabled indien:
  * de instelling *Sectie: Documenten* en *Item: MultipleUpload* aangevinkt is
  * EN de inlogger lid is van een rechtengroep die bij hoofdzaak het recht uploaden van documenten heeft.

### Deblokkeer (leegmaken einde/blokkeer-datum)

* Zichtbaar en enabled indien:
  * de inlogger muteerrechten heeft op de bezwaar/beroep
  * EN de einddedatum (in blok *Keten*) een **gevulde** waarde heeft
  * EN externe zaak/dms nummer (dvintzaakcode) een **gevulde** waarde heeft
  * EN de bovenliggende zaak niet is geblokkeerd
  * EN - indien de bezwaarberoepzaak NIET onder een compartiment valt - de instelling *Sectie: Koppeling Zaak* en *Item: Methode* en *Tekst: StUF-ZAKEN 310* staat aangevinkt
  * EN - indien de bezwaarberoepzaak WEL onder een compartiment valt - dan moet de kolom *dmsmethode* van het betreffende compartiment in beheerportaal-Nieuw gevuld zijn met *StUF-Zaken 310*
  * de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan
  * EN bezwaar/beroep een zelfstandige zaak is in externe zaaksysteem: de instelling *Sectie: Programma en Item: BezwaarBeroepIsZaak* is aangevinkt
  * EN de inlogger het recht leegmaken afhandeldatum bezwaar/beroep heeft voor de betreffende module (bijv. dlbomgafsedt = ‘T’).

## Triggers linksonder

### Toon documenten

Zie [Toon documenten en download](/docs/probleemoplossing/programmablokken/toon_documenten_en_download.md).

* Zichtbaar wanneer:
  * een van onderstaande twee beweringen waar is:
    * de instelling *Sectie: Documenten en Item: Documentregistratie* is aangevinkt EN de gebruiker het recht *Inzien geregistreerde documenten* bij de betreffende module aangevinkt heeft staat (bijv. tbomgrechten.dlcomgcorregvsb)
    * deze instelling staat niet aan EN de gebruiker het recht *Inzien documenten buiten registratie om bij de betreffende module* aangevinkt heeft staat  (bijv. tbomgrechten.dlcomgcorvsb)
  * EN wanneer tenminste één van onderstaande twee instellingen is aangevinkt
    * *Sectie: Documenten* en *Item: OphalenViaFileserver*
    * *Sectie: Documenten* en *Item: OphalenViaDms*.
* Enabled indien:
  * de  programma-instelling *Sectie: Documenten* en *Item: OphalenViaFileserver* aangevinkt is
  * OF  de  programma-instelling *Sectie: Documenten* en *Item: OphalenViaDMS* is aangevinkt
    * EN *Sectie: KoppelingDOCNAARDMS* en *Item: Methode* en *Tekst: CMIS 1.0* en aangevinkt
  * OF de programma-instelling *Sectie: Documenten* en *Item: OphalenViaDMS* is aangevinkt
    * EN *Sectie: KoppelingDOCNAARDMS* en *Item: Methode* en *Tekst: StUF-ZAKEN 310* (en aangevinkt) en het externe zaak/DMS nummer is gevuld
  * OF de programma-instelling *Sectie: Documenten en Item: OphalenViaDMS* is aangevinkt
    * EN de instelling *Sectie: KoppelingDOCNAARDMS en Item: Methode en Tekst: StUF-ZAKEN 310* en aangevinkt EN de kolom externe zaak/dms nummer (dvintzaakcode) is leeg MAAR de instelling *Sectie: KoppelingDOCNAARDMS en Item: Ontvangstadres_cmis* is gevuld (bijzondere instelling in hybride situatie dat zowel via Stuf Zaak/DMS als via CMIS documenten opgehaald moeten kunnen worden).

Indien de instelling *Sectie: Documenten en Item: Documentregistratie* is aangevinkt wordt met de knop de lijst met geregistreerde documenten geopend zie [Geregistreerde Documenten](/docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten.md). Anders wordt de algemene documentenlijst geopend.

### Upload document(en)

Zie [Upload document](/docs/probleemoplossing/programmablokken/upload_document.md).

* Zichtbaar wanneer compartiment OK en tenminste één van onderstaande twee instellingen is aangevinkt:
  * *Sectie: Documenten* en *Item: OphalenViaFileserver*
  * *Sectie: Documenten* en *Item: OphalenViaDms* EN de instelling *Sectie: Documenten* en *Item: MultipleUpload* aangevinkt is.
* Enabled indien:
  * bovenliggende zaak niet geblokkeerd is
  * EN tenminste één van onderstaande drie items waar is:
    * de programma-instelling *Sectie: Documenten* en *Item: OphalenViaFileserver* is aangevinkt
    * de programma-instelling *Sectie: Documenten* en *Item: OphalenViaDMS* is aangevinkt EN *Sectie: KoppelingDOCNAARDMS* en *Item: Methode* en *Tekst: CMIS 1.0* is aangevinkt
    * de programma-instelling *Sectie: Documenten* en *Item: OphalenViaDMS* is aangevinkt EN *Sectie: KoppelingDOCNAARDMS* en *Item: Methode* en *Tekst = StUF-ZAKEN 310* is aangevinkt en het externe zaak/DMS nummer is gevuld.

### Urenregistratie

* Zichtbaar en enabled indien de inlogger compartimentsrechten heeft EN:
  * het recht *uren zichtbaar* aangevinkt heeft staan bij blok *Bezwaar/beroep* bij de betreffende module (beheer functionele rechten)
  * OF het recht *mag uren van anderen muteren* aangevinkt heeft staan op de medewerkerskaart.
