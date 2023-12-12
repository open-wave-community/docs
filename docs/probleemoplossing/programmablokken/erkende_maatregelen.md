# Erkende Maatregelen

Alle ondernemingen in Nederland met meer dan x energieverbruik moeten energiebesparende – erkende - maatregelen nemen. De bevoegd gezagen of hun uitvoerende instanties moeten hierop gaan inspecteren.
De ondernemingen moeten hun maatregelen eens per 4 jaar melden aan de RVO, maar het mag vaker.

De maatregelen worden in twee etappes opgehaald uit een webservice van het RVO:

- door het opvragen van een lijst van inrichtingen die sinds een bepaalde datum maatregelen hebben gemeld bij het RVO
- door per inrichting de maatregelen op te vragen en deze te verwerken tot een nieuwe melding bij de omgevingszaken, waarbij de pdf met het erkendemaatregelen-rapport wordt opgeslagen op de daartoe bedoelde plaats (fileserver of DMS).

Dit gebeurt vanuit het operationsportaal (te bereiken via het beheerportaal-Nieuw) dus de gebruiker moet applicatiebeheerrechten hebben (tbmedewerkers.dnbeheer >= 99).

## Coderingstabellen Erkende Maatregelen

In het beheerportaal _Inrichtingenbeheer_ zijn onder de kolom _Controle en Maatregelen_ twee tegel met (gevulde) hulptabellen:

- **Erkende Maatregelen Rubricering**. Deze tegel geeft toegang tot een tabel met coderingen en omschrijvingen over de status van een inrichting zoals: R1!!-G: 50-75% van de maatregelen(nog) niet uitgevoerd; energieverbruik Groot.
  - Scherminformatie: zie beheertegel _Tabellen StandaardApi_, code: _beheer_tbekrubricering_.
- **Erkende Maatregelen Bedrijfstakken Soorten maatregelen**. Deze tegel geeft toegang tot een tabel met bedrijfstakken. Een bedrijfstak geeft toegang tot een tabel maatregelen. Per bedrijfstak zijn de mogelijke maatregelsoorten gecodeerd en beschreven. Zo kent de bedrijfstak Verf en drukinkt (15) o.a. de maatregel 15-FA1: Energiezuinige warmteopwekking toepassen bij de activiteit: In werking hebben van een stookinstallatie (emissies naar de lucht).
  - Scherminformatie: zie beheertegel _Tabellen StandaardApi_:
  - code: _beheer_tbekbedrijfstak_
  - code: _beheer_tbeksoortmaatregel_

Zie [https://www.rvo.nl/onderwerpen/duurzaam-ondernemen/energie-besparen/informatieplicht-energiebesparing/bedrijven-en-instellingen/erkende-maatregelenlijsten](https://www.rvo.nl/onderwerpen/duurzaam-ondernemen/energie-besparen/informatieplicht-energiebesparing/bedrijven-en-instellingen/erkende-maatregelenlijsten.md).

## Ophalen Inrichtingen die Maatregelen hebben gemeld

In het operationsportaal bestaat onder de kolom _Import_ de tegel _Erkende Maatregelen te verwerken RVO inrichting-ids_. Deze tegel geeft toegang tot de lijst met inrichtingen waarvan de gemelde maatregelen nog verwerkt moeten worden tot een melding in de module omgevingszaken.

- Scherminformatie: zie beheertegel _Tabellen StandaardApi_, code: _beheer_tbekteverwerkeninr_.

Indien de RVO-id bekend is in OpenWave (tbmilinrichtingen.dniderkmaatr) dan zal de OpenWave inrichtingnaam en adres zichtbaar worden. De datum/tijd kolom slaat op het moment dat de inrichting is opgehaald met SOAP-request vraagLijstInrichtingIDs. Nieuwe inrichtingen kunnen altijd worden opgehaald met **de wizardknop linksonder**. De volgende instellingen zijn daarbij verplicht:

- **Datum Vanaf**: Deze wordt opgehaald uit de kolom _Tekst_ van de instelling bij _Sectie: ErkendeMaatregelen Item: DatumVanaf_ in het format yyyy-MM-ddTHH:mm:ss. Met deze instelling wordt opgegeven vanaf welke datum het programma de opvraag moet doen (gevraagd wordt naar de inrichtingen die vanaf die datum maatregelen hebben gerapporteerd). De eerste keer zal de applicatiebeheerder deze moeten invoeren. Na een geslaagde ophaalactie zal OpenWave zelf de datum elke keer verzetten. Bij het verwerken van de maatregelen tot meldingen bij omgevingszaken volgt altijd een extra controle op het reeds bestaan van de melding c.q. maatregel, zodat doublures worden voorkomen
- **Endpoint RVO**. De kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: Endpoint_ voor het SOAP-request vraagLijstInrichtingIDs
- **OIN van bevoegd gezag/uitvoerende instantie**. De kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: OIN_ (gevraagd wordt naar de inrichtingen die vanaf die datum maatregelen hebben gerapporteerd, waarvoor het OIN-nummer bevoegd is)
- **Naam van OIN**. Kolom _Info_ bij _Sectie: ErkendeMaatregelen Item: OIN_
- **CertificaatNaam**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: ClientCertificaatNaam_. Het certificaat (aan te vragen bij RVO) wordt geplaatst bij de OpenWave installatie
- **CertificaatPass**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: ClientCertificaatPassword_
- **CertificaatType**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: CertificaatType_ (default PKCS12)
- **CharSet in soapbericht**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: Charset_ (default UTF-8)
- **Mapnaam voor opslag PDF op fileserver of cmis**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: DocMapIncDocroot_

Het uitgaande vraagbericht vraagLijstInrichtingIDs en het antwoord worden gelogd in de messagelog indien:

- en instelling _Sectie: ErkendeMaatregelen en Item: Messagelog_ aangevinkt staat
- en de instelling _Sectie: OWB en Item: MessageLog_ aangevinkt staat.

Bij succesvolle afronding zal OpenWave zelf de kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: DatumVanaf_ vervangen met datum en tijd van de afleverdatum van het antwoordbericht.

## Ophalen Inrichtingen die Maatregelen hebben gemeld

Door het dubbel klikken op een regel van bovenstaande lijst met inrichtingen die één of meer onverwerkte maatregelen hebben gerapporteerd, zal het programma per inrichting een SOAP request vraagGegevensIndividueleInrichting naar het RVO doen om de maatregelen van één inrichting op te halen en te verwerken tot een melding in de module omgevingszaken.

Met het SOAP Request_vraagGegevensIndividueleInrichting worden de maatregelen van die inrichting opgevraagd.
Met het antwoord wordt een nieuwe meldingszaak gemaakt in de tabel tbomgvergunningen met als zaaktype Erkende Maatregel (de betreffende dnkey van het Omgevingszaakttype ErkendeMaatregel staat in _Getal1_ van _Sectie: ErkendeMaatregelen Item: DnkeyVanOmgevingsZaakType_).

De omgevingszaak wordt gekoppeld aan een bestaande inrichting (indien deze niet bestaat wordt deze aangemaakt). Bij de inrichting zal een nieuwe energiekaart worden aangemaakt.

De maatregelen die horen bij de melding komen in de nieuwe tabel tbomgerkmaatreg die gekoppeld is aan de zojuist aangemaakte omgevingszaak. Deze tegel is zichtbaar indien in de bovenliggende omgevingszaak de (onzichtbare) kolom dverkmaatrrappid gevuld is met een rapportage-id van het RVO. Dit gebeurt automatisch. De tegel is zodoende alleen zichtbaar bij omgevingszaken van het type melding Erkende Maatregelen. De rapportage-id is ook zichtbaar in de aanvraagnaam.

- Scherminformatie: zie beheertegel _Tabellen StandaardApi_, code: _omgeving_tbomgerkmaatreg_.

De melding zelf is gecodeerd op rubricering zichtbaar in dvaanvraagoms (het blok toelichting). De maatregelen zijn gecodeerd naar bedrijfstak en soort-maatregel (zie hierboven het kopje codetabellen). Indien alzo is ingesteld dan zal van de melding een Zaak in het externe zaaksysteem gemaakt worden. Bij de melding hoort een pdf-document. Deze zal worden opgeslagen in het DMS (indien aanwezig) of anders op fileserver. De volgende instellingen zijn daarbij verplicht:

- **Endpoint RVO**. De kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: Endpoint_ voor het SOAP-request vraagGegevensIndividueleInrichting
- **OIN van bevoegd gezag/uitvoerende instantie**. De kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: OIN_
- **Naam van OIN**. Kolom _Info_ bij _Sectie: ErkendeMaatregelen Item: OIN_
- **CertificaatNaam**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: ClientCertificaatNaam_. Het certificaat (aan te vragen bij RVO) wordt geplaatst bij de OpenWave installatie
- **CertificaatPass**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: ClientCertificaatPassword_
- **CertificaatType**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: ClientCertificaatType_ (default PKCS12)
- **CharSet in soapbericht**. Kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: Charset_ (default UTF-8)
- **De ID (dnkey) van het Omgevingszaaktype**. Kolom _Getal1_ bij _Sectie: ErkendeMaatregelen Item: DnkeyVanOmgevingsZaakType_. _Getal1_ moet verwijzen naar een niet vervallen dnkey van een kaart uit tbsoortomgverg (beheertabel _zaaktypes omgeving_) van type melding en met een gevulde defaultbehandelaar en die bedoeld is voor de Erkende Maatregelen
- **DummyLocatie**. _Getal2_ bij Sectie: _Koppeling ZAAK Item: DummyLokatiePerceelkey_ met gevuld zijn met en dnkey die verwijst naar een kaart in tbperceeladressen met de functie Onbekend Adres
- **AdresRol Erk Maatr. contact**. De kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: RolContactadres_ met gevuld zijn met een codering die verwijst naar een bestaande codering in tbadressoort (beheerportaal-Nieuw) die gebruikt gaat worden voor het toevoegen van de contactpersoon bij een set erkende maatregelen.
- **Document Registreren**. Indien de instelling _Sectie: ErkendeMaatregelen Item: DocRegistreren_ aangevinkt is zal ook een kaart in geregistreerde documenten (tbcorrespondentie) worden aangemaakt bij het plaatsen van de PDF
- **Documenttype**. De kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: Documenttype_ moet gevuld zijn met het documenttype waaronder het PDF-document moeten worden opgeslagen in het DMS / geregistreerde documenten
- **DocumentStatus**. De kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: Documentstatus_ moet gevuld zijn met het documenttype waaronder het PDF-document moeten worden opgeslagen in het DMS / geregistreerde documenten
- **DocumentVertrouwelijkheid**. De kolom _Tekst_ bij _Sectie: ErkendeMaatregelen Item: DocVertrouwelijkheid_ moet gevuld zijn met een waarde die voorkomt in de kolom omschrijving van de tabel tbvertrouwelijkheid (beheerportaal-Nieuw) die gebruikt wordt voor het opslaan van het PDF-document in het DMS / geregistreerde documenten
- **Categorie Elektra tot 50000**. De waarde van de kolom _Getal1_ bij _Sectie: ErkendeMaatregelen Item: KeyElekVerbruiktot50000_ moet verwijzen naar een dnkey van een kaart in tbmilverbruikcat (portaal Inrichtingenbeheer _Energie verbruik categorie_) die staat voor de categorie Elektra tot 50000 kWh. Deze waarde is nodig voor het aanmaken van nieuwe energiekaarten bij de inrichting
- **Categorie Elektra tot 200000**. De waarde van de kolom _Getal1_ bij _Sectie: ErkendeMaatregelen Item: KeyElekVerbruiktot200000_ moet verwijzen naar een dnkey van een kaart in tbmilverbruikcat (tegel _Energie verbruik categorie_) die staat voor de categorie Elektra vanaf 50000 tot 200000 kWh. Deze waarde is nodig voor het aanmaken van nieuwe energiekaarten bij de inrichting
- **Categorie Elektra vanaf 200000**. De waarde van de kolom _Getal1_ bij _Sectie: ErkendeMaatregelen Item: KeyElekVerbruikvanaf200000_ moet verwijzen naar een dnkey van een kaart in tbmilverbruikcat (tegel _Energie verbruik categorie_) die staat voor de categorie Elektra vanaf 200000 kWh. Deze waarde is nodig voor het aanmaken van nieuwe energiekaarten bij de inrichting
- **Categorie gas tot 25000**. De waarde van de kolom _Getal1_ bij _Sectie: ErkendeMaatregelen Item: KeyGasVerbruiktot25000_ moet verwijzen naar een dnkey van een kaart in tbmilverbruikcat (tegel _Energie verbruik categorie_) die staat voor de categorie Gas tot 25000 m3. Deze waarde is nodig voor het aanmaken van nieuwe energiekaarten bij de inrichting
- **Categorie gas tot 75000**. De waarde van de kolom _Getal1_ bij _Sectie: ErkendeMaatregelen Item: KeyGasVerbruiktot75000_ moet verwijzen naar een dnkey van een kaart in tbmilverbruikcat (tegel _Energie verbruik categorie_) die staat voor de categorie Gas vanaf 25000 tot 75000 m3. Deze waarde is nodig voor het aanmaken van nieuwe energiekaarten bij de inrichting
- **Categorie gas vanaf 75000**. De waarde van de kolom _Getal1_ bij _Sectie: ErkendeMaatregelen Item: KeyGasVerbruikvanaf75000_ moet verwijzen naar een dnkey van een kaart in tbmilverbruikcat (tegel _Energie verbruik categorie_) die staat voor de categorie Gas vanaf 75000 m3. Deze waarde is nodig voor het aanmaken van nieuwe energiekaarten bij de inrichting.

Het uitgaande vraagbericht vraagGegevensIndividueleInrichting en het antwoord worden gelogd in de messagelog indien:

- en instelling _Sectie: ErkendeMaatregelen en Item: Messagelog_ aangevinkt staat
- en de instelling _Sectie: OWB en Item: MessageLog_ aangevinkt staat.

Na het aanmaken van de omgevingszaak met maatregelen worden dus eventueel:

- Zaak in Zaaksysteem aangemaakt om de PDF te plaatsen (kan ook op fileserver worden geplaatst indien geen DMS)
- Processen en checklisten toegevoegd.
