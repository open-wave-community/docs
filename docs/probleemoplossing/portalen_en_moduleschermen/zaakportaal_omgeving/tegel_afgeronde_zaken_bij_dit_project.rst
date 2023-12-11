Tegel Afgeronde zaken bij dit project
=====================================

**Let op: niet standaard uitgeleverd**

Trigger
-------

De tegel is een trigger voor het lijstscherm *Afgeronde zaken bij dit
project* en toont de zaken die op hetzelfde perceeladres, en hetzelfde
**hoofprojectlocatie** af hebben gespeeld als de zaak waarvandaan de
lijst aangeroepen wordt. Is alleen zichtbaar indien er ook een
hoofdprojectlocatie (tbzaakkadperc.dlhoofdprojectlocatie = 'T') is
opgegeven bij de zaak.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *omgevingdetail*
-  Kolom: *Samenhang*
-  Kopregel: *Lopende zaken bij dit project*
-  Dynamisch tegelopschrift:
-  Actie: *getFlexList(zakenlijst,projectzaken,{id},1,W)*
-  SQL tegel onzichtbaar indien result=0:

.. code:: sql

   select case when count(dnkey) = 1 then 1 else 0 end
       from tbzaakkadperc
       where dnkeyomgvergunningen = {id}
       and dlhoofdprojectlocatie = 'T'
