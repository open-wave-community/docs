Horeca zaken
============

Trigger
-------

De tegel is een trigger voor het lijstscherm van de *Vervolgzaken van
type Horeca* bij een DSO project. Dit houdt in de horecavergunningen die
via een groep verbonden zijn aan de DSO zaken voor het DSO project.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert:

      -  de tegel is zichtbaar als er horecavergunningen zijn (zowel
         open als gesloten) die via groep verbonden zijn aan de DSO
         zaken vallende onder het DSO project

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing (codering: dso_vervolgzaak_horeca)
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
-  Kolom: *Vervolgzaken*
-  Kopregel: *Horeca zaken*
-  Dynamisch tegelopschrift:
   *getTileContent(dso_vervolgzaak_horeca,{id})*
-  Actie:
   *getFlexList(SysStandardList,,{id},nil,dso_vervolgzaak_horeca)*
-  Onzichtbaar indien result van de volgende select 0 is:

.. code:: sql

   select case when 
      (select count(*) from tbhorecavergunningen 
       where dnkeygroepvergunning in (select dnkeygroepvergunning from tbomgvergunning 
                                      where dnkeydsoproject = {id})) >= 1 
    then 1 else 0 end
