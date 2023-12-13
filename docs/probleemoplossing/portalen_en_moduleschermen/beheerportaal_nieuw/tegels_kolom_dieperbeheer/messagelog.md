# Messagelog

De tegel is een trigger voor een tabel waarin de de verzonden en ontvangen StUfZaken en StUfOLO berichten worden gelogd, zie bij Instellen/Inrichten: [MessageLog](../../../../instellen_inrichten/messagelog.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _beheerportaal-NIEUW_
- Kolom: _Dieper Beheer_
- Kopregel: _Messagelog_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(tbmessagelog)_
