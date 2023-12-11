Medewerkers (actief)
====================

Trigger
-------

De tegel is een trigger voor een lijst met *Actieve medewerkers*, zie
`Medewerkers </docs/instellen_inrichten/medewerkers.md>`__.

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
   `Beheerportaal </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaa.md>`__
-  Kolom: `Tegels onder kolom
   Medewerkers </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_medewerkers.md>`__
-  Kopregel: *Medewerkers (actief)*
-  Actie: *getFlexList(TBMEDEWERKERS,nil,nil,2,nil)*
