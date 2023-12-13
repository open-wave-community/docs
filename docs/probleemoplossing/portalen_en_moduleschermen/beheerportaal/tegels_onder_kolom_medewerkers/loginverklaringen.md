# Loginverklaringen

## Trigger

De tegel is een trigger voor een lijst van _Loginverklaringen_ die de inlogger moet afvinken bij het inloggen.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: [Beheerportaal](README.md)
- Kolom: [Tegels onder kolom Medewerkers](README.md)
- Kopregel: _Loginverklaringen_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbloginverklaringen)_
