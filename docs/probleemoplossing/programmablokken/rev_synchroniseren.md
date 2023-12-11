# REV-synchroniseren

Zie voor beheer en gebruik en export (OpenWave) Register Externe Veiligheid -gegevens: [Register Externe Veiligheid](/docs/instellen_inrichten/register_exrterne_veiligheid.md)

Voor een functioneel beheerder is via het Operationsportaal onder kolom Import de tegel *REV Synchronisatie* te benaderen. Deze tegel toont een lijst op basis van de tabel TbRevImportlocevactiv van actuele locatie-EVactiviteiten uit het REV, waarmee OpenWave data kunnen worden gesynchroniseerd.

Onderaan de lijst vijf knoppen:

* Met de knop *haal REV locatie-evactiviteiten identificatiecodes* worden actuele locatie-EVactiviteiten opgehaald uit REV en in de tabel TbRevImportlocevactiv opgenomen. De ontbrekende inrichtingskeys kunnen in deze lijst worden aangevuld.
* Met de *selecteerknop* kunnen een of meer rijen worden geselecteerd voor synchronisatie.
* Met de *synchroniseerknop* worden de gegevens in OpenWave overschreven voor die items die geselecteerd zijn EN een gevulde inrichtingskey hebben.
* De knop *is al proces bezig* laat zien of er al een proces om locatie-EVactiviteiten op te halen is gestart.
* De knop refresh bouwt de lijst opnieuw op op grond van de inhoud van TbRevImportlocevactiv.

## Maak lijst van locatie-EVactiviteiten uit REV

Met de knop **haal REV locatie-evactiviteiten identificatiecodes** linksonder wordt een lijst samengesteld van actuele locatie-EVactiviteiten van de bronhouder.
De bestaande lijst wordt met het gebruik van deze knop overschreven. De betreffende REV-API ({*base-URL*}/LocatieEVActiviteiten) wordt daartoe met een GET-request aangesproken. Noodzakelijke instellingen zijn:

* De base-URL moet opgegeven worden in kolom *Tekst* van *Sectie: REV* en *Item: AlgemeenEndpoint* bijvoorbeeld: <https://acc.apps.geodan.nl/public/revpreproductie/rev/api/rev/v3/>
* De namespaceidentificatie van de bronhouder moet opgegeven worden in de kolom *Tekst* van instelling *Sectie: Inrichtingen* en *Item: REVNamespaceIdentificatie* bijvoorbeeld: *NL.IMEV.OVIJ*
* In de kolom *Tekst* van *Sectie: REV* en *Item: Apikey* moet de API-key opgegeven worden waarmee de organisatie gerechtigd is de REV-API aan te roepen.

De resultset van de REV-API bestaat uit alle actuele locatie-EVactiviteiten waar OpenWave - op grond van de namespaceidentificatie - die van de bronhouder uitfiltert en die worden toegevoegd aan de tabel TbRevImportlocevactiv die vervolgens wordt getoond in de lijst. Bij het starten van het proces wordt de tabel TbRevImportlocevactiv eerst leeggemaakt. Aangezien het vullen een tijdrovende kwestie kan zijn, wordt dit - om een time-out probleem te vermijden - gedaan in een runnable (dus zonder feedback in een userinterface). In de operationslog (tegel Operationslog in het service centrumportaal) is zichtbaar of het proces al klaar is (onder de code: *haalrevidentificatiecodes*). Om te vermijden dat gelijktijdig twee of meer keer hetzelfde proces wordt gestart, krijgt *Getal1* van de instelling *Sectie:  Operations* en *Item: synchroniseerUitREV* bij het starten de waarde 1 en bij afsluiten de waarde 0. De **vraagteken-knop "is er al een proces bezig"** kijkt naar deze instelling. Met de **refreshknop** wordt (ook tijdens het proces) de lijst opnieuw uitgeschreven (dus op grond van de tabel tbRevImportlocevactiv).

Per opgehaalde locatie-EVactiviteit wordt dezelfde API nogmaals aangesproken, maar dan specifiek voor één identificatienummer, om locatie gegevens en REV-bedrijfsnaam op te halen. De REV-requests worden gelogd (servicecentrum portaal: messagelog) indien de instelling *Sectie: OWB, Item: MessageLog* aangevinkt is EN de instelling *Sectie: REV, Item: MessageLog* ook aangevinkt is.

### Actuele locatie-EVactiviteiten kolommen

De actuele locatie-EVactiviteiten worden getoond in de lijst in de volgende kolommen:

* de id in OpenWave: dnkey van TbRevImportlocevactiv
* de identificatiecode van de locatie-EVactiviteit in het REV
* aanvinkvakje (dlmatchidentificatie). Is aangevinkt indien de kolom inrichtingskey is gevuld en wel op basis van de REV-identificatiecode. Indien niet aangevinkt en de kolom inrichtingskey is wel gevuld dan is dit dus gebeurd op basis van de bronobjectid.
* de inrichtingskey uit OpenWave. Dit is de tbmilinrichtingen.dnkey die gevonden is op basis van de REV-identificatiecode opgezocht in tbmilinrichtingen.dvidentificatie. Indien er geen match is op identificatie en indien *Getal1* van de instelling *Sectie: REV, Item: ImportBronobjectID* de waarde 1 heeft, dan wordt geprobeerd de inrichtingskey te vinden door het inrichtingsnummer te zoeken op grond van de opgehaalde bronobjectID.

Leeg indien er geen match is.

De beheerder kan zelf een inrichtingskey toevoegen aan de regel indien hij/zij de REV-identificatiecode of REV-bedrijfsnaam weet thuis te brengen bij een bestaande OpenWave inrichting (zie knop *synchroniseer aangevinkte items)*.

* BronObjectID uit REV. Indien *Getal1* van de instelling *Sectie: REV, Item: ImportBronobjectID* de waarde 1 heeft, dan wordt deze waarde geïnterpreteerd als een inrichtingnummer van OpenWave.
* Inrichtingsnaam OW wordt opgehaald uit OpenWave op grond van de inrichtingskey.
* Exportdatum naar REV geeft aan wanneer vanuit  OpenWave de gehele set locatie-EVactiviteit (met activiteiten, referentie- en EV-contouren) is geëxporteerd. Kan alleen gevuld zijn indien inrichtingskey gevuld is.
* Locatie omschrijving in REV. De locatie zoals omschreven in het REV.
* Bedrijfsnaam in REV. Kan dus afwijken van die in OpenWave.
* BAGnummeridentificatie in REV. De BAG-nummer identificatie uit het REV.
* Kleurballetje. Rood wil zeggen dan de REV-Bagnummeridentificatie afwijkt van die van de locatie (tbperceeladressen.dvbagidentcode_3) waar de inrichting aan verbonden is (dus alleen bij gevulde inrichtingskey). Heeft verder geen directe consequentie want voor het REV heeft de inrichting een eigen kolom voor deze BAG-identificatie (dvrevbagnummerid).
* BAG-adres, plaats en gemeente. Deze komen uit OpenWave op grond van de REV BAGnummeridentificatie.

## Zet een selectie klaar voor synchronisatie

Met de knop **aanvinken/uitvinken** kan een selectie op de rijen uit de lijst worden gemaakt, waarmee zij klaar worden gezet voor synchronisatie. Alleen de rijen die aangevinkt zijn EN die een gevulde inrichtingskey hebben kunnen worden gesynchroniseerd (dus de aangevinkte items zonder inrichtingskey worden genegeerd).

Overigens kan het aanvinkvakje ook per rij met de hand worden aan- en uitgevinkt.

## Synchronisatie aangevinkte rijen

Met de knop **synchroniseer aangevinkte items** worden de REV-data in OpenWave van de inrichtingen die corresponderen met de aangevinkte rijen (aangevinkte rijen met een lege inrichtingskey worden genegeerd) overschreven met de data uit het REV. Per rij (dus per inrichting) gebeurt het volgende:

* De volledige locatie-EVactiviteit set van de inrichting wordt opgehaald uit het REV (op identificatiecode). Hierna genoemd de Json-resultset.
* De gekoppelde EV-activiteiten bij de betreffende inrichting uit tbmilbklactiviteiten worden verwijderd (en daarmee ook de gekoppelde referentiecontouren: dus de kaarten uit tbmilopslag met overeenkomende dnkeybklactiviteiten EN de daaraan gekoppelde EV-contourkaarten uit tbmilopslagevcontour).
* De inrichtingsdata m.b.t. REV van de betreffende tbmilinrichtingen-kaart worden overschreven met de gevonden waardes uit de Json resultset (dvlocatieevactiviteit, dvbedrijfsnaam, dvidentificatie, ddbegingeldigheid, dvgmlpolygoon, dvrevlocatieomschrijving, dvhandelsnaam, dvkvknr, dvrevbagnummerid).
* De volgende kolommen van tbmilinrichtingen worden leeggemaakt: ddeindgeldigheid, ddrevpreviewok (datum laatste preview ok), ddmagexport (datum klaargezet voor export), dvcodemwmagexport (de medewerkerscode die ddmagexport heeft gevuld).
* De volgende kolommen van tbmilinrichtingen worden gevuld met een timestamp: dddatumlaatstewijziging, ddexportnaarrev (dus de laatste exportdatum naar REV).
* Bij de inrichting worden vervolgens de activiteiten en referentiecontouren en EV-contouren uit Json resultset toegevoegd met alle attributen. Voorwaarde is wel dat de featuretype-namen en attribuutnamen uit de Json resultset overeenkomen met de definities uit de OpenWave beheertabellen EN dat voor de attributen geldt dat deze in OpenWave aangevinkt staan als Overnemen (zie [Register Externe Veiligheid](/docs/instellen_inrichten/register_exrterne_veiligheid.md)). De dddatumlaatstewijziging en ddexportnaarrev wordt voor alle aangemaakte kaarten gevuld met timestamp.

De **noodzakelijke instellingen** zijn dezelfde als hierboven beschreven bij de knop *haal REV locatie-evactiviteiten identificatiecodes*. Om opslagkaarten te kunnen toevoegen (de referentiecontouren) zijn echter nog een aantal instellingen verplicht:

* Dnkeywaarde uit tbmilsrtOpslag die gebruikt moet worden om een tbmilopslagkaart aan te maken : *Getal1* van *Sectie: REV, Item: importdefkeymilsrtopslag*
* Dnkeywaarde uit tbmilrubriek := *Getal1* van *Sectie: REV, Item: importdefkeymilrubriek*
* Dnkeywaarde uit tbmilvoorzopslag:= *Getal1* van *Sectie: REV, Item: importdefkeymilvoorzopslag*
* Dnkeywaarde uit tbmilstatusopslag := *Getal1* van *Sectie: REV, Item: importdefkeymilstatusopslag*

Aangezien het synchroniseren een tijdrovende kwestie kan zijn, wordt dit - om een time-out probleem te vermijden - gedaan in een runnable (dus zonder feedback in een userinterface). In de operationslog (tegel Operationslog in het service centrumportaal) is zichtbaar of het proces al klaar is (onder de code: *synchroniseeruitrev*) en zijn eventuele foutmeldingen zichtbaar. Om te vermijden dat gelijktijdig twee of meer keer hetzelfde proces wordt gestart, krijgt *Getal1* van de instelling *Sectie: Operations* en *Item: synchroniseeruitrev* bij het starten de waarde 1 en bij afsluiten de waarde 0.
