# PAS-coderingen

## Trigger

De tegel is een trigger voor de view van mogelijke *PAS-coderingen* (Programma Aanpak Stikstof). bij een inrichting.

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *Inrichtingenbeheer*
  - Kolom: *Registratie Vee*
  - Vast opschrift: *Pas-coderingen*
  - Actie: *getFlexList(SysStandardList,,,,beheer_tbmilcodepas)*

