# Erkende Maatregelen;te verwerken;RVO inrichtingids

Zie: [Erkende Maatregelen](/docs/probleemoplossing/programmablokken/erkende_maatregelen.md).

## Trigger

De tegel geeft toegang tot de lijst met inrichtingen waarvan de gemelde maatregelen nog verwerkt moeten worden tot een melding in de module omgevingszaken.

Voor de definitie van de lijst zie beheertegel *Tabellen standaardapi* (tbstandardtable.dvcode = *beheer_tbekteverwerkeninr*).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Operations*
- Kolom: *Import*
- Kopregel: *Erkende Maatregelen;te verwerken;RVO inrichtingids*
- Actie: *getFlexList(SysStandardList,nil,nil,,beheer_tbekteverwerkeninr)*
