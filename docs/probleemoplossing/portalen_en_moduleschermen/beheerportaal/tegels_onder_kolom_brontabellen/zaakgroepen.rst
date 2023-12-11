Zaakgroepen
===========

Trigger
-------

De tegel is een trigger voor een tabel die wordt gebruikt om zaken, al
of niet uit verschillende modules, aan elkaar te kunnen ketenen.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Beheer*
-  Kolom: *Brontabellen*
-  Kopregel: *Zaakgroepen*
-  Actie:
   *getFlexList(StandardList,nil,nil,tbgroepvergunning;dnkey,nil,nil,nil,nil,insertStandardRow;deleteStandardRow)*
