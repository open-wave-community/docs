# Lijst Mijn Openstaande Horecazaken

Schermidentifier: MDLC_getOpenMilieuGebruikzakenList.xml.

## Welke gegevens worden getoond

De rijen uit de view vwfrmhorvergorkestrator_lopend, dat zijn horecazaken:

  * met lege besluit/afgehandeld datum 
  * EN lege ingetrokken datum 
  * EN lege blokkeerdatum.

Boven op deze where clausules van de view is de volgende extra restrictie van kracht afhankelijk van de vierde parameter van de flexlist aanroep: getFlexList(OpenHorecaZaken,nil,nil,I,O).

De 4 parameter heeft de waarde:

  * I = programma filtert op die openstaande Horecazaken waarvoor de inlogger gelijk is aan de actieve behandelaar dan wel de zaakverantwoordelijke (dvcodeaccountman)
  * of T = programma filtert op die openstaande Horecazaken waarvoor de inlogger behoort tot het zaakverantwoordelijk team. 

## Problemen

  * De lijst is leeg of geeft maar een gedeelte van de open horecazaken:
    * de inlogger heeft geen kijkrechten op horecazaken.
  * De lijst geeft een foutmelding:
    * er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

  * zoekeditbox rechtsonder: altijd aanwezig 
  * pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling *Getal1* bij *Sectie: paging* en *Item: pagesize* (defaultwaarde = 100)
  * klikken op regel opent altijd bijbehorend zaakportaal Horeca
  * versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).

### Knoppen linskonder

  * Toon kaart:
    * Zichtbaar indien inlogger het recht heeft locatie-adressen zichtbaar.
    * Opent de kaartviewer van de geselecteerde zaak.
  * Locatie-adres:
    * Zichtbaar indien inlogger het recht heeft locatie-adressen zichtbaar.
    * Opent de detailkaart met gegevens van het locatie-adres.
  * Detailscherm:
    * Zichtbaar indien inlogger het recht heeft omgevingskaarten zichtbaar.
    * Opent het detailscherm van de geselecteerde zaak.
  * Memo:
    * Zichtbaar indien inlogger het inzien memo-recht heeft (tbhorrechten.dlbhormemovsb)
    * Opent de memo van de geselecteerde zaak.

## Betekenis kleurenballetjes

  * Eerste kolom (dvzaakgevaar):
    * leeg indien de fatale datum leeg is
    * rood indien datum_van_vandaag > fatale datum 
    * oranje indien vandaag < = fatale datum < = datum_van_vandaag + 2
    * wit in alle andere gevallen. 
  *  Kolom Proces (dvprocesgevaar):
    * leeg indien geen proces gedefinieerd bij zaak
    * groen indien er geen openstaande processtappen zijn 
    * rood indien er tenminste één openstaande processtap is met streefdatum < = datum_van_vandaag 
    * oranje indien er tenminste één openstaande processtap is met vandaag < streefdatum < = datum_van_vandaag + 2
    * wit in alle andere gevallen. 
  *  Kolom Advies (dvadviesgevaar):
    * leeg indien geen advies gedefinieerd bij zaak
    * groen indien er geen openstaande adviezen zijn
    * rood indien er tenminste één openstaand advies is met een rappeldatum < = datum_van_vandaag 
    * oranje indien er tenminste één openstaande advies is met vandaag < rappeldatum < = datum_van_vandaag + 2
    * wit in alle andere gevallen. 

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde iconen, zie hiervoor [Sectie OWB](/docs/instellen_inrichten/configuratie/sectie_owb.md).

