Lijst Onderdelen/Activiteiten bij een omgevingszaak
===================================================

De schermidentifier is: MDLC_geefOmgActiviteitenOverzicht.xml. Dit
scherm kan worden aangeroepen vanuit het zaakportaal Omgeving.

Error
-----

Het scherm geeft een foutmelding:

-  er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie
   `Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
   die niet valide is
-  de inlogger moet kijkrechten hebben op de activiteiten/onderdelen bij
   de omgevingszaak.

Triggers
--------

In het scherm: dubbel klikken op een regel opent het detailscherm van
een Onderdeel. Altijd enabled.

Welke triggers in *scherm linksonder*

-  insertknop:

   -  zichtbaar indien:

      -  inlogger insert-rechten heeft op de activiteiten/onderdelen bij
         de omgevingszaak
      -  enabled indien de bovenliggende omgevingszaak niet is
         geblokkeerd.

-  deleteknop:

   -  zichtbaar indien inlogger verwijderrechten heeft op de
      activiteiten/onderdelen bij de omgevingszaak
   -  enabled indien de bovenliggende omgevingszaak niet is geblokkeerd.
