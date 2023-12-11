Tabellen bij standaard API
==========================

Trigger
-------

De tegel is een trigger voor een lijst met metadata over een andere view
of tabel ten behoeve van flexlist en flexdetail (zie: `Scherminformatie
voor
detailschermen </docs/instellen_inrichten/schermdefinitie/scherminformatie_voor_detailschermen.md>`__).

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd: `Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__

-  Portaal:
   `Beheerportaal </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal.md>`__
-  Kolom: `Tegels onder kolom
   Instellingen </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_instellingen.md>`__
-  Kopregel: *Standaardtabellen*
-  Actie: *getFlexList(StandardList,nil,nil,vwfrmsysstandardtable;dnkey,
   nil,nil,nil,nil,insertStandardRow([dvcode;Geef codering van
   tabel;string;300]);deleteStandardRow)*
