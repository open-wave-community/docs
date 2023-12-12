# Inspectietrajectsoorten

## Trigger

De tegel is een trigger voor het doorkiesscherm naar naar een tabel met *Soorten inspectietrajecten*.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: [Beheerportaal](/probleemoplossing/portalen_en_moduleschermen/beheerportaa.md)
- Kolom: [Tegels onder kolom Instellingen II](/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_instellingen_ii/README.md)
- Kopregel: *Inspectietrajectsoorten*
- Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbinspaanleiding)*
