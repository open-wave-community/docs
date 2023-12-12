# Sluiten van zaak

Het sluiten van een (hoofd)zaak kan vanuit het detailscherm van een zaak met:

- de knop achter de afhandel/besluitdatum (blok _Afhandeling_)
- de knop achter de intrekkingsdatum (blok _Ingetrokken;tijdens;behandeling_)
- vanuit een action die gekoppeld is aan een processtap (zie kopje blok _Action_ bij de definitie van:[Termijnstappen](/instellen_inrichten/inrichting_processen/termijnstappen.md)).

In onderstaand verhaal wordt meestal een omgevingszaak als voorbeeld genomen, maar grosso modo werken de andere modules hetzelfde.

## parameters Wizard sluitZaak

Deze knoppen starten een action startWizard(sluitZaak,param2,param3,param4).

param1 = sluitZaak.

Het gaat in deze wizard altijd om het sluiten van een zaak in één van de hoofdtabellen tbomgvergunning, tbhandhavingen, tbovvergunningenm tbinfoaanvragen tbhorecavergunningen of tbmilvergunningen.

Met de parameters param2, param3 en param4 is het gedrag en de schermen van de wizard te beïnvloeden:

- param2 moet een keywaarde bevatten van de kaart uit een hoofdtabel
- param3 moet een moduleletter zijn (W,H,O,I,C of B) die verwijst naar de hoofdtabel
- param4 met een kolomnaam bevatten uit de hoofdtabel die door de wizard gevuld wordt met de systeemdatum. De mogelijkheden zijn beperkt: indien param3 =
  - W dan ddbesluitdatum of ddingetrokken
  - O dan ddbesluitdatum of ddingetrokken
  - B dan ddbesluitdatum of ddingetrokken
  - H dan ddeinddatum
  - C dan dddatumbesluit of ddingetrokken
  - I dan ddafgehandeld
  - E dan ddbesluitdatum of ddingetrokken

In het geval dat Wizard sluitZaak wordt aangeroepen vanuit een processtap die afgehandeld moet worden, nadat een zaak is afgesloten dan moet param3 bestaan uit twee delen gescheiden door een puntkomma: de moduleletter en een keyverwijzing naar de kaart in tbtermijnbewstappen waarvan de afgehandelddatum gevuld moet worden na het sluiten van de nieuwe zaak.

## Rechten

De zaak mag niet geblokkeerd zijn. Verder geldt:

- Voor het vullen van de afhandel/besluit/intrekkingsdatum gelden de gewone wijzigrechten op de module.
- Voor het leegmaken van een gevulde datum (met dezelfde knop) geldt echter dat de inlogger OOK het recht _Leegmaken van gevulde afhandel-intrekkingsdatum_ bij de betreffende module moet hebben (bijv. tbomgrechten.dlbomgafsedt).

### Legesregel verplicht

Op zaaktypeniveau (beheerportaal _Zaakbeheer_) kan bij de definitie van een zaaktype aangegeven worden of bij het betreffende zaaktype een legesregel verplicht is. Geldt niet voor modules Info en Milieu/gebruik en Bouw/sloop. Indien dat het geval is en er geen legesregel is gedefinieerd bij de zaak, zal de gebruiker de zaak niet kunnen afsluiten. Er verschijnt een melding.

### Aard besluit

Indien het gaat om het vullen van de afhandel/besluitdatum van een zaak zal de inlogger een resultaat moeten kiezen uit de tabel TbAardBesluit die bereikbaar is in het beheerportaal _Zaakbeheer_ via de tegel _Afhandeling/Besluit omg/apv/bouw/milieu/gebruik_. Voor handhavingen geldt de tabel TbHandhAfrondin via de beheertegel _Afhandeling handhaving_.

Per zaaktype kan (bijv. tegel _Zaaktypes omgeving_) aangegeven worden welke items uit de tabel tbaardbesluit bij het betreffende zaaktype van toepassing kunnen zijn (tevens kunnen bij deze combinatie aard-besluit en zaaktype de bewaartermijnen aangegeven worden). Dit gebeurt in het detailscherm van een zaaktype in het blok _Gekoppeld Afhandeling/Besluit_.

Indien de instelling _Sectie: Programma, Item: sluitzaakresultbekend_ aangevinkt is en het aardbesluit is reeds gevuld (bijvoorbeeld via een processtap) dan zal de wizard het overschrijven van aardbesluit NIET toestaan.

### Openstaande adviezen/processtappen

OpenWave kijkt of er nog items bij de adviezen (ddadviesdatum leeg niet vervallen) en bij de processtappen (in gebruik en lege afhandeldatum) open staan. Normaliter wordt dit aantal gemeld bij het afsluiten/intrekken en kan de inlogger aangeven of Openwave zelf deze adviezen en/of processtappen mag afsluiten.

Indien echter een advies een zelfstandige zaak is in een extern zaaksysteem/DMS dan mogen deze adviezen **NIET** automatisch worden afgesloten; het programma verhindert deze optie.

Een advies is een zelfstandige zaak in een extern zaaksysteem/DMS indien:

- Als de hoofdzaak NIET tot een compartiment behoort dan:
  - moet de instelling met _Sectie: Koppeling Zaak en Item: Methode_ aangevinkt staan en de waarde van kolom _Tekst_ moet zijn: _StUF-ZAKEN 310_
  - moet de instelling met _Sectie: Koppeling Zaak en Item: ZaaktypeAdvies_ aangevinkt staan en de waarde van kolom _Tekst_ bevat het externe zaaktype
  - en _Getal1_ van _Sectie: Koppeling Zaak en Item: Zender_Organisatie_ moet verwijzen naar een dnkey van tbcontactadressen (namelijk die van de behandelende organisatie zelf die als aanvrager voor de deelzaak advies fungeert).
- Als de hoofdzaak WEL tot een compartiment behoort dan:
  - moet de kolom dvdmsmethode van het betreffende compartiment (beheerportaal-Nieuw) gevuld zijn met: StUF-ZAKEN 310
  - en moet de kolom dvdmszaaktypeadvies van het compartiment gevuld zijn
  - en moet de kolom dnkeyorganisatie van het compartiment gevuld zijn en deze waarde moet verwijzen naar een dnkey van tbcontactadressen (namelijk die van de behandelende organisatie zelf die als aanvrager voor de deelzaak advies fungeert).

### Openstaande Inspectietrajecten

Indien instelling _Sectie: Programma en Item: SluitOpenInspbijSluitenZaak_ bestaat en aan is gevinkt, dan kijkt OpenWave of er nog items bij de inspecties open staan. Net als bij adviezen en processen wordt dit aantal gemeld bij het afsluiten/intrekken en kan de inlogger aangeven of Openwave zelf deze inspectietrajecten en de daar bijbehorende bezoeken en overtredingen mag afsluiten. Indien echter een inspectietraject een zelfstandige zaak is in een extern zaaksysteem/DMS dan mogen deze inspectietrajecten **NIET** automatisch worden afgesloten; het programma verhindert deze optie.

Een inspectietraject is een zelfstandige zaak in een extern zaaksysteem/DMS indien:

- Als de hoofdzaak NIET tot een compartiment behoort dan:
  - moet de instelling met _Sectie: Koppeling Zaak en Item: Methode_ aangevinkt staan en de waarde van kolom _Tekst_ moet zijn: _StUF-ZAKEN 310_
  - moet de instelling met _Sectie: Koppeling Zaak en Item: ZaaktypeInspectietraject_ aangevinkt staan en de waarde van kolom _Tekst_ bevat het externe zaaktype
  - en _Getal1_ van _Sectie: Koppeling Zaak en Item: Zender_Organisatie_ moet verwijzen naar een dnkey van tbcontactadressen (namelijk die van de behandelende organisatie zelf die als aanvrager voor de deelzaak inspectie fungeert).
- Als de hoofdzaak WEL tot een compartiment behoort dan:
  - moet de kolom dvdmsmethode van het betreffende compartiment (beheerportaal-Nieuw) gevuld zijn met: StUF-ZAKEN 310
  - en moet de kolom dvdmszaaktypeinspecties van het compartiment gevuld zijn
  - en moet de kolom dnkeyorganisatie van het compartiment gevuld zijn en deze waarde moet verwijzen naar een dnkey van tbcontactadressen (namelijk die van de behandelende organisatie zelf die als aanvrager voor de deelzaak advies fungeert).

### Openstaande Producten

Indien de instelling _Sectie: Programma en Item: SluitProductenbijSluitenZaak_ bestaat en aan is gevinkt, dan kijkt OpenWave of er nog openstaande producten zijn bij de zaak die wordt gesloten. Net als bij adviezen en processen wordt dit aantal gemeld bij het afsluiten/intrekken en kan de inlogger aangeven of Openwave zelf deze producten mag afsluiten. De opleverdatum van de producten zal dan worden gevuld.

### Automatisch blokkeren

Indien in het beheerportaal bij het betreffende zaaktype de kolom _blokkeren bij sluiten zaak_ aangevinkt wordt (bijv. tbsoortomgverg.dlblokkerenbijsluitenzaak), dan zal het vullen van de einddatum ook resulteren in het vullen van de blokkeerdatum.

### Automatisch aanmaken inspectietraject indien compartiment

Indien de hoofdzaak valt onder een compartiment, maar bij de compartiment/zaak definitie (beheerportaal-Nieuw) is aangegeven dat het toezicht op die zaak NIET onder dat compartiment valt (dus exclusief inspectie: hetgeen betekent dat het toezicht wordt uitgevoerd door de host-organisatie), dan wordt automatische een inspectietraject aangemaakt bij het afsluiten van de zaak. Bij de compartiment/zaak definitie MOET zijn opgegeven met welke inspecteur (van de host-organisatie) en met welke aanleiding dat traject gemaakt moet worden.

### EmailnaarBAGBeheerder

Met het afsluiten van de zaak kan automatisch een [mail naar de BagBeheerder](/probleemoplossing/programmablokken/email_bag-beheerder.md) worden gestuurd. Dit is het geval indien:

- Vanuit module handhaving:
  - als een initiërende mail naar de BAG-beheerder is gestuurd (op detailscherm in blok _Keten_)
  - en de inlogger zelf een email-adres heeft (beheertegel _Medewerkers_)
  - en de BAG-beheerder een email-adres heeft (beheertegel _Gemeentes_).
- Vanuit module omgeving:
  - Indien de zaak die wordt beëindigd betreft:
    - een verleende reguliere procedure (bij zaaktype in beheer moet de soortproc de waarde **R** hebben)
    - of een verleende uitgebreide procedures (bij zaaktype in beheer moet de soortproc de waarde **U** hebben)
    - of een ingetrokken sloopmelding (_Getal2_ van de instelling _Sectie: Koppeling OLO en Item: MeldingOnderdeelSlopen_ moet gelijk zijn aan de primary key van het zaaktype)
    - of een calamiteit (_Getal2_ van de instelling _Sectie: Koppeling OLO en Item: Calamiteitenmelding_ moet gelijk zijn aan de primary key van het zaaktype)
  - en bij minimaal een van de activiteiten zijn werkzaamheden van toepassing. Zie soort activiteit (beheertegel _Soort activiteit/onderdeel_) blok _Eigenschappen_
  - en de inlogger zelf een email-adres heeft (beheertegel _Medewerkers_)
  - en de BAG-beheerder een email-adres heeft (beheertegel _Gemeentes_).

### Automatisch kopiëren van zaak indien cyclisch toezicht

Alleen indien:

- het gaat om een omgevingszaak
- en de kolom _soort procedure_ (dvsoortproc) van het zaaktype (tbsoortomgverg) de waarde **C** heeft (van Cyclisch Toezicht)
- en de besluit/afhandeldatum (ddbesluitdatum) wordt gevuld
- en de omgevingszaak is gekoppeld aan een inrichting (dnkeyKeymilinrichtingen is gevuld)
- en de inlogger heeft een keuze gemaakt voor een van de opties _nieuwe toezichtzaak op basis van einddatum_ of _nieuwe toezichtzaak op basis van startdatum_ (deze opties worden gevraagd indien de hierboven staande items waar zijn).

DAN wordt automatisch een nieuwe zaak aangemaakt op:

- dezelfde locatie
- met hetzelfde zaaktype
- met dezelfde default behandelaar/teams
- met dezelfde product informatie
- met hetzelfde bevoegd gezag
- met dezelfde contactpersonen

De begindatum van de nieuwe cyclische toezicht zaak is gebaseerd op de einddatum of begindatum van de te kopiëren zaak met daarbij opgeteld de cyclus zoals vastgelegd bij de gekoppelde inrichting. Zie: [Cyclische Toezicht: controle frequentie](/probleemoplossing/programmablokken/cyclische_inspecties.md).

Het kan zo ingesteld staan dat bij deze nieuwe cyclisch toezichtzaak automatisch ook een nieuw inspectietraject moet worden gemaakt. Zie het kopje **Automatisch aanmaken inspectietraject** bij [Aanmaken van nieuwe zaak](/probleemoplossing/programmablokken/maak_nieuwe_zaak.md).

### ActualiseerZaakstatus indien gekoppeld aan extern zaak/DMS

Dit Stufbericht gaat uit indien:

- de externe zaakcode gevuld is (dvintzaakcode)
- en – indien de zaak NIET valt onder een compartiment - dan moet de instelling met _Sectie: Koppeling Zaak en Item: Methode_ moet aangevinkt staan. De waarde van kolom _Tekst_ moet zijn: _StUF-ZAKEN 310_
- en – indien wel compartiment - dan moet de kolom dvdmsmethode van het betreffende compartiment gevuld zijn met: _StUF-ZAKEN 310_.

De status die wordt gezet is:

- StatusInBehandeling indien sluitzaak is aangeroepen door het leegmaken van gevulde besluitdatum
- StatusIngetrokken indien de intrekkingsdatum werd gevuld
- StatusAfgesloten indien de besluitdatum werd gevuld.
