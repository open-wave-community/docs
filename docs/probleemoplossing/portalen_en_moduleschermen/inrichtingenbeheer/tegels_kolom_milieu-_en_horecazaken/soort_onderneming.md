# Soort onderneming

## Trigger

De tegel is een trigger voor het tonen van het een lijst met *Soort horecaondernemingen*, zoals restaurant, bar/café.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Inrichtingenbeheer*
* Kolom: *Milieu- en Horecazaken*
* Kopregel: *Soort onderneming*
* Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbhorsrtonderneming)*
