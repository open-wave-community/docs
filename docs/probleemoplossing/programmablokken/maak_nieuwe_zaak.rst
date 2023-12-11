Aanmaken van nieuwe zaak
========================

Vanuit het archiefportaal **Zaken**/Inrichtingen (wordt uit gefaseerd)
kan met de insertknop een nieuwe zaak aangemaakt worden op de straat die
op dat moment actief is. Vanuit het openingsportaal vanuit de lijst
onder de tegel **Alle Zaken** kan een nieuwe zaak aangemaakt worden
waarbij het programma eerst vraagt om gemeente, woonplaats en straat.
Vanuit het openingsportaal vanuit de lijst onder de tegel **Alle Zaken**
met de knop *Nieuwe zaak op deze straat* kan een nieuwe zaak aangemaakt
worden op dezelfde straat als die van de de actieve rij. Vanuit
termijnbewakingsstappen indien zo gedefinieerd: zie
`Termijnstappen </docs/instellen_inrichten/inrichting_processen/termijnstappen.md>`__.

parameters Wizard maakNieuweZaak
--------------------------------

Deze knoppen starten een action
startWizard(maakNieuweZaak,param2,param3,param4). param1 =
maakNieuweZaak. Het gaat in deze wizard altijd om het maken van nieuwe
kaart in één van de hoofdtabellen tbomgvergunning, tbhandhavingen,
tbovvergunningen, tbinfoaanvragen, tbhorecavergunningen of
tbmilvergunningen.

Met de parameters param2, param3 en param4 is het gedrag en de schermen
van de wizard te beïnvloeden:

-  A. Blanco: de inlogger moet Straat, Adres en Module en Zaaktype
   kiezen. In dat geval moeten param2 en param3 en param4 de waarde null
   hebben, dus: *startWizard(maakNieuweZaak)*
-  B. Straat wordt al meegegeven: inlogger moet Adres en Module en
   Zaaktype kiezen. In dat geval moeten param2 een keyverwijzing zijn
   naar een kaart in tbopenbareRuimte. bijvoorbeeld:
   *startWizard(maakNieuweZaak,1234)*
-  C. Straat en Adres en Module worden al meegegeven: Vervolgzaak. De
   inlogger moet alleen nog een zaaktype kiezen die hoort bij de gegeven
   module. In dit geval moet param2 geen waarde hebben, moet param3 een
   moduleletter bevatten (W,H,O,I,C of B) en param4 moet een dnkey zijn
   uit de tabel die hoort bij de moduleletter. Op grond van deze dnkey
   is het (perceel)-adres bekend waaronder nieuwe zaak aangemaakt wordt.
   Bijvoorbeeld: *startWizard(maakNieuweZaak, ,W,5678)*
-  D. Straat en Adres en Module en Zaaktype worden al doorgegeven.
   Vervolgzaak. In dit geval moet param2 geen waarde hebben. Param3 moet
   een moduleletter bevatten (W,H,O,I,C of B). Param4 bestaat uit twee
   delen gescheiden door een puntkomma: een dnkey uit de tabel die hoort
   bij de moduleletter van param3 op grond waarvan adres wordt
   opgehaald. Het tweede deel van param4 bestaat uit een moduleletter
   waaronder nieuwe zaak moet worden aangemaakt, direct gevolgd door een
   dnkey van het zaaktype (bijv. tbsoortomgverg.dnkey) die hoort bij
   deze module. Bijvoorbeeld *startWizard(maakNieuweZaak,
   ,W;7890,5678;H123)*.

In het geval dat Wizard maakNieuweZaak wordt aangeroepen vanuit een
processtap die afgehandeld moet worden (vervolgzaak\_, nadat een nieuwe
zaak is aangemaakt dan moet param3 bestaan uit twee delen gescheiden
door een puntkomma: de moduleletter en een keyverwijzing naar de kaart
in tbtermijnbewstappen waarvan de afgehandeld datum gevuld moet worden
na het aanmaken van de nieuwe zaak.

Rechten
-------

**Recht op insert zaak bij module.** De inlogger moet lid zijn van een
rechtengroep die op tenminste één van de modules Omgeving, Handhaving,
Milieu/gebruik, Horeca, Info-aanvragen of APV/Overig insertrechten
heeft.

**Recht op aanmaak nieuw locatie:** Na keuze van de module waarvoor een
nieuwe zaak aangemaakt moet worden kan de inlogger de locatie aanwijzen
binnen de gegeven straat. Het kan zijn dat daarbij een huisnummer wordt
ingetikt, waardoor het programma een nieuwe locatie (in
tbperceeladressen) moet aanmaken. De rechtengroep van de inlogger moet
hiervoor op het hoofdscherm rechten het recht: *locatieadressen nieuw*
(tbrechten.dldpclins) aangevinkt hebben.

**Recht aanmaak contactadres** De inlogger kan alleen aangeven dat
hij/zij een nieuw contactadres als aanvrager wil aanmaken indien hij/zij
lid is van een rechtengroep die op het hoofdscherm rechten het recht:
*contactadressen nieuw* (tbrechten.dldcadins) aangevinkt heeft. Is dat
niet het geval dan kan alleen uit de bestaande lijst met contacten
gekozen worden.

Indien de instelling *Sectie: Programma en Item: adresrolviazaaktype* is
aangevinkt, gaat OpenWave eerst kijken naar de verplichte adresrol bij
het betreffende zaaktype (beheerportaal) in de kolom *verplichte
adressoort (rol)* (dvadrsrolverpl). Indien:

-  gevuld dan verplicht de wizard een contactpersoon aan te wijzen die
   onder deze rol wordt opgeslagen
-  leeg dan vraagt de wizard NIET om een contactpersoon.

Indien deze instelling *Sectie: Programma en Item: adresrolviazaaktype*
niet bestaat of NIET is aangevinkt, dan vraagt het programma in alle
gevallen - behalve bij handhavingszaken: daar gaat het om de rol HPC -
om een contactpersoon aan te wijzen, die wordt opgeslagen met de rol
AVR.

Keuze zaaktypes
~~~~~~~~~~~~~~~

De inlogger moet een keuze maken uit een lijst met zaaktypes. Zie
hiervoor de tegels in beheerportaal zaaktypes Omgeving, Handhaving,
Milieu/gebruik, Horeca, info-aanvragen en APV/overig. Het gaat om de
kaarten met een lege vervaldatum. Zie verder bij instellen/inrichten.
Indien de inlogger lid is van een compartiment kunnen alleen die
zaaktypes worden gekozen die toegekend zijn aan dat compartiment (en wel
alleen binnen de gemeentes die toegekend zijn aan dat compartiment). Per
zaaktype kan in het compartiment een eigen masker en lengte opgegeven
zijn/worden voor het genereren van compartiment eigen zaaknummers.
Indien de inlogger GEEN lid is van een compartiment kunnen alleen die
zaaktypes worden gekozen bij de gegeven gemeente indien de combinatie
zaaktype/gegeven gemeente NIET voorkomt in een
`compartiment </docs/instellen_inrichten/compartimenten.md>`__.

Ophalen actoren
~~~~~~~~~~~~~~~

**Zaakverantwoordelijk team** wordt gevuld met:

-  Indien geen compartiment dan met de defaultwaarde van het
   zaakverantwoordelijk team bij de definitie van het zaaktype
   (beheerportaal *Zaakbeheer*).
-  Indien wel compartiment dan in de compartimentsdefinitie
   (beheerportaal *Zaakbeheer*) bij het betreffende zaaktype en
   gemeente.

**Actieve behandelaar** (nieuwe kaart in tbinbehandelingbij):

-  Indien de zaak met de hand wordt aangemaakt, dan indien:

   -  De instelling *Sectie: Programma en Item:
      NieuweZaakKiesBehandelaar* is aangevinkt, dan moet de inlogger een
      medewerker uit de medewerkerstabel aanwijzen (met als default de
      default behandelaar van het zaaktype)
   -  anders de default behandelaar van het zaaktype indien:

      -  de nieuwe zaak een vervolgzaak betreft (bijvoorbeeld aangemaakt
         vanuit een processtap)
      -  en de instelling *Sectie: Programma en Item:
         Defbehbijvervolgzaak* is aangevinkt
      -  en bij het betreffende zaak type is een default behandelaar
         gedefinieerd

   -  anders de medewerkerscode van de inlogger.

-  Indien door een robot (DSO of OLO of…) dan:

   -  indien geen compartiment dan met de defaultwaarde van de
      behandelaar bij de definitie van het zaaktype (beheerportaal
      *Zaakbeheer*)
   -  indien wel compartiment dan in de compartimentsdefinitie
      (beheerportaal-Nieuw) de defaultwaarde van de behandelaar bij het
      betreffende zaaktype en gemeente.

Zie `Behandelaar bij nieuwe
zaak </docs/probleemoplossing/programmablokken/bepaling_behandelaar_nieuwe_zaak.md>`__
voor een schematische weergave van deze redeneringen bij automatisch en
handmatig aangemaakte zaken.

Kopiëren kolommen bij dupliceren omgevingszaak (vervolgzaak)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien *param3* begint met de moduleletter: W en *param4* is gevuld (dus
je kopieert een omgevingszaak met de dnkey van *param4*: situatie C of D
van hierboven bij het kopje *parameters Wizard maakNieuweZaak*) dan
kijkt OpenWave naar de kolom *Tekst* van instelling *Sectie: Programma*
en *Item: KopieerOmgKolommen*. Zie voorbeelden bij processtapdefinitie
bij kopje *Automatisch kiezen vervolgzaak* bij
`Termijnstappen </docs/instellen_inrichten/inrichting_processen/termijnstappen.md>`__.
Indien deze instelling *KopieerOmgKolommen* is:

-  gevuld met een opsomming van één of meer veldnamen uit
   tbomgvergunning gescheiden door een puntkomma
-  en indien kolomnaam ongelijk aan dnkey, dnkeygroepvergunning en
   dnkeysoortomgverg, dnkeyperceeladressen, dvaanvraagnaam, ddaanvraag,
   dvzaakcode, ddfataledatum en dnkeyoinbevgez dan wordt de inhoud van
   deze kolommen naar de nieuwe omgevingszaak gekopieerd.

Indien een zaak wordt gekopieerd waarbij de kolom OLO/DSO-nummer gevuld
is en de kolom dvlvoaanvraagnummer is opgenomen in bovengenoemde
instelling dan redeneert het programma als volgt bij het maken van de
nieuwe zaak: Indien *Getal1* van die instelling de waarde 1 heeft, dan
wordt het OLO/DSO-nummer (dvlvoaanvraagnr) van de zaak die gekopieerd
wordt voorzien van de postfix underscore + 1 (indien \_1 al bestaat
dan_2 en zo verder met maximum van 100). Anders (dus *Getal1* is
ongelijk aan 1) dan wordt de nieuwe gekopieerde kaart voorzien van die
postfix. Dit laatste is nodig om de uniciteit van de kolom
dvlvoaanvraagnr te behouden in verband met opvangen van aanvullende
documenten van het OLO/DSO. Wanneer het de bedoeling is dat aanvullende
(OLO)-documenten bij de oorspronkelijke zaak terechtkomen dan moet
*Getal1* leeg blijven. Indien het de bedoeling is dat de aanvullende
documenten bij de nieuwe zaak terechtkomen dan moet *Getal1* de waarde 1
hebben.

Kopiëren kolommen bij dupliceren handhavingzaak (vervolgzaak)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien *param3* begint met de moduleletter: H en *param4* is gevuld (dus
je kopieert een handhavingzaak met de dnkey van *param4*: situatie C of
D van hierboven bij het kopje *parameters Wizard maakNieuweZaak*) dan
kijkt OpenWave naar de kolom *Tekst* van instelling *Sectie: Programma*
en *Item: KopieerHahKolommen*. Zie voorbeelden bij processtapdefinitie
bij kopje *Automatisch kiezen vervolgzaak* bij
`Termijnstappen </docs/instellen_inrichten/inrichting_processen/termijnstappen.md>`__.
Indien deze instelling *KopieerHahKolommen* is:

-  gevuld met een opsomming van één of meer veldnamen uit tbhandhavingen
   gescheiden door een puntkomma
-  en indien kolomnaam ongelijk aan dnkey, dnkeygroepvergunning en
   dnkeysoorthhzaak, dnkeyperceeladressen, dvomsbouwerk, ddverzoekdatum,
   dvaanschrijfnr, ddfataledatum, dnkeyoinbevgez dan wordt de inhoud van
   deze kolommen naar de nieuwe handhavingzaak gekopieerd.

Ophalen processtappen
~~~~~~~~~~~~~~~~~~~~~

De zaaktypes van Omgeving, Handhaving, Milieu/gebruik, Horeca,
Info-aanvragen en APV/overig kunnen gekoppeld zijn aan processen. De
bijbehorende processtappen worden automatisch aan de nieuwe zaak
toegevoegd indien het attribuut *automatisch* bij die koppelingen
aangevinkt is.

Ophalen checklijsten
~~~~~~~~~~~~~~~~~~~~

De zaaktypes van Omgeving, Handhaving, Milieu/gebruik, Horeca,
Info-aanvragen en APV/overig kunnen gekoppeld zijn aan processen die
automatisch aan de nieuwe zaak kunnen worden toegevoegd (zie hierboven).
Indien aan een automatisch toegevoegd proces één of meer checklijsten
zijn verbonden die ook de eigenschap *automatisch toevoegen* hebben
(tbkopproccheck.dlauto = 'T'), dan worden deze checklijsten automatisch
toegevoegd bij de zaak.

Controle met BAG
~~~~~~~~~~~~~~~~

Deze kan automatisch worden uitgevoerd met een StUF-BG bevraging indien
de instelling *Sectie: KoppelingBAG Item: Methode* en *Tekst: StUF-310*
aangevinkt is. De verplichte instellingen hierbij voor de opmaak en
adressering van de stuf-berichten zijn (zie `BAG
bevraging </docs/probleemoplossing/programmablokken/bag_bevraging.md>`__):

Sectie: KoppelingBAG
^^^^^^^^^^^^^^^^^^^^

-  Item: *HTTPSoapAction_tgoLv01*. In de kolom *Tekst* hier de waarde
   ``[http://www.egem.nl/StUF/sector/bg/0310/tgoLv01](http://www.egem.nl/StUF/sector/bg/0310/tgoLv01.md)``

   -  ``Item: Ontvangstadres`` In de kolom *Tekst* het endpoint waar het
      vraagbericht naar toe moet
   -  ``Item: Zender_Applicatie`` De kolom *Tekst* met de applicatie
   -  ``Item: Zender_Organisatie`` De kolom *Tekst* met de organisatie
   -  ``Item: Ontvanger_Applicatie`` De kolom *Tekst* met de applicatie
   -  ``Item: Ontvanger_Organisatie`` De kolom *Tekst* met de
      organisatie

Indien het adres niet wordt aangetroffen in de BAG, dan wordt de
identificatie van het locatie adres leeggemaakt. Wel gevonden: dan
worden Datum BAG, identificatie en puntcoördinaten gevuld.

**Opmerking:** indien gewenst kunnen bepaalde huisnummers uitgesloten
worden van controle/synchronisatie met BAG. Zie de instelling
*NieuweZaakGeenBAGSync* bij `Sectie
Programma </docs/instellen_inrichten/configuratie/sectie_programma.md>`__.

Automatisch aanmaken zaak in extern zaak/DMS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dit is het geval indien er GEEN sprake is van een compartiment en:

-  omgevingszaak en de instelling *Koppeling ZAAK* en *Item:
   AutoZaakDmsOmgeving* is aangevinkt
-  handhavingszaak en de instelling *Koppeling ZAAK* en *Item:
   AutoZaakDmsHandhaving* is aangevinkt
-  APV/overig zaak en de instelling *Koppeling ZAAK* en *Item:
   AutoZaakDmsApvOverg* is aangevinkt (LET OP: geen schrijffout!)
-  milieu/gebruikzaak en de instelling *Koppeling ZAAK* en *Item:
   AutoZaakDmsMilieuGebruik* is aangevinkt
-  infoaanvraagzaak en de instelling *Koppeling ZAAK* en *Item:
   AutoZaakDmsInfoAanvraag* is aangevinkt
-  horecazaak en de instelling *Koppeling ZAAK* en *Item:
   AutoZaakDmsHoreca* is aangevinkt.

Indien er WEL sprake is van een compartiment dan:

-  omgevingszaak en de kolom dlAutoZaakDmsOmgeving is aangevinkt bij het
   betreffende compartiment (beheerportaal-Nieuw)
-  handhavingszaak en de kolom dlAutoZaakDmsHandhaving is aangevinkt bij
   het betreffende compartiment (beheerportaal-Nieuw)
-  APV/overig zaak en de kolom dlAutoZaakDmsApvOverg is aangevinkt bij
   het betreffende compartiment (beheerportaal-Nieuw)
-  milieu/gebruikzaak en de kolom dlAutoZaakDmsMilieuGebruik is
   aangevinkt bij het betreffende compartiment (beheerportaal-Nieuw)
-  infoaanvraagzaak en de kolom dlAutoZaakDmsInfoAanvraag is aangevinkt
   bij het betreffende compartiment (beheerportaal-Nieuw)
-  horecazaak en de kolom dlAutoZaakDmsHoreca is aangevinkt bij het
   betreffende compartiment (beheerportaal-Nieuw).

Zie voor overige verplichte instellingen voor aanmaken zaak in extern
zaak/DMS bij `Creëer zaak
zaak/dms </docs/probleemoplossing/programmablokken/creeer_zaak_zaak_dms.md>`__.

Automatisch aanmaken mappen op fileshare
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien:

-  de zaak NIET valt onder een compartiment:

   -  de instelling *Sectie: Documenten, Item: OphalenViaFileserver*
      aangevinkt is
   -  en de instelling *Sectie: Documenten, Item:
      AutomAanmaakFileservermappen* aangevinkt is

OF indien

-  de zaak WEL valt onder een compartiment:

   -  de kolom *ophalen via fileserver* op de detailkaart van het
      betreffende compartiment is aangevinkt
   -  en de kolom *Automatisch aanmaken mappen* (dlautoaanmaakmappen)
      aangevinkt is bij het betreffende compartiment

dan zullen bij het aanmaken van een nieuwe zaak of inrichting
automatisch de mappen genoemd in de rijen van *Sectie: Aanmaakmappen*
worden aangemaakt, waarbij er een '4' voorkomt in *Getal1* (dus indien
*Getal1* de waarde 25 heeft dan niet, indien bijv. 4 of 124 dan wel).
Hierbij uitgezonderd zijn de mappen waarin de variabelen ``%adviesnr%``,
``%bezwaarnr%`` en ``%inspnr%`` zijn opgenomen. Indien OpenWave in de
Cloud draait maar de fileserver staat niet in de Cloud, dan moet wel de
`satellite </docs/instellen_inrichten/satellite_filesysteem.md>`__
geïnstalleerd zijn op de fileserver.

Automatisch vullen van kolom dvhyperlink
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Zie: `Hyperlink </docs/instellen_inrichten/hyperlink.md>`__.

Automatisch aanmaken inspectietraject
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien:

-  de instelling *Sectie: Inspecties en Item: OmgAutoAanmaak* is
   aangevinkt
-  en de kolom *Tekst* is gevuld met T en/of C

dan zal bij het aanmaken van een nieuwe omgevingszaak met soort zaaktype
= T (Toezicht) of C (Cyclisch Toezicht) automatisch een nieuw
inspectietraject worden aangemaakt op naam van de inlogger en met
dezelfde startdatum als die van de omgevingszaak.

Indien *Getal1* van deze instelling is gevuld wordt sowieso de einddatum
(ddcontrole) van het inspectietraject gevuld met de startdatum. Indien
de waarde verwijst naar een dnkey in tbinspresultaat wordt deze waarde
overgenomen in dnkeyinspresultaat.

Indien *Getal2* van deze instelling is gevuld en de waarde verwijst naar
een dnkey in tbinspaanleiding dan wordt deze waarde overgenomen in
dnkeyinspaanleiding.

Wanneer op deze manier een inspectietraject gemaakt wordt dat al of niet
gelijk wordt afgesloten en de inspectietrajecttegel wordt niet opgenomen
in de portalen, dan kunnen toch de tegels **Bezoeken** en
**Overtredingen** getoond worden. Via deze tegels kan de gebruiker een
nieuw bezoek dan wel overtreding invoeren, die dan vanzelf aan het
onzichtbare traject wordt gekoppeld. Indien het traject direct wordt
afgesloten, maar het wel de bedoeling is dat bezoeken of overtredingen
kunnen worden ingevoerd dan moet de instelling *Sectie: InspectieMilieu*
en *Item: NietBlokkerenMetHoofdzaak* **NIET** aangevinkt staan.

Automatisch toevoegen aan Groep
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien de zaak wordt aangemaakt vanuit een vervolgaction bij een
processtap dan wordt de groep waar de hoofdzaak bij is aangesloten, ook
toegekend aan de nieuwe gekopieerde zaak. Indien de hoofdzaak nog niet
aan een groep is toegekend (nog steeds in geval van vervolgaction) dan
wordt een nieuwe groep aangemaakt met de startdatum en aanvraagnaam van
de oorspronkelijke zaak. Deze groep wordt vervolgens zowel aan de
bestaande hoofdzaak als aan de nieuwe gekopieerde zaak toegekend. Met
een instelling kan opgegeven worden dat bij het aanmaken van de groep
niet de zaakomschrijving maar het DMS-nummer van de originele zaak als
waarde gepakt worden, zie `Maak nieuwe
zaak </docs/instellen_inrichten/configuratie/sectie_programma.md>`__.

Automatisch vullen van Bevoegd gezag
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien de zaak wordt aangemaakt vanuit een vervolgaction bij een
processtap dan wordt het bevoegd gezag (dnkeyoin) waar de hoofdzaak bij
is aangesloten, ook toegekend aan de nieuwe gekopieerde zaak.

Automatisch vullen van uitvoerende instantie bij omgevingzaak
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bij het handmatig aanmaken van een nieuwe omgevingzaak kan met de
configuratie instelling *Sectie: Programma* en *Item:
NieuweZaakUitvoerendeInstantie* ingesteld worden dat automatisch voor de
nieuwe zaak de uitvoerende instantie gezet wordt. Dit is het geval als
bovengenoemde instelling aangevinkt is en er een geldig OIN-nummer staat
in kolom *Tekst* van deze instelling. Dit OIN-nummer zal van de
uitvoerende instantie zijn die bij omgevingszaken moet worden gezet.

Het wel of niet vullen van de uitvoerende instantie bij een
omgevingszaak heeft invloed op het vanuit OpenWave aanroepen van de
samenwerkingsfunctionaliteit: indien uitvoerende instantie gevuld is bij
de zaak dan zal altijd op basis van OIN-nummer van de uitvoerende
instantie de bevragingen op de samenwerking (SWF ruimte aanmaken,
verversen etc., SWF actieverzoeken uitzetten etc.) voor de zaak worden
gedaan. Is deze niet gevuld dan kijkt het programma naar het bevoegd
gezag van de zaak. Is deze ook niet gevuld dan kijkt het programma naar
de OIN behorende bij de gemeente waarin de zaak zich afspeelt. In de
beheertabel tboin (beheerportaal-Nieuw, kolom Administratie, tegel
*OIN-nummers*) moet een verbinding gelegd zijn tussen het viercijferige
gemeentenummer en het OIN-nummer.

Automatisch vullen van Wettelijke basis en overtreding bij Handhaving
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

De Wettelijke basis (dnkeywetbasis) en overtreding
(dnkeyhandhovertreding) worden automatisch gevuld met de bijbehorende
waardes uit tbhandhovertreding waarvoor geldt dat de
tbhandhovertreding.dnkey (portaal Zaakbeheer, kolom Handhaving/toezicht,
tegel: *Wetten/overtredingen*) gelijk is aan de instelling *Getal1* van
*Sectie: Programma* en *Item: Defaultkeyovertreding*.

Automatisch Navigeren naar zaakportaal
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien de instelling *Sectie: Programma* en *Item:
NieuweZaakGaNaarZaakPortaal* aangevinkt is, dan zal na het handmatig
aanmaken van een nieuwe zaak automatisch door genavigeerd worden naar
het betreffende zaakportaal, tenzij de zaak is aangemaakt vanuit een
processtap (dan keert de gebruiker terug naar het proces).
