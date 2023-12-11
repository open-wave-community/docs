Tabellen Standaardapi
=====================

De tegel is een trigger voor een lijst met metadata over een andere view
of tabel ten behoeve van flexlist en flexdetail (zie: `Scherminformatie
voor
detailschermen </docs/instellen_inrichten/schermdefinitie/scherminformatie_voor_detailschermen.md>`__).

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
-  Kolom: `Tegels onder kolom Scherm- en
   Tegelbeheer </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal_nieuw/tegels_kolom_schermbeheer.md>`__
-  Kopregel: *Tabellen Standaardapi*
-  Dynamisch tegelopschrift:
-  Actie: *getFlexList(tbsysstandardtable)*
