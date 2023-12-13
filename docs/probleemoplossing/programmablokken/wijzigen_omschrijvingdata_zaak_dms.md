# UpdateZaak-bericht wijzigen metadata(StUF)

Het updateZaak-bericht kan ook gebruikt worden om een zaak af te sluiten. Normaliter gebeurt dit met een actualiseerZaakStatus bericht, maar kan desgewenst ook met een updateZaak-bericht. Zie hiervoor het kopje _Uitzondering doorgeven einddatum en resultaat via updateZaak_Lk01_ onderaan [Wijzigen Status externe zaak met Zaak/DMS](wijzig_status_zaak_zaak_dms.md).

## Gebruik van updateZaak-bericht

Dit lemma gaat verder alleen over het gebruik van updateZaak-bericht voor het doorgeven van een wijziging in bevoegd gezag of de aanvraagnaam of de startdatum.

### Zaaknaam

Indien:

- de instelling _Sectie: Koppeling Zaak en Item: UpdateZaakNaam_ is aangevinkt en de string _omschrijving_ voorkomt in de kolom _Tekst_ van deze instelling
- en de instelling _Sectie: Koppeling Zaak en Item: HTTPSoapAction_updateZaak_Lk01_ heeft de waarde `[http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01.md)`

dan zal een wijziging van de zaakomschrijving (bijv. tbomgvergunning.dvaanvraagnaam of tbhandhavingen.dvomsbouwwerk) doorgezet worden in een updateZaak_LK01 bericht aan het DMS.

### Bevoegd Gezag

Indien:

- de instelling _Sectie: Koppeling Zaak en Item: UpdateZaakNaam_ is aangevinkt en de string _instantie_ voorkomt in de kolom _Tekst_ van deze instelling
- en de instelling _Sectie: Koppeling Zaak en Item: HTTPSoapAction_updateZaak_Lk01_ heeft de waarde `[http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01.md)`

dan zal een wijziging van het bevoegd gezag (bijv. tbomgvergunning.dnkeyoinbevgez) of tbhandhavingen.dnkeyoinbevgez) doorgezet worden in een updateZaak_LK01 bericht aan het DMS.

### Startdatum

Indien:

- de instelling _Sectie: Koppeling Zaak en Item: UpdateZaakNaam_ is aangevinkt en de string _startdatum_ voorkomt in de kolom _Tekst_ van deze instelling
- en de instelling _Sectie: Koppeling Zaak en Item: HTTPSoapAction_updateZaak_Lk01_ heeft de waarde `[http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/updateZaak_Lk01.md)`

dan zal een wijziging van de startdatum (bijv. tbomgvergunning.ddaanvraag of thhandhavingen.ddverzoekdatum) doorgezet worden in een updateZaak_LK01 bericht aan het DMS.

### Overige voorwaarden

Voorwaarden zijn daarbij dat:

- indien de zaak speelt in een compartiment dan moet:
  - de kolom dldmsupdatezaakbericht van het betreffende compartiment aangevinkt zijn
  - en de kolom dvdmsmethode moet de waarde _Stuf Zaken 310_ hebben
- indien de zaak NIET in een compartiment speelt dan:
  - moet _Getal1_ van de instelling _Sectie: Koppeling Zaak en Item: UpdateZaakNaam_ de waarde 1 hebben
  - en moet kolom _Tekst_ van de instelling _Sectie: Koppeling ZAAK_ en _Item: Methode_ aangevinkt zijn en de waarde _Stuf zaken 310_ hebben.

Verder moet:

- de betreffende zaak een gevulde dvintzaakcode hebben (de identifier in het zaak/DMS)
- en moet de Status nog in behandeling of leeg zijn
- en moeten de stuurgegevens en endpoints en credentials vastgelegd zijn in de gemeentekaart van waar de zaak speelt (beheertegel _Gemeentes_: blok StUF zaak/DMS).

## Triggers

Het wijzigen van de omschrijving (in het element omschrijving van het blok object van het StUF-bericht) van een zaak wordt getriggerd door een verandering van:

- dvaanvraagnaam van een omgevingszaak
- dvomsbouwwerk van een handhavingszaak
- dvpublbouwwerk van de APV/Overige zaak (de nieuwe omschrijving wordt dan aardwerkzaamheden + dvpublbouwerk)
- dvpublbouwwerk van de milieu/gebruik zaak (de nieuwe omschrijving wordt dan aardwerkzaamheden + dvpublbouwerk)
- dvomschrijving van een infoaanvraag
- soort onderneming bij een horecazaak (de nieuwe omschrijving wordt _het uitbaten van_ + soort onderneming).

Het wijzigen van het bevoegd gezag van een zaak wordt in alle modules getriggerd door een verandering van de kolom dnkeyoinbevgezag. De nieuwe bevoegd gezag naam (uit tboin.dvorganisatie where dnkey = dnkeyoinbevgezag) komt in het blok **extraElementen** onderaan het blok **object** onder de attribuutnaam gedefinieerd door de kolom _Tekst_ van de instelling _Sectie: Koppeling Zaak Item: ElementnaamBevGez_. Defaultwaarde van deze attribuutnaam = _instantie_.

Het wijzigen van de startdatum (in het element startdatum van het blok object van het StUF-bericht) van een zaak wordt getriggerd door een verandering van:

- ddaanvraag van een omgevingszaak
- ddverzoekdatum van een handhavingszaak
- ddontvangsdatum van de APV/Overige zaak (de nieuwe omschrijving wordt dan aardwerkzaamheden + dvpublbouwerk)
- ddontvangstdatum van de milieu/gebruik zaak (de nieuwe omschrijving wordt dan aardwerkzaamheden + dvpublbouwerk)
- ddaanvraagdatum van een infoaanvraag
- ddaanvraagdatum bij een horecazaak (de nieuwe omschrijving wordt _het uitbaten van_ + soort onderneming).

Indien de instelling _Sectie: Koppeling ZAAK_ en _Item: UpdateZaakEenObject_ aangevinkt is, dan wordt de updateZaak-bericht verzonden met maar één blok object (normaal twee blokken object: de oude situatie en de nieuwe situatie).
