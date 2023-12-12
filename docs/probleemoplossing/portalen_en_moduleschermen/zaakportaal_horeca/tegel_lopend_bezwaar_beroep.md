# Tegel Lopend Bezwaar/Beroep

## Trigger

De tegel is een trigger voor het lijstscherm van lopende bezwaar/beroepzaken bij een Horecazaak ([Bezwaar en beroep](/docs/probleemoplossing/module_overstijgende_schermen/bezwaar_beroep/README.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _horeca_openbezwberoep_)
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _horecadetail_
- Kolom: _Overig_
- Kopregel: _Lopend bezwaar/beroep_
- Dynamisch tegelopschrift: _getTileContent(horeca_openbezwberoep,{id})_
- Actie: _getFlexList(tbbezwaarberoep,tbhorecavergunningen,{id},O,C)_
