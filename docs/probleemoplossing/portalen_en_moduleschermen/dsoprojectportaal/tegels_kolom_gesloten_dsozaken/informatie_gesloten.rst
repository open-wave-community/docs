Informatie (Gesloten)
=====================

Trigger
-------

De tegel is een trigger voor het lijstscherm van de *Afgesloten zaken
van type Informatie* bij een DSO project.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert:

      -  de tegel is zichtbaar als er voor dit DSO project afgesloten
         omgevingszaken (besluitdatum is gevuld) zijn van DSO type
         *Informatie* OF *Informatie ongewoon voorval* en er GEEN
         activiteiten met eigenschap *WKB* aanwezig zijn voor deze zaken

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing (codering *dso_informatie_gesloten*)
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
-  Kolom: *Afgesloten DSO-Zaken*
-  Kopregel: *Informatie*
-  Dynamisch tegelopschrift:
   *getTileContent(dso_informatie_gesloten,{id})*
-  Actie:
   *getFlexList(SysStandardList,tbdsoproject,{id},nil,dso_informatie_gesloten)*
-  Onzichtbaar indien result van de volgende select 0 is:

.. code:: sql

   select case when
      (select count(*)
       from tbomgvergunning
       where dnkeydsoproject = {id}
       and (lower(dvdsoverzoektype) = 'informatie' OR lower(dvdsoverzoektype) = 'informatie ongewoon voorval')
       and ddbesluitdatum is not null
       and (lower(dvdsoverzoekdoel) <> ''vooroverleg'' and lower(dvdsoverzoekdoel) <> ''conceptverzoek'')
       and dnkey not in (select dnkeyomgvergunningen from tbtoestemmingen
                         where dnkeysrttoestemming in (select dnkey from tbsrttoestemming
                                                       where dliswkb = 'T'))) >= 1
       then 1 else 0 end
