# OpenWave Documentatie

Welkom op de OpenWave documentatie.

## Technische specificaties

Met de ingang [Technische specificaties](/docs/techniek/index.md) kan de organisatie zelf nagaan of hun installatie van OpenWave met alle plug-ins en koppelingen up to date is. In OpenWave, in het beheerportaal, eerste kolom, geeft de tegel Versie-informatie namelijk live de stand van zaken weer van de in gebruik zijnde componenten.

## Applicatiebeheer

De ingang [Applicatiebeheer](/README.md) is de ingang voor functioneel beheerders en voor de OpenWave supportafdeling van REM zelf. Het onderdeel applicatiebeheer is dus niet gericht op eindgebruikers. De belangrijkste functie is dat alle instellingen die het gedrag van OpenWave kunnen beïnvloeden, gevonden kunnen worden, waarbij voor de meeste instellingen er diverse toegangswegen zijn.

## Begrippen met betrekking tot userinterface

### Vormgeving

Het kleurthema van OpenWave is instelbaar en kijkt naar de waarde van kolom _Tekst_ van configuratie instelling _Sectie: PreInlog, Item: ApplicationColor_ voor het bepalen van de kleuren van de OpenWave omgeving. Default is de kleur blauw (kolom _Tekst_ heeft waarde blue). Andere opties zijn groen, rood, paars of oranje.
Vanaf 1.29 is staat OpenWave qua vormgeving in de zogenaamde legacy modus (_Sectie: PreInlog, Item: ApplicationLegacy_ is aangevinkt). Dit is de vormgeving van OpenWave zoals de gebruiker gewend is. Het uitvinken van de legacy modus resulteert in weergave van OpenWave in de nieuwe vormgeving. In versie 1.29 worden de puntjes op de i gezet voor de nieuwe vormgeving, vandaar dat default nog de huidige vormgeving aan staat. Voor de kleurinstellingen en het kunnen switchen tussen legacy modus en nieuwe vormgeving zie pagina [Sectie PreInlog](//instellen_inrichten/configuratie/sectie_prelog.md).

### Portaal

Via diverse portalen geeft OpenWave toegang tot lijst- en detailschermen met data. Een portaalscherm is een tegeltableau. Achter een tegel bevindt zich in de meeste gevallen een lijst van gegevens bijvoorbeeld _alle openstaande omgevingszaken_ of _mijn uit te voeren collegiale toetsen_. Door middel van het toekennen van rechten en/of het toekennen van tegels aan medewerkers kan voor elke gebruiker een bepaald portaal er anders uitzien.

Het belangrijkste portaal is het openingsportaal. Na het inloggen wordt altijd dit portaal geopend. Daarnaast zijn er zaakportalen. Deze zaakportalen geven toegang tot de gegevens van één zaak. De beheerportalen, het operationsportaal en portaal Service centrum zijn portalen waar alleen een functioneel beheerder recht op heeft. De beheerportalen geven toegang tot onder meer het vullen van coderingstabellen, maken van rapportages, maken van documentsjablonen, maken van schermen en filters en logschermen.
Het operationsportaal geeft toegang tot import- en export operaties van gegevens zoals _inlezen BAG-extract_ of _maken van vernietigingslijsten_ of _inlezen, exporteren van rapportages en processen_. In het Service centrum kan men bepaalde loggings ophalen, sessie- en versie informatie inzien.

### Sidebar

De sidebar beheert de geopende portaalschermen als vervanging van browsertabbladen in een weg te schuiven balk aan de linkerzijde van het scherm.

### Lijstscherm

Alle lijstschermen in OpenWave hebben dezelfde basis lay-out: een knoppenbalk linksonder, een titel aan de bovenkant, een zoekeditbox rechtsonder, een filteroptie rechtsboven, paging rechtsboven. Afhankelijk van instellingen, rechten, zijn al deze features wel of niet zichtbaar en enabled voor de gebruiker.

In de lijst zelf is het klikken op een geselecteerde regel een trigger voor een vervolgactie: meestal het openen van een detailscherm.
De bepaling van de kolommen van een lijst is in principe aanpasbaar door een functioneel beheerder. De lijsten zijn gebaseerd op views.

### Detailscherm

Met het detailscherm wordt het formulier bedoeld met de gegevens van één record, dus bijvoorbeeld van één omgevingszaak of van één legesregel. Alle detailschermen in OpenWave hebben dezelfde basis lay-out: een knoppenbalk linksonder, een titel aan de bovenkant, knoppen achter kolommen op het scherm, een editschuif rechtsboven, een menulijstje rechtsboven. Afhankelijk van instellingen, rechten, zijn al deze features wel of niet zichtbaar en enabled voor de gebruiker.

De gegevens in een detailscherm zijn ingedeeld in blokken. Mutaties vinden per editbox (dus per gegeven) direct plaats: er is dus geen knop om een geheel formulier te wijzigen of op te slaan. Wel kan met de zogenaamde editschuif rechtsboven een geheel formulier in de wijzigmodus worden gezet. De bepaling van de kolommen en blokken van een detailscherm is in principe aanpasbaar door een functioneel beheerder.

### Wizard

Achter een tegel of met een knop kan een zogenaamde wizard worden gestart. Deze wizards bestaan uit één of meer achtereenvolgende schermen binnen een wizardvenster waarmee in de meeste gevallen een ingewikkelde invoerroutine wordt ondersteund. Bovenaan elk scherm staat een titel; onderaan elk scherm de knoppen _annuleren, volgend/vorig scherm of uitvoeren_. Er zijn wizards voor het aanmaken van nieuwe kaarten, voor het kiezen en uitvoeren van een rapport, voor het maken van een document, het berekenen van leges en zo verder. In de regel zijn deze wizards vast geprogrammeerd en dus niet aanpasbaar.

## Indeling applicatiebeheer

De Dokuwiki-handleiding onder deze ingang applicatiebeheer is als volgt ingedeeld:

- [Functionaliteiten](docs/functionaliteiten/README.md)
- [Instellen/inrichting](docs/instellen_inrichten/README.md)
- [Probleemoplossing](docs/probleemoplossing/README.md)
  - [portalen en moduleschermen](docs/probleemoplossing/portalen_en_moduleschermen/README.md)
  - [module overstijgende schermen](docs/probleemoplossing/module_overstijgende_schermen/README.md)
  - [programmablokken](docs/probleemoplossing/programmablokken/README.md)

### Functionaliteiten

Onder dit lemma worden diverse verwijzingen naar andere lemma's gegroepeerd onder logische zoektermen. Zo kan de zoekterm _email_ op heel veel plekken in de handleiding voorkomen. Er zijn algemene email-instellingen, er zijn email-instellingen die met de post- en verzendstroom van doen hebben, er zijn email-instellingen die met adviezen te maken hebben en zo verder. Deze functionaliteiten-ingang bestaat uit doorverwijspagina's op grond van goede beschrijvingen.

### Instellingen/Inrichting

Onder dit lemma worden instellingen gegroepeerd onder diverse benamingen en van verschillende orde:

- de bepalende beheerportaal-tabellen zoals de portaaldefinitie-tabellen, medewerkerstabel, compartimententabel, zaaktypetabellen, adressoorten
- Configuratie-Instellingen. Naar deze tabel wordt in handleiding veelvuldig verwezen bijv. _Indien Getal1 van de instelling Sectie: X en Item: Y de waarde 1 heeft dan…._
- Voor applicatiebouwers: Hoe schermen, knoppen, actions, query's en relaties te definiëren
- het maken van sjablonen voor documenten en rapportages
- het maken van processen en processtappen, checklijsten

### Portalen en moduleschermen

Onder deze ingang worden alle portalen en tegels opgesomd die in de officiële OpenWave releases zijn uitgeleverd. Elke tegel is te reconstrueren op grond van de geboden informatie. Bij een aantal tegels uit het openingsportaal is een onderliggende lemma _lijstscherm_ gemaakt. Dit gaat over de bijzonderheden van lijst die getoond wordt achter de betreffende tegel (welke view, welke instellingen van belang zijn, betekenis icoontjes).

Voor de zaakportalen (zoals omgeving en handhavingen) is een onderliggend lemma _detailscherm_ toegevoegd. Dit gaat over de bijzonderheden van het detailscherm van een zaak: instellingen die bepalen welke blokken en kolommen wel of niet zichtbaar zijn, berekeningswijzen, muteerrechten en de zichtbaarheid en actief zijn van triggers (knoppen) op het scherm.

#### Module-Overstijgende schermen

Bij elke hoofdzaak (zoals omgevingszaak, een handhavingszaak) worden gegevens genoteerd in een 1 op n situatie. Veel van deze (dochter-)tabellen worden in meerdere hoofdzaken gebruikt. Bijvoorbeeld zowel bij handhavingszaken als bij omgevingszaken als bij APV/overige zaken kunnen adviezen uitstaan en kunnen processen zijn gekoppeld. Zij delen daarom - ongeacht de module waarin zij worden aangesproken - dezelfde schermen met dezelfde userinterface.

Ook het interne kaartscherm is zo'n module-overstijgend scherm alhoewel daar geen gemeenschappelijke tabel aan ten grondslag ligt. Deze schermen worden hier besproken in hun lijst- en detailvariant met betrekking tot de instellingen die bepalen welke blokken en kolommen wel of niet zichtbaar zijn, welke berekeningswijzen gelden, welke muteerrechten nodig zijn, en hoe de zichtbaarheid en het actief zijn van triggers (knoppen) op het scherm geregeld is.

### Programmablokken

Onder dit lemma worden de programma-flow en de instellingen besproken die te maken hebben met de uitvoering van complexe taken. Zoals het aanmaken van een nieuwe zaak, het inlezen van OLO/DSO, het koppelen van een zaak met extern zaak/DMS, het ophalen en plaatsen van documenten, het maken van een document, het vernietigen van zaken en documenten.

## Begrippen met betrekking tot indeling van zaken

### Modules

OpenWave bestaat al sinds 1990 (in een dos-desktop dbaseIII versie) en is al die jaren - met behoud van geschiedenis - doorgegroeid tot huidige Cloud-versie onder een Postgresql database. Die oude geschiedenis is terug te vinden in de indeling van VTH-zaken, zoals die voor de WABO en ver voor de Omgevingswet en ver voor het zaakgericht werken, gemeen was. Die oude indeling was meer afdelingsgericht: de bouw/sloop, de APV, de toezicht/handhaving, de horeca, de inrichtingen met milieuvergunningen en de afdeling die informatievragen verzorgt.

Met de WABO kwam daar een nieuwe indelingscategorie bij: de **omgevingszaken**.
Zaken in OpenWave zijn nog steeds in deze modules op te delen, maar dat hoeft niet meer. Er zijn organisaties die nog maar twee modules gebruiken (handhaving en omgeving) en er zijn organisaties die maar één kaartenbak/module gebruiken voor alle VTH-zaken. Deze laatste trend wordt steeds beter door de OpenWave programmatuur ondersteund.

In deze handleiding komt het begrip module om bovenstaande reden vaak terug. Rechten en instellingen zijn heel vaak module gebonden. Vandaar.

De oude benamingen dekken dus niet altijd de nieuwe lading. De module omgevingszaken heeft als hoofdtabel tbomgvergunning, maar hier kunnen dus best toezichtzaken en horecazaken in opgenomen zijn. Omdat functioneel beheerders kopteksten en schermen zelf kunnen beïnvloeden, merkt de eindgebruiker uiteindelijk niets van de archaïsche benamingen op databaseniveau. Om dezelfde reden zijn in deze documentatie slechts sporadisch schermvoorbeelden gebruikt.

### Hoofdzaken

De zaken die in de hoofdtabellen van de genoemde modules geregistreerd zijn noemen we de hoofdzaken.

![](docs/img/hoofdzaken.png){ width=800 class="media" loading="lazy" }

- De module omgevingszaken heeft als hoofdtabel tbomgvergunning. Deze tabel was gericht op zaken die via de OLO binnenkomen (WABO), maar is geëvolueerd naar een tabel waarin ook onder meer toezichtzaken en klachten en APV zaken kunnen worden geregistreerd.
- De module handhavingszaken heeft als hoofdtabel tbhandhavingen. Deze tabel is gericht op zaken die te maken hebben met bestuursdwang.
- De module APV/Overige zaken heeft als hoofdtabel tbovvergunningen. Deze tabel is gericht op APV-zaken.
- De module Horecazaken heeft als hoofdtabel tbhorecavergunningen. Deze tabel is gericht op een bijzonder soort APV-zaken: namelijk horeca. Een horecazaak dient altijd verbonden ter zijn aan een inrichting.
- De module InfoAanvragen heeft als hoofdtabel tbinfoaanvragen.
- De module Milieu/Gebruik heeft als hoofdtabel tbmilvergunningenn. Deze tabel is gericht op (pre Wabo) milieuvergunnings- en gebruiksvergunningzaken. Een milieu/gebruik zaak dient altijd verbonden ter zijn aan een inrichting.
- De module Bouw/Sloop heeft als hoofdtabel tbbouwvergunningenn. Deze tabel is gericht op (pre Wabo) bouw- en sloopvergunningzaken.
- De module Inrichtingen heeft als hoofdtabel tbmilinrichtingen. Deze tabel is voor het vastleggen van inrichtingendossiers. Voor zaakgericht werken blijft het containerbegrip inrichtingen een lastige. Ook omdat dat bericht met de nieuwe omgevingswet is gesneuveld. OpenWave blijft vooralsnog de module inrichtingen gebruiken. Daaraan kunnen zaken uit de andere hoofdtabellen worden gerelateerd en kunnen externe veiligheidscontouren worden gekoppeld naast vee/stallen, afvalstromen enzovoorts.

Vanuit het openingsportaal wordt met evenzovele tegels als ingestelde modules toegang verkregen tot lijsten van hoofdaken. Vanuit een zakenlijst kan de gebruiker doorklikken naar een zaakportaal. Een zaakportaal geeft ook door middel van tegels, toegang tot dochtertabellen bij een zaak.

### Dochtertabellen

Bij elke hoofdzaak worden gegevens genoteerd in een 1 op n situatie. Bijvoorbeeld: een zaak heeft 1 of meer behandelaars, heeft 1 of meer contactadressen, heeft 1 of meer documenten, heeft 1 of meer processtappen. Deze 1 op n gegevens worden genoteerd in een aantal dochtertabellen zoals tbadviezen, tbtermijnbewstappen (processtappen), tbinbehandelingbij, tbinspecties (toezicht) en tbcorrespondentie (geregistreerde documenten). Maar ook: tbmilopslag (externe veiligheid) en tbmilafvalstoffen en tbmilstal (stallen/vee) bij inrichtingen.

Een aantal van deze tabellen wordt gedeeld door meerdere hoofdzaken. Zij delen in dat geval dezelfde schermen: de module-overstijgende schermen. Een greep uit de mogelijkheden:

![deelzaken](docs/img/deelzaken.png){ width=800 class="media" loading="lazy" }

### Deelzaken

Een aantal dochtertabellen dat module-overstijgende schermen heeft, wordt in deze handleiding als deelzaak gekarakteriseerd. Dat zijn de deelzaken:

- Toezicht/inspecties met de tabel tbinspecties
- de Adviezen met de tabel tbadviezen
- de Bezwaar/beroepzaken met de tabel tbbezwaarberoep

Deze tabellen zijn namelijk voorzien van een kolom waarin de zaak-identifier van een extern zaak/DMS kan worden opgenomen. Alle hoofdzaken hebben deze kolom vanzelf. Gevolg is dat deze deelzaken met de StUF zaak/DMS koppeling ook als zaak in een extern zaak/DMS kunnen worden opgenomen: en wel als deelzaak van de bijbehorende hoofdzaak. Nogmaals, dit hoeft dus niet. Met name de inspecties en bezwaarberoepzaken kunnen ook als hoofdzaak worden opgenomen (in tbomgvergunning). Grote voordeel om bijvoorbeeld inspecties als dochtertabel te implementeren (al of niet gebruikmakend van Stuf zaak/DMS) is dat deze dan direct via het zaakportaal van de hoofdzaak te benaderen zijn.

## Begrippen met betrekking tot bevoegdheid

### Compartimentsrechten

Een compartiment is gedefinieerd als een combinatie van een of meer bevoegde gezagen die binnen een OpenWave-implementatie een bepaalde set van zaaktypes afhandelen voor die gezagen. Een gebruiker is al of niet lid van een compartiment. Het begrip _host_ slaat op de organisatie waarbinnen het compartiment gedefinieerd is. De functionele beheerder van de host is degene die alle instellingen voor het compartiment doet.

Als een medewerker lid is van een compartiment kan deze alleen zaken beheren die vallen onder dat compartiment. Bij de compartimentsdefinitie zijn tal van instellingen die dus alleen gelden voor zaken die spelen onder dat compartiment. Zo kan een compartiment documenten op een andere plek opslaan dan de host, andere sjablonen gebruiken, andere processen definiëren.

### Functionele rechten

Van een ander typen zijn de functionele rechten, die per module en daarbinnen ook per dochtertabel zijn georganiseerd. Het gaat hier om autorisaties als wijzigrecht en of verwijderrecht op adviezen onder de module omgevingszaken of insert rechten op een nieuwe handhavingszaak.

### Beheerrechten

Voor toegang tot de tegels op de beheerportalen, het operationsportaal en portaal Service centrum geldt dat de medewerker in de medewerkerstabel in de kolom dnbeheerniveau minimaal de waarde 99 moet hebben.
