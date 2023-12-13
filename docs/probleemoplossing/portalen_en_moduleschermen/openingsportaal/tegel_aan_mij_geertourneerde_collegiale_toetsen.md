# Tegel Aan mijn geretourneerde collegiale toetsen

## Trigger

De tegel is een trigger voor de doorkieslijst _Aan mij geretourneerde collegiale toetsen_ gebaseerd op vwfrmcorrespcollegtoets waarvoor geldt dat:

- de toetsdatum gevuld is(dddatumgetoetst)
- en de aanvrager (dvcodemwaanvrager) is gevuld met de inlogger
- en de kolom _Gezien_ is niet aangevinkt (dlgezien heeft de waarde 'F')
- en het bovenliggende document is nog niet verstuurd en niet digitaal ondertekend
- en de vervaldatum van het geregistreerde document is niet gevuld of groter dan vandaag.

Dubbel klikken op een item van deze lijst leidt tot de detailkaart van het geregistreerde document (tbcorrespondentie) waar de collegiale toets bij hoort.

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
- Vast Opschrift: _Aan mij geretourneerde;collegiale toetsen_
- Dynamisch tegelopschrift: _getTileContent(opening_mretct)_
- Actie: _getFlexList(SysStandardList,nil,nil,G,opening_mretct)_
