# Tegel Bodem Opslag/Voorzieningen

## Trigger

De tegel is een trigger voor een tabel met *Opslagvoorzieningen mbt de bodem* per inrichting. Alle rijen uit tbmilopslag vallen hieronder waarvoor geldt dat ze gekoppeld zijn aan de rubriek met tbmilrubiek.dvcode = 3 (= bodem: zie tegel milieurubrieken op het inrichingsbeheerportaal onder kolom Kenmerken en Verplichtingen). Zie voor indeling, rubricering van de opslagkaarten [Opslagtabel bij inrichtingen](/docs/instellen_inrichten/opslag_bij_inrichtingen.md)

* De tegel is alleen zichtbaar voor inlogger wanneer:  
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

* indien foutieve queryverwijzing (codering *inrichting_bodemopslag*)
* indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
* indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *inrichtingdetail*
* Kolom: *Bodem*
* Kopregel: *Bodem opslag/voorz*
* Dynamisch tegelopschrift: *getTileContent(inrichting_bodemopslag,{id})*
* Actie: *getFlexList(tbmilopslag,tbmilinrichtingen,{id},3,V)*
