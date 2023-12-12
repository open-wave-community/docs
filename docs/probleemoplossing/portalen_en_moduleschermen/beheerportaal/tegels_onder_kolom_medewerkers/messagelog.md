# Messagelog

## Trigger

De tegel is een trigger voor een tabel waarin de de verzonden en ontvangen StUfZaken en StUfOLO berichten worden gelogd, zie bij Instellen/Inrichten: [MessageLog](/docs/instellen_inrichten/messagelog.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: [Beheerportaal](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaa.md)
- Kolom: [Tegels onder kolom Medewerkers](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_medewerkers.md)
- Kopregel: _Messagelog_
- Actie: _getFlexList(tbmessagelog)_
