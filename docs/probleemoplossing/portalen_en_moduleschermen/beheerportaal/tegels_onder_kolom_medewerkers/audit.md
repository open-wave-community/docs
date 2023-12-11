# Audit

## Trigger

De tegel is een trigger voor een lijst van alle in OpenWave verrichte handelingen, zie bij Instellen/Inrichting: [Audit](/docs/instellen_inrichten/audit.md).

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portaltegel](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)

* Portaal: [Beheerportaal](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal.md)
* Kolom: [Tegels onder kolom Medewerkers](/docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_medewerkers.md)
* Kopregel: *Audit*
* Actie: *getFlexList(tbaudit)*
