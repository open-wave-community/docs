# Schermkolomdefinitie rapportages

## Trigger

De tegel is een trigger naar de lijst met *Schermkolomdefinities voor rapportages* (vwfrmscreencolumns.dnreportkey is not null).

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Beheer*
* Kolom: *Instellingen*
* Kopregel: *Schermkolomdefinitie rapportages*
* Actie: *getFlexList(SysStandardList,nil,nil,,beheer_tbscreencolumns_rapportage)*
