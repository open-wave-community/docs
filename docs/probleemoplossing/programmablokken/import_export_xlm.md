# Import/Export rapport, sjabloon etc

### Waar vandaan aangeroepen

Operationsportaal: tegels **Export** en **Import** xml OpenWave,sjablonen,schermen,queries, processen…

## Rechten

De inlogger moet beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99.

### Exporteren

In scherm wordt gevraagd een keuze te maken uit de opties:

- rapportdefinities
- sjablonendefinities
- schermkolomdefinities
- queries
- processen
- configuratie-items
- standaard tabellen
- Emailsjablonen
- Container rapportages

#### Export rapportdefinities(uit de tabel tbrapporten)

- In het eerste scherm wordt gevraagd om één of meer rapportgroepen te kiezen.
- In het tweede scherm wordt gevraagd om één of meer rapportage-definities te kiezen die behoren bij de aangevinkte rapportgroepen.
- De export xml wordt gemaakt onder de naam export*rapporten*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De xml bestaat uit de geselecteerde kaarten uit tbrapporten per rapportgroep en daarbinnen - genest - de bijbehorende kaarten uit tbrapportparameters.

#### Export sjabloon (uit de tabel tbdocumenten)

- In het eerste scherm wordt gevraagd om één of meer documentgroepen te kiezen.
- In het tweede scherm wordt gevraagd om één sjabloon aan te wijzen dat behoort tot een van de aangevinkte sjabloongroepen. Er kan maar één sjabloon tegelijk worden geëxporteerd omdat het basis Word/Odt document in het sjabloon zit opgesloten.
- De export xml wordt gemaakt onder de naam export*sjablonen*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De xml bestaat dus uit één kaart uit tbdocumenten met de bijbehorende documentgroep en daarbinnen - genest - de bijbehorende kaarten uit tbdocparameters.

#### Export schermkolomdefinities (uit de tabel tbscreencolumns)

- In het eerste scherm wordt gevraagd om één of meer klassen te kiezen.
- In het tweede scherm wordt gevraagd om één of meer schermkolomdefinities aan te wijzen die behoren bij de aangevinkte klassen.
- De export xml wordt gemaakt onder de naam export*screencolumns*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De xml bestaat uit de geselecteerde kaarten uit tbscreencolumns per klasse.

#### Export queries (uit de tabel tbqueries)

- In het eerste scherm wordt gevraagd om één of meer groepen te kiezen.
- In het tweede scherm wordt gevraagd om één of meer queries aan te wijzen die behoren bij de aangevinkte groepen.
- De export xml wordt gemaakt onder de naam export*queries*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De xml bestaat uit de geselecteerde kaarten uit tbqueries per groep.

#### Export processen (uit de tabel tbprocedures en tbprocitems)

- In het eerste scherm wordt gevraagd om één of meer Groepen te kiezen. De groepen zijn in dit geval de modules.
- In het tweede scherm wordt gevraagd om één of meer Processen te kiezen die behoren bij de aangevinkte groepen.
- De export xml wordt gemaakt onder de naam export*processen*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De xml bestaat uit de geselecteerde kaarten uit tbprocedures en daarbinnen - genest - de bijbehorende kaarten uit tbprocitems (de processtappen).

Als bij processtappen een default behandelaar of team is toegekend wordt dit ook geëxporteerd. Dit wordt echter alleen ingevuld als de naam van de betreffende behandelaar of het team bestaat in het systeem waar wordt geïmporteerd. Als de behandelaar of het team niet bestaat dan wordt dit veld niet gevuld. Informatie met betrekking tot compartimenten wordt niet meegenomen in de export.

#### Export configuratie-items (uit de tabel tbinitialisatie)

- In het eerste scherm wordt gevraagd om één of meer secties te kiezen.
- In het tweede scherm wordt gevraagd om één of meer items te kiezen die behoren bij de aangevinkte secties.
- De export xml wordt gemaakt onder de naam export*configuratieitems*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De items die in OpenWave in de lijstweergave onder de beheertegel _Configuratie-items_ in de kolom _Tekst_ niet leesbaar zijn, maar gemarkeerd door een aantal asterisk-tekens, zullen in de export deze kolom _Tekst_ (dvstring) missen.\

#### Export standaard tabellen-items (uit de tabel tbsysstandardtable en tbsysstandardbutton)

- In het eerste scherm wordt gevraagd om één of meer categorieën te kiezen. Indien er geen categorieën zijn vink dan de lege groep aan.
- In het tweede scherm wordt gevraagd om één of meer coderingen te kiezen die behoren bij de aangevinkte categorieën.
- De export xml wordt gemaakt onder de naam export*standaardtabellen*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De xml bestaat uit de geselecteerde kaarten uit tbsysstandardtable en daarbinnen - genest - de bijbehorende kaarten uit tbsysstandardbutton (de knoppen).

#### Export Emailsjablonen (uit de tabel tbemailsjabloon)

- In het eerste scherm wordt gevraagd om één of meer groepen te kiezen.
- In het tweede scherm wordt gevraagd om één of meer emailsjablonen aan te wijzen die behoren tot een van de aangevinkte sjabloongroepen.
- De export xml wordt gemaakt onder de naam export*emailsjablonen*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De xml bestaat dus uit één of meerdere kaarten uit tbemailsjabloon met de bijbehorende sjabloongroep(en) en daarbinnen - genest - de bijbehorende kaarten uit tbemailparameters.

#### Export Container rapportages (uit de tabel tbexportcontainer)

- In het eerste scherm wordt gevraagd om één of meer containers te kiezen.
- In het tweede scherm wordt gevraagd om één of meer container rapportages te kiezen die behoren bij de aangevinkte containers.
- De export xml wordt gemaakt onder de naam export*container_rapportages*_datum/tijd_.xml in de map die op uw computer staat ingesteld als download map.
- De xml bestaat uit de geselecteerde kaarten uit tbexportcontainer per container.

### Importeren

- In het eerste scherm wordt gevraagd een importbestand aan te wijzen.
- In het tweede scherm duidt OpenWave het aangewezen bestand als NIET importeerbaar (in dat geval stopt het proces) OF als WEL importeerbaar.
- In dit laatste geval herkent OpenWave de aangewezen file als een export xml van type rapportdefinities, sjablonendefinities, schermkolomdefinities, processen, configuratie-items of standaardtabellen.

#### Importeren uit export_rapporten.xml

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren rapportgroepen.

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren rapporten bij de aangevinkte rapportgroepen.

Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe rapporten toevoegen
- nieuwe rapporten toevoegen en al bestaande overschrijven
- alles toevoegen (bestaande krijgen naam(1))

De eerste keuze betekent dat van de aangewezen combinaties rapportgroepsnaam/rapportnaam alleen de ontbrekende worden geïmporteerd. Bestaande kaarten in tbrapporten worden NIET overschreven.

Bij de tweede keuze worden de bestaande combinaties rapportgroepsnaam/rapportnaam dus WEL overschreven.

Bij de derde keuze worden de bestaande combinaties rapportgroepsnaam/rapportnaam geïmporteerd, maar niet overschreven, omdat de geïmporteerde rapportnaam een (1) achter de naam krijgt.

Ontbrekende groepsnamen worden zo nodig aangemaakt.

#### Importeren uit export_sjablonen.xml

Het programma zal in een vervolgscherm vervolgens vragen de te importeren sjabloongroep te bevestigen (er is geen andere keuze mogelijk).

Het programma zal in een vervolgscherm vervolgens vragen het te importeren sjabloon te bevestigen (er is geen andere keuze mogelijk).

Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe sjabloon toevoegen
- nieuwe sjabloon toevoegen en al bestaande overschrijven
- alles toevoegen (bestaande krijgen naam(1))
- bij bestaande sjabloon de sjabloonfile inlezen

De eerste keuze betekent dat van de aangewezen combinatie sjabloongroepsnaam/sjabloonnaam/module alleen de ontbrekende worden geïmporteerd. Bestaande kaart in tbdocumenten wordt NIET overschreven.

Bij de tweede keuze wordt de bestaande combinatie sjabloongroepsnaam/sjabloonnaam/module dus WEL overschreven.

Bij de derde keuze worden de bestaande combinatie sjabloongroepsnaam/sjabloonnaam/module geïmporteerd, maar niet overschreven, omdat de geïmporteerde sjabloonnaam een (1) achter de naam krijgt.

De vierde keuze behelst dat bij een bestaande combinatie sjabloongroepsnaam/sjabloonnaam/module ALLEEN de sjabloonfile (dus het MS-Word/ODT document in de kolom dvtemplatebase64) wordt gewijzigd.

Ontbrekende groepsnaam wordt zo nodig aangemaakt.

#### Importeren uit export_screencolumns.xml

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren klassen.

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren schermkolomdefinities bij de aangevinkte klassen.

Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe schermkolomdefinities toevoegen
- nieuwe schermkolomdefinities toevoegen en al bestaande overschrijven
- XML inlezen bij al bestaande kolomdefinities
- XML inlezen bij al bestaande kolomdefinities, enkel als deze leeg is

De eerste keuze betekent dat van de aangewezen schermkolomdefinities alleen de ontbrekende worden geïmporteerd. Bestaande schermkolomdefinities worden NIET overschreven.

Bij de tweede keuze worden de bestaande schermkolomdefinities dus WEL geheel overschreven.

Bij de derde keuze worden bij bestaande schermkolomdefinities ALLEEN de xml overschreven (dus de kolom dvscreenxml).

Bij de vierde keuze worden bij bestaande schermkolomdefinities ALLEEN de xml overschreven (dus de kolom dvscreenxml) als deze NIET gevuld is.

Bij het importeren van een schermkolomdefinitie wordt de sysstandaardcategorie (indien aanwezig) niet meegenomen.

#### Importeren uit export_queries.xml

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren groepen.

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren queries bij de aangevinkte klassen.

Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe queries toevoegen
- nieuwe queries toevoegen en al bestaande overschrijven

De eerste keuze betekent dat van de aangewezen queries alleen de ontbrekende worden geïmporteerd. Bestaande queries worden NIET overschreven.

Bij de tweede keuze worden de bestaande queries dus WEL geheel overschreven.

#### Importeren uit export_processen.xml

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren groepen (modules).

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren processen bij de aangevinkte klassen.

Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe processen toevoegen
- nieuwe processen toevoegen en al bestaande overschrijven
- alles toevoegen, bestaande krijgen naam(1)

De eerste keuze betekent dat van de aangewezen processen alleen de ontbrekende worden geïmporteerd. Bestaande processen worden NIET overschreven. Het gaat hier om de combinatie procesnaam en groep.

Bij de tweede keuze worden de bestaande processen dus WEL geheel overschreven.

Bij de derde keuze worden de bestaande combinatie groep/procesnaam WEL geïmporteerd, maar niet overschreven, omdat het geïmporteerde proces een (1) achter de naam krijgt.

Bij het importeren van processen wordt (indien aanwezig) de default behandelaar en/of het team die gekoppeld is aan onderliggende processtappen ook overgenomen. Deze wordt echter alleen ingevuld als de behandelaar of team ook bestaat in het systeem waar geïmporteerd wordt. Als dit niet het geval is wordt dit veld dus niet gevuld.

#### Importeren uit export_configuratie.xml

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren secties.

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren items bij de aangevinkte secties. Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe items toevoegen
- nieuwe items toevoegen en al bestaande overschrijven

De eerste keuze betekent dat van de aangewezen items alleen de ontbrekende worden geïmporteerd. Bestaande items worden NIET overschreven.

Bij de tweede keuze worden de bestaande items dus WEL overschreven. Let op: dat geldt ook voor de items waarvan de kolom _Tekst_ (dvstring) bij export leeg is gemaakt (de asterisken).

#### Importeren uit export_standaardtabellen.xml

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren categorieën (indien leeg vink dan de lege groep aan).

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren coderingen bij de aangevinkte categorieën.

Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe standaardtabellen toevoegen
- nieuwe standaardtabellen toevoegen en al bestaande overschrijven

De eerste keuze betekent dat van de aangewezen standaardtabelcoderingen alleen de ontbrekende worden geïmporteerd. Bestaande kaarten in tbsysstandardtable worden NIET overschreven.

Bij de tweede keuze worden de bestaande kaarten in tbsysstandardtable en de bijbehorende kaarten in tbsysstandardbutton dus WEL overschreven.

#### Importeren uit export_emailsjablonen.xml

Het programma zal in een vervolgscherm vervolgens vragen de te importeren sjabloongroep(en) te bevestigen (er is geen andere keuze mogelijk).

Het programma zal in een vervolgscherm vervolgens vragen de te importeren sjablonen te bevestigen (er is geen andere keuze mogelijk).

Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe emailsjablonen toevoegen
- nieuwe emailsjablonen toevoegen en al bestaande overschrijven
- alles toevoegen (bestaande krijgen naam(1))
- bij bestaande emailsjablonen het onderwerp en body van de emailsjabloon inlezen

De eerste keuze betekent dat van de aangewezen combinatie sjabloongroepsnaam/sjabloonnaam/module alleen de ontbrekende worden geïmporteerd. Bestaande kaart in tbemailsjabloon wordt NIET overschreven.

Bij de tweede keuze wordt de bestaande combinatie sjabloongroepsnaam/sjabloonnaam/module dus WEL overschreven.

Bij de derde keuze worden de bestaande combinatie sjabloongroepsnaam/sjabloonnaam/module geïmporteerd, maar niet overschreven, omdat de geïmporteerde sjabloonnaam een (1) achter de naam krijgt.

De vierde keuze behelst dat bij een bestaande combinatie sjabloongroepsnaam/sjabloonnaam/module ALLEEN het onderwerp en de body worden gewijzigd.

Ontbrekende groepsnaam wordt zo nodig aangemaakt.

#### Importeren uit export_container_rapportages.xml

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren containers.

Het programma zal in een vervolgscherm vervolgens vragen een keuze te maken uit de mogelijk te importeren rapportages bij de aangevinkte containers.

Vervolgens vraagt OpenWave te kiezen voor één van onderstaande mogelijkheden:

- nieuwe rapportages toevoegen
- nieuwe rapportages toevoegen en al bestaande overschrijven
- alles toevoegen (bestaande rapportages krijgen naam(1))
- alles toevoegen (bestaande containers krijgen naam(1))

De eerste keuze betekent dat van de aangewezen combinaties containernaam/rapportagenaam alleen de ontbrekende worden geïmporteerd. Bestaande kaarten in tbexportcontainer worden NIET overschreven.

Bij de tweede keuze worden de bestaande combinaties containernaam/rapportagenaam dus WEL overschreven.

Bij de derde keuze worden de bestaande rapportages geïmporteerd, maar niet overschreven, omdat de geïmporteerde rapportagenaam een (1) achter de naam krijgt.

Bij de vierde keuze worden de bestaande containers geïmporteerd, maar niet overschreven, omdat de geïmporteerde containernaam een (1) achter de naam krijgt.
