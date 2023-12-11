# Messagelog

## Trigger

De tegel is een trigger voor een tabel waarin alle uitgaande en binnenkomende berichten worden gelogd zoals StUfZaken en StUfOLO en DSO-berichten, zie bij Instellen/Inrichten: [MessageLog](/docs/instellen_inrichten/messagelog.md).

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Servicecentrum*
* Kolom: *Logs*
* Kopregel: *Messagelog*
* Actie: *getFlexList(tbmessagelog)*
