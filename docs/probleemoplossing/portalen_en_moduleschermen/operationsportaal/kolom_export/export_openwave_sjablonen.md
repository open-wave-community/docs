# Export OpenWave sjablonen

Zie ook [Import/Export rapport, sjabloon etc.](/probleemoplossing/programmablokken/import_export_xlm.md).

## Trigger

De tegel is een trigger voor de wizard die het exporteren van rapportages, sjablonen, processen, queries e.d. regelt.

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *Operations*
  - Kolom: *Export*
  - Kopregel: *Export xml OpenWave;sjablonen,schermen;queries, processen…*
  - Actie: *startWizard(exporttoxml,,,,)

