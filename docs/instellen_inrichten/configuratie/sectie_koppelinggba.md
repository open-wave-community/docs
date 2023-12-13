# Sectie KoppelingGBA

Hieronder de instellingen uit de [configuratietabel](README.md) (tbinitialisatie) van de _Sectie: koppelingGBA_ gerangschikt op item. Zie [BRP (GBA) bevraging](/probleemoplossing/programmablokken/bpr_bevraging?s[]=gba.md).

## Items Configuratietabel

| Item                     | Kolom        | Omschrijving                                                               |
|--------------------------|--------------|----------------------------------------------------------------------------|
| AllowAllHostnameVerifier | Aanvinkvakje | Indien aangevinkt is zal de OpenWave Cloud instemmen met een self-signed of verlopen (server)certificaat bij een verbinding onder https. |
| Charset                  | Tekst        | StUF bericht. Hier kan opgegeven worden welke charset in de xml header wordt gebruikt bijv. utf-8. (default is dat ISO-8859-1). |
| HTTPSoapAction           | Tekst        | De soapaction voor het npsLv01 vraagbericht is `[http://www.egem.nl/StUF/sector/bg/0310/npsLv01](http://www.egem.nl/StUF/sector/bg/0310/npsLv01.md)`. LET OP: de soapactions kunnen ingesloten moeten zijn met dubbele quootjes. |
| Methode                  | Tekst        | Alleen de waardes _StUF-BG 310_ of _Competent_ zijn toegestaan.            |
|                          | Aanvinkvakje | Indien aangevinkt dan begrijpt het programma dat de koppeling actief is.   |
| Zender_Applicatie        | Getal2       | Hier kan het maximum aantal retourobjecten opgegeven worden (default 100) bij StUG BG 310 npsLv01 bericht. |
|                          | Tekst        | Hier kan de sortering worden opgegeven (default 2) bij StUG BG 310 npsLv01 bericht. |
| Zender_Gebruiker         | Getal1       | Indien een waarde 1 of een waarde 2 en indien zender-gebruiker op de gemeentetabelkaart (tb33gemeente.dvstufnhrzendergeb) in het blok _GBAV/BPR Stuf BG stuurgegevens_ leeg is dan zal OpenWave - indien _Getal1_ de waarde 1 heeft - het stuurgegeven `<zender>` `<gebruiker>` in het StUF-bericht npsLv01 vullen met de loginnaam (tbmedewerkers.dvloginnaam) van de inlogger. Indien _Getal1_ de waarde 2 heeft, dan de email van de inlogger (tbmedewerkers.dvemail). |
