# Tegel Projecten energie

## Trigger

De tegel is een trigger voor het tonen van de _Energieprojectregistraties_ bij de inrichting. Bij opvoer van nieuwe energieprojectregistraties is er keuze uit records in codetabel tbmilprojecten met indicatie 'en', te vinden in beheerportaal _Inrichtingenbeheer_ onder tegel _Projecten duurzaamheid_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _inrichting_energieproj_)
- indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _inrichtingdetail_
- Kolom: _Duurzaamheid_
- Kopregel: _Projecten energie_
- Dynamisch tegelopschrift: _getTileContent(inrichting_energieproj,{id})_
- Actie: _getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_vwfrmmilenergieprojecten)_
