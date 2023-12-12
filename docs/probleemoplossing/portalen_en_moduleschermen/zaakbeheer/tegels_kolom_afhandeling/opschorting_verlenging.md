# Opschorten Verlengen

## Trigger

De tegel is een trigger voor het tonen van de lijst met redenen waarom een zaak moet worden _Opgeschort of Verlengd_, zo mogelijk voorzien van een termijn.

Voor de definitie van de achterliggende lijst en knoppen: zie beheertegel: _Tabellen standaardapi_ (tbsysstandardtable.dvcode = beheer_tbcodeopschort).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Afhandeling_
- Kopregel: _Opschorting Verlenging_
- Actie: _getFlexList(SysStandardList,nil,nil,nil,beheer_tbcodeopschort)_
