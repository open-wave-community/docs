# Tegel Alle open uitgezette samenwerkingsruimtes

## Trigger

De tegel is een trigger voor het openen van de [Lijst Openstaande uitgezette samenwerkingsruimtes](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_alle_open_uitgezette_samenwerkingsruimtes/lijst_openstaande_uitgezette_samenwerkingsruimtes.md).

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

  - indien foutieve queryverwijzing
  - indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *Opening*
  - Kolom: *Deelzaken*
  - Kopregel:
  - Vast Opschrift: *Alle open uitgezette;samenwerkingsruimtes*
  - Dynamisch tegelopschrift: *getTileContent(open_swfruimtes)*
  - Actie: *getFlexList(SysStandardList,nil,nil,G,openstaande_swfruimtes)*

