# Horeca aardbesluit

## Trigger

De tegel is een trigger voor een lijst van statussen en omschrijvingen van _Besluiten op een horeca-vergunningsaanvraag_ zoals verleend, geweigerd.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Beheer_
- Kolom: _Brontabellen_
- Kopregel: _Horeca aardbesluit_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbhoraardbesluit)_
