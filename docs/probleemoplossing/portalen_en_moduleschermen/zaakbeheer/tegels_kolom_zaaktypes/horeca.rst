Zaaktypes Horeca
================

Trigger
-------

De tegel is een trigger voor het doorkiesscherm naar *Soorten
Horecavergunningen*.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

-  Portaal: *Zaakbeheer*
-  Kolom: *Zaaktypes*
-  Kopregel: *Zaaktypes horeca*
-  Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbsoorthorverg)*
