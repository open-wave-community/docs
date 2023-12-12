# Tegel Mijn Gewijzigde SWF Zaken

## Trigger

De tegel is een trigger voor de doorkieslijst _Mijn Gewijzigde SWF zaken_. Hierin worden alle openstaande, door de geschedulede actie _Synchroniseer Openstaande SWF ruimtes_ gewijzigde SWF zaken in OpenWave getoond waarvoor waarvan de inlogger of de behandelaar is, of in het zaakverantwoordelijk team zit. Wijzigingen kunnen zijn op de SWF ruimte zelf en/of de onderliggende actieverzoeken, ketenpartners en documenten van de SWF ruimte. Voor meer informatie over hoe deze lijst tot stand komt zie pagina: [Synchroniseer Open SWF ruimtes](/probleemoplossing/programmablokken/synchroniseer_open_swfruimtes.md)

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
- Kolom: _Mijn Taken_
- Kopregel:
- Vast Opschrift:_Mijn Gewijzigde SWF Zaken_
- Dynamisch tegelopschrift: _getTileContent(open_mijngewijz_swfzaken)_
- Actie: _getFlexList(SysStandardList,nil,nil,G,opening_vwfrmswfgewijzigdezaken)_
