# Tegel Bestuurlijke Maatregelen

## Trigger

De tegel is een trigger voor tabel met opgelegde *Bestuurlijke maatregelen* per omgevingzaak.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. **De meegeleverde query bij de tegeldefinitie kijkt hiertoe naar de aangevinkte kolom dlbestmaatreg in tbsoortomgverg (zaaktypes omgeving).**
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *handh_bestmaatreg*)
  * indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *omgevingdetail*
  * Kolom: *Overig*
  * Kopregel: *Bestuurlijke maatregelen*
  * Dynamisch tegelopschrift:
  * Actie: *getFlexList(tbbestmaatreg,tbomgvergunning,{id},nil,W)*
  * Query: *select case when b.dlbestmaatreg = 'T' then 1 else 0 end from tbomgvergunning a inner join tbsoortomgverg b
       on (a.dnkeysoortomgverg = b.dnkey) where a.dnkey = {id}*

