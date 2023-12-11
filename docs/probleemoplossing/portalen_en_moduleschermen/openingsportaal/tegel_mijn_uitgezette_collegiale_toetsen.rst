Tegel Mijn uitgezette collegiale toetsen
========================================

Trigger
-------

De tegel is een trigger voor de doorkieslijst *Mijn uitgezette
collegiale toetsen* gebaseerd op vwfrmcorrespcollegtoets waarvoor geldt
dat:

-  de toetsdatum nog leeg is (dddatumgetoetst)
-  en de aanvrager (dvcodemwaanvrager) is gevuld met de inlogger
-  en het bovenliggende document is nog niet verstuurd en niet digitaal
   ondertekend
-  en de vervaldatum van het geregistreerde document is niet gevuld of
   groter dan vandaag.

Dubbel klikken op een item van deze lijst leidt tot de detailkaart van
het geregistreerde document (tbcorrespondentie) waar de collegiale toets
bij hoort.

-  De tegel is alleen zichtbaar voor inlogger wanneer: \*deze aan
   hem/haar is toegekend

   -  en de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar, maar wel
gedefinieerd:

-  indien foutieve query verwijzing
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
-  Kolom: *Mijn Taken*
-  Kopregel
-  Vast Opschrift: *Mijn uitgezette;collegiale toetsen*
-  Dynamisch tegelopschrift: *getTileContent(opening_muzct)*
-  Actie: *getFlexList(SysStandardList,nil,nil,G,opening_muzct)*
