# Tegel Beheerportaal-Nieuw

## Trigger

De tegel is een trigger voor het nieuwe [Beheerportaal](/probleemoplossing/portalen_en_moduleschermen/beheerportaal_nieuw/README.md).

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *Opening*
  * Kolom: *Beheer*
  * Kopregel:
  * Vast Opschrift: *[Meer Beheer (Nieuw)…..]*
  * Dynamisch tegelopschrift:
  * Actie: *opentabpage(#beheerportaal-NIEUW)*

