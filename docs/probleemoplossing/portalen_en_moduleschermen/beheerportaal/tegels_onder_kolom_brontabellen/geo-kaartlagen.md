# GEO kaartlagen

## Trigger

De tegel is een trigger voor een lijst van *Kaartlagen* die getoond worden op de kaartjes van OWB.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Beheer*
* Kolom: *Brontabellen*
* Kopregel: *GEO kaartlagen*
* Actie: *getFlexList(StandardList,nil,nil,vwfrmgeowms;dnkey,nil,nil,nil,nil,insertStandardRow;deleteStandardRow)*
