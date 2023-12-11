Geen Lopende zaken
==================

Trigger
-------

De tegel geeft aan dat er voor het DSO project (wordt aangeroepen vanuit
het DSO projectportaal) geen Lopende DSO zaken zijn.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert:

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing (codering: dso_geenlopendezaken)
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren
-  indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen)
   op de tegeldefinitie uitgevinkt is.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *dsoprojectportaal*
-  Kolom: *Lopende DSO-Zaken*
-  Kopregel: *Geen Lopende zaken*
-  Dynamisch tegelopschrift: *dso_geenlopendezaken*
-  Actie:
-  Onzichtbaar indien result van de volgende select 0 is:

.. code:: sql

   select case when 
      (select count(*) from tbomgvergunning where dnkeydsoproject = {id} and ddbesluitdatum is null) >= 1 
     then 0 else 1 end
