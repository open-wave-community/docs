# Prognose

## Trigger

De tegel is een trigger voor het doorkiesscherm naar de _Prognoses_ en hun soorten.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Overig 1_
- Kopregel: _Prognose_
- Actie: _getFlexList(StandardList,nil,nil,vwfrmprognose;dnkey,nil,nil,nil,nil,insertStandardRow;deleteStandardRow)_
