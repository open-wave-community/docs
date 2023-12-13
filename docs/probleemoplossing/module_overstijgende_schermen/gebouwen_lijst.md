# Gebouwen Lijst

De schermidentifier is: MDLC_getMilVergGebouwList.xml.

Dit scherm kan worden aangeroepen vanuit:

* het zaakportaal milieu/gebruik (tegel *Gebouwen*). De lijst toont de gebouwen van de milieu/gebruikszaak
* het zaakportaal bouw/sloop (tegel *Gebouwen*). De lijst toont de gebouwen van de bouwsloopzaak.

De bron van de lijst is de tabel tbgebouwen.

### Probleem

Het scherm geeft een foutmelding indien er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](../../instellen_inrichten/schermdefinitie/README.md)) die niet valide is.

## Rechten

Voor het tonen van de lijst vanuit het zaakportaal MilieuGebruikDetail dient de inlogger lid te zijn van een rechtengroep die kijkrechten heeft op preparaties/installaties voor de Milieu/Gebruikszaken.

Voor het tonen van de lijst vanuit het zaakportaal BouwSloopDetail dient de inlogger lid te zijn van een rechtengroep die kijkrechten heeft op preparaties/installaties voor de Bouwsloopzaken.

### Triggers

* knop gebouw **Toevoegen**:
  * de knop is zichtbaar indien de inlogger lid is van een rechtengroep die insert rechten heeft op preparaties/installaties (voor de betreffende module)
  * de knop is enabled indien de bovenliggende zaak niet is geblokkeerd.
* knop gebouw **Verwijderen**:
  * de knop is zichtbaar indien de inlogger lid is van een rechtengroep die verwijderrechten heeft op preparaties/installaties (voor de betreffende module)
  * de knop is enabled indien de bovenliggende zaak niet is geblokkeerd.
