# Wijzigen Status externe zaak met Zaak/DMS

Een statuswijziging in OpenWave wordt automatisch getriggerd en - in geval van zaak/DMS koppeling - doorgegeven aan het externe zaaksysteem.
Dat gebeurt met een actualiseerZaakStatus_Lk01 bericht. Zie onderaan de mogelijke uitzondering indien het gaat om het doorgeven van een einddatum en resultaat via een updateZaak-bericht.

## Verplichte Instellingen

* **Methode**
  * Indien de zaak NIET wordt behandeld door een compartiment dan MOET de instelling *Sectie: Koppeling ZAAK:* en *Item: Methode* aangevinkt staan en heeft als *Tekst*: StUF-ZAKEN 310.
  * Indien de zaak WEL wordt behandeld door een compartiment dan MOET de kolom dvdmsmethode bij de compartimentsdefinitie de waarde StUF-ZAKEN 310 hebben.
* **Action**
  * Instelling *Sectie: Koppeling ZAAK* en *Item: HTTPSoapAction_actualiseerZaakstatus_Lk01*. De waarde in kolom *Tekst* = `[http://www.egem.nl/StUF/sector/zkn/0310/actualiseerZaakstatus_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/actualiseerZaakstatus_Lk01.md)`

LET OP: de soapactions kunnen ook ingesloten moeten zijn door dubbele quootjes, dus bijv. `"[http://www.egem.nl/StUF/sector/zkn/0310/actualiseerZaakstatus_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/actualiseerZaakstatus_Lk01.md)"`

### Endpoint, credentials en stuurgegevens

Voor het endpoint en de stuurgegevens zal het programma eerst kijken naar de waarden in de blokken *StUF zaak/DMS endpoint en credentials* en *StUF zaak/dms stuurgegevens* van het **detailscherm van de gemeente waar de zaak speelt** (beheertegel *Gemeentes*) waarbij:

* Voor de Ontvanger_administratie geldt dat als de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsOntvangerAdm* bestaat en is aangevinkt EN *Getal1* heeft de waarde 1, dat dan in het bericht het stuurgegeven ontvanger administratie gevuld wordt met de gemeente-id van de locatie waar de zaak zich afspeelt.
* Voor de Zender_administratie geldt dat als de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsZenderAdm* bestaat en is aangevinkt EN *Getal1* heeft de waarde 1, dat dan in het bericht het stuurgegeven zender administratie gevuld wordt met de gemeente-id van de locatie waar de zaak zich afspeelt.

Indien alhier **het endpoint asynchroon gevuld** is, dan neemt het programma de credentials en stuurgegevens over van deze kaart. Een uitzondering hierop is de situatie dat een zaak speelt bij een gemeente die gedefinieerd is in een compartiment terwijl de zaak zelf niet door dat compartiment wordt behandeld, maar door de host. In dat laatste geval valt OpenWave terug op de algemene StUF zaak/DMS instellingen uit tbinitialisatie (beheertegel *Configuratie*). Dat is ook het geval indien in tb33gemeente geen instellingen worden gevonden: dan valt het programma terug op de volgende configuratie-instellingen van *Sectie: Koppeling ZAAK: gemeentes*:

* *Item: Ontvangstadres_Asynchroon* moet gevuld zijn t.b.v. actualiseer status bericht.
* *Item: Ontvanger_applicatie*. De kolom *Tekst* met de ontvanger (ook verplicht).
* *Item: Ontvanger_organisatie*. De kolom *Tekst* met de organisatie (ook verplicht).
* *Item: Zender_applicatie*. De kolom *Tekst* met de ontvanger (ook verplicht).
* *Item: Zender_organisatie*. De kolom *Tekst* met de organisatie (ook verplicht).
* *Item: Ontvanger_administratie*. De kolom *Tekst* met de administratie. Echter, indien de instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsOntvangerAdm* bestaat en is aangevinkt EN *Getal1* heeft de waarde 1, dan wordt in het bericht het stuurgegeven ontvanger administratie gevuld met de gemeente-id van de locatie waar de zaak zich afspeelt.
* *Item: Zender_administratie*. De kolom *Tekst* met de administratie. Echter, indien de instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsZenderAdm* bestaat en is aangevinkt EN *Getal1* heeft de waarde 1, dan wordt in het bericht het stuurgegeven zender administratie gevuld met de gemeente-id van de locatie waar de zaak zich afspeelt.
* *Item: Zender_gebruiker*. De kolom *Tekst* met de gebruiker.
* Als de instelling *Sectie: Koppeling ZAAK* en *Item: **HTTPAuthenticatieNaam*** bestaat en is aangevinkt dan wordt de verzending over HTTPS geautoriseerd met:
  * authenticatienaam is kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: HTTPAuthenticatieNaam*
  * authenticatiepass is kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: HTTPAuthenticatiePass*. Zie ook: [2-way encryptie van externe wachtwoorden](/docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md).
  * In de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: HTTPAuthenticatieType* kan desgewenst het authenticatietype worden ingevuld: Basic (default) of NTLM (versie 1).
  * In de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: Domein* kan desgewenst het domein worden ingevuld.
* Indien er gebruik moet worden gemaakt van een **client-certificaat** (wordt geplaatst op de CONF-map van de WSAS server) dan:
  * moet de (file)-naam van dat certificaat worden opgeslagen in de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: ClientCertificaatNaam*
  * het certificaat password in de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: ClientCertificaatPassword*. Zie ook: [2-way encryptie van externe wachtwoorden](/docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md)
  * het certificaattype in de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: ClientCertificaatType* (default PKCS12).

#### Verwerkingssoorten bij entiteit ZAKSST in blok <heeft>

Een verschil in interpretatie van StUF standaard leidt tot de mogelijkheid om de verwerkingssoorten (zoals I of T) in het blok *<ns:heeft stuf:entiteittype="ZAKSTT"* (4 stuks) chronologisch op te geven. Aangezien er twee blokken object zijn (oude en nieuwe situatie) zijn er ook twee heeft SST-blokken. Het gaat respectievelijk om de instellingen:

* De kolom *Tekst* van Sectie: *Koppeling Zaak* en Item: *ActStatusObject1Verwsoort1*. Defaultwaarde = I (een hoofdletter i).
* De kolom *Tekst* van Sectie: *Koppeling Zaak* en Item: *ActStatusObject1Verwsoort2*. Defaultwaarde = I (een hoofdletter i).
* De kolom *Tekst* van Sectie: *Koppeling Zaak* en Item: *ActStatusObject1Verwsoort3*. Defaultwaarde = T (let op: een hoofdletter t).
* De kolom *Tekst* van Sectie: *Koppeling Zaak* en Item: *ActStatusObject1Verwsoort4*. Defaultwaarde = I (een hoofdletter i).
* De kolom *Tekst* van Sectie: *Koppeling Zaak* en Item: *ActStatusObject2Verwsoort1*. Defaultwaarde = I (een hoofdletter i).
* De kolom *Tekst* van Sectie: *Koppeling Zaak* en Item: *ActStatusObject2Verwsoort2*. Defaultwaarde = I (een hoofdletter i).
* De kolom *Tekst* van Sectie: *Koppeling Zaak* en Item: *ActStatusObject2Verwsoort3*. Defaultwaarde = T (let op: een hoofdletter t).
* De kolom *Tekst* van Sectie: *Koppeling Zaak* en Item: *ActStatusObject2Verwsoort4*. Defaultwaarde = I (een hoofdletter i).

### IsGezetDoor

Degene die de status wijzigt wordt doorgegeven in het StUF-bericht. De wijze waarop is afhankelijk van *Getal1* van de instelling *Sectie: Koppeling ZAAK* en *Item: Behandelaardoorgeven*. Indien:

* *Getal1* heeft de waarde 1 dan wordt de gemeente-id van de zaak + de medewerkerscode van de inlogger als identificatie van de medewerker gebruikt
* *Getal1* heeft de waarde 2 dan wordt de gemeente-id van de zaak + de loginnaam van de inlogger als identificatie van de medewerker gebruikt
* *Getal1* heeft de waarde 3 dan wordt de gemeente-id van de zaak + de vaste waarde kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: Behandelaardoorgeven* gebruikt.

### Een statuswijziging wordt getriggerd door

* creëren van een zaak
* wijzigen van besluit/afhandeldatum bij handhaving, info, omgeving en APV/overig en milieu/gebruik
* wijzigen van intrekkingsdatum bij omgeving en APV/overig en milieu/gebruik
* wijzigen van afgehandelddatum bij deelzaken inspecties, adviezen, bezwaarberoep (mits deze deelzaken als aparte zaak in extern zaak/DMS zijn gedefinieerd)
* blokkeren van handhaving, omgeving en APV/overig en milieu/gebruik (mits StatusGeblokkeerd een mapping heeft in beheertabel *Zaakstatussen*).

#### Creëren van een zaak

Bij het creëren van een zaak wordt altijd:

* de mapping van de status *StatusInbehandeling* doorgegeven (zie beheertegel *Zaakstatussen*)
* met een lege einddatum
* EN een lege resultaatomschrijving.

Zie ook [Creëer zaak zaak/DMS](/docs/probleemoplossing/programmablokken/creeer_zaak_zaak_dms.md).

#### Vullen van een lege besluit/afhandeldatum van hoofdzaak

Bij het vullen van een lege besluit/afhandeldatum bij handhaving, omgeving en APV/overig en milieu/gebruik kijkt het programma naar het volgende:

* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de zaak
* de StatusAfgesloten moet een mapping hebben in beheertabel *Zaakstatussen*
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusAfgesloten*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusAfgesloten* doorgegeven
* indien StatusGeblokkeerd ook een mapping heeft in beheertabel *Zaakstatussen* dan:
  * wordt een lege einddatum meegestuurd
  * MET een lege resultaatomschrijving
* anders, (StatusGeblokkeerd heeft geen mapping) wordt de zaak met het afsluiten ook beëindigd in het externe zaaksysteem door:
    *gevulde einddatum mee te sturen
  * MET een gevulde resultaatomschrijving. Die resultaatomschrijving komt:
  * indien het gaat om een omgevingszaak of APV/Overige zaak of Milieu/gebruikzaak van de kolom *Resultaatmapping bij zaak/DMS koppeling* (dvdmsaardbesluit) uit de beheertabel *Afhandeling Besluit Omg/APV/Bouw/Milieu/Gebruik* (tbaardbesluit) bij het betreffende aard besluit
  * anders (het gaat om een handhavingszaak) van de kolom *Resultaatmapping bij zaak/DMS koppeling* (dvdmsaardbesluit) uit de beheertabel *Afhandeling Handhaving* (tbhandhafronding) bij de betreffende afronding.

LET OP: Indien een gevulde einddatum wordt meegestuurd bij een Omgevingszaak met een OLO-nummer (dvlvoaanvraagnr) EN de instelling *Sectie: Koppeling OLO* en *Item: Olonrdatumbijafsluitenextzaak* is aangevinkt dan wordt aan het OLO-nummer een datum string met format '-jjjjmmdd' toegevoegd (dus als OLO-nummer is 123456 en de datum is 24 feb 2017 dan wordt dat 123456-20170224).
Dit betekent dat een tweede adviesaanvraag (soms half jaar later) op hetzelfde OLO-nummer dan als nieuwe zaak wordt beschouwd door OpenWave.

#### Leegmaken van een gevulde besluit/afhandeldatum van hoofdzaak

Bij het leegmaken van een gevulde besluit/afhandeldatum bij handhaving, omgeving, milieu/gebruik en APV/overig kijkt het programma naar het volgende:

* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de zaak
* de StatusInbehandeling moet een mapping hebben in beheertabel *Zaakstatussen*
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusInbehandeling*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusInbehandeling* doorgegeven
* een lege einddatum wordt meegestuurd
* MET een lege resultaatomschrijving.

#### Veranderen van een gevulde besluit/afhandeldatum of intrekkingsdatum van hoofdzaak

Bij het veranderen van een gevulde besluit/afhandeldatum bij handhaving, milieu/gebruik, omgeving en APV/overig (en niet leegmaken) gebeurt er niets. Bij het veranderen van een gevulde intrekkingsdatum bij omgeving en APV/overig en milieu/gebruik (en niet leegmaken) gebeurt er niets.

#### Vullen van een lege intrekkingsdatum van hoofdzaak

Bij het vullen van een lege intrekkingsdatum bij omgeving en APV/overig en milieu/gebruik kijkt het programma naar het volgende:

* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de zaak
* de StatusIngetrokken moet een mapping hebben in beheertabel *Zaakstatussen*
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusIngetrokken*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusIngetrokken* doorgegeven
* indien StatusGeblokkeerd ook een mapping heeft in beheertabel *Zaakstatussen* dan:
  * wordt een lege einddatum wordt meegestuurd
  * MET een lege resultaatomschrijving
* anders, (StatusGeblokkeerd heeft geen mapping) wordt de zaak met het intrekken ook beëindigd in het externe zaaksysteem door:
  * een gevulde einddatum mee te sturen
  * MET een gevulde resultaatomschrijving. Die resultaatomschrijving komt van de kolom *Resultaatomschrijving* van de beheertabel *Zaakstatussen* bij de status 'StatusIngetrokken'.

#### Leegmaken van een gevulde intrekkingsdatum van hoofdzaak

Bij het leegmaken van een gevulde intrekkingsdatum bij omgeving en APV/overig en milieu/gebruik kijkt het programma naar het volgende:

* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de zaak
* de StatusInbehandeling moet een mapping hebben in beheertabel *Zaakstatussen*
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusInbehandeling*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusInbehandeling* doorgegeven
* er een lege einddatum wordt meegestuurd
* MET een lege resultaatomschrijving

#### Vullen van een lege afgehandelddatum bij deelzaakinspecties

Bij het vullen van een lege afgehandelddatum (ddcontrole) bij inspecties kijkt het programma naar het volgende:

* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de zaak
* de StatusAfgesloten moet een mapping hebben in beheertabel *Zaakstatussen*
* de kolom *Resultaat* (dnkeyinspresultaat dan wel dnkeyaardbesluitsoortinsp) van het inspectietraject moet een gevulde waarde hebben. In het geval dat *Getal1* van de instelling *Sectie: Inspecties en Item: ResultaatVerplichtBijAfsluiten* de waarde 1 heeft kijkt het programma naar dnkeyaardbesluitsoortinsp, anders naar dnkeyinspresultaat)
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusAfgesloten*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* indien de mapping van de status *StatusGeblokkeerd* (beheertabel *Zaakstatussen*) gevuld is dan:
  * wordt deze mapping van status *StatusGeblokkeerd* doorgegeven
  * anders (mapping *StatusGeblokkeerd* is leeg) dan wordt de mapping van *StatusAfgesloten* doorgegeven
* een gevulde einddatum wordt meegestuurd
* MET een gevulde resultaatomschrijving. Deze resultaatomschrijving komt
  * in het geval dat *Getal1* van de instelling *Sectie: Inspecties en Item: ResultaatVerplichtBijAfsluiten* **NIET** de waarde 1 heeft uit beheertegel *InspectieResultaten* (tbinspresultaat) uit de kolom *Mapping resultaat bij zaak/DMS koppeling* (dvdmsaardbesluit)
  * in het geval dat *Getal1* van deze instelling **WEL** de waarde 1 heeft uit de kolom tbaardbesluit.dvdmsaardbesluit via de koppeltabel tbaardbesluitsoortinsp (koppeltabel tussen tbinspaanleiding en tbaardbesluit).

#### Leegmaken van een gevulde afgehandelddatum bij deelzaakinspecties

Bij het leegmaken van een gevulde afgehandelddatum (ddcontrole) bij inspecties kijkt het programma naar het volgende:

* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de zaak
* de StatusInbehandelding moet een mapping hebben in beheertabel *Zaakstatussen*
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusInbehandeling*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusInbehandeling* doorgegeven
* een lege einddatum wordt meegestuurd (kan mogelijk niet worden geaccepteerd door extern zaak/DMS)
* MET een lege resultaatomschrijving.

#### Sluiten/heropenen zaak bij deelzaak adviezen

De knop **Sluit/heropen zaak in zaak/DMS systeem** op het detailscherm van advies kan worden ingedrukt indien:

* de externe zaak/DMS code (dvintzaakcode) gevuld is bij de advieszaak
* de StatusAfgesloten en StatusInbehandeling moeten een mapping hebben in beheertabel *Zaakstatussen*
* de kolom *Resultaat* (dvdmsresultaat ) van het soort advies/aanbeveling (tbretouradvies) moet een gevulde waarde hebben bij het betrokken advies
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet bij het sluiten ongelijk zijn aan de mapping van *StatusAfgesloten*
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet bij het heropenen ongelijk zijn aan de mapping van *StatusInbehandeling*.

 Is hieraan voldaan dan wordt voor het sluiten (*datum DMS afgehandeld* is nog leeg) een statuswijzingbericht doorgezonden waarbij:

* indien de mapping van de status *StatusGeblokkeerd* (beheertabel *Zaakstatussen*) gevuld is dan:
  * wordt deze mapping van status *StatusGeblokkeerd* doorgegeven
  * anders (mapping *StatusGeblokkeerd* is leeg) dan wordt de mapping van *StatusAfgesloten* doorgegeven
* als einddatum wordt een opgegeven datum meegestuurd. Deze datum wordt in het advies zichtbaar als *einddatum (dddmsafgehandeld)*
* MET een gevulde resultaatomschrijving uit tbretouradvies.

Is hieraan voldaan dan wordt voor het *heropenen einddatum* (dddmsafgehandeld
is gevuld) een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusInbehandeling* doorgegeven
* een lege einddatum wordt meegestuurd (kan mogelijk niet worden geaccepteerd door extern zaak/DMS)
* MET een lege resultaatomschrijving.

#### Sluiten/heropenen zaak bij deelzaak bezwaar/beroep

De knop **Sluit/heropen zaak in zaak/DMS systeem** op het detailscherm van bezwaar/beroep kan worden ingedrukt indien:

* de externe zaak/DMS code (dvintzaakcode) gevuld is bij de bezwaarberoepzaak
* de StatusAfgesloten en StatusInbehandeling moeten een mapping hebben in beheertabel *Zaakstatussen*
* de kolom *Resultaat* (dvdmsresultaat ) van de aard besluit bezwaar/beroep (tbaardbeslbezwaar) moet een gevulde waarde hebben bij de bezwaar/beroepzaak (wordt gevuld bij vullen van de uitspraakdatum)
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet bij het sluiten ongelijk zijn aan de mapping van *StatusAfgesloten*
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet bij het heropenen ongelijk zijn aan de mapping van *StatusInbehandeling*.

 Is hieraan voldaan dan wordt voor het sluiten (*datum DMS afgehandeld* is nog leeg) een statuswijzingbericht doorgezonden waarbij:

* indien de mapping van de status *StatusGeblokkeerd* (beheertabel *Zaakstatussen*) gevuld is dan:
  * wordt deze mapping van status *StatusGeblokkeerd* doorgegeven
  * anders (mapping *StatusGeblokkeerd* is leeg) dan wordt de mapping van *StatusAfgesloten* doorgegeven
* als einddatum wordt een opgegeven datum meegestuurd. Deze datum wordt in bezwaar/beroep zichtbaar als *einddatum (dddmsafgehandeld)*
* MET een gevulde resultaatomschrijving uit tbaardbeslbezwaar.

Is hieraan voldaan dan wordt voor het *heropenen einddatum* (dddmsafgehandeld
is gevuld) een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusInbehandeling* doorgegeven
* een lege einddatum wordt meegestuurd (kan mogelijk niet worden geaccepteerd door extern zaak/DMS)
* MET een lege resultaatomschrijving.

#### Vullen van blokkeerdatum van een hoofdzaak

Bij het blokkeren (vullen van blokkeerdatum) van handhaving, omgeving en APV/overig kijkt het programma naar het volgende:

* StatusGeblokkeerd moet een mapping hebben in beheertabel *Zaakstatussen*
* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de zaak
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusGeblokkeerd*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusGeblokkeerd* doorgegeven
* een gevulde einddatum meegestuurd wordt (de blokkeringsdatum)
* MET een gevulde resultaatomschrijving. Die resultaatomschrijving komt:
  * indien het gaat om een omgevingszaak of APV/Overige zaak of milieu/gebruik van de kolom *Resultaatmapping bij zaak/DMS koppeling* (dvdmsaardbesluit) uit de beheertabel *Afhandeling Besluit Omg/APV/Bouw/Milieu/Gebruik* (tbaardbesluit) bij het betreffende aard besluit
  * anders (de het gaat om een handhavingszaak) van de kolom *Resultaatmapping bij zaak/DMS koppeling* (dvdmsaardbesluit) uit de beheertabel *Afhandeling Handhaving* (tbhandhafronding) bij de betreffende afronding.

LET OP: Indien een gevulde einddatum wordt meegestuurd bij een Omgevingszaak met een OLO-nummer (dvlvoaanvraagnr) EN de instelling *Sectie: Koppeling OLO* en *Item: Olonrdatumbijafsluitenextzaak* is aangevinkt dan wordt aan het OLO-nummer een datum string met format '-jjjjmmdd' toegevoegd (dus als OLO-nummer is 123456 en de datum is 24 feb 2017 dan wordt dat 123456-20170224).
Dit betekent dat een tweede adviesaanvraag (soms half jaar later) op hetzelfde OLO-nummer dan als nieuwe zaak wordt beschouwd door OpenWave.

#### Vullen van blokkeerdatum van een inrichting MET blokkeermapping

* Bij het blokkeren (vullen van blokkeerdatum) van een inrichting EN StatusGeblokkeerd heeft een mapping in beheertabel *Zaakstatussen* dan kijkt het programma naar het volgende:
* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de inrichting
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusGeblokkeerd*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusGeblokkeerd* doorgegeven
* een gevulde einddatum meegestuurd wordt (de blokkeringsdatum)
* MET een gevulde resultaatomschrijving. Die resultaatomschrijving komt van de kolom *Resultaatomschrijving* van de beheertabel *Zaakstatussen* bij de status 'StatusGeblokkeerd'.

#### Vullen van blokkeerdatum van een inrichting ZONDER blokkeermapping

Bij het blokkeren (vullen van blokkeerdatum) van inrichting EN StatusGeblokkeerd heeft GEEN mapping in beheertabel *Zaakstatussen*, dan kijkt het programma naar het volgende:

* de externe zaak/DMS code (dvintzaakcode) moet gevuld zijn bij de inrichting
* de StatusAfgesloten moet een mapping hebben in beheertabel *Zaakstatussen*
* de waarde van de kolom *Status* (bij zaak/DMS gezet) moet ongelijk zijn aan de mapping van *StatusAfgesloten*.

Is hieraan voldaan dan wordt een statuswijzingbericht doorgezonden waarbij:

* de mapping van de status *StatusAfgesloten* doorgegeven
* een gevulde einddatum meegestuurd wordt (de blokkeringsdatum)
* MET een gevulde resultaatomschrijving. Die resultaatomschrijving komt van de kolom *Resultaatomschrijving* van de beheertabel *Zaakstatussen* bij de status 'StatusAfgesloten'.

#### Deblokkeren

Bij het deblokkeren van een zaak of inrichting wordt er geen statuswijziging uitgezonden.

### Logging

De berichten kunnen gelogd worden op 2 manieren:

* Loggen in tbMessagelog (beheertegel *Messagelog*). Deze logging staat aan indien de instelling aangevinkt is van *Sectie: OWB* en *Item: MessageLog*. In kolom *Getal1* van deze instelling staat het aantal dagen dat de loggingskaarten bewaard moeten blijven. Default is dat 31.
* Indien de instelling *Sectie: OWB* en *Item: Loggen* aangevinkt is dan worden de berichten onder een door OpenWave te bepalen naam (bijvoorbeeld 1.1345123012_VanOW_naarZaak) op een logmap van de server geplaatst (om die te zien zijn dus systeembeheerrechten noodzakelijk).

### Mapping resultaatomschrijvingen en GEMMA

De mapping van de resultaatomschrijvingen kunnen bijvoorbeeld uit de GEMMA-lijst komen:
Onbekend; Afgewezen; Buiten behandeling gesteld; Gegrond; Geweigerd; Ingetrokken; Niet hier bepaald; Niet nodig; Niet ontvankelijk; Niet vastgesteld; Ongegrond; Ontvankelijk; Toegekend; Vastgesteld; Verleend; Vervallen of Verwerkt.

### Uitzondering doorgeven einddatum en resultaat via updateZaak_Lk01

Indien het programmablok ActualiseerZaakstatus wordt aangeroepen voor het doorgeven van een einddatum en een resultaat kan het zijn dat dit niet met een actualiseerZaakstatus-bericht moet gebeuren, maar met een updateZaak-bericht. Dit is het geval indien:

* de zaak NIET speelt in een compartiment
* EN de instelling – *Getal1* van *Sectie: Koppeling ZAAK* en *Item: ResultaatViaUpdateZaak* heeft de waarde 1

OF indien

* de zaak WEL speelt in een compartiment  
* EN de instelling – *Getal1* van *Sectie: Koppeling ZAAK* en *Item: ResultaatViaUpdateZaak* heeft de waarde 2.

Deze tweede compartimentsinstelling zal in een volgende versie worden vervangen door een databaseveld in tbcompartiment.

Voor het verzenden van een asynchroon updateZaak_Lk01- bericht moet de kolom *Tekst* van *Sectie: Koppeling ZAAK* en Item: HTTPSoapAction_updateZaak_Lk01*
gevuld zijn met de waarde `[http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01.md)`.

LET OP: de soapactions kunnen ook ingesloten moeten zijn door dubbele quootjes, dus bijv. `"[http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01.md)"`.
