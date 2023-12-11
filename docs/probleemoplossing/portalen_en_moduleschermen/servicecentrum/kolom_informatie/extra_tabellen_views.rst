Extra tabellen en views
=======================

Trigger
-------

De tegel is een trigger naar informatie over aanwezige public tabellen
en views in de database die niet bij de standaard uitlevering horen van
OpenWave.

Bij de meeste OpenWave omgevingen zal deze lijst (nog) niet gevuld zijn!

Alleen indien door REM/Functioneel beheer uitzonderingstabellen/views
zijn aangemaakt, zal de lijst records bevatten.

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
-  Kolom: *Informatie*
-  Kopregel: *Extra tabellen en views*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,,servicecentrum_vwadmextraobjects)*
