REV Kwetsbare locaties gebouwen
===============================

Trigger
-------

De tegel is een trigger voor tonen van het overzicht van de codetabel
voor de *REV kwetsbare locaties en gebouwen*. Voor de definitie van de
lijst zie beheertabel *tabellen standaardapi* (tbsysstandardtable.dvcode
= *beheer_tbrevkwetsbaargebouwlocatie)*.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Inrichtingenbeheer*
-  Kolom: *Registratie en Veiligheid*
-  Kopregel: *REV;Kwetsbare;locaties gebouwen*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,G,beheer_tbrevkwetsbaargebouwlocatie)*
