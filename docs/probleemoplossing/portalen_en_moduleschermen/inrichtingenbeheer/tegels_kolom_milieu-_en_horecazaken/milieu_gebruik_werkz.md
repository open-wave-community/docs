# Milieu/gebruik werkzaamheden

## Trigger

De tegel is een trigger voor een tabel van _Werkzaamheden bij Milieu/gebruiksvergunningen_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Inrichtingenbeheer_
- Kolom: _Milieu- en Horecazaken_
- Kopregel: _Milieu/gebruik; werkzaamheden_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbmilwerkz)_
