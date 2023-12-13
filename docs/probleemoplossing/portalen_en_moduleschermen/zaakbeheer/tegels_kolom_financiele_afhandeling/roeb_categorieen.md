# ROEB Categorieën

## Trigger

De tegel is een trigger voor het tonen van de lijsten met _ROEB - Hoofd- en subcategorieën en bedragen_ (zie ook [Roeb berekening vastg. kosten](../../../../instellen_inrichten/roeb_berekening_vastg._kosten.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Financiele Afhandeling_
- Kopregel: _ROEB categorieen_
- Actie: _getFlexList(SysStandardList,nil,nil,nil,beheer_tbroebhfdcat)_
