# Tegel Mijn Openstaande Bezwaar/beroepszaken

## Trigger

De tegel is een trigger voor de doorkieslijst *Mijn Openstaande Bezwaar/beroepszaken*.

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

  * indien foutieve queryverwijzing  
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

### Tegeldefinitie (Standaard)

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *Opening*
  * Kolom: *Mijn Taken*
  * Kopregel:*Mijn openstaande;Bezwaar/beroep;zaken*
  * Vast Opschrift:
  * Dynamisch tegelopschrift
  * Actie: *getFlexList(OpenBezwaarBeroepZaken,nil,nil,1,nil)*

## Tegeldefinitie Vaarwegzaken

Indien men geen reguliere zaken behandeld maar alleen Vaarwegzaken, kan men de vaarweggegevens tonen door de tegel als volgt te definiëren:

  * Portaal: *Opening*
  * Kolom: *Mijn Taken*
  * Kopregel:*Mijn openstaande;Bezwaar/beroep;zaken*
  * Vast Opschrift:
  * Dynamisch tegelopschrift
  * Actie: *getFlexList(OpenBezwaarBeroepZaken,nil,nil,1,nil,nil,nil,nil,1)*

