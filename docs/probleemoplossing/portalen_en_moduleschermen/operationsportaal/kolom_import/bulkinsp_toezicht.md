s# Aanmaken inspectie/toezicht in bulk

Zie ook [Bulk aanmaken van inspecties/toezichtzaken](../programmablokken/bulkinspzaken.md).

## Trigger

De tegel is een trigger voor de wizard die het in bulk aanmaken van inspecties dan wel toezichtzaken regelt.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichtenn_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Operations*
- Kolom: *Import*
- Kopregel: *Aanmaken inspectie/toezicht; in bulk*
- Actie: *getFlexList(SysStandardList,nil,nil,,operations_vwfrmbulkinsptoezicht)*
