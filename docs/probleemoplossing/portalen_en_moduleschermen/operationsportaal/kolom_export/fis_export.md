# Fis Export

Zie ook [Financiële export (Fis export)](/probleemoplossing/programmablokken/financiele_export.md).

## Trigger

De tegel is een trigger voor het starten van lijstscherm met de *Te exporteren legesregels*. Via deze lijst kan het verzamelen van de te exporteren legesgegevens geregeld worden ten behoeve van de financiële export.

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *Operations*
  - Kolom: *Export*
  - Vast opschrift: *Fis export*
  - Actie: *getFlexList(SysStandardList,nil,nil,,operations_vwfrmlegesexport)*

