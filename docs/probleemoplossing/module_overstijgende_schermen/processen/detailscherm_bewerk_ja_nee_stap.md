# Detailscherm bewerk ja/nee stap

De schermidentifier is: MDDC_geefAfvinkstapDetail.xml.

Dit scherm kan worden aangeroepen vanuit Lijst Bewerk Ja/Nee stappen.

## Probleem

Het scherm geeft een foutmelding:

* er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
* de inlogger moet kijkrechten hebben op de processtappen bij betreffende hoofdzaak (bijvoorbeeld zichtbaar-rechten op proces/checklijst bij omgeving).

## Muteren

De kolommen kunnen gemuteerd worden indien:

* de inlogger wijzigrechten heeft op de adviezen bij betreffende hoofdzaak
* EN die bovenliggende hoofdzaak niet is geblokkeerd
* EN de editschuif aan staat
* EN - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de hoofdzaak bevatten en de gemeente waar de omgevingszaak speelt
* EN - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar de hoofdzaak speelt in geen enkel compartiment voorkomen.
