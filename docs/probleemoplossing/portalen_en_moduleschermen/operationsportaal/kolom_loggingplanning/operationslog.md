# Operationslog

## Trigger

De tegel geeft toegang tot de statuslijst met uitgevoerde export/import operations zoals vernietigen van zaken en documenten, en importeren BAG-gegevens, het exporteren van drop=publicaties etc.

In de kolom *Logging/Planning* wordt zoveel mogelijk getoond wat er mis ging en goed ging tijdens het uitvoeren van een operatie. De meeste operations worden uitgevoerd als runnable. Op de achtergrond wordt de taak uitgevoerd en er is geen interactie met de gebruiker. In de operationslog schrijft de runnable wel data weg, maar dit ziet de gebruiker pas nadat hij/zij de refreshknop gebruikt heeft om de voortgang te kunnen zien:

* Er kan ook een aantal operations gestart zijn door de Taskscheduler (dus automatisch om de zoveel tijd).
* De kolom aantal (geïmporteerde, geëxporteerde, bewerkte items) geeft inzicht in de voortgang.
* De kolom status geeft aan of de operation onder water nog loopt (ben bezig) of dat de taak uitgevoerd is (Klaar of Mislukt.
* De kolom STOP geeft aan of de operatie moedwillig is gestopt (met de stopknop op de detailpagina van de operationlog-regel).

Voor de definitie van de lijst zie beheertegel *Tabellen standaardapi* (tbstandardtable.dvcode = *operations_tboperationslog*).

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Operations*
* Kolom: *Logging/Planning*
* Vast opschrift: *Operationslog*
* Actie: *getFlexList(SysStandardList,nil,nil,nil,operations_tboperationslog)*

## Knoppen lijstscherm

* met de verversknop wordt de actieve regel ververst:  de inhoud van de kolommen stop, aantal en status kan hierdoor veranderen
* met de -knop kan één specifieke regel worden verwijderd (niet doen als een operatie nog loopt!!)
* met de memo-knop kan het logboek van de actieve regel getoond worden,
* met de wizardknop kunnen regels worden verwijderd voor een op te geven datum

## Knoppen detailscherm

* met de stopknop wordt de kolom dlstop aangevinkt. Een aantal operation (met name de runnables) zullen tijdens de uitvoer van de taak geregeld kijken of deze waarde op True is gezet. Zo ja dan wordt de runnable afgebroken
* met de memo-knop kan het logboek van de actieve regel getoond worden,
* met de downloadknop (alleen zichtbaar indien door de operation de kolom dvfilebase64 is gevuld: bijvoorbeeld bij exportFIS) kan de aangemaakte file worden gedownload naar de device van de gebruiker.
