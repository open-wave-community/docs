# Vervallen Stal/Dier Richtlijn

## Trigger

De tegel is een trigger voor het starten van een wizard waarmee u alle kaarten met eenzelfde richtlijn voorziet van een vervaldatum.

Het gaat hier om de richtlijn die hoort bij de combinatie stal en dier.

* De tegel is alleen zichtbaar voor inlogger wanneer:
    *deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Operations*
* Kolom: *Overig*
* Vast opschrift: *Vervallen;Stal/Dier Richtlijn*
* Actie: *startWizard(vervallenstaldierrichtlijn)*
