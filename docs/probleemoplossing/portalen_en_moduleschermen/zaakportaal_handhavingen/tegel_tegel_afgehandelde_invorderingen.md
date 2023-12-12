# Tegel Afgehandelde Invorderingen

## Trigger

De tegel is een trigger voor de tabel met *Invorderingen die afgehandeld cq betaald * zijn n.a.v. een handhavingszaak op basis van de view vwfrmhandhinvorderingen where dnkeyhandhaving = dnkey van de bovenliggende handhavingzaak and ddafgehandeld is not null.

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *handh_afinv*) 
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren. 

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *handhavingdetail*
  * Kolom: *Overig*
  * Kopregel: *Afgehandelde invorderingen*
  * Dynamisch tegelopschrift: *getTileContent(handh_afinv,{id})*
  * Actie: *getFlexList(TBHANDHINVORDERINGEN,TBHANDHAVINGEN,{id},A,H)*

De actie getFlexList(tbhandhinvorderingen,tbhandhavingen,{id},O,H) geeft een lijst van openstaande (niet betaalde)  invorderingen (vwfrmhandhinvorderingen.ddafgehandeld is null)

