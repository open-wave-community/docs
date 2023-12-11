# Soorten bezwaar/beroep

## Trigger

De tegel is een trigger voor het doorkiesscherm naar naar een tabel met *Soorten bezwaar/beroep*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Zaakbeheer*
* Kolom: *Handhaving- en Toezicht*
* Kopregel: *Soorten bezwaar/beroep*
* Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbsoortbezwaar)*
