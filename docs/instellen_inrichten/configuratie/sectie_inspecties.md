# Sectie Inspecties

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de _Sectie: Inspecties_ gerangschikt op item.

## Items Configuratietabel

| Item | Kolom | Omschrijving |
| ------------------------------ | ------------ | -------------- |
| DagenTerug_OpenInspectieLijst | Getal2 | Default 730. _Getal2_ slaat op het aantal dagen dat de lijst (mijn) open inspectietrajecten (d.m.v. view vwfrmmopeninsptrajecten) terug kijkt (gemeten op de ddrappel = startdatum). |
| DagenTerug_OpenBezoekenLijst | Getal2 | Default 365. _Getal2_ slaat op het aantal dagen dat de lijst (mijn) open inspectiebezoeken (d.m.v. view vwfrmomgorkestrator_insp) terug kijkt (gemeten op de ddgepland). |
| EMLToezichtControle | Aanvinkvakje | Indien aangevinkt en _Getal1_ bevat een geldige inspectietrajectsoort dnkey, dan wordt bij het inlezen van EML gegevens via tegel _Inlezen EML gegevens_ (operationsportaal), de nieuw aan te maken overtredingen geplaatst onder nieuw inspectietraject met als aanleiding dit type traject. |
| | Getal1 | Hier staat de dnkey van de inspectietrajectsoort (tbinspaanleiding) dat gebruikt wordt als de aanleiding van het EML inspectietraject. |
| OmgAutoAanmaak | Aanvinkvakje | Indien aangevinkt en de kolom _Tekst_ is gevuld met T en/of C dan zal bij het aanmaken van een nieuwe omgevingszaak met soort zaaktype = T (Toezicht) of C (Cyclisch Toezicht) automatisch een nieuw inspectietraject worden aangemaakt op naam van de inlogger en met dezelfde startdatum als die van de omgevingszaak. |
| | Getal1 | Indien gevuld wordt sowieso de einddatum (ddcontrole) van het inspectietraject gevuld met de startdatum. Indien de waarde verwijst naar een dnkey in tbinspresultaat wordt deze waarde overgenomen in dnkeyinspresultaat. |
| | Getal2 | Indien gevuld en de waarde verwijst naar een dnkey in tbinspaanleiding dan wordt deze waarde overgenomen in dnkeyinspaanleiding. |
| ResultaatVerplichtBijAfsluiten | Aanvinkvakje | Indien aangevinkt kan een inspectietraject niet worden afgesloten zonder resultaat. |
| | Getal1 | Indien de waarde 1, dan wordt het dropdown-menu voor de resultaatkeuze gehaald uit de koppeltabel tbaardbesluitsoortinsp (koppeling tussen tbinspaanleiding en tbaardbesluit). De tbinspecties.dnkeyinspaanleiding bepaalt in dat geval de mogelijkheden. Indien _Getal1_ een andere waarde heeft, dan wordt de resultaatkeuze uit de tabel tbinspresultaat gehaald. |