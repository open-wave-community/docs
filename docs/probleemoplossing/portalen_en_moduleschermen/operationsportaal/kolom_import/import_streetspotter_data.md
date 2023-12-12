# Import Streetspotter data

Zie ook [Inlezen Streetspotter data](/docs/probleemoplossing/programmablokken/inlezen_streetspotter_data.md).

## Trigger

De tegel is een trigger voor de wizard die het inlezen van Streetspotter data regelt.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Operations*
- Kolom: *Import*
- Kopregel: *Inlezen Streetspotter data*
- Actie: *startWizard(uploadmultiplefiles,-1,,no_uploadfile;importstreetspotterdata)*
