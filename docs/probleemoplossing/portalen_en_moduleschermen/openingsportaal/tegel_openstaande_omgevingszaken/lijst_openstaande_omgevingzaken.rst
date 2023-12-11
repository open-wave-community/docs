Lijst Openstaande omgevingszaken
================================

Schermidentifier: MDLC_geefOpenOmgZakenLijst.xml.

Welke gegevens worden getoond
-----------------------------

De rijen uit de view vwfrmomgorkestrator_lopend, dat zijn
omgevingszaken:

-  met lege besluit/afgehandeld datum
-  en lege ingetrokken datum
-  en lege blokkeerdatum.

De API legt daar de volgende restrictie overheen:

-  Indien de kolom *alleen gemeentes* (zie beheertegel *Medewerkers*)
   bij de kaart van de inlogger gevuld is, dan worden alleen die
   omgevingszaken getoond waarvan de id van de locatie-gemeente (bedoeld
   wordt de locatie waaraan de bovenliggende zaak is verbonden) voorkomt
   in die kolom *alleen gemeentes*.
-  Compartimentsrestricties. Zie hiertoe de uitleg bij de tegel waarvan
   deze lijst wordt aangeroepen.

Problemen
---------

-  De lijst is leeg of geeft maar een gedeelte van de open
   omgevingszaken:

   -  de inlogger heeft geen kijkrechten op omgevingszaken
   -  op de medewerkerskaart van de inlogger staat dat hij/zij alleen
      gegevens kan zien van bepaalde gemeentes
   -  de medewerker is lid van een compartiment.

-  De lijst geeft een foutmelding:

   -  er is mogelijk een zelf gedefinieerde schermindeling gebruikt
      (Schermkolomdefinitie onder Beheer) die niet valide is.

Zichtbaarheid bepaalde kolommen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  kolom **Beh.ins** (dvcompartimentsnaam) is alleen zichtbaar indien er
   tenminste één compartiment is gedefinieerd (beheertegel
   *Compartimentsrechten*)
-  kolom **Team** (dvteamnaamzaakverantw) is alleen zichtbaar indien
   *Getal1* van de instelling *Sectie: Zaakverantwoordelijke en Item =
   Omgeving* de waarde 2 of 3 heeft
-  de kolommen **CT Uit** (dnaantalctuitstaand) en **CT Ret**
   (dnaantalctretour) en **CT Gez** (dnaantalctgezien) zijn alleen
   zichtbaar indien de instelling *sectie: Programma* en *Item:
   OmgAantCollegToetsZichtbaar* aangevinkt is. Dnaantalctuitstaand met
   het aantal uitstaande (dus nog niet geretourneerde) collegiale
   toetsen bij de zaak. Dnaantalctretour met het aantal geretourneerde
   collegiale toetsen bij de zaak. Dnaantalctgezien met het aantal
   geretourneerde + geziene collegiale toetsen bij de zaak.

Triggers
--------

Welke zijn van toepassing op deze lijst?

-  zoekeditbox rechtsonder: altijd aanwezig
-  pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de
   instelling *Getal1* bij *Sectie: Paging* en *Item: pagesize*
   (defaultwaarde = 100)
-  klikken op regel opent altijd bijbehorend zaakportaal omgeving
-  versie-informatie rechtsonder (hierop klikken en screensource =
   tbscreencolumns geeft aan of er een afwijkende schermkolommen
   definitie gebruikt wordt).

Betekenis kleurenballetjes
--------------------------

-  Eerste kolom (dvzaakgevaar):

   -  leeg indien de fatale datum leeg is
   -  rood indien datum_van_vandaag > fatale datum
   -  oranje indien vandaag < = fatale datum < = datum_van_vandaag +
      waarschuwingsperiode (Zaakbeheer: tegel Zaaktypes omgeving, kolom
      fatale termijn waarschuwingsperiode)
   -  wit in alle andere gevallen.

-  Kolom Proces (dvprocesgevaar): \*leeg indien geen proces gedefinieerd
   bij zaak

   -  groen indien er geen openstaande processtappen zijn \*rood indien
      er tenminste één openstaande processtap is met streefdatum < =
      datum_van_vandaag
   -  oranje indien er tenminste één openstaande processtap is met
      vandaag < streefdatum < = datum_van_vandaag + waarschuwingsperiode
      (Zaakbeheer: tegel Zaaktypes omgeving, kolom processtap
      waarschuwingsperiode)
   -  wit in alle andere gevallen.

-  Kolom Advies (dvadviesgevaar): \*leeg indien geen advies gedefinieerd
   bij zaak

   -  groen indien er geen openstaande adviezen zijn \*rood indien er
      tenminste één openstaand advies is met een rappeldatum < =
      datum_van_vandaag
   -  oranje indien er tenminste één openstaande advies is met vandaag <
      rappeldatum < = datum_van_vandaag + waarschuwingsperiode
      (Zaakbeheer: tegel Zaaktypes omgeving, kolom advies
      waarschuwingsperiode)
   -  wit in alle andere gevallen.

-  Kolom OLO (dvologevaar): \*leeg indien geen OLO-berichten (bijlagen)
   gedefinieerd bij zaak

   -  groen indien er geen openstaande OLO-berichten zijn.
   -  rood indien er tenminste één openstaand OLO-bericht is.

-  Kolom Inr (dvinrverplgevaar). Een zaak moet aan een inrichting worden
   gekoppeld indien tenminste één van de activiteiten/onderdelen de
   eigenschap inrichting verplicht heeft (beheertegel *Soort
   activiteit/onderdelen*, kolom *eigenschappen: inrichting verplicht*):
   \*leeg indien het koppelen van een inrichting niet verplicht is bij
   de zaak (of er is al een inrichting gekoppeld)

   -  rood indien er geen inrichting is gekoppeld terwijl dit wel
      verplicht is.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde
iconen, zie hiervoor `Sectie
OWB </docs/instellen_inrichten/configuratie/sectie_owb.md>`__.
