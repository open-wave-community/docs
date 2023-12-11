# Import  BAG-Mutaties

Zie ook [Inlezen BAG Extract en/of BAG-mutaties](/docs/probleemoplossing/programmablokken/inlezen_bag-extract_en_bag-mutaties.md).

## Trigger

De tegel is een trigger voor de wizard die het importeren van BAG-mutaties van één gemeente regelt.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Operations*
* Kolom: *Import*
* Kopregel: *Mutaties BAG (zip);per gemeente*
* Actie: *startWizard(uploadmultiplefiles,-1,,no_uploadfile;importzipmutatiesbag)
