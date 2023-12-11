Bodemenergiesystemen: WKO gegevens bij inrichtingen
===================================================

Indien **MBA activiteit Bodemenergiesysteem** van toepassing is op een
inrichting/locatiedossier, dienen er WKO gegevens geregistreerd te
worden. Dit zijn gegevens omtrent bodemenergiesystemen. In OpenWave
wordt 1 inrichting/locatiedossier gezien als 1 bodemenergiesysteem. Als
er meerdere installaties zijn, dan wordt er pèr installatie een
inrichting/locatiedossier aangemaakt in OpenWave.

Wat wordt verstaan onder een Bodemenergiesysteem
------------------------------------------------

Een bodemenergiesysteem is een installatie die bestaat uit tenminste
twee bronnen (buizen): een warmte en een koude bron, en een pomp. In de
zomer wordt warmte uit de lucht naar de warmte bron gepompt. In de
winter wordt deze warmte gebruikt om inrichting/locatiedossier te
verwarmen, en andersom met koude bron om inrichting/locatiedossier te
verkoelen in de zomer.

In zo'n bron/buis kunnen 1 of meerdere filters zitten. Per filter is er
een watervoerend pakket.

Voor het stuk buis waar een filter zit is een vergunning van toepassing:

In de vergunning staat hoeveel er verplaatst mag worden, en hoeveel er
minimaal verpompt moet worden voor de balans van het systeem. Ieder jaar
wordt er een rapport gemaakt met de daadwerkelijke gegevens. Dit rapport
wordt vergeleken met wat er in de vergunning staat.

In het inrichtingportaal kan men de WKO gegevens kwijt via de twee
tegels **WKO vergunningen** en **WKO Rapportages**.

De twee tegels zijn default niet toegewezen aan medewerkers. Dit kan
door functioneel beheer gedaan worden via beheertegel *Portal* en bij
het inrichtingportaal naar kolom *Bodem* te navigeren.

**Goed om te weten**: er is geen import/koppeling voor deze gegevens. De
twee tegels en hun onderliggende schermen zijn bedoeld voor het
handmatig opvoeren van de WKO vergunning gegevens en de gerapporteerde
gegevens per bodemenergiesysteem.

WKO vergunningen
----------------

Via de tegel *WKO vergunningen* kan een gebruiker een vergunning
aanmaken, wijzigen en verwijderen. Voor de rechten omtrent
zichtbaarheid, wijzigen, aanmaken en verwijderen van WKO vergunningen
zie onderstaand bij kopje *Rechten*.

Bij het aanmaken van een WKO vergunning dienen de volgende gegevens
opgegeven te worden:

-  **Geldig vanaf**: de datum vanaf wanneer deze vergunning geldig is
-  **Type WKO systeem**: keuze uit een Open of Gesloten systeem
-  **Soort WKO systeem**: keuze uit Doublet, Mono of Recirculatie
-  **Watervoerend pakket**: keuze uit 1, 1 en 2, 2, 2 en 3, 3.

Vervolgens kan in het detailscherm van de vergunning opgegeven worden
wat de vergunde gegevens zijn omtrent hoeveelheid **Grondwater** en
vergunde gegevens omtrent **Energie**.

Ook kan hier (indien bekend) een geldigheid tot datum opgegeven worden
en indien de vergunning vervallen is, een vervaldatum opgegeven worden.
De datums *Geldig vanaf*, *Geldig tot* en *Vervaldatum* zijn bepalend
voor of de vergunning geldend is bij de aan te maken WKO rapportages.
Dit wordt verder toegelicht bij onderstaand kopje *Geldende vergunning
bij rapportage*.

WKO rapportages
---------------

Via de tegel *WKO rapportages* kan een gebruiker een WKO rapportage
aanmaken, wijzigen en verwijderen. Voor de rechten omtrent
zichtbaarheid, wijzigen, aanmaken en verwijderen van WKO rapportages zie
onderstaand bij kopje *Rechten*.

Bij het aanmaken van een rapportage dient het **Jaar** van de meting
opgegeven te worden. Ieder jaar kan dus een nieuwe rapportage aangemaakt
worden waar de metingen van het bodemenergiesysteem voor dat jaar worden
gerapporteerd.

Voor iedere rapportage kunnen de volgende gegevens worden teruggevonden/
genoteerd worden in Openwave:

-  **Algemeen**: het jaar waarin de metingen zijn gedaan en eventueel de
   vervaldatum van de rapportage
-  **Vergunde afwijking energiebalans**: hier staat de Afwijkende balans
   zoals deze bij de geldende WKO vergunning is opgegeven
-  **Gemeten hoeveelheden grondwater (in m3)**: per maand kan hier de
   Warmtelevering en Koudelevering genoteerd worden. Totalen worden
   berekend en getoond. Ook is hier te zien wat de maximale vergunde m3
   per maand is
-  **Energie hoeveelheden (in MWth)**: de vergunde Warmte- en
   Koudelevering zijn hier zichtbaar. De gebruiker kan hier per kwartaal
   de cijfers voor de gemeten Warmte- en Koudelevering noteren. Ook hier
   worden totalen berekend en getoond
-  **Gemeten Onttrekking en infiltratie (in graden C)**: de vergunde
   waardes voor Delta T warm en koud worden hier getoond. De gebruiker
   kan hier per maand voor zowel Warmte- als Koudelevering de gegevens
   omtrent Gemiddelde Onttrekking en Gemiddelde Infiltratie opgeven
-  **Gemeten spuiwater (in m3)**: per maand kan hier de gemeten
   hoeveelheid spuiwater genoteerd worden. Ook is hier de vergunde Max
   spuiwater getoond en wordt er een totaal bijgehouden van de
   genoteerde metingen
-  **Infiltratietemperatuur (in graden C)**: per maand is hier voor
   zowel Warmtelevering als Koudelevering op te geven wat de maximale
   infiltratie temperatuur was. Ook is hier de vergunde Max infiltratie
   temperatuur getoond
-  **SPF**: de vergunde SPF wordt getoond en de gemeten SPF is op te
   geven.

De vergunde gegevens die zichtbaar zijn in het detailscherm van een WKO
rapportage horen bij de voor dat rapportjaar geldende vergunning. Hoe
bepaalt wordt welke vergunning dat is, is terug te lezen bij onderstaand
kopje *Geldende vergunning bij rapportage*.

Geldende vergunning bij rapportage
----------------------------------

Anders dan de gebruiker gewend is in OpenWave, zal er niet per WKO
rapportage de vraag worden gesteld welke vergunning van toepassing is.
Deze afweging is namelijk opgenomen in de view onderliggende aan de WKO
rapportages (vwfrmmilwkorapp).

De view bepaalt op basis van het rapportagejaar, welke WKO vergunning er
toen geldig was. Er kan altijd maar 1 geldende vergunning zijn per
rapportage. De logica voor bepaling welke vergunning geldend is voor het
rapport is als volgt:

-  de WKO vergunning mag niet vervallen zijn in het rapportagejaar
-  het jaar van de *Geldig van* datum is kleiner of gelijk aan het
   rapportagejaar en jaar van *Geldig tot* moet leeg zijn, OF gelijk aan
   OF groter zijn dan het rapportagejaar
-  indien er WKO vergunningen zijn die elkaar qua periode overlappen,
   dan pakt de view als geldende vergunning diegene met de meest recente
   *Geldig van* datum

Voorbeeld:

Stel er zijn vier WKO vergunningen aanwezig bij een
inrichting/locatiedossier met de volgende datums:

-  Vergunning 1: Geldig van 01-01-2017, Geldig tot 31-12-2021,
   Vervaldatum is leeg
-  Vergunning 2: Geldig van 01-01-2020, Geldig tot 01-05-2020,
   Vervaldatum is leeg
-  Vergunning 3: Geldig van 01-06-2020, Geldig tot is leeg, Vervaldatum
   is leeg
-  Vergunning 4: Geldig van 01-01-2020, Geldig tot 31-12-2020,
   Vervaldatum is 01-05-2020

Een WKO rapportage uit jaar 2020 zal als geldende WKO vergunning,
Vergunning 3 hebben.

Deze is namelijk geldend in 2020, zonder *Geldig tot* datum, niet
vervallen en is recenter dan Vergunning 2. Vergunning 4 is niet van
toepassing, deze heeft een gevulde vervaldatum.

Een WKO rapportage uit jaar 2021 zal als geldende WKO vergunning, OOK
Vergunning 3 hebben.

Vergunning 1 zal niet van toepassing zijn, ook al is deze in de jaren
2017 tot en met 2021 in principe geldig, omdat Vergunning 3 een *Geldig
van* datum later heeft dan Vergunning 1 en wel voorliggend aan jaar
2021. Omdat de *Geldig tot* datum van Vergunning 3 niet gevuld is, is
deze ook nog geldig in 2021 (en 2022, 2023 enzovoorts).

Rechten
-------

Er zijn vier nieuwe rechten aangemaakt bij module Inrichtingen, terug te
vinden in het beheerportaal-Nieuw onder tegel *Functionele rechten*,
inrichtingen-rechten en blokje *WKO (Bodemenergiesystemen)*: Zichtbaar
(dlcmilinrwkovsb), Nieuw (dlcmilinrwkoins), Wijzigen (dlcmilinrwkoedt)
en Verwijderen (dlcmilinrwkodel).

Een gebruiker dient de corresponderende rechten te hebben voor het
kunnen aanmaken, bewerken, verwijderen en inzien van de WKO vergunningen
en rapportages.

De rechten zijn geldend voor zowel WKO rapportages als vergunningen.
