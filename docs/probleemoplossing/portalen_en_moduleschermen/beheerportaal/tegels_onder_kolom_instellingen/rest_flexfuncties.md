# Rest Flexfuncties

## Trigger

De tegel is een trigger naar een lijst van *Flexfuncties* die met een REST API van buiten OpenWave kunnen worden aangesproken.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Beheer*
* Kolom: *Instellingen*
* Kopregel: *Rest Flexfuncties*
* Actie: *getFlexList(SysStandardList,nil,nil,,beheer_restflexfuncties)*

De actie betekent dat in de tabel tbsysstandardtable (beheertegel *Tabellen StandaardApi*) een kaart moet bestaan met de code *beheer_restflexfuncties* waarin de tabel, knoppen en schermen zijn gedefinieerd.
