# Vernietigingslijst

Zie ook [Vernietigingslijst](/probleemoplossing/programmablokken/vernietigingslijst.md).

## Trigger

De tegel is een trigger voor het openen van een lijst van _Te vernietigen zaken_ op grond van bewaartermijnen. Voor de definitie van de lijst zie beheertabel _Tabellen standaardapi_ (tbsysstandardtable.dvcode = _beheer_tevernietigen)_. Vanuit de lijst kan een nieuwe lijst worden samengesteld en/of het vernietigingsproces in gang worden gezet.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Operations_
- Kolom: _Overig_
- Vast opschrift: _Vernietigingslijst_
- Actie: _getFlexList(SysStandardList,nil,nil,,beheer_tevernietigen)_
