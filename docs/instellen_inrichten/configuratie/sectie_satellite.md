# Sectie Satellite

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de _Sectie: Satellite_ gerangschikt op item.

Let op: elk compartiment heeft zijn eigen instellingen m.b.t. satellite (beheerportaal-Nieuw: _Compartiment_) Zie [Satellite t.b.v. benadering fileserver](/docs/instellen_inrichten/satellite_filesysteem.md).

## Items Configuratietabel

| Item                     | Kolom        | Omschrijving |
| ------------------------ | ------------ | ------------ |
| AllowAllHostnameVerifier | Aanvinkvakje | Indien aangevinkt zal de OpenWave Cloud instemmen met een self-signed of verlopen certificaat van de satellite-server bij een verbinding onder https.                     |
|                          | Aanvinkvakje | Indien aangevinkt zullen de berichten van de Cloud naar de satellite gaan onder httpsauthenticatie.                                                                       |
| ChunkMbsize              | Getal1       | In _Getal1_ komt de grootte van de chunks in Mb te staan. Een document kan namelijk worden opgeknipt in chunks. Alleen een integer is toegestaan (default waarde = 1 Mb). |
| Domain                   | Tekst        | De domeinnaam van de satellite.                                                                                                                                           |
| Endpoint_fileserver      | Tekst        | Het endpoint van de satellite-service. Zie onderaan deze pagina.                                                                                                          |
| HTTPAuthenticatieNaam    | Tekst        | De usernaam voor https-authenticatie naar de satellite (operationeel indien aangevinkt).                                                                                  |
| HTTPAuthenticatieType    | Tekst        | Type versleuteling van de https-authenticatie. Vooralsnog alleen _Basic_.                                                                                                 |
| HTTPAuthenticatiePass    | Tekst        | Het password bij https-authenticatie naar de satellite.                                                                                                                   |
| Messagelog               | Aanvinkvakje | Indien aangevinkt dan worden de berichten van en naar de satellite gelogd in de beheertabel tbmessagelog (mits ook _Sectie: OWB en Item: Messagelog_ aangevinkt is).      |

Het endpoint moet zijn:

`https://xxxx:yyyy/services/nl.rem.satellite.published.Fileserver.nl.rem.satellite.published.FileserverHttpSoap12Endpoint/`

Op de plaats van de xxxx en de yyyy ip.nummer en poort.
