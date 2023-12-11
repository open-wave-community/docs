# Sectie KoppelingBAG

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de *Sectie: KoppelingBAG* gerangschikt op item.
Zie [BAG bevraging via StUF BG vraagbericht](/docs/probleemoplossing/programmablokken/bag_bevraging.md).

## Items Configuratietabel

| Item | Kolom | Omschrijving |
|---|---|---|
| AllowAllHostnameVerifier | Aanvinkvakje |Indien aangevinkt is zal de OpenWave Cloud instemmen met een self-signed of verlopen (server)certificaat bij een verbinding onder https. |
| Charset | Tekst |StUF bericht. Hier kan opgegeven worden welke charset in de transport header wordt gebruikt bijv. utf-8. (default is dat ISO-8859-1). |
| ClientCertificaatNaam | Tekst |De client-certificaatnaam van het certificaat (zoals die op de map conf staat op de WSAS-server) dat nodig is voor goede ontvangst van het StUF-BG 310 bericht. |
| CertificaatPassword | Tekst |Het (gecrypte) password van het certificaat dat nodig is voor goede ontvangst van het StUF-BG 310 bericht. |
| CertificaatType | Tekst |Het Certificaattype  (default PKCS12) dat nodig is voor goede ontvangst van het StUF-BG 310 bericht. |
| HTTPAuthenticatieNaam | Tekst |Naam voor authenticatie binnen https. |
| | Aanvinkvakje | Indien aangevinkt dan wordt de verzending over HTTPS geautoriseerd met naam en wachtwoord. |
| HTTPAuthenticatiePass | Tekst |Wachtwoord voor authenticatie binnen HTTPS. Kan gecrypt zijn opgeslagen. |
| HTTPAuthenticatieType | Tekst |Hier kan desgewenst het authenticatietype worden ingevuld: NTLM (versie 1) of Basic (default waarde). |
|HTTPSoapAction_oprLv01 | Tekst |Soapaction voor vraag-bericht oprLv01: `[http://www.egem.nl/StUF/sector/bg/0310/oprLv01](http://www.egem.nl/StUF/sector/bg/0310/oprLv01.md)` LET OP: de soapactions kunnen ingesloten moeten zijn met dubbele quootjes. |
|HTTPSoapAction_tgoLv01 | Tekst |Soapaction voor vraag-bericht tgoLv01: `http://www.egem.nl/StUF/sector/bg/0310/tgoLv01` LET OP: de soapactions kunnen ingesloten moeten zijn met dubbele quootjes. |
|HTTPSoapAction_wplLv01 | Tekst |Soapaction voor vraag-bericht wplLv01: `http://www.egem.nl/StUF/sector/bg/0310/wplLv01` LET OP: de soapactions kunnen ingesloten moeten zijn met dubbele quootjes. |
| MessageLog | Aanvinkvakje |Indien aangevinkt EN de instelling *Sectie: OWB Item: Messagelog* is ook aangevinkt, dan worden de NHR vraagberichten gelogd in de beheertabel tbmessagelog. |
| Methode | Tekst |Alleen de waardes *StUF-310* is toegestaan. |
| | Aanvinkvakje |Indien aangevinkt dan begrijpt het programma dat de koppeling actief is. |
| Ontvanger_administratie | Tekst |Stuurgegeven StUf beantwoordensynchronevraagberichten oprLv01, tgoLv01 en wplLv01. |
| Ontvanger_applicatie | Tekst |Stuurgegeven StUf beantwoordensynchronevraagberichten oprLv01, tgoLv01 en wplLv01. |
| Ontvanger_gebruiker | Tekst |Stuurgegeven StUf beantwoordensynchronevraagberichten oprLv01, tgoLv01 en wplLv01. |
| Ontvanger_organisatie | Tekst |Stuurgegeven StUf beantwoordensynchronevraagberichten oprLv01, tgoLv01 en wplLv01. |
| Ontvangstadres | Tekst |Het endpoint voor de StUF-BG 310 beantwoordensynchronevraagberichten: oprLv01, tgoLv01 en wplLv01. |
| Zender_administratie | Tekst |Stuurgegeven StUf beantwoordensynchronevraagberichten oprLv01, tgoLv01 en wplLv01. |
| Zender_applicatie | Tekst |Stuurgegeven StUf beantwoordensynchronevraagberichten oprLv01, tgoLv01 en wplLv01. |
| Zender_gebruiker | Tekst |Stuurgegeven StUf beantwoordensynchronevraagberichten oprLv01, tgoLv01 en wplLv01. |
| Zender_organisatie | Tekst |Stuurgegeven StUf beantwoordensynchronevraagberichten oprLv01, tgoLv01 en wplLv01. |
