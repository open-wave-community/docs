Container Export Rapportages
============================

Trigger
-------

De tegel is een trigger voor een lijst van *Containers met rapportages*
(tbexportcontainer) die via de operations (beheertegel *Operations*) al
of niet gescheduled gestart kunnen worden en waarvan de resultaatsets
als zip worden ingepakt en geëxporteerd zie: `Export Report
Container </docs/instellen_inrichten/export_report_container.md>`__.

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
-  Kolom: `Tegels onder kolom Instellingen
   II </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_instellingen_ii.md>`__
-  Kopregel: *Container;Exportrapportages*
-  Actie:
   *getFlexList(SysStandardList,,{id},,beheer_containerexportrapportages)*
