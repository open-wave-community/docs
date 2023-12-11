Inrichtingenbeheer
==================

Deze tegel verwijst door naar portaal **Inrichtingenbeheer**. Dit
portaal bevat alle beheertegels te maken met beheren van
inrichtingen/locatie dossiers en onderliggende dochtertabellen in
OpenWave.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren
-  indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen)
   op de tegeldefinitie uitgevinkt is.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: docs:`Beheerportaal -
   NIEUW </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal_nieuw.md>`__
-  Kolom: `Tegels onder kolom Overige
   beheerportalen </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal_nieuw/tegels_kolom_overige_portalen.md>`__
-  Kopregel: *Inrichtingenbeheer*
-  Dynamisch tegelopschrift:
-  Actie: *opentabpage(#inrichtingenbeheer)*
