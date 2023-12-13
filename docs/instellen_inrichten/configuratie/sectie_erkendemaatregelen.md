# Sectie ErkendeMaatregelen

Hieronder de instellingen uit de configuratietabel (tbinitialisatie) van de _Sectie: ErkendeMaatregelen_ gerangschikt op item. Zie [Erkende Maatregelen](../../probleemoplossing/programmablokken/erkende_maatregelen.md).

## Items Configuratietabel

| Item                       | Kolom        | Omschrijving                                                             |
|----------------------------|--------------|--------------------------------------------------------------------------|
| charset                    | Tekst        | Default UTF 8. Komt bovenaan de xml-vraag-berichten te staan.            |
| datumVanaf                 | Tekst        | In dit tekstveld (!) komt datum/tijd van het laatste moment dat OpenWave de lijst met inrichtingen uit RVO die nieuwe matregelen hebben gemeld, heeft opgehaald. Het formaat moet zijn: yyyy-MM-ddTHH:mm:ss . |
| clientcertificaatnaam      | Tekst        | Naam van certificaat dat gebruikt wordt voor berichtenverkeer met RVO.   |
| clientcertificaatpassword  | Tekst        | Password van certificaat dat gebruikt wordt voor berichtenverkeer met RVO. |
| certificaattype            | tekst        | Type van certificaat dat gebruikt wordt voor berichtenverkeer met RVO (default PKCS12). |
| DnkeyVanOmgevingsZaakType  | Getal1       | De dnkey van de soort omgevingszaak uit tbsoortomgverg die geldt voor de melding erkende maatregelen. |
| DocMapIncDocroot           | Tekst        | De map waarop de PDF moet worden geplaatst indien geen spraken van StUF zaak/DMS. |
| DocumentStatus             | Tekst        | Onder welke status het op te halen EK-document moet worden geregistreerd (in geregistreerde documenten of DMS). |
| Documenttype               | Tekst        | Onder welke type het op te halen EK-document moet worden geregistreerd (in geregistreerde documenten of DMS). |
| DocVertrouwelijkheid       | Tekst        | Onder welke vertrouwelijkheid het op te halen EK-document moet worden geregistreerd (in geregistreerde documenten of DMS). |
| Endpoint                   | Tekst        | Het endpoint bij het RVO voor de vraagberichten: vraagGegevensIndividueleInrichtingRequest en vraagLijstInrichtingIDsRequest. |
| KeyElekVerbruiktot50000    | Getal1       | Dnkey uit tbmilverbruikcat die staat voor jaarlijks elektragebruik tot 50000 kWh. |
| KeyElekVerbruiktot200000   | Getal1       | Dnkey uit tbmilverbruikcat die staat voor jaarlijks elektragebruik van 50000 kWh tot 200000 kWh. |
| KeyElekVerbruikvanaf200000 | Getal1       | Dnkey uit tbmilverbruikcat die staat voor jaarlijks elektragebruik vanaf 200000 kWh. |
| KeyGasVerbruiktot25000     | Getal1       | Dnkey uit tbmilverbruikcat die staat voor jaarlijks gasgebruik tot 25000 M3. |
| KeyGasVerbruiktot75000     | Getal1       | Dnkey uit tbmilverbruikcat die staat voor jaarlijks gasgebruik vanaf 25000 tot 75000 M3. |
| KeyGasVerbruikvanaf75000   | Getal1       | Dnkey uit tbmilverbruikcat die staat voor jaarlijks gasgebruik vanaf 75000 M3. |
| Messagelog                 | Aanvinkvakje | Indien aangevinkt (en de instelling _Sectie: OWB en Item: MessageLog_ staat ook aangevinkt) dan worden de vraag- en antwoordberichten gelogd in tbmessagelog. |
| OIN                        | Tekst        | Het OIN-nummer van de organisatie die de meldingen opvraagt.             |
|                            | Info         | De naam van de organisatie die de meldingen opvraagt (die hoort bij het OIN-nummer). |
| RolContactadres            | Tekst        | Een verwijzing naar de kolom dvcode van tbadressoort. De rol die hoort bij de erkende maatregelen-contactadressen bij de inrichting. |
