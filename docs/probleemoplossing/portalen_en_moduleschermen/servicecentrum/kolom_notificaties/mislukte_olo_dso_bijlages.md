# Mislukte_OLO/DSO-bijlages

## Trigger

De tegel is een trigger voor de weergave van de tabel met mislukte OLO/DSO-Bijlages (tbbadextupload). De bijlages die niet automatisch geplaatst konden worden krijgen in deze tabel een regel met een omschrijving van de reden.

Zie ook de tegelbeschrijving op het portaal operations: [Verwerken Mislukte OLO/DSO bijlages](/probleemoplossing/portalen_en_moduleschermen/operationsportaal/kolom_overig/verwerken_mislukte_olo.dso_-_bijlages.md) om de lijst op te schonen en nog een poging tot verwerking te doen.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Servicecentrum_
- Kolom: \*Notificaties/
- Kopregel: _Mislukte OLO/DSO;bijlages_
- Actie: _getFlexList(StandardList,nil,nil,vwfrmbadextupload;dnkey,nil,nil,nil,nil,deleteStandardRow)_
