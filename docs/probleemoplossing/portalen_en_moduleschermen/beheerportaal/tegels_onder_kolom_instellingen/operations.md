# Operations

## Trigger

De tegel is een trigger naar het Portaal _Operations_. Daarin bevinden zich tegels waarmee zogenaamde bulk-operaties op de onderliggende database kunnen worden uitgevoerd zoals: **Importeren**, **Exporteren** en **Vernietigen**.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Beheer_
- Kolom: _Instellingen_
- Kopregel: _Operations_
- Actie: _opentabpage(#operations)_
