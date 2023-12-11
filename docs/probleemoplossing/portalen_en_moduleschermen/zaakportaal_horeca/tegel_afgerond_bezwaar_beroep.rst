Tegel Afgerond Bezwaar/Beroep
=============================

Trigger
-------

De tegel is een trigger voor het lijstscherm van afgeronde
bezwaar/beroepzaken bij een Horecazaak (`Bezwaar en
beroep </docs/probleemoplossing/module_overstijgende_schermen/bezwaar_beroep.md>`__).

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing (codering *horeca_afgerondbezwaar*)
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *horecadetail*
-  Kolom: *Overig*
-  Kopregel: *Afgerond bezwaar/beroep*
-  Dynamisch tegelopschrift:
   *getTileContent(horeca_afgerondbezwaar,{id})*
-  Actie: *getFlexList(tbbezwaarberoep,tbhorecavergunningen,{id},A,C)*
