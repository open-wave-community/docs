# Afhandeling/Besluit (omg/apv/bouw/milieu/gebruik)

## Trigger

De tegel is een trigger voor een tabel van _Resultaat-omschrijvingen van Besluiten_ op een zaak zoals verleend en geweigerd.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Afhandeling_
- Kopregel: _Afhandeling/Besluit;omg/apv/bouw/milieu/gebruik_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbaardbesluit)_
