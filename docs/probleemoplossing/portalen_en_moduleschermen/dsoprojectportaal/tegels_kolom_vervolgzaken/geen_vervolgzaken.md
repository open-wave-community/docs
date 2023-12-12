# Geen Vervolgzaken

## Trigger

De tegel geeft aan dat er voor het DSO project (wordt aangeroepen vanuit het DSO projectportaal) geen Vervolgzaken zijn. Dat betekent dat er geen niet-DSO zaken zijn die via een groep aan een DSO zaak zijn verbonden aan het DSO project.

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert:
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  - indien foutieve queryverwijzing  (codering: dso_geenvervolgzaak)
  - indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  -  Portaal: *dsoprojectportaal*
  -  Kolom: *Vervolgzaken*
  -  Kopregel: *Geen Vervolgzaken*
  -  Dynamisch tegelopschrift: *dso_geenvervolgzaak*
  -  Actie:
  -  Onzichtbaar indien result van de volgende select 0 is:

```sql
select case when
   (select count(*) from vwfrmverbondenaandsozaak
    where dnkeydsoproject is null
    and dnkeygroepvergunning in (select dnkeygroepvergunning from tbomgvergunning
                                  where dnkeydsoproject = {id})) >= 1
  then 0 else 1 end
```

