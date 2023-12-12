# Sectie Koppeling BRP

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de _Sectie: KoppelingBRP_ gerangschikt op item.
Zie [BRP (GBA) bevraging](/docs/probleemoplossing/programmablokken/bpr_bevraging.md).

## Items Configuratietabel

| Item                        | Kolom        | Omschrijving                                                            |
|-----------------------------|--------------|-------------------------------------------------------------------------|
| AllowAllHostnameVerifier    | Aanvinkvakje | Indien aangevinkt is zal de Openwave Cloud instemmen met een self-signed of verlopen (server)certificaat bij een verbinding onder https. |
| HTTPSoapActionStelGbavVraag | Tekst        | Soapaction voor vraag-bericht Competent. Moet zijn: _stelGbavVraag_.    |
| Messagelog                  | Aanvinkvakje | Indien aangevinkt worden de uitgaande Competent vraagberichten gelogd in de beheertabel tbmessagelog indien ook de algemene instelling _Sectie: OWB en Item: Messagelog_ is aangevinkt. |
