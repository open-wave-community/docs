Detailscherm Onderdelen/Activiteiten
====================================

De schermidentifier is: **MDDC_geefOmgActiviteitDetail.xml**.

Dit scherm kan worden aangeroepen vanuit de lijst
*Onderdelen/activiteiten* bij een omgevingszaak (tbtoestemmingen).

Error
-----

Het scherm geeft een foutmelding, indien:

-  er mogelijk een zelf gedefinieerde schermindeling gebruikt is die
   niet valide is
-  de inlogger geen kijkrechten heeft op de activiteiten/onderdelen bij
   een
   `omgevingszaak </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_onderdelen/lijst_onderdelen.md>`__.

Muteren
~~~~~~~

De kolommen kunnen gemuteerd worden indien:

-  de inlogger wijzigrechten heeft op de activiteiten/onderdelen bij een
   omgevingszaak
-  en die bovenliggende omgevingszaak niet is geblokkeerd
-  en de editschuif aan staat.

Daarop zijn de volgende uitzonderingen:

-  De kolom *Vervallen* (dlisvervallen) is niet muteerbaar indien de
   afgehandeld datum (ddbesluitdatum) van de bovenliggende omgevingszaak
   leeg is.
-  De kolom *Verloopdatum* (ddgeldigtm) is niet muteerbaar indien de
   kolom *Tijdelijk?* (dlistijdelijk) leeg is (niet aangevinkt).
-  De kolom *IsVervallenPer* (ddvervallen) is niet muteerbaar indien de
   kolom *Vervallen* (dlisvervallen) leeg is (niet aangevinkt).

De kolom *W011* is muteerbaar maar wordt in de volgende situaties
automatisch aangepast:

-  indien de activiteit een bouwactiviteit betreft (in beheer is de
   eigenschap *Werkzaamheden, gereedmelding, terugkoppeling bag en CBS
   van toepassing* (dluitvoering) toegewezen aan de soort activiteit) en

   -  de herziene kosten van de activiteit zijn gevuld en groter of
      gelijk aan 50.0000,
   -  OF de herziene kosten zijn NIET gevuld maar de vastgestelde kosten
      zijn groter of gelijk aan 50.000,
   -  OF vastgestelde en herziene kosten zijn beide niet gevuld, maar de
      kosten berekend vanuit ROEB zijn groter of gelijk aan 50.000 (zie
      `Roeb berekening vastg.
      kosten </docs/instellen_inrichten/roeb_berekening_vastg._kosten.md>`__),
   -  OF alleen de opgegeven kosten zijn gevuld en groter of gelijk aan
      50.000 dan zal *W011* automatisch aangevinkt worden

-  hetzelfde geldt ook andersom: stond *W011* aan en de kosten worden
   lager dan 50.000 voor de bouwactiviteit, dan zal *W011* automatisch
   uitgevinkt worden.

Let op: voorheen werd als bouwactiviteit gezien een activiteit waarvoor
in beheer de OLO-tag `LVO:onderdeelBouwen <LVO:onderdeelBouwen>`__
toegewezen was aan de soort activiteit. Vanaf versie 1.28 wordt er niet
meer gekeken naar deze tag, maar enkel naar de kolom
tbsrttoestemming.dluitvoering

Houd er rekening mee dat indien de vastgestelde of herziene kosten niet
zijn opgegeven, dat een wijziging in de ROEB van invloed kan zijn op de
eigenschap W011.

Zie voor CBS en gebruik van deze kolom W011 de knop CBS bij het kopje
triggers linksonder in `Detailscherm
Omgevingszaak </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken.md>`__

Woonmonitor
~~~~~~~~~~~

Het blok *Woonmonitor* is alleen zichtbaar indien er in het
beheerportaal *Zaakbeheer* voor de soort toestemming is aangegeven dat
hierbij woonmonitor van toepassing is. Indien dit het geval is kan men
in dit blok gegevens omtrent woonmonitor registreren voor het
onderdeel/de activiteit.

WKB en MBA
~~~~~~~~~~

Of een DSO-activiteit een MBA-activiteit is kan ingesteld worden in het
portaal *Zaakbeheer* (tegel *Soort activiteit/onderdeel*).

Of een DSO-activiteit een WKB-activiteit (melding of informatie) is kan
tevens ingesteld worden in het Zaakbeheer (tegel *Soort
activiteit/onderdeel*). Deze eigenschap wordt onder meer gebruikt in het
DSO Project portaal.

Triggers in het scherm zelf (achter de kolommen)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  **Email start werk naar BAGbeheerder**. Zichtbaar en enabled indien:

   -  de inlogger wijzigrechten heeft
   -  en de kolom *Start gemeld BAG* (ddstartnaarBAG) moet leeg zijn
   -  en de kolom *Start Werk* (ddstartwrkzhn) moet gevuld zijn
   -  en de BAGbeheerder moet emailadres hebben (beheertegel
      *Gemeentes*: het gaat om de gemeentes van de locatie adressen)
   -  en de inlogger moet emailadres hebben (beheertegel *Medewerkers*).

-  **Email gereed naar BAGbeheerder**. Zichtbaar en enabled indien:

   -  de inlogger wijzigrechten heeft
   -  en de kolom *Gereedmelding BAG* (ddnaarbaga) moet leeg zijn
   -  en de kolom *Opgeleverd* (ddopgeleverd) moet gevuld zijn
   -  en de BAGbeheerder moet emailadres hebben (beheertegel
      *Gemeentes*: het gaat om de gemeentes van de locatie adressen)
   -  en de inlogger moet emailadres hebben (beheertegel *Medewerkers*).
