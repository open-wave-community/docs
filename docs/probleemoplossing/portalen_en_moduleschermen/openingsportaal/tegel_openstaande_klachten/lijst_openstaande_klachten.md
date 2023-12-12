# Lijst Openstaande Klachten

Schermidentifier: [https://api.open-wave.nl/RemMethods/getRemMethod/509](https://api.open-wave.nl/RemMethods/getRemMethod/509.md).

Zie ook [Tegel Openstaande Klachten](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_openstaande_klachten.md)

## Welke gegevens worden getoond

De rijen uit de view vwfrmklachten, dat zijn klachten:

- waarbij de afrond datum (ddafgerond) leeg is of groter dan vandaag.

Boven op deze where clausules van de view is de volgende extra restrictie van kracht:

- Indien de de kolom _alleen gemeentes_ (zie beheertegel _Medewerkers_) bij de kaart van de inlogger gevuld is, dan worden alleen die klachten getoond waarvan de id van de locatie-gemeente (bedoeld wordt de locatie waaraan de bovenliggende zaak is verbonden) voorkomt in die kolom _alleen gemeentes_.
- Compartimentsrestricties. Zie hiertoe de uitleg bij de tegel waarvan deze lijst wordt aangeroepen.

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de openstaande klachten:
  - zie de criteria hierboven
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ van tbinitialisatie _Sectie: Paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd zaakportaal van bovenliggende zaak
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).
