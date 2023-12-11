# Nalevingscoderingen controle

## Trigger

De tegel is een trigger voor tonen van het overzicht van duidingen op het _Nalevingsgedrag_ van een inrichting zoals goed, matig, onbekend.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Inrichtingenbeheer_
- Kolom: _Controle en Maatregelen_
- Kopregel: _Nalevingscoderingen; controle_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbmilnaleving)_
