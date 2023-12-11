Tegel Uitgezette SWF actieverzoeken
===================================

Trigger
-------

De tegel is een trigger voor het openen van de `Lijst Openstaande
uitgezette
actieverzoeken </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_uitgezette_swf_actieverzoeken/lijst_openstaande_uitgezette_actieverzoeken.md>`__.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar, maar wel
gedefinieerd:

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

-  Portaal: *Opening*
-  Kolom: *Deelzaken*
-  Kopregel:
-  Vast Opschrift: *Uitgezette SWF;actieverzoeken*
-  Dynamisch tegelopschrift: *getTileContent(uitgezette_actieverzoeken)*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,G,uitgezette_actieverzoeken)*
