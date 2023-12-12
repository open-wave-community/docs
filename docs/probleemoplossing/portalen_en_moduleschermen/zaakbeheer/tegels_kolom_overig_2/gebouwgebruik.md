# Gebouwgebruik

## Trigger

De tegel is een trigger voor een lijst met feitelijk *Gebruik van een gebouw* zoals opslag, atelier, wonen.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Zaakbeheer*
- Kolom: *Overig 2*
- Kopregel: *Gebouwgebruik*
- Actie: *getFlexList(StandardList,nil,nil,tbgebouwgebruik;dnkey,nil,nil,nil,nil,insertStandardRow([dvomschrijving;Gebruik zoals wonen atelier of opslag;string;300]);deleteStandardRow)*
