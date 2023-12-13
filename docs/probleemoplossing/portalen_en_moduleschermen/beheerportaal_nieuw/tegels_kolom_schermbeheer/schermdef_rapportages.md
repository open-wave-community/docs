# Schermkolomdefinitie Rapportages

De tegel is een trigger naar de lijst met _Schermkolomdefinities voor rapportages_ (vwfrmscreencolumns.dnreportkey is not null).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _beheerportaal-NIEUW_
- Kolom: _Scherm- en Tegelbeheer_
- Kopregel: _Schermkolomdefinitie;rapportages_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(SysStandardList,nil,nil,,beheer_tbscreencolumns_rapportage)_
