# Messagelog

## Trigger

De tegel is een trigger voor een tabel waarin alle uitgaande en binnenkomende berichten worden gelogd zoals StUfZaken en StUfOLO en DSO-berichten, zie bij Instellen/Inrichten: [MessageLog](/instellen_inrichten/messagelog.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Servicecentrum_
- Kolom: _Logs_
- Kopregel: _Messagelog_
- Actie: _getFlexList(tbmessagelog)_
