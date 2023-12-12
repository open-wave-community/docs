# Container Exportrapportages

De tegel is een trigger voor een lijst van _Containers met rapportages_ (tbexportcontainer) die via de operations (beheertegel _Operations_) al of niet gescheduled gestart kunnen worden en waarvan de resultaatsets als zip worden ingepakt en geëxporteerd zie: [Export Report Container](/instellen_inrichten/export_report_container.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _beheerportaal-NIEUW_
- Kolom: _Werkbeheer_
- Kopregel: _Container;Exportrapportages_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(SysStandardList,,{id},,beheer_containerexportrapportages)_
