# Vernietigingslijst

Zie ook [Vernietigingslijst](/docs/probleemoplossing/programmablokken/vernietigingslijst.md).

## Trigger

De tegel is een trigger voor het openen van een lijst van *Te vernietigen zaken* op grond van bewaartermijnen. Voor de definitie van de lijst zie beheertabel *Tabellen standaardapi* (tbsysstandardtable.dvcode = *beheer_tevernietigen)*. Vanuit de lijst kan een nieuwe lijst worden samengesteld en/of het vernietigingsproces in gang worden gezet.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Operations*
* Kolom: *Overig*
* Vast opschrift: *Vernietigingslijst*
* Actie: *getFlexList(SysStandardList,nil,nil,,beheer_tevernietigen)*
