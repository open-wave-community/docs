# Zaaktypes APV/Overig

## Trigger

De tegel is een trigger voor het doorkiesscherm naar *Soorten APV/overige vergunningen*.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ( [Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md) ):

- Portaal: [Beheerportaal](README.md)
- Kolom: [Tegels onder kolom Instellingen II](tegels_onder_kolom_instellingen_ii/README.md)
- Kopregel: *Zaaktypes apv/overig*
- Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_vwfrmsoortovverg)*
