# Tegel Locaties

## Trigger

De tegel is een trigger voor het openen van de lijst- en detailschermen van _gemeentes, woonplaatsen per gemeente, openbare ruimtes per woonplaats en adressen per openbare ruimte_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

- indien foutieve query verwijzing
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Opening_
- Kolom: _Diversen_
- Kopregel:
- Vast Opschrift:_Locaties_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(tb33gemeente)_

## Gerelateerde Pagina's

- [Detailscherm gemeente/ lijst woonplaatsen](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_locaties/detail_gemeente_met_lijst_woonplaatsen.md)
- [Detailscherm openbare ruimte/ lijst locatie-adressen](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_locaties/detail_openbare_ruimte_met_lijst_locatie-adressen.md)
- [Detailscherm woonplaats/ lijst openbare ruimtes](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_locaties/detail_woonplaats_met_lijst_openbare_ruimtes.md)
- [Lijst Gemeentes](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_locaties/lijst_gemeentes.md)
