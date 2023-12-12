# Combinatie product, klant, werkpakket

## Trigger

De tegel is een trigger voor een lijst van reëel bestaande _Combinaties van producten, klanten en werkpakketten_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ( [Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md) ):

- Portaal: [Beheerportaal](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/README.md)
- Kolom: [Tegels onder kolom Instellingen II](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_instellingen_ii/README.md)
- Kopregel: _Combinatie producten;klanten en werkpakketten_
- Actie: _getFlexList(SysStandardList,nil,nil,,beheer_tbprodwkpklant)_
