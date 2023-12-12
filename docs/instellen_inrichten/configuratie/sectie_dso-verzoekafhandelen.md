# Sectie DSO-VerzoekAfhandelen

Hieronder de instellingen uit de [configuratietabel](/instellen_inrichten/configuratie/README.md) (tbinitialisatie) van de _Sectie: DSO-VerzoekAfhandelen_ gerangschikt op item. Het geautoriseerde OIN-nummer die in de https-header van berichten naar het algemeen endpoint wordt opgenomen, staat in de kolom _Tekst_ van instelling _Sectie: SWF en Item: OINvanZender_.

- Idem dito _Sectie: SWF en Item: Certificaatnaam_.
- Idem dito _Sectie: SWF en Item: CertificaatPassword_.
- Idem dito _Sectie: SWF en Item: CertificaatType_.

## Items Configuratietabel

| Item                                  | Kolom        | Omschrijving |
| ------------------------------------- | ------------ | ------------ |
| aantaldagenterugGemisteVerzoeken      | Getal1       | Het aantal dagen terug dat OpenWave moet hanteren voor de API-aanroep _verzoeken/zoek_ voor het ophalen van DSO gemisteVerzoeken. Defaultwaarde = 7 |
| aantaldagenterugGerelateerdeVerzoeken | Getal1       | Het aantal dagen terug dat OpenWave moet hanteren voor de API-aanroep _verzoeken/zoek_ voor het ophalen van DSO gerelateerde zaken. Defaultwaarde = 3 |
| AlgemeenEndpoint | Tekst        | Hier dient het algemene gedeelte van het endpoint van de DSO-API's Verzoeken-Afhandelen te staan bijvoorbeeld `https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v2/` |
| Hoofdprojectlocatie                   | Aanvinkvakje | Indien aangevinkt dan wordt de kolom dlhoofdprojectlocatie van tbzaakkadperc (projectlocaties) van de eerste projectlocatie uit het stambericht op T gezet, mits de omgevingzaak verwijst naar de dummylokatieperceelkey of dnkeyswfdummyadres (dus naar onbekend adres). |     |
| MessageLog                            | Aanvinkvakje | Indien aangevinkt dan wordt de binnenkomende stamberichten gelogd in tbMessagelog, mits de algemene instelling _sectie: OWB en item: messagelog_ ook is aangevinkt |
| OntbrekendPostadresVullenMetVestiging | Aanvinkvakje | Indien aangevinkt en het stambericht bevat geen post- cq correspondentieadres bij aanvrager (initiatiefnemer) en/of gemachtigde dan zullen de verblijfs- cq vestiginggegevens in OpenWave zowel in het vestigingsadres als in het postadres bij de contactadreskaart worden overgenomen |
| PolygoonGemisteVerzoeken              | Tekst        | Het geografisch gebied waaruit de gemiste verzoeken worden opgehaald. Een reeks van rijksdriehoek x- en y-coördinaten, waarbij eerste en laatste paar overeenkomt. X en y gescheiden door een komma en de paren gescheiden door een spatie. Bijvoorbeeld: 75000,550000 125000,550000 125000,515000 75000,515000 75000,550000 |
