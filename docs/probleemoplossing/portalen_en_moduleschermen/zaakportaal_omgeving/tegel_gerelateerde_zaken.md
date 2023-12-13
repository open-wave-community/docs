# Tegel DSO Gerelateerde Zaken

## Trigger

De tegel is een trigger voor het lijstscherm van DSO gerelateerde zaken. Zie [DSO Gerelateerde Zaken](../programmablokken/dso_gerelateerde_zaken.md)

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval is de tegel alleen zichtbaar indien er aan de omgevingszaak gerelateerde kaarten aanwezig zijn in tbgerelateerde verzoeken.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _omgeving_groep_)
- indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _omgevingdetail_
- Kolom: _Samenhang_
- Kopregel: _DSO-gerelateerde zaken_
- Dynamisch tegelopschrift: _getTileContent(dso_gerelateerde_zaken,{id})_

Deze query, _dso_gerelateerde_zaken_, moet handmatig aangemaakt en gevuld worden via de _Queries_ beheertegel met deze sql:

```sql
select 'Aantal: ' || count(dnkey) Aantal
   from tbgerelateerdezaken
   where dnkeyomgvergunningen = {id}
```

- Actie: _getFlexList(SysStandardList,,{id},,omgeving_gerelateerdezaken)_
- sql tegel onzichtbaar:

```sql
select case when exists
   (select 1 from tbgerelateerdezaken where dnkeyomgvergunningen = {id})
   then 1
   else 0
   end
```
