# Compartimentsrechten

## Trigger

De tegel is een trigger voor een lijst van de gedefinieerde *Compartimentsrechten*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: [Beheerportaal](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal.md)
* Kolom: [Tegels onder kolom Medewerkers](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_medewerkers.md)
* Kopregel: *Compartimentsrechten*
* Actie: *getFlexList(SysStandardList,nil,nil,nil,beheer_compartiment)*
