# Tegel Openstaande Invorderingen

## Trigger

De tegel is een trigger voor de tabel met *Openstaande/niet betaalde  invorderingen* n.a.v. een omgevingzaak op basis van de view vwfrmhandhinvorderingen where dnkeyomgvergunningen = dnkey van de bovenliggende omgevingzaak and ddafgehandeld is null.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. **De meegeleverde query bij de tegeldefinitie kijkt hiertoe naar de aangevinkte kolom dlinvordering in tbsoortomgverg (zaaktypes omgeving).**
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *handh_opinv*)
  * indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *omgevingdetail*
  * Kolom: *Overig*
  * Kopregel: *Openstaande invorderingen*
  * Dynamisch tegelopschrift:
  * Actie: *getFlexList(tbhandhinvorderingen,tbomgvergunning,{id},O,W)*
  * Query: *select case when  b.dlinvordering = 'T' then 1 else 0 end from tbomgvergunning a inner join tbsoortomgverg b
       on (a.dnkeysoortomgverg = b.dnkey) where a.dnkey = {id}*

De actie *getFlexList(tbhandhinvorderingen,tbomgvergunning,{id},A,W)* geeft een lijst van afgehandelde/betaalde invorderingen (vwfrmhandhinvorderingen.ddafgehandeld is not null)

