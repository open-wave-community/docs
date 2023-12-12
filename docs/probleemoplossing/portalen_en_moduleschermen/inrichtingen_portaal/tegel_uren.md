# Tegel Uren

## Trigger

De tegel is een trigger voor het lijstscherm met een overzicht van het totaal aantal *Geregistreerde uren* bij een inrichting ([Urenregistratie](/docs/probleemoplossing/module_overstijgende_schermen/urenregistratie.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering *inrichting_uren*)
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom altijd verversen (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *inrichtingdetail*
- Kolom: *Welke controles*
- Kopregel: *Uren*
- Actie: *getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_tburen)*
- SQL:

```sql
select case when e.dlcmilinruurvsb = 'T' then 1 else 0 end
  from tbmedewerkers d
  inner join tbmilrechten e on (d.dnkeyrechten = e.dnkeyrechten)
  where trim(d.dvcode) = trim(:keyaccount)
```
