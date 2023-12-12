# Register Externe Veiligheid

Vanuit OpenWave kunnen gegevens periodiek worden aangeleverd aan het Register Externe Veiligheid (REV). Daartoe is het Informatiemodel Externe Veiligheid (IMEV) ingepast in de OpenWave database.

Zie voor synchronisatie van gegevens uit het REV naar OpenWave: [REV-synchroniseren](/docs/probleemoplossing/programmablokken/rev_synchroniseren.md)

## Beheer

Aan de beheerkant van OpenWave is het IMEV zichtbaar in de volgende structuur:

![](/img/applicatiebeheer/instellen_inrichten/ow_rev_structuur_beheer.png){ class="media" loading="lazy" alt="" width="800" }

Via beheerportaal *Inrichtingenbeheer* zijn onder de kolom *Registratie en Veiligheid* deze tabellen terug te vinden, waarbij datatypes in OpenWave vertaald zijn naar (D): string op basis van Doorkieslijst, (I)nteger, (F)loat, (S)tring op basis van invoer en (B)oolean.

De kardinaliteit is terug te zien in het aanvinkvakje *Overnemen* en de daaraan gekoppelde verplichting om een waarde te vullen.

### Definitietabel tbmilcodebkl

Achter de tegel *REV BKL-activiteiten* bevindt zich de (gevulde) tabel met de EV-activiteiten uit het IMEV model. De meeste EV-activiteiten horen bij de hoofdgroep LocatieActiviteit (andere mogelijkheden zijn BuisleidingStelsel, Wegen en LocatieBasisnet). Bij elke EV-activiteit zijn de attributen uit het IMEV-model overgenomen (0 of maximaal 5) met het kolomtype dat daar bij hoort. Indien het type Doorkieslijst is, dan is de naam van de bijbehorende waardelijst uit het IMEV-model gevuld.

Met het __aanvinkvakje overnemen__ wordt geregeld dat wanneer de betreffende activiteit aan een inrichting wordt toegekend (in de tabel tbmilbklactiviteiten), dan het betreffende attribuut aldaar wordt overgenomen met de verplichting om dit attribuut van een waarde te voorzien alvorens de activiteit naar het REV geëxporteerd kan worden. Het IMEV heeft en aantal attributen verplicht gesteld. Het aanvinkvakje overnemen is voor deze attributen initieel gevuld in OpenWave. Ook de attributen die van invloed zijn op het automatisch toekennen van EV-contouren (zie hieronder bij de tabel tbrevafstanden) zijn initieel aangevinkt.

Bij elk attribuut kan een omschrijving worden opgegeven bijvoorbeeld ten behoeve van de gevraagde eenheid. Deze beschrijvingen zijn aan de voorkant bij de invoer van de betreffende attribuutwaardes zichtbaar te maken. Zoveel mogelijk zijn de beschrijvingen alvast uit het IMEV overgenomen. Aanpassing hiervan heeft geen consequentie voor de programmalogica.

**LET OP:** de objectbenamingen, de attribuutnamen en types en waardelijstnamen moeten WEL exact zo zijn als in het IMEV-model zijn opgegeven.

### Definitietabel tbrevrefcontour

Achter de tegel *REV Referentie EV contouren* bevindt zich de (gevulde) tabel met de Referentiecontouren uit het IMEV model. Bij elke referentiecontour zijn de attributen uit het IMEV-model overgenomen (0 of maximaal 16) met het kolomtype dat daar bij hoort. Indien het type doorkieslijst is, dan is de naam van de bijbehorende waardelijst uit het IMEV-model gevuld.

Met het __aanvinkvakje overnemen__ wordt geregeld dat wanneer de betreffende referentiecontour aan een EV-activiteit bij een inrichting wordt toegekend (in de tabel tbmilopslag), dan het betreffende attribuut aldaar wordt overgenomen met de verplichting om dit attribuut van een waarde te voorzien alvorens de referentiecontour naar het REV geëxporteerd kan worden. Het IMEV heeft een aantal attributen verplicht gesteld. Het aanvinkvakje overnemen is voor deze attributen initieel gevuld in OpenWave. Ook de attributen die van invloed zijn op het automatisch toekennen van EV-contouren (zie hieronder bij de tabel tbrevafstanden) zijn initieel aangevinkt.

Bij elk attribuut kan een omschrijving worden opgegeven bijvoorbeeld ten behoeve van de gevraagde eenheid. Deze beschrijvingen zijn aan de voorkant bij de invoer van de betreffende attribuutwaardes zichtbaar te maken. Zoveel mogelijk zijn de beschrijvingen alvast uit het IMEV overgenomen. Aanpassing hiervan heeft geen consequentie voor de programmalogica.

**LET OP:** de objectbenamingen, de attribuutnamen en types en waardelijstnamen moeten WEL exact zo zijn als in het IMEV-model zijn opgegeven.

### Koppeltabel activiteit/referentiecontour

In het IMEV-model is vastgelegd welke referentiecontouren bij welke EV-activiteiten mogelijk zijn. In OpenWave vindt dit zijn weerslag in de koppeltabel tbkoppelbklactrefcontour. Zichtbaar in het blok *Gekoppelde referentiecontouren* op de detailkaart van de definitietabel tbmilcodebkl.

### Definitietabel tbrevevcontour

Achter de tegel *REV EV contouren* bevindt zich de (gevulde) tabel met de EV-contouren uit het IMEV model. Bij elke EV-contour zijn de attributen uit het IMEV-model overgenomen (0 of maximaal 10) met het kolomtype dat daar bij hoort. Indien het type Doorkieslijst is, dan is de naam van de bijbehorende waardelijst uit het IMEV-model gevuld.

Met het __aanvinkvakje overnemen__ wordt geregeld dat wanneer de betreffende EV-contour aan een referentiecontour bij een inrichting wordt toegekend (in de tabel tbmilopslagevcontour), dan het betreffende attribuut aldaar wordt overgenomen met de verplichting om dit attribuut van een waarde te voorzien alvorens de EV-contour naar het REV geëxporteerd kan worden. Het IMEV heeft een aantal attributen verplicht gesteld. Het aanvinkvakje overnemen is voor deze attributen initieel gevuld in OpenWave.

Bij elk attribuut kan een omschrijving worden opgegeven bijvoorbeeld ten behoeve van de gevraagde eenheid. Deze beschrijvingen zijn aan de voorkant bij de invoer van de betreffende attribuutwaardes zichtbaar te maken. Zoveel mogelijk zijn de beschrijvingen alvast uit het IMEV overgenomen. Aanpassing hiervan heeft geen consequentie voor de programmalogica.

**LET OP:** de objectbenamingen, de attribuutnamen en types en waardelijstnamen moeten WEL exact zo zijn als in het IMEV-model zijn opgegeven.

### Koppeltabel activiteit/EV-contour

In het IMEV-model is vastgelegd welke EV-contouren bij welke EV-activiteiten mogelijk zijn. In OpenWave vindt dit zijn weerslag in de koppeltabel tbkoppelbklactevcontour. Zichtbaar in het blok *Gekoppelde EV-contouren* op de detailkaart van de definitietabel tbmilcodebkl.

### Waardelijsten

De in te vullen attributen van de activiteiten, referentiecontouren, EV-contouren en kwetsbare gebouwen/locaties kunnen gekoppeld zijn aan dwingende waardelijsten. In OpenWave krijgt in dat geval het type attribuut de waarde 'D' (van Doorkieslijst) en wordt het attribuut direct gekoppeld aan de naam van de betreffende waardelijst. Die waardelijsten zijn gevuld aangeleverd in de tabellen tbrevwaardelijsten en tbrevitemswaardelijsten achter de tegel *REV-waardelijsten*.

**LET OP:** de waardelijstnamen en items-benamingen moeten exact zo zijn als in het IMEV-model zijn opgegeven.

### Definitietabel Kwetsbare gebouwen/locaties

Achter de tegel *REV Kwetsbare gebouwen locaties* bevindt zich de (gevulde) tabel tbrevkwetsbaargebouwlocatie met de twee kwetsbaarheidsdefinities uit het IMEV model. Bij de twee kwetsbaarheidsdefinities zijn de attributen uit het IMEV-model overgenomen (0 of maximaal 7) met het kolomtype dat daar bij hoort. Indien het type Doorkieslijst is, dan is de naam van de bijbehorende waardelijst uit het IMEV-model gevuld.

Met het __aanvinkvakje overnemen__ wordt geregeld dat wanneer het betreffende kwetsbare gebouw-of locatie definitie bij een inrichting wordt toegekend (in de tabel tbmilbklkwetsbgebloc), dan het betreffende attribuut aldaar wordt overgenomen met de verplichting om dit attribuut van een waarde te voorzien alvorens het gebouw of locatie naar het REV geëxporteerd kan worden. Het IMEV heeft een aantal attributen verplicht gesteld. Het aanvinkvakje overnemen is voor deze attributen initieel gevuld in OpenWave.

Bij elk attribuut kan een omschrijving worden opgegeven bijvoorbeeld ten behoeve van de gevraagde eenheid. Deze beschrijvingen zijn aan de voorkant bij de invoer van de betreffende attribuutwaardes zichtbaar te maken. Zoveel mogelijk zijn de beschrijvingen alvast uit het IMEV overgenomen. Aanpassing hiervan heeft geen consequentie voor de programmalogica.

**LET OP:** de objectbenamingen, de attribuutnamen en types en waardelijstnamen moeten exact zo zijn als in het IMEV-model zijn opgegeven.

### TbRevJsonMallen

Deze tabel met voorbeelden van Json exportdefinities per EV-activiteit wordt gevuld aangeleverd en wordt door OpenWave gebruikt voor de opmaak van de Json export files. Niet aankomen dus.

### TbREVAfstanden: regels voor automatisch invoegen van een of meer EV-contouren

Deze tabel is gevuld. Niet op grond van IMEV, naar op grond van aangeleverde regels van een omgevingsdienst. De bedoeling van deze tabel is vast te leggen welke EV-contouren bij een bepaalde referentiecontour (die op zijn beurt - per definitie - gekoppeld is aan een EV-activiteit) automatisch kunnen worden aangemaakt op grond van de ingevulde attributen bij de activiteit en of referentiecontour.

![](/img/applicatiebeheer/instellen_inrichten/revafstanden.png){ class="media" loading="lazy" alt="" width="800" }

Bovenstaand voorbeeld betekent dat indien bij een referentiecontour (tbmilopslag)  met de definitie *OpslagReferentie* waarbij:

  - het attribuut *typeOpslagReferentie* is gevuld met Opslagtank
  - EN waarbij het attribuut *Inhoud* een waarde heeft tussen 5 en 13
  - EN waarbij attribuut *bovengronds* gevuld is met (F)alse
  - EN waarbij de referentiecontour Opslagreferentie is gekoppeld aan een EV-activiteit met definitie OpslagtankPropaanPropeen_VasteAfstandGeenVergunningplicht
  - EN het attribuut *aantalBevoorrradingen* van die activiteit is groter dan 5

DAN zal het gebruik van de wizardknop *Haal EV-contouren uit afstandentabel* onder aan het lijstje van EV-contouren binnen de detailkaart van die tbmilopslagkaart (referentiecontour) resulteren in de aanmaak van de volgende EV-contourkaarten in de tabel tbmilopslagevcontour:

  - een kaart met definitie PR-Contour met afstand 25 en typePlaatsgebondenRisico = Beperkt kwetsbaar en maatgevende stof/categorieNaam = brandbaar gas en maatgevende stof/chemischeNaam = propaan
  - een kaart met definitie PR-Contour met afstand 25 en typePlaatsgebondenRisico = Kwetsbaar en maatgevende stof/categorieNaam = brandbaar gas en maatgevende stof/chemischeNaam = propaan
  - een kaart met definitie PR-Contour met afstand 50 en typePlaatsgebondenRisico = Zeer Kwetsbaar en maatgevende stof/categorieNaam = brandbaar gas en maatgevende stof/chemischeNaam = propaan
  - een kaart met definitie Brandaandachtsgebied met afstand 20 en typeBrand = fakkelbrand en maatgevende stof/categorieNaam = brandbaar gas en maatgevende stof/chemischeNaam = propaan.

Voor alle aangemaakte EV-contour-kaarten geldt bovendien dat de beginGeldigheid als waarde datum van vandaag krijgt.

## Activiteiten, contouren, kwetsbare gebouwen/locaties bij een inrichting

![](/img/applicatiebeheer/instellen_inrichten/ow_rev_structuur_inrichting.png){ class="media" loading="lazy" alt="" width="800" }

De groene blokken slaan op tabellen van de OpenWave database die ook buiten het REV om bestaan: Er zijn veel inrichtingen die geen Locatie-EVactiviteit zijn (dus geen EV-activiteiten hebben) en een tbmilopslagkaart hoeft geen referentiecontour te zijn (dat wil zeggen hoeft niet gekoppeld te zijn aan een EV-activiteit).

### Inrichtingen (locatie-EV-activiteiten)

Op de detailkaart van een inrichting is het blok REV opgenomen.

Een **locatie-EVactivteit** in het IMEV (een locatie waar de activiteit met externe veiligheidsrisico’s wordt verricht) is in OpenWave een inrichting van een bepaald type. Dit type is bepalend voor welke EV-activiteiten (zie hieronder) bij een inrichting kunnen worden gedefinieerd:

  - LocatieActiviteit (locatie van een bedrijf waar de activiteit met externe veiligheidsrisico’s wordt verricht) waarbij
    - het blok *Polygoon of Lijn* gevuld moet zijn met een polygoon dat aangeeft op welke grondgebied de EV-activiteiten plaatsvinden.
  - Wegen (geheel van locaties voor het vervoer van gevaarlijke stoffen over de weg) waarbij
    - het blok *Polygoon of Lijn* gevuld moet zijn met een lijn of Multilijn
    - de kolom *Traject vervoer gev. stof (route)* gevuld moet worden.
  - LocatieBasisnet (geheel van locaties voor het vervoer van gevaarlijke stoffen over het basisnet) waarbij
    - het blok *Polygoon of Lijn* gevuld moet zijn met een lijn of Multilijn
    - de kolom *Traject vervoer gev. stof (route)* gevuld moet worden
    - de kolom *Type vervoer* gevuld moet worden.
  - BuisleidingStelsel (een stelsel van meerdere Buisleidingen)
    - waarbij de inhoud van het blok *Polygoon of Vlak* niet van toepassing is
    - de kolom *eigenaar* gevuld moet worden.

Indien het blok *Polygoon of Lijn* gevuld moet zijn, maar leeg is, zal OpenWave bij de export naar REV proberen de benodigde gegevens uit de kolom dvgmlpolygoon van het bijbehorende perceeladres van de inrichting te halen. Is die ook leeg of van verkeerd Geotype dan volgt een foutmelding.

Indien het blok *Polygoon of Lijn* leeg is, dan is onder het menu opties de keuzes *Teken vlak op kaart* zichtbaar.

De datum **Datum laatste preview ok** (ddrevpreviewok) wordt alleen gevuld indien de preview export Json, die gestart wordt met de knop achter deze kolom, geen fouten heeft opgeleverd. Indien datum laatste wijziging kleiner is dan deze previewdatum, zou deze inrichting met activiteiten, referentie- en EV-contouren probleemloos geëxporteerd kunnen worden.

Voor de daadwerkelijke export dient echter ook de kolom **Klaargezet voor Export** (ddmagexport) gevuld te zijn. Deze datumkolom kan alleen gevuld worden door iemand met het recht: *mag inrichting klaarzetten voor export REV* (tbmedewerkers.dlmagrevexportzetten) op de medewerkerskaart. Onder water wordt bij het vullen of leeghalen van deze datum de kolom **Door:** (dvcodemwmagexport) gevuld met de medewerkerscode.

Deze datumkolom wordt automatisch leeggemaakt indien een wijziging plaatsvindt op één van de te exporteren REV-attributen of onderliggende activiteiten/contouren. De kolom **Door:** (dvcodemwmagexport) wordt bij het automatisch leegmaken van ddmagexport gevuld met de medewerkerscode van de inlogger die een attribuut heeft gewijzigd.

De REV **identificatiecode** van de locatie EV-activiteit wordt automatisch berekend bij het wijzigen van de beginGeldigheid datum, mits de identificatiecode een lege waarde heeft. De waarde wordt opgebouwd met de kolom *Tekst* van de instelling *Sectie: Inrichtingen en Item: revnamespaceidentificatie* gevolgd door een punt gevolgd door het inrichtingsnummer gevolgd door een underscore gevolgd door de dnkey van de inrichting. Dus zoiets als NL.IMEV.00002.4567_123.

Alleen indien de datum ExportnaarREV nog leeg is EN de inlogger het recht *Wijzigen van REV-identificatiecode van tbmilinrichtingen* (tbmilrechten.dlbmilinrrevidedt) heeft, kan de inlogger hier zelf een code toekennen.

De kolom **OW-identificatie** (dvrevbronobjectid) kan gebruikt worden om de locatie-EVactiviteit zowel in het REV als in OpenWave met een eigen codering te vullen. Toepassing: zie [REV-synchroniseren](/docs/probleemoplossing/programmablokken/rev_synchroniseren.md).

De **beginGeldigheid** slaat hier op de begin geldigheid van de Locatie-EVactiviteit. Een wijziging op beginGeldigheid wordt niet geaccepteerd indien de datum ExportNaarREV reeds is gevuld. Een beginGeldigheid moet - op het moment van export - kleiner zijn dan vandaag. Indien de Locatie-EVactiviteit voor het eerst wordt geëxporteerd (met een POST, wanneer de exportdatum dus nog leeg is) dan moet deze kleiner of gelijk zijn - dus eerder gestart zijn - dan de beginGeldigheid van de onderliggende EV-activiteiten (in tbmilbklactiviteiten). Bij een succesvol geaccepteerd wijzigingsbericht (een PUT), wanneer een of meer attributen van waarde zijn veranderd, zal de beginGeldigheid automatisch met de datum van de export worden vervangen.

De **eindGeldigheid** slaat hier op de eindgeldigheid van de Locatie-EVactiviteit. Een wijziging wordt alleen geaccepteerd bij een gevulde begingeldigheidsdatum. De eindGeldigheid moet groter zijn dan de beginGeldigheid. Een eindeGeldigheid mag niet in de toekomst liggen. Indien de datum ExportNaarREv is gevuld en de oude waarde van ddeindGeldiheid was ook gevuld met een waarde kleiner dan de exportdatum, dan wordt de wijziging niet geaccepteerd. Bij een wijziging die wel wordt geaccepteerd zullen alle onderliggende eindGeldigheidsdatums van EV-activiteiten en contouren (voor zover die voorzien zijn van een gevulde beginGeldigheid) zo nodig worden aangepast naar deze datum.

De **datum laatst gewijzigd** wordt automatisch gevuld met het moment, waarop een van de volgende inrichtingskolommen een nieuwe waarde krijgt: polygoon, kvknr, handelsnaam, inrichtingsnaam, of de REV-Kolommen: dvroutebasisnetwegen, dvvervoerstypebasisnet, dveigenaarbuislst, dvlocatieevactiviteit en ddbeginGeldigheid, ddeindGeldigheid, dvrevbagnummerid, dvrevbronobjectid en dvrevlocatieomschrijving.

De **datum laatste wijziging set** is een berekend veld en belangrijk voor de automatische geschedulede export naar het REV. De set van contouren en activiteiten van een inrichting worden opnieuw geëxporteerd indien deze datum *laatste wijziging set* groter is dan de datum exportnaarREV. De *datum laatste wijziging set* (in de view vwfrmmilinrichtingen de kolom ddmaxlaatstgewijzigd) is de hoogste waarde (max()) van de datums laatst gewijzigd bij de inrichting en de bijbehorende EV-activiteiten (tbmilbklactiviteiten) en de bijbehorende referentiecontouren (tbmilopslag) en de bijbehorende EV-contouren (tbmilopslagevcontour).

De datum **geëxporteerd naar REV** (ddexportnaarREV) wordt automatisch gevuld op het moment dat een gehele set - dus: inrichting (locatie-EVactiviteit) met alle onderliggende objecten (EV-activiteiten, referentie- en EV-contouren) - succesvol is geëxporteerd naar het REV. De geschedulede export naar REV (zie verderop) loopt alle inrichtingskaarten af waarvoor onder meer geldt dat de *datum laatste wijziging set* groter is dan deze datum *geëxporteerd naar REV*.

Eenmaal geëxporteerd betekent dat de locatie-EVactiviteit ook bestaat in het REV. Dat kan alleen ongedaan worden gemaakt met een gevulde eindeGeldigheid die dan opnieuw geëxporteerd moet worden.

Met de schermknop **preview export Json** wordt de gehele set - dus: inrichting (locatie-EVactiviteit) met alle onderliggende objecten (EV-activiteiten, referentie- en EV-contouren) - omgezet naar een Json exportfile en aangeboden aan het REV ter validatie (validate only) zonder dat het REV de wijzigingen doorzet naar het register.

Endpoint en APIkey en bronhouderscode dienen gevuld te zijn (respectievelijk kolom *Tekst* van *Sectie: REV en Item: AlgemeenEndpoint* en kolom *Tekst* van *Sectie: REV en Item: Apikey* en kolom *Tekst* van *Sectie: REV en Item: Bronhouder*). Bronhouderscode en APIkey worden door Geodan uitgegeven. Bij ontbreken komt een leeg scherm.

OpenWave controleert of (de gevuld aangeleverde) Json-mallen (zie hierboven bij beheer) nog compleet gevuld zijn. De preview controleert zoveel mogelijk op voorhand of de te exporteren set van objecten aan alle voorwaarden voldoet. Bijv.

  - Bij een inrichting moet minimaal één geldige EV-activiteit gedefinieerd zijn, en per activiteit minimaal één geldige referentiecontour en bij de referentiecontouren minimaal één geldige EV-contour gedefinieerd zijn.
  - De objecten moeten voldoen aan alle regels met betrekking tot de begin- en eindGeldigheid.
  - De datum laatst gewijzigd moet groter zijn dan de datum geëxporteerd naar REV.
  - Alle objecten moeten een gevulde identificatiecode hebben.
  - De attributen bij elk object moeten alle een gevulde waarde hebben.

Indien een controle faalt wordt dit in tekst op scherm vertoont en gaat er geen bericht naar het REV.

Bij succes wordt de Json file (van die ene inrichting met alle onderliggende objecten) naar het REV geëxporteerd ter validatie. Deze exportfile wordt in het scherm getoond alsmede het retourbericht van het REV.

Retourcode 200 of 201 betekent dat het bericht succesvol geaccepteerd is door de validatieprocedure van het REV. Bij succes wordt *Datum laatste preview ok* (ddrevpreviewok) op de inrichtingskaart automatisch gevuld.

Voor de daadwerkelijke export - dus die loopt via de taskscheduler - dient echter ook de kolom **Klaargezet voor Export** (ddmagexport) gevuld te zijn. Deze datumkolom kan alleen gevuld worden door iemand met het recht: *mag inrichting klaarzetten voor export REV* (tbmedewerkers.dlmagrevexportzetten) op de medewerkerskaart. Onder water wordt bij het vullen of leeghalen van deze datum de kolom **Door:** (dvcodemwmagexport) gevuld met de medewerkerscode.

De schermknop **Toon gegevens REV** is alleen zichtbaar indien de datum *geëxporteerd naar REV* (ddexportnaarREV) gevuld is. De gehele set aan objecten zoals die geregistreerd staan in het REV wordt opgehaald en getoond (als Json) op basis van de REV-identificatiecode van de inrichting.

De **locatieomschrijving** wordt doorgegeven aan het REV in de Json-tag *locatieomschrijving* met de hier ingevoerde waarde. Indien leeg dan wordt het locatie-adres uit tbperceeladressen gebruikt om de tag locatieomschrijving te vullen.

De **BAG-nummerid** kan gevuld worden met de BAG nummeraanduiding-identifier van de locatie. Indien gevuld wordt deze in de Json-tag *adres* doorgegeven. Deze doublure is helaas nodig omdat anders bij synchronisatie het REV bepalend zou zijn voor de officiële nummeraanduidng in tbperceeladressen.

### TbMilBklActiviteiten (EV-activiteiten)

Te benaderen via de tegel *REV BKL-activiteiten* op het inrichtingportaal.

Het inzien, wijzigen en insert van gegevens is verder gekoppeld aan de SBI/MBA/BKL rechten bij een inrichting (tbmilrechten.dlcmilinrsbivsb).

Aan een inrichting kunnen meerdere EV-activiteiten worden gedefinieerd. De codelijst op basis van de definitietabel tbmilcodebkl wordt gefilterd op de locatie-EVactiviteit van de inrichting.

De activiteit heeft op de detailpagina een aantal standaardkolommen + een aantal - per activiteit verschillende - attributen.

De **geometrie** is dezelfde als die van de bovenliggende inrichting.

De **identificatiecode** wordt automatisch toegekend. De waarde wordt opgebouwd met de kolom *Tekst* van de instelling *Sectie: Inrichtingen en Item: revnamespaceidentificatie* gevolgd door een punt gevolgd door de naam van de activiteit gevolgd door een underscore gevolgd door de dnkey van de activiteit. Dus zoiets als NL.IMEV.00002.AmmoniakKoelinstallatie_TeBerekenenAfstand_12.

De **beginGeldigheid** slaat hier op de begin geldigheid van de EV-activiteit. Een wijziging op beginGeldigheid wordt niet geaccepteerd indien de datum ExportNaarREV reeds is gevuld. Een beginGeldigheid moet op het moment van export kleiner zijn dan vandaag. Indien de EV-Activiteit voor het eerst wordt geëxporteerd (met een POST, wanneer de exportdatum dus nog leeg is) dan moet deze kleiner of gelijk zijn - dus eerder gestart zijn - dan de beginGeldigheid van de onderliggende referentiecontouren (in tbmilopslag).

Omgekeerd geldt dus dat de beginGeldigheid bij een POST groter of gelijk moet zijn aan de beginGeldigheid van de bovenliggende Locatie-EVactivieit (de inrichting). Bij een succesvol geaccepteerd wijzigingsbericht (een PUT, wanneer de exportdatum reeds gevuld is), waarbij een of meer wijzigingen op attributen worden doorgegeven, zal de beginGeldigheid automatisch met de datum van de export worden vervangen.

De **eindGeldigheid** slaat hier op de eindgeldigheid van de EV-activiteit. Een wijziging wordt alleen geaccepteerd bij een gevulde begingeldigheidsdatum. De eindGeldigheid moet groter zijn dan de beginGeldigheid. Een eindeGeldigheid mag niet in de toekomst liggen. Indien de datum ExportNaarREv is gevuld en de oude waarde van ddeindGeldiheid was ook gevuld met een waarde kleiner dan de exportdatum, dan wordt de wijziging niet geaccepteerd. Bij een wijziging die wel wordt geaccepteerd zullen alle onderliggende eindGeldigheidsdatums van referentie- en EV-contouren (voor zover die voorzien zijn van een gevulde beginGeldigheid) zo nodig worden aangepast naar deze datum.

De **datum laatst gewijzigd** wordt automatisch gevuld met het moment, waarop een van de kolommen een nieuwe waarde krijgt.

De datum **geëxporteerd naar REV** (ddexportnaarREV) wordt automatisch gevuld op het moment dat een gehele set - dus: inrichting (locatie-EVactiviteit) met alle onderliggende objecten (EV-activiteiten, referentie- en EV-contouren) - succesvol is geëxporteerd naar het REV. Eenmaal geëxporteerd betekent dat de EV-activiteit ook bestaat in het REV. Dat kan alleen ongedaan worden gemaakt met een gevulde eindeGeldigheid die dan opnieuw geëxporteerd moet worden.

De kolom **vergunningplicht** heeft default de waarde (F)alse.

De kolommen **vergunningsnummer, bevoegdgezag en kvknrAanvrager** mogen leeg blijven (zij krijgen in dat geval in het Register de waarde: waardeOnbekend).

In het blok **Notitie** kan een eigen notitie worden opgegeven. Deze tekst heeft geen referentie in het REV.

In het **blok Kenmerken** zijn de attributen overgenomen uit de definitietabel tbmilcodebkl (zie hierboven) waarbij het vakje *Overnemen* aangevinkt is. Deze attributen moeten een gevulde waarde krijgen alvorens de activiteit geëxporteerd kan worden. Het vraagtekenschermknopje toont de omschrijving van het attribuut zoals gedefinieerd in de definitietabel tbmilcodebkl. Deze omschrijving heeft geen invloed op de export.

Onderaan in het detailscherm van de activiteit is in het blok *referentiecontouren* een lijstje van gekoppelde referentiecontouren (tbmilopslagkaarten) te zien. Zie voor de insert hieronder bij tbmilopslag (referentiecontouren).

### TbMilOpslag (Referentiecontouren)

De referentiecontouren zijn onderdelen van de bestaande tbMilOpslagkaarten in OpenWave.

Het inzien, wijzigen en insert van gegevens is verder gekoppeld aan de bestaande opslagrechten bij een inrichting (tbmilrechten.dlcmilinropsvsb).

In de detailkaart van tbmilopslag zijn de blokken **REV activiteit referentie contour** en **Kenmerken referentiecontour** toegevoegd. Dat laatste blok is alleen zichtbaar indien de opslagkaart aan een EV-activiteit is gekoppeld. De blokken met de geometriegegevens zijn verplaatst naar de plek onder deze nieuwe blokken.

Om een **bestaande tbmilOpslagkaart als referentiecontour te koppelen** aan een EV-activiteit (tbmilbklactiviteiten) kan in het blok *REV activiteit referentie contour* de schermknop *Kies activiteit en referentiecontour* worden gebruikt. De inlogger dient dan een EV-activiteit te kiezen (uit de set die reeds gekoppeld is aan de bovenliggende inrichting) en vervolgens op basis van de *koppeltabel activiteit/referentiecontour* (zie beheer) een referentiecontour.

Om direct een **nieuwe opslagkaart met referentiecontour** toe te voegen kan de insertknop worden gebruikt onderaan het lijstje van gekoppelde referentiecontouren in het detailscherm van de EV-activiteit. Ook hier wordt de keuze van de mogelijke referentiecontouren beperkt door de *koppeltabel activiteit/referentiecontour*.

De opslagkaart kent van oudsher een aantal verplichte kolommen die bij een insert moeten worden gevuld. Een aantal daarvan is eigenlijk dubbelop met betrekking tot de REV-data. Onder het kopje *Nieuwe Opslagkaart* van [Opslagtabel bij inrichtingen](/docs/instellen_inrichten/opslag_bij_inrichtingen.md) wordt uitgelegd hoe hiertoe defaultwaardes in te stellen.

De **geometrie** van de referentiecontour is vastgelegd in een punt (in het blok *geometrie punt*) of door een vlak of lijn (in het blok *geometrie lijn of vlak*). Zie ook hieronder bij attribuut geometrie.

Indien de x en y coördinaat van het blok *geometrie punt* leeg zijn, dan is onder het menu Opties de keuze *wijs punt aan op kaart* zichtbaar.

Indien het blok *geometrie lijn of vlak* leeg is, dan zijn onder het menu Opties de keuzes *Teken vlak op kaart* en *Teken lijn op kaart* zichtbaar.

Het blok *Kenmerken referentiecontour* op de detailpagina van de opslagkaart heeft een aantal standaardkolommen + een aantal - per referentiecontour verschillende - attributen.

De **identificatiecode** wordt automatisch toegekend. De waarde wordt opgebouwd met de kolom *Tekst* van de instelling *Sectie: Inrichtingen en Item: revnamespaceidentificatie* gevolgd door een punt gevolgd door de naam van de EV-activiteit gevolgd door een underscore gevolgd door de naam van de  referentiecontour gevolgd door een underscore gevolgd door de dnkey van de referentiecontour (tbmilopslag.dnkey). Dus zoiets als NL.IMEV.00002.TankenLPG_Tankzuil_3243

De **beginGeldigheid** slaat hier op de begin geldigheid van de Referentiecontour. Een wijziging op beginGeldigheid wordt niet geaccepteerd indien de datum ExportNaarREV reeds is gevuld. Een beginGeldigheid moet op het moment van export kleiner zijn dan vandaag.
 Indien de referentiecontour voor het eerst wordt geëxporteerd (met een POST, wanneer de exportdatum dus nog leeg is) dan moet deze kleiner of gelijk zijn - dus eerder gestart zijn - dan de beginGeldigheid van de onderliggende EV-contouren (in tbmilopslagevcontouren).

Omgekeerd geldt dus dat de beginGeldigheid bij een POST groter of gelijk moet zijn aan de beginGeldigheid van de bovenliggende EV-Activiteit. Bij een succesvol geaccepteerd wijzigingsbericht (een PUT, wanneer de exportdatum reeds gevuld is), waarbij een of meer wijzigingen op attributen worden doorgegeven, zal de beginGeldigheid automatisch met de datum van de export worden vervangen.

De **eindGeldigheid** slaat hier op de eindgeldigheid van de Referentiecontour. Een wijziging wordt alleen geaccepteerd bij een gevulde begingeldigheidsdatum. De eindGeldigheid moet groter zijn dan de beginGeldigheid. Een eindeGeldigheid mag niet in de toekomst liggen. Indien de datum ExportNaarREv is gevuld en de oude waarde van ddeindGeldiheid was ook gevuld met een waarde kleiner dan de exportdatum, dan wordt de wijziging niet geaccepteerd. Bij een wijziging die wel wordt geaccepteerd zullen alle onderliggende eindGeldigheidsdatums van de EV-contouren (voor zover die voorzien zijn van een gevulde beginGeldigheid) zo nodig worden aangepast naar deze datum.

De **datum laatst gewijzigd** wordt automatisch gevuld met het moment, waarop een van de kolommen een nieuwe waarde krijgt.

De datum **geëxporteerd naar REV** (ddexportnaarREV) wordt automatisch gevuld op het moment dat een gehele set - dus: inrichting (locatie-EVactiviteit) met alle onderliggende objecten (EV-activiteiten, referentie- en EV-contouren) - succesvol is geëxporteerd naar het REV. Eenmaal geëxporteerd betekent dat de referentiecontour ook bestaat in het REV. Dat kan alleen ongedaan worden gemaakt met een gevulde eindeGeldigheid die dan opnieuw geëxporteerd moet worden.

Het **blok wordt verder aangevuld met de attributen** overgenomen uit de definitietabel tbrevrefcontour (zie hierboven) waarbij het vakje *Overnemen* aangevinkt is. Deze attributen moeten een gevulde waarde krijgen alvorens de referentiecontour geëxporteerd kan worden. Het vraagtekenschermknopje toont de omschrijving van het attribuut zoals gedefinieerd in de definitietabel tbrevrefcontour. Deze omschrijving heeft geen invloed op de export.

Het attribuut **geometrie** geeft aan welke type geometrie van toepassing is op de referentiecontour (punt, vlak of lijn). Indien de onderliggende EV-contouren een gevuld attribuut Afstand hebben, dan moet het geotype van de referentiecontour een Punt zijn.

Onder het blok geometrie in het detailscherm van de referentiecontour is in het blok*EV-contouren* een lijstje van gekoppelde EV-contouren (tbmilopslagevcontour-kaarten) te zien. Zie voor de insert hieronder bij TbMilOpslagEvContour (EV-contouren).

### TbMilOpslagEvContour (Ev-contouren)

Rechten: opslagrechten: tbmilrechten.dlcmilinropsvsb).

Er zijn twee manieren om een EV-contour te definiëren bij een referentiecontour. Beiden vanuit het detailscherm van de bovenliggende referentiecontour in het blok*EV-contouren*.

  - Met de insertknop kan een keuze voor een EV-contour gemaakt worden op basis van de *Koppeltabel activiteit/ev-contour* (beheer). De bovenliggende EV-activiteit is dus bepalend voor de mogelijkheden. De contour wordt dan sec - zonder vooraf ingevulde velden- toegevoegd.
  - Met de wizardknop *Haal EvContouren uit de afstandentabel* worden automatisch 1 of meer EV-contouren op basis van de regels in tabel TbREVAfstanden (zie uitleg hierboven beheer) toegevoegd.\\De beginGeldigheid krijgt als waarde de datum van vandaag. Let op: op het moment van export moet deze kleiner zijn dan vandaag

De wizard voegt alleen EV-contourkaarten toe indien deze nog niet bestaan bij de bovenliggende referentiekaart. Dat laatste betekent voor PR-contouren dat OpenWave kijkt naar de combinatie contournaam = PR-contour en het typePlaatsgebondenRisico. Voor de overige soorten EV-contouren checkt OpenWave alleen op de contournaam (dus bij een bepaalde referentiecontour wordt brandaandachtsgebied of explosieaandachtsgebied alleen toegevoegd indien deze nog niet bestaan).

Het blok *Kenmerken EV-contour* op de detailpagina van de EV-contourkaart heeft een aantal standaardkolommen + een aantal - per EV-contour verschillende - attributen.

De **identificatiecode** wordt automatisch toegekend. De waarde wordt opgebouwd met de kolom *Tekst* van de instelling *Sectie: Inrichtingen en Item: revnamespaceidentificatie* gevolgd door een punt gevolgd door de naam van de EV-activiteit gevolgd door een underscore gevolgd door de naam van de referentiecontour gevolgd door een underscore gevolgd door de naam van de EV-contour gevolgd door een underscore en de dnkey van de EV-contour (tbmilopslagevcontour.dnkey). Dus zoiets als NL.IMEV.00002.OpslagMeststof_OpslagReferentie_PRContour_190.

De **beginGeldigheid** slaat hier op de begin geldigheid van de EV-contour. Een wijziging op beginGeldigheid wordt niet geaccepteerd indien de datum ExportNaarREV reeds is gevuld. Indien de EV-contour voor het eerst wordt geëxporteerd (met een POST, wanneer de exportdatum dus nog leeg is) moet de beginGeldigheid groter zijn dan de beginGeldigheid van de bovenliggende Referentiecontour. Bij een succesvol geaccepteerd wijzigingsbericht (een PUT, wanneer de exportdatum reeds gevuld is), waarbij een of meer wijzigingen op attributen worden doorgegeven, zal de beginGeldigheid automatisch met de datum van de export worden vervangen.

De **eindGeldigheid** slaat hier op de eindgeldigheid van de EV-contour. Een wijziging wordt alleen geaccepteerd bij een gevulde begingeldigheidsdatum. De eindGeldigheid moet groter zijn dan de beginGeldigheid. Een eindeGeldigheid mag niet in de toekomst liggen. Indien de datum ExportNaarREv is gevuld en de oude waarde van ddeindGeldiheid was ook gevuld met een waarde kleiner dan de exportdatum, dan wordt de wijziging niet geaccepteerd.

De **datum laatst gewijzigd** wordt automatisch gevuld met het moment, waarop een van de kolommen een nieuwe waarde krijgt.

De datum **geëxporteerd naar REV** (ddexportnaarREV) wordt automatisch gevuld op het moment dat een gehele set - dus: inrichting (locatie-EVactiviteit) met alle onderliggende objecten (EV-activiteiten, referentie- en EV-contouren) - succesvol is geëxporteerd naar het REV. Eenmaal geëxporteerd betekent dat de EV-contour ook bestaat in het REV. Dat kan alleen ongedaan worden gemaakt met een gevulde eindeGeldigheid die dan opnieuw geëxporteerd moet worden.

Het **blok wordt verder aangevuld met de attributen** overgenomen uit de definitietabel tbrevevcontour (zie hierboven) waarbij het vakje *Overnemen* aangevinkt is. Deze attributen (met uitzondering van *afstand*) moeten een gevulde waarde krijgen alvorens de EV-contour geëxporteerd kan worden. Het vraagtekenschermknopje toont de omschrijving van het attribuut zoals gedefinieerd in de definitietabel tbrevevcontour. Deze omschrijving heeft geen invloed op de export.

Het attribuut **geometrie** geeft aan welke type geometrie van toepassing is op de EV-contour (punt of vlak). Indien het attribuut afstand gevuld is, dan is het geotype per definitie Punt. Het betreffende punt waaraan de afstand gelieerd is dat van de bovenliggende referentiecontour!!!!

De puntcoördinaten in het blok *Geometrie;punt Ref.Cont* zijn hier niet muteerbaar en komen uit de bovenliggende referentiecontour.

Bij de export van de Json naar REV redeneert OpenWave qua geometrie en **afstand** als volgt:

  - Indien attribuut afstand is gevuld, dan wordt deze afstand doorgegeven met als referentiepunt het Punt van de bovenliggende referentiecontour.
  - Indien afstand niet gevuld, dan wordt het polygoon van de EV-contourkaart doorgegeven.

Onderaan de detailkaart is de knop *Teken en vervang vlak op kaart* zichtbaar (mits opslagrechten: tbmilrechten.dlcmilinropsedt).

### TbMilBklKwetsbGebLoc (Kwetsbare gebouwen en locaties)

Hoewel er in het IMEV model geen relatie bestaat tussen een kwetsbaar gebouw/locatie en een locatie-Evactiviteit (inrichting) zijn deze in OpenWave wel toegankelijk gemaakt op het inrichtingsportaal via de tegel *REV kwetsbare geb/locaties*.

In OpenWave is een kwetsbaar gebouw/locatie vanuit beheer oogpunt dus gekoppeld aan een inrichting. Niet alle organisaties zullen kwetsbare gebouwen en locaties aanleveren aan het REV via OpenWave. De tegel is daarom onzichtbaar te maken door de instelling *Sectie: REV en Item: Kwetsgebzichtbaar* uit te vinken.

Het inzien, wijzigen en insert van gegevens is verder gekoppeld aan de SBI/MBA/BKL rechten bij een inrichting (tbmilrechten.dlcmilinrsbivsb).

Bij een inrichting kunnen meerdere kwetsbare gebouwen of locaties worden gedefinieerd op basis van *definitietabel Kwetsbare gebouwen/locaties*.

Het gebouw/locatie heeft op de detailpagina een aantal standaardkolommen + een aantal attributen (de attributen zijn voor locatie en gebouw verschillend).

Het blok **Geometrie Vlak** moet gevuld moet zijn: onderaan de detailpagina is hiertoe de knop *Teken vlak op kaart* zichtbaar.

De datum **Datum laatste preview ok** (ddrevpreviewok) wordt alleen gevuld indien de preview export Json, die gestart wordt met de knop achter deze kolom, geen fouten heeft opgeleverd. Indien datum laatste wijziging kleiner is dan deze previewdatum, zou deze kwetsbare gebouw/locatie probleemloos geëxporteerd kunnen worden.

De REV **identificatiecode** van de kwetsbare gebouw/locatie wordt automatisch toegekend. De waarde wordt opgebouwd met de kolom *Tekst* van de instelling *Sectie: Inrichtingen en Item: revnamespaceidentificatie* gevolgd door een punt gevolgd door ofwel KwetsbaarGebouw dan wel KwetsbareLocatie gevolgd door een underscore gevolgd door de dnkey van de kaart in TbMilBklKwetsbGebLoc. Dus zoiets als NL.IMEV.00002.KwetsbareLocatie_5.

De **beginGeldigheid** slaat hier op de begin geldigheid van het gebouw of locatie. Een wijziging op beginGeldigheid wordt niet geaccepteerd indien de datum ExportNaarREV reeds is gevuld. Een beginGeldigheid mag niet in de toekomst liggen.

De **eindGeldigheid** slaat hier op de eindgeldigheid van het gebouw of locatie. Een wijziging wordt alleen geaccepteerd bij een gevulde begingeldigheidsdatum. De eindGeldigheid moet groter zijn dan de beginGeldigheid. Een eindeGeldigheid mag niet in de toekomst liggen. Indien de datum ExportNaarREv is gevuld en de oude waarde van ddeindGeldiheid was ook gevuld met een waarde kleiner dan de exportdatum, dan wordt de wijziging niet geaccepteerd.

De **datum laatst gewijzigd** wordt automatisch gevuld met het moment, waarop een van de kolommen van de kaart in TbMilBklKwetsbGebLoc een nieuwe waarde krijgt. De *datum laatst gewijzigd* is belangrijk voor de automatische geschedulede export naar het REV. De kwetsbare gebouwen en locaties worden opnieuw geëxporteerd indien deze datum groter is dan de datum exportnaarREV.

De datum **geëxporteerd naar REV** (ddexportnaarREV) wordt automatisch gevuld op het moment dat een kwetsbare gebouw/locatie - succesvol is geëxporteerd naar het REV. De geschedulede export naar REV (zie verderop) loopt alle kaarten in TbMilBklKwetsbGebLoc af waarvoor onder meer geldt dat de *datum laatste wijziging set* groter is dan deze datum *geëxporteerd naar REV*.

Eenmaal geëxporteerd betekent dat het gebouw/locatie ook bestaat in het REV. Dat kan alleen ongedaan worden gemaakt met een gevulde eindeGeldigheid die dan opnieuw geëxporteerd moet worden.

Met de schermknop **preview export Json** wordt een gebouw/locatie omgezet naar een JSon exportfile en aangeboden aan het REV ter validatie (validate only) zonder dat het REV de wijzigingen doorzet naar het register.

Endpoint en APIkey en bronhouderscode dienen gevuld te zijn (respectievelijk kolom *Tekst* van *Sectie: REV en Item: AlgemeenEndpoint* en kolom *Tekst* van *Sectie: REV en Item: Apikey* en kolom *Tekst* van *Sectie: REV en Item: Bronhouder*). Bronhouderscode en APIkey worden door Geodan uitgegeven. Bij ontbreken komt een leeg scherm.

OpenWave controleert of (de gevuld aangeleverde) Json-mallen (zie hierboven bij beheer) m.b.t. gebouw/locatie nog compleet gevuld zijn.

De preview controleert zoveel mogelijk op voorhand of het te exporteren gebouw/locatie aan alle voorwaarden voldoet. Bijv.

  - De objecten moeten voldoen aan alle regels met betrekking tot de begin- en eindGeldigheid.
  - De datum laatst gewijzigd moet groter zijn dan de datum geëxporteerd naar REV.
  - Alle objecten moeten een gevulde identificatiecode hebben.
  - De attributen bij elk object moeten alle een gevulde waarde hebben.

Indien een controle faalt wordt dit in tekst op scherm vertoont en gaat er geen bericht naar het REV.

Bij succes wordt de Json file (van die ene kwetsbare gebouw/locatie) naar het REV geëxporteerd. Deze exportfile wordt in het scherm getoond alsmede het retourbericht van het REV.

Retourcode 200 of 201 betekent dat het bericht succesvol geaccepteerd is door de validatieprocedure van het REV. Bij succes wordt *Datum laatste preview ok* (ddrevpreviewok) op de gebouw/locatiekaart automatisch gevuld.

De schermknop **Toon gegevens REV**  is alleen zichtbaar indien de datum *geëxporteerd naar REV* (ddexportnaarREV) gevuld is. Het kwetsbare gebouw/locatie zoals die geregistreerd staat in het REV wordt opgehaald en getoond (als Json) op basis van de REV-identificatiecode.

In het blok **Kenmerken** zijn de attributen overgenomen uit de definitietabel Kwetsbare gebouwen/locaties (zie hierboven) waarbij het vakje Overnemen aangevinkt is. Deze attributen moeten een gevulde waarde krijgen alvorens het gebouw/locatie geëxporteerd kan worden. Het vraagtekenschermknopje toont de omschrijving van het attribuut zoals gedefinieerd in de definitietabel. Deze omschrijving heeft geen invloed op de export.

Het attribuut *geometrie* geeft aan welke type geometrie van toepassing is op het gebouw/locatie (multivlak of vlak). OpenWave ondersteunt voorlopig alleen Vlak.

## Export naar REV

Endpoint en APIkey en bronhouderscode dienen gevuld te zijn (respectievelijk kolom *Tekst* van *Sectie: REV en Item: AlgemeenEndpoint* en kolom *Tekst* van *Sectie: REV en Item: Apikey* en kolom *Tekst* van *Sectie: REV en Item: Bronhouder*). Bronhouderscode en ApiKey worden door Geodan uitgegeven.

De export wordt gescheduled verzorgd door de [Taskscheduler](/docs/instellen_inrichten/taskscheduler). In deze tabel (*beheer: Service centrum-portaal, tegel: Taskscheduler*) moet een kaart aangemaakt worden met als Action: *ExportREV*, aangevinkt, een geplande startdatum/tijd en bijvoorbeeld een ophoging van 1440 minuten (= dagelijks.md).

Wanneer de taak gaat draaien wordt eerst een kaart aangemaakt in tboperationslog met code = ExportREV en begintijd = timestamp en als medewerker het robotaccount dat geïnstalleerd is bij de implementatie van de cronjob (vaak *TASKS*).

De taskscheduler doet eerst een controle of de vorige uitvoer van exportrev al is afgelopen. Dat is het geval indien *Getal1* van de instelling *Operations Item: ExportREV* de waarde 0 heeft. Zo niet dan wordt de task afgesloten met status 2 (niet succesvol afgerond).

Indien de task ExportREV kan worden gestart wordt de status in de taskcheduler kaart op 1 gezet (ben bezig…) en krijgt *Getal1* van de instelling *Operations Item: ExportREV* de waarde 1.

De taskscheduler voert de action ExportREV in twee loops uit:

  - Loop **Kwetsbare gebouwen en locaties**: de rijen uit tbmilbklkwetsbgebloc waarvoor geldt:
    - ddBeginGeldigheid niet leeg en kleiner dan vandaag
    - EN ddexportnaarREV is leeg OF dddatumlaatstewijziging groter dan ddexportnaarrev
    - EN ddeindGeldigheid is leeg of ddeindGeldigheid groter dan ddexportnaarrev
  - Loop **Locatie-Evactiviteiten**: de rijen uit tbmilinrichtingen waarvoor geldt:
    - Ddbegingeldigheid is niet leeg en kleiner dan vandaag
    - EN ddeindGeldigheid is leeg of ddeindGeldigheid groter dan ddexportnaarrev
    - EN ddexportnaarrev is leeg OF vwfrmmilinrichtingen.ddmaxsetlaatstgewijzigd groter dan ddexportnaarrev
    - EN dvlocatieevactiviteit is niet leeg
    - EN de kolom **Klaargezet voor Export** (ddmagexport) moet gevuld zijn (zie hierboven).

Omdat voor elke wijziging altijd de gehele set vanaf de locatie-EVactiviteit moet worden aangeleverd is binnen de loop van inrichtingen een subloop EV-activiteiten: tbmilbklactiviteiten:

  - ddBeginGeldigheid niet leeg en kleiner of gelijk aan vandaag
  - EN ddeindGeldigheid is null of ddeindGeldigheid groter dan ddexportnaarrev
  - EN de activiteitnaam is ongelijk aan *ActiviteitRestcategorie*

En binnen de loop van tbmilbklactiviteiteneen subloop referentiecontouren: tbmilopslag:

  - ddBeginGeldigheid niet leeg en kleiner of gelijk aan vandaag
  - EN ddeindGeldigheid is null of ddeindGeldigheid groter dan ddexportnaarrev

En binnen de loop van tbmilopslag een subloop EV-contouren: tbmilopslagevcontour:

  - ddBeginGeldigheid niet leeg en kleiner of gelijk aan vandaag
  - EN ddeindGeldigheid is null of ddeindGeldigheid groter dan ddexportnaarrev

Bij elke te evalueren kaart wordt dezelfde controle uitgevoerd als plaatsvindt bij de hierboven beschreven preview-schermknop op de detailschermen inrichtingen en kwetsbare gebouwen/locaties. Indien probleem dan wordt dit in de operationslog gemeld en wordt de volgende kaart bekeken.

Indien de instelling *Sectie: REV en Item: ExportTest* NIET aangevinkt is dan

  - wordt elke kaart die voldoet aan de criteria omgezet in een Json-file (bij inrichtingen gaat het dus steeds om de hele set inrichting + bijbehorende activiteiten + referentie en EV-contouren) en geëxporteerd naar het endpoint. Een nieuwe set met een POST bericht, wijzigingen op een bestaande set met een PUT bericht
  - Indien *Sectie: OWB,  Item: MessageLog* aangevinkt is EN de instelling *Sectie: REV, Item: Messagelog* ook aangevinkt is, dan wordt elke geëxporteerde Jsonfile + antwoord opgenomen in de Messagelog.
  - Indien succesvol opgenomen in REV (resultode 200 of 201) dan worden van de betreffende kaarten in OpenWave
    - de datum exportnaarREV gevuld met timestamp
    - de beginGeldigheid van alle gewijzigde objecten (alle kaarten waarvan de ddlaastgewijzigd groter is dan de (vorige) exportnaarrevdatum) op vandaag gezet.

Exporttest aan of uit en succes of geen succes: elke kaart krijgt een evaluatie-regel in operationslog. Dus indien de instelling *Sectie: REV, Item: ExportTest* WEL aangevinkt is, wordt alleen de operationslog gevuld, en dus geen export naar REV en geen wijzigingen in de export- en geldigheidsdatums.

Zijn alle kaarten van beide loops doorlopen, dan wordt de status in de taskcheduler kaart op 0 gezet (succesvol uitgevoerd) en en krijgt *Getal1* van de instelling *Sectie: Operations, Item: ExportREV* de waarde 0.

