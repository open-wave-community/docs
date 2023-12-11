Lijst Mijn recent binnengekomen adviezen
========================================

Schermidentifier: MDLC_geefRecenteAdviezenLijst.xml (voor vaarwegzaken
is dit: MDLC_geefRecenteAdviezenVaarwegLijst.xml).

Zie ook `Tegel Mijn recent binnengekomen
adviezen </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_recent_binnengekomen_adviezen.md>`__

Welke gegevens worden getoond
-----------------------------

De rijen uit de view vwfrmomgorkestrator_ing_adv (dan wel
vwfrmomgorkestrator_ing_adv_vaarweg), dat zijn adviezen:

-  waarbij de datering advies (dddateringadvies) groter is dan vandaag
   MINUS het aantal dagen in *Getal2* van de instelling *Sectie =
   Adviezen* en *Item = DagenTerug_RecentLijst* Defaultwaarde = 365
-  en het resultaat advies (advies positief) heeft nog de waarde: nnb
   (nog niet bekend)
-  en met een lege vervaldatum
-  en er moet een actieve behandelaar zijn bij de bovenliggende zaak
   (tegel *In behandeling bij*).

Boven op deze where clausules van de view is de volgende extra
restrictie van kracht, die aangestuurd kunnen worden met de vierde
parameter op de action van de tegelaanroep:

De vierde parameter kan de volgende waarden hebben:

-  

   1. De waarde 1 betekent dat de recent binnengekomen adviezen getoond
      worden waarvoor de interne adviesbehandelaar gelijk is aan de
      inlogger

-  

   2. De waarde 2 betekent dat de binnengekomen adviezen getoond worden
      waarvoor geldt dat de dossierbehandelaar van de bovenliggende zaak
      gelijk is aan de inlogger

-  

   4. De waarde 4 betekent dat de binnengekomen adviezen getoond worden
      waarvoor geldt dat zij toegekend zijn aan een team waartoe de
      inlogger behoort.

Zichtbaarheid kolommen
----------------------

-  Voor de kolom **verantwoordelijke persoon** (interne behandelaar)
   geldt dat de kolom alleen zichtbaar is indien de instelling *Sectie:
   Adviezen en Item: Voorwiezichtbaar* is aangevinkt.
-  Voor de kolom **verantwoordelijk team** geldt dat de kolom alleen
   zichtbaar is indien de instelling *Sectie: Adviezen en Item:
   teamzichtbaar* is aangevinkt.

Problemen
---------

-  De lijst is leeg of geeft maar een gedeelte van mijn recent
   binnengekomen adviezen:

   -  zie de criteria hierboven.

-  De lijst geeft een foutmelding:

   -  er is mogelijk een zelf gedefinieerde schermindeling gebruikt
      (Schermkolomdefinitie onder Beheer) die niet valide is.

Triggers
--------

Welke zijn van toepassing op deze lijst?

-  pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de
   instelling *Getal1* van tbinitialisatie *Sectie: Paging*\ en *Item:
   pagesize* (defaultwaarde = 100)
-  klikken op regel opent altijd zaakportaal van bovenliggende zaak
-  versie-informatie rechtsonder (hierop klikken en screensource =
   tbscreencolumns geeft aan of er een afwijkende schermkolommen
   definitie gebruikt wordt).
