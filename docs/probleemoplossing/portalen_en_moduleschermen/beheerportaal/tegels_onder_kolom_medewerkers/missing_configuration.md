# Ontbrekende configuratie items

## Trigger

De tegel is een trigger voor een tabel waarin het programma tijdens het uitvoeren van grote programmablokken per regel noteert welke *Configuratie-items ontbreken* voor het uitvoeren van het betreffende programmablok. Deze regels worden x aantal dagen bewaard (instelling *Getal1* van *Sectie: Programma* en *Item: Opschonenmissingconfiguration*). Default 30 dagen.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: [Beheerportaal](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaa.md)
* Kolom: [Tegels onder kolom Medewerkers](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_medewerkers.md)
* Kopregel: *Ontbrekende;configuratieitems*
* Actie: *getFlexList(SysStandardList,,,,beheer_tbmissingconfiguration)*
