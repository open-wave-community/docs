Tegel Locaties
==============

Trigger
-------

De tegel is een trigger voor het openen van de lijst- en detailschermen
van *gemeentes, woonplaatsen per gemeente, openbare ruimtes per
woonplaats en adressen per openbare ruimte*.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
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
-  Kolom: *Diversen*
-  Kopregel:
-  Vast Opschrift:*Locaties*
-  Dynamisch tegelopschrift:
-  Actie: *getFlexList(tb33gemeente)*

Gerelateerde Pagina's
---------------------

-  `Detailscherm gemeente/ lijst
   woonplaatsen </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_locaties/detail_gemeente_met_lijst_woonplaatsen.md>`__
-  `Detailscherm openbare ruimte/ lijst
   locatie-adressen </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_locaties/detail_openbare_ruimte_met_lijst_locatie-adressen.md>`__
-  `Detailscherm woonplaats/ lijst openbare
   ruimtes </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_locaties/detail_woonplaats_met_lijst_openbare_ruimtes.md>`__
-  `Lijst
   Gemeentes </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_locaties/lijst_gemeentes.md>`__
