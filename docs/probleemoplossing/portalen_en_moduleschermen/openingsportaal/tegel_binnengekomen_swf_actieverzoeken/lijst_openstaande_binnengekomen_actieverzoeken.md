# Lijst Openstaande binnengekomen actieverzoeken

Schermidentifier: MDLC_getBinnengekomenSWFActieverzoekenList.xml (sysstandard).

## Welke gegevens worden getoond

De rijen uit de view vwfrmswfopeninkomendeacties bestaan uit alle openstaande binnengekomen actieverzoeken (dluitgaand is F(alse)).

Zie: [Samenwerkingsfunctionaliteit](/docs/instellen_inrichten/samenwerkingsfunctionaliteit.md).

## Rechten

De lijst kan alleen opgevraagd worden door een medewerker die lid is van een rechtengroep met het omgevingsrecht _Samenwerkingsruimte - Zichtbaar_ (tbomgrechten.dlcomgswfvsb).

## Problemen

- De lijst geeft een foutmelding:
  - Er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ van tbinitialisatie _Sectie: paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel verwijst altijd door naar de achterliggende zaak
- zoekeditbox rechtsonder: altijd aanwezig
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt)
- de knop _Detailgegevens_ linksonder. Deze knop toont de detailgegevens van de SWF-ruimte van de geselecteerde regel
- de knop _dowload als excel_ linksonder. Met deze knop is het mogelijk om de getoonde lijst te exporteren naar Excel.
