# CBS Export

Zie ook [CBS export](/docs/probleemoplossing/programmablokken/cbs_export.md).

## Trigger

De tegel is een trigger voor het starten van lijstscherm met de *Te exporteren CBS-gegevens*. Via deze lijst kan het verzamelen van de te exporteren CBS-gegevens geregeld worden ten behoeve van de export naar CBS.

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  -  Portaal: *Operations*
  -  Kolom: *Export*
  -  Vast opschrift: *CBS export*
  -  Actie: *getFlexList(SysStandardList,nil,nil,,operations_vwfrmcbsexport)*

