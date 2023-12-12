# Tegel MBA

## Trigger

De tegel is een trigger voor een lijst van alle *MBA-coderingen*: Milieu Belastende Activiteiten. Voor de definitie van de lijst zie beheertabel *tabellen standaardapi* (tbsysstandardtable.dvcode = *inrichting_tbmilmba)*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
    *deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

* indien foutieve queryverwijzing (codering *inrichting_mba*)
* indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
* indien inlogger geen recht heeft om query uit te voeren.

## Bijzonderheden

De onderliggende tabel (tbmilmba) bevat de kolom dlhoofdmba (T of F). De OpenWave programmatuur zorgt ervoor dat slechts één MBA-activiteit bij een inrichting de waarde T kan hebben. Indien een MBA-activiteit wordt bestempeld als hoofdactiviteit, worden bij alle overige MBA-kaarten bij dezelfde inrichting de dlhoofdmba op F gezet. Bij het inserten van een nieuwe MBA activiteit krijgt deze automatisch de waarde dlhoofdmba = T mits er geen andere kaarten zijn met T.

Zie lemma [Milieu  Belastende Activiteiten](/docs/instellen_inrichten/milieu_belastende_activiteiten_mba.md).

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *inrichtingdetail*
* Kolom: *Wat gebeurt er*
* Kopregel: *MBA*
* Dynamisch tegelopschrift: *getTileContent(inrichting_mba,{id})*
* Actie: *getFlexList(SysStandardList,nil,nil,nil,inrichting_tbmilmba)*
