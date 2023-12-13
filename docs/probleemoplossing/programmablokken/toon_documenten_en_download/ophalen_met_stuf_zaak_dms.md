# Toon documenten met StUF zaak/DMS

Indien gewerkt wordt met StUF-Zaken (zaak/DMS koppeling) dan worden een geefLijstZaakDocument \_Lv01 en geefZaakDocumentLezen_lv01 vraagberichten uitgestuurd. De volgende instellingen zijn daarbij onontbeerlijk.

Voor het openen van een document dat in het DMS staat via OnlyOffice: zie het betreffende kopje bij [Toon documenten en download](toon_documenten_en_download.md).

## Instellingen

De externe zaak/DMS code moet gevuld zijn (dvintzaakcode):

- voor de omgevingszaken, handhaving, inrichting, bouw/sloop en APV/overig en milieu/gebruik kijkt het programma hiertoe naar de zaak zelf
- bij inspecties, kijkt het programma ook naar de kolom externe zaak/dms code van de inspectiekaart zelf
- bij bezwaar/beroep, kijkt het programma ook naar de kolom externe zaak/dmscode (dvintzaakcode) van de bezwaar/beroep kaart zelf
- bij adviezen geldt dat het programma kijkt naar instelling _Sectie: Programma_ en _Item: AdviesIsZaak_:
  - indien deze is aangevinkt dan kijkt het programma naar de externe zaak/DMS code van de advieskaart zelf
  - anders (instelling is niet aangevinkt of deze bestaat niet) bij adviezen: dan kijkt het programma naar de externe zaak/DMS code van de bijbehorende hoofdzaak (dus omgeving, handhaving, overig).

### Instellingen m.b.t. opmaak en adressering

In alle gevallen bekijkt OpenWave eerst de gemeente waar de zaak speelt waarvoor de documenten opgevraagd worden. Voor credentials, stuurgegevens en endpoint kijkt het programma naar de kaart in tb33gemeente (beheerportaal-Nieuw) die voor de betreffende gemeente is. Wordt daar geen informatie gevonden, dan valt OpenWave terug op de algemene stufzaak/DMS instellingen.

Een uitzondering hierop is de situatie dat een zaak speelt bij een gemeente die gedefinieerd is in een compartiment terwijl de zaak zelf niet door dat compartiment wordt behandeld, maar door de host. In dat laatste geval valt OpenWave ook terug op de algemene stufzaak/DMS instellingen uit tbinitialisatie (beheertegel _Configuratie_).
_Sectie: KoppelingDocNaarDms_:

- _Item: Ontvangstadres_BeantwoordVraag_. De kolom _Tekst_ moet gevuld worden met juiste endpoint van de DMS-service
- _Item: HTTPSoapAction_geefLijstZaakdocumenten_Lv01_. De kolom _Tekst_ moet gevuld worden met juiste soapaction:
  - indien zaak/DMS dan `[http://www.egem.nl/StUF/sector/zkn/0310/geefLijstZaakdocumenten_Lv01](http://www.egem.nl/StUF/sector/zkn/0310/geefLijstZaakdocumenten_Lv01.md)`
  - indien (oude) stufzaken dan `[http://www.egem.nl/StUF/sector/zkn/0310/zakLv01](http://www.egem.nl/StUF/sector/zkn/0310/zakLv01.md)`
- _Item: HTTPSoapAction_geefZaakdocumentLezen_Lv01_. De kolom _Tekst_ moet gevuld worden met juiste soapaction:
  - indien zaak/DMS dan `[http://www.egem.nl/StUF/sector/zkn/0310/geefZaakdocumentLezen_Lv01](http://www.egem.nl/StUF/sector/zkn/0310/geefZaakdocumentLezen_Lv01.md)`
  - indien (oude) stufzaken dan `[http://www.egem.nl/StUF/sector/zkn/0310/edcLv01](http://www.egem.nl/StUF/sector/zkn/0310/edcLv01.md)`
- _Item: Ontvanger_applicatie_. De kolom _Tekst_ met de ontvanger
- _Item: Ontvanger_organisatie_. De kolom _Tekst_ met de organisatie
- _Item: Ontvanger_administratie_. De kolom _Tekst_ met de administratie
- _Item: Ontvanger_gebruiker_. De kolom _Tekst_ met de gebruiker
- _Item: Zender_applicatie_. De kolom _Tekst_ met de ontvanger
- _Item: Zender_organisatie_. De kolom _Tekst_ met de organisatie
- _Item: Zender_administratie_. De kolom _Tekst_ met de administratie
- _Item: Zender_gebruiker_. De kolom _Tekst_ met de gebruiker.

LET OP: de soapactions kunnen ingesloten moeten zijn met dubbele quootjes, dus bijvoorbeeld:

`"http://www.egem.nl/StUF/sector/zkn/0310/geefZaakdocumentLezen"`

Als de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: HTTPAuthenticatieNaam_ bestaat en is aangevinkt dan wordt de verzending over HTTPS geautoriseerd met :

- authenticatienaam is kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: HTTPAuthenticatieNaam_
- authenticatiepass is kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: HTTPAuthenticatiePass_. Zie ook: [2-way encryptie van externe wachtwoorden](../../../../instellen_inrichten/2way_encryptie_externe_wachtwoorden.md)
- in de kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: HTTPAuthenticatieType_ kan desgewenst het authenticatietype worden ingevuld: NTLM (versie 1) of Basic (default waarde)
- In de kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: Domein_ kan desgewenst het domein worden ingevuld.

Indien er gebruik moet worden gemaakt van een **client-certificaat** (wordt geplaatst op de CONF-map van de WSAS server) dan:

- moet de (file)-naam van dat certificaat worden opgeslagen in de kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS en Item: ClientCertificaatNaam_
- het certificaat password in de kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS en Item: ClientCertificaatPassword_. Zie ook: [2-way encryptie van externe wachtwoorden](../../../../instellen_inrichten/2way_encryptie_externe_wachtwoorden.md)
- het certificaattype in de kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS_ en _Item: ClientCertificaatType_ (default PKCS12).

Indien de instelling _Sectie: KoppelingDOCNAARDMS en Item: AllowAllHostnameVerifier_ aangevinkt is zal de OpenWave Cloud instemmen met een self-signed of verlopen (server)certificaat bij een verbinding onder https.

In het **geefLijstZaakDocument_lv01** bericht wordt de normale **scope** van het bericht uitgevraagd met uitzondering van de tag _dct.omschrijving_. Dit in verband met verschil tussen de officiele validator en de officiële versie 1.2 beschrijving. De meeste DMS -systemen geven in het antwoordbericht toch de waarde terug, maar niet altijd.

Met het aanvinken van de instelling _Sectie: KoppelingDOCNAARDMS en Item: ZakLV01MetDCTOmschrijving_, zal _<ns:dct.omschrijving xsi:nil="true/>_ wel in de scope van het vraagbericht worden opgenomen.

In het **geefZaakDocumentLezen_lv01 bericht** kan de **scope** op twee manieren worden gedefinieerd. Standaard gebeurt dat als volgt

```xml
 <ns:scope>
 <ns:object StUF:entiteittype="EDC" StUF:scope="kerngegevens"/>
 </ns:scope>
```

Indien echter de instelling _Sectie: KoppelingDOCNAARDMS en Item: StUFGeefDocumentMetScope_ aangevinkt is dan:

```xml
 <ns:scope>
 <ns:object StUF:entiteittype="EDC" >
 <ns:isRelevantVoor StUF:entiteittype="EDCZAK">
 <ns:gerelateerde StUF:entiteittype="ZAK">
 <ns:identificatie xsi:nil="true"/>
 </ns:gerelateerde>
 </ns:isRelevantVoor>
 </ns:object>
 </ns:scope>
```

## Filtering retourbericht geef lijst zaakdocumenten

In het retourbericht (zakLa01) worden de documenten opgesomd in de gevraagde kolommen
`<identificatie>`, `<creatiedatum>`, `<titel>`, `<vertrouwelijkheidAanduiding>`, `<auteur>` en `<link>`.

Mogelijk wordt ook de kolom `<dct.omschrijving>` geleverd (niet altijd).
Default wordt de kolom `<dct.omschrijving>` in OpenWave getoond in de kolom _map_.

Default wordt de kolom `<titel>` in OpenWave getoond in de kolom _titel_.

Hier kan van afgeweken worden met de instellingen:

- _Sectie: KoppelingDOCNAAMDMS_ en _Item: WaveKolomTitelIsStUFTag_. In de kolom _Tekst_ kan hier dus bijvoorbeeld komen `<dct.omschrijving>`
- _Sectie: KoppelingDOCNAAMDMS_ en _Item: WaveKolomMapIsStUFTag_. In de kolom _Tekst_ kan hier dus bijvoorbeeld komen `<titel>`.

Het programma gaat de lijst filteren op grond van tag vertrouwelijkAanduiding indien de kolom dvvertrouwelijkheid (_mag documenten inzien tot en met vertrouwlijkheidsniveau_) van tbrechten (beheertegel _Functionele rechten_), waar de inlogger toe behoort, een gevulde waarde heeft. Is dat het geval dan worden alleen die documenten getoond waarvoor geldt dat de waarde van de tag `<vertrouwelijkAanduiding>` LEEG is of een waarde heeft waarvan het vereiste niveau (beheertegel _Vertrouwelijkheid_) kleiner of gelijk is aan het niveau ingesteld bij de medewerker.

## Logging

De berichten kunnen gelogd worden op 2 manieren:

- Loggen in tbMessagelog (beheertegel _Messagelog_). Deze logging staat aan indien de instelling aangevinkt is van _Sectie: OWB_ en _Item: MessageLog_. In kolom _Getal1_ van deze instelling staat het aantal dagen dat de loggingskaarten bewaard moeten blijven. Default is dat 31.
- Indien de instelling _Sectie: OWB_ en _Item: Loggen_ aangevinkt is dan worden de berichten onder een door OpenWave te bepalen naam (bijvoorbeeld 1.1345123012_VanOW_naarZaak) op een logmap van de server geplaatst (om die te zien zijn dus systeembeheerrechten noodzakelijk).
