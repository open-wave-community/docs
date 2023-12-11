Tegel Vervoer
=============

Trigger
-------

De tegel is een trigger voor een tabel om *Vervoerders* bij een
inrichting te noteren. Keuze uit records in codetabel tbmilvervoerders,
te vinden in beheerportaal *Inrichtingenbeheer* onder tegel
*Vervoerders*.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing (codering *inrichting_vervoerders*)
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *inrichtingdetail*
-  Kolom: *Duurzaamheid*
-  Kopregel: *Vervoer*
-  Dynamisch tegelopschrift:
   *getTileContent(inrichting_vervoerders,{id})*
-  Actie:
   *getFlexList(SysStandardList,tbmilinrichtingen,{id},nil,inrichting_vwfrmmilinrvervoer)*
