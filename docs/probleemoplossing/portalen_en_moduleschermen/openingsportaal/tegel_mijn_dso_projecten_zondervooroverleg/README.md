# Tegel Mijn DSO-projecten (zonder Vooroverleg)

## Trigger

De tegel is een trigger voor de doorkieslijst *Mijn DSO projecten (zonder Vooroverleg)*. Hierin worden alle DSO projecten (distinct) getoond waarvan de ingelogde medewerker een van de actieve behandelaren is. Indien er voor een DSO project alleen een vooroverleg bestaat, dan zal dit project NIET voorkomen in de getoonde lijst.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

  * indien foutieve queryverwijzing
  * indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *Opening*
  * Kolom: *Mijn Taken*
  * Kopregel:
  * Vast Opschrift:*Mijn DSO-projecten;(zonder Vooroverleg)*
  * Dynamisch tegelopschrift:
  * Actie: *getFlexList(SysStandardList,nil,nil,G,opening_vwfrmdsoprojectoverzichtzvo)*
  * Onzichtbaar indien resultaat van volgende select 0 is:
```sql
select case when d1logic = 'F' then 0 else 1 end
    from tbinitialisatie
    where lower(dvsectie) = 'programma'
    and lower(dvitem) = 'dsoportaalzondervooroverleg'
```

