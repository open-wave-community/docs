# Zwemcodetabel

## Trigger

De tegel is een trigger voor het tonen van de codetabel voor *Zwemwater*. Deze codetabel wordt gebruikt bij het oproepen van keuzelijsten bij ([Zwemwater](https://doc.open-wave.nl/openwave/1.29/applicatiebeheer/instellen_inrichten/zwemwater.md)).

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Inrichtingenbeheer*
* Kolom: *Overig*
* Vast opschrift: *Zwemcodetabel*
* Actie: *getFlexList(SysStandardList,tbmilinrichtingen,{id},G,beheer_tbmilzwemcodetabel)*
