# Inrichtingenbeheer

Deze tegel verwijst door naar portaal **Inrichtingenbeheer**. Dit portaal bevat alle beheertegels te maken met beheren van inrichtingen/locatie dossiers en onderliggende dochtertabellen in OpenWave.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: docs:[Beheerportaal - NIEUW](/probleemoplossing/portalen_en_moduleschermen/beheerportaal_nieuw/README.md)
- Kolom: [Tegels onder kolom Overige beheerportalen](/probleemoplossing/portalen_en_moduleschermen/beheerportaal_nieuw/tegels_kolom_overige_portalen/README.md)
- Kopregel: _Inrichtingenbeheer_
- Dynamisch tegelopschrift:
- Actie: _opentabpage(#inrichtingenbeheer)_
