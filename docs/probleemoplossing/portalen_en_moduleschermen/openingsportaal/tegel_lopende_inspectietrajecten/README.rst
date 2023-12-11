Tegel Lopende Inspectietrajecten
================================

Trigger
-------

De tegel is een trigger voor de doorkieslijst *Lopende
inspectietrajecten*.

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
-  Kolom: *Deelzaken*
-  Kopregel:*Lopende;inspectietrajecten*
-  Vast Opschrift:
-  Dynamisch tegelopschrift
-  Actie: *getFlexList(OpenInspTrajecten,nil,nil,0,nil)* of
   *getFlexList(OpenInspTrajecten,nil,nil,3,nil)*

De parameter 0 geeft aan dat alle lopende inspectietrajecten moeten
worden getoond, waarbij:

-  indien de inlogger lid is van een
   `compartiment </docs/instellen_inrichten/compartimenten.md>`__,
   alleen die inspectietrajecten getoond worden die horen bij zaken die
   spelen in een gemeente die onderdeel is van dat compartiment (dus ook
   bij zaaktypes die niet onder het compartiment vallen)
-  indien de inlogger GEEN lid is van een compartiment dan is er geen
   compartimentsrestrictie.

De parameter 3 geeft aan dat alle lopende inspectietrajecten moeten
worden getoond, waarbij:

-  indien de inlogger lid is van een compartiment, alleen die
   inspectietrajecten worden getoond die horen bij zaken die vallen
   onder het compartiment (dus combinatie gemeente en zaaktype zijn
   gedefinieerd in dat compartiment en waarbij in de
   compartimentsdefinitie bij de zaak *inclusief inspectie* is
   aangevinkt)
-  indien de inlogger GEEN lid is van een compartiment, alleen die
   inspectietrajecten worden getoond die horen bij zaken waarvan de
   combinatie gemeente en zaaktype en *inclusief inspectie* in geen
   enkel compartiment voorkomt.
