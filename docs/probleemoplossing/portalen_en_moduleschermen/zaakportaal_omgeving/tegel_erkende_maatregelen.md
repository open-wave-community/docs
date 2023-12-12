# Tegel Erkende Maatregelen

## Trigger

De tegel is een trigger voor het lijstscherm van ingelezen [Erkende Maatregelen](/probleemoplossing/programmablokken/erkende_maatregelen.md) bij een omgevingszaak.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *omgeving_erkmaatr*)
  * indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *omgevingdetail*
  * Kolom: *Overig*
  * Kopregel: *Erkende;Maatregelen*
  * Dynamisch tegelopschrift: *getTileContent(omgeving_erkmaatr,{id})*
  * Actie: *getFlexList(SysStandardList,nil,{id},,omgeving_tbomgerkmaatreg)*
  * SQL zichtbaarheid tegel:

```sql
select case when dverkmaatrrappid is null then 0 else 1 end
  from tbomgvergunning
  where dnkey = {id}
```

