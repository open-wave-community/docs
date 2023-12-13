# Tegel Afgeronde zaken bij dit project

**Let op:** niet standaard uitgeleverd

## Trigger

De tegel is een trigger voor het lijstscherm _Afgeronde zaken bij dit project_ en toont de zaken die op hetzelfde perceeladres, en hetzelfde **hoofprojectlocatie** af hebben gespeeld als de zaak waarvandaan de lijst aangeroepen wordt. Is alleen zichtbaar indien er ook een hoofdprojectlocatie (tbzaakkadperc.dlhoofdprojectlocatie = 'T') is opgegeven bij de zaak.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _handhavingdetail_
- Kolom: _Samenhang_
- Kopregel: _Lopende zaken bij dit project_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(zakenlijst,projectzaken,{id},1,H)_
- SQL tegel onzichtbaar indien result=0:

```sql
select case when count(dnkey) = 1 then 1 else 0 end
  from tbzaakkadperc
  where dnkeyhandhavingen = {id}
  and dlhoofdprojectlocatie = 'T'
```
