# Verwerken OLO-bijlagen vanuit digi-koppelaar

Voor het uploaden vanuit de digi-koppelaar van OLO-bijlagen naar OpenWave is een endpoint aanwezig.

Authenticatie op het endpoint vindt plaats met een username en password, met HTTP AUTH Basic. De bestanduploads hebben per upload twee parameters nodig: de filename en het OLO-nummer waar het bestand bij hoort.
De bestandsupload is een POST request (enctype="multipart/form-data). De twee parameters kunnen in de POST payload of als GET parameter worden meegestuurd.

Een voorbeeld:

- a) filename='test.docx'
- b) OLO-nummer='0123456789'
- Een voorbeeldaanroep in het geval van een request met twee GET parameters: `[https://[serveradres]/OLO_upload/olo_upload.php?filename=test.docx&amp;olonummer=0123456789](https://[serveradres]/OLO_upload/olo_upload.php?filename=test.docx&amp;olonummer=0123456789)`

## Verwerken OLO-bijlagen

![](applicatiebeheer/probleemoplossing/programmablokken/olodso_bijlages.png){ class="media" loading="lazy" alt="" width="700" }

De olo_upload.php-luisterservice plaatst de binnengekomen file op een andere map op de webserver.
Deze map is gedefinieerd in kolom _Tekst_ van de instelling: _Sectie: OWB Item: TussenMapOloUploadfiles_.
In de kolom _Tekst_ staat de mapnaam op de webserver: deze mapnaam MOET eindigen op de karakterreeks: '/openwave/uploadolo/' en beginnen met een '/'.
De luisterservice roept hiertoe de API getAuthorisation aan en daarna met de verkregen sessie-sleutel de API geefInstellingen (om de OloUploadmap op te halen) en tenslotte de API Uploadfile.

Adres en poort waar deze OpenWave API's staan te luisteren staan in de map config in de file openwave.ini op dezelfde machine als de luisterservice. Dit is een systeembeheerinstelling.

De user/pass waarmee getAuthorisation aangeroepen wordt (dezelfde als afgesproken met de leverancier van het document) moet wel opgenomen zijn in de medewerkerstabel waarbij:

- de user toegang moet hebben tot de browserversie
- EN _passworddatum verloopt nooit_ aangevinkt is
- EN de kolom _2-factor authentication opheffen_ aangevinkt is
- EN de user lid is van een rechtengroep die minimaal bij de omgevingszaken het recht _Creëren en uploaden documenten_ aangevinkt heeft staan
- EN de user lid is van een rechtengroep die minimaal op één van de modules (bouw/sloop, horeca, handhavingen, APV/overig/ milieu/gebruik/ info, omgeving of inrichtingen) kijkrechten heeft.

Alle overige rechten kunnen dus uitgevinkt staan voor deze medewerker.

De luisterservice roept nu per document de API uploadfile aan.
De API uploadfile moet - naast de parameter paramidentifier met daarin de filenaam - voorzien worden van de parameter paramauto die aangeeft welk automatisch proces een document probeert op te slaan. Het luisterproces geeft de waarde 'OLO' door en als paramidentifier de documentnaam opgebouwd volgens het masker olonr_filenaam.
Dus bijvoorbeeld 123456_Plaatje.jpg.

Zo gauw de API uploadfile de focus heeft worden alle files die op de _TussenMapOloUploadfiles_ staan en die een filedatum/timestamp hebben ouder dan het aantal uren hetgeen is ingesteld in _Getal1_ van de instelling van _Sectie: OWB_ en _Item: MaxUurUpload_, verwijderd.

Het OLO-nummer wordt gebruikt om de Omgevingszaak te traceren (tbomgvergunning.dvlvonr) en daarbij eventueel het nodige externe zaak/DMS nummer op te halen (dvintzaakcode). Aangezien deze laatste ook door automatische processen worden aangemaakt kan er een vertraging wenselijk zijn: als het programma het OLO-nummer niet kan vinden of aan het OLO-nummer is nog geen externe zaakidentificatie gekoppeld dan kan in een loop nog een aantal maal een poging worden gedaan.
Deze loop is qua aantal en wachtduur instelbaar met de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: WachtOpExtAantalSeconden_. In *Getal1*staat het aantal seconden dat gewacht wordt (default 2, maar aanbevolen: 180) alvorens opnieuw te zoeken en in _Getal2_ staat het aantal maal dat dat herhaald mag worden (default 5, maar aanbevolen: 3).

Er is een extra instelling m.b.t. OLO-nummer en prefix bij Vooroverleg. De kolom _Tekst_ van de instelling _Koppeling OLO en Item: Vooroverleg_ moet dan gevuld zijn met een tekst waarvan de lengte kleiner of gelijk 5 is. OpenWave kijkt of het OLO-nummer bestaat. Zo ja, dan worden de documenten bij de omgevingskaart met dat OLO-nummer geplaatst. Zo nee, dan kijkt OpenWave of er een prefix is ingesteld en – indien dat het geval is EN de instelling _Sectie: Koppeling OLO_ en _Item: Vooroverleg_ is ook aangevinkt – dan wordt het OLO-nummer nogmaals gezocht met de prefix eraan vastgeplakt.

Indien:

- er op één OLO-nummer meerdere adviesaanvragen (vrgDi01AanvragenAdvies) binnenkomen, waarbij ook meerdere zaken worden aangemaakt (instelling _Sectie: Koppeling OLO Item: MeerdereAdviesaanvragen_ is aangevinkt)
- EN dat de bijlages eerder worden verwerkt dan het leverenaanvraag bericht van dat OLO-nummer (omvDu01LeverenAanvraag), hetgeen OpenWave niet in de hand heeft

kan het zijn dat er extra controle nodig is om ervoor te zorgen dat de bijlages niet bij de verkeerde zaak terechtkomen.
OpenWave kan die extra check doen indien bijlages ook worden geregistreerd in tbcorrespondentie (indien dus _Sectie: Documentregisteren en Item: AlleOLODSOUploads_ is aangevinkt). OpenWave kijkt - indien ook de instelling _Sectie: Koppeling OLO en Item: CheckOpDubbeleDocumentnaam_ is aangevinkt - in dat geval of de documentnaam reeds voorkomt in de geregistreerde documenten bij de gevonden zaak (kolom dvdocfilenaam). Zo ja, dan wordt het document niet geplaatst en wel een kaart gemaakt in tabel mislukte OLO/DSO-bijlages.

Het daadwerkelijk plaatsen van de file (op fileshare, of cmis of Stuf zaak/DMS) gaat gelijk aan het beschrevene in het lemma [Upload document(en)](/docs/probleemoplossing/programmablokken/upload_document.md), waarbij het volgende extra geldt:

- bij plaatsing via CMIS of fileshare kijkt het programma naar de unieke map gedefinieerd door _Sectie: AanmaakMappen_ en _Item begint met 'Omgeving\__' EN _Getal2_ = 1
- bij plaatsing via STUF Zaken kijkt het programma wat betreft het documenttype indien er GEEN compartiment van toepassing is naar kolom _Tekst_ van instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: OloDocType_ (defaultwaarde 'OLO'), indien er WEL compartiment van toepassing is naar de tekst in het veld OLO/DSO documenttype in het detailscherm van de compartimentsrechten in het beheerportaal-Nieuw
- bij plaatsing via STUF Zaken kijkt het programma ook wat betreft metadata vertrouwelijkheid indien er GEEN compartiment van toepassing is naar kolom _Tekst_ van instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: OloVertrouwelijkheid_ (defaultwaarde 'OPENBAAR') en indien er WEL compartiment van toepassing is naar de tekst in het veld OLO/DSO vertrouwelijkheid in het detailscherm van de compartimentsrechten in het beheerportaal-Nieuw
- wat betreft Auteur bij StUF zaken: deze krijgt de waarde onbekend
- indien zowel is ingesteld dat documenten op de fileserver geplaatst kunnen worden als in een DMS, dan zullen de OLO-bijlages in het DMS worden geplaatst, tenzij de instelling _Sectie: Koppeling OLO en Item: BestandenNaarFileserver_ aangevinkt is: dan krijgt de fileserver-variant de voorkeur.

### Automatische registratie van document

Indien de zaak speelt in een compartiment dan kijkt OpenWave naar of de kolom _OLO/DSO uploads registreren_ (tbcompartiment.dldocregalleolodsouploads) aangevinkt is bij het betreffende compartiment onder de tegel compartimentsrechten in beheerportaal-Nieuw kolom Gebruikers. Indien de zaak NIET speelt in een compartiment dan kijkt OpenWave naar de instelling _Sectie: Documentregisteren_ en _Item: AlleOLODSOUploads_. Aangevinkt dan wordt van de bijlage automatisch een registratie gemaakt in tbcorrespondentie met:

- **Documenttype** (dvdoctype_oms) indien GEEN compartiment met kolom _Tekst_ van Instelling _Sectie: KoppelingDOCNAARDMS Item: OloDocType_ (defaultwaarde 'OLO'), indien WEL compartiment met kolom OLO/DSO documenttype in het detailscherm van de compartimentsrechten in het beheerportaal-Nieuw
- **Definitief** met indien _Getal1_ van de instelling _Sectie: Documentregisteren en Item: AlleOLODSOUploads_ aangevinkt is, met (N)ee, anders met (J)a
- **Richting** met (B)innenkomend
- **Vertrouwelijkheid** indien GEEN compartiment met kolom _Tekst_ van Instelling _Sectie: KoppelingDOCNAARDMS Item: OloVertrouwelijkheid_ (defaultwaarde = 'openbaar'), indien WEL compartiment met kolom OLO/DSO vertrouwelijkheid in het detailscherm van de compartimentsrechten in het beheerportaal-Nieuw
- dvomschrijving met de waarde van kolom dvomschrijving van de corresponderende kaart uit de tabel tbomgoloberichten (de tabel met opgesomde documenten uit het DSO-verzoekbericht of OLO-aanvraagbericht).

### Technische instelling

WSAS moet benaderd worden op poort 9763(HTTP), dit is een onopgeloste bug. Op poort 9443(HTTPS) werkt het upload.php script niet.
Voer de instellingen in de PHPcake configuratie "openwave.ini" in als volgt:

- port = 9763
- use_protocol = http
- use_protocol_endpoint = Http

### Loggen en verwerken van Mislukte OLO/DSO bijlages

OpenWave heeft de volgorde van het leveren van een verzoek/aanvraag bericht en bijlages niet in de hand.
Om bijlages te kunnen plaatsen (op de fileshare op grond van een map gemaakt met een OpenWave zaaknummer of in een DMS op grond van een identificatie gekoppeld aan een OpenWave zaaknummer) moet OpenWave eerst het verzoek/aanvraag bericht verwerken tot een zaak.
OpenWave stalt alle binnenkomende bijlages op een temp-map totdat het verzoek/aanvraag bericht binnenkomt. Dan wordt gepoogd alle gestalde bijlages op hun plaats van bestemming te brengen. Deze wachttijd is wel gelimiteerd.

De wachttijd is instelbaar: instelling _Sectie: KoppelingDOCNAARDMS en Item: WachtOpExtAantalSeconden_. _Getal1_ geeft aantal seconden aan dat OpenWave moet wachten alvorens opnieuw te kijken of het verzoek/aanvraag bericht al binnen is en verwerkt. _Getal2_ geeft aan hoeveel keer die wachttijd uitgevoerd mag worden (defaultwaarde _Getal1_ = 2 en _Getal2_ = 5).

De temp-map waar de bijlages zijn gestald wordt automatisch opgeschoond voor documenten die ouder zijn dan een bepaalde timestamp (dit is de instelling _Getal1_ van _Sectie: OWB en Item: MaxUurUpload_. Defaultwaarde 24).

Indien het verzoek/aanvraag bericht pas binnenkomt als de wachttijd al is verstreken, dan wordt de beheertabel _Mislukte Olo-bijlagen_ gevuld voor het betreffende document.

Dit proces gaat in de regel goed wanneer er niet al te veel bijlages bij een OLO/DSO aanvraag zitten. Bij grote aantallen (80 of meer documenten bij één zaak; maar ook afhankelijk van de grootte van de documenten) kunnen er echter problemen ontstaan zeker indien de wachttijd instelling te ruim is.

Een te grote instelling (Getal1 x Getal2 > 5 minuten) kan een time-out problemen geven. Zeker in het geval dat de documenten ook nog doorgezet moeten worden naar een DMS (daar zit ook een wachttijd op aanvragen identificatiecode). Bij een time-out wordt ook de tabel met mislukte OOLO-bijlagen niet meer bijgewerkt.

### Advies

Daarom het volgende advies, indien uw organisatie OLO/DSO zaken krijgt te verwerken:

- Stel _Getal1_ van _Sectie: OWB en Item: MaxUurUpload_ in op 168 uur.
- Stel _Getal1_ van _Sectie: KoppelingDOCNAARDMS en Item: WachtOpExtAantalSeconden_ in op 180.
- Stel _Getal2_ van _Sectie: KoppelingDOCNAARDMS en Item: WachtOpExtAantalSeconden_ in op 3.
- Vink de instelling _Sectie: KoppelingDOCNAARDMS en Item: CloseConnectionOloDso_ aan.

Dit betekent dat:

- niet geplaatste OLO-DSO bijlages een week lang blijven staan op de temp-map alvorens ze automatisch worden verwijderd
- OpenWave bij het verwerken van bijlages slechts drie keer kijkt of er al een zaak is aangemaakt (in het begin en na 3 minuten en dan nogmaals na 3 minuten). Is de zaak er niet dan wordt een nieuwe regel in de tabel mislukte OLO-bijlages gemaakt met de betreffende documentverwijzing.
- In de drie minuten tussentijd wordt de databaseconnectie voor dat ene document gesloten.

In het beheerportaal _Operations_ is een tegel gekomen: _Verwerken Mislukte OLO-bijlages_. De tegel start een wizard die probeert de niet-verwerkte bijlages die mogelijk nog steeds op de temp-map staan (MaxUurUpload!) alsnog te plaatsen. Dit is een runnable (proces zonder userinterface). Resultaat is te zien in de memo van de betreffende kaart in operationslog (ook in operationsportal).

### Zelf ophalen uit FTP-site

Zie knop **Ophalen ontbrekende OLO-documenten van FTPS-site** bij [OLO/DSO/AIM Bijlage verwijzingen](/docs/probleemoplossing/module_overstijgende_schermen/olo-aim_bijlage_verwijzingen.md).
