Klachtvorm
==========

Trigger
-------

De tegel is een trigger voor een lijst met *Vormen waarin een klacht
voor kan komen*.

-  De tegel is alleen zichtbaar voor inlogger wanneer

   -  deze aan hem/haar is toegekend:
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Beheer*
-  Kolom: *Brontabellen II*
-  Kopregel: *Klachtvorm*
-  Actie: *getFlexList(StandardList,nil,nil,tbklachtvorm;dnkey,
   nil,nil,nil,nil,insertStandardRow([dvcodevorm;Geef unieke
   codering.;string;200]);deleteStandardRow)*
