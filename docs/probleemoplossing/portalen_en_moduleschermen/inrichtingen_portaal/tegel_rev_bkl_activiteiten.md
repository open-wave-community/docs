# Tegel REV BKL Activiteiten

## Trigger

De tegel is een trigger voor een lijst van alle *REV BKL Activiteiten*: register externe veiligheid. per inrichting

ZIE: [Register Externe Veiligheid](/docs/instellen_inrichten/register_exrterne_veiligheid.md)

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering *inrichting_bklactiv*)
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *inrichtingdetail*
- Kolom: *Wat gebeurt er*
- Kopregel: *REV BKL-activiteiten*
- Dynamisch tegelopschrift: *getTileContent(inrichting_bklactiv,{id})*
- Actie: *getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_tbmilbklactiviteiten)*
