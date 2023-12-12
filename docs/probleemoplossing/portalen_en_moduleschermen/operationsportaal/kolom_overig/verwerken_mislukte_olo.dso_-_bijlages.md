# Verwerken Mislukte OLO/DSO bijlages

## Trigger

De tegel is een trigger voor het starten van een wizard waarmee getracht wordt de documenten genoemd in de tabel mislukte OLO bijlages (documenten die mogelijk nog op de temp-map staan) alsnog te plaatsen. De wizard probeert de niet-verwerkte bijlages die mogelijk nog steeds op de temp-map staan (MaxUurUpload!) alsnog te plaatsen. Deze documenten zijn ook zichtbaar via de tegel _up-en downloadmappen_ op het servicecentrum portaal (kolom bron: TussenmapDSPUploadfiles). Dit is een runnable (proces zonder userinterface). Resultaat is te zien in de memo van de betreffende kaart in operationslog (ook in operationsportal).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Operations_
- Kolom: _Overig_
- Vast opschrift: _Verwerken mislukte;OLO/DSO bijlages_
- Actie: _startwizard(verwerkmislukteolobijlages)_
