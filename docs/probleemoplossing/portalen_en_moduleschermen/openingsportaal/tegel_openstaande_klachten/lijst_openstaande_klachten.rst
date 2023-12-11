Lijst Openstaande Klachten
==========================

Schermidentifier: https://api.open-wave.nl/RemMethods/getRemMethod/509.

Zie ook `Tegel Openstaande
Klachten </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_openstaande_klachten.md>`__

Welke gegevens worden getoond
-----------------------------

De rijen uit de view vwfrmklachten, dat zijn klachten:

-  waarbij de afrond datum (ddafgerond) leeg is of groter dan vandaag.

Boven op deze where clausules van de view is de volgende extra
restrictie van kracht:

-  Indien de de kolom *alleen gemeentes* (zie beheertegel *Medewerkers*)
   bij de kaart van de inlogger gevuld is, dan worden alleen die
   klachten getoond waarvan de id van de locatie-gemeente (bedoeld wordt
   de locatie waaraan de bovenliggende zaak is verbonden) voorkomt in
   die kolom *alleen gemeentes*.
-  Compartimentsrestricties. Zie hiertoe de uitleg bij de tegel waarvan
   deze lijst wordt aangeroepen.

Problemen
---------

-  De lijst is leeg of geeft maar een gedeelte van de openstaande
   klachten:

   -  zie de criteria hierboven

-  De lijst geeft een foutmelding:

   -  er is mogelijk een zelf gedefinieerde schermindeling gebruikt
      (Schermkolomdefinitie onder Beheer) die niet valide is.

Triggers
--------

Welke zijn van toepassing op deze lijst?

-  pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de
   instelling *Getal1* van tbinitialisatie *Sectie: Paging* en *Item:
   pagesize* (defaultwaarde = 100)
-  klikken op regel opent altijd zaakportaal van bovenliggende zaak
-  versie-informatie rechtsonder (hierop klikken en screensource =
   tbscreencolumns geeft aan of er een afwijkende schermkolommen
   definitie gebruikt wordt).
