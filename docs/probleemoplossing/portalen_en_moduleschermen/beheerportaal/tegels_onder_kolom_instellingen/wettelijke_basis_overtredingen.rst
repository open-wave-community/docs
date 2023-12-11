Wetten/Overtredingen
====================

Trigger
-------

De tegel is een trigger voor het lijstscherm *Wettelijke basis*.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal:
   `Beheerportaal </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal.md>`__
-  Kolom: `Tegels onder kolom
   Instellingen </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_instellingen.md>`__
-  Kopregel: *Wetten/Overtredingen*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,G,beheer_tbhandhwetbasis)*
