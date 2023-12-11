# Horeca aanvraagreden

## Trigger

De tegel is een trigger voor een lijst van mogelijke _Redenen van aanvraag bij Horecavergunningen_, zoals nieuwe zaak, overname, wijziging statuten.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Inrichtingbeheer_
- Kolom: _Milieu- en Horecazaken_
- Kopregel: _Horeca aanvraagreden_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbhorredenaanvraag)_
