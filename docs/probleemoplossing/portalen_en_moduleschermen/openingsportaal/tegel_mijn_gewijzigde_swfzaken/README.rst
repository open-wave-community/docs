Tegel Mijn Gewijzigde SWF Zaken
===============================

Trigger
-------

De tegel is een trigger voor de doorkieslijst *Mijn Gewijzigde SWF
zaken*. Hierin worden alle openstaande, door de geschedulede actie
*Synchroniseer Openstaande SWF ruimtes* gewijzigde SWF zaken in OpenWave
getoond waarvoor waarvan de inlogger of de behandelaar is, of in het
zaakverantwoordelijk team zit. Wijzigingen kunnen zijn op de SWF ruimte
zelf en/of de onderliggende actieverzoeken, ketenpartners en documenten
van de SWF ruimte. Voor meer informatie over hoe deze lijst tot stand
komt zie pagina: `Synchroniseer Open SWF
ruimtes </docs/probleemoplossing/programmablokken/synchroniseer_open_swfruimtes.md>`__

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
-  Kolom: *Mijn Taken*
-  Kopregel:
-  Vast Opschrift:*Mijn Gewijzigde SWF Zaken*
-  Dynamisch tegelopschrift: *getTileContent(open_mijngewijz_swfzaken)*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,G,opening_vwfrmswfgewijzigdezaken)*
