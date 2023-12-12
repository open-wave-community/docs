# Compartimenten

Portal beheer-Nieuw. Tegel Compartimentsrechten.

API(s):

  - getSysStandardList
  - getSysStandardDetail

Screenidentifiers (beheertegel *schermkolominfomatie*)

  - MDLC_getTbCompartimentList.xml
  - MDDC_getTbCompartimentDetail.xml
  - MDWC_insertTbCompartiment.xml

  Zie verder in de standaardtabel bij onderstaande tabelidentifiers.

tbSysStandardtable tabelidentifiers  (Beheertegel *Tabellen Standaardapi*)

  - beheer_compartiment
    - beheer_kopcompgem
    - beheer_kopcompsrtomgverg
    - beheer_kopcompsrtbwvverg
    - beheer_kopcompsrtovvverg
    - beheer_kopcompsrthhzaak
    - beheer_kopcompsrtmilverg
    - beheer_kopcompsrtinfoav
    - beheer_kopcompsrtmilinr

Met het compartimenteren kan worden bewerkstelligd dat een kleine organisatie de verantwoordelijkheid neemt voor het afhandelen van bepaalde zaaktypes binnen een grotere OpenWave installatie (hierna: de Gastheer). Bijvoorbeeld een samenwerkingsverband Z behandelt alleen de reguliere omgevingsprocedures van gemeente X en Y  alsmede de APV’s van gemeente X en Y binnen de OpenWave installatie van hun omgevingsdienst. Die omgevingsdienst behandelt dan per definitie alle overige gedefinieerde zaken voor de gemeentes X en Y, maar ook de APV’s en reguliere omgevingsprocedures buiten de gemeentes X en Y.

![](applicatiebeheer/instellen_inrichten/compartiment.png.png){ class="media" loading="lazy" alt="" width="400" }

De cirkelsectoren in bovenstaande tekening staan voor gemeentes of combinatie van één of meer gemeentes, die in de OpenWave installatie zijn gedefinieerd met woonplaatsen en adressen.

De tussenruimtes tussen de cirkelbogen en de sectorlijnen staan voor de zaken die in de OpenWave installatie worden behartigd bij die gemeentes. Bij een sector met gekleurde niet-blauwe vlakken is sprake van een compartiment. Een gekleurd niet-blauw vlak is een zaaktype dat alleen door medewerkers die lid zijn van het compartiment kunnen worden aangemaakt of gemuteerd.

Indien een medewerker lid is van een compartiment (beheerportaal-Nieuw, detailscherm van medewerkers) dan heeft hij of zij kijkrechten op alle zaken en inrichtingen die zich afspelen in gemeentes die aan datzelfde compartiment zijn verbonden. Wijzigen, verwijderen en nieuw aanmaken kan echter alleen op zaaktypes (en bij inrichtingen: bedrijfsoorten) die aan datzelfde compartiment zijn verbonden. Dit geldt in ieder geval voor de schermen *Alle zaken* en *Alle inrichtingen*.

Op het openingsportaal zijn de doorkieslijsten achter de tegels Openstaande omgevingszaken, APV, Milieu/gebruik, Handhaving, Horeca, Info-aanvragen, bezwaarberoep, uitstaande- en recent binnengekomen adviezen en inspectietrajecten en bezoeken instelbaar of zij alle zaken van de betrokken compartimentgemeentes laten zien OF dat zij alleen die zaken laat zien, die in het compartiment gedefinieerd zijn. Dat instellen gebeurt met de tegeldefinitie.

Een compartiment wordt dus gedefinieerd door zowel één of meer gemeentes als één of meer zaaktypes.

Omgekeerd geldt dat indien een medewerker GEEN lid van een compartiment is (dus valt onder de gastheer), hij of zij ook alle zaken en inrichtingen ziet ongeacht de gemeente waar die zaken spelen. Wijzigen, verwijderen en nieuw aanmaken van een zaak bij een bepaalde gemeente kan echter alleen op zaaktypes (en bij inrichtingen: bedrijfsoorten) die aan geen enkel compartiment voor diezelfde gemeente zijn toegewezen.

OpenWave zal altijd eerst controleren op compartimentsrechten en daarna op de (bestaande) functionele rechten.

## Default behandelaar

Per zaaktype dat valt onder het compartiment (beheertegel *Compartimentsrechten*) kan een default behandelaar worden aangewezen uit de lijst met medewerkers die aan dat compartiment zijn toegewezen.

## Compartiment en extern zaak/DMS systeem

Per zaaktype dat valt onder het compartiment (beheertegel *Compartimentsrechten*) kan de zaaktypecodering worden opgegeven waaronder het zaaktype in het extern zaaksysteem van het compartiment bekend is.
De stuurgegevens en endpoints van het externe zaaksysteem ten behoeve van een StUF-zaak/DMS koppeling moeten per gemeente worden opgegeven in de tabel33 gemeente (beheerportaal-Nieuw tegel *Gemeentes*).

## Deelzaken Inspecties, bezwaar/beroep

Indien voor een compartiment is ingesteld (beheertegel *Compartimentsrechten*) dat het compartiment een bepaald zaaktype behandelt, kan daarbij ook worden aangegeven of dit inclusief of exclusief de deelzaken inspecties en bezwaar/beroep is. Dat betekent dat een compartiment bijvoorbeeld een reguliere bouwzaak afhandelt, maar dat de inspectie daarop door de OpenWave gastheer wordt afgehandeld waarbinnen het compartiment valt.

Als bij de definitie van het zaaktype in het compartiment is opgegeven:

  - exclusief inspectie
  - EN een inspecteur is aangewezen uit de lijst met medewerkers van de gastheer
  - EN een aanleiding inspectie is opgegeven

dan zal bij het afsluiten van een zaak door het compartiment dat valt onder het bewuste zaaktype, automatisch een inspectietraject aangemaakt worden op naam van de opgegeven inspecteur.

## Satellite

Een compartiment kan verbonden zijn door middel van een satellite naar een afwijkende fileshare dan die van de Gastheer. Bij het compartiment kunnen hiertoe het endpoint en credentials worden opgegeven.

## Overrule compartiment

Het blok compartiment in de detailpagina van een hoofdzaak is alleen zichtbaar indien er minimaal één (niet vervallen) compartiment is gedefinieerd in het beheerportaal (beheertegel *Compartimentsrechten*).

In dit blok kan de zaak aan een ander compartiment of aan de host worden toegekend (het berekende compartiment kan worden overruled) door in de dropdownlijst het gewenste compartiment aan te wijzen. De keuze 0 betekent dat de zaak door de host wordt behandeld (vwfrmkeycompartiment krijgt in dat geval de waarde null).

Mutatierechten op deze kolom alleen indien de inlogger het recht *Mag ander compartiment toekennen bij hoofdzaak (dlmagcompoverrulen)* aangevinkt heeft staan.

Verder moet per compartiment/zaaktype de kolom dvcodedefbehandelaar gevuld zijn (bijv. bij omgevingszaak tbkopcompsrtomgverg.dvcodedefbehandelaar). In geval dat een zaak naar een compartiment wordt overgedragen, zal een nieuwe dossierbehandelaar met deze naam automatisch aangemaakt worden bij de bestaande zaak.

Verder moet per zaaktype (bijv. tbsoortomgverg) de kolom dvcodedefbehandelaar gevuld zijn. In geval dat een zaak van een compartiment naar de host wordt overgedragen, zal een nieuwe dossierbehandelaar met deze naam automatisch aangemaakt worden bij de bestaande zaak.

## De data van het compartimentsscherm

Het detailscherm van een compartiment bestaat uit 3 delen:

  - de detailgegevens van het compartiment
  - een opsomming van de gemeentes die tot het compartiment behoren
  - een opsomming van de zaaktypes per module die tot het compartiment behoren.

## Detailgegevens compartiment

### Blok Compartiment

  - **Naam compartiment** (dvnaam)
  - **Vervaldatum** (ddvervaldatum). Indien gevuld kan het compartiment niet meer toegekend worden aan Processen, Sjablonen, Rapportages en Adviesinstanties.
  - **Omschrijving** (dvomschrijving).
  - **Documentenopslag in DMS** (dldms). Indien aangevinkt dan kunnen documenten geüpload worden naar het DMS van het compartiment. De credentials, endpoint en stuurgegevens in geval van stuf Zaak/DMS staan de tabel tb33gemeente (beheertegel: per gemeente dus..).
  - **Documentenopslag fileserver** (dlfileserver). Indien aangevinkt dan kunnen documenten geüpload worden naar een fileserver. Indien deze fileserver anders is dan die van de Gastheer moet de communicatie via een satellite verlopen.
  - **Fileserver via satellite** (dlsatellite). Indien aangevinkt dan verloopt opvraag en opslag van documenten op een fileserver van het compartiment via een aldaar geïnstalleerde satellite. Endpoint en credentials staan in het blok satellite.
  - **Documenten fileserver openen met Office URI schemes** (dldocsfileshareofficeuri ). Indien aangevinkt en documentopslag op fileserver en extensie is .docx of .xlsx EN de inlogger komt vanuit een valide IP-range, dan zal het document op de fileserver van het compartiment met de lokale ms-word of ms-excel worden geopend. Readonly indien bovenliggende zaak is geblokkeerd.
  - **Automatisch aanmaak fileservermappen bij nieuwe handmatige zaak** (dlautoaanmaakmappen). Indien aangevinkt en documentopslag op fileserver dan worden bij een nieuwe (handmatig) aangebrachte zaak automatisch de mappen genoemd onder instelling *Sectie: Aanmaakmappen* aangemaakt.
  - **Automatisch aanmaak fileservermappen bij nieuwe zaak door OLO/DSO-bericht** (dloloautoaanmaakmappen). Indien aangevinkt en documentopslag op fileserver dan worden bij een verwerking van OLO of DSO bericht automatisch de mappen genoemd onder instelling *Sectie: Aanmaakmappen* aangemaakt.
  - **Roeblijsten voor berekening vastgestelde kosten bij omgevingsonderdelen** (dlroeb). Indien aangevinkt dan maakt het compartiment gebruik van de roebtabellen onder het onderdeel bij een omgevingszaak.
  - **No reply emailadres**. (dvnoreplyemailadres). Algemeen emailadres dat gebruikt kan worden voor no-reply berichten.
  - **Default afzender bij email** (dvafzemaildefvolg) is '1, 2 of 3. Defaultadres voor afzender email: 1 = tbmedewerker.dvemail, 2 = tbmedewerker.dvnietpersemail en 3 = tbcompartiment.dvnoreplyemailadres.

### Blok Zaak/DMS

  - **DMS methode** (dvdmsmethode). Indien de zaken die door het compartiment worden behandeld gekoppeld zijn aan een extern zaaksysteem, dan staat hier het protocol. Ofwel *StUF-ZAKEN 310* (Stuf zaak/dms) ofwel *CMIS 1.0*.
  - **E-suite als DMS?** (dlesuitedms). Indien het gekoppelde DMS voor het compartiment E-Suite is, dan dient dit veld aangevinkt te worden (default false). Aangevinkt betekent dat bij gebruik van de externe hyperlink naar het DMS, op de tag %dmsnr% in de hyperlink de benodigde vertaalslag zal worden uitgevoerd om naar E-Suite te navigeren.
  - **Dnkey van organisatie** (dnkeyorganisatie). Deze dnkey moet verwijzen naar een bestaande dnkey in tbcontactadressen die staat voor de organisatie van het compartiment. Dit contactadres wordt gebruikt als initiator bij een stuf/zaak creeerzaakbericht indien het gaat om een handhavingszaak, inspectiezaak of advies of inrichting.
  - **Zaaktype DMS adviezen** (dvdmszaaktypeadvies). Dit zaaktype wordt gebruikt bij een stuf/zaak creeerzaakbericht in het geval dat de deelzaak advies een eigen zaak is in het externe zaaksysteem van het compartiment. Dit is het geval wanneer deze kolom een gevulde waarde heeft (EN kolom dldms en dnkeyorganisatie) EN de instelling *Sectie: Adviezen en Item: AdviesIsZaak* aangevinkt is.
  - **Zaaktype DMS inspecties**  (dvdmszaaktypeinspecties). Dit zaaktype wordt gebruikt bij een stuf/zaak creeerzaakbericht in het geval dat de deelzaak inspectie een eigen zaak is in het externe zaaksysteem van het compartiment. Dit is het geval wanneer deze kolom een gevulde waarde heeft (EN kolom dldms en dnkeyorganisatie) EN de moduleletter van de inspectiezaak komt NIET voor in de kolom *Info* van de aangevinkte instelling *Sectie: Koppeling Zaak en Item: ZaaktypeInspectietraject* (maar de instelling bestaat wel).
  - **Automatisch zaak aanmaken in DMS** (dlautozaakdmsomgeving, dlautozaakdmsapvoverg, dlautozaakdmshandhaving, dlautozaakdmsmilieugebruik, dlautozaakdmshoreca, dlautozaakdmsinfoaanvraag). Indien aangevinkt dan zal bij het creëren van een hoofdzaak in de betreffende module in OpenWave automatisch een stuf/zaak creeerzaakbericht uitgaan mits een DMS-zaaktype aan het compartimentzaaktype is toegevoegd (zie hieronder). En natuurlijk indien dvdmsmethode = StUF-ZAKEN 310.
  - **Wijziging zaakomschrijving of bevoegdgezag doorgeven in updatezaakbericht zaak/dms** (dldmsupdatezaakbericht). Zie [UpdateZaak-bericht wijzigen metadata(StUF)](/docs/probleemoplossing/programmablokken/wijzigen_omschrijvingdata_zaak_dms.md).
  - **Wijziging documentnaam e.a. metadata doorgeven in zaak/dms**(dldmsupdatemetazaakdoc). Indien aangevinkt kan een wijziging in de documentnaam of type of vertrouwelijkheid van een document via een Stuf updateZaakDocument_Di02 worden doorgegeven aan het DMS.
  - **Zaakomschrijving bij creeerzaakbericht i.p.v. zaaktypeomschrijving in zaak/dms** (dlaanvrgnmipvzaaktype). Indien aangevinkt zal bij het naken van een Stuf creeerzaak_Lk01- bericht de zaaknaam uit de kaart zelf komen en anders uit de zaaktypeomschrijving (beheer bijv. tbsoortomgverg).
  - **Afsluiten zaak in DMS via UpdateZaak-bericht i.p.v. actualiseerZaakstatus** (dldmssfsluitenmetupdatezaak). Indien aangevinkt dan wordt het afsluiten van een zaak (einddatum en resultaat) doorgegeven aan DMS met updatezaakbercht ipv actualiseerzaakbericht.
  - **Metadata van geregistreerde documenten kunnen synchroniseren vanuit DMS**(dlsynchroniseervanuitdms) Indien aangevinkt dan kunnen metadata (titel, documenttype, vertrouwelijkheid e.d.) van geregistreerde documenten worden gesynchroniseerd vanuit DMS.
  - **Automatisch synchroniseren bij hernoemen gereg. document vanuit DMS**(dlautosynchroniseervanuitdms). Indien aangevinkt dan wordt bij hernoemen van geregistreerd document eerst automatisch gesynchroniseerd vanuit DMS.
  - **Ontvangsdatum opnemen** (dlontvangstdatuminedclk01). Datum van vandaag als ontvangstdatum toevoegen bij alle edclk01 (voegzaakdocumenttoe).
  - **Opnemen heeftalsverantwoordelijke**(dndmsheeftalsverantw). Indien 1 2 of 3 dan wordt het blok heeftalsverantwoordelijke opgenomen in creerzaakbericht. 1 = gemeenteid+mwcode, 2 = gemeenteid+loginnaan. 3 = gemeenteid + vastewaarde).
  - **Opnemen heeft als uitvoerende** (dndmsheeftalsuitv). Indien 1 2 of 3 dan wordt het blok heeftalsuitvoerende opgenomen in creerzaakbericht. 1 = gemeenteid+mwcode, 2 = gemeenteid+loginnaan. 3 = gemeenteid + vastewaarde)  .
  - **Status isGezetDoor** (dndmsstatusgezetdoor) is 'Schrijfwijze van isgezetDoor in blok heeftStatus van creeerzaakbericht en actualiseerzaakstatusbericht (1 = gemeenteid+mwcode, 2 = gemeenteid+loginnaan. 3 = gemeenteid + vastewaarde).
  - **Vaste Tekst** (dvdmsmwvastetekst) is vaste waarde bij dndmsheeftalsverantw of dndmsstatusgezetdoor of dndmsheeftalsuitv = 3 .
  - **Externe link naar DMS (portaalknop Externe link kijkt naar deze instelling)** (dvexternehyperlink). Hier staat de hyperlink die gebruikt wordt om naar externe link te verwijzen (werkt conform configuratie-instelling *Externe Link*). De bekende tags ( `%zaaknr%` , %dmsnr% enzovoorts) zijn te gebruiken. Let op: er is maar 1 externe link per compartiment in te stellen. Deze zal dus voor alle modules (denk ook aan inspectietrajecten) werken.

### Blok Documenten

  - **Documenttype verplicht bij upload** (dldocumenttypeverplicht). Indien aangevinkt zal bij het uploaden van een document dat hoort bij een compartimentszaak gevraagd worden om het documenttype aan te wijzen.
  - **Vertrouwelijkheid verplicht bij upload** (dlvertrouwelijkheidverplicht). Indien aangevinkt zal bij het uploaden van een document dat hoort bij een compartimentszaak gevraagd worden om het documenttype aan te wijzen.
  - **Status verplicht bij upload** (dlstatusverplicht). Indien aangevinkt zal bij het uploaden van een document dat hoort bij een compartimentszaak gevraagd worden om een status op te geven.
  - **Titel verplicht bij upload** (dltitelverplicht). Indien aangevinkt zal bij het uploaden van een document dat hoort bij een compartimentszaak gevraagd worden om een titel op te geven.
  - **Auteur verplicht bij upload** (dlauteurverplicht). Indien aangevinkt zal bij het uploaden van een document dat hoort bij een compartimentszaak de auteur worden meegegeven (aan DMS) met waarde Onbekend. Tenzij het document met een sjabloon gemaakt is, dan wordt de inlogger als auteur beschouwd.
  - **Handmatige uploads registreren** (dldocregallehandmuploads). Indien aangevinkt dan krijgen zowel alle handmatige uploads als gecreëerde documenten op basis van een sjabloon in het compartiment automatisch een kaart in geregistreerde documenten (tbcorrespondentie).
  - **OLO/DSO uploads registreren** (dldocregalleolodsouploads). Indien aangevinkt dan krijgen alle OLO/DSO bijlages voor het compartiment automatisch een kaart in geregistreerde documenten (tbcorrespondentie).
  - **Default brieven/emails opslaan** (dnautoopslaan). Indien deze kolom wordt gevuld met 1 dan zal OpenWave bij het creëren van een brief op basis van een sjabloon als default de fileserver voorstellen. Bij 2 wordt DMS voorgesteld en bij 3 de optie Nee (hetgeen betekent: niet automatisch opslaan). Deze instelling is alleen zinvol bij hybride gebruik van fileshare EN DMS in het compartiment.
  - **OLO/DSO documenttype** (dvolodsodocumenttype). Het documenttype dat wordt meegegeven aan OLO(/DSO)-documenten voor het compartiment die naar het DMS gaan. Wordt ook gebruikt voor meegeven van documenttype bij automatische registratie van OLO/DSO documenten. Voorheen was dit niet per compartiment in te stellen maar keek het programma naar kolom *Tekst* bij instelling *Item: OloDocType, Sectie: koppelingDOCNAARDMS*.
  - **OLO/DSO vertrouwelijkheid** (dvolodsovertrouwelijkheid). De vertrouwelijkheidsindicatie die wordt meegegeven aan OLO(/DSO)-documenten voor het compartiment die naar het DMS gaan. Wordt ook gebruikt voor meegeven van de vertrouwelijkheidsindicatie bij automatische registratie van OLO/DSO documenten. Voorheen was dit niet per compartiment in te stellen maar keek het programma naar kolom *Tekst* bij instelling */Item: OloVertrouwelijkheid, Sectie: koppelingDOCNAARDMS*.
  - **Automatisch aanmaken van externe link (DMS) bij registratie in tbcorrespondentie** (dlextlinkautovul). Indien aangevinkt en een document wordt succesvol met StUF zaak/dms naar het DMS verzonden, waarbij dat document ook nog eens in OpenWave geregistreerd wordt, dan wordt  in de kolom tbcorrespondentie.dvurl een string geconstrueerd op basis van de kolom  dvexternedoclink waarin de substrings %dmszaakcode% en %dmsdoccode%  on the fly worden vervangen door hun echte waarde bij het betreffende document.
  - **Externe link voor tbcorrespondentie.dvurl met variabelen %dmszaakcode% en %dmsdoccode%**(dvexternedoclink). Zie hierboven.

### Blokken Satellite

  - **Satellite endpoint** (dvsatelendpoint) het adres van de satellite-server in het compartiment. Moet zijn:
```
https://xxxx:yyyy/services/nl.rem.satellite.published.Fileserver.nl.rem.satellite.published.FileserverHttpSoap12Endpoint/
```

  Op de plaats van de xxxx en de yyyy ip.nummer en poort.

  - **Domein** (dvsateldomain). Bedoeld wordt het domein van de server waar de satellite draait.
  - **Authenticatie**. Indien de kolom: dvhttpauthenticatienaam gevuld is dan gaat de berichten van de Cloud naar de satellite onder httpsauthenticatie.
    - De usernaam voor htttps-authenticatie staat in deze kolom **HTTPSAuthenticatieNaam** (dvhttpauthenticatienaam).
    - Het Password staat in kolom **HTTPSAuthenticatiePass** (dvhttpauthenticatiepass) (zie ook: [2-way encryptie van externe wachtwoorden](/docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden).md).
    - Het Type versleuteling staat in kolom **HTTPSAuthenticatieType** (dvhttpauthenticatietype) (vooralsnog alleen Basic).
    - De inhoud van de kolom **username toegang satellite-ini** (dvsatelfileserveruser) wordt vergeleken met de *api-name* van de satellite ini-file. In die ini-file staat de echte toegangsnaam voor de fileserver die aan de satellite is verbonden.
    - De inhoud van de gecrypte kolom **password toegang satellite-ini** (dvsatelfileserverpass) wordt vergeleken met de *api-pass* van de satellite ini-file. In die ini-file staat de echte toegangspass voor de fileserver die aan de satellite is verbonden.
  - **Chunksize (MB)** (dnchunkmbsize). De grootte van de pakketjes die van en naar de satellite worden gestuurd bij ophalen en zenden van documenten.
  - **Satellite berichten loggen** (dlmessagelog). Indien aangevinkt en de algemene Messageloginstelling *Sectie: OWB en Item: MessageLogstaat* staat ook aangevinkt, dan worden de berichten naar de satellite gelogd en zichtbaar gemaakt via de tegel *Messagelog* (beheerportaal).
  - **Bestaande files overschrijven** (dloverschrijffiles). Indien NIET aangevinkt dan wordt een eventueel bestaande file op de fileserver van de satellite NIET overschreven: de file wordt in dat geval geplaatst onder dezelfde naam met toevoeging (n) zoals test(3).txt.
  - **Self signed certificaat OK** (dlallowallhostnameverifier). Indien aangevinkt zal de Openwave instemmen met een self-signed of verlopen certificaat van de satelliteserver bij een verbinding onder https.
  - **Documentroot in satellite.ini** (Item: docroot) (dvsatellitedocroot). De documentroot die de satellite (satellite.ini item docroot) gebruikt i.p.v. de instelling *Sectie: Documenten en Item: Documentroot*. Van toepassing bij het aanmaken van mappen en het plaatsen van bestanden via de satellite bij de instellingen *Sectie: aanmaakmappen en Sectie: Hyperlink*.
  - **Verplaatsmap documenten bij upload dms (inclusief docroot)**. Indien vanuit de fileserver op het compartiment bestanden aangewezen worden om verplaatst te worden naar het DMS van het compartiment (dus zowel dlfileserver als dldms aangevinkt), dan komt hier het volledige pad inclusief de waarde van *Documentroot in satellite.ini* waar de verplaatste documenten naar toe gekopieerd worden.

### Blok OLO Terugkoppeling

  - **KoppelZaakAanAanvraag-bericht verzenden?** (dlolokoppelzaakbericht) is 'T of F. Indien T dan moet het binnengekomen OLO bericht dat hoort bij het compartiment gevolgd worden door een vrgDi01KoppelZaakAanAanvraag
  - **Endpoint voor rgDi01KoppelZaakAanAanvraag-bericht** (dvolokoppelzaakendpoint). Endpoint voor vrgDi01KoppelZaakAanAanvraag-bericht
  - **Stuurgegeven ontvanger organisatie** (dvolokoppelzaakontvangorg). Stuurgegeven ontvanger organisatie voor vrgDi01KoppelZaakAanAanvraag
  - **Stuurgegeven ontvangher applicatie** (dvolokoppelzaakontvangapp). Stuurgegeven ontvanger applicatie voor vrgDi01KoppelZaakAanAanvraag
  - **Stuurgegeven zender organisate** (dvolokoppelzaakzenderorg). Stuurgegeven zender organisatie voor vrgDi01KoppelZaakAanAanvraag
  - **Stuurgegeven zender applicatie** (dvolokoppelzaakzenderapp). Stuurgegeven zender applicatie voor vrgDi01KoppelZaakAanAanvraag

### Blok SWF

  - **OINnummer t.b.v. importeren actieverzoeken (dvswfoinzender)**. Hierin kan opgesomd worden voor welke OIN-nummers bij het compartiment actieverzoeken kunnen worden opgehaald. Indien meer dan één dan de OIN-nummer, scheiden met een puntkomma.
  - **ID uit tbperceeladressen** (dnkeyswfdummyadres)- t.b.v. dummy locatie nieuwe zaak bij behandeling van  actieverzoek (dnkeyswfdummyadres). Deze kolom wordt echter ook gebruikt voor binnenkomende DSO-verzoeken die voor een compartiment bedoeld zijn: zie schema bij [Verwerking DSO STAM berichten](/docs/probleemoplossing/programmablokken/verwerking_dso_stam_berichten.md).
  - **Altijd nieuwe zaak bij binnenkomende actieverzoeken** (dlswfactieverzoeknwezaak). Aangevinkt betekent dus ook dat een actieverzoek op een bestaande SWF-id toch leidt tot een nieuwe (compartimentszaak). Een SWF-id kan in dat geval aan meerdere zaken zijn toegekend.

## Gemeentes van compartiment

Lijst van gemeentes (uit tb33gemeente) die horen bij de rijen uit tbwoonplaatsen.

Een compartiment bestaat uit een of meer gemeentes.

## Omgeving zaaktypes van compartiment

De lijst bestaat uit de zaaktypes uit tbsoortomgverg (omgevingszaken zaaktypes) waarvoor geldt dat wanneer een omgevingszaak van dit type speelt in een van de compartimentgemeentes, dan de behandeling van die zaak door medewerkers van dat compartiment wordt gedaan. De medewerkers die een dergelijke zaak kunnen behandelen zijn de medewerkers die op hun medewerkerskaart aan het betreffende compartiment zijn toegevoegd.

Er kunnen dus een of meer niet-vervallen zaaktypes uit tbsoortomgverg worden toegekend aan het compartiment in de tabel tbkopcompsrtomgverg:

  - **Zaaktype-code** (dvzaaktypecode). Zaaktype van het externe zaak/DMS systeem (indien de compartimentszaak met zaak/DMS gekoppeld moet worden aan een extern zaak/DMS systeem).
  - **DMS-aanvinkvakje**(dlnaardms). Indien aangevinkt dan zal OpenWave StUFf zaak/DMS berichten sturen naar het externe zaak/DMS (creeerzaak, updatezaak, voegzaakdocumenttoe etc.).
  - **SWF-Verzoek** (dlswfactieverzoek). Indien aangevinkt zullen zaken aangemaakt n.a.v. binnengekomen SWF-actieverzoeken van dit zaaktype zijn. Let op: kan maar voor een zaaktype aangevinkt zijn.
  - **Zaaktype omschrijving**(tbsoortomgverg.dvomschrijving).
  - **Default behandelaar** (dvcodedefbehandelaar). Default behandelaar in tbinbehandelingbij bij aanmaak nieuwe zaak. Kan hier gekozen worden uit de medewerkers die aan het compartiment zijn toegevoegd.
  - **Default zaakverantw. team** (dnkeyteamsdefverantw). Kan hier gekozen worden uit de teams (beheerportaal-Nieuw) die toegekend zijn aan het compartiment.
  - **Inclusief inspectie aanvinkvakje** (dlinclinspectie). Indien aangevinkt dan vallen ook de deelzaken inspecties onder de verantwoordelijkheid van het compartiment. Indien NIET aangevinkt, dan wordt de hoofdzaak wel door het compartiment afgehandeld, maar de deelzaak inspectie door de HOST.
  - **Inclusief bezwaar/beroep aanvinkvakje** (dlinclfbezwaarberoep). Indien aangevinkt dan vallen ook de deelzaken inspecties onder de verantwoordelijkheid van het compartiment. Indien NIET aangevinkt, dan wordt de hoofdzaak wel door het compartiment afgehandeld, maar de deelzaak bezwaar/beroep door de HOST.
  - **Inspecteur** (dvcodeinspecteur). De medewerkerscode van de inspecteur op wiens naam automatisch een inspectietraject moet worden aangemaakt bij afsluiten van de compartiments-omgevingszaak. Dit is het geval indien het compartiment bij die zaak zelf geen inspecties doet (dus indien dlinclinspectie NIET aangevinkt is). Er kan hier gekozen worden uit de medewerkers die NIET aan een compartiment verbonden zijn (dus die van de host).
  - **Aanleiding inspectie** (dnkeyaanleiding). De aanleiding van de inspectie (uit tbinspaanleiding) indien automatisch een inspectietraject moet worden aangemaakt bij afsluiten van de compartiments-omgevingszaak. Dit is het geval indien het compartiment bij die zaak zelf geen inspecties doet (dus indien dlinclinspectie NIET is aangevinkt).
  - **Leges verplicht aanvinkvakje** (dllegesregelverplicht). Indien aangevinkt zal het vullen van de besluitdatum van de omgevingszaak via de wizard *SluitZaak* (bij zaken van dit compartimentszaaktype) gecontroleerd worden of er wel minimaal een legesregel is gedefinieerd bij de zaak. Zo niet, dan kan de zaak niet worden afgesloten.
  - **masker vast deel** (dvmasker). Vast gedeelte voor de dvzaakcode bij nieuwe zaak. Indien leeg kijkt OpenWave naar tbsoortomgverg.dvmasker.
  - **masker lengte ophoger (dnlenophoger)**. Lengte van variabele gedeelte voor de dvzaakcode bij nieuwe zaak. Indien leeg kijkt OpenWave naar tbsoortomgverg.dnlenophoger.

## Zaaktypes overige modules

Soortgelijk als hierboven bij Omgevingszaken.

Alleen voor inrichtingen geldt dat zij onder een compartiment vallen op grond van bedrijfsoorten (tbmilbedrijfsoorten).

