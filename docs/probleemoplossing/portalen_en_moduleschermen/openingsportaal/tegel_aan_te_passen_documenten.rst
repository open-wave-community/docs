Tegel Aan te passen documenten
==============================

Trigger
-------

De tegel is een trigger voor de doorkieslijst *Aan te passen documenten*
gebaseerd op vwfrmcorrespondentie waarvoor geldt dat:

-  brief moet aangepast worden is aangevinkt (dlbriefmoetaangepast =
   'T')
-  en de inlogger is de actieve dossierbehandelaar van de bovenliggende
   zaak
-  en de vervaldatum van het geregistreerde document is niet gevuld of
   groter dan vandaag.

Dubbel klikken op een item van deze lijst leidt tot de detailkaart van
het geregistreerde document (tbcorrespondentie).

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
-  Vast Opschrift: *Aan te passen documenten*
-  Dynamisch tegelopschrift: *getTileContent(opening_aantepassen)*
-  Actie: *getFlexList(SysStandardList,nil,nil,G,opening_aantepassen)*
