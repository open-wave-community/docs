# Tegel Alle Zaken (Compartiment)

## Trigger

De tegel is een trigger voor de lijst van alle afgehandelde of openstaande zaken uit OpenWave die zich afspelen in de gemeentes behorende bij het compartiment van de inlogger.

Voor meer informatie over de lijst Alle zaken (zie [Lijst Alle zaken](/docs/probleemoplossing/module_overstijgende_schermen/zaken_inrichtingen_locaties/zaken.md)). Voor de definitie van de lijst en knoppen en filter: zie beheerportaal-Nieuw *Tabellen standaardapi* (tbstandardtable.dvcode = *opening_allezakencompartiment*).

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

  * indien foutieve query verwijzing 
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *Opening*
  * Kolom: *Hoofdzaken*
  * Kopregel:
  * Vast Opschrift:*Alle zaken;(Compartiment)*
  * Dynamisch tegelopschrift:
  * Actie: *getFlexList(SysStandardList,nil,nil,G,opening_allezakencompartiment)*

