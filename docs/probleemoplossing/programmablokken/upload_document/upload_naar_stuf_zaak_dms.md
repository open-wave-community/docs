# Upload documenten met StUF zaak/DMS

Indien gewerkt wordt met Stuf-Zaken (zaak/DMS koppeling) dan wordt per up te loaden document een genereerDocumentidentificatie_di02 en een voegZaakDocument_Lk01 bericht uitgestuurd.

## Noodzakelijke Instellingen

De externe zaak/DMS code van de zaak moet gevuld zijn (dvintzaakcode).

- Voor de omgevingszaken, handhaving, inrichting, bouw/sloop en APV/overig kijkt het programma hiertoe naar de zaak zelf.
- Bij inspecties, kijkt het programma of de moduleletter (W = omgeving, V = inrichting, H = handhaving, O = APV/overig) voorkomt in de kolom _Info_ van de instelling _Sectie: Koppeling Zaak Item: ZaaktypeInspectietraject_:
  - is dat het geval dan kijkt het programma naar de externe zaak/DMS code van de bijbehorende hoofdzaak (dus omgeving, handhaving, overig, inrichting, horeca)
  - is dat niet het geval dan dan kijkt het programma naar de externe zaak/DMS code van de inspectiekaart zelf.
- Bij bezwaarberoep, kijkt het programma ook naar de zaak/DMS code (dvintzaakcode) van de bezwaarberoep kaart zelf.
- Bij adviezen geldt dat het programma kijkt naar instelling _Sectie: Programma_ en _Item: AdviesIsZaak_:
  - indien deze is aangevinkt dan kijkt het programma naar de externe zaak/DMS code van de advieskaart zelf
  - anders (instelling is niet aangevinkt of deze bestaat niet) bij adviezen dan kijkt het programma naar de externe zaak/DMS code van de bijbehorende hoofdzaak (dus omgeving, handhaving, overig).

## Instellingen voor opmaak en adressering

### Protocol en action

- **Methode**
  - Indien de zaak NIET wordt behandeld door een compartiment dan MOET de instelling _Sectie: KoppelingDOCNAARDMS:_ en _Item: Methode_ aangevinkt staan en heeft als _Tekst_: StUF-ZAKEN 310.
  - Indien de zaak WEL wordt behandeld door een compartiment dan MOET de kolom dvdmsmethode bij de compartimentsdefinitie de waarde StUF-ZAKEN 310 hebben.
- **Action**
  - Instelling _Sectie: KoppelingDOCNAARDMS Item: HTTPSoapAction_voegZaakdocumentToe_Lk01_. De kolom _Tekst_ moet gevuld worden met juiste soapaction:
    - indien zaak/DMS dan `[http://www.egem.nl/StUF/sector/zkn/0310/voegZaakdocumentToe_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/voegZaakdocumentToe_Lk01.md)`
    - indien (oude) stufzaken dan `[http://www.egem.nl/StUF/sector/zkn/0310/edcLk01](http://www.egem.nl/StUF/sector/zkn/0310/edcLk01.md)`.
  - Instelling _Sectie: KoppelingDOCNAAMDMS Item: HTTPSoapAction_genereerDocumentIdentificatie_Di02_. De kolom _Tekst_ moet gevuld worden met juiste soapaction: `[http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02](http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02.md)`.
  - Instelling _Sectie: KoppelingDOCNAAMDMS Item: HTTPSoapAction_updateZaakDocument_Di02_. De kolom _Tekst_ moet gevuld worden met juiste soapaction: `[http://www.egem.nl/StUF/sector/zkn/0310/updateZaakDocument_Di02](http://www.egem.nl/StUF/sector/zkn/0310/updateZaakDocument_Di02.md)`. Deze instelling wordt alleen gebruikt in combinatie met OnlyOffice. Wanneer een bestaand StUF document on line wordt bewerkt met OnlyOffice dan zal het gewijzigde document via updateZaakDocument met de bestaande documentidentifier worden aangeboden aan het DMS, in plaats van voegZaakDocumentToe.

LET OP: de soapactions kunnen ook ingesloten moeten zijn door dubbele quootjes, dus bijv. `"[http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02](http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02.md)"`.

### Endpoint, credentials en stuurgegevens

Voor het endpoint en de stuurgegevens zal het programma eerst kijken naar de waarden in de blokken _stuf zaak/dms endpoint en credentials_ en _stufzaak.dms stuurgegevens_ van het **detailscherm van de gemeente waar de zaak speelt** (beheertegel _Gemeentes_) waarbij:

- Voor de Ontvanger_administratie geldt dat als de kolom _Tekst_ van de instelling _Sectie: Koppeling ZAAK_ en _Item: GemeenteIDAlsOntvangerAdm_ bestaat en is aangevinkt, dat dan in het bericht het stuurgegeven ontvanger administratie gevuld wordt met de gemeente-id van de locatie waar de zaak zich afspeelt.
- Voor de Zender_administratie geldt dat als de kolom _Tekst_ van de instelling _Sectie: Koppeling ZAAK_ en _Item: GemeenteIDAlsZenderAdm_ bestaat en is aangevinkt, dat dan in het bericht het stuurgegeven zender administratie gevuld wordt met de gemeente-id van de locatie waar de zaak zich afspeelt.

Indien alhier het endpoint vrije berichten en het endpoint asynchroon gevuld zijn dan neemt het programma de credentials en stuurgegevens over van deze kaart.

Een uitzondering hierop is de situatie dat een zaak speelt bij een gemeente die gedefinieerd is in een compartiment terwijl de zaak zelf niet door dat compartiment wordt behandeld, maar door de host. In dat laatste geval valt OpenWave terug op de algemene stufzaak/DMS instellingen uit tbinitialisatie (beheertegel _Configuratie_). Dat is ook het geval indien in tb33gemeente geen instellingen worden gevonden. Dan valt het programma terug op de volgende configuratie-instellingen van _Sectie: KoppelingDOCNAARDMS_:

- _Item: Ontvangstadres_VrijeBerichten_ moet gevuld zijn met het endpoint van de ontvanger t.b.v. genereerZaakidentficatie bericht
- _Item: Ontvangstadres_Asynchroon_ moet gevuld zijn t.b.v. creeerzaak bericht
- _Item: Ontvanger_applicatie_. De kolom _Tekst_ met de ontvanger (ook verplicht)
- _Item: Ontvanger_organisatie_. De kolom _Tekst_ met de organisatie (ook verplicht)
- _Item: Zender_applicatie_. De kolom _Tekst_ met de ontvanger (ook verplicht)
- _Item: Zender_organisatie_. De kolom _Tekst_ met de organisatie (ook verplicht)
- _Item: Ontvanger_administratie_. De kolom _Tekst_ met de administratie. Echter, indien de instelling _Sectie: Koppeling ZAAK_ en _Item: GemeenteIDAlsOntvangerAdm_ bestaat, is aangevinkt en _Getal1_ waarde 1 heeft dan wordt in het bericht het stuurgegeven ontvanger administratie gevuld met de gemeente-id van de locatie waar de zaak zich afspeelt
- _Item: Zender_administratie_. De kolom _Tekst_ met de administratie. Echter, indien de instelling _Sectie: Koppeling ZAAK_ en _Item: GemeenteIDAlsZenderAdm_ bestaat, is aangevinkt en _Getal1_ waarde 1 heeft dan wordt in het bericht het stuurgegeven zender administratie gevuld met de gemeente-id van de locatie waar de zaak zich afspeelt
- _Item: Zender_gebruiker_. De kolom _Tekst_ met de gebruiker
- Als de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: **HTTPAuthenticatie**Naam_ bestaat en is aangevinkt dan wordt de verzending over HTTPS geautoriseerd met :
  - authenticatienaam is kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: HTTPAuthenticatieNaam_
  - authenticatiepass is kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: HTTPAuthenticatiePass_ Zie ook: [2-way encryptie van externe wachtwoorden](/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md)
  - In de kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: HTTPAuthenticatieType_ kan desgewenst het authenticatietype worden ingevuld: Basic (default) of NTLM (versie 1)
  - In de kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: Domein_ kan desgewenst het domein worden ingevuld
- Indien er gebruik moet worden gemaakt van een **client-certificaat** (wordt geplaatst op de CONF-map van de WSAS server) dan:
  - moet de (file)-naam van dat certificaat worden opgeslagen in de kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS en Item: ClientCertificaatNaam_
  - het certificaat password in de kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS en Item: CertificaatPassword_ Zie ook: [2-way encryptie van externe wachtwoorden](/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md)
  - het certificaattype in de kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS en Item: CertificaatType_ (default PKCS12).

### Overige instellingen

Indien de instelling _Sectie: KoppelingDOCNAARDMS en Item: AllowAllHostnameVerifier_ aangevinkt is zal de OpenWave Cloud instemmen met een self-signed of verlopen certificaat bij een verbinding onder https.

In de kolom _Tekst_ van de instelling met _Sectie: KoppelingDOCNAARDMS_ en _Item: Charset_ kan opgegeven worden welke charset in de https header wordt gebruikt bijv. UTF-8 (default is dat ISO-8859-1). Ongeacht de waarde van de charset-instelling kan indien gewenst ervoor gezorgd worden dat uitgaande berichten van OpenWave naar het DMS ontdaan worden van diakritische tekens indien de instelling _Sectie: KoppelingDOCNAARDMS en Item: UitgaandWin1252_ aangevinkt wordt.

Indien _Sectie: KoppelingDOCNAARDMS_ Item: **Ontvangstdatuminedclk01** aangevinkt is zal bij de upload altijd de tag ontvangstdatum worden gevuld met de datum van vandaag. Bij een compartiment kijkt het programma naar de waarde van de kolom dlontvangstdatuminedclk01 bij dat compartiment.

De verwerking soort van de gerelateerde bij IsRelevantVoor van het Voegzaakdocument bericht is instelbaar vanwege interpretatieverschillen StUF standaard, in de kolom _Getal1_ van _Sectie: KoppelingDOCNAARDMS en Item: HTTPSoapAction_voegZaakdocumentToe_Lk01_:

- Indien leeg of ongelijk aan 1, 2 of 3 dan 'T'
- indien 1 dan ook 'T'
- indien 2 dan 'I'
- indien 3 dan 'W'.

Het gaat dus om de "W" in onderstaand stukje.

```xml
<ns:isRelevantVoor StUF:entiteittype="EDCZAK" StUF:sleutelOntvangend="?" StUF:verwerkingssoort="T">
      <ns:gerelateerde StUF:entiteittype="ZAK" StUF:sleutelOntvangend="?" StUF:verwerkingssoort="W">
                <ns:identificatie>123</ns:identificatie>
      </ns:gerelateerde>
  </ns:isRelevantVoor>
```

## Logging

De berichten kunnen gelogd worden op 2 manieren:

- Loggen in tbMessagelog (beheertegel _Messagelog_). Deze logging staat aan indien de instelling aangevinkt is van _Sectie: OWB_ en _Item: MessageLog_. In kolom _Getal1_ van deze instelling staat het aantal dagen dat de loggingskaarten bewaard moeten blijven. Default is dat 31.
- Indien de instelling _Sectie: OWB_ en _Item: Loggen_ aangevinkt is dan worden de berichten onder een door OpenWave te bepalen naam (bijvoorbeeld 1.1345123012_VanOW_naarZaak) op een logmap van de server geplaatst (om die te zien zijn dus systeembeheerrechten noodzakelijk).

## Programmaflow

Nadat de wizard voor het aanwijzen van up te loaden files is afgesloten, gebeurt het volgende:

- De [Upload Lijst](/probleemoplossing/module_overstijgende_schermen/uploads_lijst.md) wordt geopend waarin alle aangewezen files in principe de status klaargezet hebben. De inlogger moet zelf de refreshknop linksonder gebruiken om de voortgang te kunnen monitoren
- de aangewezen up te loaden files worden één voor één opgehaald van het device (of van netwerk wat daaraan verbonden is) van de inlogger en geplaatst op een webserver map
- zo gauw een file volledig binnen is gestreamd dan wacht de webserver y milliseconden (dat instelbare interval _Getal1_ van _Sectie: OWB_ en _Item:VertragingMilSecUploadFile_) en roept de OpenWave API aan dat er een file X klaar staat op de webserver
- de API verandert de betreffende regel van file X in de uploadtabellijst van status _klaargezet_ naar _wordt_momenteel_geupload_
- de API pakt de file X en zet deze om in base64 en verzendt deze met stufzaak/DMS genereerdocumentidentificatie en voegzaakdocumenttoe (in het stuurgegeven tijdstipbericht staat het exacte tijdstip waarop dat gebeurd is).
- Als er een bevestigingsbericht komt van zaak/DMS dan:
  - verandert de API de betreffende regel van file X in de uploadtabellijst van _wordt_momenteel_geupload_ naar _verzonden_ (of mislukt)
  - wordt een kaart in de messagelog aangemaakt (indien zo ingesteld) met date/time van dat moment.

Die API's van de webserver naar zaak/DMS kunnen dus gelijktijdig lopen, met een startinterval van minimaal 5 seconden.

## Testen met fake endpoint

De opmaak van de uitgaande berichten (genereerdocumentidentificatie en voegzaakdocumenttoe) kan getest worden zonder dat er een luisterend ontvangstadres is, door de instelling _Sectie: KoppelingDOCNAARDMS en Item: TestOpFakeEndpoint_ aan te vinken. Als ontvangstadres_vrijeberichten en ontvangstadres_asynchroon kan dan bijvoorbeeld [www.rem.nl](http://www.rem.nl.md) ingevoerd worden. OpenWave genereert in dit geval zelf een unieke documentidentificatie waarmee dan een voegzaakdocumenttoe wordt gemaakt. In de messagelog is deze te zien.
