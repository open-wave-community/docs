# Codering stallen

## Trigger

De tegel is een trigger voor tonen van het *Overzicht van stal* te coderen volgens RAV.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *Inrichtingenbeheer*
  * Kolom: *Registratie Vee*
  * Kopregel: *Codering stallen*
  * Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbmilcodestal)*

