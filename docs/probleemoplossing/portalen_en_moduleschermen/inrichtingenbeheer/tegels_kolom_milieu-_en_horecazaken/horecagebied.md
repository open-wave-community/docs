# Horecagebied

## Trigger

De tegel is een trigger voor tonen van het overzicht van mogelijke _Gebiedsduidingen_ zoals binnenstad, 19e -eeuwse gordel.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Inrichtingenbeheer_
- Kolom: _Milieu- en Horecazaken_
- Kopregel: _Horecagebied_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbhorgebied)_
