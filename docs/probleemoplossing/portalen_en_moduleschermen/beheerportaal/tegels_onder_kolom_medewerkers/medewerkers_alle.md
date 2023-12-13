# Medewerkers (alle)

## Trigger

De tegel is een trigger voor een lijst met _Alle medewerkers_, zie [Medewerkers](../../../../instellen_inrichten/medewerkers.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: [Beheerportaal](../../portalen_en_moduleschermen/beheerportaal.md)
- Kolom: [Tegels onder kolom Medewerkers](README.md)
- Kopregel: _Medewerkers (alle)_
- Actie: _getFlexList(TBMEDEWERKERS,nil,nil,1,nil)_
