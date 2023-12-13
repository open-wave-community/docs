# Tabellen bij standaard API

## Trigger

De tegel is een trigger voor een lijst met metadata over een andere view of tabel ten behoeve van flexlist en flexdetail (zie: [Scherminformatie voor detailschermen](../../../../instellen_inrichten/schermdefinitie/scherminformatie_voor_detailschermen.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd: [Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)

- Portaal: [Beheerportaal](README.md)
- Kolom: [Tegels onder kolom Instellingen](tegels_onder_kolom_instellingen/README.md)
- Kopregel: _Standaardtabellen_
- Actie: _getFlexList(StandardList,nil,nil,vwfrmsysstandardtable;dnkey, nil,nil,nil,nil,insertStandardRow([dvcode;Geef codering van tabel;string;300]);deleteStandardRow)_
