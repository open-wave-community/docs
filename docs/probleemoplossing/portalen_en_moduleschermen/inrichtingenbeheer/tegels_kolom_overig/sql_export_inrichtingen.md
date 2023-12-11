# SQL export inrichtingen

## Trigger

De tegel is een trigger voor het tonen van de lijst- en detailsscherm voor het definieren van properties voor het project Data op kaart (zie [Data Op Kaart / Export Inrichtingen als WFS](/docs/instellen_inrichten/data_op_kaart.md)

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Inrichtingenbeheer_
- Kolom: _Overig_
- Vast opschrift: _SQL;export inrichtingen_
- Actie: _getFlexList(SysStandardList,nil,nil,,inrichtingenbeheer_tbexportinrkrt_sql)_
