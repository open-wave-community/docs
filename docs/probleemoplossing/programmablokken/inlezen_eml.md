# Inlezen EML gegevens

In de kolom *Import* op het portaal *Operations* staat de ingang voor het verwerken van EML overtredingen onder tegel **Inlezen EML gegevens** (geen standaard uitgeleverde tegel). Zie voor de tegeldefinitie:[Import EML gegevens](/docs/probleemoplossing/portalen_en_moduleschermen/operationsportaal/kolom_import/import_eml_gegevens.md).

LET OP: Afhankelijk van het aantal te verwerken regels kan het gaan om een geheugen intensieve proces.
Het is de bedoeling dat alleen de EML gegevens gaande overtredingen bij inrichtingen m.b.t. OpenWave worden opgenomen in het inleesbestand.
Mochten er een groot aantal te verwerken regels in het inleesbestand staan (1000 of meer) dan raden we aan deze alleen na reguliere werktijd uit te voeren.

### Inlezen aangeleverde EML gegevens

OpenWave zal de EML overtredingsgegevens doorlopen gaande inrichtingen, op basis van de Excelfile die wordt geüpload via de wizard onder tegel *Inlezen EML Gegevens*.
Dit leidt (mogelijk) tot het aanmaken van één nieuw inspectietraject per inrichting en daaronder het aanmaken van de overtreding(en).

### Structuur files

De inlogger dient een Excelfile aan te wijzen op zijn of haar device met daarin op 1 tabblad de te verwerken EML overtredingen.

In de Excelfile moet één van de eerste 5 regels een regel zijn die bestaat uit de volgende kolommen (in de documentatie hier zijn de kolommen gescheiden met een komma) in deze specifieke volgorde(!):

`Inrichtingsnummer,eml_code_maatregel,omschrijving_maatregel,activiteit,datum,uitleg inrichting , opm. Meijer`

De door OpenWave te verwerken EML gegevens, begint direct onder deze bovenstaande regel. Vanaf hier wordt dus de daadwerkelijk door OpenWave te verwerken gegevens verwacht.

Het programma verwacht dat de regels gevuld zijn conform de hierboven genoemde kolommen. Goed om te weten is dat als er een # in de gegevens staat (staat soms in de opmerking bij een overtredingsregel), dan kan de JAVA dit niet 'correct' verwerken. Dit betekent dat het inleesprogramma WEL doorgaat maar zal er in OpenWave als tekst 'ERROR: # N/A' getoond worden in de velden waar eerder een # stond.

Verder moet de datumkolom *datum* de vorm dd-mm-jjjj hebben. Dit betekent dat het de eigenschap *Datum* heeft in Excel. Is dit niet het geval of is de datumkolom leeg? Dan kan de regel niet verwerkt worden en komt deze op de uitvallijst.

### Benodigde instellingen

Voordat het inleesprogramma de overtredingsregels in de Excelfile gaat verwerken, controleert het programma eerst of de benodigde instellingen/gegevens aanwezig zijn:

(het programma geeft een foutmelding in de wizard als een van onderstaande niet goed is ingesteld)

* de configuratie instelling die aangeeft met welk inspectietrajectsoort het nieuwe inspectietraject moet worden aangemaakt waaronder de overtredingen zullen worden aangemaakt. Het gaat dan om instelling *Sectie: Inspecties en Item: EMLToezichtControle* bij *Getal1* moet een geldige tbinspaanleiding.dnkey zijn opgegeven
* er precies één medewerker is met de naam *Intake EML* (veld achternaam bij de medewerkerkaart).

### Verwerking

Het starten van het verwerkingsproces (wordt gedaan met een runnable) leidt tot:

* aanmaken van een regel in de tabel tboperationslog (ook in portaal *Operations*) met codering *EML gegevens inlezen* en het moment van starten
* vullen van de *Datum* van de instelling *Sectie: Operations* *Item: InlezenEMLGegevens* met timestamp. De kolom *Tekst* wordt gevuld met medewerkerscode en *Getal1* met 1. Hiermee wordt voorkomen dat een tweede persoon ook een importproces Inlezen EML start.

Het programma loopt de regels in de Excel één voor één door waarbij geldt dat er eerst gecontroleerd wordt of er voor het inrichtingsnummer al een regel is verwerkt tijdens deze inleesactie.

Is er voor het inrichtingsnummer nog niet in deze inleesactie een regel verwerkt, dan gaat het programma eerst kijken of de inrichting bekend is in OpenWave. Zo niet dan komt deze op de uitvallijst. Wordt de inrichting wel gevonden in OpenWave, dan wordt er bij de inrichting een nieuw inspectietraject aangemaakt met aanleiding zoals opgegeven in eerder genoemde instelling en met als inspecteur de medewerker met naam *Intake EML*.

Vervolgens wordt onder dit inspectietraject de overtreding aangemaakt.

Is er wel al eerder een regel verwerkt in deze inleesactie voor de inrichting, dan gaat het programma kijken of hiervoor ook succesvol een inspectietraject en overtreding is aangemaakt, zo ja dan wordt onder het eerder nieuw aangemaakte inspectietraject de overtreding toegevoegd van de huidige inleesregel. Is dit niet het geval dan komt de regel op de uitvallijst.

De inleesactie wordt uitgevoerd in een separaat proces zonder userinterface. De gebruiker kan via het lijstscherm van de operationslog (te vinden via tegel *Operationslog*) het zogenaamde logboek terugvinden (het logboek is waar de uitvallijst te vinden is!).

Indien klaar dan wordt:

* de einddatum/tijd op de tboperationslog-kaart gezet
* de status op de tboperationslog-kaart gevuld met 'Klaar'
* *Getal1* van de instelling *Sectie: Operations* *Item: InlezenEMLGegevens* weer op 0 gezet: de tegel wordt hiermee weer vrijgegeven.

#### Wetten en Overtredingen (beheer)

Na het controleren van de vereiste instellingen, kijkt het programma of er onder de beheertegel *Wetten/Overtredingen* (basistabel tbhandhwetbasis) een wet met onderwerp *EML* bestaat. Zo ja, dan worden de EML overtredingen in de Excelfile op basis van de waarde in *eml_code_maatregel* opgezocht onder deze wet en de nieuw aan te maken regels hier toegevoegd. Is er meer dan één wet gevonden dan pakt het programma de oudste (eerst aangemaakte regel) wet EML. Is er nog geen met wet EML? Dan maakt het programma deze aan.

Bij het doorlopen van de inleesregels wordt er per regel gekeken of de overtreding al bestaat in beheertabel tbhandhovertreding (detailscherm van een Wet/Overtreding) met als bovenliggende wet de eerder opgezochte (of aangemaakte) EML wet.

Wordt de overtreding gevonden dan pakt het programma deze dnkey als basis van de overtreding bij het aanmaken van de overtreding (in tbinsponrechtm) bij de inrichting onder het nieuwe inspectietraject.

Indien de overtreding niet gevonden wordt dan maakt het programma de overtreding aan in tbhandhovertreding met:

* als dnkeyhandhwetbasis de EML wet
* als dvemlcodering de waarde uit veld *eml_code_maatregel*
* en als dvomschrijving waarde uit veld *omschrijving_maatregel*. Vervolgens wordt de nieuwe dnkey gebruikt als basis voor de overtreding bij de inrichting.

#### Nieuwe overtredingen bij inrichtingen

Indien het dus om een bekende inrichting in OpenWave gaat wordt de EML overtreding aangemaakt bij de inrichting. In de Excelfile kunnen meerdere overtredingen voorkomen voor een inrichting. Het inleesprogramma maakt één inspectietraject aan en schaart hieronder de aan te maken overtredingen.
De EML overtreding per inleesregel wordt als volgt aangemaakt, waarbij de kolomnamen verwijzen naar de Excel-gegevens:

* **Inspecteur** is de medewerker met naam *Intake EML*
* **Datum constatering** wordt gevuld met de waarde gevonden in kolom *datum*
* **Dnkeyhandhovertreding** wordt gevuld met de dnkey van de aangemaakte/gevonden overtreding in beheertabel tbhandhovertreding
* **Activiteit** wordt gevuld met de waarde zoals opgegeven in kolom *activiteit*
* **Uitleg** wordt gevuld met de waarde zoals opgegeven in kolom *uitleg inrichting*
* **Interne opmerking** wordt gevuld met de waarde zoals opgegeven in kolom *opm. Meijer*

#### Datum inspectietraject

Aan het einde van het inlezen, gaat het programma de startdatum van het aangemaakte inspectietraject per inrichting bepalen. Hierbij wordt de datum overgenomen van de oudste, geconstateerde overtreding in het inleesbestand voor de inrichting.

#### Opstellen logboekverslag

Het verslag wordt als volgt opgesteld:
indien er foutmeldingen zijn (inrichting is niet gevonden, overtreding kan niet worden aangemaakt etc.) zullen deze bovenaan in het verslag staan daarna volgt de volgende telling:

* Aantal verwerkte overtredingen: <aantal regels die het programma doorlopen heeft>
* Aantal nieuwe overtredingen: <aantal overtredingen die aangemaakt zijn>
* Aantal overgeslagen overtredingen: <aantal overtredingen die overgeslagen zijn>
* Aantal niet gevonden inrichtingen: <aantal niet gevonden inrichtingen>

De uitvallijst/het verslag is terug te vinden in de memo van het operations logboek: na uploaden van de Excelfile met de EML gegevens kan de voortgang van verwerking hier worden gevolgd.
