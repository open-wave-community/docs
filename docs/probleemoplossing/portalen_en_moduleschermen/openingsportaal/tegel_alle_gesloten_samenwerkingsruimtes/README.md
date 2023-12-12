# Tegel Alle gesloten samenwerkingsruimtes

## Trigger

De tegel is een trigger voor het openen van de [Lijst Gesloten samenwerkingsruimtes](/docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_alle_gesloten_samenwerkingsruimtes/lijst_gesloten_samenwerkingsruimtes.md).

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *Opening*
  - Kolom: *Deelzaken*
  - Kopregel:
  - Vast Opschrift: *Alle gesloten;samenwerkingsruimtes*
  - Dynamisch tegelopschrift:
  - Actie: *getFlexList(SysStandardList,nil,nil,G,gesloten_swfruimtes)*

