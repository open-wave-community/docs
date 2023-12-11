Schermkolomdefinitie tabellen standaard-api
===========================================

De tegel is een trigger naar de lijst met *Schermkolomdefinities* voor
lijst-/detailschermen waarnaar wordt verwezen vanuit de tabel
*tbsysstandard* (beheertegel: *Tabellen standaardapi*). Het gaat om de
set uit vwfrmscreencolumns where dnreportkey is null and
lower(dvclassname) = 'sysstandard'.

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

-  Portaal: *beheerportaal-NIEUW*
-  Kolom: *Scherm- en Tegelbeheer*
-  Kopregel: *Schermkolomdefinitie;tabellen standaard-api*
-  Dynamisch tegelopschrift:
-  Actie:
   *getFlexList(SysStandardList,nil,nil,,beheer_tbscreencolumns_tabellenstandapi)*
