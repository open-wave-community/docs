# Complex Verspreiden

## Voorwaarden en rechten

De wizard regelt het kopiëren van een verleende omgevingszaak naar een aantal andere aan te wijzen locatieadressen.
De wizard kan gestart worden indien aan een aantal voorwaarden is voldaan:

  * de omgevingszaak niet is geblokkeerd
  * de inlogger heeft het omgevingszaak-recht *mag verspreiden* aangevinkt staan (tbomgrechten.dlbomgverspr)
  * de besluitdatum gevuld is
  * het aard besluit de betekenis verleend heeft. Beheertegel *Afhandeling/Besluit omg/APV/milieu/gebruik*: detailscherm tbaardbesluit: *heeft betekenis verleend* moet aangevinkt staan (vwfrmomgvergunningen.dlverleend krijgt in dat geval de waarde 'T')  
  * de kolom *aantal eenheden* groter is dan 1
  * de soort omgevingszaak (beheerportaal Zaakbeheer, tegel *Zaaktypes omgeving*) de eigenschap *verspreidbaar als complex* aangevinkt heeft staan  
  * het aantal reeds verspreide zaken (andere omgevingszaken waarvan de kolom dnkeyparentverg is gevuld met de dnkeywaarde van de omgevingszaak die verspreid moet worden) kleiner is dan de kolom dnaantaleenheden. De reeds verspreide zaken zijn ook zichtbaar via de tegel *Verbonden aan groep*.

## Relatie oorspronkelijke complex en gekopieerde (verspreide) zaken

Het verspreiden betekent dat één afgesloten verleende zaak gekopieerd wordt naar één of meer andere adressen. De oorspronkelijke complexvergunning behoudt een relatie met deze verspreide zaken omdat de verspreide zaken een gevulde kolom dnkeyparentverg hebben die verwijst naar de dnkey van de oorspronkelijke complexvergunning. In de detailkaart van de omgevingszaak is dat zichtbaar in de kolom *Oorspr. complex*. Is deze kolom gevuld dan kan met de knop achter deze kolom naar de oorspronkelijke zaak worden genavigeerd.

Indien de complexe zaak nog geen verwijzing heeft naar een groep (dnkeygroepvergunning is null) dan wordt bij het verspreiden een groep aangemaakt in tbgroepvergunning met omschrijving de wavezaakcode (dvzaakcode) + (complex: + dnkey). De oorspronkelijke complexkaart en alle verspreide zaken krijgen alle een verwijzing naar deze groep (dnkeygroepvergunning). Via de tegel *Verbonden aan groep* op het omgevingsportaal zijn alle leden van de groep zichtbaar. 

### Wat wordt er gekopieerd?

Alle kolommen van de oorspronkelijke complexe zaak worden gekopieerd en krijgen hetzelfde vergunningsnummer/zaakcode als de oorspronkelijke complexvergunning. Daarop de volgende uitzonderingen voor de gekopieerde zaken:

  * dnkeyperceeladressen bevat de verwijzing naar een ander locatieadres
  * dnkeyparentverg krijgt de waarde van de dnkey van de oorspronkelijke complexe zaak
  * dnaantaleenheden krijgt de waarde 1.

Daarnaast worden de contactadressen, de onderdelen (tbtoestemmingen) en de kaarten uit tbinbehandelingbij mee gekopieerd.

### Procedure aanwijzen adressen

  * Het verspreiden gaat per range van huisnummers/letters per straat.
  * Het programma gaat eerst het maximum bepalen van het aantal adressen dat aangewezen kan worden (dnaantaleenheden minus het aantal reeds verspreid: een telling op grond van dnkeyparentverg = dnkey van de complexe zaak)
  * Het programma vraagt aan de gebruiker hoeveel zaken hij/zij denkt te verspreiden (in één straat). Dat aantal mag het maximum niet overschrijden.

Het programma vraagt woonplaats en straatnaam aan te wijzen. Vervolgens kunnen huisnummers van/tot, huisletters van/tot en een huisnummer-toevoeging worden opgegeven, en kan worden aangegeven of het gaat om *Even nummers, Oneven nummers of Doorlopend*.

Hierop zijn de volgende restricties van toepassing:

  * Indien huisnummer-toevoeging wordt ingevuld dan kan het programma geen range samenstellen en geldt:
    * dat huisnummer van en huisnummer totenmet gelijk moeten zijn en gevuld (getal kleiner/gelijk dan 99999)
    * dat huisletter van en huisletter totenmet gelijk moeten zijn (mogen wel leeg zijn).
  * Indien huisletter wordt ingevuld dan geldt:
    * dat huisnummer van en huisnummer totenmet gelijk moeten zijn en gevuld (getal kleiner/gelijk dan 99999)
    * dat zowel huisletter van en huisletter totenmet gevuld moeten zijn (met letter), waarbij huisletter vanaf kleiner of gelijk is aan huisletter totenmet.
  * Indien alleen huisnummer wordt ingevuld dan geldt:
    * dat zowel huisnummer van en huisnummer totenmet gevuld moeten zijn (met getal kleiner/gelijk dan 99999), waarbij huisnummer vanaf kleiner of gelijk is aan huisnummer totenmet.

Het programma telt ofwel alle dan wel de even of oneven mogelijkheden op grond van de ranges en vergelijkt deze uitkomst met het aantal opgegeven te verspreiden zaken.

Indien OK (kleiner of gelijk is OK), dan laat het programma in een lijst zien welke adressen gelinkt/aangemaakt zullen worden:

  * *Key bestaande locatie* gevuld betekent dat het adres reeds bestaat in OpenWave 
  * *Omg.kaart bestaat reeds* gevuld wil zeggen dat het aangewezen adres reeds gekoppeld is aan een omgevingszaak die een gevulde dnkeyparentverg heeft (dus die reeds verspreid is!!).

Het programma zal nu voor de items met een lege kolom *Omg.kaart bestaat reeds* een kopie maken van de oorspronkelijke complexe zaak, waarbij - indien *Key bestaande locatie*  leeg is - ook een nieuwe locatie wordt aangemaakt (tbperceeladressen).

De nieuw aangemaakte locaties worden - indien de BAG-koppeling aan staat - geverifieerd met de BAG.

