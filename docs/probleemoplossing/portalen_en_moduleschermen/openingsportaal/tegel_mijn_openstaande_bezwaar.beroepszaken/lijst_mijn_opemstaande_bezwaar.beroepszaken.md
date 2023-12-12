# Lijst Mijn Openstaande Bezwaar/Beroepszaken

Schermidentifier: MDLC_getOpenBezwaarBeroepZakenList.xml (voor vaarwegzaken is dit: MDLC_getOpenBezwaarBeroepZakenVaarwegList.xml).

Zie ook [Tegel Mijn Openstaande Bezwaar/beroepszaken](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_openstaande_bezwaar.beroepszaken.md)

## Welke gegevens worden getoond

De rijen uit de view vwfrmopenbezwaarberoep (dan wel vwfrmopenbezwaarberoep_vaarweg), dat zijn bezwaar/beroepszaken:

- waarbij de uitspraakdatum (dduitspraak) leeg is of groter dan vandaag.

Boven op deze where clausules van de view is de volgende extra restrictie van kracht:

- alleen die lopende bezwaar/beroepszaken worden getoond waarvoor de inlogger dezelfde is als de juridisch verantwoordelijke (dvcodejurist).

## Problemen

- De lijst is leeg of geeft maar een gedeelte van mijn openstaande bezwaar/beroepszaken:
  - zie de criteria hierboven.
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ van tbinitialisatie _Sectie: paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd zaakportaal van bovenliggende zaak
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).
