Thema subthema export inrichtingen
==================================

Trigger
-------

De tegel is een trigger voor het tonen van de lijst- en detailsschermen
voor het definieren van thema's en subthema's voor het project Data op
kaart (zie `Data Op Kaart / Export Inrichtingen als
WFS </docs/instellen_inrichten/data_op_kaart.md>`__

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
-  Kolom: *Overig*
-  Vast opschrift: *Thema/subthema;export inrichtingen*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,,inrichtingenbeheer_tbexportinrkrt_thema)*
