# Lijst Recent Binnengekomen adviezen

Schermidentifier: MDLC_geefRecenteAdviezenLijst.xml (voor vaarwegzaken is dit: MDLC_geefRecenteAdviezenVaarwegLijst.xml).

Zie ook [Tegel Recent Binnengekomen adviezen](tegel_recent_binnengekomen_adviezen.md)

## Welke gegevens worden getoond

Afhankelijke van de aanroep (4e parameter zie tegelbeschrijving) kan er verschillend met compartimentsrestricties worden omgegaan.

De rijen uit de view vwfrmomgorkestrator_ing_adv (dan wel vwfrmomgorkestrator_ing_adv_vaarweg), dat zijn adviezen:

- waarbij de datering advies (dddateringadvies) groter is dan vandaag MINUS het aantal dagen in _Getal2_ van de instelling _Sectie: Adviezen_ en _Item: DagenTerug_RecentLijst_ Defaultwaarde = 365
- en het resultaat advies (advies positief) heeft nog de waarde: nnb (nog niet bekend)
- en met een lege vervaldatum
- en er moet een actieve behandelaar zijn bij de bovenliggende zaak (tegel _In behandeling bij_).

Boven op deze where clausules van de view is de volgende extra restrictie van kracht:

- Indien de de kolom _alleen gemeentes_ (zie beheertegel _Medewerkers_) bij de kaart van de inlogger gevuld is, dan worden alleen die adviezen getoond waarvan de id van de locatie-gemeente (bedoeld wordt de locatie waaraan de bovenliggende zaak is verbonden) voorkomt in die kolom _alleen gemeentes_.
- Compartimentsrestricties. Zie hiertoe de uitleg bij de tegel waarvan deze lijst wordt aangeroepen.

## Zichtbaarheid kolommen

- Voor de kolom **verantwoordelijke persoon** (interne behandelaar) geldt dat de kolom alleen zichtbaar is indien de instelling _Sectie: Adviezen en Item: Voorwiezichtbaar_ is aangevinkt.
- Voor de kolom **verantwoordelijk team** geldt dat de kolom alleen zichtbaar is indien de instelling _Sectie: Adviezen en Item: teamzichtbaar_ is aangevinkt.

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de recent binnengekomen adviezen:
  - zie de criteria hierboven.
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ van tbinitialisatie _Sectie: Paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd zaakportaal van bovenliggende zaak
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).
