# Doublures

## Trigger

De tegel is een trigger voor een lijst van doublures (in tbdoublecheck) ten gevolge van een check vooraf op ingeschoten berichten zoals DSO STAM-bericht. Het kan zijn dat er twee identieke berichten tegelijkertijd naar binnen worden geschoten. Met behulp van deze tabel met een unique constraint op de kolom dvwaarde, wordt dubbele aanmaak voorkomen. OpenWave zorgt dat de tabel in principe na de check weer leeggemaakt wordt. Ook dat kan theoretisch fout gaan. Vandaar de userinterface met een minknop.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Sevicecentrum*
- Kolom: *Logs*
- Kopregel: *Doublures*
- Actie: *getFlexList(SysStandardList,nil,nil,,servicecentrum_tbdoublecheck)*
