# Lijst Openstaande uitgezette samenwerkingsruimtes

Schermidentifier: MDLC_getSWFRuimteOverzichtList.xml (sysstandard).

## Welke gegevens worden getoond

De rijen uit de view vwfrmswfopenuitgezetteruimtes dat zijn de openstaande in SWF bestaande uitgezette SWF ruimtes (dluitgaand is T(rue)).
Zie: [Samenwerkingsfunctionaliteit](/docs/instellen_inrichten/samenwerkingsfunctionaliteit.md).

## Rechten

De lijst kan alleen opgevraagd worden door een medewerker die lid is van een rechtengroep met het omgevingsrecht *Samenwerkingsruimte - Zichtbaar* (tbomgrechten.dlcomgswfvsb).

## Problemen

  * De lijst geeft een foutmelding:
    * Er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

  * pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling *Getal1* van tbinitialisatie *Sectie: paging* en *Item: pagesize* (defaultwaarde = 100)
  * klikken op regel verwijst altijd door naar de achterliggende zaak
  * zoekeditbox rechtsonder: altijd aanwezig
  * versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt)
  * de knop *Detailgegevens* linksonder. Deze knop toont de detailgegevens van de SWF ruimte van de geselecteerde regel
  * de knop *dowload als excel* linksonder. Met deze knop is het mogelijk om de getoonde lijst te exporteren naar Excel.

