RAV/BWL-combinaties
===================

Trigger
-------

De tegel is een trigger voor het tonen van het overzicht van *Diercode,
stalcode en BWL coderingen*.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Inrichtingenbeheer*
-  Kolom: *Registratie Vee*
-  Kopregel: *RAV/BWL-combinaties*
-  Actie: *getFlexList(SysStandardList,,,G,beheer_tbmilravbwl)*
