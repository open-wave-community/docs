# Container Exportrapportages

De tegel is een trigger voor een lijst van *Containers met rapportages* (tbexportcontainer) die via de operations (beheertegel *Operations*) al of niet gescheduled gestart kunnen worden en waarvan de resultaatsets als zip worden ingepakt en geëxporteerd zie: [Export Report Container](/docs/instellen_inrichten/export_report_container.md).

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing 
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren 
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *beheerportaal-NIEUW*
  * Kolom: *Werkbeheer*
  * Kopregel: *Container;Exportrapportages*
  * Dynamisch tegelopschrift:
  * Actie: *getFlexList(SysStandardList,,{id},,beheer_containerexportrapportages)*

