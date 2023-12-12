# Sectie KoppelingNHR

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie/README.md) (tbinitialisatie) van de _Sectie: koppelingNHR_ gerangschikt op item. Zie [NHR bevraging](/docs/probleemoplossing/programmablokken/nhr_bevraging.md).

## Items Configuratietabel

| Item                      | Kolom        | Omschrijving                                                              |
|---------------------------|--------------|---------------------------------------------------------------------------|
| AllowAllHostnameVerifier  | Aanvinkvakje | Indien aangevinkt is zal de OpenWave Cloud instemmen met een self-signed of verlopen (server)certificaat bij een verbinding onder https. |
| Charset                   | Tekst        | StUF bericht. Hier kan opgegeven worden welke charset in de transport header wordt gebruikt bijv. utf-8. (default is dat ISO-8859-1). |
| ClientCertificaatNaam     | Tekst        | Deprecated. De client-certificaatnaam van het certificaat (zoals die op de map conf staat op de WSAS-server) dat nodig is voor goede ontvangst van het StUF-BG 310 bericht: vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| ClientCertificaatPassword | Tekst        | Deprecated. Het (gecrypte) password van het certificaat dat nodig is voor goede ontvangst van het StUF-BG 310 bericht: vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| ClientCertificaatType     | Tekst        | Deprecated. Het Certificaattype (default PKCS12) dat nodig is voor goede ontvangst van het StUF-BG 310 bericht: vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| HTTPSoapAction            | Tekst        | Soapaction voor vraag-bericht                                             |
Voor Competent moet dit zijn: _ophalenVestiging_
voor Stuf-BG moet dit zijn: `[http://www.egem.nl/StUF/sector/bg/0310/vesLv01](http://www.egem.nl/StUF/sector/bg/0310/vesLv01.md)`.
LET OP: de soapactions kunnen ingesloten moeten zijn met dubbele quootjes. |
| MacLv01 | Aanvinkvakje |Indien aangevinkt dan worden het StUFBericht voor het opvragen van vestigingen op grond van een KvK-nummer gedaan met de berichtsoort macLv01 en anders dus met vesLv01. |
| | Tekst |Deze waarde wordt gebruikt voor de sortering (stuurgegevens) van het macLv01 of VesLv01 bericht. Default 2. |
| MessageLog | Aanvinkvakje |Indien aangevinkt, dan worden de NHR vraagberichten (zowel Competent als StUF BG) gelogd in de beheertabel tbmessagelog indien ook de algemene instelling _Sectie: OWB en Item: messagelog_ is aangevinkt. |
| Methode | Tekst |Alleen de waardes _StUF-BG 310_ of _Competent_ zijn toegestaan. |
| | Aanvinkvakje |Indien aangevinkt dan begrijpt het programma dat de koppeling actief is. |
| Ontvanger_administratie | Tekst |Deprecated Stuurgegeven StUf vraagbericht vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| Ontvanger_applicatie | Tekst |Deprecated Stuurgegeven StUf vraagbericht vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| Ontvanger_gebruiker | Tekst |Deprecated Stuurgegeven StUf vraagbericht vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| Ontvanger_organisatie | Tekst |Deprecated Stuurgegeven StUf vraagbericht vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| Ontvangstadres | Tekst |Deprecated. Het endpoint voor het StUF-BG 310 bericht: vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| PostbusnrInHuisnr | Aanvinkvakje |Indien aangevinkt, dan wordt bij NHR (en BRP) controle indien het om een postbusadres gaat, het postbusnummer in het veld _huisnummer_ geplaatst i.p.v. in veld _straatnaam_. Dit geldt vanaf 1.28 ook voor de binnenkomende DSO berichten: indien initiatiefnemer of gemachtigde een postbusnummer heeft dan wordt dit bij de contactpersoon opgeslagen als straatnaam Postbus en bij huisnummer het Postbusnummer. |
| Zender_administratie | Tekst |Deprecated Stuurgegeven StUf vraagbericht vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| Zender_applicatie | Tekst |Deprecated Stuurgegeven StUf vraagbericht vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| Zender_gebruiker | Tekst |Deprecated Stuurgegeven StUf vraagbericht vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
| Zender_organisatie | Tekst |Deprecated Stuurgegeven StUf vraagbericht vesLv01. Deze instelling is nu per gemeente te doen in de beheertabel tb33gemeente bij de kopjes _NHR-gegevens_. |
