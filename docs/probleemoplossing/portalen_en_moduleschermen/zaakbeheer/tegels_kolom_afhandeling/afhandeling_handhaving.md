# Afhandeling handhaving

## Trigger

De tegel is een trigger voor een tabel met _Afronding statussen van een handhavingszaak_ zoals volledig, niet en gedeeltelijk.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Afhandeling_
- Kopregel: _Afhandeling handhaving_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbhandhafronding)_
