# IP-ranges

## Trigger

De tegel is een trigger voor een lijst van gegevens van de *IP-ranges*.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: [Beheerportaal](README.md)
- Kolom: *Brontabellen*
- Kopregel: *IP-ranges*
- Actie: *getFlexList(StandardList,nil,nil,tbipranges;dnkey, nil,nil,nil,nil,insertStandardRow([dviprange;ip-range;string;200][dvomschrijving;omschrijving;string;200]);deleteStandardRow)*
