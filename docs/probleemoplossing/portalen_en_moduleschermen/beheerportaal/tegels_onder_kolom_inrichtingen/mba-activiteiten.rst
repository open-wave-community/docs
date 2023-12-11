MBA-Activiteiten
================

Trigger
-------

De tegel is een trigger voor tonen van het overzicht van de codetabel
*Milieu Belastende activiteiten*. Voor de definitie van de lijst zie
beheertabel *tabellen standaardapi* (tbsysstandardtable.dvcode =
*beheer_tbmilcodemba)*.

-  De tegel is alleen zichtbaar voor inlogger wanneer: \* deze aan
   hem/haar is toegekend \* de evaluatie van het *SQL statement
   onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0
   oplevert.
-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Beheer*
-  Kolom: *Inrichtingen*
-  Kopregel: *MBA-coderingen*
-  Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbmilcodemba)*
