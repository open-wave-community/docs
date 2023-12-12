# Samenwerkingsfunctionaliteit

Onder een omgevingszaak is de tegel *Samenwerkingsruimtes* zichtbaar en benaderbaar voor die medewerkers die (beheertegel *Functionele rechten*) geautoriseerd zijn om de samenwerkingsruimte te zien (tbomgrechten.dlcomgswfvsb).
De tegel geeft toegang tot de tabellen tbswfruimte, tbswfoinpartners, tbswfdocumenten, tbswfactieverzoeken en tbswfnotificaties.

![](/docs/img/applicatiebeheer/instellen_inrichten/samenwerkingfunctionaliteitinopenwave.png){ class="media" loading="lazy" alt="" width="800" }

## Inregelen landelijke samenwerkingsruimte

OpenWave verzorgt het berichtenverkeer van en naar de landelijke samenwerkingsfunctionaliteit op een eigen certificaat (van Rem Automatisering). Bij het certificaat hoort een whitelist die aangeeft welke partners (OIN-nummers) berichten kunnen sturen op dat certificaat.

## Noodzakelijke instellingen

  - **Endpoint**. In de kolom *Tekst* van de instelling *Sectie: SWF en Item: AlgemeenEndpoint* dient het algemene gedeelte van het endpoint van de landelijke samenwerkingsfunctionaliteit te staan bijvoorbeeld `[https://service.pre.omgevingswet.overheid.nl/overheid/samenwerken/api/behandelen/v4/](https://service.pre.omgevingswet.overheid.nl/overheid/samenwerken/api/behandelen/v4/.md)`.
  - **CertificaatPassword**. In de kolom *Tekst* van de instelling *Sectie: SWF en Item: CertificaatPassword* dient het password van het certificaat gecrypt opgeslagen te worden. Deze gecrypte waarde wordt door REM aangeleverd (en kan niet via userinterface van OpenWave gedecrypt worden). Wordt door Rem geregeld.
  - **CertificaatType**. In de kolom *Tekst* van de instelling *Sectie: SWF en Item: CertificaatType* dient het type van het certificaat te staan namelijk *PKCS12*. Wordt door Rem geregeld.
  - **ClientCertificaatNaam**. In de kolom *Tekst* van de instelling *Sectie: SWF en Item: ClientCertificaatNaam* dient de naam van het certificaat te staan namelijk *digikoppeling.open-wave.nl_20210624.p12*. Wordt door Rem geregeld.
  - **OIN van zender**. In de kolom *Tekst* van de instelling *Sectie: SWF en Item: OINvanZender* dient het OIN-nummer te staan van de organisatie die OpenWave gebruikt en die dus in de whitelist voor moet komen. Bijvoorbeeld de omgevingsdienst ODDEVALLEI zal *00000001852282229000* als waarde moeten invullen. Indien vanuit de tegel *Samenwerkingsruimte* berichten worden verstuurd, dan kan OpenWave - indien de bijbehorende omgevingszaak bij een compartiment hoort - de OINvanZender ophalen uit de compartimentstabel (tbcompartiment.dvswfoinzender).

<wrap important>**Let op:** indien men in OpenWave met meerdere organisaties werkt zal voor bepalen OIN van zender deze instelling gebruikt worden indien de uitvoerende instantie van de zaak bovenliggend aan SWF ruimte gevuld is. Is deze niet gevuld dan zal het programma naar bevoegd gezag kijken (indien gevuld) en anders het OIN nummer van de gemeente waarin de zaak zich afspeelt. </WRAP>

  - **Messagelog**. Indien de instelling *Sectie: SWF en Item: MessageLog_InkomendeActieverzoeken* is aangevinkt dan worden de berichten van de operatie *Ophalen Inkomende Open Actieverzoeken* gelogd in de beheertabel tbmessagelog. Dit is niet altijd nodig en bovendien verzwarend, vandaar deze instelling. Uitgaande berichten naar samenwerkingsfunctionaliteit vanuit de tegel *Samenwerkingsruimtes* bij een omgevingszaak, worden wel altijd gelogd in de tabel tbmessagelog (mits de instelling *Sectie: OWB, Item: MessageLog* aangevinkt is).
  - **Key van onbekend lokatieadres**.*Getal2* van de instelling *Sectie: Koppeling ZAAK Item: DummyLokatiePerceelkey* moet gevuld zijn met een dnkey uit tbperceeladressen die staat voor een onbekend adres waaraan nieuwe zaken worden gekoppeld bij de operatie *inlezen open inkomende actieverzoeken*.
  - **Zaaktype bij actieverzoek**. In de beheertabel *Zaaktypes omgeving* moet één (niet vervallen) kaart zijn waarbij *Is zaaktype actieverzoek SamenwerkingsFunctionaliteit* (dlswfactieverzoek) aangevinkt is. Onder dit zaaktype worden nieuwe binnenkomende open actieverzoeken, waarvoor een nieuwe zaak moet worden aangemaakt, met een nieuwe samenwerkingsruimte geplaatst.

### Bepalen OIN van zender aanmaken en muteren van samenwerkingsruimtes

Naast bovengenoemde instellingen en condities zoals verder per blok op deze pagina beschreven, wordt er voor ALLE aanroepen naar de SWF toe vanuit OpenWave een OIN zender bepaald. Dit is het OIN nummer van de organisatie die de aanroep initieert en zal zoals bovenstaand genoemd bij Noodzakelijke instellingen, moeten voorkomen in de whitelist om ook de aanroep te mogen doen naar de SWF.

Het kan per OpenWave installatie verschillen of er altijd 1 OIN van zender is of dit per zaak kan verschillen. Indien men met 1 organisatie in OpenWave werkt en dit is een uitvoerende instantie dan is het voldoende om de configuratie instelling zoals hierboven beschreven, ingesteld te hebben. Idem ditto als er precies één gemeente/provincie in de OpenWave omgeving werkt en er alleen zaken in behandeling zijn waarvan de gemeente het bevoegd gezag is.

Het wordt ingewikkelder als met meer dan 1 gemeente in dezelfde OpenWave omgeving werkt, er met compartimenten gewerkt wordt en of als er zowel een gemeente als een uitvoerende instantie in dezelfde OpenWave omgeving werkt. De aanroepen naar SWF zullen dan afhankelijk van de zaak waarin gewerkt wordt met een andere OIN van zender moeten gebeuren: het is niet de bedoeling dat dan voor zaak van organisatie 1, de aanroep naar SWF gebeurt met het OIN nummer van organisatie 2.

Om deze redenen is de volgende logica van toepassing bij het bepalen van OIN van zender voor alle SWF aanroepen:

  - indien de uitvoerende instantie gevuld is van de zaak waaronder de SWF-ruimte plaats vindt, dan kijkt het programma altijd naar kolom *Tekst* van instelling *Sectie: SWF en Item: OINvanZender*. Het programma verwacht dat voor organisaties die uitvoerende instanties zijn (los van of er ook anderen in de OpenWave omgeving werken) bij de instelling het OIN van de uitvoerende instantie staat
  - indien de uitvoerende instantie LEEG is bij de zaak waaronder de SWF-ruimte plaats vindt, maar het bevoegd gezag is WEL gevuld, dan haalt het programma het OIN nummer van het bevoegd gezag op in tboin en gebruikt deze als OIN van zender
  - indien zowel de uitvoerende instantie als het bevoegd gezag LEEG is bij de zaak waaronder de SWF-ruimte plaats vindt, dan kijkt het programma naar de gemeente waarin de zaak zich afspeelt en gaat via de gemeentecode proberen het OIN nummer op te halen in tboin. Wordt deze niet gevonden dan kan de aanroep NIET plaatsvinden.

Zie ook schematisch weergeven de logica met als voorbeeld SWF-ruimte aanmaken:

[<img src="/_media/docs/applicatiebeheer/instellen_inrichten/stroomschema_swfruimte_aanmaken.jpg?w=800&amp;tok=8e8c3c" class="mediacenter" loading="lazy" alt="" width="800" />](/_detail/docs/applicatiebeheer/instellen_inrichten/stroomschema_swfruimte_aanmaken.jpg?id=docs%3Aapplicatiebeheer%3Ainstellen_inrichten%3Asamenwerkingsfunctionaliteit.md)

#### Belangrijk voor ALLE organisaties

Het is dus zeer belangrijk dat de organisaties in de OpenWave omgeving voorkomen in tboin (*OIN nummers* tegel in beheerportaal-Nieuw). Voor alle via DSO binnengekomen zaken zullen de aanroepen naar SWF altijd goed gaan met bovenstaande logica. Immers dan is altijd de uitvoerende instantie en/of het bevoegd gezag gevuld. Voor de handmatig aangemaakte zaken zal het bevoegd gezag en/of de uitvoerende instantie niet standaard gevuld zijn. Het is aan te raden dit door de behandelaar van de zaak te laten vullen.

Voor de zaken die aangemaakt worden n.a.v. binnenkomende SWF-actieverzoeken is het instelbaar om het bevoegd gezag of uitvoerende instantie automatisch te laten vullen. In het beheerportaal-Nieuw is onder tegel *OIN nummers* per eigen organisatie aan te geven of automatisch het bevoegd gezag, of de uitvoerende instantie gevuld moet worden bij het aanmaken van een SWF advieszaak in OpenWave door het aanvinken van veld *Is bevoegd gezag bij advieszaak o.b.v. binnenkomend actieverzoek SWF* (in geval van bevoegd gezag), of van veld *Is uitvoer inst./behandeldienst bij advieszaak o.b.v. binnenkomend actieverzoek SWF* (in geval van uitvoerende instantie). Er kan maar 1 van de twee velden aangevinkt zijn per OIN nummer.

## Aanmaken / verwijderen samenwerkingsruimte

De omgevingskaart mag niet geblokkeerd zijn en het compartiment moet kloppen.

Een gebruiker die geautoriseerd is om een nieuwe samenwerkingsruimte aan te maken (tbomgrechten.dlcomgswfins) kan vanuit de lijst achter de tegel *Samenwerkingsruimtes* op een omgevingsportaal een nieuwe ruimte creëren. Dat gaat in twee stappen. Eerst wordt de ruimte in OpenWave gemaakt (een kaart in de tabel tbswfruimte). Hierbij:

  - wordt de Bron (dvbronVerzoek) alleen gevuld met de waarde ‘DSO_LV’ indien de zaak in OpenWave een DSO-zaak betreft (dus projectid gevuld). In alle andere gevallen blijft deze kolom leeg.
  - wordt het verzoekNummer (dvverzoeknummer)  gevuld met het DSO-verzoeknummer indien de zaak een DSO-zaak is: in alle andere gevallen blijft deze kolom leeg

Vervolgens kan vanuit het detailscherm de ruimte in de landelijke DSO-samenwerkingsruimte worden gemaakt. Is dat laatste gelukt dan wordt in de openwave tabel de kolom *SWF id* automatisch gevuld met de landelijke identificatie. Dan wordt o.a. ook automatisch de SWF creatiedatum gevuld.

Indien de kolom *SWF id* gevuld is, dan is de kaart niet muteerbaar in OpenWave en een getrouwe afspiegeling van de landelijke samenwerkingsruimte.

Zolang de kolom *SWF id* nog niet is gevuld, kan de kaart verwijderd worden uit OpenWave (tbomgrechten.dlcomgswfdel). Indien de kolom *SWF id* wel is gevuld  dan kan de kaart alleen verwijderd worden indien ook landelijke de samenwerkingsruimte is beëindigd: de kolom tbswfruimte.ddverwijderd wordt daarbij gevuld.

Op de detailkaart van een samenwerkingsruimte in OpenWave zijn linksonder vier knoppen:

  - Aanmaken ruimte in SWF (zie hierboven).
  - Beëindigen ruimte in SWF. Hiermee wordt de landelijke op beëindigd gezet, waarna - bij succes - de kolom tbswfruimte.ddverwijderd wordt gevuld. Deze knop is alleen zichtbaar en enabled indien:
    - compartiment ok
    - tbswfruimte.ddverwijderd is null
    - Status is GESLOTEN
    - bovenliggende omgevingszaak niet geblokkeerd
    - de gebruiker het afsluitrecht heeft (tbomgrechten.dlcomgswfafs)
    - aangemaakt door organisatie OIN is gelijk aan kolom *Tekst* van de instelling *Sectie: SWF en Item: OINvanZender* OF - indien de zaak speelt in een compartiment - gelijk aan tbcompartiment.dvswfoinzender. Dus alleen de organisatie die de landelijke ruimte heeft gecreëerd kan deze ook verwijderen.
  - Status van de ruimte op GESLOTEN zetten. Deze knop is alleen zichtbaar en enabled indien:
    - compartiment ok
    - tbswfruimte.ddverwijderd is null
    - status is OPEN
    - de gebruiker het afsluitrecht heeft (tbomgrechten.dlcomgswfafs)
    - bovenliggende omgevingszaak niet geblokkeerd
    - aangemaakt door organisatie OIN is gelijk aan kolom *Tekst* van de instelling *Sectie: SWF en Item: OINvanZender* OF - indien de zaak speelt in een compartiment - gelijk aan tbcompartiment.dvswfoinzender. Dus alleen de organisatie die de landelijke ruimte heeft gecreëerd kan de status op GESLOTEN zetten.
  - Synchroniseren van gegeven met landelijke ruimte. Deze knop is alleen zichtbaar en enabled indien:
    - compartiment ok
    - bovenliggende omgevingszaak niet geblokkeerd.

Indien het programma bij het verversen tot de constatering komt dat de landelijke ruimte niet meer bestaat, dan wordt de kolom tbswfruimte.ddverwijderd gevuld met timestamp van dat moment.

Voor de documenten, actieverzoeken en notificaties geldt dat indien tijdens het verversen (synchroniseren) blijkt dat een verzoek of document of notificatie niet meer bestaat in het SWF, deze regel in OpenWave een rood bolletje krijgt (onderliggend wordt de kolom dlinswf gevuld met F). De historie blijft zo bestaan.

## Aanwijzen/Wijzigen van de samenwerkingspartners

Als de (landelijke) samenwerkingsruimte is aangemaakt en nog open staat moet aangegeven worden aan welke ketenpartners straks een of meer actieverzoeken worden verzonden. Op het detailscherm van de samenwerkingsruimte is hiertoe het blok *Ketenpartners*. De insertknop is zichtbaar indien:

  - de gebruiker insertrechten op de samenwerkingsruimte (tbomgrechten.dlcomgswfvsb) heeft
  - de samenwerkingsruimte nog NIET is beëindigd
  - de aanmaker van de samenwerkingsruimte (tbswf.dvaangemaaktdooroinin) dezelfde is als de door programmatuur bepaalde OIN van zender (zie kopje *Bepalen OIN van zender aanmaken en muteren van samenwerkingsruimtes*).

Met de insertknop kan een ketenpartner gekozen worden uit de beheertabel tboin waarvoor geldt:

  - dat de OIN-organisatie nog niet is vervallen
  - EN dat de eigenschap *SWF* is aangevinkt (is partner samenwerkingsfunctionaliteit: dlswf)
  - EN dat het OIN-nummer ongelijk is aan de door programmatuur bepaalde OIN van zender (zie kopje *Bepalen OIN van zender aanmaken en muteren van samenwerkingsruimtes*)
  - EN dat het OIN nog niet is toegevoegd bij de betreffende samenwerkingsruimte.

Daarnaast dient een privilege toegekend te worden aan de partner (BT= beperkte toegang en VT = volledige toegang). Dit privilege wordt vergeleken met de vertrouwelijkheidaanduiding van een geüpload document. Een ketenpartner met *Beperkte Toegang* die documenten opvraagt van een samenwerkingsruimte, zal alleen de documenten met *Regulier Vertrouwelijk* zien.

Indien succesvol (hetgeen betekent dat ook de landelijke SWF de partner heeft geaccepteerd) wordt een kaart aangemaakt in tbswfoinpartners bij de betreffende samenwerkingsruimte.

Voor het verwijderen van een ketenpartner dient de gebruiker het afsluit/verwijderrecht in SWF te hebben op de samenwerkingsruimte (tbomgechten.dlcomgswfafs).

#### Wijzigen privilege van samenwerkingspartner

In het blok *Ketenpartners* is de knop *Wijzig ketenpartner privilege* zichtbaar indien:

  - de gebruiker wijzigrechten op de samenwerkingsruimte (tbomgrechten.dlcomgswfedt) heeft
  - de samenwerkingsruimte nog NIET is beëindigd
  - men de aanmaker van de samenwerkingsruimte is: de aanmaker van de samenwerkingsruimte (tbswf.dvaangemaaktdooroinin) moet dezelfde zijn als de door programmatuur bepaalde OIN van zender (zie kopje *Bepalen OIN van zender aanmaken en muteren van samenwerkingsruimtes*).

De knop start een wizard waarmee het gewenste privilege opgegeven kan worden voor de ketenpartner. Bij uitvoeren van de wizard zal aan het SWF dit nieuw opgegeven privilege worden doorgegeven.
Let op: er is helaas geen verversactie voor de Ketenpartnerlijst bij een SWF-ruimte. Het aanpassen van het privilege zal pas voor de medewerker zichtbaar zijn na draaien van Task *SynchroniseerOpenSWFRuimtes*. Voor het instellen van de task scheduler zie pagina [Taskscheduler](/instellen_inrichten/taskscheduler.md).

## Uploaden en downloaden en synchroniseren van documenten

OpenWave kijkt voor de documentfunctionaliteit alleen naar het recht om de samenwerkingsruimte te zien (tbomgrechten.dlcomgswfvsb).

De samenwerkingsruimte moet nog open staan!!

#### Uploaden

Als de (landelijke) samenwerkingsruimte is aangemaakt kunnen documenten geüpload worden. Op het detailscherm van de samenwerkingsruimte is hiertoe het blok *Documenten* aanwezig. Met de uploadknop (mits de samenwerkingsruimte nog NIET is beëindigd) wordt een wizard gestart waarmee de gebruiker een document kan aanwijzen. Dat kan een document zijn dat op de eigen device staat of een document uit de geregistreerde documentenlijst bij dezelfde omgevingzaak. In het laatste geval kan alleen een keuze gemaakt worden uit die documenten waarvoor geldt dat ze niet zelf uit het SWF afkomstig zijn (tbcorrespondentie.Dvswfdocumentid moet leeg zijn) en  dat het document *vrij* moet zijn (dvdocplaats =(S)erver) en niet vervallen.

De gebruiker dient ook aan te geven of het document *Strikt Vertrouwelijk* of *Regulier Vertrouwelijk* is. Strikt vertrouwelijke documenten kunnen alleen gezien worden door ketenpartners met het privilege *Volledige Toegang*.

Bij een document hoort een beschrijving. Nummer en Kenmerk zijn niet verplicht.

De documenten die ook in de landelijke SWF staan worden in OpenWave gesynchroniseerd in de tabel tbswfdocumenten. Daar is ook de identifier zichtbaar waaronder het document landelijk bekend is.

#### Downloaden

Met de downloadknop kan een document naar de device van de gebruiker worden gedownload. Vooralsnog wordt het gedownloade document dus niet automatisch in de documentopslag van OpenWave (fileshare of DMS) geplaatst. Zie daarvoor de knop hieronder: *Doorzetten naar documentopslag + registreren*

#### Synchroniseren

De synchroniseerknop haalt alle (metadata van alle) documenten bij de betreffende samenwerkingsruimte op, waarmee de lijst in OpenWave gelijk wordt gemaakt aan de lijst in de landelijke ruimte. Immers ketenpartners kunnen documenten hebben toegevoegd of gewijzigd.

#### Verwijderen

De verwijderknop zal NOOIT het document in SWF verwijderen maar is bedoeld om documenten uit de lijst van OpenWave te verwijderen die gepoogd zijn up te loaden bij het SWF maar waarvoor dat niet gelukt is. Zo'n document is te herkennen aan icoon rood kruis. Indien men op de verwijderknop klikt voor een documentregel waarvan het document wel in SWF staat (icoon groen vinkje) dan zal het programma een melding geven met dat het document niet verwijderd kan worden.

#### Doorzetten naar documentopslag + registreren

Indien er gebruik wordt gemaakt van documentregistratie in OpenWave, dan kan met behulp van deze knop de aangevinkte documenten doorgezet worden naar de documentopslag (fileshare/DMS).

Voor het automatisch registreren van SWF documenten zal gekeken worden of instelling *Sectie: DocumentRegistreren, Item: AlleGeselecteerdeSWFUploads* aan staat (bij compartiment of *Geselecteerde SWF uploads automatisch registreren?* aangevinkt is.

In de lijst met SWF documenten wordt bij kolom *Reg?* aangegeven of het document al geregistreerd staat bij de zaak (er komt een kaart voor in tbcorrespondentie met overeenkomend Doc id SWF). Zo ja dan staat er een groen vinkje, anders een rood kruisje.

Men kan 1 of meer documenten aanwijzen alvorens op de knop te klikken. Er zal alleen een scherm getoond worden indien er een fout optreedt waardoor de documenten niet doorgezet kunnen worden.

De wizard zal voor de documenten die nog niet voorkomen in tbcorrespondentie, deze doorzetten naar fileshare dan wel DMS en indien gelukt daarna een kaart aanmaken in tbcorrespondentie. In de lijst *Geregistreerde Documenten* zijn de aangemaakte kaarten terug te vinden. Documenttype zal zijn *SWF* en de vertrouwelijkheid van de documenten wordt als volgt bepaald:

  - indien instelling *Sectie: SWF*, *Item: vertalingVertrouwelijkheid* bestaat dan wordt in *Getal1* van deze instelling de dnkeyvertrouwelijkheid verwacht voor SWF document vertrouwelijkheid **SV** (strikt vertrouwelijk) en bij *Getal2* de dnkeyvertrouwelijkheid voor **RV** (Regulier vertrouwelijk)
  - indien bovengenoemde instelling niet bestaat en/of er wordt geen vertrouwelijkheid gevonden op basis van de instelling, dan valt het programma terug op de default vertrouwelijkheid voor DSO documenten: instelling *Sectie: KoppelingDOCNAARDMS, Item: OloVertrouwelijkheid* (voor compartimentzaken geldt waarde van veld tbcompartiment.dvolodsovertrouwelijkheid)

#### Wijzigen vertrouwelijkheid van document

Met de wijzigknop kan de vertrouwelijkheid van het document in de SWF-ruimte gewijzigd worden.
De wijzigknop is zichtbaar indien:

  - de gebruiker wijzigrechten op de samenwerkingsruimte (tbomgrechten.dlcomgswfedt) heeft
  - de samenwerkingsruimte nog NIET is beëindigd
  - het document aangemaakt is in het verleden door de organisatie die de documentvertrouwelijkheid probeert te wijzigen: de organisatie die probeert te wijzigen moet dezelfde zijn als de door programmatuur bepaalde OIN van zender (zie kopje *Bepalen OIN van zender aanmaken en muteren van samenwerkingsruimtes*) en die moet overeenkomen met originele aanmaker van het document.

De knop start een wizard waarmee de gewenste vertrouwelijkheid opgegeven kan worden voor het document. Bij uitvoeren van de wizard zal aan het SWF de nieuwe vertrouwelijkheid worden doorgegeven.

**Let op:** Het aanpassen van de vertrouwelijkheid zal pas voor zichtbaar zijn na verversen van de documenten in SWF. Dit kan bijvoorbeeld door klikken op de verversknop onderaan de lijst.

**N.b.** het is niet zo dat de vertrouwelijkheid in de eventueel in OpenWave corresponderende documentregistratie (en/of DMS opslag) wordt aangepast! Indien men daar de vertrouwelijkheid zou willen wijzigen, dan zal dit handmatig moeten worden uitgevoerd door de gebruiker.

## Uitgaande Actieverzoeken

Als de (landelijke) samenwerkingsruimte is aangemaakt en nog open staat kunnen één of meer actieverzoeken worden verstuurd naar één van ketenpartners van de samenwerkingsruimte met een titel en een beschrijving. In het geval dat men niet de aanmaker van de SWF ruimte is, kan men ook een actieverzoek versturen aan de initiator van de SWF ruimte.

Op het lijstscherm zijn de volgende knoppen zichtbaar en enabled:

  - De insertknop waarmee een nieuw actieverzoek gemaakt kan worden (met tbswfactieverzoeken.dluitgaand = T) is zichtbaar en enabled indien:
    - de gebruiker insertrechten heeft op de samenwerkingsruimte (tbomgrechten.dlcomgswfvsb)
    - de samenwerkingsruimte nog NIET is beëindigd en nog OPEN staat
    - het OIN nummer van de aanmaker van het verzoek moet gelijk zijn aan de door programmatuur bepaalde OIN van zender (zie kopje *Bepalen OIN van zender aanmaken en muteren van samenwerkingsruimtes*). De organisatie waarmee het actieverzoek wordt aangemaakt kan de aanmaker van de samenwerkingsruimte zijn maar dat hoeft niet (kan ook een van de ketenpartners zijn die een actieverzoek heeft ontvangen)
    - compartiment ok en bovenliggende zaak niet is geblokkeerd.
  - Verversknop (synchroniseer met landelijke ruimte)is zichtbaar en enabled indien:
    - compartiment ok en bovenliggende zaak niet is geblokkeerd
    - de SWF-ruimte nog NIET is beëindigd.

Op het detailscherm zijn de volgende knoppen zichtbaar en enabled indien:

  - Actieverzoek gereedmelden is zichtbaar en enabled indien:
    - het actieverzoek nog in de landelijke SWF aanwezig is
    - de status van de actie op OPEN staat
    - de gebruiker muteerrechten heeft op de samenwerkingsruimte (tbomgrechten.dlcomgswfedt)
    - de samenwerkingsruimte nog NIET is beëindigd en nog OPEN staat
    - de ontvanger van het actieverzoek (tbswfactieverzoeken.dvontvangeroin) dezelfde is als de door programmatuur bepaalde OIN van zender (zie kopje *Bepalen OIN van zender aanmaken en muteren van samenwerkingsruimtes*)
    - compartiment ok en bovenliggende zaak niet is geblokkeerd.

Met het gereedmelden wordt de status van het actieverzoek: GEREED

  - Actieverzoek intrekken is zichtbaar en enabled indien:
    - het actieverzoek nog in de landelijke SWF aanwezig is
    - de status van de actie op OPEN of GEREED staat
    - de gebruiker muteerrechten heeft op de samenwerkingsruimte (tbomgrechten.dlcomgswfedt)
    - de samenwerkingsruimte nog NIET is beëindigd en nog OPEN staat
    - de zender van het actieverzoek (tbswfactieverzoeken.dvzenderoin) dezelfde is als de door programmatuur bepaalde OIN van zender (zie kopje *Bepalen OIN van zender aanmaken en muteren van samenwerkingsruimtes*)
    - compartiment ok en bovenliggende zaak niet is geblokkeerd.

Met het intrekken wordt de status van het actieverzoek: INGETROKKEN.

## Inkomende Open Actieverzoeken

Op het operationsportaal onder de kolom *Import* is een tegel gedefinieerd *Ophalen SWF Open Actieverzoeken*. De actie achter deze tegel haalt alle inkomende openstaande actieverzoeken op uit de landelijke SWF voor de OpenWave installatie.

Indien de inlogger:

  - GEEN lid van een compartiment is, dan worden de berichten opgehaald die verzonden zijn naar:
    - het OIN-nummer gedefinieerd in kolom *Tekst* van de instelling *Sectie: SWF en Item: OINvanZender*
    - EN naar de OIN-nummers (gescheiden door puntkomma) gedefinieerd in kolom *Info* van de instelling *Sectie: SWF en Item: OINvanZender*. Bedoeld voor de situatie van een samenwerkingsverband, zoals de BEL-combinatie, die zowel een overkoepelend OIN-nummer hebben als individuele gemeentelijke OIN-nummers. <wrap important>**LET OP**: alle OIN-nummers moeten op de whitelist geplaatst worden.</WRAP>
  - WEL lid van een compartiment is dan worden de berichten opgehaald die verzonden zijn naar de OIN-nummers (gescheiden door puntkomma) gedefinieerd in kolom tbcompartiment.dvswfoinzender van het betreffende compartiment. Bedoeld voor die situatie waarbij een compartiment uit een samenwerkingsverband bestaat (Over-Gemeente).

De actie achter de tegel kan ook gescheduled aangeroepen worden (zie:[Taskscheduler](/instellen_inrichten/taskscheduler).md).
De robot haalt in dat geval alle berichten op die verzonden zijn naar:

  - het OIN-nummer gedefinieerd in kolom *Tekst* van de instelling *Sectie: SWF en Item: OINvanZender*
  - EN naar de OIN-nummers (gescheiden door puntkomma) gedefinieerd in kolom *Info* van de instelling *Sectie: SWF en Item: OINvanZender*
  - EN naar de OIN-nummers (gescheiden door puntkomma) gedefinieerd in kolom tbcompartiment.dvswfoinzender van alle niet vervallen compartimenten.

Het programma redeneert voor de verwerking van die berichten als volgt: Eerst zoekt OpenWave of het actieverzoek al bestaat in de bestaande kaartenbak van tbswfactieverzoeken. Maar alleen in de kaarten die dlUitgaand op F(alse) hebben staan. Immers binnen een samenwerkingsverband kan de ene gemeente een actieverzoek aan de andere uit doen gaan.

  - Indien het actieverzoek reeds bestaat in OpenWave (tbswfactieverzoeken.dvactieverzoekid) dan wordt deze kaart ververst.
  - Indien het actieverzoek nog niet bestaat in OpenWave, maar de bijbehorende samenwerkingsruimte wel (tbswfruimte.dvsamenwerkingid), dan wordt het nieuwe actieverzoek toegevoegd aan die bestaande SWF-ruimte in OpenWave (met dluitgaand = F). Hierop is de uitzondering indien de instelling *Sectie: SWF en Item: ActieverzoekNwezaak* aangevinkt is: dan wordt altijd een nieuwe zaak aangemaakt en de SWF-ruimte gedupliceerd. Voor compartimenten is hiertoe de kolom tbcompartiment.dlActieverzoekNwezaak.
  - Indien zowel het actieverzoek als de samenwerkingsruimte nog niet bestaat (of ingesteld dat er altijd een nieuwe zaak gemaakt moet worden), dan wordt:
    - een nieuwe zaak gemaakt in tbomgvergunning met als zaaktype de (unieke, niet vervallen) kaart uit tbsoortomgverg waarvoor geldt dat de kolom *Is zaaktype actieverzoek SamenwerkingsFunctionaliteit* (dlswfactieverzoek) aangevinkt is. De behandelaar van deze zaak is de default behandelaar zoals aangegeven bij het zaaktype. Is deze niet gevuld dan zet de programmatuur als behandelaar de ingelogde medewerker die de openstaande actieverzoeken heeft binnen gehaald
    - deze nieuwe zaak wordt gekoppeld aan de locatie met tbperceeladressen.dnkey = *Getal2* van de instelling *Sectie: Koppeling ZAAK Item: DummyLokatiePerceelkey*. Bij compartimenten kijkt OpenWave naar tbcompartiment.dnkeyswfdummyadres
    - aan deze nieuwe zaak wordt de samenwerkingsruimte gekoppeld, die bij het actieverzoek hoort. Deze samenwerkingsruimte is dus door een externe partij aangemaakt
    - bij de nieuwe samenwerkingsruimte worden alle op dat moment bekende ketenpartners van de SWF ruimte opgenomen in de tabel tbswfoinpartners. De ketenpartners zijn daarmee zichtbaar in het blok *Ketenpartners* in het detailscherm van de samenwerkingsruimte
    - aan de nieuwe samenwerkingsruimte wordt het actieverzoek gekoppeld (met dluitgaand = F). De gebruiker kan zelf bij de samenwerkingsruimte de documenten ophalen
    - wanneer bij het zaaktype de verplichte adressoort (rol) is gevuld, dan wordt de OIN van de zender van het actieverzoek opgezocht in de beheertabel tboin. Indien aldaar de kolom *ID uit tbcontactadressen t.b.v. aanvrager bij nieuwe zaak op basis actieverzoek is gevuld* (met een dnkey uit tbcontactadressen), dan wordt bij de nieuwe omgevingszaak dit contactadres toegevoegd onder de gevonden adresrol van het zaaktype.

