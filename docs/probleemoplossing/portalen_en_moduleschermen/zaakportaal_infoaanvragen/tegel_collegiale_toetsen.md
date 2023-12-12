# Tegel Collegiale Toetsen

## Trigger

De tegel is een trigger voor het lijstscherm *Collegiale Toetsen* bij een Infoaanvraag.

Doorklikken opent het geregistreerde document waar de toets bij hoort.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *info_collegtoets*)
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *infodetail*
  * Kolom: *BehandelingProces*
  * Kopregel: *Collegiale Toetsen*
  * Dynamisch tegelopschrift: *getTileContent(info_collegtoets,{id})*
  * Actie: *getFlexList(SysStandardList,tbinfoaanvragen,{id},,info_collegtoets)*

