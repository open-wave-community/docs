# Tegel Samenwerkingsruimtes

## Trigger

De tegel is een trigger van een lijst Samenwerkingsruimtes (zie: [Samenwerkingsfunctionaliteit](/instellen_inrichten/samenwerkingsfunctionaliteit.md)).

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  - indien foutieve queryverwijzing (codering *omgeving_samenwerkingruimte*)
  - indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *omgevingdetail*
  - Kolom: *BehandelingProces*
  - Kopregel: *Samenwerkingsruimtes*
  - Dynamisch tegelopschrift: *getTileContent(omgeving_samenwerkingruimte,{id})*
  - Actie: *getFlexList(tbswfruimte,tbomgvergunning,{id},nil,W)*

