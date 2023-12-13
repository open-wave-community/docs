# Tegel Te Versturen Brieven

## Trigger

De tegel is een trigger voor de doorkieslijst _Te versturen brieven_ gebaseerd op vwfrmcorrespondentie (geregistreerde documenten) waarvoor geldt dat:

- Verzendwijze per post (dlmoetperpost = T)
- De verstuurddatum leeg is (ddverstuurd)
- en **Definitief** = Ja
- en **Uitgaand** (dvdocrichting = 'U')
- en indien _Moet digitaal ondertekend worden_ is aangevinkt (dlmoetdigondertekenen = 'T'), dan moet ook _Is digitaal ondertekend_ aangevinkt zijn (dlisdigondertekend = 'F')
- en de vervaldatum is niet gevuld of groter dan vandaag.

Dubbel klikken op een item van deze lijst leidt tot de detailkaart van het geregistreerde document (tbcorrespondentie).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  \*deze aan hem/haar is toegekend
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
- Vast Opschrift: _Te versturen brieven_
- Dynamisch tegelopschrift: _getTileContent(opening_versturen)_
- Actie: _getFlexList(SysStandardList,nil,nil,G,opening_versturen)_
