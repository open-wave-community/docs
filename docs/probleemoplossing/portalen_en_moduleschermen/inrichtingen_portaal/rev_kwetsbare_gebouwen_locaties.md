# Tegel REV Kwetsbare Gebouwen Locaties

## Trigger

De tegel is een trigger voor een lijst van alle _Kwetsbare gebouwen en locaties_ waarop de ev-contouren van een inrichting van invloed kunnen zijn

ZIE: [Register Externe Veiligheid](/instellen_inrichten/register_exrterne_veiligheid.md)

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de instelling _Sectie: REV en Item: KWETSGEBZICHTBAAR_ aangevinkt is (wordt aangeroepen bij tegeldefinitie)
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _inrichting_bklgebloc_)
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _inrichtingdetail_
- Kolom: _Wat gebeurt er_
- Kopregel: _REV kwetsbare geb/locaties_
- Dynamisch tegelopschrift: _getTileContent(inrichting_bklgebloc,{id})_
- Actie: _getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_tbmilbklkwetsbgebloc)_
