# Tegel Te Ondertekenen Brieven

## Trigger

De tegel is een trigger voor de doorkieslijst _Te ondertekenen brieven_ gebaseerd op vwfrmcorrespondentie waarvoor geldt dat:

- De verstuurddatum leeg is (ddverstuurd)
- en **Definitief** = Ja
- en **Moet digitaal ondertekend worden** is aangevinkt (dlmoetdigondertekenen = 'T')
- en **Is digitaal ondertekend** is nog leeg (dlisdigondertekend = 'F')
- en de vervaldatum is niet gevuld of groter dan vandaag.

Dubbel klikken op een item van deze lijst leidt tot de detailkaart van het geregistreerde document (tbcorrespondentie).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - en de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

- indien foutieve query verwijzing
- indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Opening_
- Kolom: _Mijn Taken_
- Kopregel
- Vast Opschrift: _Te ondertekenen brieven_
- Dynamisch tegelopschrift: _getTileContent(opening_ondertekenen)_
- Actie: _getFlexList(SysStandardList,nil,nil,G,opening_ondertekenen)_
