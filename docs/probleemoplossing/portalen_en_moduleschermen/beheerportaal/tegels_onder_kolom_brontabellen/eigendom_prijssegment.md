# Eigendom & Prijssegment

## Trigger

De tegel is een trigger voor een lijst met de mogelijkheden voor te kiezen *Eigendom & Prijssegment* die bij een onderdeel/activiteit gekozen kan worden waarbij de eigenschap *Woonmonitor* van toepassing is.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Beheer*
* Kolom: *Brontabellen*
* Vast opschrift: *Eigendom&Prijssegment*
* Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbwmeigendomprijs)*
