Installaties Lijst
==================

De schermidentifier is: MDLC_getOmgInstallatiesList.xml.

Dit scherm kan worden aangeroepen vanuit:

-  het zaakportaal omgevingsdetail (tegel *Installaties*). De lijst
   toont de installaties die toegekend zijn aan de Omgevingszaak
-  het zaakportaal milieu/gebruik (tegel *Installaties*). De lijst toont
   de installaties die toegekend zijn aan de Milieu/Gebruikszaak
-  het zaakportaal bouw/sloop (tegel *Installaties*). De lijst toont de
   installaties die toegekend zijn aan de Bouwsloopzaak.

De bron van de lijst is de tabel tbomgbwinstallaties.

Probleem
--------

Het scherm geeft een foutmelding indien er is mogelijk een zelf
gedefinieerde schermindeling gebruikt (zie
`Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
die niet valide is.

Rechten
-------

Voor het tonen van de lijst vanuit het zaakportaal OmgevingsDetail dient
de inlogger lid te zijn van een rechtengroep die kijkrechten heeft op
preparaties/installaties voor de Omgevingszaken.

Voor het tonen van de lijst vanuit het zaakportaal MilieuGebruikDetail
dient de inlogger lid te zijn van een rechtengroep die kijkrechten heeft
op preparaties/installaties voor de Milieu/Gebruikszaken. Voor het tonen
van de lijst vanuit het zaakportaal BouwSloopDetail dient de inlogger
lid te zijn van een rechtengroep die kijkrechten heeft op
preparaties/installaties voor de Bouwsloopzaken.

Triggers
--------

-  knop installaties **Toevoegen/wegnemen**:

   -  de knop is zichtbaar indien de inlogger lid is van een
      rechtengroep die insert rechten heeft op preparaties/installaties
      (voor de betreffende module)
   -  de knop is enabled indien de bovenliggende zaak niet is
      geblokkeerd.

-  knop installaties **Verwijderen**:

   -  de knop is zichtbaar indien de inlogger lid is van een
      rechtengroep die verwijderrechten heeft op
      preparaties/installaties (voor de betreffende module)
   -  de knop is enabled indien de bovenliggende zaak niet is
      geblokkeerd.
