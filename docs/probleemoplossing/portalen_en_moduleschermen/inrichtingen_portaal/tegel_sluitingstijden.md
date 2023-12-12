# Tegel Sluitingstijden

## Trigger

De tegel is een trigger voor een tabel om (N)ormale en (I)ncidentele vergunningen van een inrichting te noteren.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _inrichting_horsluitingstijden_)
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _inrichtingdetail_
- Kolom: _Horeca_
- Kopregel: _Sluitingstijden_
- Dynamisch tegelopschrift: _getTileContent(inrichting_horsluitingstijden,{id})_
- Actie: _getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_tbhorsluitingstijden)_
