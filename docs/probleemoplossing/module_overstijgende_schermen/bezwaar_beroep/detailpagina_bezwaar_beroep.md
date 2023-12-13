# Detailscherm Bezwaar/beroep

De schermidentifier is: Indien de instelling _Sectie: Programma en Item: BezwaarberoepIsZaak_ is aangevinkt dan de file: MDDC_getBezwaarBeroepDetail_Z.xml en anders MDDC_getBezwaarBeroepDetail.xml.

Dit scherm kan worden aangeroepen vanuit de _Lijst Bezwaar/beroep_ bij een zaak.

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft voor bezwaar/beroep bij betreffende hoofdzaak.

## Muteren

De kolommen kunnen gemuteerd worden indien:

- de inlogger wijzigrechten heeft op bezwaar/beroep bij betreffende hoofdzaak
- en in het blok _Keten_ is de einddatum/blokkeerdatum NIET gevuld
- en die bovenliggende hoofdzaak niet is geblokkeerd
- en de editschuif aan staat
- en - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de hoofdzaak bevatten en de gemeente waar de hoofdzaak speelt en dan moet de eigenschap _inclusief bezwaarberoep_ bij dat zaaktype in het compartiment zijn aangevinkt
- en - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar de hoofdzaak speelt in geen enkel compartiment voorkomen tenzij de eigenschap _inclusief bezwaarberoep_ bij dat zaaktype in het compartiment NIET is aangevinkt. |

Een voorbeeld met betrekking tot compartimentsrechten: stel de bezwaar/beroepzaak hoort bij een omgevingszaak. Dan geldt:

- dat vwfrmomgvergunningen.dnkeycompartiment (van de betreffende omgevingszaak) gevuld moet zijn en gelijk moet zijn aan tbmedewerkers.dnkeycompartiment (van de inlogger) en dat vwfrmomgvergunningen.dlinclbezwaarberoep de waarde 'T' moet hebben
- OF dat tbmedewerkers.dnkeycompartiment (van de inlogger) leeg is en vwfrmomgvergunningen.dnkeycompartiment (van de betreffende omgevingszaak) is ook leeg
- OF dat tbmedewerkers.dnkeycompartiment (van de inlogger) leeg is en vwfrmomgvergunningen.dnkeycompartiment (van de betreffende omgevingszaak) is gevuld, maar dat vwfrmomgvergunningen.dlinclbezwaarberoep de waarde 'F' heeft.

Voor de dropdownlijst met **verantwoordelijke jurist** geldt het volgende:

- de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
- en de medewerker moet in dienst zijn
- en het vakje _interne medewerker_ moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap: _overrule compartiment_ aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

### Extern zaak/DMS nummer

Hieronder komt het begrip externe zaak/DMS nummer voor. Daarmee wordt bedoeld de kolom externe zaak/dms (dvintzaakcode) die voor kan komen op de bezwaar/beroepkaart zelf en/of bij de bovenliggende hoofdzaak. Het programma kijkt naar de bezwaar/beroepkaart zelf indien de instelling _Sectie: Programma en Item: BezwaarberoepIsZaak_ is aangevinkt.

In alle andere gevallen (niet aangevinkt of instelling bestaat niet) dan komt het externe zaak/DMS nummer uit de hoofdzaak van de betreffende module.

### Zichtbaarheid blokken

Het blok **Keten** is alleen zichtbaar indien de instelling instelling _Sectie: Programma en Item: BezwaarberoepIsZaak_ is aangevinkt.

### Contactadressen

Aan elke bezwaar/beroepzaak kunnen één of meer contacten worden toegevoegd.
Zie lijst en detailscherm bij [ContactenLijst](contactenlijst.md).

## Triggers in het scherm zelf achter kolommen

### Bepaal uitspraak datum en besluit achter de kolom uitspraakdatum

- Zichtbaar en enabled indien:
  - de inlogger wijzigrechten heeft op de bezwaar/beroepkaart voor de betreffende module
  - en de eindedatum in blok _Keten_ is NIET gevuld.

Indien de uitspraakdatum gevuld is dan worden - na een waarschuwing - zowel die datum als het (soort)besluit leeggemaakt. Bij het vullen van de datum MOET een soort besluit worden gekozen.

### Maak Zaak in zaak/DMS achter de kolom zaak/DMS code in blok Keten

- Zichtbaar en enabled indien:
  - de inlogger muteerrechten heeft op bezwaar/beroep
  - en de einddatum zaak/dms (dddmsafgehandeld) moet leeg zijn
  - en externe zaak/dms nummer (dvintzaakcode) een **lege waarde** heeft
  - en de bovenliggende zaak niet is geblokkeerd
  - en - indien de bezwaarberoepzaak NIET onder een compartiment valt - de instelling _Sectie: Koppeling Zaak_ en _Item: Methode_ en _Tekst: StUF-ZAKEN 310_ staat aangevinkt
  - en - indien de bezwaarberoepzaak WEL onder een compartiment valt - dan moet de kolom _dmsmethode_ van het betreffende compartiment in het beheerportaal-Nieuw gevuld zijn met _StUF-Zaken 310_
  - en de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan (bijvoorbeeld dlcomgbezwdms)
  - en - indien de bezwaarberoepzaak NIET onder een compartiment valt - dan moet de kolom _Tekst_ van de instelling _Sectie: Koppeling ZAAK_ en _Item: ZaaktypeBezwaarBeroep_ gevuld zijn (en aangevinkt)
  - en - indien de hoofdzaak WEL onder een compartiment valt - dan moet de kolom _zaaktype zaak/dmssysteem (dvdmszaaktypebezwaarberoep)_ van het betreffende compartiment in beheerportaal-Nieuw gevuld zijn
  - en het bezwaar/beroep een zelfstandige zaak is in externe zaaksysteem: de instelling _Sectie: Programma en Item: BezwaarBeroepIsZaak_ is aangevinkt
  - en er minimaal één contactpersoon is bij de bezwaar/beroepkaart zijn met de rol IND (indiener).

### Sluit of heropen zaak in zaak/DMS systeem

Achter einddatum/blokkeerdatum van zaak/DMS nummer in het blok _Keten_.

- Zichtbaar en enabled indien:
  - de inlogger muteerrechten heeft op de bezwaar/beroep
  - en externe zaak/dms nummer (dvintzaakcode) een **gevulde** waarde heeft
  - en de bovenliggende zaak niet is geblokkeerd
  - en - indien de bezwaarberoepzaak NIET onder een compartiment valt - de instelling _Sectie: Koppeling Zaak_ en _Item: Methode_ en _Tekst: StUF-ZAKEN 310_ staat aangevinkt
  - en - indien de bezwaarberoepzaak WEL onder een compartiment valt - dan moet de kolom _dmsmethode_ van het betreffende compartiment in beheerportaal-Nieuw gevuld zijn met _StUF-Zaken 310_
  - en de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan (bijvoorbeeld dlcomgbezwdms)
  - en - voor het heropenen - de inlogger is lid van rechtengroep die het recht wijzigen (DMS) afgehandeld datums bij betreffende module/inrichting aangevinkt heeft staan (zoals tbomgrechten.dlbomgafsedt)
  - en bezwaar/beroep een zelfstandige zaak is in externe zaaksysteem: de instelling _Sectie: Programma en Item: BezwaarBeroepIsZaak_ is aangevinkt
  - en het resultaat zoals dat doorgegeven moet worden aan het zaak/DMS gevuld is (zie beheertegel _Uitspraak bezwaarberoep_ (tbaardbeslbezwaar)). Deze wordt gevuld door het vullen van de uitspraakdatum.

## Triggers rechtsboven in menu opties

### Toon geregistreerde documenten (bij dit bezwaarberoep)

Zie [Geregistreerde Documenten](geregistreerde_documenten/README.md).

- Zichtbaar en enabled indien:
  - de instelling _Sectie: Documenten en Item: Documentregistratie_ is aangevinkt
  - en de gebruiker het recht _Inzien geregistreerde documenten bij de betreffende module_ aangevinkt heeft staat (bijv. tbomgrechten.dlcomgcorregvsb).

#### Creëer document

Zie [Creëer document](../programmablokken/creeer_document.md).

- Zichtbaar indien:
  - de inlogger lid is van een rechtengroep die bij hoofdzaak het recht creëren van documenten heeft
  - en compartiment OK.
- De knop is disabled indien de bovenliggende zaak geblokkeerd is.

### Toon uploads bij dit bezwaar/beroep

Zie [Upload Lijst](uploads_lijst.md).

- Zichtbaar en enabled indien:
  - de instelling _Sectie: Documenten_ en _Item: MultipleUpload_ aangevinkt is
  - en de inlogger lid is van een rechtengroep die bij hoofdzaak het recht uploaden van documenten heeft.

### Deblokkeer (leegmaken einde/blokkeer-datum)

- Zichtbaar en enabled indien:
  - de inlogger muteerrechten heeft op de bezwaar/beroep
  - en de einddedatum (in blok _Keten_) een **gevulde** waarde heeft
  - en externe zaak/dms nummer (dvintzaakcode) een **gevulde** waarde heeft
  - en de bovenliggende zaak niet is geblokkeerd
  - en - indien de bezwaarberoepzaak NIET onder een compartiment valt - de instelling _Sectie: Koppeling Zaak_ en _Item: Methode_ en _Tekst: StUF-ZAKEN 310_ staat aangevinkt
  - en - indien de bezwaarberoepzaak WEL onder een compartiment valt - dan moet de kolom _dmsmethode_ van het betreffende compartiment in beheerportaal-Nieuw gevuld zijn met _StUF-Zaken 310_
  - de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan
  - en bezwaar/beroep een zelfstandige zaak is in externe zaaksysteem: de instelling _Sectie: Programma en Item: BezwaarBeroepIsZaak_ is aangevinkt
  - en de inlogger het recht leegmaken afhandeldatum bezwaar/beroep heeft voor de betreffende module (bijv. dlbomgafsedt = ‘T’).

## Triggers linksonder

### Toon documenten

Zie [Toon documenten en download](../programmablokken/toon_documenten_en_download.md).

- Zichtbaar wanneer:
  - een van onderstaande twee beweringen waar is:
    - de instelling _Sectie: Documenten en Item: Documentregistratie_ is aangevinkt en de gebruiker het recht _Inzien geregistreerde documenten_ bij de betreffende module aangevinkt heeft staat (bijv. tbomgrechten.dlcomgcorregvsb)
    - deze instelling staat niet aan en de gebruiker het recht _Inzien documenten buiten registratie om bij de betreffende module_ aangevinkt heeft staat (bijv. tbomgrechten.dlcomgcorvsb)
  - en wanneer tenminste één van onderstaande twee instellingen is aangevinkt
    - _Sectie: Documenten_ en _Item: OphalenViaFileserver_
    - _Sectie: Documenten_ en _Item: OphalenViaDms_.
- Enabled indien:
  - de programma-instelling _Sectie: Documenten_ en _Item: OphalenViaFileserver_ aangevinkt is
  - OF de programma-instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_ is aangevinkt
    - en _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ en _Tekst: CMIS 1.0_ en aangevinkt
  - OF de programma-instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_ is aangevinkt
    - en _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ en _Tekst: StUF-ZAKEN 310_ (en aangevinkt) en het externe zaak/DMS nummer is gevuld
  - OF de programma-instelling _Sectie: Documenten en Item: OphalenViaDMS_ is aangevinkt
    - en de instelling _Sectie: KoppelingDOCNAARDMS en Item: Methode en Tekst: StUF-ZAKEN 310_ en aangevinkt en de kolom externe zaak/dms nummer (dvintzaakcode) is leeg MAAR de instelling _Sectie: KoppelingDOCNAARDMS en Item: Ontvangstadres_cmis_ is gevuld (bijzondere instelling in hybride situatie dat zowel via Stuf Zaak/DMS als via CMIS documenten opgehaald moeten kunnen worden).

Indien de instelling _Sectie: Documenten en Item: Documentregistratie_ is aangevinkt wordt met de knop de lijst met geregistreerde documenten geopend zie [Geregistreerde Documenten](geregistreerde_documenten/README.md). Anders wordt de algemene documentenlijst geopend.

### Upload document(en)

Zie [Upload document](../programmablokken/upload_document.md).

- Zichtbaar wanneer compartiment OK en tenminste één van onderstaande twee instellingen is aangevinkt:
  - _Sectie: Documenten_ en _Item: OphalenViaFileserver_
  - _Sectie: Documenten_ en _Item: OphalenViaDms_ en de instelling _Sectie: Documenten_ en _Item: MultipleUpload_ aangevinkt is.
- Enabled indien:
  - bovenliggende zaak niet geblokkeerd is
  - en tenminste één van onderstaande drie items waar is:
    - de programma-instelling _Sectie: Documenten_ en _Item: OphalenViaFileserver_ is aangevinkt
    - de programma-instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_ is aangevinkt en _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ en _Tekst: CMIS 1.0_ is aangevinkt
    - de programma-instelling _Sectie: Documenten_ en _Item: OphalenViaDMS_ is aangevinkt en _Sectie: KoppelingDOCNAARDMS_ en _Item: Methode_ en _Tekst = StUF-ZAKEN 310_ is aangevinkt en het externe zaak/DMS nummer is gevuld.

### Urenregistratie

- Zichtbaar en enabled indien de inlogger compartimentsrechten heeft en:
  - het recht _uren zichtbaar_ aangevinkt heeft staan bij blok _Bezwaar/beroep_ bij de betreffende module (beheer functionele rechten)
  - OF het recht _mag uren van anderen muteren_ aangevinkt heeft staan op de medewerkerskaart.
