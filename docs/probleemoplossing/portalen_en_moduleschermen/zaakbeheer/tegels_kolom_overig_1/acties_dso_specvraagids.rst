.. _acties-dso-spec-vraagids:

Acties DSO Spec. Vraagid's
==========================

Trigger
-------

De tegel is een trigger voor een mappingslijst van Vraagid's uit de DSO
activiteitspecificaties naar andere tabellen in OpenWave. Zie onder
kopje: *Mapping antwoorden uit specificaties op grond van vraagid* uit
`Verwerking DSO STAM
berichten </docs/probleemoplossing/programmablokken/verwerking_dso_stam_berichten.md>`__

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Zaakbeheer*
-  Kolom: *Overig 1*
-  Kopregel: *Acties op;DSO-SpecVraagids*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,G,beheer_tbdsospecvraagid)*
