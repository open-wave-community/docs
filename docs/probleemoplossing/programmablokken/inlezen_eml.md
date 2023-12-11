# Inlezen EML gegevens

In de kolom _Import_ op het portaal _Operations_ staat de ingang voor het verwerken van EML overtredingen onder tegel **Inlezen EML gegevens** (geen standaard uitgeleverde tegel). Zie voor de tegeldefinitie:[Import EML gegevens](/docs/probleemoplossing/portalen_en_moduleschermen/operationsportaal/kolom_import/import_eml_gegevens.md).

LET OP: Afhankelijk van het aantal te verwerken regels kan het gaan om een geheugen intensieve proces.
Het is de bedoeling dat alleen de EML gegevens gaande overtredingen bij inrichtingen m.b.t. OpenWave worden opgenomen in het inleesbestand.
Mochten er een groot aantal te verwerken regels in het inleesbestand staan (1000 of meer) dan raden we aan deze alleen na reguliere werktijd uit te voeren.

### Inlezen aangeleverde EML gegevens

OpenWave zal de EML overtredingsgegevens doorlopen gaande inrichtingen, op basis van de Excelfile die wordt geüpload via de wizard onder tegel _Inlezen EML Gegevens_.
Dit leidt (mogelijk) tot het aanmaken van één nieuw inspectietraject per inrichting en daaronder het aanmaken van de overtreding(en).

### Structuur files

De inlogger dient een Excelfile aan te wijzen op zijn of haar device met daarin op 1 tabblad de te verwerken EML overtredingen.

In de Excelfile moet één van de eerste 5 regels een regel zijn die bestaat uit de volgende kolommen (in de documentatie hier zijn de kolommen gescheiden met een komma) in deze specifieke volgorde(!):

`Inrichtingsnummer,eml_code_maatregel,omschrijving_maatregel,activiteit,datum,uitleg inrichting , opm. Meijer`

De door OpenWave te verwerken EML gegevens, begint direct onder deze bovenstaande regel. Vanaf hier wordt dus de daadwerkelijk door OpenWave te verwerken gegevens verwacht.

Het programma verwacht dat de regels gevuld zijn conform de hierboven genoemde kolommen. Goed om te weten is dat als er een # in de gegevens staat (staat soms in de opmerking bij een overtredingsregel), dan kan de JAVA dit niet 'correct' verwerken. Dit betekent dat het inleesprogramma WEL doorgaat maar zal er in OpenWave als tekst 'ERROR: # N/A' getoond worden in de velden waar eerder een # stond.

Verder moet de datumkolom _datum_ de vorm dd-mm-jjjj hebben. Dit betekent dat het de eigenschap _Datum_ heeft in Excel. Is dit niet het geval of is de datumkolom leeg? Dan kan de regel niet verwerkt worden en komt deze op de uitvallijst.

### Benodigde instellingen

Voordat het inleesprogramma de overtredingsregels in de Excelfile gaat verwerken, controleert het programma eerst of de benodigde instellingen/gegevens aanwezig zijn:

(het programma geeft een foutmelding in de wizard als een van onderstaande niet goed is ingesteld)

- de configuratie instelling die aangeeft met welk inspectietrajectsoort het nieuwe inspectietraject moet worden aangemaakt waaronder de overtredingen zullen worden aangemaakt. Het gaat dan om instelling _Sectie: Inspecties en Item: EMLToezichtControle_ bij _Getal1_ moet een geldige tbinspaanleiding.dnkey zijn opgegeven
- er precies één medewerker is met de naam _Intake EML_ (veld achternaam bij de medewerkerkaart).

### Verwerking

Het starten van het verwerkingsproces (wordt gedaan met een runnable) leidt tot:

- aanmaken van een regel in de tabel tboperationslog (ook in portaal _Operations_) met codering _EML gegevens inlezen_ en het moment van starten
- vullen van de _Datum_ van de instelling _Sectie: Operations_ _Item: InlezenEMLGegevens_ met timestamp. De kolom _Tekst_ wordt gevuld met medewerkerscode en _Getal1_ met 1. Hiermee wordt voorkomen dat een tweede persoon ook een importproces Inlezen EML start.

Het programma loopt de regels in de Excel één voor één door waarbij geldt dat er eerst gecontroleerd wordt of er voor het inrichtingsnummer al een regel is verwerkt tijdens deze inleesactie.

Is er voor het inrichtingsnummer nog niet in deze inleesactie een regel verwerkt, dan gaat het programma eerst kijken of de inrichting bekend is in OpenWave. Zo niet dan komt deze op de uitvallijst. Wordt de inrichting wel gevonden in OpenWave, dan wordt er bij de inrichting een nieuw inspectietraject aangemaakt met aanleiding zoals opgegeven in eerder genoemde instelling en met als inspecteur de medewerker met naam _Intake EML_.

Vervolgens wordt onder dit inspectietraject de overtreding aangemaakt.

Is er wel al eerder een regel verwerkt in deze inleesactie voor de inrichting, dan gaat het programma kijken of hiervoor ook succesvol een inspectietraject en overtreding is aangemaakt, zo ja dan wordt onder het eerder nieuw aangemaakte inspectietraject de overtreding toegevoegd van de huidige inleesregel. Is dit niet het geval dan komt de regel op de uitvallijst.

De inleesactie wordt uitgevoerd in een separaat proces zonder userinterface. De gebruiker kan via het lijstscherm van de operationslog (te vinden via tegel _Operationslog_) het zogenaamde logboek terugvinden (het logboek is waar de uitvallijst te vinden is!).

Indien klaar dan wordt:

- de einddatum/tijd op de tboperationslog-kaart gezet
- de status op de tboperationslog-kaart gevuld met 'Klaar'
- _Getal1_ van de instelling _Sectie: Operations_ _Item: InlezenEMLGegevens_ weer op 0 gezet: de tegel wordt hiermee weer vrijgegeven.

#### Wetten en Overtredingen (beheer)

Na het controleren van de vereiste instellingen, kijkt het programma of er onder de beheertegel _Wetten/Overtredingen_ (basistabel tbhandhwetbasis) een wet met onderwerp _EML_ bestaat. Zo ja, dan worden de EML overtredingen in de Excelfile op basis van de waarde in _eml_code_maatregel_ opgezocht onder deze wet en de nieuw aan te maken regels hier toegevoegd. Is er meer dan één wet gevonden dan pakt het programma de oudste (eerst aangemaakte regel) wet EML. Is er nog geen met wet EML? Dan maakt het programma deze aan.

Bij het doorlopen van de inleesregels wordt er per regel gekeken of de overtreding al bestaat in beheertabel tbhandhovertreding (detailscherm van een Wet/Overtreding) met als bovenliggende wet de eerder opgezochte (of aangemaakte) EML wet.

Wordt de overtreding gevonden dan pakt het programma deze dnkey als basis van de overtreding bij het aanmaken van de overtreding (in tbinsponrechtm) bij de inrichting onder het nieuwe inspectietraject.

Indien de overtreding niet gevonden wordt dan maakt het programma de overtreding aan in tbhandhovertreding met:

- als dnkeyhandhwetbasis de EML wet
- als dvemlcodering de waarde uit veld _eml_code_maatregel_
- en als dvomschrijving waarde uit veld _omschrijving_maatregel_. Vervolgens wordt de nieuwe dnkey gebruikt als basis voor de overtreding bij de inrichting.

#### Nieuwe overtredingen bij inrichtingen

Indien het dus om een bekende inrichting in OpenWave gaat wordt de EML overtreding aangemaakt bij de inrichting. In de Excelfile kunnen meerdere overtredingen voorkomen voor een inrichting. Het inleesprogramma maakt één inspectietraject aan en schaart hieronder de aan te maken overtredingen.
De EML overtreding per inleesregel wordt als volgt aangemaakt, waarbij de kolomnamen verwijzen naar de Excel-gegevens:

- **Inspecteur** is de medewerker met naam _Intake EML_
- **Datum constatering** wordt gevuld met de waarde gevonden in kolom _datum_
- **Dnkeyhandhovertreding** wordt gevuld met de dnkey van de aangemaakte/gevonden overtreding in beheertabel tbhandhovertreding
- **Activiteit** wordt gevuld met de waarde zoals opgegeven in kolom _activiteit_
- **Uitleg** wordt gevuld met de waarde zoals opgegeven in kolom _uitleg inrichting_
- **Interne opmerking** wordt gevuld met de waarde zoals opgegeven in kolom _opm. Meijer_

#### Datum inspectietraject

Aan het einde van het inlezen, gaat het programma de startdatum van het aangemaakte inspectietraject per inrichting bepalen. Hierbij wordt de datum overgenomen van de oudste, geconstateerde overtreding in het inleesbestand voor de inrichting.

#### Opstellen logboekverslag

Het verslag wordt als volgt opgesteld:
indien er foutmeldingen zijn (inrichting is niet gevonden, overtreding kan niet worden aangemaakt etc.) zullen deze bovenaan in het verslag staan daarna volgt de volgende telling:

- Aantal verwerkte overtredingen: <aantal regels die het programma doorlopen heeft>
- Aantal nieuwe overtredingen: <aantal overtredingen die aangemaakt zijn>
- Aantal overgeslagen overtredingen: <aantal overtredingen die overgeslagen zijn>
- Aantal niet gevonden inrichtingen: <aantal niet gevonden inrichtingen>

De uitvallijst/het verslag is terug te vinden in de memo van het operations logboek: na uploaden van de Excelfile met de EML gegevens kan de voortgang van verwerking hier worden gevolgd.
