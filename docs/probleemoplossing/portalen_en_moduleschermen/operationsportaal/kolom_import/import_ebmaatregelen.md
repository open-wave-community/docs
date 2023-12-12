# Import Energie Besparende Maatregelen (EBM)

Zie ook [Inlezen EB Maatregelen (EBM)](/docs/probleemoplossing/programmablokken/inlezen_energiebesparende_maatregelen.md).

## Trigger

De tegel is een trigger voor de wizard die het inlezen van **Energie besparende maatregelen** regelt.

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *Operations*
  * Kolom: *Import*
  * Kopregel: *Inlezen EB Maatregelen*
  * Actie: *startWizard(uploadmultiplefiles,-1,,no_uploadfile;inlezenebmaatregelen)*

