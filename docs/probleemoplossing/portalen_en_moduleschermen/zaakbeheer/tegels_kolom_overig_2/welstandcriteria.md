# Welstandcriteria

## Trigger

De tegel is een trigger voor het tonen van het overzicht van _Welstandcriteria_ en het gebied waarop ze van toepassing zijn.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Overig 2_
- Kopregel: _Welstandcriteria_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbwelstandcriteria)_
