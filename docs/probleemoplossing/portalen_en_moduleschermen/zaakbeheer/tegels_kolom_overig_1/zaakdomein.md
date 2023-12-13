# Zaakdomein

## Trigger

De tegel is een trigger voor een lijst met in te stellen *Zaakdomeinen* waaruit kan worden gekozen in het detailscherm van een zaak.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Zaakbeheer*
* Kolom: *Overig 1*
* Kopregel: *Zaakdomein*
* Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbzaakdomein)*
