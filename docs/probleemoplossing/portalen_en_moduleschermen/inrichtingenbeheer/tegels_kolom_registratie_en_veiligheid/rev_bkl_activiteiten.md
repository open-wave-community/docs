# REV BKL-activiteiten

## Trigger

De tegel is een trigger voor tonen van het overzicht van de codetabel voor de _Besluit kwaliteit leefomgeving (BKL)_ activiteiten en coderingen. Voor de definitie van de lijst zie beheertabel _tabellen standaardapi_ (tbsysstandardtable.dvcode = _beheer_tbmilcodebkl)_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Inrichtingenbeheer_
- Kolom: _Registratie en Veiligheid_
- Kopregel: _REV; BKL-activiteiten_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbmilcodebkl)_
