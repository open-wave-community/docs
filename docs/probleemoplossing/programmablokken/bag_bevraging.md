# BAG bevraging via StUF BG vraagbericht

Voor verwerken van XML-BAG-Extracten en BAG-mutaties: zie:[Inlezen BAG Extract en/of BAG-mutaties](/docs/probleemoplossing/programmablokken/inlezen_bag-extract_en_bag-mutaties.md).

## Waar vandaan aangeroepen

Vanuit diverse plekken in OpenWave kunnen vraagberichten in StUF-BG 310 gesteld worden aan de leverancier van BAG-gegevens.

* Vanuit achterliggende lijst/detailschermen van tegel *Locaties* op openingsportaal:
  * verifiëren van woonplaats (wplLv01)
  * verifiëren van openbare ruimtenaam (oprLv01)
  * opvragen van openbare ruimtenamen bij een woonplaats (oprLv01)
  * opvragen van verblijfsobjecten bij een openbare ruimte (tgoLv01)
  * verifiëren van een locatie adres (tgoLv01)
* Bij het verifiëren van een locatie adres onder de knoppen *Locatie* op de lijsten *Alle Zaken*, *Alle Inrichtingen*, *Alle locaties* en op de zaakportalen, het inrichtingsportaal en bijbehorende detailschermen (tgoLv01).
* Bij het verifiëren van een locatie adres bij aanmaken nieuwe zaak en/of inrichting (tgoLv01).
* Bij het opvragen van verblijfsobjecten bij een openbare ruimte bij aanmaken nieuwe zaak en/of inrichting (tgoLv01).

## Verplichte instellingen

* de instelling *Sectie: KoppelingBAG* en *Item: Methode* en *Tekst = StUF-310* bestaat en is aangevinkt
* EN de inlogger behoort tot een rechtengroep die BAG-rechten heeft op locaties (locatie adressen BAG bij hoofdrechtengroep: tbrechten.dldpclbag)
* EN de instelling *Sectie: KoppelingBAG* en *Item: Ontvangstadres* bestaat en kolom *Tekst* is gevuld met het endpoint voor beantwoordensynchronevraag
* EN de instelling *Sectie: KoppelingBAG* en *Item: HTTPSoapAction_tgoLv01* bestaat en kolom *Tekst* is gevuld met `[http://www.egem.nl/StUF/sector/bg/0310/tgoLv01](http://www.egem.nl/StUF/sector/bg/0310/tgoLv01.md)`
* EN de instelling *Sectie: KoppelingBAG* en *Item: HTTPSoapAction_wplLv01* bestaat en kolom *Tekst* is gevuld met `[http://www.egem.nl/StUF/sector/bg/0310/wplLv01](http://www.egem.nl/StUF/sector/bg/0310/wplLv01.md)`
* EN de instelling *Sectie: KoppelingBAG* en *Item: HTTPSoapAction_oprLv01* bestaat en kolom *Tekst* is gevuld met `[http://www.egem.nl/StUF/sector/bg/0310/oprLv01](http://www.egem.nl/StUF/sector/bg/0310/oprLv01.md)`
* EN de stuurgegevens kolom *Tekst* bij *Sectie: KoppelingBAG op Items: Ontvanger_Applicatie en Ontvanger_Organisatie en Zender_Applicatie en Zender_Organisatie* zijn gevuld. Alleen Ontvanger_Organisatie mag gevuld zijn met een lege waarde.

LET OP: de soapactions kunnen ingesloten moeten zijn met dubbele quootjes dus bijvoorbeeld:
`"[http://www.egem.nl/StUF/sector/bg/0310/oprLv01](http://www.egem.nl/StUF/sector/bg/0310/oprLv01.md)"`.

## Facultatieve instellingen

* **maximum aantal retourobjecten** In de kolom *Getal2* van de instelling met *Sectie: KoppelingBAG* en *Item: Zender_Applicatie* kan het maximum aantal retourobjecten opgegeven worden (default 100). Deze instelling wordt gebruikt bij het opvragen van openbare ruimtenamen bij een woonplaats (oprLv01) en opvragen van verblijfsobjecten bij een openbare ruimte (tgoLv01).
* Als de instelling *Sectie: KoppelingBAG* en *Item: HTTPAuthenticatieNaam* bestaat en is aangevinkt dan wordt de verzending over HTTPS geautoriseerd met:
    *authenticatienaam is kolom *Tekst* van de instelling *Sectie: KoppelingBAG* en *Item: HTTPAuthenticatieNaam*
  * authenticatiepass is kolom *Tekst* van de instelling *Sectie: KoppelingBAG* en *Item: HTTPAuthenticatiePass*. Zie ook: [2-way encryptie van externe wachtwoorden](/docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md).
  * In de kolom *Tekst* van de instelling *Sectie: KoppelingBAG* en *Item: HTTPAuthenticatieType* kan desgewenst het authenticatietype worden ingevuld: ( Basic is de default waarde).

Indien er gebruik moet worden gemaakt van een **client-certificaat** (wordt geplaatst op de CONF-map van de WSAS server) dan:

* moet de (file)-naam van dat certificaat worden opgeslagen in de kolom *Tekst* van *Sectie: KoppelingBAG en Item: ClientCertificaatNaam*
* het certificaat password in de kolom *Tekst* van *Sectie: KoppelingBAG en Item: CertificaatPassword*. Zie ook: [2-way encryptie van externe wachtwoorden](/docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md)
* het certificaattype in de kolom *Tekst* van *Sectie: KoppelingBAG en Item: CertificaatType* (default PKCS12).

Indien de instelling  *Sectie: KoppelingBAG en Item: AllowAllHostnameVerifier* aangevinkt is zal de Openwave Cloud instemmen met een self-signed of verlopen (server)certificaat bij een verbinding onder https.

* In de kolom *Tekst* van de instelling met *Sectie: KoppelingBAG* en *Item: Charset* kan opgegeven worden welke charset in de https header wordt gebruikt bijv. utf-8 (default is dat ISO-8859-1).

## Vraag en antwoordverwerking

### wplLv01 verifieer woonplaats

Het vraagbericht wordt opgesteld met de tbwoonplaats.woonplaatsnaam en de tb33gemeente.dvgemeentecode (de gemeente-id).

Indien:

* gevuld antwoord dan worden de volgende tbwoonplaats kolommen overschreven:
  * dvidentificatiecode met `<identificatiecode>` uit het antwoordbericht
  * ddcontroleBAG met datum van vandaag
  * ddvervaldatum met null
* leeg antwoord dan worden de volgende tbwoonplaats kolommen overschreven:
  * dvidentificatiecode met null
  * ddcontroleBAG met null
  * ddvervaldatum met datum van vandaag.

### oprLv01 verifieer openbare ruimtenaam

Het vraagbericht wordt opgesteld met de tbopenbareruimte.dvopruimtenaam en de tbwoonplaats.dvidentificatiecode (zie hierboven).

Indien:

* gevuld antwoord dan worden de volgende tbopenbareruimte kolommen overschreven:
  * dvopruimteid met `<gor.identificatiecode>` uit het antwoordbericht
  * ddcontroleBAG met datum van vandaag
  * ddvervaldatum met null
  * dvopruimtetype met `<gor.type>` uit het antwoordbericht
* leeg antwoord dan worden de volgende tbopenbareruimte kolommen overschreven:
  * dvopruimteid met null
  * ddcontroleBAG met null
  * ddvervaldatum met datum van vandaag.

### tgoLv01 verifieer locatieadres

Het vraagbericht wordt opgesteld met de dvwoonplaatsnaam, dvopruimtenaam, dvhuisnummer, dvhuisletter en dvhuisnummertoevoeging, dvgemeenteid) uit vwfrmlokaties.
Er wordt gevraagd naar het verblijfsobject op dat adres.

Indien:

* gevuld antwoord dan worden de volgende tbperceeladressen kolommen overschreven:
  * dvidentificatiecode met `<identificatiecode>` uit het antwoordbericht
  * ddcontroleBAG met datum van vandaag
  * ddvervaldatum met null
  * dvtypeadrobj met ‘V’
  * dvpostcode met `<aoa.postcode>` uit het antwoordbericht.
  * dvbestemming met `<gebruiksdoel>` uit het antwoordbericht
  * dnxcoordinaat met de x van `<gml:pos>` uit de gekozen rij van het antwoordbericht
  * dnycoordinaat met de y van `<gml:pos>` uit de gekozen rij van het antwoordbericht
* leeg antwoord dan worden de volgende tbperceeladressen kolommen overschreven:
  * dvidentificatiecode met null
  * ddcontroleBAG met null
  * ddvervaldatum met datum van vandaag.

### oprLv01 opvragen openbare ruimtenamen bij een woonplaats

Het vraagbericht wordt opgesteld met de tbwoonplaats.dvidentificatiecode (zie hierboven wplLv01) en een door de inlogger ingetikte karakterreeks die wordt geïnterpreteerd als de openbare Ruimtenaam begint met …… LET OP: WEL case-sensitive.

Indien gevuld antwoord dan kan de inlogger kiezen uit een lijst van openbare ruimtenamen. Het programma controleert of deze openbare ruimte reeds bestaat in tbopenbareruimte (controle op dvopruimtenaam en dnkeywoonplaats).

* Indien de openbare ruimte nog niet bestaat dan wordt een nieuwe kaart aangemaakt met:
  * dnkeywoonplaats met de dnkey van de betrokken woonplaats
  * dvopruimteid met `<gor.identificatiecode>` uit de gekozen rij van het antwoordbericht
  * dvopruimtenaam met `<gor.openbareRuimteNaam>` uit de gekozen rij van het antwoordbericht
  * ddcontroleBAG met datum van vandaag.
* Indien de kaart reeds bestond dan wordt deze overschreven met:
  * dvopruimteid met `<gor.identificatiecode>` uit de gekozen rij van het antwoordbericht
  * ddcontroleBAG met datum van vandaag.

### tgoLv01 opvragen verblijfsobjecten bij een openbare ruimte

Het vraagbericht wordt opgesteld met de tbopenbareruimte.dvopruimtenaam en tbwoonplaats.dvidentificatiecode (zie hierboven wplLv01).

Indien gevuld antwoord dan kan de inlogger kiezen uit een lijst van verblijfsobjecten. Het programma controleert of dit locatie adres reeds bestaat in tbperceeladressen (controle op dnkeyopenbruimte + dvhuisnummer + dvhuisletter + dvhuisnummertoevoeging).

* Indien het locatie adres nog niet bestaat dan wordt een nieuwe kaart aangemaakt met:
  * dnkeyopenbruimte met de dnkey van de betrokken openbare ruimte
  * dvidentificatiecode met `<identificatie>` uit de gekozen rij van het antwoordbericht (zie voor betekenis: [Locatie detailscherm](/docs/probleemoplossing/module_overstijgende_schermen/locatie.md))
  * ddcontroleBAG met datum van vandaag
  * dvtypeadrobj met ‘V’
  * dvhuisnummer met `<aoa.huisnummer>` uit de gekozen rij van het antwoordbericht
  * dvhuisletter met `<aoa.huisletter>` uit de gekozen rij van het antwoordbericht
  * dvhuisnummertoevoeging met `<aoa.huisnummertoevoeging>` uit de gekozen rij van het antwoordbericht
  * dvpostcode met `<aoa.postcode>` uit de gekozen rij van het antwoordbericht
  * dvbestemming met `<gebruiksdoel>` uit de gekozen rij van het antwoordbericht
  * dnxcoordinaat met de x van `<gml:pos>` uit de gekozen rij van het antwoordbericht
  * dnycoordinaat met de y van `<gml:pos>` uit de gekozen rij van het antwoordbericht.
* Indien de kaart reeds bestond dan wordt deze overschreven met:
  * dvidentificatiecode met `<identificatie>` uit de gekozen rij van het antwoordbericht
  * ddcontrolebag met datum van vandaag
  * dvpostcode met `<aoa.postcode>` uit de gekozen rij van het antwoordbericht
  * dvtypeadrobj met ‘V’
  * dvbestemming met `<gebruiksdoel>` uit de gekozen rij van het antwoordbericht
  * dnxcoordinaat met de x van `<gml:pos>` uit de gekozen rij van het antwoordbericht mits gevuld
  * dnycoordinaat met de y van `<gml:pos>` uit de gekozen rij van het antwoordbericht mits gevuld.

## Logging BAG-berichten

De berichten kunnen gelogd worden op 2 manieren:

* Loggen in tbMessagelog (beheertegel *Messagelog*) Deze logging staat aan indien de instelling aangevinkt is van *Sectie: OWB* en *Item: MessageLog*. In kolom *Getal1* van deze instelling staat het aantal dagen dat de loggingskaarten bewaard moeten blijven. Default is dat 31.
* Indien de instelling *Sectie: OWB* en *Item: Loggen* aangevinkt is dan worden de berichten onder een door OpenWave te bepalen naam (bijvoorbeeld 1.1345123012_VanOW_naar BAG) op een logmap van de server geplaatst (om die te zien zijn dus systeembeheerrechten noodzakelijk).
