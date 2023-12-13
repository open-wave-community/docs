# NHR bevraging

## Waar vandaan aangeroepen

Vanuit het contactadresdetailscherm (zie [Contactadres](/docs/applicatiebeheer/probleemoplossing/module_overstijgende_schermen/contact_adres)) met de knop _controleer BPR/NHR_. Bij inrichtingen in het detailscherm EN in het detailscherm van een vervoerder (via beheertegel _Vervoerders_) is de NHR te bevragen via knop _Controleer NHR_.

**Let op:** Voor de NHR controle bij de vervoerder geldt dat voor het ophalen van de stuurgegevens wordt gekeken naar de opgegeven woonplaats van de vervoerder: immers er is geen zaak/inrichting locatie om de gemeente te bepalen waar de stuurgegevens moeten worden opgehaald. Het programma kijkt bij welke gemeente (tb33gemeente) de woonplaats voorkomt. Indien de woonplaats niet wordt gevonden, OF meer dan 1 keer wordt gevonden, dan kan niet bepaald worden bij welke gemeente de stuurgegevens moeten worden opgehaald en zal de NHR controle niet plaats kunnen vinden.

## Verplichte algemene instellingen

- De instelling _Sectie: KoppelingNHR_ en _Item: Methode_ bestaat en is aangevinkt en:
  - EN kolom _Tekst_ = StUF-BG 310
  - OF kolom _Tekst_ = Competent.
- De instelling _Sectie: KoppelingNHR_ en _Item: HTTPSoapAction_ bestaat en kolom _Tekst_ is gevuld:
  - met - indien methode Competent - met _ophalenVestiging_
  - OF - indien StUF-BG 310 - met `[http://www.egem.nl/StUF/sector/bg/0310/vesLv01](http://www.egem.nl/StUF/sector/bg/0310/vesLv01)`. LET OP: de soapactions kunnen ingesloten moeten zijn met dubbele quootjes
  - EN de inlogger behoort tot een rechtengroep die wijzig BPR/NHR heeft op contactadressen (hoofdrechtengroep: tbrechten.dldcadbra).

Bij elke gemeente (beheerportaal-Nieuw: [Gemeentes](/docs/applicatiebeheer/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_instellingen/gemeentes)) is een blok gegevens te vullen:

[<img src="/_media/openwave/applicatiebeheer/probleemoplossing/programmablokken/tb33gemeentenhr.png?w=600&amp;tok=507c3f" class="media" loading="lazy" alt="" width="600" />](/_detail/openwave/applicatiebeheer/probleemoplossing/programmablokken/tb33gemeentenhr.png?id=docs%3Aapplicatiebeheer%3Aprobleemoplossing%3Aprogrammablokken%3Anhr_bevraging)

### Van boven naar beneden in blok NHR bevraging

- Endpoint voor NHR vraagberichten naar landelijke basisregistratie via Competent (haalVestiging) of endpoint van (lokale) makelaar bij StUF-BG bevraging (vesLv01). Indien methode StUF BG en dit gegeven is niet gevuld, dan kijkt het programma ook nog naar de kolom _Tekst_ van de deprecated instelling _Sectie: KoppelingNHR_ en _Item: Ontvangstadres_
- Client certificaatnaam: de naam van het client-certificaat zoals geïnstalleerd op de webserver (wsasmap conf). Het certificaat wordt door de systeembeheerder geplaatst op de webserver. Indien methode StUF BG en dit gegeven is niet gevuld, dan kijkt het programma ook nog naar de kolom _Tekst_ van de deprecated instelling _Sectie: KoppelingNHR_ en _Item: ClientCertificaatNaam_
- Client certificaattype: certificaattype. Indien methode StUF BG en dit gegeven is niet gevuld, dan kijkt het programma ook nog naar de kolom _Tekst_ van de deprecated instelling _Sectie: KoppelingNHR_ en _Item: ClientCertificaatType_
- Certificaat password (zie ook [2-way encryptie van externe wachtwoorden](/docs/applicatiebeheer/instellen_inrichten/2way_encryptie_externe_wachtwoorden)). Indien het password begint of eindigt met een spatie dan hier inklemmen in dubbele quootjes. Indien methode StUF BG en dit gegeven is niet gevuld, dan kijkt het programma ook nog naar de kolom _Tekst_ van de deprecated instelling _Sectie: KoppelingNHR_ en _Item: ClientCertificaatPassword_
- Https authenticatienaam: Indien geen certificaat (alleen mogelijk bij StUF-BG) dan kan de connectie beveiligd worden met naam en password. Indien methode StUF BG en dit gegeven is niet gevuld, dan kijkt het programma ook nog naar de kolom _Tekst_ van de deprecated instelling _Sectie: KoppelingNHR_ en _Item: HTTPAuthenticatieNaam_
- Password: (zie ook [2-way encryptie van externe wachtwoorden](/docs/applicatiebeheer/instellen_inrichten/2way_encryptie_externe_wachtwoorden)) Indien methode StUF BG en dit gegeven is niet gevuld, dan kijkt het programma ook nog naar de kolom _Tekst_ van de deprecated instelling _Sectie: KoppelingNHR_ en _Item: HTTPAuthenticatiePass_
- Methode: de authenticatie gegevens gaan weer bewerkt over het net. Ondersteund wordt momenteel Base (base64) en NTLM. Indien methode StUF BG en dit gegeven is niet gevuld, dan kijkt het programma ook nog naar de kolom _Tekst_ van de deprecated instelling _Sectie: KoppelingNHR_ en _Item: HTTPAuthenticatieType_
- Domein: Domein voor bovenstaande credentials.

### Van boven naar beneden in blok NHR stuurgegevens Competent

- De indicatie (mag leeg zijn, wordt niet gebruikt).
- Een gebruikerscode (aansluitingsnummer) zoals deze bekend is in COMPETenT.

### Het blok Stuf BG stuurgegevens

- afzender en ontvanger gegevens voor het stuurgedeelte van het StUF BG bericht. Ontvanger_Applicatie en Zender_Applicatie en Zender_Organisatie moeten gevuld zijn. Indien niet gevuld kijkt het programma ook nog naar de deprecated instellingen bij kolom _Tekst_ van _Sectie: KoppelingNHR_ en _items: Ontvanger_Applicatie, Ontvanger_Organisatie, Ontvanger_Administratie, Ontvanger_Gebruiker, Zender_Administratie, Zender_Applicatie, Zender_Organisatie en Zender_Gebruiker_.

## Facultatieve instellingen

- In de kolom _Getal2_ van de instelling met _Sectie: KoppelingNHR_ en _Item: Zender_Applicatie_ kan het maximum aantal retourobjecten opgegeven worden bij StUF Bericht (default 100).
- Indien de instelling _Sectie: KoppelingNHR en Item: AllowAllHostnameVerifier_ aangevinkt is zal de Openwave Cloud instemmen met een self-signed of verlopen (server)certificaat bij een verbinding onder https.
- In de kolom _Tekst_ van de instelling met _Sectie: KoppelingNHR_ en _Item: Charset_ kan opgegeven worden welke charset in de https header wordt gebruikt bijv. utf-8 (default is dat ook utf-8).
- Indien de instelling _Sectie: KoppelingNHR en Item: macLv01_ aangevinkt is dan worden het StUFBericht voor het opvragen van vestigingen op grond van een KvK-nummer gedaan met de berichtsoort macLv01 en anders met vesLv01.
- In de kolom _Tekst_ van de instelling met _Sectie: KoppelingNHR_ en _Item: MacLv01_ kan de sortering worden opgegeven (default: 2) van de stuurgegevens voor de vesLv01 en MacLv01 vraagberichten.

## Vraag en antwoordverwerking

Voor het zoekvenster bij StUF BG bevraging geldt dat minstens 1 van onderstaande beweringen waar moet zijn:

- KvK-nr is gevuld
- vestigingsnummer is gevuld
- postcode is gevuld (en wordt default gevuld met pc van vestigingsadres).
- plaats EN straat zijn gevuld (en worden default gevuld met vestigingsadres)
- handelsnaam EN plaats zijn gevuld (plaats default vanuit vestigingsadres).

Indien bij de vraag het vestigingsnummer leeg is EN KvK-nummer gevuld EN instelling _Sectie: KoppelingNHR en Item: macLv01_ aangevinkt, dan zal het vraagbericht een macLv01 bericht zijn. In alle andere gevallen wordt een vesLv01 bericht gestuurd.

Voor het zoekvenster bij Competent bevraging geldt dat minstens 1 van onderstaande beweringen waar moet zijn:

- KvK-nr is gevuld
- vestigingsnummer is gevuld

Er wordt case-sensitive gezocht en op de volledige waarden (dus niet: straatnaam begint met …).

Zo mogelijk wordt naast KvK-nr, vestigingsnummer, handelsnaam en bedrijfsnaam ook de eindebedrijfdatum gevuld.

OpenWave kent bij een contact zowel een vestigings- als een postadres. De antwoorden op de NHR-bevraging kunnen voorzien zijn van verblijfs- c.q. bezoekadres (altijd) en correspondentie- c.q. postadres (soms). OpenWave vraagt elke keer met radiobuttons hoe hier me om te gaan (en geeft aan of het postadres in het antwoordbericht gevuld is):

- De keuze _Verblijfsadres overnemen in zowel vestigingsadres als postadres bij ontbreken van NHR-postadres-gegevens_ heeft tot gevolg dat inden:
  - zowel verblijfsadres als correspondentieadres van het antwoord gevuld zijn, respectievelijk vestigingsadres en postadres daarmee gevuld worden
  - alleen verblijfsadres van het antwoord is gevuld, zowel het vestigingsadres als postadres daarmee gevuld worden.
- De keuze _Alleen verblijfsadres overnemen bij ontbreken van NHR-postadres-gegevens_ heeft tot gevolg dat inden:
  - zowel verblijfsadres als correspondentieadres van het antwoord gevuld zijn, respectievelijk vestigingsadres en postadres daarmee gevuld worden
  - alleen verblijfsadres van het antwoord is gevuld, alleen het vestigingsadres daarmee gevuld wordt.
- De keuze _Adresgegevens niet overnemen_ heeft tot gevolg dat zowel vestiging- als postadres niet worden overschreven.

## Logging van vraag- en antwoordberichten

- Loggen in tbMessagelog (beheertegel _Messagelog_). Deze logging staat aan indien:
  - de instelling aangevinkt is van _Sectie: OWB_ en _Item: MessageLog_. In kolom _Getal1_ van deze instelling staat het aantal dagen dat de loggingskaarten bewaard moeten blijven. Default is dat 31
  - EN de instelling _Sectie: KoppelingNHR en Item: Messagelog_ staat aangevinkt.
