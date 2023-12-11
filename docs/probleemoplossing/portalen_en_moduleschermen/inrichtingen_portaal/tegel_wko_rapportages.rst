Tegel WKO rapportages
=====================

Trigger
-------

De tegel is een trigger voor een tabel waarin per inrichting *WKO
Rapportages* worden vastgelegd.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *inrichtingdetail*
-  Kolom: *Bodem*
-  Kopregel: *WKO Rapportages*
-  Dynamisch tegelopschrift:
-  Actie:
   *getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_vwfrmmilwkorapp)*
