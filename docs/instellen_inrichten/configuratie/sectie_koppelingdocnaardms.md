# Sectie KoppelingDOCNAARDMS

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de *Sectie: koppelingDOCNAARDMS* gerangschikt op item. Indien de itemnaam uit twee regels bestaat dan is dat vanwege de leesbaarheid. In de werkelijkheid in de databasetabel staan de twee regels aan elkaar in de kolom dvitem van tbinitialisatie.

OpenWave zal voor het verzenden van StUF Zaak/DMS berichten voor de nodige stuurgegevens en credentials eerst kijken in de beheertabel *Gemeentes* bij de gemeente waar de zaak zich afspeelt. Als daar geen gegevens worden gevonden grijpt het programma terug op onderstaande algemene instellingen. Wat betreft het aan/uitzetten van de methode: indien de zaak speelt in een compartiment dan wordt aldaar (beheerportaal-Nieuw) de methode ingesteld per compartiment.

## Items Configuratietabel

| Item | Kolom | Omschrijving |
|---|---|---|
| AllowAllHostnameVerifier | Aanvinkvakje | Indien aangevinkt is zal de OpenWave Cloud instemmen met een self-signed of verlopen (server)certificaat bij een verbinding onder https met een DMS. |
| AuteurVerplicht | Aanvinkvakje  | StUF bericht voor voegZaakdocumentToe. Indien aangevinkt:

* zal de inlogger als auteur in het bericht worden meegegeven indien het gaat om een automatisch opgeslagen document op basis van sjabloon

* zal *onbekend* als auteur worden meegegeven indien het gaat om een upload van een aangewezen document via de uploadwizard. |
| Charset | Tekst | StUF bericht. Hier kan opgegeven worden welke charset in de transport header wordt gebruikt bijv. utf-8. (default is dat ISO-8859-1). |
| ClientCertificaatNaam | Tekst | Indien er gebruik moet worden gemaakt van een client-certificaat (wordt geplaatst op de CONF-map van de WSAS server) dan staat hier de bestandnaam van dat certificaat. |
| CertificaatPassword | Tekst | Indien er gebruik moet worden gemaakt van een client-certificaat dan staat hier het password (kan gecrypt worden opgeslagen. |
| CertificaatType | Tekst | Het client-certificaattype (default PKCS12). |
| DocumenttypeVerplicht | Aanvinkvakje | Indien aangevinkt zal de inlogger voor elk up te loaden document het documenttype moeten aanwijzen uit een keuzelijst dat wordt meegegeven in StUF bericht voor voegZaakdocumentToe en bij CMIS upload document. |
| CloseConnectionOloDso | Aanvinkvakje | Indien aangevinkt dan wordt de databaseconnectie van een OLO/DSO bijlages die gestreamd naar de OpenWave server is gegaan niet nodeloos opengehouden in het geval dat de verwerking op zich laat wachten vanwege het wachten op het aanvraag/verzoekbericht. |
| Domein | Tekst | Het domein bij HTTPS-authenticatie indien *HTTPAuthenticatieNaam* is aangevinkt. |
| Externedoclink |Tekst| Indien gevuld en *Getal1* heeft de waarde 1  en een document wordt succesvol met StUF zaak/dms naar het DMS verzonden, waarbij dat document ook nog eens in OpenWave geregistreerd wordt, dan wordt  in de kolom tbcorrespondentie.dvurl een string geconstrueerd op basis van deze *Tekst* waarin de substrings %dmszaakcode% en %dmsdoccode%  on the fly worden vervangen door hun echte waarde bij het betreffende document.

Een compartiment heeft hiertoe eigen instellingen (dvexternedoclink en dlextlinkautovul)|
| |Getal1|zie hierboven|
| HTTPAuthenticatieNaam | Tekst | Naam voor authenticatie binnen https. |
| | Aanvinkvakje  | Indien aangevinkt dan wordt de verzending over HTTPS geautoriseerd met naam en wachtwoord. |
| HTTPAuthenticatiePass | Tekst | Wachtwoord voor authenticatie binnen HTTPS. Kan gecrypt zijn opgeslagen. |
| HTTPAuthenticatieType | Tekst | Hier kan desgewenst het authenticatietype worden ingevuld: NTLM (versie 1) of Basic (default waarde). |
| HTTPSoapAction_geefLijstZaakdocumenten_Lv01 | Tekst | StUF-bericht. De kolom *Tekst* moet gevuld worden met juiste soapaction voor geefLijstZaakdocumenten: Indien zaak/DMS dan

`[http://www.egem.nl/StUF/sector/zkn/0310/](http://www.egem.nl/StUF/sector/zkn/0310/.md) geefLijstZaakdocumenten_Lv01`. Indien (oude) stufzaken dan `[http://www.egem.nl/StUF/sector/zkn/0310/zakLv01](http://www.egem.nl/StUF/sector/zkn/0310/zakLv01.md)`.

LET OP: het kan zijn dat deze *Tekst* tussen dubbele quootjes moet staan. |
| HTTPSoapAction_geefZaakdocumentLezen_Lv01 | Tekst | StUF-bericht. De kolom *Tekst* moet gevuld worden met juiste soapaction voor geefZaakdocumentLezen: Indien zaak/DMS dan `[http://www.egem.nl/StUF/sector/zkn/0310/](http://www.egem.nl/StUF/sector/zkn/0310/.md) geefZaakdocumentLezen_Lv01`. Indien (oude) stufzaken dan `[http://www.egem.nl/StUF/sector/zkn/0310/edcLv01](http://www.egem.nl/StUF/sector/zkn/0310/edcLv01.md)`.

LET OP: het kan zijn dat deze *Tekst* tussen dubbele quootjes moet staan. |
| HTTPSoapAction_genereerDocumentIdentificatie_Di02  | Tekst | De kolom *Tekst* moet gevuld worden met juiste soapaction voor genereerDocumentIdentificatie t.b.v. voegZaakdocumentenToe:

`http://www.egem.nl/StUF/sector/zkn/0310/genereerDocumentIdentificatie_Di02`

LET OP: het kan zijn dat deze *Tekst* tussen dubbele quootjes moet staan.
|
| HTTPSoapAction_updateZaakDocument_Di02 | Tekst | De kolom *Tekst*moet gevuld worden met juiste soapaction t.b.v. voegZaakdocumentenToe: `[http://www.egem.nl/StUF/sector/zkn/0310/](http://www.egem.nl/StUF/sector/zkn/0310/.md) updateZaakdocument_Di02`.

LET OP: het kan zijn dat deze *Tekst* tussen dubbele quootjes moet staan. Deze methode wordt gebruikt indien een StUF-document met OnlyOffice wordt bewerkt en weer opgeslagen onder de bestaande documentidentifier. |
| HTTPSoapAction_voegZaakdocumentToe_Lk01 | Tekst | StUF-bericht. De kolom *Tekst* moet gevuld worden met juiste soapaction voor voegZaakdocumentToe: Indien zaak/DMS dan `[http://www.egem.nl/StUF/sector/zkn/0310/](http://www.egem.nl/StUF/sector/zkn/0310/.md) voegZaakdocumentToe_Lk01`. Indien (oude) stufzaken dan `[http://www.egem.nl/StUF/sector/zkn/0310/edcLk01](http://www.egem.nl/StUF/sector/zkn/0310/edcLk01.md)`.

LET OP: het kan zijn dat deze *Tekst* tussen dubbele quootjes moet staan. |
| | Getal1 | De verwerkingssoort van de gerelateerde bij *IsRelevantVoor* van het Voegzaakdocument bericht is hier instelbaar. Indien leeg of ongelijk aan 1, 2 of 3 dan 'T', indien 1 dan ook 'T', indien 2 dan 'I',  indien 3 dan 'W'. |
| InboxmapOLO | Tekst | Een vaste map op de fileshare waar een derde partij OLO-bijlagen kan stallen door achter deze *inboxmapolo* een submap te creëren met als submapnaam het OLO-nummer. |
| | Aanvinkvakje | Indien aangevinkt zal bij het opvragen van de documentenlijst bij een omgevingszaak, OpenWave de documenten op *inboxmapolo* verplaatsen naar de juiste map bij de zaak of naar het DMS via StUFVoegZaakDocumentToe. |
| Login_cmis | Tekst | Loginnaam voor server waarnaar CMIS-vraagbericht wordt verstuurd. |
| MagDocMetadataUpdaten | Aanvinkvakje | Indien aangevinkt kan een geregistreerd document van een zaak die niet aan een compartiment is toegewezen en die in een DMS staat via updateZaakDocument_Di02bericht van een andere naam worden voorzien. Het compartiment heeft hier een aparte kolomnaam voor: tbcompartiment.dldmsupdatemetazaakdoc. |
| MapKopieVerplaatsteFiles | Tekst | UNC-pad van de map (inclusief documentroot) waarnaar met de knop verplaatste files van fileshare naar (StUF) DMS worden gekopieerd. De knop vanuit de algemene documentenlijst waarmee deze actie getriggerd wordt is zichtbaar indien instelling *Sectie: Documenten Item: OphalenViaFileserver* is aangevinkt EN instelling *Sectie: Documenten Item: OphalenViaDMS* is aangevinkt EN de instelling *Sectie: Koppeling ZAAK* en Item: *Methode en Tekst = StUF-ZAKEN 310* is ook aangevinkt. |
| Methode | Tekst | Alleen de waarde *CMIS 1.0* of de waarde *StUF-ZAKEN 310* is toegestaan. |
| | Aanvinkvakje  | Indien aangevinkt dan kunnen documenten opgehaald en geplaatst worden met DMS-services via de opgegeven methode. |
| OloDocType | Tekst | Het documenttype dat toegevoegd moet worden aan een OLO-bijlage dat via automatische verwerking door OpenWave geplaatst wordt in het DMS (defaultwaarde *OLO*). |
| OloVertrouwelijkheid | Tekst | De vertrouwelijkheidsduiding die toegevoegd moet worden aan een OLO.DSO-bijlage die via automatische verwerking door OpenWave geplaatst wordt in het DMS (defaultwaarde *OPENBAAR*). Dit indien vertrouwelijk (in tbomgoloberichten) de waarde F heeft. Indien vertrouwelijk (in tbomgoloberichten) de waarde T heeft, dan wordt de instelling *sectie DSO item: VertalingVertrouwelijkheid* gebruikt|
| Ontvanger_administratie | Tekst | Stuurgegeven StUF bericht voor geefLijstZaakdocumenten en geefZaakdocumentLezen en voegZaakdocumentToe. |
| Ontvanger_applicatie | Tekst | Stuurgegeven StUF bericht voor geefLijstZaakdocumenten en geefZaakdocumentLezen en voegZaakdocumentToe. |
| Ontvanger_gebruiker | Tekst | Stuurgegeven StUF bericht voor geefLijstZaakdocumenten en geefZaakdocumentLezen en voegZaakdocumentToe. |
| Ontvanger_organisatie | Tekst | Stuurgegeven StUF bericht voor geefLijstZaakdocumenten en geefZaakdocumentLezen en voegZaakdocumentToe. |
| Ontvangstadres_Asynchroon | Tekst | StUF-bericht. De kolom *Tekst* moet gevuld worden met juiste endpoint van de zaak/DMS-service voor voegZaakDocumentToe. Bij compartimenten wordt gekeken naar de kolom dlontvangstdatuminedclk01. |
| Ontvangstadres_BeantwoordVraag | Tekst | StUF-bericht. De kolom *Tekst* moet gevuld worden met juiste endpoint van de zaak/DMS-service voor geefLijstZaakdocumenten en geefZaakdocumentLezen. |
| Ontvangstadres_cmis | Tekst | CMIS. De kolom *Tekst*moet gevuld worden met juiste endpoint van de DMS-service voor opvragen van lijst documenten en ophalen en uploaden van een document. |
| Ontvangstadres_VrijeBerichten | Tekst | StUF-bericht. De kolom *Tekst* moet gevuld worden met juiste endpoint van de zaak/DMS-service voor genereerdocumentidentificatie. |
| Ontvangstdatuminedclk01 | Aanvinkvakje  | Indien aangevinkt dan wordt in het edclk01 bericht (uploaden van nieuw document met StUF zaak/dms: voegzaakdcumenttoe) de ontvangstdatum toegevoegd met de datum van vandaag. Bij compartiment kijkt OpenWave naar de kolom tbcompartiment.dlontvangstdatuminedclk01. |
| Pass_cmis | Tekst | Password voor server waarnaar CMIS-vraagbericht wordt verstuurd. Kan gecrypt worden opgeslagen. |
| RichtingalsExtraElement | Aanvinkvakje  | Indien aangevinkt zal bij een updatezaakdocument (bij hernoemen van geregistreerd document) en bij aanmaak van document op basis van sjabloon dat direct wordt opgeslagen in geregistreerde documenten en wordt verzonden naar het DMS (StUF/zaak: voegZaakDocumentToe), een blok extraElementen worden toegevoegd met attribuutnaam **Richting** en als waarde **uitgaand** of **inkomend** of **intern**. Indien de instelling *Sectie: DocumentRegistreren* en *Item: AlleHandmatigeUploads* bestaat en is aangevinkt, dan zal de richting keuze en blok in StUF bericht ook bij handmatige uploads van toepassing zijn. |
| StatusVerplicht | Aanvinkvakje  | Indien aangevinkt zal de inlogger voor elk up te loaden document de status moeten intikken dat wordt meegegeven in StUF bericht voor voegZaakdocumentToe. |
| StUFGeefDocumentMetScope | Aanvinkvakje  | StUF bericht geefZaakdocumentLezen. Indien aangevinkt wordt bij het opvragen van de scope van kerngegevens van een document deze expliciet uitgevraagd i.p.v. volstaan met attribuut scope="kerngegevens" (default). |
| SynchroniseerVanuitDMS | Aanvinkvakje  | Indien aangevinkt komt onderaan de lijst van geregistreerde documenten (mits compartiment ok, niet geblokkeerd en DMS-koppeling) een synchronisatieknop waarmee de geregistreerde documenten (die voorzien zijn van een externe documentidentifier) worden gesynchroniseerd vanuit het DMS (het DMS is dan leidend). Indien de zaak speelt in een compartiment kijkt OpenWave naar tbcompartiment.dlsynchroniseervanuitdms. |
| | Getal1 | Indien de waarde 1, dan zal bij het hernoemen van een geregistreerd document dat zich bevindt in het DMS, deze eerst automatisch worden gesynchroniseerd. Voor een compartiment kijkt OpenWave naar tbcompartiment.dlautosynchroniseervanuitdms. |
| TestOpFakeEndpoint | Aanvinkvakje  | Indien aangevinkt dan kan als *Ontvangstadres_VrijeBerichten* en *Ontvangstadres_Asynchroon* een fake-endpoint zoals [www.rem.nl](http://www.rem.nl.md) worden gebruikt, waarna het programma zelf een fake documentidentificatiecode genereert waarmee het vervolgbericht geefZaakDocumentlezen in ieder geval gecreëerd wordt, waarschijnlijk niet verwerkt, maar wel is opgeslagen in de messagelog. |
| TitelVerplicht | Aanvinkvakje  | Indien aangevinkt zal de inlogger voor elk up te loaden document een titel moeten intikken (default is de titel gelijk aan de bestandnaam) dat wordt meegegeven in StUF bericht voor voegZaakdocumentToe. |
| UitgaandWin1252 | Aanvinkvakje | Indien aangevinkt worden alle tekens boven ASCII-waarde 127 in het uitgaande StUFbericht omgezet (ë naar e etcetera) ongeacht instelling van de charset. |
| VerplaatsmapOLO | Tekst | Cmis. Een vaste map waar een derde partij in het DMS OLO-bijlagen kan stallen door achter deze *verplaatsmapolo* een submap te creëren met als submapnaam het OLO-nummer waar de bijlagen bij horen. Bij het opvragen van de documentenlijst bij een omgevingszaak via CMIS zal OpenWave deze documenten verplaatsen naar de juiste map bij de zaak. |
| VertrouwelijkheidVerplicht | Aanvinkvakje  | Indien aangevinkt zal de inlogger voor elk up te loaden document de vertrouwelijkheidsduiding moeten aanwijzen uit een keuzelijst dat wordt meegegeven in StUF bericht voor voegZaakdocumentToe. |
| VerzenddatumSturen | Aanvinkvakje | Indien aangevinkt, dan zal bij het creëren van een email de tag `<verzenddatum>` gevuld met de dag van vandaag (fn_vandaag(0)) meegestuurd worden met het voegZaakdocumentToe_Lk01-bericht. |
| WachtOpExtAantalSeconden | Getal1 | Het aantal seconden (default 2) dat OpenWave wacht bij een geautomatiseerd proces voor het plaatsen van OLO-bijlages. Eerst wordt gewacht of de zaak in OpenWave al is gemaakt en vervolgens kan dan ook nog eens gewacht worden op het DMS voor uitgifte van een extern zaakidentificatienummer dat ook via een geautomatiseerd proces aangemaakt wordt bij het verwerken van het OLO-bericht zelf. Dat kan soms even duren. *Getal1* x *Getal2* mag niet boven 10 minuten komen (thread instelling in de applicatieserver). Advies bij veel documenten per zaak: aantal seconden = 180. |
| | Getal2 | Het aantal pogingen (default 5) dat OpenWave doet (met tussenpozen van *Getal1* seconden) om uit te vissen of een zaak is aangemaakt of externe zaakidentificatie is uitgegeven. Het aantal pogingen moet 2 of groter zijn (Advies bij veel documenten per zaak = 3). |
| WaveKolomMapIsStUFTag | Tekst | StUF bericht geefLijstZaakdocumenten. Kan gevuld worden met `<titel>`. Indien dat het geval is wordt de tag van het retourbericht titel gebruikt voor het vullen van de Wavekolom Map (default wordt deze gevuld met dct.omchrijving). |
| WaveKolomTitelIsStUFTag | Tekst | StUF bericht geefLijstZaakdocumenten. Kan gevuld worden met `<dct.omschrijving>`. Indien dat het geval is wordt de tag van het retourbericht dct.omschrijving gebruikt voor het vullen van de Wavekolom Titel (default is dat met titel). |
| ZakLV01MetDCTOmschrijving | Aanvinkvakje | Indien aangevinkt zal in het zakLv01 bericht (geefLijstZaakDocument) de tag dct.omschrijving worden opgenomen in de scope. Vanwege discrepantie tussen de officiële validator en beschrijving is dit niet standaard het geval, hoewel veel DMS-sen in het antwoordbericht toch de dct.omschrijving retourneren ongeacht de vraag. |
| Zender_administratie | Tekst | Stuurgegeven StUF bericht voor geefLijstZaakdocumenten en geefZaakdocumentLezen en voegZaakdoucmentToe. |
| Zender_applicatie | Tekst | Stuurgegeven StUF bericht voor geefLijstZaakdocumenten en geefZaakdocumentLezen en voegZaakdoucmentToe. |
| Zender_gebruiker | Tekst | Stuurgegeven StUF bericht voor geefLijstZaakdocumenten en geefZaakdocumentLezen en voegZaakdoucmentToe. |
| Zender_organisatie | Tekst | Stuurgegeven StUF bericht voor geefLijstZaakdocumenten en geefZaakdocumentLezen en voegZaakdoucmentToe. |
