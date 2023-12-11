# REV-waardenlijsten

## Trigger

De tegel is een trigger voor tonen van het overzicht van de codetabel voor de _REV waardenlijsten_.

Voor de definitie van de lijst zie beheertabel _tabellen standaardapi_ (tbsysstandardtable.dvcode = _beheer_tbrevwaardelijsten)_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Inrichtingenbeheer_
- Kolom: _Registratie en Veiligheid_
- Kopregel: _REV-waardenlijsten_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbrevwaardelijsten)_
