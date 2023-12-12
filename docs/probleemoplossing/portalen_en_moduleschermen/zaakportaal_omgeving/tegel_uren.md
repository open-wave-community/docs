# Tegel Uren

## Trigger

De tegel is een trigger voor het lijstscherm met een overzicht van het *Totaal aantal geregistreerde uren* bij een omgevingszaak([Urenregistratie](/docs/probleemoplossing/module_overstijgende_schermen/urenregistratie/README.md)).

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *omgeving_uren*)
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *omgevingdetail*
  * Kolom: *Welke controles*
  * Kopregel: *Uren*
  * Actie: *getFlexList(SysStandardList,tbomgvergunning,{id},nil,omgeving_tburen)*
  * SQL:

```sql
SELECT CASE WHEN e.dlcomguurvsb = 'T' THEN 1
       ELSE 0
       END
  FROM   tbmedewerkers d
    INNER JOIN tbomgrechten e
    ON ( d.dnkeyrechten = e.dnkeyrechten )
  WHERE  Trim(d.dvcode) = Trim(:keyaccount)
```

