Lijst bewerk ja/nee stappen
===========================

De schermidentifier is MDLC_geefAfvinkstappenOverzicht.xml.

Dit scherm kan worden aangeroepen vanuit Lijst *Processtappen* (de knop
is zichtbaar indien de instelling *Sectie: Processen* en *Item:
AfvinkstappenGeenEigenScherm* NIET is aangevinkt).

Probleem
--------

Het scherm geeft een foutmelding:

-  er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie
   `Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
   die niet valide is
-  de inlogger moet kijkrechten hebben op de processtappen bij
   betreffende hoofdzaak.

Muteren
~~~~~~~

Een kolom kan gemuteerd worden indien:

-  de inlogger wijzigrechten heeft op de processtappen bij betreffende
   hoofdzaak (bijvoorbeeld wijzigrechten op proces/checklijst bij
   omgeving)
-  en die bovenliggende hoofdzaak niet is geblokkeerd
-  en in de schermkolomdefinitie (beheer) is de eigenschap
   *lijst_automatisch in editmode* aangevinkt
-  en de kolom heeft de tag ``<edit>`` op true staan in de
   schermkolomdefinitie
-  en - indien de inlogger lid is van een compartiment - dan moet het
   betreffende compartiment het zaaktype van de bovenliggende zaak
   bevatten en de gemeente waar die zaak speelt
-  en - indien de inlogger GEEN lid is van een compartiment, dan mag de
   combinatie van het zaaktype van de bovenliggende zaak en de gemeente
   waar die zaak speelt in geen enkel compartiment voorkomen
-  en de editschuif aan staat.

Triggers
~~~~~~~~

-  Dubbel klikken op een regel (buiten het aanvinkvakje) opent het
   detailscherm van een procesafvinkstap. Altijd enabled.
