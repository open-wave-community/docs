# Sectie Adviezen

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de *Sectie: Adviezen* gerangschikt op item. Zie [Adviezen](/docs/probleemoplossing/module_overstijgende_schermen/adviezen.md).

## Items Configuratietabel

| **Item** | **Kolom** | **Omschrijving** |
|---|---|---|
| AdviescodeBoa | Aanvinkvakje |Indien aangevinkt en in kolom *Tekst* staat een verwijzing naar een adviesinstantiecode, dan zal de menu-optie *maak nieuwe handhavingszaak EN BOA-advies van dit traject* zichtbaar zijn om vanuit het inspectietraject een nieuwe advieszaak automatisch aan te maken bij de nieuwe handhavingskaart. |
| | Tekst |In de kolom *Tekst* moet de codering van de adviesinstantie komen, die gebruikt wordt bij de menu-optie *maak nieuwe handhavingszaak EN BOA-advies van dit traject*. |
| AdviescodeHostbijCompartiment | Tekst |Indien het advies valt onder een compartiment, maar het advies is aangevraagd bij de HOST-organisatie (de adviesinstantiecode komt voor in de hier gevulde *Tekst* (waarbij de coderingen gescheiden moeten zijn met een puntkomma, dus bijv. EZ;VROM;), dan geldt dat medewerkers van de Host-organisatie (dus inloggers die niet aan een compartiment gekoppeld zijn) toch de advieskaart kunnen muteren mits:

de inlogger advieseditrechten heeft,

En de bovenliggende kaart niet geblokkeerd is,

EN  de instelling *Sectie: Adviezen en Item: DateringDoorUpload* NIET aangevinkt is.

 Indien de instelling *Sectie: Adviezen en Item: DateringDoorUpload* WEL aangevinkt is, kunnen deze host-inloggers niet muteren, maar wel de uploadknop gebruiken. |
| AdviesIsZaak | Aanvinkvakje | Indien aangevinkt zijn de externe zaak/DMS kolommen bij adviezen zichtbaar en operationeel. |
| AdviesVerantwoordelijke | Getal1 | Wanneer in de beheertabel *Adviesinstanties* geen default behandelaar geconfigureerd is, dan kijkt het programma naar de waarde van *Getal1*.

Indien de waarde 1 is dan is de default behandelaar de ingelogde gebruiker.

Indien waarde 2, dan is de default behandelaar de actieve behandelaar van de hoofdzaak (tbinbehandelingbij)

Indien geen waarde blijft het veld *Interne behandelaar* leeg. |
| CategorieVerplicht | Aanvinkvakje |Indien aangevinkt dan moet bij het opvoeren van een nieuwe adviesaanvraag ook een item uit de tabel tbadvcategorie worden gekozen (via de tussentabel tbadvcatadvinstnn). |
| DagenTerug_OpenstaandLijst | Getal2 |De hier ingevulde waarde slaat op het aantal dagen terug dat het programma terug gaat in de tijd bij de lijst (mijn) uitstaande adviezen op het openingsscherm. Defaultwaarde = 365. |
| DagenTerug_RecentLijst | Getal2 |Wordt gebruikt voor de tegel en lijst *recent binnengekomen adviezen* op het openingsportaal. Defaultwaarde = 365. De lijst die getoond wordt zijn adviezen waarbij:

de datering advies (dddateringadvies) groter is dan vandaag MINUS het aantal dagen in *Getal2*

EN het resultaat advies (advies positief) heeft nog de waarde: nnb (nog niet bekend)

EN met een lege vervaldatum

EN er moet een actieve behandelaar zijn bij de bovenliggende zaak (tegel *In behandeling bij*). |
| DateringDoorUpload | Aanvinkvakje |Indien aangevinkt dan zal bij een upload van een document vanuit een advieskaart de kolom *datering advies* (tbadviezen.ddadvdatering) gevuld worden met de systeemdatum (indien die kolom leeg was). Hetzelfde geldt voor de kolom *adviesdatum* (tbadviezen.ddadvadvies). Indien aangevinkt betekent dat ook dat de kolom ddadvdatering niet muteerbaar is. |
| | Getal1 | Als de instelling bestaat maar NIET is aangevinkt dan zal de waarde 2 bij *Getal1* aangeven dat er in het detailscherm van het advies de kolom *adviesretourdatum* (tbadviezen.ddadvadvies) niet zichtbaar is. |
| Dvadvgeverposvisible | Aanvinkvakje |Indien aangevinkt dan wordt op het detailscherm van een advies de radiobuttonkolom Beoordeling Adviesgever zichtbaar naast de bestaande kolom Beoordeling Adviesaanvrager. In deze kolom kan de adviesgever zelf zijn/haar beoordeling geven. Tevens is hierdoor het veld *Soort advies/aanbeveling* niet meer zichtbaar. |
| KiesAdviseur | Aanvinkvakje |Indien aangevinkt dan zal de bij het aanmaken van een nieuw advies, het uitzetten van meerdere adviezen en in het detailscherm van het advies, een adviseur gekozen kunnen worden. Men kan kiezen uit medewerkers die adviseur zijn namens de gekozen adviesinstantie. De lijst *Mijn uit te brengen adviezen* zal vervolgens alleen de adviezen tonen voor de inlogger waarbij deze de gekozen adviseur is, en de adviezen waar GEEN adviseur is toegewezen. |
| MultiSelect | Getal1 | Indien *Getal1* de waarde 1 heeft (default) dan wordt de rij met te kiezen adviesinstanties die getoond wordt bij het starten van de wizard *meerdere adviezen uitzetten* vanuit de openstaande adviezenlijst bij een zaak, opgebouwd met alleen die instanties die nog niet voorkomen in de adviezen bij die zaak. Bij *Getal1* = 2 worden alle adviesinstanties opgenomen. |
| StandaardEmailTekstAanhef | Tekst | Wordt gebruikt voor de aanhef van de email vanuit advies naar het emailadres van de adviesinstantie.

Indien er voor de module van de zaak waaronder het advies hangt, een emailsjabloon bestaat met eigenschap *Is sjabloon voor standaardmail naar adviesinstantie?* aangevinkt dan wordt er niet naar deze instelling gekeken! |
| StandaardEmailTekstBody | Info | Wordt gebruikt voor de body van de email vanuit advies naar het emailadres van de adviesinstantie. De variabelen %zaaknaam%, %module%, %soortvergunning%, %zaakcode%, %lokatie%, %olonummer%, %soortvergunning%, %omschrijving% en %deeplink% worden hierbij met de juiste gegevens automatisch vervangen.

Indien er voor de module van de zaak waaronder het advies hangt, een emailsjabloon bestaat met eigenschap *Is sjabloon voor standaardmail naar adviesinstantie?* aangevinkt dan wordt er niet naar deze instelling gekeken. Er zal dan een mail worden opgesteld met body conform gedefinieerde body bij het sjabloon. |
| Teamzichtbaar | Aanvinkvakje | Indien aangevinkt dan is in het lijst- en detailscherm van een advies zichtbaar aan welk team deze is toegekend (welk team is verantwoordelijk). |
| Voorwiezichtbaar | Aanvinkvakje | Indien aangevinkt dan is in het lijst- en detailscherm van een advies zichtbaar aan welke persoon deze is toegekend (wie is verantwoordelijk). |
