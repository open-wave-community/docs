Ontbrekende configuratie items
==============================

De tegel is een trigger voor een tabel waarin het programma tijdens het
uitvoeren van grote programmablokken per regel noteert welke
*Configuratie-items ontbreken* voor het uitvoeren van het betreffende
programmablok. Deze regels worden x aantal dagen bewaard (instelling
*Getal1* van *Sectie: Programma* en *Item:
Opschonenmissingconfiguration*). Default 30 dagen.

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
-  Kolom: *Dieper Beheer*
-  Kopregel: *Ontbrekende;configuratieitems*
-  Dynamisch tegelopschrift:
-  Actie:
   *getFlexList(SysStandardList,,,,beheer_tbmissingconfiguration)*
