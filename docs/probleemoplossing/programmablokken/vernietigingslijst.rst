Vernietigingslijst
==================

Via het beheerportaal-Nieuw kan met de tegel *Operations* doorgeklikt
worden naar het Operationsportaal. Daarin is de tegel
*Vernietigingslijst* opgenomen. In deze lijst staan de zaken klaar die
vernietigd kunnen worden op grond van de bewaartermijnen ingegeven bij
de combinatie zaaktype en resultaat. Daartoe wordt de tabel
tbtevernietigen gevuld met daarin de verwijzingen naar de te vernietigen
zaken. Het fysiek vernietigen betekent vernietigen van de zaken waarnaar
wordt verwezen in de lijst, waarvan de kolom *Akkoord inspecteur* een
gevulde datum heeft. Alle bijbehorende documenten worden daarbij ook
verwijderd in zoverre deze zich op de fileshare bevinden. Documenten die
in een DMS staan blijven onaangeroerd. OpenWave zendt geen verwijderzaak
bericht naar het DMS. De vernietigingstabel kan alleen door middel van
de knoppen linksonder worden gevuld en geleegd.

Het gaat daarbij om zaken uit de hoofdtabellen (tbomgvergunning,
tbhandhavingen, tbovvergunningen en tbhorecavergunningen,
tbmilvergunningen) en om de deelzaken inspecties (tbinspecties). Bij
inspectiezaken gaat het alleen om die zaken waarvoor geldt dat de
aanleiding van de inspectie verwijst naar een kaart in tbinspaanleiding
met de eigenschap *is hoofdzaak* (dlhoofdzaak = 'T'). De bewaartermijnen
bij inspectiezaken komen uit de koppeltabel tbaardbesuitsoortinsp
(tbaardbesluit en tbinspaanleiding) die benaderd wordt vanuit de
detailpagina van een soort inspectietraject (tbinspaanleiding) in
beheerportaal Zaakbeheer. Om de inspectiekaarten naar deze koppeltabel
te laten verwijzen bij het vullen van inspectieresultaat dient de kolom
*Getal1* van de aangevinkte instelling *Sectie: Inspecties en Item:
ResultaatVerplichtBijAfsluiten* de waarde 1 te hebben. Anders (wel
aangevinkt, maar een andere waarde dan 1) verwijst het
inspectieresultaat naar de tabel tbinspresulaat en die heeft geen
bewaartermijnen.

Bewaar/vernietig-informatie op detailpagina's per zaak
------------------------------------------------------

Behalve op vernietigingslijst is per zaak ook informatie te zien en te
beïnvloedden met betrekking tot de bewaartermijnen. Op de detailpagina
van een zaak kan het blok **TMLO** zichtbaar worden gemaakt. Dit gebeurt
door het aanvinken van de instellingen:

*Sectie: TMLO en Item: Omgeving* (en/of Item: *handhaving, horeca,
apv/overig, info, bouwsloop, milieugebruik*). Bij inspectiezaken is het
blok TMLO op de detailkaart vanzelf zichtbaar indien de
inspectieaanleiding de eigenschap *is hoofdzaak* heeft.

Op de detailkaart kan aangevinkt worden of de zaak eeuwig bewaard moet
blijven,. In dat geval zal die zaak nooit in de vernietigingslijst
terechtkomen. Zichtbaar is ook de bewaartermijn, zoals ingesteld bij de
combinatie zaaktype/resultaat. De gebruiker kan een afwijkende
bewaartermijn opgeven, die dus alleen voor de betrokken zaak van
toepassing is. Het berekende vernietigingsjaar is het jaar van de
optelling van de (afwijkende) bewaartermijn bij de triggerdatum. Welke
triggerdatum dat is wordt aangegeven door de kolom *bewaartrigger*. Die
kan zijn:

-  leeg: dan is er geen vernietigjaar te berekenen omdat bijvoorbeeld
   geen bewaartermijn is opgegeven bij de combinatie zaaktype/resultaat,
   of het vakje *eeuwig bewaren* is aangevinkt, of de zaak is nog niet
   afgesloten
-  I: dan is de *Ingetrokken na verlening* datum ingevuld bij de
   betreffende zaak
-  L: dan de de *verloop cq geldigtot* datum ingevuld bij de zaak
-  V: dan is de vervaldatum ingevuld bij de zaak
-  A: dan is de triggerdatum de *aanvang/startdatum* van de zaak (zo
   opgegeven bij combinatie zaaktype/resultaat)
-  E: dan is de triggerdatum de *besluit/afgehandeld/einddatum* van de
   zaak (zo opgegeven bij combinatie zaaktype/resultaat).

De berekende bewaartermijn die hier zichtbaar is kan bij omgevingszaken
nog afwijken van de werkelijke bewaartermijn, zoals deze bij de
vernietigingslijst wordt berekend. Dat heeft te maken met uitzonderingen
per activiteit/onderdeel (ook in te stellen bij combinatie
zaaktype/resultaat in beheerportaal Zaakbeheer).

Overigens zijn de ingetrokken_naverlenings_datum en de vervallen_datum
en verloopdatum (geldigtot) bij een omgevingszaak opgenomen in het blok
**Geldigheid** en dat blok is alleen zichtbaar indien het betreffende
zaaktype als soort procedure NIET is Toezicht, Cyclisch, Klacht, Melding
of Vooroverleg. Deze drie kolommen zijn niet van toepassing bij
Handhavingszaken en Infoaanvragen en ook niet bij deelzaak Inspecties.

Kolommen van de Vernietigingslijst
----------------------------------

-  De eerste kolom **dldocdelmislukt** (zonder label) kan gevuld zijn
   met een stopicoontje. Is dat het geval dan konden tijdens het proces
   van fysiek vernietigen van de betreffende zaak, één of meer
   documenten - om wat voor reden dan ook - niet verwijderd worden. De
   zaak is daarom ook niet verwijderd. De beheerder zal de documenten en
   zaak handmatig dienen te verwijderen. Indien de te vernietigen lijst
   opnieuw wordt samengesteld, wordt deze zaak overigens vanzelf weer
   opgenomen.
-  De kolom **blokkering** laat zien of de zaak geblokkeerd is. Bij het
   samenstellen van de lijst kijkt OpenWave of de instelling *Sectie:
   Vernietigen en Item: AlleenGeblokkeerde* aangevinkt is. Zo ja dan
   komen alleen geblokkeerde zaken op de lijst.
-  De **hoofdzaakcode** wordt altijd gevuld, ook als de regel slaat op
   een deelzaak inspecties (tenzij de inspectieregel gebaseerd is op een
   inspectie die alleen gekoppeld is aan een inrichting: in dat geval
   blijft de hoofdzaakcode leeg)
-  De **deelzaakcode** inspecties en de kolom **betreft deelzaak**
   worden alleen gevuld indien de vernietigingsregel slaat op een
   deelzaak inspecties.
-  Het **module** icoontje toont de herkomst van de zaak in module
   (Omgeving, Handhaving, Horeca, Info-aanvraag, APV/Overig
   Milieu/Gebruik of Bouw/sloop).
-  De kolom **compartiment** toont het compartiment waaronder de zaak
   valt. Voor alle bewerkingen op de lijst, maar ook voor het fysiek
   vernietigen van zaken van de lijst geldt dat alleen zaken meegewogen
   worden die onder hetzelfde compartiment vallen als die van de
   inlogger. Indien de inlogger dus NIET gelieerd is aan een
   compartiment (in tbmedewerkers) worden alleen zaken opgenomen/
   vernietigd die NIET onder een compartiment vallen. De lijst kan
   echter wel zaken uit verschillende compartimenten (leeg of gevuld)
   bevatten: dat betekent dat de lijst door evenzoveel beheerders is
   aangemaakt.
-  De kolom **triggerdatum** toont de datum van de zaak waarop de
   bewaartermijn is toegepast.
-  **soort trigger** slaat op de triggerdatum. Dat kan zijn:

   -  Ingetrokken: de datum *na_verlening_ingetrokken_datum* is bij de
      zaak gevuld
   -  Verlopen: de *verloop (geldig tot)_datum* is gevuld
   -  Vervaldatum: de *vervaldatum* is gevuld
   -  Startdatum: De triggerdatum is de *start/aanvangsdatum*
   -  Einddatum: de triggerdatum is *eind/besluit/afgehandeld/datum*.

-  De kolom **te vernietigen vanaf** is een berekende datum op grond van
   de bewaartermijn bij ofwel de combinatie zaaktype/resultaat, dan wel
   de afwijkende bewaartermijn per individuele zaak, opgeteld bij de
   start- of einddatum van die zaak (zie hieronder bij knop
   *Samenstellen lijst*). Indien kleiner dan de systeemdatum komt de
   zaak op de lijst.
-  **bewaartermijn in dagen** komt uit de kolom dnbewaardagen bij de
   combinatie zaaktype/resultaat. Bij omgevingszaken kan dit nog wat
   ingewikkelder liggen omdat afwijkingen op deze combinatie mogelijk
   zijn per activiteit/onderdeel. Zie hieronder bij knop *samenstellen
   lijst*.
-  **afwijkende bewaartermijn** komt uit de zaak zelf, indien hier een
   afwijking o de bewaartermijn is ingegeven.
-  **reden afwijking** is ook overgenomen uit de zaak zelf, maar indien
   de bewaartermijn is berekend bij een omgevingszaak op grond van
   afwijkingen op de bewaartermijn van de combinatie zaaktype/resultaat
   per onderdeel/activiteit, dan is dat hier zichtbaar met een asterisk.
-  **Te vernietigen vanaf**. De afwijkende bewaartermijn, dan wel de
   berekende bewaartermijn opgeteld bij de triggerdatum.
-  **Status** Kan zijn: ingetrokken (na verlening), Verlopen, Vervallen
   of anders het resultaat dat gekozen is bij de
   afhandel/besluit/eindedatum.
-  **Bevoegd gezag**. Dit is de kolom dvorganisatie uit de tabel tboin
   (beheerportaal-Nieuw) waarnaar per zaak wordt verwezen met:

   -  een rechtstreekse verwijzing via de kolom dnkeyoinbevgez (die weer
      automatisch gevuld wordt door DSO) op zaakniveau
   -  een indirect verwijzing bij het niet gevuld zijn van deze kolom
      dnkeyoinbevgez. Dit gaat via de gemeente-id (tabel 33) van de
      locatie waar de zaak speelt. Deze gemeente-id wordt opgezocht in
      de tabel tboin. DUS: een voorwaarde voor het goed functioneren van
      de vernietigingslijst is dat alle betrokken gemeentes van de
      organisatie een OIN-kaart hebben in de tabel tboin.

-  **gemeenteid** De gemeente-id van de gemeente waar de zaak speelt.
-  Datum **naar (archief) inspecteur**. De datum waarop een (selectie
   van) de lijst is uitgedraaid ter goedkeuring van de
   archiefinspecteur. Zie onder wizardknop *Samenstellen/bewerken
   vernietigingslijst*.
-  Datum **(archief) inspecteur akkoord**. De datum waarop een (selectie
   van) de lijst is voorzien van een datum waarmee aangegeven is dat de
   archiefinspecteur akkoord is met de vernietiging. Zie onder
   wizardknop *samenstellen/bewerken vernietigingslijst*. Zonder deze
   gevulde datum kan een item niet fysiek vernietigd worden vanuit deze
   lijst.
-  Kolom **Akkoord inspect. door**. Deze kolom is gevuld met de
   medewerkerscode van de inlogger die *Datum (archief) inspecteur
   akkoord heeft gevuld.*
-  Datum **Vakafdeling akkoord**. De datum waarop een (selectie van) de
   lijst is voorzien van een datum waarmee aangegeven is dat de
   vakafdeling akkoord is met de vernietiging. Zie onder wizardknop
   *samenstellen/bewerken vernietigingslijst*.
-  Kolom **Akkoord vakafdeling door**. Deze kolom is gevuld met de
   medewerkerscode van de inlogger die *Datum vakafdeling akkoord heeft
   gevuld*.

Knoppen onder aan de lijst
--------------------------

Vraagtekenknop: is al een proces bezig?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Deze knop geeft antwoord op vraag of een andere (beheer)medewerker op
dat moment al bezig is een vernietigingsproces uit voeren. Bij het
samenstellen van de lijst en ook bij het uitvoeren (dus vernietigen van
zaken van die lijst) wordt in de configuratietabel *Getal1* van de rij
met *Sectie: Operations en Item: Vernietiging* op 1 gezet. Daarmee wordt
voorkomen dat twee processen tegelijk kunnen starten. OpenWave zet deze
waarde automatisch weer op 0 als een proces wordt beëindigd.

Verversknop
~~~~~~~~~~~

Zowel het samenstellen van de lijst als het daadwerkelijk vernietigen
van zaken uit die lijst gebeurt door een zogenaamd runnable programma.
Dat betekent dat de gebruiker nadat het proces is gestart door kan gaan
met andere werkzaamheden. Onder water voert de runnable zijn taken uit.
Dat betekent ook dat de wijzigingen in de lijst niet voortdurend door
die runnable worden uitgeschreven. Met deze knop kan de lijst ververst
worden. De gebruiker kijkt naar de dan actuele situatie mits de
vraagtekenknop meldt dat er geen proces meer loopt.

Verwijderknop
~~~~~~~~~~~~~

Met deze -knop kan de inlogger de actieve zaak uit de lijst verwijderen.

Het gaat hierbij dus niet om het vernietigen en verwijderen van de
achterliggende zaak en documenten zelf.

Vernietigknop (vuilnisvat)
~~~~~~~~~~~~~~~~~~~~~~~~~~

Met deze knop worden alle zaken en documenten waarnaar in de lijst wordt
verwezen fysiek vernietigd, waarvoor geldt dat:

-  het compartiment overeenkomt met dat van de inlogger
-  de kolom ddakkoordinspecteur een gevulde waarde heeft.

Voor deze zaken gebeurt het volgende:

-  Per zaak wordt gekeken of er geregistreerde documenten zijn, die zich
   op de fileshare bevinden. Zo ja, dan worden deze één voor één
   vernietigd. Als de vernietigingsregel een inspectiezaak betreft, dan
   worden alleen die documenten vernietigd waarvoor geldt dat de
   tbcorrespondentie.dnkeyinspecties dezelfde waarde heeft als de
   inspectiekey die hoort bij vernietigingsregel.
-  Kan voor één of meer documenten de vernietiging niet uitgevoerd
   worden (om wat voor reden dan ook, bijv. is geopend door een
   gebruiker, of vernietigingsdatumvanaf van een deelzaakinspecties is
   later dan die van de hoofdzaak), dan wordt de betreffende zaak in de
   lijst gemarkeerd met dldocdelmislukt = 'T'. Zichtbaar met het
   stopicoon in eerste kolom, na afloop en/of verversen. Een document
   waarnaar verwezen wordt dat niet bestaat is geen reden voor
   mislukking. Een document dat geopend is met OnlyOffice (dat betekent
   altijd dat een kopie is geopend) is niet zichtbaar voor dit proces en
   wordt dus gewoon verwijderd.
-  Voor de zelfde zaak wordt vervolgens gekeken naar de NIET
   geregistreerde documenten. OpenWave kijkt hiertoe voor NIET deelzaken
   naar ALLE mappen genoemd in de instelling van *Sectie: Aanmaakmappen*
   voor de betreffende module. Voor inspectiedeelzaken wordt alleen
   gekeken naar de mappen waarin de constructie %inspnr% voorkomt voor
   de betreffende module.
-  Alle documenten op die mappen **en** alle submappen daarvan worden
   verwijderd. Ook hier geldt dat indien voor één of meer documenten de
   vernietiging niet uitgevoerd kon worden (om wat voor reden dan ook ),
   dat dan de betreffende zaak in de lijst gemarkeerd wordt met
   dldocdelmislukt = 'T'. Zichtbaar met het stopicoon in eerste kolom,
   na afloop en/of verversen.
-  Indien voor de zaak alle documenten succesvol zijn en de instelling
   *Sectie: Vernietiging en Item: AlleenDocumentenGeenZaken* **NIET** is
   aangevinkt dan:

   -  wordt een kaart aangemaakt in tbaudit met tabelnaam en pointer en
      inloggerscode en systeemdatum en wordt daarbij de kolom Dvlocation
      gevuld met *Vernietigingslijst*
   -  wordt de zaak zelf verwijderd (dus uit tbomgvergunning,
      tbhandhavingen, tbovvergunningen of uit tbisnpecties etc.) met
      alle aanhankelijke gegevens
   -  wordt de rij met de verwijzing naar de zaak uit de
      vernietigingslijst gehaald.

De zaken waarvoor één of meer documenten niet verwijderd konden worden
blijven dus bestaan. Zowel fysiek als de verwijzing in de
vernietigingslijst. De beheerder kan dit handmatig oplossen.

Zaken waarvoor ook in een DMS een relatie is, blijven in dat DMS bestaan
(ook de documenten in dat DMS blijven bestaan) terwijl ze in OpenWave
dus verwijderd worden.

Wizardknop: Samenstellen/bewerken vernietigingslijst
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met de wizardknop linksonder *Samenstellen/bewerken vernietigingslijst*
wordt een pagina getoond met de volgende doorkiesmogelijheden:

-  **Nieuwe lijst maken**. De bestaande items die voldoen aan
   compartiment worden eerst vernietigd!!!
-  kolom **Vakafdeling akkoord vullen** voor (gedeelte van) lijst
-  kolom **Naar Archiefinspecteur vullen** voor (gedeelte van) lijst
-  kolom **Archiefinspecteur akkoord vullen** bij items met gevulde Naar
   Archiefinspecteur voor (gedeelte van) lijst
-  kolom **Vakafdeling akkoord leegmaken** voor (gedeelte van) lijst
-  kolom **Archiefinspecteur leegmaken** voor (gedeelte van) lijst
-  kolom **Archiefinspecteur akkoord leegmaken** voor (gedeelte van)
   lijst
-  (gedeelte van) rijen van de lijst verwijderen

Alle keuzes slaan op het bewerken en maken van de lijst (dus bewerken
van de tabel tbtevernietigen): er worden met deze wizard geen
zaken/documenten fysiek verwijderd.

Wizardopties
------------

Wizardoptie: nieuwe lijst maken
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

De bestaande items die voldoen aan compartiment worden eerst
vernietigd!!!

Met deze keuze moet de gebruiker eerst:

-  één of meer modules moet aanwijzen (of combinaties van modules met
   deelzaak inspecties)
-  en vervolgens een of meer bevoegd gezagen uit tboin
   (beheerportaal-Nieuw), **waarvoor geldt dat
   tboin.dlvernietigingslijst op T staat** (niet alle OIN-organisaties
   zijn een gemeente of provincie). Belangrijk is dat alle betrokken
   gemeentes een kaart hebben in deze tabel waarvoor - naast het
   OIN-nummer/naam ook de kolom gemeenteid wordt gevuld, waarmee een
   relatie gelegd wordt met de locatie van de zaak en deze bevoegd gezag
   tabel indien in de zaak zelf niet rechtstreeks wordt verwezen naar
   tboin (dus als dnkeyoinbevgez leeg is).

Als module(s) en bevoegd gezag(en) bekend is dan worden **alle** items
(dus ook items voorzien van datum akkoord inspecteur) van de lijst
verwijderd waarvoor geldt dat:

-  indien de inlogger niet gelieerd is aan een compartiment, de kolom
   compartiment ook leeg is
-  indien de inlogger wel gelieerd is aan een compartiment, de
   compartimentsnaam gelijk is aan die van de inlogger (tbmedewerkers).

Het programma gaat vervolgens items aan de vernietigingslijst toevoegen
door alle zaken en inspectie-deelzaken te doorlopen waarvoor geldt dat:

-  de module overeenkomt met de aangevinkte module(s)
-  het compartiment overeenkomt met dat van de inlogger
-  het bevoegd gezag (direct of indirect via gemeente-id) overeenkomt
   met het aangevinkte bevoegde gezag(en)
-  de blokkeerdatum gevuld is indien de instelling *Sectie: Vernietiging
   Item: AlleenGeblokkeerde* aangevinkt is
-  de einddatum van de zaak gevuld is
-  de begindatum van de zaak gevuld is
-  het resultaat (aardbesluit) van die zaak gevuld is. Deze laatste
   restrictie geldt niet voor de infoaanvragen.

Per (deel)-zaak wordt eerst gekeken of de kolom *eeuwigbewaren* is
aangevinkt (detailpagina zaak in blok TMLO). Zo ja dan wordt de zaak
overgeslagen. Per zaak wordt vervolgens gekeken of er een individuele
afwijking is op de bewaartermijn. Deze afwijking staat in de kolom
dnafwijkingbewaarindagen ook in het blok **TMLO** op de detailkaart van
de zaak.

Geen individuele afwijking dan wordt op grond van het zaaktype en
resultaat (aardbesluit) de bewaartermijn opgehaald. Zie *blok gekoppeld
afhandeling/aard besluit* op het detailscherm van de tegels *Zaaktype*
in het beheerportaal *Zaakbeheer*. Voor inspecties zie *blok gekoppeld
aan afhandeling* op het detailscherm van de tegels
*Inspectietrajectsoorten* in het beheerportaal *Zaakbeheer*.

Indien er geen combinatie gevonden wordt, wordt de (deel)-zaak NIET
opgenomen in de vernietigingslijst, omdat dan de bewaartermijn onbekend
is. Bij de zaaktypes van de infoaanvragen zit de bewaartermijninformatie
op het detailscherm van het zaaktype zelf bij ontbreken van
resultaattabel.

Vervolgens wordt de gevonden (eventueel afwijkende) bewaartermijn
opgeteld bij de zogenaamde triggerdatum in de *te vernietigen vanaf
datum*. Die triggerdatum word per zaak als volgt bepaald:

-  de ingetrokkendatum: indien de datum *na_verlening_ingetrokken_datum*
   bij de zaak is gevuld (niet van toepassing bij Handhaving en Info,
   Inspecties)
-  anders de verloopdatum: indien de *verloop (geldig tot)_datum* is
   gevuld (niet van toepassing bij Handhaving en Info en Inspecties)
-  anders de vervaldatum: indien de *vervaldatum* is gevuld (niet van
   toepassing bij Handhaving en Info en Inspecties)
-  anders de start/aanvangdatum indien bij de betreffende combinatie
   zaaktype/resultaat bewaren vanaf Aanvang/startdatum is aangevinkt
-  anders de besluit/afgehandeld/einddatum indien bij de betreffende
   combinatie zaaktype/resultaat bewaren vanaf
   besluit/afgehandeld/einddatum is aangevinkt.

Dan geldt dat indien de berekende *te vernietigen vanaf datum* kleiner
of gelijk is aan de systeemdatum, dat dan de zaak toegevoegd wordt aan
de lijst.

Voor omgevingszaken kunnen uitzonderingen gelden per zaaktype/resultaat
op de bewaartermijn op grond van de onderdelen/activiteiten. Aan de
combinatie zaaktype- onderdeel/activiteit-resultaat kan namelijk ook een
bewaartermijn worden toegevoegd die exacter is dan die van het
zaaktype-resultaat alleen. Dit wordt geregeld in de tabel
tbomgbewaarresulttoest: een koppeltabel tussen tbaardbeslsoortzaak en
tbtoestemmingen. In het beheerportaal *Zaakbeheer* bij Zaaktypes
omgeving kan op regels van het blok *gekoppeld aan afhandeling/aard
besluit* van het detailscherm van het zaaktype doorgeklikt worden om per
activiteit/onderdeel een afwijkende waarde op te geven bij het
betreffende resultaat. De activiteiten/onderdelen komen uit de tabel
tbsrttoestemming (tegel *Soort activiteit/onderdeel* op beheerportaal
*Zaakbeheer*). Indien er meer dan één onderdeel/activiteit aan een
omgevingszaak is toegevoegd, dan geldt de hoogst gevonden bewaartermijn.
De kolom *reden afwijking* wordt gevuld met een asterisk.

Wizardoptie: kolom Naar Vakafdeling akkoord vullen voor (gedeelte van) lijst
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met deze keuze moet de gebruiker eerst:

-  één of meer modules moet aanwijzen
-  en vervolgens een of meer bevoegd gezagen uit tabel tboin
   (beheerportaal-Nieuw) **waarvoor geldt dat tboin.dlvernietigingslijst
   op T staat**.

Het kan zijn dat deze extra controle vereist wordt door de
archiefinspecteur.

Wizardoptie: kolom Naar Archiefinspecteur vullen voor (gedeelte van) lijst
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met deze keuze moet de gebruiker eerst:

-  één of meer modules moet aanwijzen
-  en vervolgens een of meer bevoegd gezagen uit tabel tboin
   (beheerportaal-Nieuw) **waarvoor geldt dat tboin.dlvernietigingslijst
   op T staat**.

De kolom ddnaarinspecteur van de rijen van de op dat moment bestaande
vernietigingslijst worden gevuld met de systeemdatum indien:

-  dvmodule voorkomt in de selectie modules
-  de kolom dvnaarbevoegdgezag voorkomt in de selectie bevoegd gezagen
-  het compartiment overeenkomt met dat van de inlogger.

Van tevoren kunnen exportfiles gemaakt worden per bevoegd gezag op grond
van een in te geven filtersetting die ter beoordeling naar de
archiefinspecteur gaan.

Wizardoptie: kolom Archiefinspecteur Akkoord vullen voor (gedeelte van) lijst
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met deze keuze moet de gebruiker eerst:

-  één of meer modules moet aanwijzen
-  en vervolgens een of meer bevoegd gezagen uit tabel tboin
   (beheerportaal-Nieuw) **waarvoor geldt dat tboin.dlvernietigingslijst
   op T staat**.

De kolom ddakkoordinspecteur van de rijen van de op dat moment bestaande
vernietigingslijst worden gevuld met de systeemdatum indien:

-  dvmodule voorkomt in de selectie modules
-  de kolom dvnaarbevoegdgezag voorkomt in de selectie bevoegd gezagen
-  het compartiment overeenkomt met dat van de inlogger
-  de kolom ddnaarinspecteur een gevulde waarde heeft.

Wizardoptie: kolom Vakafdeling akkoord leegmaken voor (gedeelte van) lijst
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met deze keuze moet de gebruiker eerst:

-  één of meer modules moet aanwijzen
-  en vervolgens een of meer bevoegd gezagen uit tabel tboin
   (beheerportaal-Nieuw) **waarvoor geldt dat tboin.dlvernietigingslijst
   op T staat**.

Wizardoptie: kolom Naar Archiefinspecteur (en Archiefinspecteur Akkoord) leegmaken voor (gedeelte van) lijst
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met deze keuze moet de gebruiker eerst:

-  één of meer modules moet aanwijzen
-  en vervolgens een of meer bevoegd gezagen uit tabel tboin
   (beheerportaal-Nieuw) **waarvoor geldt dat tboin.dlvernietigingslijst
   op T staat**.

De kolom ddnaarinspecteur (en logischerwijs de kolom
ddakkoordinspecteur) van de rijen van de op dat moment bestaande
vernietigingslijst worden leeggemaakt indien:

-  dvmodule voorkomt in de selectie modules
-  de kolom dvnaarbevoegdgezag voorkomt in de selectie bevoegd gezagen
-  het compartiment overeenkomt met dat van de inlogger.

Wizardoptie: kolom Archiefinspecteur Akkoord leegmaken voor (gedeelte van) lijst
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met deze keuze moet de gebruiker eerst:

-  één of meer modules moet aanwijzen
-  en vervolgens een of meer bevoegd gezagen uit tabel tboin
   (beheerportaal-Nieuw) **waarvoor geldt dat tboin.dlvernietigingslijst
   op T staat**.

De kolom ddakkoordinspecteur van de rijen van de op dat moment bestaande
vernietigingslijst worden leeggemaakt indien:

-  dvmodule voorkomt in de selectie modules
-  de kolom dvnaarbevoegdgezag voorkomt in de selectie bevoegd gezagen
-  het compartiment overeenkomt met dat van de inlogger.

Wizardoptie: (gedeelte van) rijen van de lijst verwijderen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Het gaat hier om verwijderen van items uit de lijst: dus niet om het
verwijderen en vernietigen van de achterliggende zaken en documenten.

Met deze keuze moet de gebruiker eerst:

-  één of meer modules moet aanwijzen
-  en vervolgens een of meer bevoegd gezagen uit tabel tboin
   (beheerportaal-Nieuw) **waarvoor geldt dat tboin.dlvernietigingslijst
   op T staat**.

De de rijen van de op dat moment bestaande vernietigingslijst worden
verwijderd indien:

-  dvmodule voorkomt in de selectie modules
-  de kolom dvnaarbevoegdgezag voorkomt in de selectie bevoegd gezagen
-  het compartiment overeenkomt met dat van de inlogger.

Operationslog
~~~~~~~~~~~~~

Tijdens het daadwerkelijk verwijderen van zaken en documenten wordt in
de tabel tboperationslog (Operationsportaal kolom *Overig*) een kaart
aangemaakt met de code *Vernietigen zaken*. In de kolom **aantal
verwerkt** wordt het aantal zaken bijgehouden dat door de
vernietigingsloop is gegaan. De gebruiker zal zelf af en toe de
refreshknop linksonder moeten gebruiken om deze voortgang te kunnen zien
(het vernietigen is een onafhankelijk proces zonder userinterface). In
de kolom **Voortgang** staat *Ben bezig* OF *Klaar* OF *Afgebroken door
gebruiker*. Deze laatste mogelijkheid is het geval wanneer de gebruiker
tijdens het proces de kolom tboperations.dlstop op T heeft gezet. In de
kolom **LOG** (te openen via knop linksonder) worden de aantallen
bijgehouden en wordt aangegeven welke zaken/documenten NIET verwijderd
konden worden.
