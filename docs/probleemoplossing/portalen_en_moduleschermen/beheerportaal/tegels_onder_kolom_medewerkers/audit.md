# Audit

## Trigger

De tegel is een trigger voor een lijst van alle in OpenWave verrichte handelingen, zie bij Instellen/Inrichting: [Audit](../../../../instellen_inrichten/audit.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portaltegel](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)

- Portaal: [Beheerportaal](README.md)
- Kolom: [Tegels onder kolom Medewerkers](README.md)
- Kopregel: _Audit_
- Actie: _getFlexList(tbaudit)_
