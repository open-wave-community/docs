Sectie Inspecties
=================

Hieronder de instellingen uit de
`configuratietabel </docs/instellen_inrichten/configuratie.md>`__
(tbinitialisatie) van de *Sectie: Inspecties* gerangschikt op item.

Items Configuratietabel
-----------------------

+--------------------------+--------------+--------------------------+
| Item                     | Kolom        | Omschrijving             |
+==========================+==============+==========================+
| Dagen                    | Getal2       | Default 730. *Getal2*    |
| Terug_OpenInspectieLijst |              | slaat op het aantal      |
|                          |              | dagen dat de lijst       |
|                          |              | (mijn) open              |
|                          |              | inspectietrajecten       |
|                          |              | (d.m.v. view             |
|                          |              | vwfrmmopeninsptrajecten) |
|                          |              | terug kijkt (gemeten op  |
|                          |              | de ddrappel =            |
|                          |              | startdatum).             |
+--------------------------+--------------+--------------------------+
| Dage                     | Getal2       | Default 365. *Getal2*    |
| nTerug_OpenBezoekenLijst |              | slaat op het aantal      |
|                          |              | dagen dat de lijst       |
|                          |              | (mijn) open              |
|                          |              | inspectiebezoeken        |
|                          |              | (d.m.v. view             |
|                          |              | v                        |
|                          |              | wfrmomgorkestrator_insp) |
|                          |              | terug kijkt (gemeten op  |
|                          |              | de ddgepland).           |
+--------------------------+--------------+--------------------------+
| EMLToezichtControle      | Aanvinkvakje | Indien aangevinkt en     |
|                          |              | *Getal1* bevat een       |
|                          |              | geldige                  |
|                          |              | inspectietrajectsoort    |
|                          |              | dnkey, dan wordt bij het |
|                          |              | inlezen van EML gegevens |
|                          |              | via tegel *Inlezen EML   |
|                          |              | gegevens*                |
|                          |              | (operationsportaal), de  |
|                          |              | nieuw aan te maken       |
|                          |              | overtredingen geplaatst  |
|                          |              | onder nieuw              |
|                          |              | inspectietraject met als |
|                          |              | aanleiding dit type      |
|                          |              | traject.                 |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Hier staat de dnkey van  |
|                          |              | de inspectietrajectsoort |
|                          |              | (tbinspaanleiding) dat   |
|                          |              | gebruikt wordt als de    |
|                          |              | aanleiding van het EML   |
|                          |              | inspectietraject.        |
+--------------------------+--------------+--------------------------+
| OmgAutoAanmaak           | Aanvinkvakje | Indien aangevinkt en de  |
|                          |              | kolom *Tekst* is gevuld  |
|                          |              | met T en/of C dan zal    |
|                          |              | bij het aanmaken van een |
|                          |              | nieuwe omgevingszaak met |
|                          |              | soort zaaktype = T       |
|                          |              | (Toezicht) of C          |
|                          |              | (Cyclisch Toezicht)      |
|                          |              | automatisch een nieuw    |
|                          |              | inspectietraject worden  |
|                          |              | aangemaakt op naam van   |
|                          |              | de inlogger en met       |
|                          |              | dezelfde startdatum als  |
|                          |              | die van de               |
|                          |              | omgevingszaak.           |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien gevuld wordt      |
|                          |              | sowieso de einddatum     |
|                          |              | (ddcontrole) van het     |
|                          |              | inspectietraject gevuld  |
|                          |              | met de startdatum.       |
|                          |              | Indien de waarde         |
|                          |              | verwijst naar een dnkey  |
|                          |              | in tbinspresultaat wordt |
|                          |              | deze waarde overgenomen  |
|                          |              | in dnkeyinspresultaat.   |
+--------------------------+--------------+--------------------------+
|                          | Getal2       | Indien gevuld en de      |
|                          |              | waarde verwijst naar een |
|                          |              | dnkey in                 |
|                          |              | tbinspaanleiding dan     |
|                          |              | wordt deze waarde        |
|                          |              | overgenomen in           |
|                          |              | dnkeyinspaanleiding.     |
+--------------------------+--------------+--------------------------+
| Result                   | Aanvinkvakje | Indien aangevinkt kan    |
| aatVerplichtBijAfsluiten |              | een inspectietraject     |
|                          |              | niet worden afgesloten   |
|                          |              | zonder resultaat.        |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien de waarde 1, dan  |
|                          |              | wordt het dropdown-menu  |
|                          |              | voor de resultaatkeuze   |
|                          |              | gehaald uit de           |
|                          |              | koppeltabel              |
|                          |              | tbaardbesluitsoortinsp   |
|                          |              | (koppeling tussen        |
|                          |              | tbinspaanleiding en      |
|                          |              | tbaardbesluit). De       |
|                          |              | tbinspec                 |
|                          |              | ties.dnkeyinspaanleiding |
|                          |              | bepaalt in dat geval de  |
|                          |              | mogelijkheden. Indien    |
|                          |              | *Getal1* een andere      |
|                          |              | waarde heeft, dan wordt  |
|                          |              | de resultaatkeuze uit de |
|                          |              | tabel tbinspresultaat    |
|                          |              | gehaald.                 |
+--------------------------+--------------+--------------------------+
