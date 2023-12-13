# Omgevingszaken

## Trigger

De tegel is een trigger voor het lijstscherm van de *Vervolgzaken van type Omgeving* bij een DSO project. Dit houdt in de omgevingszaken die via een groep verbonden zijn aan de DSO zaken voor het DSO project. Dit zijn dus zaken die NIET zelf uit het DSO komen.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert:
      * de tegel is zichtbaar als er omgevingszaken zijn (zowel open als gesloten) die via groep verbonden zijn aan de DSO zaken vallende onder het DSO project
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing
  * indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  *  Portaal: *dsoprojectportaal*
  *  Kolom: *Vervolgzaken*
  *  Kopregel: *Omgevingszaken*
  *  Dynamisch tegelopschrift: *getTileContent(dso_vervolgzaak_omgeving,{id})*
  *  Actie: *getFlexList(SysStandardList,,{id},nil,dso_vervolgzaak_omgeving)*
  *  Onzichtbaar indien result van de volgende select 0 is:

```sql
select case when
   (select count(*) from tbomgvergunning
    where dnkeydsoproject is null
    and dnkeygroepvergunning in (select dnkeygroepvergunning from tbomgvergunning
                                 where dnkeydsoproject = {id})) >= 1
  then 1 else 0 end
```

