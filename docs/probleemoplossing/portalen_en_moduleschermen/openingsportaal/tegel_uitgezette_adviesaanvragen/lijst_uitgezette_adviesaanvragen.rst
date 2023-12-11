Lijst Uitgezette Adviesaanvragen
================================

Schermidentifier: MDLC_geefOpenstaandeAdviezenLijst.xml (voor
Vaarwegzaken is dit: MDLC_geefOpenstaandeAdviezenVaarwegLijst.xml).

Welke gegevens worden getoond
-----------------------------

Indien actionaanroep op tegel is
getFlexList(OpenAdviezen,nil,nil,\ **0**,nil) dan de rijen uit de view
**vwfrmomgorkestrator_adv**, indien actionaanroep op tegel is
getFlexList(OpenAdviezen,nil,nil,\ **0**,nil,nil,nil,nil,1) dan de rijen
uit de view **vwfrmomgorkestrator_adv_vaarweg**.

Dat zijn adviezen:

-  met lege **adviesdatum (ddadviesdatum**)
-  en met een gevulde rappeldatum die jonger is dan *Getal2* van de
   instelling *Sectie: Adviezen en Item: DagenTerug_OpenstaandLijst*
   dagen geleden (default 365)
-  en met een lege vervaldatum
-  en met een lege blokkeerdatum (van bovenliggende zaak)
-  en er moet een actieve behandelaar zijn bij bovenliggende zaak (tegel
   *In behandeling bij*).

Indien action-aanroep op tegel is
getFlexList(OpenAdviezen,nil,nil,\ **10**,nil) dan de rijen uit de view
**vwfrmomgorkestrator_datadv**, indien action-aanroep op tegel is
getFlexList(OpenAdviezen,nil,nil,\ **10**,nil,nil,nil,nil,1) dan de
rijen uit de view **vwfrmomgorkestrator_datadv_vaarweg**.

Dat zijn adviezen:

-  met lege **dateringadvies (dddateringadvies**)
-  en met een gevulde rappeldatum die jonger is dan *Getal2* van de
   instelling *Sectie: Adviezen en Item: DagenTerug_OpenstaandLijst*
   dagen geleden (default 365)
-  en met een lege vervaldatum
-  en met een lege blokkeerdatum (van bovenliggende zaak)
-  en er moet een actieve behandelaar zijn bij bovenliggende zaak
   (tegel: *In behandeling bij*).

Boven op deze where clausules van bovenstaande views is de volgende
extra restrictie van kracht:

-  Indien de de kolom *alleen gemeentes* (zie beheertegel *Medewerkers*)
   bij de kaart van de inlogger gevuld is, dan worden alleen die
   adviezen getoond waarvan de id van de locatie-gemeente (bedoeld wordt
   de locatie waaraan de bovenliggende zaak is verbonden) voorkomt in
   die kolom *alleen gemeentes*.
-  Compartimentsrestricties. Indien de vierde parameter de waarde 3 of
   13 heeft. Zie hiertoe de uitleg bij de tegel waarvan deze lijst wordt
   aangeroepen.

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

-  De lijst is leeg of geeft maar een gedeelte van de uitgezette
   adviesaanvragen:

   -  zie de criteria hierboven.

-  De lijst geeft een foutmelding:

   -  er is mogelijk een zelf gedefinieerde schermindeling gebruikt
      (Schermkolomdefinitie onder Beheer) die niet valide is.

Triggers
--------

Welke zijn van toepassing op deze lijst?

-  pagingknoppen rechts boven: aanwezig indien aantal rijen groter dan
   de instelling *Getal1* van tbinitialisatie *Sectie: Paging* en *Item:
   pagesize* (defaultwaarde = 100)
-  klikken op regel opent altijd zaakportaal van bovenliggende zaak
-  versie-informatie rechtsonder (hierop klikken en screensource =
   tbscreencolumns geeft aan of er een afwijkende schermkolommen
   definitie gebruikt wordt).

Betekenis kleurenballetjes
--------------------------

-  Eerste kolom (dvadviesgevaar):

   -  wit indien de rappeldatum > overmorgen
   -  rood indien rappeldatum < vandaag
   -  oranje indien vandaag < = rappeldatum < = overmorgen.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde
iconen, zie hiervoor `Sectie
OWB </docs/instellen_inrichten/configuratie/sectie_owb.md>`__.
