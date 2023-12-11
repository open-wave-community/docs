# Lijst Mijn Openstaande omgevingszaken

Schermidentifier: MDLC_geefOpenOmgZakenLijst.xml.

## Welke gegevens worden getoond

De rijen uit de view vwfrmomgorkestrator_lopend, dat zijn omgevingszaken:

- met lege besluit/afgehandeld datum
- en lege ingetrokken datum
- en lege blokkeerdatum

Boven op deze where clausules van de view is de volgende extra restrictie van kracht afhankelijk van de vierde parameter van de flexlist aanroep: getFlexList(OpenOmgZaken,nil,nil,I,W).

De 4 parameter heeft de waarde:

- I = programma filtert op die openstaande omgevingszaken waarvoor de inlogger gelijk is aan de actieve behandelaar dan wel de zaakverantwoordelijke (dvcodeaccountman)
- T = programma filtert op die openstaande omgevingszaken waarvoor de inlogger behoort tot het zaakverantwoordelijk team.

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de open omgevingszaken:
  - de inlogger heeft geen kijkrechten op omgevingszaken.
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Bijzondere kolommen

- kolom Beh.ins (dvcompartimentsnaam) is alleen zichtbaar indien er tenminste één compartiment is gedefinieerd (beheertegel _Compartimentsrechten_)
- kolom Team (dvteamnaamzaakverantw) is alleen zichtbaar indien _Getal1_ van de instelling _Sectie: Zaakverantwoordelijke en Item = Omgeving_ de waarde 2 of 3 heeft.
- de kolom Straatnaam/Projectlocatie wordt in principe gevuld met de openbareruimtenaam uit tbperceeladressen tenzij bij dat perceeladres de kolom dlonbekendadres is aangevinkt en er een hoofdprojectlocatie opgegeven is onder de tegel Projectlocaties/Kadastrale percelen. In dat laatste geval zal de opgegeven hoofdprojectlocatieomschrijving (de kolom tbzaakkadperc.dvstraatnaam) van de zaak getoond worden.

## Triggers

Welke zijn van toepassing op deze lijst?

- zoekeditbox rechtsonder: altijd aanwezig
- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ bij _Sectie: Paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd bijbehorend zaakportaal omgeving
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).

### Knoppen linskonder

- Toon kaart:
  - Zichtbaar indien inlogger het recht heeft locatie-adressen zichtbaar.
  - Opent de kaartviewer van de geselecteerde zaak.
- Locatie-adres:
  - Zichtbaar indien inlogger het recht heeft locatie-adressen zichtbaar.
  - Opent de detailkaart met gegevens van het locatie-adres.
- Detailscherm:
  - Zichtbaar indien inlogger het recht heeft omgevingskaarten zichtbaar.
  - Opent het detailscherm van de geselecteerde zaak.
- Memo:
  - Zichtbaar indien inlogger het inzien memo-recht heeft (tbomgrechten.dlbomgmemovsb)
  - Opent de memo van de geselecteerde zaak.

## Betekenis kleurenballetjes

- Eerste kolom (dvzaakgevaar):
  - leeg indien de fatale datum leeg is
  - rood indien datum_van_vandaag > fatale datum
  - oranje indien vandaag < = fatale datum < = datum_van_vandaag + waarschuwingsperiode (Zaakbeheer: tegel Zaaktypes omgeving, kolom fatale termijn waarschuwingsperiode)
  - wit in alle andere gevallen.
- Kolom Proces (dvprocesgevaar):
  \*leeg indien geen proces gedefinieerd bij zaak
  - groen indien er geen openstaande processtappen zijn
    \*rood indien er tenminste één openstaande processtap is met streefdatum < = datum_van_vandaag
  - oranje indien er tenminste één openstaande processtap is met vandaag < streefdatum < = datum_van_vandaag + waarschuwingsperiode (portal beheer: tegel zaaktypes omgeving, kolom processtap waarschuwingsperiode)
  - wit in alle andere gevallen.
- Kolom Advies (dvadviesgevaar):
  \*leeg indien geen advies gedefinieerd bij zaak
  - groen indien er geen openstaande adviezen zijn
    \*rood indien er tenminste één openstaand advies is met een rappeldatum < = datum_van_vandaag
  - oranje indien er tenminste één openstaande advies is met vandaag < rappeldatum < = datum_van_vandaag + waarschuwingsperiode (Zaakbeheer: tegel Zaaktypes omgeving, kolom advies waarschuwingsperiode)
  - wit in alle andere gevallen.
- Kolom OLO (dvologevaar):
  \*leeg indien geen OLO-berichten (bijlagen) gedefinieerd bij zaak
  - groen indien er geen openstaande OLO-berichten zijn
  - rood indien er tenminste één openstaand OLO-bericht is.
- Kolom Inr (dvinrverplgevaar). Een zaak moet aan een inrichting worden gekoppeld indien tenminste één van de activiteiten/onderdelen de eigenschap inrichting verplicht heeft (beheertegel _Soort activiteit/onderdelen_, kolom _eigenschappen: inrichting verplicht_):
  \*leeg indien het koppelen van een inrichting niet verplicht is bij de zaak (of er is al een inrichting gekoppeld)
  - rood indien er geen inrichting is gekoppeld terwijl dit wel verplicht is.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde iconen, zie hiervoor [Sectie OWB](/docs/instellen_inrichten/configuratie/sectie_owb.md).
