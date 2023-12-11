SBI-coderingen
==============

Trigger
-------

De tegel is een trigger voor een lijst van alle gehanteerde
*SBI-coderingen* (standaard bedrijfsindeling) per inrichting.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing (codering *inrichting_sbi*)
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *beheer*
-  Kolom: *Inrichtingen*
-  Kopregel: *Sbi-coderingen*
-  Actie: *getFlexList(tbmilcodesbi)*
