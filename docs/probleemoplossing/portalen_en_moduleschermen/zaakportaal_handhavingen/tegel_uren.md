# Tegel Uren

## Trigger

De tegel is een trigger voor het lijstscherm met een overzicht van het *Totaal aantal geregistreerde uren* bij een handhavingszaak ([Urenregistratie](/probleemoplossing/module_overstijgende_schermen/urenregistratie/README.md)).

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  - indien foutieve queryverwijzing (codering *handhaving_uren*)
  - indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *handhavingdetail*
  - Kolom: *Welke controles*
  - Kopregel: *Uren*
  - Actie: *getFlexList(SysStandardList,tbhandhavingen,{id},nil,handhaving_tburen)*
  - SQL:
```sql
select case when e.dlchahuurvsb = 'T' then 1 else 0 end
  from tbmedewerkers d
  inner join tbhhrechten e on (d.dnkeyrechten = e.dnkeyrechten)
  where trim(d.dvcode) = trim(:keyaccount)
```

