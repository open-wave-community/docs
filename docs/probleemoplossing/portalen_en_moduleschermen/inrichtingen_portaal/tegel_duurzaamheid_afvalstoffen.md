# Tegel Afvalstoffen - Duurzaamheid

## Trigger

De tegel is een trigger voor het tonen van de afvalstofregistraties bij de inrichting. Niet te verwarren met de oude manier van afvalstoffen registreren bij inrichtingen (zie tegel *Afvalstoffen* onder kolom *Bodem*). Bij opvoer van nieuwe afvalstofregistraties is er keuze uit records in codetabel tbmilsrtafvalstof, te vinden in beheer onder tegel *Soort afvalstof*. Deze nieuwe manier van registreren geeft ook de mogelijkheid om per afvalstofregistratie vervoerder(s) aan te geven.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

* indien foutieve queryverwijzing (codering *inrichting_afvalstof*)
* indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
* indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *inrichtingdetail*
* Kolom: *Duurzaamheid*
* Kopregel: *Afvalstoffen*
* Dynamisch tegelopschrift: *getTileContent(inrichting_afvalstof,{id})*
* Actie: *getFlexList(tbmilafvalstoffen,tbmilinrichtingen,{id},nil,V)*
