Upload documenten met StUF zaak/DMS
===================================

Indien gewerkt wordt met Stuf-Zaken (zaak/DMS koppeling) dan wordt per
up te loaden document een genereerDocumentidentificatie_di02 en een
voegZaakDocument_Lk01 bericht uitgestuurd.

Noodzakelijke Instellingen
--------------------------

De externe zaak/DMS code van de zaak moet gevuld zijn (dvintzaakcode).

-  Voor de omgevingszaken, handhaving, inrichting, bouw/sloop en
   APV/overig kijkt het programma hiertoe naar de zaak zelf.
-  Bij inspecties, kijkt het programma of de moduleletter (W = omgeving,
   V = inrichting, H = handhaving, O = APV/overig) voorkomt in de kolom
   *Info* van de instelling *Sectie: Koppeling Zaak Item:
   ZaaktypeInspectietraject*:

   -  is dat het geval dan kijkt het programma naar de externe zaak/DMS
      code van de bijbehorende hoofdzaak (dus omgeving, handhaving,
      overig, inrichting, horeca)
   -  is dat niet het geval dan dan kijkt het programma naar de externe
      zaak/DMS code van de inspectiekaart zelf.

-  Bij bezwaarberoep, kijkt het programma ook naar de zaak/DMS code
   (dvintzaakcode) van de bezwaarberoep kaart zelf.
-  Bij adviezen geldt dat het programma kijkt naar instelling *Sectie:
   Programma* en *Item: AdviesIsZaak*:

   -  indien deze is aangevinkt dan kijkt het programma naar de externe
      zaak/DMS code van de advieskaart zelf
   -  anders (instelling is niet aangevinkt of deze bestaat niet) bij
      adviezen dan kijkt het programma naar de externe zaak/DMS code van
      de bijbehorende hoofdzaak (dus omgeving, handhaving, overig).

Instellingen voor opmaak en adressering
---------------------------------------

Protocol en action
~~~~~~~~~~~~~~~~~~

-  **Methode**

   -  Indien de zaak NIET wordt behandeld door een compartiment dan MOET
      de instelling *Sectie: KoppelingDOCNAARDMS:* en *Item: Methode*
      aangevinkt staan en heeft als *Tekst*: StUF-ZAKEN 310.
   -  Indien de zaak WEL wordt behandeld door een compartiment dan MOET
      de kolom dvdmsmethode bij de compartimentsdefinitie de waarde
      StUF-ZAKEN 310 hebben.

-  **Action**

   -  Instelling *Sectie: KoppelingDOCNAARDMS Item:
      HTTPSoapAction_voegZaakdocumentToe_Lk01*. De kolom *Tekst* moet
      gevuld worden met juiste soapaction:

      -  indien zaak/DMS dan
         ``[http://www.egem.nl/StUF/sector/zkn/0310/voegZaakdocumentToe_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/voegZaakdocumentToe_Lk01.md)``
      -  indien (oude) stufzaken dan
         ``[http://www.egem.nl/StUF/sector/zkn/0310/edcLk01](http://www.egem.nl/StUF/sector/zkn/0310/edcLk01.md)``.

   -  Instelling *Sectie: KoppelingDOCNAAMDMS Item:
      HTTPSoapAction_genereerDocumentIdentificatie_Di02*. De kolom
      *Tekst* moet gevuld worden met juiste soapaction:
      ``[http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02](http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02.md)``.
   -  Instelling *Sectie: KoppelingDOCNAAMDMS Item:
      HTTPSoapAction_updateZaakDocument_Di02*. De kolom *Tekst* moet
      gevuld worden met juiste soapaction:
      ``[http://www.egem.nl/StUF/sector/zkn/0310/updateZaakDocument_Di02](http://www.egem.nl/StUF/sector/zkn/0310/updateZaakDocument_Di02.md)``.
      Deze instelling wordt alleen gebruikt in combinatie met
      OnlyOffice. Wanneer een bestaand StUF document on line wordt
      bewerkt met OnlyOffice dan zal het gewijzigde document via
      updateZaakDocument met de bestaande documentidentifier worden
      aangeboden aan het DMS, in plaats van voegZaakDocumentToe.

LET OP: de soapactions kunnen ook ingesloten moeten zijn door dubbele
quootjes, dus bijv.
``"[http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02](http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02.md)"``.

Endpoint, credentials en stuurgegevens
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Voor het endpoint en de stuurgegevens zal het programma eerst kijken
naar de waarden in de blokken *stuf zaak/dms endpoint en credentials* en
*stufzaak.dms stuurgegevens* van het **detailscherm van de gemeente waar
de zaak speelt** (beheertegel *Gemeentes*) waarbij:

-  Voor de Ontvanger_administratie geldt dat als de kolom *Tekst* van de
   instelling *Sectie: Koppeling ZAAK* en *Item:
   GemeenteIDAlsOntvangerAdm* bestaat en is aangevinkt, dat dan in het
   bericht het stuurgegeven ontvanger administratie gevuld wordt met de
   gemeente-id van de locatie waar de zaak zich afspeelt.
-  Voor de Zender_administratie geldt dat als de kolom *Tekst* van de
   instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsZenderAdm*
   bestaat en is aangevinkt, dat dan in het bericht het stuurgegeven
   zender administratie gevuld wordt met de gemeente-id van de locatie
   waar de zaak zich afspeelt.

Indien alhier het endpoint vrije berichten en het endpoint asynchroon
gevuld zijn dan neemt het programma de credentials en stuurgegevens over
van deze kaart.

Een uitzondering hierop is de situatie dat een zaak speelt bij een
gemeente die gedefinieerd is in een compartiment terwijl de zaak zelf
niet door dat compartiment wordt behandeld, maar door de host. In dat
laatste geval valt OpenWave terug op de algemene stufzaak/DMS
instellingen uit tbinitialisatie (beheertegel *Configuratie*). Dat is
ook het geval indien in tb33gemeente geen instellingen worden gevonden.
Dan valt het programma terug op de volgende configuratie-instellingen
van *Sectie: KoppelingDOCNAARDMS*:

-  *Item: Ontvangstadres_VrijeBerichten* moet gevuld zijn met het
   endpoint van de ontvanger t.b.v. genereerZaakidentficatie bericht
-  *Item: Ontvangstadres_Asynchroon* moet gevuld zijn t.b.v. creeerzaak
   bericht
-  *Item: Ontvanger_applicatie*. De kolom *Tekst* met de ontvanger (ook
   verplicht)
-  *Item: Ontvanger_organisatie*. De kolom *Tekst* met de organisatie
   (ook verplicht)
-  *Item: Zender_applicatie*. De kolom *Tekst* met de ontvanger (ook
   verplicht)
-  *Item: Zender_organisatie*. De kolom *Tekst* met de organisatie (ook
   verplicht)
-  *Item: Ontvanger_administratie*. De kolom *Tekst* met de
   administratie. Echter, indien de instelling *Sectie: Koppeling ZAAK*
   en *Item: GemeenteIDAlsOntvangerAdm* bestaat, is aangevinkt en
   *Getal1* waarde 1 heeft dan wordt in het bericht het stuurgegeven
   ontvanger administratie gevuld met de gemeente-id van de locatie waar
   de zaak zich afspeelt
-  *Item: Zender_administratie*. De kolom *Tekst* met de administratie.
   Echter, indien de instelling *Sectie: Koppeling ZAAK* en *Item:
   GemeenteIDAlsZenderAdm* bestaat, is aangevinkt en *Getal1* waarde 1
   heeft dan wordt in het bericht het stuurgegeven zender administratie
   gevuld met de gemeente-id van de locatie waar de zaak zich afspeelt
-  *Item: Zender_gebruiker*. De kolom *Tekst* met de gebruiker
-  Als de instelling *Sectie: KoppelingDOCNAARDMS* en *Item:*
   **HTTPAuthenticatie**\ *\ Naam* bestaat en is aangevinkt dan wordt de
   verzending over HTTPS geautoriseerd met :

   -  authenticatienaam is kolom *Tekst* van de instelling *Sectie:
      KoppelingDOCNAARDMS* en *Item: HTTPAuthenticatieNaam*
   -  authenticatiepass is kolom *Tekst* van de instelling *Sectie:
      KoppelingDOCNAARDMS* en *Item: HTTPAuthenticatiePass* Zie ook:
      `2-way encryptie van externe
      wachtwoorden </docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md>`__
   -  In de kolom *Tekst* van de instelling *Sectie:
      KoppelingDOCNAARDMS* en *Item: HTTPAuthenticatieType* kan
      desgewenst het authenticatietype worden ingevuld: Basic (default)
      of NTLM (versie 1)
   -  In de kolom *Tekst* van de instelling *Sectie:
      KoppelingDOCNAARDMS* en *Item: Domein* kan desgewenst het domein
      worden ingevuld

-  Indien er gebruik moet worden gemaakt van een **client-certificaat**
   (wordt geplaatst op de CONF-map van de WSAS server) dan:

   -  moet de (file)-naam van dat certificaat worden opgeslagen in de
      kolom *Tekst* van *Sectie: KoppelingDOCNAARDMS en Item:
      ClientCertificaatNaam*
   -  het certificaat password in de kolom *Tekst* van *Sectie:
      KoppelingDOCNAARDMS en Item: CertificaatPassword* Zie ook: `2-way
      encryptie van externe
      wachtwoorden </docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md>`__
   -  het certificaattype in de kolom *Tekst* van *Sectie:
      KoppelingDOCNAARDMS en Item: CertificaatType* (default PKCS12).

Overige instellingen
~~~~~~~~~~~~~~~~~~~~

Indien de instelling *Sectie: KoppelingDOCNAARDMS en Item:
AllowAllHostnameVerifier* aangevinkt is zal de OpenWave Cloud instemmen
met een self-signed of verlopen certificaat bij een verbinding onder
https.

In de kolom *Tekst* van de instelling met *Sectie: KoppelingDOCNAARDMS*
en *Item: Charset* kan opgegeven worden welke charset in de https header
wordt gebruikt bijv. UTF-8 (default is dat ISO-8859-1). Ongeacht de
waarde van de charset-instelling kan indien gewenst ervoor gezorgd
worden dat uitgaande berichten van OpenWave naar het DMS ontdaan worden
van diakritische tekens indien de instelling *Sectie:
KoppelingDOCNAARDMS en Item: UitgaandWin1252* aangevinkt wordt.

Indien *Sectie: KoppelingDOCNAARDMS* Item: **Ontvangstdatuminedclk01**
aangevinkt is zal bij de upload altijd de tag ontvangstdatum worden
gevuld met de datum van vandaag. Bij een compartiment kijkt het
programma naar de waarde van de kolom dlontvangstdatuminedclk01 bij dat
compartiment.

De verwerking soort van de gerelateerde bij IsRelevantVoor van het
Voegzaakdocument bericht is instelbaar vanwege interpretatieverschillen
StUF standaard, in de kolom *Getal1* van *Sectie: KoppelingDOCNAARDMS en
Item: HTTPSoapAction_voegZaakdocumentToe_Lk01*:

-  Indien leeg of ongelijk aan 1, 2 of 3 dan 'T'
-  indien 1 dan ook 'T'
-  indien 2 dan 'I'
-  indien 3 dan 'W'.

Het gaat dus om de "W" in onderstaand stukje.

.. code:: xml

   <ns:isRelevantVoor StUF:entiteittype="EDCZAK" StUF:sleutelOntvangend="?" StUF:verwerkingssoort="T">
         <ns:gerelateerde StUF:entiteittype="ZAK" StUF:sleutelOntvangend="?" StUF:verwerkingssoort="W">
                   <ns:identificatie>123</ns:identificatie>
         </ns:gerelateerde>
     </ns:isRelevantVoor>

Logging
-------

De berichten kunnen gelogd worden op 2 manieren:

-  Loggen in tbMessagelog (beheertegel *Messagelog*). Deze logging staat
   aan indien de instelling aangevinkt is van *Sectie: OWB* en *Item:
   MessageLog*. In kolom *Getal1* van deze instelling staat het aantal
   dagen dat de loggingskaarten bewaard moeten blijven. Default is dat
   31.
-  Indien de instelling *Sectie: OWB* en *Item: Loggen* aangevinkt is
   dan worden de berichten onder een door OpenWave te bepalen naam
   (bijvoorbeeld 1.1345123012_VanOW_naarZaak) op een logmap van de
   server geplaatst (om die te zien zijn dus systeembeheerrechten
   noodzakelijk).

Programmaflow
-------------

Nadat de wizard voor het aanwijzen van up te loaden files is afgesloten,
gebeurt het volgende:

-  De `Upload
   Lijst </docs/probleemoplossing/module_overstijgende_schermen/uploads_lijst.md>`__
   wordt geopend waarin alle aangewezen files in principe de status
   klaargezet hebben. De inlogger moet zelf de refreshknop linksonder
   gebruiken om de voortgang te kunnen monitoren
-  de aangewezen up te loaden files worden één voor één opgehaald van
   het device (of van netwerk wat daaraan verbonden is) van de inlogger
   en geplaatst op een webserver map
-  zo gauw een file volledig binnen is gestreamd dan wacht de webserver
   y milliseconden (dat instelbare interval *Getal1* van *Sectie: OWB*
   en *Item:VertragingMilSecUploadFile*) en roept de OpenWave API aan
   dat er een file X klaar staat op de webserver
-  de API verandert de betreffende regel van file X in de
   uploadtabellijst van status *klaargezet* naar
   *wordt_momenteel_geupload*
-  de API pakt de file X en zet deze om in base64 en verzendt deze met
   stufzaak/DMS genereerdocumentidentificatie en voegzaakdocumenttoe (in
   het stuurgegeven tijdstipbericht staat het exacte tijdstip waarop dat
   gebeurd is).
-  Als er een bevestigingsbericht komt van zaak/DMS dan:

   -  verandert de API de betreffende regel van file X in de
      uploadtabellijst van *wordt_momenteel_geupload* naar *verzonden*
      (of mislukt)
   -  wordt een kaart in de messagelog aangemaakt (indien zo ingesteld)
      met date/time van dat moment.

Die API's van de webserver naar zaak/DMS kunnen dus gelijktijdig lopen,
met een startinterval van minimaal 5 seconden.

Testen met fake endpoint
------------------------

De opmaak van de uitgaande berichten (genereerdocumentidentificatie en
voegzaakdocumenttoe) kan getest worden zonder dat er een luisterend
ontvangstadres is, door de instelling *Sectie: KoppelingDOCNAARDMS en
Item: TestOpFakeEndpoint* aan te vinken. Als
ontvangstadres_vrijeberichten en ontvangstadres_asynchroon kan dan
bijvoorbeeld `www.rem.nl <http://www.rem.nl>`__ ingevoerd worden.
OpenWave genereert in dit geval zelf een unieke documentidentificatie
waarmee dan een voegzaakdocumenttoe wordt gemaakt. In de messagelog is
deze te zien.
