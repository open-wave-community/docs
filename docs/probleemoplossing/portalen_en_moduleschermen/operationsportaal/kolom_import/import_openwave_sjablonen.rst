Import OpenWave sjablonen
=========================

Zie ook `Import/Export rapport, sjabloon
etc. </docs/probleemoplossing/programmablokken/import_export_xlm.md>`__.

Trigger
-------

De tegel is een trigger voor de wizard die het importeren van
rapportages, sjablonen, processen, queries e.d. regelt.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Operations*
-  Kolom: *Import*
-  Kopregel: *Import xml OpenWave;sjablonen,schermen;queries,
   processen…*
-  Actie: \*startWizard(uploadmultiplefiles,-1,,no_uploadfile;importxml)
