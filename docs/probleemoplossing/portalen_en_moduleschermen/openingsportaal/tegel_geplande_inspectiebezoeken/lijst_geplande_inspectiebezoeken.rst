Lijst Geplande Inspectiebezoeken
================================

Schermidentifier: MDLC_geefOpenInspectieBezoekenLijst.xml

Welke gegevens worden getoond
-----------------------------

De rijen uit de view vwfrmomgorkestrator_insp, dat zijn
inspectiebezoeken:

-  waarbij de geplande bezoekdatum (ddgepland) jonger is dan *Getal2*
   van de instelling *Sectie: Inspecties en Item:
   DagenTerug_OpenBezoekenLijst* dagen geleden (default 365)
-  en de bovenliggende inspectietraject afgehandeld datum (ddcontrole)
   leeg is of groter dan vandaag
-  en de afgehandeld datum van het bezoek nog leeg is
-  en de bovenliggende zaak/inrichting NIET is geblokkeerd. Indien
   echter de instelling *Sectie: InspectieMilieu en Item:
   Nietblokkerenmethoofdzaak* aangevinkt is, dan mag de bovenliggende
   zaak WEL geblokkeerd zijn.

Boven op deze where clausules van de view is de volgende extra
restrictie van kracht:

-  indien de de kolom *alleen gemeentes* (zie beheertegel *Medewerkers*)
   bij de kaart van de inlogger gevuld is, dan worden alleen die
   inspectiebezoeken getoond waarvan de id van de locatie-gemeente
   (bedoeld wordt de locatie waaraan de bovenliggende zaak of inrichting
   is verbonden) voorkomt in die kolom *alleen gemeentes*
-  indien de inlogger lid is van een
   `compartiment </docs/instellen_inrichten/compartimenten.md>`__ ziet
   hij/zij alleen bezoeken van zaken die gelokaliseerd zijn in de aan
   het compartiment toegekende gemeentes.

Problemen
---------

-  De lijst is leeg of geeft maar een gedeelte van de geplande
   inspectiebezoeken:

   -  zie de criteria hierboven.

-  De lijst geeft een foutmelding:

   -  Er is mogelijk een zelf gedefinieerde schermindeling gebruikt
      (Schermkolomdefinitie onder Beheer) die niet valide is.

Triggers
--------

Welke zijn van toepassing op deze lijst?

-  pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de
   instelling *Getal1* van tbinitialisatie *Sectie: paging* en *Item:
   pagesize* (defaultwaarde = 100)
-  klikken op regel opent altijd zaakportaal van bovenliggende zaak of
   inrichting
-  versie-informatie rechtsonder (hierop klikken en screensource =
   tbscreencolumns geeft aan of er een afwijkende schermkolommen
   definitie gebruikt wordt).

Betekenis kleurenballetjes
--------------------------

-  Eerste kolom (dvbezoekgevaar):

   -  rood indien de geplande bezoekdatum < = vandaag
   -  wit in alle andere gevallen.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde
iconen, zie hiervoor `Sectie
OWB </docs/instellen_inrichten/configuratie/sectie_owb.md>`__.
