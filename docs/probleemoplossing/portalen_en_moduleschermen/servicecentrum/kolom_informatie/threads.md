# Threads

## Trigger

De tegel is een trigger voor een lijst van alle *Threads*: alle op de achtergrond draaiende processen.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

### Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Servicecentrum*
* Kolom: *Informatie*
* Kopregel: *Threads*
* Actie: *getFlexList(Threads,nil,nil,0)*

Indien de 4e parameter van de aanroep getflexlist de waarde 0 heeft (zoals default uitgeleverd en in bovenstaand voorbeeld) dan worden de threads  gefilterd op thread.getName() begint met ‘Openwave-Callable-‘ of ‘Openwave-Runnable-‘. Dat zijn de processen in openwave aangeroepen vanuit taskscheduler (‘Openwave-Callable-‘) of andere tijdrovende open-wave processen (‘Openwave-Runnable-‘), zoals im- en exportfuncties, die op de achtergrond hun taak uitoefenen. Indien de 4e parameter van de aanroep getflexlist de waarde 1 heeft, dan worden alle processen zichtbaar.
