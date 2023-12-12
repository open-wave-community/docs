# Detailscherm Processtap

De schermidentifier is _MDDC_geefProcesDetail.xml_

Dit scherm kan worden aangeroepen vanuit de lijst met _Processtappen_, mits doorgekozen wordt vanuit een stap die enabled is (zie kopje Disabled/enabled bij beschrijving lijst processtappen).

## Probleem

Het scherm geeft een foutmelding:

- er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/instellen_inrichten/schermdefinitie/README.md)) die niet valide is
- de inlogger moet kijkrechten hebben op de processtappen bij betreffende hoofdzaak (bijvoorbeeld zichtbaar-rechten op proces/checklijst bij omgeving).

## Disabled/enabled

Sommige rijen kunnen disabled zijn (zie bij Lijst Processtappen) en die rijen zijn in het detailscherm niet benaderbaar.

## Muteren

Sommige rijen kunnen disabled zijn (zie bij Lijst Processtappen) en die rijen zijn in het detailscherm niet benaderbaar en dus niet muteerbaar.

Indien enabled geldt dat de kaart muteerbaar is indien:

- de inlogger wijzigrechten heeft op de adviezen bij betreffende hoofdzaak
- en die bovenliggende hoofdzaak niet is geblokkeerd
- en de editschuif aan staat
- en - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de hoofdzaak bevatten en de gemeente waar de omgevingszaak speelt
- en - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar de hoofdzaak speelt in geen enkel compartiment voorkomen
- en - indien de instelling _Sectie: Termijnbewaking_ en _Item: AfgehandeldStapNietMuteerbaar_ aangevinkt is - dan moet de afgehandelddatum nog leeg zijn. Dit kan overruled worden wanneer de inlogger geautoriseerd is om processen te verwijderen OF wanneer de inlogger het overrule afhandeldatum-recht heeft (zie ook hieronder bij subkopje _Afgehandeld datum_).

Voor de kolommen **streefdatum en omschrijving** geldt dat zij muteerbaar zijn indien in het beheerportaal-Nieuw (tegel _Processen_) bij de betreffende stap de eigenschappen _streefdatum aanpasbaar_ en _naam/omschrijving aanpasbaar_, aangevinkt waren/zijn op het moment dat het proces aan de zaak werd toegevoegd.

Het **blok Voortgang** is alleen zichtbaar indien de volgende termijnstap afhankelijk is van een ja/nee-stap (afvinkstap). De betreffende ja/nee stap kan in dit blok worden aangevinkt of uitgevinkt.

Voor de dropdownlijst met **staat gepland voor (persoon)** geldt het volgende:

- de kolom is alleen zichtbaar indien de instelling _Sectie: Termijnbewaking_ en _Item: Voorwiezichtbaar_ is aangevinkt
- de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
- en de medewerker moet in dienst zijn
- en het vakje _interne medewerker_ moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap _overrule compartiment_ aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

Voor de dropdownlijst met **staat gepland voor team** geldt het volgende:

- de kolom is alleen zichtbaar indien de instelling _Sectie: Termijnbewaking_ en _Item: teamzichtbaar_ is aangevinkt
- het team moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger.

### Afgehandeld datum

Voor de afgehandeld datum geldt dat deze in principe muteerbaar is tenzij in het beheerportaal-Nieuw onder tegel _Processen_ bij deze stap is aangekruist _Afhandeldatum niet rechtstreeks in te vullen (maar via action of invoerkolom)_. In dat geval zal de afgehandeld datum van deze processtap niet handmatig door de inlogger kunnen worden aangepast. Het vullen geschiedt dan bijvoorbeeld door de uitvoering van een action of het vullen van een extra invoerkolom (zie hieronder).

> [!WARNING] > **Let op:** indien de inlogger geautoriseerd is om processtappen te verwijderen OF het proces overrule afhandeldatum-recht heeft, dan kan hij/zij WEL de afgehandeld datum muteren (tenzij bovenliggende zaak is geblokkeerd).

### Blok action

Het blok _Action_ is zichtbaar indien aan de processtap een action is gekoppeld (beheertegel _Processen_), zie definitie [Termijnstappen](/instellen_inrichten/inrichting_processen/termijnstappen.md).

Met het uitvoeren van de action kan in een aantal gevallen worden geregeld dat automatisch de afgehandeld datum wordt gevuld. De knop die de action triggert is alleen enabled bij een lege afhandeldatum. Indien de action _startwizard(maaknieuwezaak)_ wordt aangeroepen teneinde een vervolgzaak te kiezen, zal automatisch een groep (tbgroepvergunning) worden aangemaakt, die de vervolgzaak verbindt aan de zaak waar de processtap aan is gekoppeld (als deze zaak waar de processtap aan is gekoppeld al aan een groep was verbonden, dan wordt de vervolgzaak ook aan deze bestaande groep verbonden).

### Hoe werkt de action onder water?

Dee action bij de wizardknop in blok action is standaard als volgt gedefinieerd in het detailscherm (in de mddc_geefprocesdetail.xml): %query(termijnstappen_mddc_getdvaction,%keypointer%)%. Dit is een systeemquery die door Openwave wordt beheerd.

OpenWave evalueert deze query. Deze query vervangt de action die bij de aanmaak van de termijnstappen overgenomen is vanuit tbprocitems (in de kolom dvaction) bij de betreffende termijnstap waarbij de variabelen %keypointer% en %keyparent% worden vervangen met hun echte waardes.

_Voor evalutie_ bijvoorbeeld:

startWizard(maakDocument,6578,tbdocumenten;;tbomgvergunning;%keyparent%,W)

_Na evaluatie_:

startWizard(maakDocument,6578,tbdocumenten;;tbomgvergunning;85842,W)

en vervolgens wordt de wizard gestart waarbij in dit voorbeeld een brief op grond van documentsjabloon met dnkey 6578 wordt gemaakt.

Wanneer in de action na evaluatie nog een query aanwezig, dan wordt deze recursief alsnog geëvalueerd.

Bijvoorbeeld _na eerste evaluatie_:

startWizard(maakDocument,%query(docsjabloonperzaaktype,%keyparent%)%,tbdocumenten;;tbomgvergunning;%keyparent%,W)

Dan _na tweede evaluatie_:

startWizard(maakDocument,8890,tbdocumenten;;tbomgvergunning;85842,W)

### Blok extra invoerkolommen

Het blok _Extra invoerkolommen_ is zichtbaar indien bij de processtap minimaal één extra invoerkolom is gedefinieerd (beheertegel [Processen](/probleemoplossing/module_overstijgende_schermen/processen/README.md) ), zie definitie [Termijnstappen](/instellen_inrichten/inrichting_processen/termijnstappen.md). Per processtap kan aldaar gedefinieerd worden of er extra invoerkolommen bij de stap actief worden. Er zijn 5 mogelijkheden: een datum, een string (max lengte 200), een dropdown (max lengte 100), een geheel getal of een decimaal getal. Bij de definitie van deze kolommen kan per kolom aangegeven worden dat het wijzigen van een waarde tot gevolg heeft dat de afgehandeld datum van de stap wordt gevuld (met de systeemdatum).

### Checklistitems

Het lijstje met checklistitems is alleen gevuld indien er checklistitems bestaan die gekoppeld zijn aan de betreffende processtap.

De schermidentifier is MDLC_getProcItemCheckList.xml.

Deze checklistitems worden automatisch aangemaakt bij het nieuw invoegen van een proces (zie [Checklijstitems](/probleemoplossing/module_overstijgende_schermen/checklijsten/lijst_checklistitems.md)).

De kolom status van dit checklistscherm is muteerbaar indien:

- de inlogger wijzigrechten heeft op de processtappen bij betreffende hoofdzaak (bijvoorbeeld wijzigrechten op proces/checklijst bij omgeving) en
- die bovenliggende hoofdzaak niet is geblokkeerd.
