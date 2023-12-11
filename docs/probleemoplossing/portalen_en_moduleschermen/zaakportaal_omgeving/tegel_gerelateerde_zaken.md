# Tegel DSO Gerelateerde Zaken

## Trigger

De tegel is een trigger voor het lijstscherm van DSO gerelateerde zaken. Zie [DSO Gerelateerde Zaken](/docs/probleemoplossing/programmablokken/dso_gerelateerde_zaken.md)

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval is de tegel alleen zichtbaar indien er aan de omgevingszaak gerelateerde kaarten aanwezig zijn in tbgerelateerde verzoeken.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *omgeving_groep*) 
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren 
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *omgevingdetail*
  * Kolom: *Samenhang*
  * Kopregel: *DSO-gerelateerde zaken*
  * Dynamisch tegelopschrift: *getTileContent(dso_gerelateerde_zaken,{id})*

Deze query, *dso_gerelateerde_zaken*, moet handmatig aangemaakt en gevuld  worden via de *Queries* beheertegel met deze sql:

```sql
select 'Aantal: ' || count(dnkey) Aantal 
   from tbgerelateerdezaken 
   where dnkeyomgvergunningen = {id}
```

  * Actie: *getFlexList(SysStandardList,,{id},,omgeving_gerelateerdezaken)*
  * sql tegel onzichtbaar:

```sql
select case when exists 
   (select 1 from tbgerelateerdezaken where dnkeyomgvergunningen = {id}) 
   then 1 
   else 0 
   end
```

