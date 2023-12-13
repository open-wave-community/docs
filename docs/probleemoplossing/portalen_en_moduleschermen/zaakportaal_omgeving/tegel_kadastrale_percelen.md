# Tegel Projectlocaties/Kadastrale Percelen

Zie voor toepassing: [Onbekende locatieadressen](../../../instellen_inrichten/onbekende_locatieadressen.md)

## Trigger

De tegel is een trigger voor het lijstscherm van *Projectlocaties/Kadastrale percelen* bij een omgevingszaak.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *omgeving_zaakkadperc*)
  * indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: [Zaakportaal Omgeving](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving.md)
  * Kolom: *Overig*
  * Kopregel: *Kadastrale percelen;Projectlocaties*
  * Dynamisch tegelopschrift: *getTileContent(omgeving_zaakkadperc,{id})*
  * Actie: *getFlexList(tbzaakkadperc,tbomgvergunning,{id},nil,W)*

