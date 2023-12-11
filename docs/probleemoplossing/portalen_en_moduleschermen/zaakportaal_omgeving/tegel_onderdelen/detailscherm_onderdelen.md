# Detailscherm Onderdelen/Activiteiten

De schermidentifier is: **MDDC_geefOmgActiviteitDetail.xml**.

Dit scherm kan worden aangeroepen vanuit de lijst _Onderdelen/activiteiten_ bij een omgevingszaak (tbtoestemmingen).

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft op de activiteiten/onderdelen bij een [omgevingszaak](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_onderdelen/lijst_onderdelen.md).

### Muteren

De kolommen kunnen gemuteerd worden indien:

- de inlogger wijzigrechten heeft op de activiteiten/onderdelen bij een omgevingszaak
- en die bovenliggende omgevingszaak niet is geblokkeerd
- en de editschuif aan staat.

Daarop zijn de volgende uitzonderingen:

- De kolom _Vervallen_ (dlisvervallen) is niet muteerbaar indien de afgehandeld datum (ddbesluitdatum) van de bovenliggende omgevingszaak leeg is.
- De kolom _Verloopdatum_ (ddgeldigtm) is niet muteerbaar indien de kolom _Tijdelijk?_ (dlistijdelijk) leeg is (niet aangevinkt).
- De kolom _IsVervallenPer_ (ddvervallen) is niet muteerbaar indien de kolom _Vervallen_ (dlisvervallen) leeg is (niet aangevinkt).

De kolom _W011_ is muteerbaar maar wordt in de volgende situaties automatisch aangepast:

- indien de activiteit een bouwactiviteit betreft (in beheer is de eigenschap _Werkzaamheden, gereedmelding, terugkoppeling bag en CBS van toepassing_ (dluitvoering) toegewezen aan de soort activiteit) en
  - de herziene kosten van de activiteit zijn gevuld en groter of gelijk aan 50.0000,
  - OF de herziene kosten zijn NIET gevuld maar de vastgestelde kosten zijn groter of gelijk aan 50.000,
  - OF vastgestelde en herziene kosten zijn beide niet gevuld, maar de kosten berekend vanuit ROEB zijn groter of gelijk aan 50.000 (zie [Roeb berekening vastg. kosten](/docs/instellen_inrichten/roeb_berekening_vastg._kosten.md)),
  - OF alleen de opgegeven kosten zijn gevuld en groter of gelijk aan 50.000 dan zal _W011_ automatisch aangevinkt worden
- hetzelfde geldt ook andersom: stond _W011_ aan en de kosten worden lager dan 50.000 voor de bouwactiviteit, dan zal _W011_ automatisch uitgevinkt worden.

Let op: voorheen werd als bouwactiviteit gezien een activiteit waarvoor in beheer de OLO-tag _<LVO:onderdeelBouwen>_ toegewezen was aan de soort activiteit. Vanaf versie 1.28 wordt er niet meer gekeken naar deze tag, maar enkel naar de kolom tbsrttoestemming.dluitvoering

Houd er rekening mee dat indien de vastgestelde of herziene kosten niet zijn opgegeven, dat een wijziging in de ROEB van invloed kan zijn op de eigenschap W011.

Zie voor CBS en gebruik van deze kolom W011 de knop CBS bij het kopje triggers linksonder in [Detailscherm Omgevingszaak](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken.md)

### Woonmonitor

Het blok _Woonmonitor_ is alleen zichtbaar indien er in het beheerportaal _Zaakbeheer_ voor de soort toestemming is aangegeven dat hierbij woonmonitor van toepassing is. Indien dit het geval is kan men in dit blok gegevens omtrent woonmonitor registreren voor het onderdeel/de activiteit.

### WKB en MBA

Of een DSO-activiteit een MBA-activiteit is kan ingesteld worden in het portaal _Zaakbeheer_ (tegel _Soort activiteit/onderdeel_).

Of een DSO-activiteit een WKB-activiteit (melding of informatie) is kan tevens ingesteld worden in het Zaakbeheer (tegel _Soort activiteit/onderdeel_). Deze eigenschap wordt onder meer gebruikt in het DSO Project portaal.

### Triggers in het scherm zelf (achter de kolommen)

- **Email start werk naar BAGbeheerder**. Zichtbaar en enabled indien:
  - de inlogger wijzigrechten heeft
  - en de kolom _Start gemeld BAG_ (ddstartnaarBAG) moet leeg zijn
  - en de kolom _Start Werk_ (ddstartwrkzhn) moet gevuld zijn
  - en de BAGbeheerder moet emailadres hebben (beheertegel _Gemeentes_: het gaat om de gemeentes van de locatie adressen)
  - en de inlogger moet emailadres hebben (beheertegel _Medewerkers_).
- **Email gereed naar BAGbeheerder**. Zichtbaar en enabled indien:
  - de inlogger wijzigrechten heeft
  - en de kolom _Gereedmelding BAG_ (ddnaarbaga) moet leeg zijn
  - en de kolom _Opgeleverd_ (ddopgeleverd) moet gevuld zijn
  - en de BAGbeheerder moet emailadres hebben (beheertegel _Gemeentes_: het gaat om de gemeentes van de locatie adressen)
  - en de inlogger moet emailadres hebben (beheertegel _Medewerkers_).
