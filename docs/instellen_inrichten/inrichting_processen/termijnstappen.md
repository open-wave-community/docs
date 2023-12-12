# Termijnstappen

Per proces kunnen een of meer termijnbewakingsstappen worden gedefinieerd. Termijnstappen zijn de stappen die in het termijnbewakingsscherm bij een zaak een streefdatum (ook wel deadline genoemd) hebben en een afgehandeld datum die ingevuld kan worden. Die deadlines worden berekend op basis van wat hier bij een termijnbewakingsstap wordt gedefinieerd. Dat gaat op de volgende wijze:

Bij termijnstap A wordt aangegeven dat de volgende termijnstap de stap B is, waarbij de deadline van stap B X dagen verder is dan de deadline van A. Het verschil in dagen tussen deadline van A en die van B geeft dus de termijn aan waarbinnen stap B moet zijn afgehandeld.

Een deadline die binnen nu (systeemdatum) en een Y aantal dagen dreigt te verlopen, komt op de takenlijst van de verantwoordelijke medewerker.

Het aangeven van de volgende stap en de termijnen kan in de praktijk ingewikkelder zijn dan hierboven beschreven. De volgende variaties zijn bijvoorbeeld mogelijk:

- Bij termijnstap A wordt aangegeven dat de volgende termijnstap de stap B is, waarbij de deadline van stap B X dagen verder is dan de ingevulde afgehandeld datum van A. Het verschil in dagen tussen afgehandeld A en deadline B geeft dan de termijn aan waarbinnen stap B moet zijn afgehandeld.
- Bij termijnstap A wordt aangegeven dat de volgende termijnstap:
  - de stap B is indien aanvinkstap C aangevinkt is, waarbij de deadline van stap B X dagen verder is dan de deadline van A;
  - de stap D is indien aanvinkstap C niet is aangevinkt, waarbij de deadline van stap D X dagen verder is dan de ingevulde afgehandeld datum van A.

Door termijnstappen te relateren aan afvinkstappen kunnen termijnbewakingsregels bij een zaak in de ene situatie wel ingevuld worden en in de andere situatie niet (zij krijgen in dat laatste geval een afwijkende kleur en de streefdatums worden onzichtbaar).

## Bijzondere stapdefinities StartRegel en Tussenregel

Er kunnen twee soorten termijnstappen worden gedefinieerd die niet aan de voorkant terug te vinden zijn:

- Een stap met de naam _Startregel_ waarbij volgnummer de waarde 0 heeft, wordt door OpenWave niet opgenomen bij de uit te voeren processtappen, maar enkel onder water gebruikt om twee processen aan elkaar te koppelen: zie hieronder bij uitleg Volgnummer = 0.
- Een stap met de naam _Tussenregel_ wordt wel opgenomen bij de uit te voeren processtappen aan de voorkant, maar is altijd onzichtbaar. Deze stap krijgt bij de aanroep van de _wizard sluitzaak_ automatisch als afhandeldatum de streefdatum van deze tussenstap. De Tussenregel wordt ook niet opgenomen in de vwfrmeersteprocesstapperzaak en ook niet in de vwfrmeerstestapperproces, zodat er geen openstaande taak op deze stap kan staan.

Toepassing voor de _Tussenregel_ is de situatie waarbij in een proces bijv. ontvankelijkheid een vork (A en B) is gedefinieerd:

- In A wordt vervolgproces X gekozen
- In B wordt vervolgproces Y gekozen

Beide vorken A en B verwijzen naar dezelfde eindstap: bijv. Einde Ontvankelijkheid. Door deze naam te wijzigen in Tussenregel wordt deze laatste stap onzichtbaar en komt voor de gebruiker direct de eerste stap van de gekozen vervolgproces in beeld.

## Kolommen uit blok termijnstap

#### Naam

De naam zoals die voor de gebruiker zichtbaar is.

**Volgnummer** Het volgnummer is bepalend voor de volgorde waarin de termijnstappen hier, maar ook in het termijnbewakingsscherm bij een zaak zichtbaar zijn.

> [!WARNING] **Let op:** volgnummers mogen niet groter zijn dan 999.

Bij de definitie van een processtap wordt altijd verwezen naar een volgende stap die bij hetzelfde proces hoort met een termijn. Dat gebeurt door aangeven van dit volgnummer. Zie hieronder bij lemma _volgende stap_.

**\*Volgnummer met waarde 0 (startregel**)\*

De eerste stap van elk proces is de stap met volgnummer 0 (met als naam: startregel). Deze startregel zelf zal in het gebruik nooit zichtbaar zijn. De startregel wordt gebruikt om de streefdatum en de afgehandeld datum van de allereerste termijnstap van een proces te berekenen. Immers: de termijnen van de vervolgstappen worden op basis van de eerste streefdatum en/of afgehandeld datum berekend. Die datum is de aanvraagdatum, datum constatering of ontvangstdatum van de zaak. Deze datum wordt dus zowel als streefdatum en als afgehandeld datum door het programma ingevuld bij de allereerste stap.

Als een proces als tweede of derde proces aan een zaak wordt gekoppeld, moet van de eerste stap hiervan ook de streefdatum worden ingevuld. Dit kan natuurlijk niet de oorspronkelijke ontvangstdatum zijn. Het is de bedoeling dat de eerste streefdatum van het vervolgproces wordt berekend op basis van de laatste streefdatum van het voorgaande proces. Om dat te kunnen bewerkstelligen worden de termijnregels met volgnummer 0 als dergelijke verbindingsregels beschouwd. Zij worden niet overgenomen, maar alleen gebruikt om de termijn naar de volgende regel te berekenen. De omschrijving is niet belangrijk, maar wij raden aan hiervoor de term startregel te gebruiken.

#### Vervaldatum

Een gevulde vervaldatum die groter is dan de systeemdatum heeft tot gevolg dat de termijnstap niet zichtbaar is en dat de termijnstap niet zal wordt aangemaakt bij het koppelen van een vergunning aan de proces waar deze stap een onderdeel van uitmaakt. **Opschortende werkingstermijn wordt bij deze stap opgeteld**

De berekende opschortende werking kan dus - naast de optelling bij de fatale datum in een omgevingszaak of APV/Overige - OOK bij een termijnstap worden opgeteld, maar dit hoeft niet. Zie [Ontvankelijkheid en opschortende werking](/instellen_inrichten/inrichting_processen/opschortende_werking.md).

#### Berekende streefdatum door gebruiker aan te passen

Wanneer dit vakje is aangevinkt kan in het termijnbewakingsscherm voor deze stap de termijn naar de volgende stap worden aangepast. Dit geldt in dat geval voor elke medewerker die wijzigrechten heeft in de termijnbewaking. Dit kan het geval zijn bij procesflows waarin geen sprake is van wettelijke termijnen, maar waarbij de termijn naar een volgende stap afhankelijk is van omstandigheden.

#### Omschrijving/naam van stap door gebruiker aanpasbaar?

Wanneer dit vakje is aangevinkt kan in het (detailscherm van het) termijnbewakingsscherm deze omschrijving door de gebruiker aangepast.

**Streefdatum verandert niet mee met invulling afhandeldatums** Dit wil zeggen dat bij het ophalen van een proces eenmalig de deadlines berekend worden a.d.h.v. de startdatum van de zaak (of datum constatering bij handhaving) of aan de hand van de laatste datum van het voorafgaande proces in geval van stapeling. Daarna kunnen zij niet meer gewijzigd worden: ze zijn dus onafhankelijk van de ingevulde afgehandeld datums of voorliggende deadlines.

Daarop gelden uitzonderingen; de deadlines kunnen toch veranderen bij:

- Aanhouden
- Opschortende werking bij ontvankelijkheidstoets, zie hieronder lemma _Opschortende werking_ (en overige opschortingen o.g.v. art. 4.15 Awb).

**De stap wordt bij lege afhandeldatum opgenomen in takenlijst (mijn procestaken)**

In de takenlijst komt een regel als de streefdatum van een termijnbewakingsstap verlopen is of dreigt te verlopen.

**Deze stap is de ontvangst van de aanvullende gegevens** Zie hiervoor ook: Ontvankelijkheid en opschortende werking ([Ontvankelijkheid en opschortende werking](/instellen_inrichten/inrichting_processen/opschortende_werking.md)). Indien dit vakje is aangevinkt dan heeft dat de volgende betekenis.

De termijnstap wordt geïnterpreteerd als de stap waarbij in het kader van de ontvankelijkheidstoetsing op uitnodiging aanvullende gegevens worden aangeleverd. Het programma neemt aan dat de voorgaande stap dan de uitnodiging tot het aanleveren van die aanvullende gegevens is. Het programma kan dan een opschortende werking gaan berekenen door het aantal dagen tussen de afhandeldatum van deze termijnstap (de aanlevering) minus de afhandeldatum van de voorgaande stap (de uitnodiging) te bepalen.

Wanneer de daadwerkelijke indiening echter plaatsvindt na de afgesproken datum dat ze ingediend zouden moeten zijn, dan geldt als opschortende termijn het aantal dagen tussen die afgesproken datum en de uitnodiging. De opschortende werking van X dagen wordt:

- Opgeteld bij de deadline van de termijnstap verderop in de proces waar aangevinkt is dat de opschortende werking van de aanvullende gegevens verwerkt moet worden. Dit is alleen van toepassing als er een eindstap is die vaststaat na eerste berekening.
- Opgeteld bij de fatale datum in het basis editscherm van de zaak (indien als zichtbaar gedefinieerd: zie beheertegels Zaaktypen omgeving, overige etc.).

> [!WARNING] **Let op:** deze functionaliteit wordt alleen ondersteund bij Omgevingsvergunningen, Overige vergunningen, Bouw/sloop vergunningen en Milieuvergunningen.

#### Streefdatum van deze stap blijft kleiner dan fatale datum

Als deze eigenschap is aangevinkt, dan is de streefdatum van deze stap altijd < of gelijk aan de fatale datum van de bovenliggende zaak.

#### Afhandeldatum niet rechtstreeks in te vullen (maar via action of invoerkolom)

Als deze stap is aangevinkt zal de afgehandeld datum van deze processtap **niet** handmatig door de inlogger kunnen worden aangepast. Het vullen geschiedt bijv. door de uitvoering van een action of door het vullen van een extra invoerkolom (zie hieronder bij blok _Action_ en blok _Extra invoerkolommen_). Op het detailscherm van de stap wordt deze eventuele blokkade overruled door een gebruiker die rechten heeft om procestappen te verwijderen.

### Default behandelaar of team

Aan elke termijnstap is een default behandelaar of een default team toe te kennen. Deze medewerker/de medewerkers die vallen onder het team worden de verantwoordelijken voor het afhandelen van de betreffende processtap. De takenlijsten gebaseerd op openstaande processtappen kunnen of op individuele verantwoordelijke of op team worden ingericht. Zie bijvoorbeeld tegel _Mijn Openstaande Processtappen_ op het Openingsportaal.

Indien de instelling _Sectie: Termijnbewaking en Item: Teamzichtbaar_ is aangevinkt dan is voor de gebruiker in het lijst- en detailscherm van een processtap zichtbaar aan welk team deze is toegekend. Indien de instelling _Sectie: Termijnbewaking en Item: Voorwiezichtbaar_ is aangevinkt dan is in het lijst- en detailscherm van een processtap zichtbaar aan welke persoon deze is toegekend. Indien er geen specifieke default medewerker bij een processtap is aangewezen en ook geen team, dan blijft de dossierbehandelaar (de actieve in behandeling bij) de eerst verantwoordelijke voor het afhandelen van de processtap.

### Hyperlink

Bijvoorbeeld <https://www.open-wave.nl/>. Let op dat een ampersand-teken (&) in de URL geschreven moet worden als &amp; (5 karakters).

### Blok Volgende stap

**Volgende stap** (nummer, termijn, eenheid) In dit kader kunnen de kolommen die gaan over de volgende termijnstap worden ingevoerd wanneer de kolom _tenzij afvinkstap met volgnr_ van stap leeg is.

Het volgnummer van die volgende stap moet hier worden aangegeven en daarbij hoe de berekening van de deadline van die volgende stap moet plaatsvinden. Dat kan door het aangeven van de termijn tussen de onderhavige stap en de volgende stap. Die termijn kan worden aangegeven (keuzelijst eenheden) in dagen, arbeidsdagen, weken, maanden, kwartalen of jaren. Bij arbeidsdagen worden alleen doordeweekse dagen geteld. OpenWave gaat er vanuit dat er minimaal één dag verschil ligt tussen de opeenvolgende termijnstappen.

**Tenzij afvinkstap met volgnr** (nummer, termijn, dan afgehandeld, dan deadline) In dit kader kunnen de kolommen die gaan over de volgende termijnstap worden ingevoerd die gebruikt worden wanneer:

- De kolom _afhankelijk van stap_ hierboven in de beheerapplicatie is ingevuld en
- de afvinkstap aangevinkt wordt.

Het volgnummer van die volgende stap moet hier worden aangegeven en daarbij hoe de berekening van de deadline van die volgende stap moet plaatsvinden. Dat kan door het aangeven van de termijn tussen de onderhavige stap en de volgende stap. Die termijn kan worden aangegeven (keuzelijst) in dagen, arbeidsdagen, weken, maanden, kwartalen of jaren. Bij arbeidsdagen worden alleen doordeweekse dagen geteld.

Indien er geen volgende stap is (laatste termijnstap van een proces) moet in ieder geval de kolom _volgende stap_ leeg blijven.

Wanneer n aantal arbeidsdagen wordt opgeteld bij een datum, dan gebeurt dat stapje voor stapje met een dag tegelijk. Indien de uitkomst van zo'n stapje een zaterdag of zondag oplevert, dan wordt een extra stapje gedaan.

De deadline van de volgende stap kan nu berekend worden door de termijn op te tellen bij de afgehandeld datum of bij de deadline van de onderhavige stap.

Hierin zijn drie mogelijkheden aan te geven:

- streefdatum vorige stap. Met deze keuze geldt altijd de streefdatum van de onderhavige stap als als uitgangspunt voor de berekening van de streefdatum van de nieuwe stap.
- afhandeldatum vorige stap. Indien deze keuze is aangevinkt wordt altijd de afgehandelddatum van de onderhavige stap genomen als uitgangspunt voor de berekening van de streefdatum van de nieuwe stap. Ook als deze afgehandeld-datum groter is dan de streefdatum.
- minimum afgehandeld/streefdatum. Dit betekent dat de termijn om de streefdatum van de volgende stap te berekenen wordt opgeteld bij het minimum van de afgehandeld-datum en streefdatum van de onderhavige stap. Dus indien de afgehandeld-datum groter is dan de streefdatum geldt de streefdatum als uitgangspunt.

In alle gevallen geldt dat als de afgehandeld datum nog leeg is dat dan de streefdatum als uitgangsdatum wordt genomen.

### Blok Action

Aan een processtap kan een action worden toegevoegd. Dat heeft tot gevolg dat er op het detailscherm van de betreffende processtap bij het afhandelen van de zaak een blok action zichtbaar wordt met het hier te definiëren label en een knop om de action uit te voeren. Tevens wordt er een uitvoerbare knop zichtbaar op het lijstscherm van de processtappen om de actie uit te voeren.

Bij een aantal actions is het mogelijk deze zo te parameteriseren dat met het uitvoeren van de action ook de afgehandeld datum van de betreffende stap wordt gevuld. De knop die de action triggert is alleen enabled bij een lege afgehandeld datum. Een aantal voorbeelden geredeneerd vanuit een proces bij een omgevingszaak: Let goed op de komma's en puntkomma's. Luistert nauw. Zie verdere documentatie over actions: [Actions](/instellen_inrichten/actions.md).

### Automatisch creëren van document op basis van specifiek sjabloon zonder vullen afgehandeld datum van stap

De wizard _maakDocument_ wordt geopend met de restrictie dat de gebruiker geen keuze uit de sjablonen heeft. Het sjabloon wordt in de actionaanroep al meegegeven. `startWizard(maakDocument,1234,tbdocumenten;;tbomgvergunning;%keyparent%,W)`

- _maakDocument_ is de naam van de wizard die aangeroepen worden voor het creëren van een document
- _1234_ moet hierbij in de action-definitie vervangen worden met een echte dnkey van het bedoelde sjabloon (uit tbdocumenten)
- _tbdocumenten_ is de bestandnaam van de sjablonen waar 1234 een dnkey van is
- _tbomgvergunning_ wil zeggen dat het creëren van het sjabloon wordt geinitialiseerd vanuit tbomgvergunningen (kan ook uit tbhandhavingen, tbinfoaanvragen, tbovvergunningen, tbhorecavergunningen, tbmilvergunningen, tbinspecties, tbinspbezoeken en tbmilinrichtingen)
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de initiërende tabel
- _W_ staat voor de module waarvandaan de wizard wordt aangeroepen (W (tbomgvergunning), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen of H (tbhandhavingen of V (inrichtingen)).

#### Automatisch creëren van document op basis van specifiek sjabloon MET vullen afgehandeld datum van stap

`startWizard(maakDocument,1234,tbdocumenten;;tbomgvergunning;%keyparent%,W;%keypointer%)`

- %keypointer% wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen.

#### Automatisch creëren van document op basis van specifiek sjabloon op grond van query MET vullen afgehandeld datum van stap

`startWizard(maakDocument,%query(docsjabloonperzaaktype,%keyparent%)%,tbdocumenten;;tbomgvergunning;%keyparent%,W;%keypointer%)`

- %keypointer% wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen.
- De query met de naam docsjabloonperzaaktype is een voorbeeld en bestaat niet. Belangrijk is dat de uitkomst van de query één dnkey van een documentsjabloon teruggeeft.

#### Automatisch starten van maakDocument-wizard op basis van specifieke documentsoort zonder vullen afgehandeld datum van stap

De wizard wordt geopend met de restrictie dat de gebruiker alleen uit de sjablonen van een bepaalde groep (tbdocumentsoorten) kan kiezen. `startWizard(maakDocument,1234,tbdocumentsoorten;;tbomgvergunning;%keyparent%,W)`

- _maakDocument_ is de naam van de wizard die aangeroepen worden voor het creëren van een document
- _1234_ moet hierbij in de action-definitie vervangen worden met een echte dnkey van de bedoelde groep (uit tbdocumentsoorten). De gebruiker kan vervolgens alleen een sjabloon uit deze groep kiezen
- _tbdocumentsoorten_ is de bestandnaam van de documentgroepen waar 1234 een dnkey van is
- _tbomgvergunning_ wil zeggen dat het creëren van het te kiezen document wordt geinitialiseerd vanuit tbomgvergunningen (kan ook uit tbhandhavingen, tbinfoaanvragen, tbovvergunningen, tbhorecavergunningen, tbmilvergunningen, tbinspecties, tbinspbezoeken en tbmilinrichtingen)
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de initiërende tabel
- _W_ staat voor de module waarvandaan de wizard wordt aangeroepen (W (tbomgvergunning), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen of H (tbhandhavingen of V (inrichtingen)).

#### Automatisch starten van maakdocument-wizard op basis van specifieke documentsoort MET vullen afgehandeld datum van stap

`startWizard(maakDocument,1234,tbdocumentsoorten;;tbomgvergunning;%keyparent%,W;%keypointer%)`

- %keypointer% wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen.

#### Automatisch starten van de volledige maakDocument-wizard ZONDER vullen afgehandeld datum van stap

De wizard wordt geopend zonder restrictie, waarbij de gebruiker eerst een keuze dient te maken uit de groepen (tbdocumentsoorten) en vervolgens uit de daarbij behorende sjablonen. _startWizard(maakDocument,%keyparent%,tbomgvergunning,W)_

- _maakDocument_ is de naam van de wizard die aangeroepen worden voor het creëren van een document
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de initiërende tabel (in dit voorbeeld de dnkey uit tbomgvergunning)
- _tbomgvergunning_ wil zeggen dat het creëren van het te kiezen document wordt geinitialiseerd vanuit tbomgvergunningen (kan ook uit tbhandhavingen, tbinfoaanvragen, tbovvergunningen, tbhorecavergunningen, tbmilvergunningen, tbinspecties, tbinspbezoeken en tbmilinrichtingen)
- _W_ staat voor de module waarvandaan de wizard wordt aangeroepen (W (tbomgvergunning), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen of H (tbhandhavingen of V (inrichtingen)).

#### Automatisch starten van de volledige maakDocument-wizard MET vullen afgehandeld datum van stap

`startWizard(maakDocument,%keyparent%,tbomgvergunning,W;%keypointer%)`

- %keypointer% wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen.

#### Automatisch kiezen vervolgproces zonder vullen van afgehandeld datum van stap

`startWizard(maaknieuwproces,%keyparent%,W)`

- maaNieuwProces is de naam van de wizard die aangeroepen wordt voor het invoegen van nieuwe processtappen
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _W_ staat voor de module waarvandaan de wizard wordt aangeroepen (W (tbomgvergunning), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen of H (tbhandhavingen)).

#### Automatisch kiezen vervolgproces met vullen van afgehandeld datum van stap

`startWizard(maaknieuwproces,%keyparent%,W,%keypointer%)`

- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen.

**Automatisch invoegen **vastgesteld** vervolgproces **met** vullen van afgehandeld datum van stap**

`startWizard(maaknieuwproces,%keyparent%,W;2345,%keypointer%)`.De _2345_ moet hierbij in de action-definitie vervangen worden met een echte dnkey van een proces (tbprocedures) waarvan de stappen moeten worden ingevoegd.

**Automatisch ** kiezen** vervolgzaak op dezelfde locatie **zonder** vullen van afgehandeld datum van stap**

`startwizard(maaknieuwezaak,,W,%keyparent%)`

- _maakNieuweZaak_ is de naam van de aan te roepen wizard die een nieuwe zaak aanmaakt
- _W_ staat voor de module waarvandaan de wizard wordt aangeroepen (W (tbomgvergunning), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen of H (tbhandhavingen))
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat, want van daaruit ga je gegevens als locatie en contactpersonen kopiëren).

**Automatisch **kiezen** vervolgzaak op dezelfde locatie **met** vullen van afgehandeld datum van stap**

_startwizard(maaknieuwezaak,,W;%keypointer%,%keyparent%)_

- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen.

**Automatisch aanmaken **vastgestelde** vervolgzaak op dezelfde locatie **met** vullen van afgehandeld datum van stap**

`startwizard(maaknieuwezaak,,W;%keypointer%,%keyparent%;H3456)`

- De _H_ geeft aan in welke module de nieuwe zaak gemaakt moet worden. Op de plaats van de H kunnen ook de moduleletters W (tbomgvergunning), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt.
- _3456_ (direct achter deze moduleletter) staat voor een dnkey die verwijst naar een zaaktype bij de moduleletter. Dus indien moduleletter =
  - W dan een dnkey uit tbsoortomgverg
  - O dan een dvcode uit tbsoortovverg
  - C dan een dnkey uit tbsoorthorverg
  - E dan een dnkey uit tbsoortmilverg
  - I dan een dnkey uit tbsoortinfoaanvraag.

**Automatisch sluiten van bovenliggende zaak op afhandel/besluitdatum **zonder**vullen van afgehandeld datum van stap**

`startwizard(sluitZaak,%keyparent%,W,ddbesluitdatum)`

- _sluitZaak_ is de naam van de wizard die een zaak van een resultaat en afhandeldatum voorziet
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _W_ geeft aan in welke module de zaak wordt gesloten. Op de plaats van de W kunnen ook de moduleletters W (tbomgvergunning), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen), H (tbhandhavingen) of E (tbmilvergunningen) worden gebruikt \*_ddbesluitdatum_ is de kolomnaam van het einddatum-veld in de module. Wanneer module =\* W of O of C of E dan moet hier staan ddbesluitdatum
- H dan moet hier staan ddeinddatum
- I dan moet hier staan ddafgehandeld.

**Automatisch sluiten van bovenliggende zaak op afhandel/besluitdatum **met** vullen van afgehandeld datum van stap**

`startwizard(sluitZaak,%keyparent%,W;%keypointer%,ddbesluitdatum)`

- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat).
- _W_ geeft aan in welke module de zaak wordt ingetrokken. Op de plaats van de W (tbomgvergunning) kunnen ook de moduleletters H (tbhandhavngen), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt.

**Automatisch vullen van intrekkingsdatum van bovenliggende zaak **zonder** vullen van afgehandeld datum van stap**

`startwizard(sluitZaak,%keyparent%,W,ddingetrokken)`

- _sluitZaak_ is de naam van de wizard die een zaak van een intrekkingsdatum voorziet
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _W_ geeft aan in welke module de zaak wordt ingetrokken. Op de plaats van de W (tbomgvergunning) kunnen ook de moduleletters H (tbhandhavngen), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt \* _ddingetrokken_ is de kolomnaam van het intrekkingsdatum-veld in alle modules.

**Automatisch vullen van intrekkingsdatum van bovenliggende zaak **met** vullen van afgehandeld datum van stap**

`startwizard(sluitZaak,%keyparent%,W;%keypointer%,ddingetrokken)`

- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen
- _W_ geeft aan in welke module de zaak wordt ingetrokken. Op de plaats van de W (tbomgvergunning) kunnen ook de moduleletters H (tbhandhavngen), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt.

**Automatisch aanroep wizard insertOpschorten **met** vullen van afgehandeld datum van stap**

`startwizard(insertOpschorten,%keyparent%,W,%keypointer%)`

- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen
- _W_ geeft aan in welke module de zaak wordt opgeschort. Op de plaats van de W (tbomgvergunning) kunnen ook de moduleletters H (tbhandhavingen), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt.

**Automatisch aanroep wizard insertAdvies **met** restrictie uit de adviesinstanties beginnend met een 2 en met vullen van afgehandeld datum van stap**

`startWizard(insertAdvies,%keyparent%,W,2;%keypointer%)`

- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen
- _W_ geeft aan in welke module het advies wordt aangemaakt. Op de plaats van de W (tbomgvergunning) kunnen ook de moduleletters H (tbhandhavingen), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt
- _2_ geeft hier aan de de gebruiker kan kiezen uit de adviesinstanties (voor de betreffende module) waarvan de dvcode begint met een 2.

**Automatisch aanroep wizard insertAdvies **zonder** extra restrictie adviesinstanties**met**vullen van afgehandeld datum van stap**

`startWizard(insertAdvies,%keyparent%,W,;%keypointer%)`

- _%keyparent%_ wordt on the fly automatisch vervangen m
- et de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen
- _W_ geeft aan in welke module het advies wordt aangemaakt. Op de plaats van de W (tbomgvergunning) kunnen ook de moduleletters H (tbhandhavingen), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt.

**Automatisch aanroep wizard insertAdvies **met** restrictie adviesinstanties beginnend met Welz **zonder** vullen van afgehandeld datum van stap**

`startWizard(insertAdvies,%keyparent%,W,Welz)`

- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _W_ geeft aan in welke module het advies wordt aangemaakt. Op de plaats van de W (tbomgvergunning) kunnen ook de moduleletters H (tbhandhavingen), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt
- _Welz_ geeft hier aan de de gebruiker kan kiezen uit de adviesinstanties (voor de betreffende module) waarvan de dvcode begint met een Welz.

**Automatisch aanroep wizard insertAdvies **zonder** extra restrictie adviesinstanties en **zonder** vullen van afgehandeld datum van stap**

`startWizard(insertAdvies,%keyparent%,W)`

- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _W_ geeft aan in welke module het advies wordt aangemaakt. Op de plaats van de W (tbomgvergunning) kunnen ook de moduleletters H (tbhandhavingen), O (tbovvergunningen), I (tbinfoaanvragen), C (tbhorecavergunningen) of E (tbmilvergunningen) worden gebruikt.

**Automatisch aanroep wizard actualiseerStatusinZaakSystem **met** vullen van afgehandeld datum van stap**

`startWizard(actualiseerStatusinZaaksysteem,%keyparent%,W;tbomgvergunning;ddbesluitdatum;%keypointer%,StatusAfgesloten)`

- Door deze wizard aan te roepen wordt het _actualiseerStatusinZaakSystem_ bericht verstuurd naar het DMS. In plaats van _StatusAfgesloten_ kan tevens _StatusIngetrokken_ of _StatusGeblokkeerd_ verstuurd worden
- Bij het aanroepen van deze wizard wordt de eerder ingevulde _ddbesluitdatum_, _ddingetrokken_ of _ddblokkering_ meegestuurd
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen.

**Automatisch aanroep wizard StuurDSOOntvangstbevestiging **zonder** vullen van afgehandeld datum van stap**

`startWizard(StuurDSOOntvangstbevestiging,%keyparent%,tbomgvergunning)`

- Door deze wizard aan te roepen wordt de mail _DSO ontvangstbevestiging initieel_ verstuurd naar de gemachtigde en/of aanvrager. Deze actie is alleen te gebruiken bij DSO zaken (tbomgvergunning.dlisdso is T). Na uitvoeren van de actie zal in het detailscherm van de omgevingszaak bij het blok _DSO_ de verstuurdatum gevuld zijn. Voor gehele informatie over werking van DSO ontvangstbevestiging sturen zie [DSO ontvangstbevestiging](/probleemoplossing/programmablokken/dso_ontvangstbevestiging.md)
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)

**Automatisch aanroep wizard StuurDSOOntvangstbevestiging **met** vullen van afgehandeld datum van stap**

`startWizard(StuurDSOOntvangstbevestiging,%keyparent%,tbomgvergunning,%keypointer%)`

- Door deze wizard aan te roepen wordt de mail _DSO ontvangstbevestiging initieel_ verstuurd naar de gemachtigde en/of aanvrager. Deze actie is alleen te gebruiken bij DSO zaken (tbomgvergunning.dlisdso is T). Na uitvoeren van de actie zal in het detailscherm van de omgevingszaak bij het blok _DSO_ de verstuurdatum gevuld zijn. Voor gehele informatie over werking van DSO ontvangstbevestiging sturen zie [DSO ontvangstbevestiging](/probleemoplossing/programmablokken/dso_ontvangstbevestiging.md)
- _%keyparent%_ wordt on the fly automatisch vervangen met de dnkey van de kaart uit de hoofdzaak van de module (dus de dnkey van de zaak waar je op staat)
- _%keypointer%_ wordt on the fly automatisch vervangen met de dnkey van de stap (termijnbewstappen) teneinde op de juiste plek de afhandeldatum te kunnen vullen.

### Hoe werkt action aan de voorkant in tbtermijnbewstappen?

Aan de voorkant op het detailscherm van een termijnbewaking- c.q. processtap is de action bij de wizardknop in blok _Action_ standaard als volgt gedefinieerd in het detailscherm (in de mddc_geefprocesdetail.xml):

`%query(termijnstappen_mddc_getdvaction,%keypointer%)%`. Dit is een systeemquery die door OpenWave wordt beheerd. OpenWave evalueert deze query. Deze query vervangt de action die bij de aanmaak van de termijnstappen overgenomen is vanuit tbprocitems (in de kolom dvaction) bij de betreffende termijnstap waarbij de variabelen %keypointer% en %keyparent% worden vervangen met hun echte waardes.

**Voor evaluatie bijvoorbeeld:**
`startWizard(maakDocument,6578,tbdocumenten;;tbomgvergunning;%keyparent%,W)`

Na evaluatie: `startWizard(maakDocument,6578,tbdocumenten;;tbomgvergunning;85842,W)`

en vervolgens wordt de wizard gestart waarbij in dit voorbeeld een brief op grond van documentsjabloon met dnkey 6578 wordt gemaakt. Wanneer in de action na evaluatie nog een query aanwezig, dan wordt deze recursief alsnog geëvalueerd.
Bijvoorbeeld na eerste evaluatie: startWizard(maakDocument,%query(docsjabloonperzaaktype,%keyparent%)%,tbdocumenten;;tbomgvergunning;%keyparent%,W)

Dan na tweede evaluatie: startWizard(maakDocument,8890,tbdocumenten;;tbomgvergunning;85842,W)

### Blok extra Invoerkolommen

Aan een processtap kunnen één of meer kolommen worden toegevoegd waar de gebruiker bij het afhandelen van de stap waardes aan kan toekennen. Er zijn 5 soorten extra kolommen:

- **Datum**. Indien aangevinkt dan verschijnt op het detailscherm van de termijnbewakingsstap een datum-editbox onder het hier ingevulde label. De kolomnaam in tbtermijnbewstappen waar de ingevulde waarde wordt opgeslagen is ddinvoerdatum
- **Integer**. Indien aangevinkt dan verschijnt op het detailscherm van de termijnbewakingsstap een integer-editbox (geheel getal) onder het hier ingevulde label. De kolomnaam in tbtermijnbewstappen is dninvoerint
- **Float**. Indien aangevinkt dan verschijnt op het detailscherm van de termijnbewakingsstap een float-editbox (decimale invoer) onder het hier ingevulde label. De kolomnaam in tbtermijnbewstappen is dfinvoerfloat
- **String**. Indien aangevinkt dan verschijnt op het detailscherm van de termijnbewakingsstap een string-editbox (200 karakters) onder het hier ingevulde label. De kolomnaam in tbtermijnbewstappen is dvinvoerstring
- **Dropdown**. Indien aangevinkt dan verschijnt op het detailscherm van de termijnbewakingsstap een dropdownbox(100 karakters) onder het hier ingevulde label. De kolomnaam in tbtermijnbewstappen is dvinvoerdropd. Bij de dropdown kan het SQL-statement worden gedefinieerd op grond waarvan de keuzelijst wordt gemaakt. De resultset moet bestaan uit twee kolommen van type string genaamd id en omschrijving.

Bij deze 5 mogelijkheden kan ook de kolom _Autom. vullen afhandeldatum_ worden aangevinkt. In dat geval zal de afgehandelddatum van de stap worden gevuld met de systeemdatum bij met het wijzigen van een waarde. Bij de dropdownkolom kan ook een defaultwaarde worden opgegeven. Bij het creëren van het proces aan de voorkant komt deze waarde in de kolom dvinvoerdropd te staan. Met een keuze uit het dropdownmenu wordt deze waarde weer overschreven.

**Voorbeelden dropdown**

```sql
select 'kwik' id, 'kwik' omschrijving Union select 'kwek' id, 'kwek' omschrijving Union select 'kwak' id, 'kwak' omschrijving order by id
```

De gebruiker kan dan een keuze maken uit kwik, kwek of kwak.

```sql
select distinct a.dnkeyaardbesluit id,  coalesce(a.dvomschrijving,' ') omschrijving from vwaardbeslsoortzaak a where a.dnkeysoortomgverg in (select dnkey from tbsoortomgverg where dvsoortproc in ('U','R'))
```

De gebruiker kan kiezen uit de omschrijvingen van de coderingstabel tbcodeaardbesluit is zoverre deze gekoppeld zijn aan een omgevingzaaktype zaaktype (regulier/uitgebreid). De bijbehorende tbcodeaardbesluit.dnkey van de omschrijving is de dropdownwaarde.

> [!WARNING] **Let op:**
> Het is raadzaam wanneer de keuze gekoppeld is aan het automatisch vullen van de afhandeldatum of aan een kolomkopkoppeling de gebruiker duidelijk te maken dat de keuze nog gemaakt moet worden, juist wanneer ook een default is ingebracht, want de trigger voor de afhandeldatum en kolomkoppeling zit in het wijzigen van deze kolom dvinvoerdropd. De defaultwaarde bij kwik, kwek en kwak kan bijvoorbeeld opgegeven worden als 'Kwik (bevestig deze keuze in dropdown)'.

De gekozen dropdownwaarde wordt uiteindelijk opgeslagen in de betreffende rij van tbtermijnbewstappen in de kolom dvinvoerdropd en is in het detailscherm van de processtap aan de voorkant zichtbaar. In bovenstaand voorbeeld kiest de gebruiker uit een lijst aardbesluit omschrijvingen maar wordt de bijbehorende dnkey dus in de kolom tbtermijnbewstappen.dvinvoerdropd geplaatst. Indien dit tot verwarring leidt kunnen de kolommen id en omschrijving van de dropdownquery identiek worden gemaakt: bijvoorbeeld:

```sql
select distinct a.dnkeyaardbesluit ||':'|| coalesce(a.dvomschrijving,' ') id,  a.dnkeyaardbesluit ||':'|| coalesce(a.dvomschrijving,'') omschrijving from vwaardbeslsoortzaak a where a.dnkeysoortomgverg in (select dnkey from tbsoortomgverg where dvsoortproc in ('U','R'))
```

### Blok Canvas

Zie [Grafische weergave](/instellen_inrichten/inrichting_processen/grafische_weergave.md).

### Blok kolom-koppeling

In drie kolommen kan hier bewerkstelligd worden dat bij het vullen van de afhandeldatum van een stap, een ander veld in de bovenliggende zaak (dus van tbomgvergunning, tbhandhavingen, tbapvoverige etc.) automatisch wordt gevuld. De _tabelnaam van hoofdzaak_ (DvTabelnaam) ligt eigenlijk al vast omdat het proces waarde termijnstap aanhangt al aan een module is gekoppeld. In de kolom _Veldnaam uit hoofdzaaktabel_ (dvkolomnaam) kan een kolomnaam worden aangewezen uit de hoofdzaak met uitzondering van de kolomnamen dnkeycompoverrule, dnkeyproducten en dnkeyproductklanten.

In de combobox-kolom _Veldnaam vullen met_ (dvomschrijvingvv) kan (indien de box nog leeg is) gekozen worden uit:

- ddafgehandeld. In dat geval wordt de gekozen kolom uit de hoofdzaak gevuld met dezelfde waarde als de afgehandeld datum van de stap.. Data type moet natuurlijk wel overeenkomen!!
- ddinvoerdatum. In dat geval wordt de gekozen kolom uit de hoofdzaak gevuld met dezelfde waarde als de ingevoerde waarde in de extra kolom _InvoerDatum_ bij die stap
- dvinvoerstring. In dat geval wordt de gekozen kolom uit de hoofdzaak gevuld met dezelfde waarde als de ingevoerde waarde in de extra kolom _InvoerString_ bij die stap
- dvinvoerdropd. In dat geval wordt de gekozen kolom uit de hoofdzaak gevuld met dezelfde waarde als de gekozen waarde in de extra kolom _InvoerDropd_ bij die stap
- dninvoerint. In dat geval wordt de gekozen kolom uit de hoofdzaak gevuld met dezelfde waarde als de ingevoerde waarde in de extra kolom _InvoerInt_ bij die stap
- dfinvoerfloat. In dat geval wordt de gekozen kolom uit de hoofdzaak gevuld met dezelfde waarde als de ingevoerde waarde in de extra kolom _InvoerFloat_ bij die stap.

De gekozen waarde kan met SQL-functies omkleed worden om recht te doen aan lengte en type van de kolomnaam van de hoofdzaak. Bijvoorbeeld: _substr(dvinvoerdropd,1,1)::char(1)_ hetgeen betekent dat OpenWave de eerste positie van de waarde van de kolom dvinvoerdropd overzet naar type char(1) voordat de waarde wordt overgezet in de gekozen tabelnaam/veldnaam van de hoofdzaak.

Het voorbeeld hierboven bij de dropdownkolom, waarbij een dnkey uit tbcodeaardbesluit wordt gekozen, kan doorgezet worden naar de kolom dnkeyaardbesluit (veldnaam van hoofdzaaktabel) van de tbomgvergunning (tabelnaam van hoofdzaak) met de expressie (veldnaam vullen met): _dvinvoerdropd::integer_

Bij het tweede voorbeeld met de identieke dropdownkolommen id en omschrijving zou de expressie worden: _substr(dvinvoerdropd,1,position(':' IN dvinvoerdropd)-1)::integer_

Een waarde van char(1) kan echter bij uitzondering wel geplaats worden in een kolom van type varchar.

De kolom-koppeling wordt alleen uitgevoerd indien de afhandeldatum van de stap in aanvang nog leeg is. De kolom-koppeling wordt dus NIET uitgevoerd bij een wijziging op een stap met een gevulde afhandeldatum.

### Blok Toelichting

De tekst van deze kolom wordt bij het aanmaken van de termijnbewaking aan de voorkant overgenomen in de kolom tbtermijnbewstappen.dvprocitemtoelichting. Deze kan zichtbaar gemaakt worden (waarbij om technische redenen de komma's zijn weggehaald) in de lijst van processtappen bij een zaak. Daartoe moet de instelling _Sectie: Termijnbewaking en Item: ToelichtingZichtbaar_ aangevinkt worden. In de lijst met processtappen bij een zaak is dan op elke regel een kolom zichtbaar van type schermknop met een vraagtekentje. Het indrukken van deze schermknop laat deze toelichting uit de processtapdefinitie zien - indien gevonden – in een wizardscherm.
