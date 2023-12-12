# Mislukte_OLO-bijlages

## Trigger

De tegel is een trigger voor een tabel waarin *Ontvangen OLO-Bijlages niet verwerkt* konden worden, met een omschrijving van de reden.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Beheer*
- Kolom: *Medewerkers*
- Kopregel: *Mislukte OLO-Bijlages*
- Actie: *getFlexList(StandardList,nil,nil,vwfrmbadextupload;dnkey,nil,nil,nil,nil,deleteStandardRow)*
