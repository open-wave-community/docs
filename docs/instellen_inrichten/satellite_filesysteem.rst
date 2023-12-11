.. _satellite-tbv-benadering-fileserver:

Satellite t.b.v. benadering fileserver
======================================

Indien er verbinding vanuit de Cloud wordt gezocht met een fileserver
voor het uploaden of downloaden van files dan is een installatie van een
aparte OpenWave Satellite-server binnen het LAN noodzakelijk. Indien de
betreffende zaak NIET onder een compartiment valt, dan verwacht het
programma dat deze satellite-server aanwezig is indien de kolom *Tekst*
van *Sectie: Documenten, Item: OphalenViaFileserver* gevuld is met de
waarde *Satellite*.

Indien de betreffende zaak WEL onder een compartiment valt, dan verwacht
het programma dat deze satellite-server aanwezig is indien de kolom
*Satellite (dlsatellite)* van de betreffende compartimentskaart
(beheertegel *Compartiment*) aangevinkt is.

Wanneer de gebruiker vraagt om een lijst van beschikbare mappen, of om
een lijst van beschikbare documenten op één of meer aangewezen mappen,
of om het downloaden dan wel uploaden van één of meer documenten, dan
worden deze vragen vanuit de OpenWave server in de Cloud doorgezet naar
de satellite-server binnen het LAN met SOAP berichten onder https.

Instellingen in tbinitialisatie indien GEEN compartimentszaak
-------------------------------------------------------------

Dit is het geval wanneer documenten up-of gedownload worden bij een zaak
die NIET onder een compartiment valt.

Dit zijn extra instellingen i.v.m. satellite gebruik. De instellingen
zoals beschreven in `Upload documenten naar
fileshare </docs/probleemoplossing/programmablokken/upload_document/upload_naar_fileshare.md>`__
en `Ophalen van
fileshare </docs/probleemoplossing/programmablokken/toon_documenten_en_download/ophalen_van_fileshare.md>`__
zijn dus ook noodzakelijk.

-  **Aan/uit**. de kolom *Tekst* van *Sectie: Documenten, Item:
   OphalenViaFileserver* moet gevuld zijn met de waarde *Satellite*.
-  Het **endpoint** van de satellite staat in kolom *Tekst* van *Sectie:
   Satellite* en *Item: Endpoint_fileserver*. Moet zijn:

``https://xxxx:yyyy/services/nl.rem.satellite.published.Fileserver.nl.rem.satellite.published.FileserverHttpSoap12Endpoint/``

Op de plaats van de xxxx en de yyyy ip.nummer en poort.

-  **Authenticatie**. Indien de instelling *Sectie: Satellite* en *Item:
   HTTPAuthenticatieNaam* aangevinkt is dan gaat de berichten van de
   Cloud naar de satellite onder httpsauthenticatie. De usernaam staat
   in de kolom *Tekst* bij deze HTTPAuthenticatieNaam. Het Password
   staat in kolom *Tekst* onder *Sectie: Satellite* en *Item:
   HTTPAuthenticatiePass* (zie ook: `2-way encryptie van externe
   wachtwoorden </docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md>`__).
-  **Domein** staat in kolom *Tekst* onder *Sectie: Satellite en Item:
   Domain*.
-  **Type versleuteling** staat in kolom *Tekst* onder *Sectie:
   Satellite en Item: HTTPAuthenticatieType* (vooralsnog alleen Basic).
-  **Chunksize**. In *Getal1* van de instelling *Sectie: Satellite* en
   *Item: ChunkMbsize* komt de grootte van de chunks in Mb te staan. Een
   document kan namelijk worden opgeknipt in chunks. Alleen een integer
   is toegestaan. (defaultwaarde = 1 Mb).
-  **Overschrijf file** Indien *Getal1* van *Sectie: Documenten Item:
   OphalenViaFileserver* de waarde 1 heeft dan wordt een eventueel
   bestaande file op de fileserver NIET overschreven: de file wordt in
   dat geval geplaatst onder dezelfde naam met toevoeging (n) zoals
   test(3).txt.
-  **Certificaat**. Indien de instelling *Sectie: Satellite en Item:
   AllowAllHostnameVerifier* aangevinkt is zal de Openwave Cloud
   instemmen met een self-signed of verlopen certificaat van de
   satellite-server bij een verbinding onder https.

Instellingen in tbcompartiment (beheerportaal-Nieuw) indien WEL compartimentszaak
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dit is het geval wanneer documenten up-of gedownload worden bij een zaak
die WEL onder een compartiment valt.

Dit zijn extra instellingen i.v.m. satellite gebruik. De instellingen
zoals beschreven in `Upload documenten naar
fileshare </docs/probleemoplossing/programmablokken/upload_document/upload_naar_fileshare.md>`__
en `Ophalen van
fileshare </docs/probleemoplossing/programmablokken/toon_documenten_en_download/ophalen_van_fileshare.md>`__
zijn dus ook noodzakelijk.

-  **Aan/uit**. de kolom *Satellite (dlsatellite)* van de betreffende
   compartimentskaart moet aangevinkt zijn.
-  Het **endpoint** van de satellite staat in kolom *endpoint* van blok
   satellite op de compartimentskaart. Moet zijn:

``https://xxxx:yyyy/services/nl.rem.satellite.published.Fileserver.nl.rem.satellite.published.FileserverHttpSoap12Endpoint/``

Op de plaats van de xxxx en de yyyy ip.nummer en poort.

-  **Authenticatie**. Indien de kolom *HTTPAuthenticatieNaam* gevuld is
   dan gaat de berichten van de Cloud naar de satellite onder
   httpsauthenticatie.

   -  De usernaam voor htttps-authenticatie staat in deze kolom
      *HTTPAuthenticatieNaam*.
   -  Het Password staat in kolom *HTTPAuthenticatiePass* onder blok
      satellite op de compartimentskaart (zie ook: `2-way encryptie van
      externe
      wachtwoorden </docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md>`__).
   -  Het Type versleuteling staat in kolom *HTTPAuthenticatieType*
      (vooralsnog alleen Basic).
   -  de inhoud van de kolom *username toegang satellite-ini*
      (dvsatelfileserveruser) wordt vergeleken met de *api-name* van de
      satellite ini-file. In die ini-file staat de echte toegangsnaam
      voor de fileserver die aan de satellite is verbonden.
   -  de inhoud van de kolom *password toegang satellite-ini*
      (dvsatelfileserveruser) wordt vergeleken met de *api-pass* van de
      satellite ini-file. In die ini-file staat de echte toegangspass
      voor de fileserver die aan de satellite is verbonden.

-  **Domein** staat in kolom *Domain* onder blok satellite op de
   compartimentskaart. Met domein wordt bedoeld het domein van de server
   waar de satellite is geplaatst.
-  **Chunksize**. In kolom *Chunksize* onder blok satellite op de
   compartimentskaart komt de grootte van de chunks in Mb te staan. Een
   document kan namelijk worden opgeknipt in chunks. Alleen een integer
   is toegestaan (defaultwaarde = 1 Mb).
-  **Overschrijf file** Indien deze kolom NIET is aangevinkt dan wordt
   een eventueel bestaande file op de fileserver NIET overschreven: de
   file wordt in dat geval geplaatst onder dezelfde naam met toevoeging
   (n) zoals test(3).txt.
-  **Certificaat**. Indien de kolom *AllowAllHostnameVerifier*
   aangevinkt is zal de Openwave Cloud instemmen met een self-signed of
   verlopen certificaat van de satellite-server bij een verbinding onder
   https.

Methodes
~~~~~~~~

Deletemap
^^^^^^^^^

Met deze methode verwijdert een hele map:

-  paramlogin: toegangsnaam voor satellite
-  parampass: password voor satellite
-  parammap: de relatieve mapnaam (dus zonder documentmetroot aan de
   voorkant). De mapnaam begint niet met een backslash dus bijvoorbeeld
   wel wave\\omgeving\\2345
-  parammustexists: true of false. Indien true dan controleert de
   satellite eerst of de map bestaat.

De methode retourneert 402 indien parammustexists - true en de map niet
bestaat; 0 indien gelukt en 400 indien fileserver niet benaderbaar is.

fileExist
^^^^^^^^^

Met deze methode controleert de satellite of een bepaalde file aanwezig:

-  paramlogin: toegangsnaam voor satellite
-  parampass: password voor satellite
-  paramfile: de relatieve mapnaam MET een filenaam daaraan vast. De
   mapfilenaam begint niet met een backslash dus bijvoorbeeld wel
   *wave\\omgeving\\2345\\test.txt*. De methode retourneert 402 indien
   paramfile niet bestaat; 0 indien wel bestaat en 400 indien fileserver
   niet benaderbaar is.

getfile
^^^^^^^

Wanneer vanuit de Cloud een document moet worden opgehaald van de
fileserver dan wordt het document opgeknipt in chunks ter grootte van de
chunksize-instelling hierboven (LET OP: moet een integer zijn). Voor
elke chunk wordt vanuit de Cloud de satellite-functie getfile
aangesproken met de parameters:

-  paramlogin: toegangsnaam voor de satellite:
-  parampass: password voor de satellite (plain)
-  paramfile: de relatieve mapnaam MET de op te halen filenaam daaraan
   vast. Deze relatieve mapnaam is de mapnaam die meegekomen is in de
   result set van het opvragen van de lijst van documenten (Toon
   documentenlijst via satellite: getfilelist), waar de documentroot
   (kolom *Tekst* van *Sectie: Documenten, Item: DocumentRoot*) vanaf is
   gehaald. De mapfilenaam begint niet met een backslash dus wel goed is
   bijvoorbeeld 'omgeving\\2345\\test.txt'
-  paramchunkid is een integer. Van de file wordt het nde deel
   opgevraagd (dat is paramchunkid) gebaseerd op eenheden van
   paramchunkmbsize groot
-  paramchunkmaxmbsize is de maximale grootte van de op te vragen chunks
   uitgedrukt in megabyte (integer).

De satellite-server heeft een eigen ini-file waarin de documentroot is
gedefinieerd. Deze wordt voor de relatieve mapnaam gevoegd. Het
programma past zelf de slashes/backslashes aan afhankelijk van de
machine waarop de satellite is geïnstalleerd.

Het Cloud-programma weet uit de result set van de toon documentenlijst
de exacte grootte in bytes van het op te vragen document. Per chunk
wordt een gedeelte van het gevraagde document opgevraagd op basis van
paramchunkmaxmbsize en de satellite levert dat gedeelte in base64
tezamen met de exacte grootte in bytes van dat stukje file. Als alle
stukjes geleverd zijn worden deze in de Cloud (geontbased64) aan elkaar
geplakt en op de server-downloadmap geplaatst waarna deze via de browser
van de gebruiker op zijn device download terechtkomt.

getfilelist
^^^^^^^^^^^

Wanneer vanuit de Cloud een lijst wordt gevraagd van documenten of
mappen dat wordt de satellite-functie getfilelist aangesproken met de
volgende parameters:

-  paramlogin: toegangsnaam voor de satellite:
-  parampass: password voor de satellite (plain)
-  paramfolder: naam van map waarvan de filenamen met achterliggende
   mapnamen opgevraagd wordt. Indien meer dan één uitgangsmap dan zijn
   deze gescheiden door puntkomma. De mapnamen zijn relatieve mapnamen
   t.o.v. een documentroot (kolom *Tekst* van *Sectie: Documenten, Item:
   DocumentRoot*). Deze documentroot maakt GEEN deel uit van de
   mapnamen. De mapnamen beginnen niet met een backslash dus wel goed is
   bijvoorbeeld 'omgeving\\2345' of 'omgeving\\2345;\\apv\\30498'
-  paramrecurse is een getal: 0=oneindig aantal niveaus diep, 1=alleen
   huidige laag, 2=incl. 1 laag submappen, enz). Indien ontbreekt dan de
   default waarde 0 nemen. We gebruiken vooralsnog alleen 0
-  paramfilter: mag leeg zijn wordt (nog) niet gebruikt.

De satellite-server heeft een eigen ini-file waarin de documentroot is
gedefinieerd. Deze wordt voor de relatieve mapnamen uit paramfolder
gevoegd. Het programma past zelf de slashes/backslashes aan afhankelijk
van de machine waarop de satellite is geïnstalleerd.

De satellite kijkt op de fileshare naar de aanwezige files op de mappen
van paramfolder en alle onderliggende mappen en retourneert de
bevindingen. Indien echter de instellingen *geensubmapmetsubstring1* of
*geensubmapmetsubstring21* of *geensubmapmetsubstring3* in de
satellite.ini bestaan en gevuld zijn dan worden de submappen waarin deze
waardes voorkomen overgeslagen.

In de Cloud wordt deze resultaat set van alle files zo nodig gefilterd
op de daarin voorkomende mappen zodat de gebruiker eerst één of meer
mappen kan aanwijzen en vervolgens alleen van deze mappen de documenten
kan opvragen. Per aangetroffen document retourneert de satellite:

-  id: Map en naam van document (zonder documentroot) bijv.
   'Omgeving/2010/2010VP028/aivd.png'
-  titel: naam van het document bijv. aivd.png
-  creatiedatum: bijv. 2018-01-18
-  grootte: dit is de grootte in MB bijv. 0.339
-  map: wederom zonder documentroot bijv. 'Omgeving/2010/2010VP028'

makedir
^^^^^^^

Wanneer vanuit de Cloud een map moeten worden aangemaakt op de
fileserver (vanaf satelliteversie 1.1) wordt de satellite-functie
*makedir* aangesproken met de parameters:

-  paramlogin: toegangsnaam voor de satellite:
-  parampass: password voor de satellite (plain)
-  paramdir: de relatieve mapnaam. Deze relatieve mapnaam is een mapnaam
   waar de documentroot (kolom *Tekst* van *Sectie: Documenten, Item:
   DocumentRoot*) vanaf is gehaald. De mapnaam begint niet met een
   backslash dus wel goed is 'omgeving\\2345'.

movecopydelfile
^^^^^^^^^^^^^^^

Wanneer vanuit de Cloud een map moeten worden verplaatst of verwijderd
op de fileserver (vanaf satellite versie 1.1) wordt de satellite-functie
*movecopydelfile* aangesproken met de parameters:

-  paramlogin: toegangsnaam voor de satellite:
-  parampass: password voor de satellite (plain)
-  paramfilebron: De relatieve mapnaam (mapnaam zonder documentroot) MET
   een filenaam daaraan vast van het document waarop een actie wordt
   uitgevoerd. De mapfilenaam begint niet met een backslash dus
   bijvoorbeeld wel 'wave\\omgeving\\2345\\test.txt'
-  paramaction heeft de waarde 1, 2 of 3:

   -  1 dat betekent verplaatsen van paramfilebron naar parafiledoel
   -  2 kopiëren van paramfilebron naar paramfiledoel
   -  3 delete paramfilebron

-  paramfiledoel: de relatieve mapnaam MET een filenaam daaraan vast. De
   mapfilenaam begint niet met een backslash dus bijvoorbeeld wel
   'wave\\oudkanweg\\test.txt' Indien paramaction = 3 moet deze
   parameter een lege waarde hebben
-  paramoverschrijf: true of false. Indien false dan mag een bestaande
   file niet worden overschreven, maar moet ie toegevoegd worden onder
   bijv. test(2).txt (alleen van toepassing bij paramaction 1 en 2).

putfile
^^^^^^^

Wanneer vanuit de Cloud een document moet worden geplaatst op de
fileserver dan wordt het document opgeknipt in chunks ter grootte van de
chunksize-instelling hierboven (LET OP: moet een integer zijn). Voor
elke chunk wordt vanuit de Cloud de satellite-functie *putfile*
aangesproken met de parameters:

-  paramlogin: toegangsnaam voor de satellite:
-  parampass: password voor de satellite (plain)
-  paramfile: De relatieve mapnaam MET een filenaam daaraan vast. Deze
   relatieve mapnaam is de mapnaam uit *Sectie: AanmaakMappen*, die bij
   het uploaden al of niet automatisch is aangewezen, waar de
   documentroot (kolom *Tekst* van *Sectie: Documenten, Item:
   DocumentRoot*) vanaf is gehaald. De mapfilenaam begint niet met een
   backslash dus wel goed is bijvoorbeeld 'omgeving\\2345\\test.txt'
-  paramoverschrijf: true of false. Indien false dan mag een bestaande
   file niet worden overschreven, maar moet ie toegevoegd worden onder
   bijv. test(2).txt
-  paramchunkid is een integer. Van de file wordt het nde deel geleverd
   (dat is paramchunkid) gebaseerd op eenheden van paramchunkmbsize
   groot
-  paramtotalbytesize: is de grootte van de geheel te transporteren file
   in bytes (dus niet per se alleen van het stukje dat nu ontvangen
   wordt)
-  paramlastchunkid: is de laatste chunkid (n) ofwel het aantal chunks
   dat geleverd gaat worden
-  parambase64 is de inhoud van de chunk in base64.

De satellite-server heeft een eigen ini-file waarin de documentroot is
gedefinieerd. Deze wordt voor de relatieve mapnaam gevoegd. Het
programma past zelf de slashes/backslashes aan afhankelijk van de
machine waarop de satellite is geïnstalleerd.

Het programma plaats alle (ontbased64) chunks op de daartoe bestemde map
(maakt deze zo nodig aan) met de filenaam gevolgd door '*filepart*' +
paramchunkid. Als alle chunks binnen zijn worden de fileparts
samengevoegd tot de bedoelde filenaam en verwijderd.

De satellite-server heeft een eigen ini-file waarin de documentroot is
gedefinieerd. Deze wordt voor de relatieve mapnaam gevoegd. Het
programma past zelf de slashes/backslashes aan afhankelijk van de
machine waarop de satellite is geïnstalleerd.

.. code:: ini

   ====Satellite.ini ====

   De satellite-server heeft een eigen ini-file: satellite.ini bijvoorbeeld:
     [fileserver]
     storage=LOCAL
     server=111.222.111.1
     fallbackserver=111.222.111.2
     docroot=\\\\OXYGEN\\Organisatie\\Satellite\\Testen\\
     api_user=OpenWaveUploadFile
     api_pass=30486599guio
     net_user=serviceaccount
     net_pass=57345743578hghgg
     false-pass-timeout=120s
     max-mem=1024M
     geensubmapmetsubstring1 = \\Inspecties\\
     geensubmapmetsubstring2 = \\Adviezen\\
     geensubmapmetsubstring3 = \\BezwaarBeroep\\

Hierin worden de credentials en omzetting van adressen/paden geregeld.

-  **storage**. Alleen jCifs **(deprecated per 1.28)**, LOCAL of SMBTWO.
   SMBTWO is opvolger van jCifs. SMBTWO/jCifs wordt gebruikt indien de
   satellite op een andere machine staat als waar de files moeten worden
   opgeslagen. LOCAL indien installatie op de fileserver zelf of op een
   fileshare waarbij de fileserver via UNC-paden bereikbaar is. Bij
   LOCAL moet de satellite draaien onder een Windows/service account met
   rechten op de docroot (op het netwerk/fileserver)

..

   [!WARNING] > **Let op:** Per 1.28 is jCifs deprecated. Vanaf versie
   1.29 is het niet langer mogelijk om voor jCifs te kiezen.

-  **server en fallbackserver** worden alleen gebruikt bij jCifs of
   SMBTWO. Het gaat hier om de WINS server instelling indien jCifs. Niet
   alle installaties gebruiken een wins server bij Cifs, maar een DNS of
   hosts file. Als dat zo is, vul hier dan in: 127.0.0.1
-  **docroot** Deze komt voor de relatieve mapnaam (de paramfolder uit
   de hierboven genoemde functies). Bij Jcifs/SMBTWO wordt deze docroot
   dus achter de server geplaatst en ziet er bijvoorbeeld zo uit:
   //ow/documents/. **Indien de satellite op een Windowsserver is
   geplaatst moeten de slashes vervangen worden door dubbele
   backslashes**.

Bij LOCAL gaat het om een absoluut Linux- of Windows-pad bijv. bij
linux: /var/documents/ of bij Windows: \\\\ow\\documents\\ (let op:
dubbele slashes!!!). Het is aan te raden deze docroot gelijk te zetten
met de kolom *Tekst* van de instelling *Sectie: Documenten en Item:
Documentroot*

-  **api_user en api_pass**. De satellite vergelijkt voor elke functie
   aanroep de meegestuurde paramuser en parampass (beiden in plain text)
   met de waarden api_user en api_pass. De api_pass is hier in de
   ini-file versleuteld opgeslagen met RemCrypto: dat is een vaste 2-weg
   encryptiemethode
-  **net_user en net_pass** zijn nodig om op de netwerkdrive
   (server+docroot) in te loggen met lees-, schrijf- en verwijderrechten
   indien storage=jCifs of SMBTWO. De net_pass moet in de ini-file
   versleuteld zijn met RemCrypto
-  **false-pass-timeout** Time-out in seconden
-  **max-mem** wordt nog niet ondersteund
-  **geensubmapmetsubstring1 /2 /3**. Deze instelling wordt gebruikt bij
   de methode *getfilelist*. Deze methode levert een lijst van files op
   grond van een of meer aangeleverde mapnamen in de aanroep. De
   satellite onderzoekt daarbij ook submappen van die aangeleverde
   mappen. Indien de waarde van de instelling echter gevuld is en
   voorkomt in een submapnaam, dan wordt deze submapnaam overgeslagen.

..

   [!WARNING] > **Let op:** bij Local op windows dubbele slashes!!!

De ini-file kan worden uitgelezen met de methode *getAboutInfo* met
parameters:

-  paramlogin: toegangsnaam voor de satellite:
-  parampass: password voor de satellite (plain)

Logging
~~~~~~~

In de tabel tbmessagelog worden de verzonden en ontvangen berichten van
en naar de satellite gelogd.

Deze lijst wordt alleen gevuld indien:

-  de instelling aangevinkt is van *Sectie: OWB* en *Item: MessageLog*.
   In kolom *Getal1* van deze instelling staat het aantal dagen dat de
   loggingskaarten bewaard moeten blijven. Default is dat 31
-  en - indien GEEN compartiment - , de instelling *Sectie: Satellite en
   Item: Messagelog* bestaat en is aangevinkt
-  en - indien WEL compartiment - , de kolom *Messagelog* aangevinkt is
   van de betreffende compartimentskaart (beheertegel *Compartiment*).
