# Kopieer LegesRekenregels

## Trigger

De tegel is een trigger voor het starten van een wizard waarmee Legesrekenregels (tblegesberekeingen) kunnen worden gekopieerd

Zie: [Kopiëren Legesrekenregels](../programmablokken/kopieren_legesrekenregels.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Operations*
- Kolom: *Overig*
- Vast opschrift: *Kopieer;legesrekenregels*
- Actie: *startwizard(kopieersetLegesBerekeningen)*
