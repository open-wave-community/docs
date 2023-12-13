# Lijst bezwaar/beroep bij een zaak

De schermidentifier is: MDLC_getBezwaarBeroepList.xml.

Dit scherm kan worden aangeroepen vanuit het zaakportaal van Omgeving, Handhavingen, Bouw/sloop, Milieu/gebruik en APV/Overig en Horeca.

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie [Scherm(kolom)definitie](../../../instellen_inrichten/schermdefinitie/README.md)) die niet valide is
- de inlogger geen kijkrechten heeft op de adviezen bij betreffende hoofdzaak.

## Muteerrechten

Een kolom in de bezwaar/beroeplijst kan worden gemuteerd indien:

- de inlogger lid is van een rechtengroep die wijzigrechten heeft op de bezwaar/beroep van de betrokken module
- en de bovenliggende zaak niet is geblokkeerd
- en in de schermkolomdefinitie (beheer) is de eigenschap _lijst automatisch in editmode_ aangevinkt
- en de kolom heeft de tag `<edit>` op true staan in de schermkolomdefinitie
- en - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de bovenliggende zaak bevatten en de gemeente waar die zaak speelt, waarbij de eigenschap inclusief bezwaar/beroep is aangevinkt
- en - indien de inlogger GEEN lid is van een compartiment, dan:
  - mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt in geen enkel compartiment voorkomen
  - OF, als dat wel het geval is, dan moet de eigenschap _inclusief bezwaar/beroep_ NIET aangevinkt staan
- en de editschuif aan staat.

## Triggers

- dubbel klikken op een regel opent het detailscherm van een bezwaar/beroep. Altijd enabled.

### Triggers linksonder

- insertknop:
  - zichtbaar indien:
    - inlogger insert-rechten heeft op bezwaar/beroep bij betreffende hoofdzaak
    - en de lijst wordt aangeroepen vanuit de tegel _Openstaande bezwaar/beroepzaken_
  - enabled indien de bovenliggende zaak niet is geblokkeerd.
- deleteknop:
  - zichtbaar indien inlogger verwijderrechten heeft op bezwaar/beroep bij betreffende hoofdzaak
  - enabled indien de bovenliggende zaak niet is geblokkeerd.
