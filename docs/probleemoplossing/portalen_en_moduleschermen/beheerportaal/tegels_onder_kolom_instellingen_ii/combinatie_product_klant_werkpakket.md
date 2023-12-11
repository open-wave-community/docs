# Combinatie product, klant, werkpakket

## Trigger

De tegel is een trigger voor een lijst van reëel bestaande *Combinaties van producten, klanten en werkpakketten*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ( [Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md) ):

* Portaal: [Beheerportaal](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal.md)
* Kolom: [Tegels onder kolom Instellingen II](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_instellingen_ii.md)
* Kopregel: *Combinatie producten;klanten en werkpakketten*
* Actie: *getFlexList(SysStandardList,nil,nil,,beheer_tbprodwkpklant)*
