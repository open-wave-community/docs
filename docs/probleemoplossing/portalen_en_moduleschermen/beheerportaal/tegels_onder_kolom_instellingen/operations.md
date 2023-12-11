# Operations

## Trigger

De tegel is een trigger naar het Portaal *Operations*. Daarin bevinden zich tegels waarmee zogenaamde bulk-operaties op de onderliggende database kunnen worden uitgevoerd zoals: **Importeren**, **Exporteren** en **Vernietigen**.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Beheer*
* Kolom: *Instellingen*
* Kopregel: *Operations*
* Actie: *opentabpage(#operations)*
