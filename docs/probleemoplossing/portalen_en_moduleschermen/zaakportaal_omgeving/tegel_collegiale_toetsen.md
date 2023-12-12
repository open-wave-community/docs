# Tegel Collegiale Toetsen

## Trigger

De tegel is een trigger voor het lijstscherm *Collegiale Toetsen* bij een omgevingszaak.

Zie [beheertabel](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal_nieuw/tegels_kolom_schermbeheer.md) *[tabellen standaardapi](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal_nieuw/tegels_kolom_schermbeheer/schermdef_tabellen_standaardapi.md)* (tbsysstandardtable.dvcode = *omgeving_collegtoets)*.
Doorklikken opent het geregistreerde document waar de toets bij hoort.

  *  De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering: *omgeving_collegtoets*) 
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren 
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *omgevingdetail*
  * Kolom: *BehandelingProces*
  * Kopregel: *Collegiale Toetsen*
  * Dynamisch tegelopschrift: *getTileContent(omgeving_collegtoets,{id})*
  * Actie: *getFlexList(SysStandardList,tbomgvergunning,{id},,omgeving_collegtoets)*

