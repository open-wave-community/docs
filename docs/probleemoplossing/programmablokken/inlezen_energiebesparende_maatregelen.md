# Inlezen EB Maatregelen (EBM)

In de kolom *Import* op het portaal *Operations* staat de ingang voor het verwerken van Energie Besparende Maatregelen onder tegel **Inlezen EB Maatregelen** (geen standaard uitgeleverde tegel). Zie voor de tegeldefinitie:[Import Energie Besparende Maatregelen (EBM)](/docs/probleemoplossing/portalen_en_moduleschermen/operationsportaal/kolom_import/import_ebmaatregelen.md).

**LET OP:** afhankelijk van het aantal te verwerken regels kan het gaan om een geheugen intensief proces.
Mocht er een groot aantal te verwerken regels in het inleesbestand staan (1000 of meer),
dan raden we aan de import na reguliere werktijd uit te voeren.

## Inlezen aangeleverde Energie Besparende Maatregelen (EBM) bij inrichtingen

OpenWave zal de EBM gegevens voor inrichtingen doorlopen op basis van de Excelfile die wordt geüpload via de wizard onder tegel *Inlezen EB Maatregelen*.
Indien een inrichting nog niet bestond leidt dit mogelijk tot het aanmaken ervan in OpenWave en het daaronder aanmaken van de bijhorende maatregel(en).

Indien een inrichting al bestaat in OpenWave zal de maatregel ofwel aangemaakt worden bij de inrichting (indien het om een nieuwe maatregel gaat), ofwel gewijzigd worden.

### Structuur files

De inlogger dient een Excelfile aan te wijzen op zijn of haar device met daarin op 1 tabblad: de te verwerken EB Maatregelen.
In de Excelfile moet één van de eerste 5 regels een regel zijn die bestaat uit de volgende kolommen (in deze documentatie zijn de kolommen gescheiden met een komma) in deze specifieke volgorde(!):

Inrichtingnummer,Inrichtingnaam,Gemeente,Straat,Huisnummer,Huisletter,Huistoevoeging,Postcode,Plaats,Datum scan,Maatregeltype,Maatregelnaam,Investering Bruto,Investering Netto,Jaarlijkse Besparing in Euro,TvT,CO2 Reductie,Energie Reductie

**Let op:**

* de door OpenWave te verwerken EB Maatregelen bij inrichtingen, begint direct onder deze bovenstaande regel. Vanaf hier wordt dus de daadwerkelijk door OpenWave te verwerken gegevens verwacht.
* het programma verwacht dat de regels gevuld zijn conform de hierboven genoemde kolommen. Goed om te weten is dat als er een # in de gegevens staat, dan kan de JAVA dit niet 'correct' verwerken. Dit betekent dat het inleesprogramma WEL doorgaat maar zal er in OpenWave als tekst 'ERROR: # N/A' getoond worden in de velden waar eerder een # stond.
* verder moet de datumkolom *datum* de vorm dd/mm/jjjj hebben. Dit betekent dat het de eigenschap *Datum* heeft in Excel. Is dit niet het geval of is de datumkolom leeg? Dan kan de regel niet verwerkt worden en komt deze op de uitvallijst.

### Verwerking

Het starten van het verwerkingsproces (wordt gedaan met een runnable) leidt tot:

* aanmaken van een regel in de tabel tboperationslog (ook in portaal *Operations*) met codering *EB Maatregelen inlezen* en het moment van starten
* vullen van de *Datum* van de instelling *Sectie: Operations*, *Item: InlezenEBMaatregelen* met timestamp. De kolom *Tekst* wordt gevuld met medewerkerscode en *Getal1* met 1. Hiermee wordt voorkomen dat een tweede persoon ook een importproces Inlezen EB Maatregelen start.

Het programma loopt de regels in de Excel één voor één door waarbij geldt dat het programma eerst kijkt of er voor de inrichting al een regel is verwerkt tijdens deze inleesactie.

Is er voor de inrichting nog niet in deze inleesactie een regel verwerkt dan wordt er gecontroleerd of het om een bestaande inrichting zou moeten gaan in OpenWave (kolom *Inrichtingnummer* is gevuld in de Excel) of dat er een nieuwe inrichting moet worden aangemaakt (kolom *Inrichtingnummer* is leeg).

Indien het om een bestaande inrichting gaat dan gaat het programma kijken of de inrichting daadwerkelijk voorkomt in OpenWave (er is precies 1 inrichting met inrichtingnummer gelijk aan kolom *Inrichtingnummer*). Niet gevonden dan komt deze op de uitvallijst. Wordt de inrichting wel gevonden in OpenWave, dan wordt er bij de inrichting gekeken of de EB Maatregel al bestaat:

* Ja dan wordt alleen **Laatste scandatum** gewijzigd met datum van inleesactie
* Nee dan wordt nieuwe regel ingelezen in tbmilebmgegevens.

Indien het om een niet bestaande inrichting gaat dan gaat het programma de inrichting proberen aan te maken op adres zoals opgegeven in Excel en met als naam waarde van kolom *Inrichtingnaam*:

* gelukt dan wordt er bij de inrichting een nieuwe regel aangemaakt in tbmilebmgegevens
* niet gelukt dan komt de inrichting op de uitvallijst.

Is er wel al eerder een regel verwerkt in deze inleesactie voor de inrichting, dan gaat het programma kijken of de inrichting toen ook gevonden/aangemaakt is in OpenWave:

* Zo ja dan wordt ook hier gekeken of het om een bestaande maatregel gaat bij de inrichting en deze gewijzigd/ dan wel een nieuwe EB maatregel aangemaakt bij de inrichting
* Zo nee dan komt de regel op de uitvallijst.

De inleesactie wordt uitgevoerd in een separaat proces zonder userinterface. De gebruiker kan via het lijstscherm van de operationslog (te vinden via tegel *Operationslog*) het zogenaamde logboek terugvinden (het logboek is waar de uitvallijst te vinden is!).

Indien klaar dan wordt:

* de einddatum/tijd op de tboperationslog-kaart gezet
* de status op de tboperationslog-kaart gevuld met 'Klaar'
* *Getal1* van de instelling *Sectie: Operations* *Item: InlezenEBMaatregelen* weer op 0 gezet: de tegel wordt hiermee weer vrijgegeven.

#### Beheertabellen EBM-type en EBM-naam

In het beheer zijn twee brontabellen ten behoeve van energie besparende maatregelen toegevoegd: tbebmtype en tbebmnaam. Iedere Energie Besparend Maatregel heeft een naam (tbemnaam) en valt onder een energie besparend type (tbebmtype). Tijdens de inleesactie gaat het programma controleren of het EBM-type EN de daaronder vallende maatregel al bestaan in OpenWave. Wordt de Maatregel gevonden dan pakt het programma deze dnkey als basis bij het aanmaken van de maatregel (in tbmilebmgegevens) bij de inrichting.

Indien de maatregel (en/of type) nog niet bestaat dan zal/zullen deze tijdens de inleesactie worden aangemaakt.

  ***EBM-type**: het programma zoekt in tbebmtype naar een nog niet vervallen record op basis van kolom *Maatregeltype* uit de Excel. Indien niet gevonden dan wordt er een nieuw record aangemaakt in tbebmtype waarbij dvomschrijving wordt gevuld met waarde van kolom *Maatregeltype*.

  ***Maatregel (EBM-naam)**: het programma zoekt in tbebmnaam naar een nog niet vervallen record op basis van kolom *Maatregelnaam* uit de Excel EN met dnkeyebmtype zoals gevonden op basis van kolom *Maatregeltype* OF met de dnkey van zojuist aangemaakte EBM-type.

 Indien de maatregel niet wordt gevonden dan wordt er een nieuw record aangemaakt in tbebmnaam waarbij dnkeyebmtype wordt gevuld met dnkey van tbebmtype (al dan niet gevonden/ aangemaakt zoals boven beschreven) en dvomschrijving wordt gevuld met waarde van kolom *Maatregelnaam*.
 Vervolgens wordt de nieuwe dnkey gebruikt als basis voor het aanmaken van de maatregel bij de inrichting.

#### Nieuwe Maatregel bij inrichtingen

Indien de inrichting gevonden/aangemaakt is en de maatregel nog niet bestaat bij de inrichting, dan wordt de Maatregel aangemaakt bij de inrichting. In de Excelfile kunnen meerdere EB Maatregelen voorkomen voor een inrichting.
De EB Maatregel per inleesregel wordt als volgt aangemaakt, waarbij de kolomnamen verwijzen naar de Excel-gegevens:

* **Dnkeymilinrichtingen** wordt gevuld met de dnkey van de zojuist aangemaakte inrichting indien kolom *Inrichtingnummer* leeg was, anders met de gevonden dnkey uit tmilinrichtingen waarvan inrichtingnummer gelijk aan waarde van kolom *Inrichtingnummer*
* **Dnkeyebnaam** wordt gevuld met de dnkey van de aangemaakte/gevonden maatregel in beheertabel tbebmnaam
* **Investering Bruto** wordt gevuld met de waarde zoals opgegeven in kolom *Investering Bruto*
* **Investering Netto** wordt gevuld met de waarde zoals opgegeven in kolom *Investering Netto*
* **Jaarlijkse besparing (euro)** wordt gevuld met de waarde zoals opgegeven in kolom *Jaarlijkse Besparing in Euro*
* **Terug verdien Tijd** wordt gevuld met de waarde zoals opgegeven in kolom *TvT*
* **CO2 Reductie** wordt gevuld met de waarde zoals opgegeven in kolom *CO2 Reductie*
* **Energie Reductie** wordt gevuld met de waarde zoals opgegeven in kolom *Energie Reductie*
* **Aanmaakdatum** wordt gevuld met de waarde zoals opgegeven in kolom *Datum scan*
* **Laatste scandatum** wordt gevuld met datum van vandaag

De EB maatregelen bij inrichtingen kan men terugvinden onder kolom *Duurzaamheid* in het Inrichtingportaal, **tegel Energie besparende maatregelen**.

#### Vervallen Maatregelen

De aangeleverde Excel file bevat alle maatregelen die nog steeds van kracht zijn bij inrichtingen. De maatregelen die eerder zijn aangemaakt in OpenWave (via het inleesprogramma al dan niet handmatig) EN niet meer voorkomen in de Excel file op moment van inlezen, zijn daarmee vervallen.

Het programma zal na het doorlopen van alle regels in de Excel file, de tabel van maatregelen bij inrichtingen (tbmilebmgegevens) doorlopen en voor alle regels waarvan geldt dat **Laatste scandatum** NIET de datum van vandaag heeft EN de vervaldatum nog niet gevuld is, de vervaldatum zetten (met datum van vandaag).
Men kan aan de voorkant bij inrichtingen zien of een maatregel vervallen is voor de inrichting middels het veld **Vervaldatum**.

#### Opstellen logboekverslag

Het verslag wordt als volgt opgesteld:
indien er foutmeldingen zijn (inrichting is niet gevonden, Maatregel kan niet worden aangemaakt etc.) zullen deze bovenaan in het verslag staan daarna volgt de volgende telling:

* Aantal verwerkt: `<aantal regels die het programma doorlopen heeft>`
* Aantal aangemaakte maatregelen: `<aantal maatregelen die aangemaakt zijn>`
* Aantal overgeslagen maatregelen: `<aantal maatregelen die overgeslagen zijn>`
* Aantal overgeslagen inrichtingen: `<aantal overgeslagen inrichtingen>`-
* Aantal niet aangemaakte inrichtingen: `<aantal inrichtingen dat niet aangemaakt kon worden>`
* Aantal nieuwe inrichtingen: `<aantal nieuw aangemaakte inrichtingen>`

De uitvallijst/het verslag is terug te vinden in de memo van het operations logboek: na uploaden van de Excelfile met de EB Maatregelen kan de voortgang van verwerking hier worden gevolgd.
