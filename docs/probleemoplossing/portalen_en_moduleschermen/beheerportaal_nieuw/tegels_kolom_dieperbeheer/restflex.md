# Rest Flexfuncties

De tegel is een trigger naar een lijst van _Flexfuncties_ die met een REST API van buiten OpenWave kunnen worden aangesproken.

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

- Portaal: _beheerportaal-NIEUW_
- Kolom: _Dieper Beheer_
- Kopregel: _Rest Flexfuncties_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(SysStandardList,nil,nil,,beheer_restflexfuncties)_

De actie betekent dat in de tabel tbsysstandardtable (beheertegel _Tabellen StandaardApi_) een kaart moet bestaan met de code _beheer_restflexfuncties_ waarin de tabel, knoppen en schermen zijn gedefinieerd.
