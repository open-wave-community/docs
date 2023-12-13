# Ontbrekende configuratie items

## Trigger

De tegel is een trigger voor een tabel waarin het programma tijdens het uitvoeren van grote programmablokken per regel noteert welke _Configuratie-items ontbreken_ voor het uitvoeren van het betreffende programmablok. Deze regels worden x aantal dagen bewaard (instelling _Getal1_ van _Sectie: Programma_ en _Item: Opschonenmissingconfiguration_). Default 30 dagen.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: [Beheerportaal](../../portalen_en_moduleschermen/beheerportaal.md)
- Kolom: [Tegels onder kolom Medewerkers](README.md)
- Kopregel: _Ontbrekende;configuratieitems_
- Actie: _getFlexList(SysStandardList,,,,beheer_tbmissingconfiguration)_
