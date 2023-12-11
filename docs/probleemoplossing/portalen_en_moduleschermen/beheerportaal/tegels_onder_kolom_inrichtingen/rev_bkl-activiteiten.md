# REV BKL-activiteiten

## Trigger

De tegel is een trigger voor tonen van het overzicht van de codetabel voor de *Besluit kwaliteit leefomgeving (BKL)* activiteiten en coderingen. Voor de definitie van de lijst zie beheertabel *tabellen standaardapi* (tbsysstandardtable.dvcode = *beheer_tbmilcodebkl)*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
    *deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Beheer*
* Kolom: *Inrichtingen*
* Kopregel: *REV: BKL-activiteiten*
* Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbmilcodebkl)*
