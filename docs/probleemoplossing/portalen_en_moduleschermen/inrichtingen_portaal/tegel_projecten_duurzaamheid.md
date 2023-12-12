# Tegel Projecten duurzaamheid

## Trigger

De tegel is een trigger voor het tonen van de *Duurzaamheidsprojectregistraties* bij de inrichting. Bij opvoer van nieuwe duurzaamheidsprojectregistraties is er keuze uit records in codetabel tbmilprojecten met indicatie 'DU', te vinden in beheerportaal *Inrichtingenbeheer* onder tegel *Projecten duurzaamheid*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

* indien foutieve queryverwijzing (codering *inrichting_duurzaamheidproj*)
* indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
* indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *inrichtingdetail*
* Kolom: *Duurzaamheid*
* Kopregel: *Projecten duurzaamheid*
* Dynamisch tegelopschrift: *getTileContent(inrichting_duurzaamheidproj,{id})*
* Actie: *getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_vwfrmmilduurzaamheidprojecten)*
