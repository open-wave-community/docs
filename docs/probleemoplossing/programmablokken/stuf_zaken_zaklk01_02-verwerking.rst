Verwerking zakLk01 en zakLk02 berichten
=======================================

Deze Service wordt door externe programma(s) aangeroepen:

wsdl:
``[https://IP-ADRES:POORT/Wv_StufZkn_VSK/wsdl/IVerwerkSynchroneKennisgevingService](https://IP-ADRES:POORT/Wv_StufZkn_VSK/wsdl/IVerwerkSynchroneKennisgevingService.md)``.

De service kan geïnstalleerd zijn met https authenticatie (met een
proxyserver). De service kan achter een firewall geïnstalleerd zijn.

Berichtsoorten
--------------

De Service verwerkt de volgende StUF Zaken berichtsoorten tot een nieuwe
zaak in OpenWave (tenzij doublures):

-  zakLk01
-  zakLk02

De service verwerkt dus zowel asynchrone (zakLk01) als synchrone
(zakLk02) berichten. en dat gebeurt synchroon. Het bevestigingsbericht
in geval van zakLk01 is een Bv03 bericht geretourneerd (of Fo03) en bij
zakLk02 een Bv02Bericht (Fo02Bericht). Alleen berichten met de parameter
mutatiesoort = 'T' (blok parameters) worden verwerkt. Indien geen
mutatiesoort = 'T' wordt het bericht dus niet behandeld, maar OpenWave
stuur wel een bevestigingsbericht (Bv03bericht of Bv02bericht).

Verplichte Instellingen
-----------------------

-  Kolom *Tekst* van de *Sectie: Koppeling ZAAK* en *Item: Methode* moet
   de waarde **StUF-ZAKEN 310**. Deze instelling moet aangevinkt zijn.
-  Het **zaaktype** in het bericht (tag code onder
   entiteitstype="ZAKZKT") moet een mapping hebben in de OpenWave
   beheertabellen (zaaktypes omgeving of zaaktypes handhaving of
   APV/Overig of Milieu/gebruik). Er kunnen dus geen inspectiezaken
   aangemaakt worden.
-  Indien de combinatie gemeente (zie hieronder bij koppelen aan
   locatie) / zaaktype gekoppeld is aan
   `compartiment </docs/instellen_inrichten/compartimenten.md>`__ dan
   wordt aldaar de behandelaar opgehaald (beheertegel *Compartiment*).
   Is die niet gedefinieerd dan valt het programma terug op kolom
   *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item:
   dossierbehandelaar*. Die laatste MOET gevuld zijn.
-  Valt de zaak/gemeente NIET onder een compartiment dan kijkt het
   programma eerst naar de kolom *Defaultbehandelaar*
   (dvcodedefbehandelaar) bij het gevonden zaaktype in tbsoortomgverg of
   tbsoorthhzaak, tbsoortmilverg of tbsoortovverg of tbsoortmilverg.
   Indien deze niet is gevuld dan grijpt het programma terug op de
   verplichte instelling op kolom *Tekst* van de instelling *Sectie:
   Koppeling ZAAK* en *Item: dossierbehandelaar*. Hierin moet een valide
   medewerkerscode (tbmedewerkers.dvcode) staan.
-  *Getal2* van *Sectie: Koppeling Zaak Item: Onbekende vergunning* moet
   gevuld worden met een dnkey-waarde uit de beheertabel *Zaaktypes
   omgeving* die verwijst naar het zaaktype waarop de Service moet
   terugvallen indien het doorgegeven zaaktype in het zakLk01/02 bericht
   geen mapping heeft.
-  *Getal2* van *Sectie: Koppeling Zaak* en *Item:
   DummyLokatiePerceelkey* moet gevuld zijn met een dnkeywaarde uit de
   locatietabel (tbperceeladressen) die gebruikt wordt als **onbekende
   locatieadreskaart** in het geval dat de Service het doorgegeven adres
   in het zakLk01/02 bericht niet kan thuisbrengen.
-  Indien het zakLk01/02-zaaktype gemapt is naar een zaaktype van
   **APV/Overig** dan moet *Getal2* van *Sectie: Koppeling Zaak* en
   *Item: DummyMeldingAPVOVWerzKey* gevuld zijn met een dnkey-waarde uit
   de bijbehorende werkzaamhedentabel (tbovwerkz).
-  Indien het zakLk01/02-zaaktype gemapt is naar een zaaktype van
   **Milieu/gebruik** dan moet *Getal2* van *Sectie: Koppeling Zaak* en
   *Item: DummyMeldingMilWerzKey*\ gevuld zijn naar een dnkey-waarde uit
   de bijbehorende werkzaamhedentabel (tbmilwerkz).
-  Voor de aanvrager gebruikt de Service een OLO-instelling: In de
   brontabel *Adressoorten* moet één van de adressoorten in de kolom
   *OLO-tag* voorzien worden van de waarde 'isAangevraagdDoor'. Bij
   ontbreken van deze instelling neemt de Service **AVR (aanvrager)**
   (deze moet wel gedefinieerd zijn voor omgevingszaken en/of
   milieu/gebruik en/of APV/overig). Voor zakLk01/02-zaaktypes die
   gemapt staan naar een handhavingszaak zal de Service altijd HPC
   (handhaving primaire contactpersoon) als rol voor de initiator nemen.
-  Voor de gemachtigde gebruikt de Service een OLO-instelling: In de
   brontabel *Adressoorten* moet één van de adressoorten in de kolom
   *OLO-tag* voorzien worden van de waarde 'heeftGemachtigde'. Bij
   ontbreken van deze instelling neemt de Service **GEM (gemachtigde)**
   (deze moet wel gedefinieerd zijn voor omgevingszaken en/of
   milieu/gebruik en/of APV/Overig en/of handhavingen).

Facultatieve Instellingen
-------------------------

-  Wanneer de instelling *Sectie: Koppeling Zaak* en *Item:
   BestaandContactNietOverschrijven* aangevinkt staat, dan heeft dat tot
   consequentie dat wanneer tijdens het inlezen van de aanvrager of
   gemachtigde de Service tot de conclusie komt dat deze reeds bestaat
   als contactadres in OpenWave, er alleen een koppeling plaatsvindt met
   de nieuwe zaak zonder dat daarbij de bestaande contactadresgegevens
   worden overschreven. Die controle vindt bij een persoon (NPS) alleen
   plaats op het BSN-nummer + lege vervaldatum en bij een Bedrijf (NNP)
   op de combinatie handelsregisternummer + lege vervaldatum van de
   bijbehorende contactpersoon en bij een Vestiging (VES) op
   vestigingsnummer + lege vervaldatum.
-  Indien de instelling *Sectie: Koppeling Zaak* en *Item:
   AanmaakMappen* aangevinkt is zal de service proberen op de fileshare
   (!) mappen aan te maken conform de instellingen van kolom *Tekst* bij
   *Sectie: Aanmaakmappen*. De automatisch aan te maken mappen zullen in
   ieder geval gedefinieerd moeten zijn als UNC-paden en de
   zakLk01/02-service moet hiertoe rechten hebben.
-  Vanaf 1.29 is de OpenWave database in karakterset UTF-8. Dit betekent
   dat de database een groter aantal tekens aan kan dan voorheen. Het
   voorheen filteren van tekens die niet konden worden opgeslagen in de
   OpenWave database is daarom niet meer van toepassing. Indien in
   uitzonderlijke geval het toch nodig is dat berichtverkeer over DUSK
   WEL de oude filtering toepast van tekens, dan dient men instelling
   *Sectie: Dusk en Item: WIN1252* aan te maken en aan te vinken.

Ondersteunde entiteiten in zakLk01/02 berich
--------------------------------------------

-  Zaak (ZAK)
-  Zaaktype (ZAKZKT)
-  Heeft betrekking op (ZAKOBJ) en daarbinnen AOA of OPR en/ of VES
   en/of GEM (een locatieadres of vestiging)
-  Gemachtigde (ZAKBTRGMC) en daarbinnen NPS of NNP (natuurlijk of
   niet-natuurlijk persoon)
-  Aanvrager (ZAKBTRINI) en daarbinnen NPS of NNP (natuurlijk of
   niet-natuurlijk persoon) of VES (vestiging)
-  en de Status (ZAKSTT).

Nieuwe zaak/bestaande zaak
~~~~~~~~~~~~~~~~~~~~~~~~~~

De service beschouwt de waarde van de tag identificatie onder het blok
object als het externe zaaknummer.

-  Indien deze identificatie nog niet bestaat in de kolom dvintzaakcode
   van de module waarheen het zaaktype gemapt is, dan:

   -  indien de zaaktype-mapping verwijst naar een omgevingszaak dan:

      -  indien het OLO-aanvraagnummer (zie hieronder bij blok kenmerk)
         in het zakLk01/02-bericht gevuld is dan zoekt de Service dat
         OLO-nummer in de tabel omgevingszaken:

         -  indien OLO-nr gevonden dan wordt de externe zaakcode
            toegevoegd in de kolom dvintzaakcode mits deze leeg is
         -  indien OLO-nr niet gevonden dan wordt een nieuwe zaak
            aangemaakt met externe zaakcode en OLO-nr

   -  indien geen OLO-aanvraagnummer in bericht dan wordt een nieuwe
      zaak aangemaakt met externe zaakcode
   -  indien de zaaktype-mapping NIET verwijst naar een omgevingszaak
      dan dan wordt een nieuwe zaak aangemaakt met externe zaakcode.

-  Indien de identificatie al WEL bestaat in OpenWave dan zal de service
   geen nieuwe zaak aanmaken, maar hoogstens verrijken met
   OLO-aanvraagnummer en/of verkorte externe zaakcode (zie hieronder bij
   kenmerk).

Bij een nieuwe zaak worden ook processen toegevoegd die verbonden zijn
aan het betreffende zaaktype met attribuut automatisch.

Koppelen aan locatie en/of inrichting
-------------------------------------

De service onderzoekt het blok ``<heeftBetrekkingOp>``. Indien dit blok
niet aanwezig is zal een nieuwe zaak onder de onbekende
locatieadreskaart aangemaakt worden. Indien het blok
``<heeftBetrekkingOp>`` wel bestaat dan kijkt de service hierbinnen naar
het blok ``<vestiging>``. Indien binnen het blok ``<vestiging>`` de tag
``<vestigingsNummer>`` gevuld is dan:

-  indien de lengte van ``<vestigingsNummer>`` 12 posities is, wordt
   deze gezocht in de tbmilinrichtingen-tabel op in kolom dvvestigingsnr
-  indien de lengte van ``<vestigingsNummer>`` 8 posities is, wordt deze
   gezocht in dvkvknr van tbmilinrichtingen.

Indien gevonden (als er meerdere zijn: wordt de eerste de beste genomen)
dan is daarmee de inrichting bekend. De nieuwe zaak zal aan deze
inrichting worden gekoppeld. De locatie van de gevonden inrichting is
dan tevens de locatie van de nieuw aan te maken zaak.

Indien wel een blok ``<vestiging>`` maar de tag ``<vestigingsNummer>``
was leeg of ongelijk aan 12 of 8 posities dan zoekt de service de juiste
locatiekaart in de locatieadressen op grond van de
verblijfsadresgegevens in het blok ``<vestiging>``.

-  indien dat locatieadres van de vestiging niet gevonden: zal een
   nieuwe zaak onder de onbekende locatieadreskaart aangemaakt worden
-  indien locatieadres van de vestiging wel gevonden (als er meerdere
   zijn: wordt de eerste de beste genomen): dan is daarmee de locatie
   bekend.

Op dit locatieadres wordt tevens een nieuwe inrichting met de tags
handelsnaam, vestigingsnummer (indien 12 posities dan vestigingsnummer
en indien 8 posities dan KvK-nummer) gemaakt. Dit alles nog steeds als
het blok ``<vestiging>`` in het blok ``<heeftBetrekkingOp>`` bestaat.

Indien **geen** blok ``<vestiging>`` bestaat dan kijkt de service binnen
het blok ``<heeftBetrekkingOp>`` naar het blok ``<adres>`` met
entiteittype AOA of OPR. De service zoekt in dit geval de juiste
locatiekaart in de locatieadressen op grond van de adresgegevens in dit
blok.

-  Indien dat locatieadres niet gevonden of het blok ``<adres>`` bestaat
   niet dan zal een nieuwe zaak onder de onbekende locatieadreskaart
   aangemaakt worden.
-  Indien locatieadres wel wordt gevonden (als er meerdere zijn: wordt
   de eerste de beste genomen): dan is daarmee de locatie bekend.

Invoegen behandelaar
--------------------

Indien de combinatie gemeente (locatie) / zaaktype (soortzaak) gekoppeld
is aan `compartiment </docs/instellen_inrichten/compartimenten.md>`__
dan wordt aldaar de behandelaar opgehaald (beheertegel
*Compartimentsrechten*). Is die niet gedefinieerd dan valt het programma
terug op kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en
*Item: dossierbehandelaar*. Die laatste MOET gevuld zijn.

Valt de zaak/gemeente niet onder een compartiment dan kijkt het
programma eerst naar de kolom defaultbehandelaar (dvcodedefbehandelaar)
bij de definitie in het beheerportaal bij de soort zaak. Indien deze
niet is gevuld dan grijpt het programma terug op de verplichte
instelling op kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK*
en *Item: dossierbehandelaar*. Hierin moet een valide medewerkerscode
(tbmedewerkers.dvcode) staan.

Met de gevonden waarde - mits er nog geen behandelaar aan de zaak is
toegekend - wordt een nieuwe kaart in tbinbehandelingbij aangemaakt en
gekoppeld aan de zaak.

Invoegen Processen en checklistitems
------------------------------------

De processtappen van de processen die aan het gevonden zaaktype (de
soort zaak) in het beheerportaal-Nieuw verbonden zijn en waarbij de
eigenschap auto(matisch) is aangevinkt, worden aan de nieuwe zaak
toegevoegd. Indien de nieuwe zaak onder een compartiment is toegevoegd,
dan geldt ook nog dat het proces verbonden moet zijn aan dat
compartiment (tbprocedure.dnkeycompartiment).

Op grond van de ingelezen processen worden ook checklistitems, die in
het beheer gekoppeld zijn aan die processen, automatisch toegevoegd mits
ook daar de eigenschap auto(matisch) aangevinkt is.

Bijzonderheden
--------------

-  Het **blok kenmerk** kan 0 of meer keer voorkomen en elk blok heeft
   de tags *bron* en *kenmerk*.

   -  Indien bron = 'OLO' dan beschouwt de service het bijbehorende
      kenmerk als OLO-aanvraagnummer. Deze wordt dan toegevoegd aan de
      OpenWave-zaak mits het OLO-nummer aldaar nog niet gevuld was en
      het gaat om een omgevingszaak.
   -  Indien bron = gelijk aan de waarde van het stuurgegeven
      zenderapplicatie, dan beschouwt de service het bijbehorende
      kenmerk als het verkorte zaaknummer. Deze wordt dan toegevoegd aan
      de OpenWavezaak in de kolom dvdmszaakcode.

-  Vanuit een zakLk01/02 bericht kan **geen nieuwe inspectiezaak**
   aangemaakt worden. Wel kan ook hier een bestaande inspectiezaak
   verrijkt worden met het verkorte zaaknummer met het blok kenmerk. De
   kolom *Tekst* van de instelling *Sectie: Koppeling Zaak, Item:
   ZaaktypeInspectietraject* moet gevuld zijn met de gebruikte externe
   zaaktype voor inspectiezaken.

Logging
~~~~~~~

Het loggen van de zakLk01/02_berichten kan (gelijktijdig) op drie
manieren:

-  **Loggen in tbMessagelog** (beheertegel *Messagelog*). Deze logging
   staat aan indien de instelling aangevinkt is van *Sectie: OWB* en
   *Item: MessageLog*. In kolom *Getal1* van deze instelling staat het
   aantal dagen dat de loggingskaarten bewaard moeten blijven. Default
   is dat 31.
-  **Loggen van alle serviceverkeer** van de berichtenserver DUSK (waar
   zakLk01/02-service een onderdeel van is) in een logfile op een map op
   de server waar de zakLk01/02-service draait. De naam van de logfile
   en de mapnaam staan in een configuratiefile naast de Berichtenservice
   (dusk.ini). *Sectie: [Log]* en *Item: Level* met mogelijke waardes 1
   tot 9, waarbij 9 het diepst loggen betekent. In *Sectie: [Log]* en
   *Item: Bestand* staat de map + bestandsnaam van de logfile. Voor deze
   instellingen zijn systeembeheerrechten op de server waar de service
   draait nodig.
-  **Loggen van de zakLk01/02-berichten in en uit als file op een map**
   op de server waar de zakLk01/02-service draait. Deze mapnaam staat in
   een configuratiefile naast de Berichtenservice (dusk.ini). *Sectie:
   [Log]* en *Item: MapSaveBericht*. De namen van de files die hier
   komen te staan worden door de service zelf gegenereerd (bijvoorbeeld
   Bericht_Van_Zaak_Naar_Dusk_140602150536.xml. Om deze laatste logging
   te activeren voor zalLk01/02-berichten dient ook nog eens de
   instelling *Sectie: Koppeling ZAAK* en *Item: SaveBericht* aangevinkt
   te staan. Voor het definiëren van de map zijn systeembeheerrechten op
   de server waar de zakLk01/02-service draait nodig.

.. _instelling-mbt-probleem-gelijktijdigheid:

Instelling m.b.t. probleem gelijktijdigheid
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

De service voor het verwerken van OLO-bericht kan te gelijktijdig haar
werk doen met de service voor het verwerken van een zakLk01/02 bericht
om nieuwe zaak te verwerken. Beide controleren elkaar op het reeds
bestaan van een zaak c.q. OLO. Wanneer dat tegelijkertijd gebeurt kan
dat misgaan. Indien in de *Sectie: [LOG]* van de dusk.ini (de
configuratiefile naast de Berichtenservice DUSK) het *Item:
MapOloZaakBenBezig* is opgenomen en gevuld met een map verwijzing waarop
de service schrijf- en verwijderrechten heeft, dan:

-  gaat de service voor verwerken van zakLk01/02 eerst kijken of de file
   BezigMetOLo.txt bestaat. Zo ja dan (pollend) maximaal 5 seconden tot
   de file BezigMetOLO.txt niet meer bestaat. Als die file
   BezigMetOLO.txt niet meer bestaat dan maakt de zakLk01/02 service
   zelf een file met de naam BezigMetZaak.txt aan en verwerkt het
   zakLk01/02 bericht en vernietigt daarna de file BezigMetZaak.txt
-  gaat de services voor verwerken van OLO-bericht eerst kijken of de
   file BezigMetZaak.txt bestaat. Zo ja dan (pollend) maximaal 5
   seconden tot de file BezigMetZaak.txt niet meer bestaat. Als die file
   BezigMetZaak.txt niet bestaat dan maakt de OLO-service zelf een file
   met de naam BezigMetOLO.txt aan en verwerkt het OLO-bericht en
   vernietigt daarna de file BezigMetOLO.txt.

Voor bovenstaande instellingen zijn systeembeheerrechten op de server
waar de zakLk01/02 en OLO-service draait nodig.
