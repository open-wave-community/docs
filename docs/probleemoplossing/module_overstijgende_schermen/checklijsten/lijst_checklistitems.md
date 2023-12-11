# Lijst checklijstitems

Het scherm is gebaseerd op tabel met checklijstitems per vergunning naar termijnbewakingsproces of inspectietraject.

Dit scherm kan worden aangeroepen - via doorkieslijst - zie pagina [Checklijsten](/docs/probleemoplossing/module_overstijgende_schermen/checklijsten.md), maar ook:

- vanuit detailscherm van een processtap, indien een checklijst aan een specifieke stap is gekoppeld (geen doorkieslijst)
- vanuit de knop linksonder op het detailscherm van een inspectietraject indien de checklijst gekoppeld is aan een inspectietraject.

## Probleem

Het scherm geeft een een foutmelding:

- er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
  - de inlogger moet kijkrechten hebben op de processtappen bij betreffende hoofdzaak.

## Muteren (inclusief nieuw aanmaken en verwijderen) status

De kolom **status** van dit checklistscherm is muteerbaar indien:

- de inlogger wijzigrechten heeft op de processtappen bij betreffende hoofdzaak (bijvoorbeeld wijzigrechten op proces/checklijst bij omgeving)
- en die bovenliggende hoofdzaak niet is geblokkeerd
- en - indien de inlogger lid is van een compartiment - dan moet de bovenliggende zaaktype/gemeente in dat compartiment gedefinieerd zijn. Indien de inlogger geen lid is van een compartiment, dan mag de combinatie bovenliggende zaaktype/gemeente in geen enkel compartiment gedefinieerd zijn.

## Triggers Linksonder

- **Accordeer alle items**. Zichtbaar en enabled indien de inlogger muteerrechten heeft.
- **Export naar Excel**. Zichtbaar en enabled indien zo aangegeven bij de schermkolomdefinitie.

## Bijzonderheden

Vanwege de beperkte ruimte in het detailscherm van de processtap waarin deze lijst getoond kan worden, kan indien gewenst het aantal kolommen dat zichtbaar is beperkt worden. Met het aanvinken van de volgende instelling zullen de kolommen _Groep_ en _Volgnummer_ niet meer getoond worden in de lijst: _Sectie: Programma_ en _Item: BeperkteKolommenChecklist_.
