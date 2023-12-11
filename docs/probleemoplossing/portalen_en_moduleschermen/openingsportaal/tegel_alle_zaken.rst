Tegel Alle Zaken
================

Trigger
-------

De tegel is een trigger voor de lijst van alle afgehandelde of
openstaande zaken uit OpenWave.

Voor meer informatie over de lijst Alle zaken (zie `Lijst Alle
zaken </docs/probleemoplossing/module_overstijgende_schermen/zaken_inrichtingen_locaties/zaken.md>`__).
Voor de definitie van de lijst en knoppen en filter: zie
beheerportaal-Nieuw onder kolom scherm- en tegelbeheer *Tabellen
standaardapi* (tbstandardtable.dvcode = *opening_allezaken*).

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
-  Kolom: *Hoofdzaken*
-  Kopregel:
-  Vast Opschrift:*Alle zaken*
-  Dynamisch tegelopschrift:
-  Actie: *getFlexList(SysStandardList,nil,nil,G,opening_allezaken)*

Zelf in te stellen beperking op grond van gemeentecodes
-------------------------------------------------------

Aan medewerkers kan een beperkende opsomming toegekend kan worden van
locaties waarvan zij de zaken mogen zien. Dit gebeurt in het
detailscherm van de medewerkerstabel in de kolom: *Alleen data van de
gemeentes: (gemeente-ids gescheiden door puntkomma)*. De lijst van alle
zaken kan hierop worden gefilterd indien in het blok *where clausule bij
lijst* in de tabel tbsysstandardtable (zie beheerportaal-Nieuw onder
kolom scherm- en tegelbeheer *Tabellen standaardapi*) bij de kaart met
dvcode = *opening_allezaken*) het volgende wordt ingebracht.

.. code:: sql

   case when (select dvalleengemeentes from tbmedewerkers
              where trim(dvcode) = trim(: keyaccount)) is not null
        then instr((select dvalleengemeentes | | chr(59) from tbmedewerkers
                     where trim(dvcode) = trim(: keyaccount)), dvgmntcode | | chr(59)) > 0
        else 1 = 1
        end

Let op: dit kan vertragend werken.

Zelf in te stellen beperking op grond van compartiment
------------------------------------------------------

Zo zou ook de lijst gefilterd kunnen worden op grond van het
compartiment waaraan de inlogger is verbonden. Met onderstaand voorbeeld
worden alleen die zaken getoond die spelen in de gemeentes van dat
compartiment. Indien de inlogger geen lid is van een compartiment worden
alle zaken getoond.

.. code:: sql

   case when (select dnkeycompartiment from tbmedewerkers
              where trim(dvcode) = trim(: keyaccount)) is not null
        then dvgmntcode in (select dvgemeenteid from vwfrmkopcompgem
                            where dnkeycompartiment = (select dnkeycompartiment from tbmedewerkers
                                                       where trim(dvcode) = trim(: keyaccount)))
        else 1 = 1
        end
