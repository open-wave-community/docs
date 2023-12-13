# Sluiten en Nieuw aanmaken Inspectietraject

Dit gebeurt wanneer de inlogger in het detailscherm van een inspectietraject op de schermknop achter de kolom _Afgerond_ heeft gedrukt.

## Rechten

- de inlogger moet lid zijn van een rechtengroep die voor de betreffende module het recht heeft om inspectietrajecten aan te maken
- de bovenliggende hoofdzaak mag niet geblokkeerd zijn.

Uitzondering blokkering: als de bovenliggende hoofdzaak is geblokkeerd kan er toch gemuteerd worden indien de
instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ aangevinkt is.
Dit geldt dan weer niet voor inspectietrajecten die horen bij een inrichting.

### Nieuw traject plannen

Indien gekozen wordt voor het plannen van een nieuw traject op basis van start- of einddatum, dan kan OpenWave een nieuwe datum voorstellen. Dit gebeurt als volgt:

- OpenWave kijkt eerst naar de toegekende branche en de daaraan gekoppelde controle frequentie. Deze frequentie wordt het uitgangspunt voor de berekening.
- Is bij de controle frequentie-definitie (beheerportaal _Inrichtingenbeheer_) een afwijking per gemeente gedefinieerd dan wordt deze afwijking het uitgangspunt.
- Is bij de inrichting een afwijking gedefinieerd, dan wordt deze inrichtingsafwijking het uitgangspunt voor de nieuwe toezichtdatum-berekening.

Als er gekozen wordt voor geen nieuw traject plannen is het eerste scherm in de wizard ook het enige scherm dat de gebruiker hoeft te doorlopen. Wanneer er op de knop _Volgende_ geklikt wordt, wordt het traject dan afgerond met de gekozen einddatum:

#### Bepaling termijn Cyclische inspecties bij inrichting

Indien het gaat om het afsluiten van een inspectietraject bij een inrichting en de aanleiding/soort inspectie verwijst naar een soort met de eigenschap Cyclisch = 'M' (beheertegel _Inspectietrajectsoorten_) dan zal het programma zelf een nieuwe datum voorstellen voor een nieuw traject op grond van het volgende:

- Indien de kolommen afwijking op cyclische inspectie aantal en eenheid (dvafwurgtermeenh en dnafwurgtermaantal) gevuld zijn (detailscherm van de inrichting) dan telt het programma deze periode op bij de afgehandeld datum als startdatum voor het nieuwe inspectietraject.
- Anders (geen afwijking) gaat het programma uit van de niet muteerbare aantal en eenheid kolommen van de cyclische inspectie op de inrichting detailkaart. Deze laatsten zijn gekoppeld aan de urgentieklasse van de inrichting (beheertegel _Urgentieklassen_). Per urgentieklasse kan op de standaardcyclus alhier per gemeente (de gemeente van de locatie) een uitzondering worden gemaakt.

Indien de inrichting niet gekoppeld is aan een urgentieklasse of die klasse heeft geen gevulde cyclus dan stelt het programma 1 jaar als periode voor.

#### Bepaling termijn Cyclische inspecties via SBI code/branche bij inrichting

Ook bij iedere SBI-code kan de urgentieklasse van een inrichting opgegeven worden. Dat is het veld _Code Controlefrequentie_.
Er kunnen altijd SBI-coderingen toegevoegd/verwijderd worden. De hoofd-SBI is bepalend voor onder welke branche de inrichting valt en daarmee welke controle frequentie aan de inrichting gekoppeld is. Zie verder bij [Cyclische Toezicht: controle frequentie](cyclische_inspecties.md).

#### Bepaling termijn Niet cyclische inspecties of inspecties bij zaken

- Bij een niet-cyclische inspectie, gekoppeld aan inrichtingen, zal het programma standaard een jaar voorstellen als periode tussen de oude en nieuwe inspectie.
- Bij inspecties gekoppeld aan zaken is dat een maand.

### Inspecteur nieuw traject/bezoek

In dat geval kijkt het programma naar de instelling _Sectie: InspectieMilieu en Item: Rechtengroepen_. In de kolom _Tekst_ staan gescheiden door een ; (puntkomma) de dnkeys van de rechtengroepen (tbrechten) genoemd die bedoeld zijn voor inspecteurs. Indien gevuld kan alleen een keuze gemaakt worden uit de medewerkers behorende bij een van deze rechtengroepen (en compartiment ok).

### Resultaat

Alleen indien de instelling _Sectie: Inspecties en Item: ResultaatVerplichtBijAfsluiten_ aangevinkt is, dan kan en moet hier een resultaat gekozen worden.

Afhankelijk van _Getal1_ van de instelling _Sectie: Inspecties en Item: ResultaatVerplichtBijAfsluiten_ komt deze uit tbinspresultaat (dit is het geval bij _Getal1_ <> 1 en dan wordt tbinspecties.dnkeyinpsresultaat gevuld) of uit de koppeltabel tbaardbesluitsoortinsp (in het geval dat _Getal1_ = 1 en dan wordt tbinspecties.dnkeyaardbesluitsoortinsp gevuld).

De koppeltabel tbaardbesluitsoortinsp bevat de koppelingen tussen de inspectietrajectsoorten (tbinspaanleiding) en tbaardbesluit. Dus de keuzemogelijkheden zijn bepaald door de inspectie-aanleiding.
De koppeltabel tbaardbesluitsoortinsp is te benaderen via het detailscherm van een inspectietrajectsoort (dus uit tbinspaanleiding: portaal _Zaakbeheer_, kolom _Handhaving en toezicht_, tegel _Inspectietrajectsoorten_).

Indien het resultaat via de koppeltabel uit tbaardbesluit komt, is het inspectietraject vanzelf voorzien van de ingestelde bewaartermijn bij de koppeling.

### Actualiseer zaakstatus in externe zaaksysteem

Het kan zijn dat het vullen of wijzigen van de afgehandeld datum gevolgd moet worden door een statuswijzigingbericht StUf zaak/DMS.
Zie hiervoor [Wijzig Status zaak/dms](wijzig_status_zaak_zaak_dms.md) bij de kopjes:

- Vullen van een lege afgehandeld datum bij inspecties
- Leegmaken van een gevulde afgehandeld datum bij inspecties
