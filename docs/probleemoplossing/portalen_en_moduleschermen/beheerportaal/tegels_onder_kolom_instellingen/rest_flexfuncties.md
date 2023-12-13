# Rest Flexfuncties

## Trigger

De tegel is een trigger naar een lijst van _Flexfuncties_ die met een REST API van buiten OpenWave kunnen worden aangesproken.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Beheer_
- Kolom: _Instellingen_
- Kopregel: _Rest Flexfuncties_
- Actie: _getFlexList(SysStandardList,nil,nil,,beheer_restflexfuncties)_

De actie betekent dat in de tabel tbsysstandardtable (beheertegel _Tabellen StandaardApi_) een kaart moet bestaan met de code _beheer_restflexfuncties_ waarin de tabel, knoppen en schermen zijn gedefinieerd.
