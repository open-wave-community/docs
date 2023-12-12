# Tegel Te Volgen Zaken

## Trigger

De tegel is een trigger voor de doorkieslijst _Te Volgen Zaken_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - en de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Opening_
- Kolom: _Mijn Taken_
- Kopregel:_Te Volgen Zaken_
- Vast Opschrift: _Te Volgen Zaken_
- Dynamisch tegelopschrift
- Actie: _getFlexList(SysStandardList,nil,nil,G,opening_vwfrmtevolgenzaken)_
