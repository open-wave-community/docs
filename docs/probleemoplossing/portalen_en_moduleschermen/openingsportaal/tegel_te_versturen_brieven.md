# Tegel Te Versturen Brieven

## Trigger

De tegel is een trigger voor de doorkieslijst *Te versturen brieven* gebaseerd op vwfrmcorrespondentie (geregistreerde documenten) waarvoor geldt dat:

  * Verzendwijze per post (dlmoetperpost = T)
  * De verstuurddatum leeg is (ddverstuurd) 
  * EN **Definitief** = Ja 
  * EN **Uitgaand** (dvdocrichting = 'U')
  * EN indien *Moet digitaal ondertekend worden* is aangevinkt (dlmoetdigondertekenen = 'T'), dan moet ook *Is digitaal ondertekend* aangevinkt zijn (dlisdigondertekend = 'F')
  * EN de vervaldatum is niet gevuld of groter dan vandaag.

Dubbel klikken op een item van deze lijst leidt tot de detailkaart van het geregistreerde document (tbcorrespondentie).

  *  De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend 
    * EN de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
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
  * Kolom: *Mijn Taken*
  * Kopregel
  * Vast Opschrift: *Te versturen brieven*
  * Dynamisch tegelopschrift: *getTileContent(opening_versturen)*
  * Actie: *getFlexList(SysStandardList,nil,nil,G,opening_versturen)*

