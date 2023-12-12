# Klachternst

## Trigger

De tegel is een trigger voor een lijst met soorten *Ernst van een klacht*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Zaakbeheer*
* Kolom: *Klachten*
* Kopregel: *Klachternst*
* Actie: *getFlexList(StandardList,nil,nil,tbklachternst;dnkey, nil,nil,nil,nil,insertStandardRow([dvcodeernst;Geef unieke codering.;string;200]);deleteStandardRow)*
