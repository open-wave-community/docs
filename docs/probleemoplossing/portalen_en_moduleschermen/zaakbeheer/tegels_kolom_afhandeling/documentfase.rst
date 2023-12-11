Documentfase
============

Onder deze tegel kunnen de verschillende *documentfasen* specifiek voor
geregistreerde documenten worden ingesteld.

Trigger
-------

De tegel is een trigger voor een lijst van verschillende soorten
*documentfasen*.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Zaakbeheer*
-  Kolom: *Afhandeling*
-  Kopregel: *Documentfase*
-  Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbdocumentfase)*
