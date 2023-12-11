# Tegel Lopende zaken bij dit project

**Let op: niet standaard uitgeleverd**

## Trigger

De tegel is een trigger voor het lijstscherm *Lopende zaken bij dit project* en toont de zaken die op hetzelfde perceeladres, EN hetzelfde **hoofprojectlocatie** afspelen als de zaak waarvandaan de lijst aangeroepen wordt. Is alleen zichtbaar indien er ook een hoofdprojectlocatie (tbzaakkadperc.dlhoofdprojectlocatie = 'T') is opgegeven bij de zaak.

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
    * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing 
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren. 

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: [Zaakportaal Omgeving](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving.md)
  * Kolom: *Samenhang*
  * Kopregel: *Lopende zaken bij dit project*
  * Dynamisch tegelopschrift:
  * Actie: *getFlexList(zakenlijst,projectzaken,{id},0,W)*
  * SQL tegel onzichtbaar indien result=0:

```sql
select case when count(dnkey) = 1 then 1 else 0 end 
  from tbzaakkadperc 
  where dnkeyomgvergunningen = {id} 
  and dlhoofdprojectlocatie = 'T'
```

