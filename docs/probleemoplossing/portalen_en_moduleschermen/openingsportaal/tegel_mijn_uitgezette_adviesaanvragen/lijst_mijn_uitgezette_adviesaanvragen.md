# Lijst Mijn uitgezette Adviesaanvragen

## Welke gegevens worden getoond

De rijen komen indien actionaanroep op tegel is getFlexList(OpenAdviezen,nil,nil,**1**,nil) en de vierde parameter = 1,2 of 4 dan uit **vwfrmomgorkestrator_adv**, indien action-aanroep op tegel is getFlexList(OpenAdviezen,nil,nil,**1**,nil,nil,nil,nil,1) en de vierde parameter = 1,2 of 4 dan uit **vwfrmomgorkestrator_adv_vaarweg**.

Dat zijn adviezen:

- met lege **adviesdatum (ddadviesdatum**)
- en met een gevulde rappeldatum die jonger is dan een jaar geleden
- en met een lege vervaldatum
- en met een lege blokkeerdatum (van bovenliggende zaak)
- en er moet een actieve behandelaar zijn bij bovenliggende zaak (tegel _In behandeling bij_).

De rijen komen indien action-aanroep op tegel is getFlexList(OpenAdviezen,nil,nil,**11**,nil) en de vierde parameter = 11, 12 of 14 dan
uit view **vwfrmomgorkestrator_datadv**, indien action-aanroep op tegel is getFlexList(OpenAdviezen,nil,nil,**11**,nil,nil,nil,nil,1) en de vierde parameter = 11, 12 of 14 dan uit **vwfrmomgorkestrator_datadv_vaarweg**.

Dat zijn adviezen:

- met lege **dateringadvies (dddateringadvies**)
- en met een gevulde rappeldatum die jonger is dan een jaar geleden
- en met een lege vervaldatum
- en met een lege blokkeerdatum (van bovenliggende zaak)
- en er moet een actieve behandelaar zijn bij bovenliggende zaak (tegel _In behandeling bij_).

Boven op deze where clausules van bovenstaande views is de volgende extra restrictie van kracht:

- indien de vierde parameter = 1 of 11 dan alleen die uitgezette adviezen worden getoond waarvoor de inlogger dezelfde is als de interne behandelaar (dvadviesbehandelaar)
- indien de vierde parameter = 2 of 12 dan alleen die uitgezette adviezen worden getoond waarvoor de inlogger dezelfde is als de actieve dossierbehandelaar van de bovenliggende zaak
- indien de vierde parameter = 4 of 14 dan alleen die uitgezette adviezen worden getoond waarvoor de inlogger lid is van het behandelende team.

## Zichtbaarheid kolommen

- Voor de kolom **verantwoordelijke persoon** (interne behandelaar) geldt dat de kolom alleen zichtbaar is indien de instelling _Sectie: Adviezen en Item: Voorwiezichtbaar_ is aangevinkt.
- Voor de kolom **verantwoordelijk team** geldt dat de kolom alleen zichtbaar is indien de instelling _Sectie: Adviezen en Item: teamzichtbaar_ is aangevinkt.

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de mijn uitgezette adviezen:
  - zie de criteria hierboven.
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ van tbinitialisatie _Sectie: Paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd zaakportaal van bovenliggende zaak
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).

## Betekenis kleurenballetjes

- Eerste kolom (dvadviesgevaar):
  - wit indien de rappeldatum > overmorgen
  - rood indien rappeldatum < vandaag
  - oranje indien vandaag < = rappeldatum < = overmorgen.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde iconen, zie hiervoor [Sectie OWB](/docs/instellen_inrichten/configuratie/sectie_owb.md).
