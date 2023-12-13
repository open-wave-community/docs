# Session

## Trigger

De tegel is een trigger voor een lijst van alle *Inlog sessies*, zie bij Instellen/Inrichting: [Inloggen](../programmablokken/inloggen.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: [Beheerportaal](../../portalen_en_moduleschermen/beheerportaal.md)
- Kolom: [Tegels onder kolom Medewerkers](tegels_onder_kolom_medewerkers/README.md)
- Kopregel: *Session*
- Actie: *getFlexList(StandardList,nil,nil,vwfrmsession;dnkeysession)*
