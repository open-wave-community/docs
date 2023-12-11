Taskscheduler
=============

Trigger
-------

De tegel is een trigger voor een tabel waarin taken kunnen worden
gescheduled. Zie
`Taskscheduler </docs/instellen_inrichten/taskscheduler.md>`__.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Servicecentrum*
-  Kolom: *Acties*
-  Kopregel: *Taskscheduler*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,nil,operations_tbtaskscheduler)*
