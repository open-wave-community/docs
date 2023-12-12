# Import BAG-Mutaties

Zie ook [Inlezen BAG Extract en/of BAG-mutaties](/probleemoplossing/programmablokken/inlezen_bag-extract_en_bag-mutaties.md).

## Trigger

De tegel is een trigger voor de wizard die het importeren van BAG-mutaties van één gemeente regelt.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Operations_
- Kolom: _Import_
- Kopregel: _Mutaties BAG (zip);per gemeente_
- Actie: \*startWizard(uploadmultiplefiles,-1,,no_uploadfile;importzipmutatiesbag)
