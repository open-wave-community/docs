# Urgentieklassen controlefrequentie

## Trigger

De tegel is een trigger voor het doorkiesscherm naar naar een tabel met _Urgentieklassen_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Inrichtingenbeheer_
- Kolom: _Controle en Maatregelen_
- Kopregel: _Urgentieklassen;controlefrequentie_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbmilurgentie)_
