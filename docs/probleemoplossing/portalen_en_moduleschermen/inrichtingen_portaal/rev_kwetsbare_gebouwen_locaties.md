# Tegel REV Kwetsbare Gebouwen Locaties

## Trigger

De tegel is een trigger voor een lijst van alle *Kwetsbare gebouwen en locaties* waarop de ev-contouren van een inrichting van invloed kunnen zijn

ZIE: [Register Externe Veiligheid](/docs/instellen_inrichten/register_exrterne_veiligheid.md)

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de instelling *Sectie: REV en Item: KWETSGEBZICHTBAAR* aangevinkt is  (wordt aangeroepen bij tegeldefinitie)
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

* indien foutieve queryverwijzing (codering *inrichting_bklgebloc*)
* indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
* indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *inrichtingdetail*
* Kolom: *Wat gebeurt er*
* Kopregel: *REV kwetsbare geb/locaties*
* Dynamisch tegelopschrift: *getTileContent(inrichting_bklgebloc,{id})*
* Actie: *getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_tbmilbklkwetsbgebloc)*
