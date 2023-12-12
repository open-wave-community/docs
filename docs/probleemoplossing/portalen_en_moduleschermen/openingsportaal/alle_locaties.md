# Tegel Alle Locaties

## Trigger

De tegel is een trigger voor de lijst van alle locaties uit OpenWave.

Voor meer informatie over de lijst Alle Locaties(zie [Lijst Alle locaties](/docs/probleemoplossing/module_overstijgende_schermen/zaken_inrichtingen_locaties/locaties.md)). Voor de definitie van de lijst en knoppen en filter: zie beheerportaal _Tabellen standaardapi_ (tbstandardtable.dvcode = _opening_allelocaties_).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Opening_
- Kolom: _Hoofdzaken_
- Kopregel:
- Vast Opschrift:_Alle locaties_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(SysStandardList,nil,nil,G,opening_allelocaties)_
