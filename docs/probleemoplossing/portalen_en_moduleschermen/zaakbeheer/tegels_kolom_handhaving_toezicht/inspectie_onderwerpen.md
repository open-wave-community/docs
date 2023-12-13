# Inspectie onderwerpen

## Trigger

De tegel is een trigger voor een lijst met mogelijke _Inspectie onderwerpen_ zoals gronddruk, fundering, geluidsisolatie.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Handhaving- en Toezicht_
- Kopregel: _Inspectieonderwerpen_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbinsponderwerpen)_
