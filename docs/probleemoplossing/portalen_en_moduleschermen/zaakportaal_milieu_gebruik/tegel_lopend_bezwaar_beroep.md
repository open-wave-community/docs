# Tegel Lopend Bezwaar/Beroep

## Trigger

De tegel is een trigger voor het lijstscherm van *Lopende bezwaar/beroepzaken* bij een Milieu/Gebruik zaak.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *milieugebruik_openbezwberoep*)
  * indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *milieugebruikdetail*
  * Kolom: *Overig*
  * Kopregel: *Lopend bezwaar/beroep*
  * Dynamisch tegelopschrift: *getTileContent(milieugebruik_openbezwberoep,{id})*
  * Actie: *getFlexList(tbbezwaarberoep,tbmilvergunningen,{id},O,E)*

