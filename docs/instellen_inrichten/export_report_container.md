# Export Report Container

## Doel/toepassing

Doel van deze tabel en bijbehorende operation is om een aantal resultaatsets van rapportages te kunnen exporteren als een zipfile naar een endpoint.

Toepassing is bijvoorbeeld de geschedulede export van rapportages over inspecties/inrichtingen naar de landelijke InspectieView. Dit zijn rapportages die als CSV-file worden opgeslagen en vervolgens in een zipfile worden samengebracht waarna deze zipfile op de ftp-site van InspectieView wordt geplaatst.

## Definitie van de container en rapportages

In _beheerportaal-Nieuw_ onder de kolom _Werkbeheer_ achter de tegel _Container Exportrapportages_ kunnen in de tabel **tbexportcontainer** één of meer groepen van rapportages worden gedefinieerd:

- **Code** (dvcode). Unieke codering waarmee container bijvoorbeeld via operations of taskscheduler kan worden aangeroepen
- **Naam van zipfile** (dvoutputnaam). De naam - inclusief extensie - waaronder de outputfiles van de gekoppelde rapportages uit tbexportscript moeten worden ingepakt in zipfile. De substring %date% in deze naam zal worden vervangen door yymmdd en de substring %datetime% met yyyymmdd:hhmmss
- **Type endpoint**. Type van endpoint bij gevuld dvendpointadres
  - Indien het een FTP Endpoint betreft dan kan gekozen worden uit één van onderstaande mogelijkheden:
  - FTPS-LFTP = Voor FTPS endpoints
  - SFTP-SSHJ = Voor SFTP endpoints
  - anders leeglaten
- **Endpoint voor zipfile** (dvendpointadres). Endpoint waarnaar de zipfile met dvoutputnaam naar toe wordt verplaatst. Indien deze kolom leeg is, dan wordt de zipfile opgeslagen in de kaart van tboperationslog (in de kolom dvfilebase64) Voorbeeld: _mft.webftp.dictu.nl_
- **Login** (dvendpointlogin). De Loginnaam voor het endpointadres
- **Pass** (dvendpointpass). Password voor het endpointadres (wordt gecrypt opgeslagen)
- **Beschrijving** (dvomschrijving). Vrij in te voeren omschrijving
- **Settings** (dvsettings). Middels settings kunnen extra instellingen worden meegegeven die eventueel nodig zijn voor het uploaden naar een SFTP of FTPS server. Vooralsnog kunnen alleen settings worden opgegeven wanneer het type endpoint is ingesteld op: FTPS-LFTP. De instellingen dienen in een JSON formaat te worden opgegeven.

Sterk aangeraden wordt om in het geval van een FTPS server (FTPS-LFTP) al deze instellingen mee te geven.

> [!NOTE] **Voorbeeld:** _{"verifycertificate":false,"forcesslencryption":true,"sslprotectdata":true}_

- De volgende instellingen binnen de JSON zijn mogelijk:

  - verifycertificate = kan de waarde true of false bevatten
  - forcesslencryption = kan de waarde true of false bevatten
  - sslprotectdata = kan de waarde true of false bevatten

- **(Sub)map** (dvmap). De (Sub)map(pen) vanaf het endpoint waarop de zipfile moet worden geplaatst zonder backslashes aan het begin en einde. Voorbeeld: _acc5_ of _acc5/map1_
- **Messagelog** (dlmessaglog). Indien aangevinkt (en de algemene instelling _Sectie: OWB en Item: Messagelog_ is ook aangevinkt) dan zal bij export naar FTP een kaart in de beheertabel tbmessagelog worden aangemaakt.

Bij een container kunnen nu één of meer rapportages worden gedefinieerd in de tabel **tbexportscript**:

- **Volgorde** (dnvolgorde). Volgorde van output binnen de zipfile van Exportcontainer
- **Naam van de outputfile** (dvqueryoutputnaam). De naam van de outputfile - inclusief extensie - die gecreëerd wordt bij dit rapport
- **Omschrijving** (dvomschrijving). Omschrijving van rapport/outputfile
- **OutputType** (dvoutputtype). Type file waarin de resultset van het rapport moet worden omgezet. Vooralsnog alleen CSV
- **Scheidingteken bij CSV** (dvdelimiter). Scheidingsteken tussen de kolommen bij outputtype = CSV bijv. een komma of puntkomma
- **Begrenzingsteken bij CSV** (dvquote). Begrenzingsteken van de waardes in de kolommen bij outputtype = CSV bijvoorbeeld een dubbele quote
- **Eerste regel headerregel** (dlheader). Indien aangevinkt is de eerste regel van de outputfile een headerregel met opsomming van de kolomnamen
- **Nul-waardes ook begrenzen** (dlnullinquote). Indien aangevinkt dan worden null-waardes ook begrensd door het opgegeven begrenzingsteken
- **Telt mee bij aanroep container** (dlqueryactief). Indien NIET aangevinkt wordt deze rapportage dus overgeslagen
- **Query** (dvquery). Het SQL-statement dat de output levert van één of meer regels voor de outputfile.

## Aanroep van de export via Operations

In het portaal _Operations_ onder de kolom _Export_ is een tegel opgenomen **Reportcontainer**. De gebruiker kan een container aanwijzen uit de tabel tbexportcontainer waarna OpenWave de gekoppelde rapportages - vooralsnog dus als CSV- uitrolt onder de bijbehorende outputfilenaam en vervolgens deze set van outputfiles inpakt in de opgegeven zipfile. Dit proces is een runnable. Na het starten van het proces kan de gebruiker verder werken in OpenWave terwijl de runnable loopt. De voortgang wordt gemonitord in de operationslog (tegel _Operationslog_ op het Operationsportaal). Voor elk proces wordt hierin een regel aangemaakt onder de code _exportReportContainer_.

Indien de status van deze regel in operationslog de waarde KLAAR heeft, dan is de runnable blijkbaar klaar met het werk. Dat betekent dat de zipfile is geplaatst op het externe endpoint OF - indien dat endpoint niet is opgegeven - dan is de zipfile als base64 geplaatst in de kaart van de betreffende operationslog-rij. Via de detailkaart van de operationslog-regel kan de zipfile gedownload worden naar de device van de gebruiker.

> [!WARNING]
> **Let op:** de zipfiles kunnen heel groot worden. De opslag van de zipfile in de operationslog is dus echt bedoeld voor kleinere TESTS!

## Aanroep van de export via Taskscheduler

Door een kaart in de tabel tbtaskscheduler op te nemen (portaal _Service centrum_, kolom _Acties_) kan de export ook geschedulded worden gestart.
De aanroep (de taak) is dan exportReportContainer(paramcodering). _Paramcodering_ staat dan voor een dvcode uit de tabel tbexportcontainer. Zie: [Taskscheduler](/instellen_inrichten/taskscheduler.md).

## Meest voorkomende foutmeldingen bij gebruik type endpoint: FTPS-LFTP

Wanneer er gebruik gemaakt wordt van ftps middels: FTPS-LFTP en er iets fout gaat dan kunnen in de Messagelog onder andere de volgende meldingen worden weergegeven:

1. "[...] no progress timeout"
2. "[...] Fatal error: max-retries exceeded (Connection refused)"
    Deze meldingen kunnen meerdere oorzaken hebben maar hebben vrijwel altijd te maken met verkeerde instellingen:

          * De gebruikersnaam of het wachtwoord is verkeerd
          * De endpoint url is incorrect.
          * Er is geen poortnummer gespecificeerd terwijl dit wel moet.
          * Het verkeerde poortnummer is gespecificeerd.
          * Het ip adres van de OpenWave server staat bij het endpoint niet op een whitelist.
          * Er is een certificaat nodig voor het endpoint wat bevraagd wordt maar het certificaat is niet geïnstalleerd op de OpenWave server.

3. "[...] Fatal error: Certificate verification: Not trusted"
    Het certificaat dat het endpoint aanbiedt wordt niet vertrouwd door OpenWave.
    Middels de instelling (Setting): _"verifycertificate:false"_ is deze melding veelal te omzeilen.
    Het is een foutmelding die door OpenWave zelf wordt veroorzaakt.
    Deze controleert of het endpoint wel bekend is in de server configuratie. Dit is eigenlijk altijd een false positive.

> [!WARNING]
> **Let op:** dat het endpoint dat is ingevoerd wel degelijk het juiste is.
> Let er ook op dat de instellingen als volgt zijn ingesteld bij "Settings":
> _"forcesslencryption":true_ en _"sslprotectdata":true_.
