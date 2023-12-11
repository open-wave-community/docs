# Energieverbruik categorie

## Trigger

De tegel is een trigger voor de view van mogelijke *Energieverbruik-categorieën*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Inrichtingenbeheer*
* Kolom: *Controle en Maatregelen*
* Vast opschrift: *Energie verbruik;categorie*
* Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_vwfrmmilverbruikcat)*
