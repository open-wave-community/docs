# Tegel Projecten vervoer

## Trigger

De tegel is een trigger voor het tonen van de *Vervoerprojectregistraties* bij de inrichting. Bij opvoer van nieuwe vervoerprojectregistraties is er keuze uit records in codetabel tbmilprojecten met indicatie 'VR', te vinden in beheerportaal *Inrichtingenbeheer* onder tegel *Projecten duurzaamheid*.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering *inrichting_vervoerproj*)
- indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *inrichtingdetail*
- Kolom: *Duurzaamheid*
- Kopregel: *Projecten vervoer*
- Dynamisch tegelopschrift: *getTileContent(inrichting_vervoerproj,{id})*
- Actie: *getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_vwfrmmilvervoerprojecten)*
