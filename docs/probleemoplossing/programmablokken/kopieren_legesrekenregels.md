# Kopiëren Legesrekenregels

Dit kan op drie manieren:

- één rekenregel kopiëren met de kopieerknop onderaan de lijst binnen het detailscherm van een specifieke legessoort (beheertegel _Legesdefinitie_). Indien een rekenregel word gekopieerd:
  - vanaf een rij met een lege datumtotmet dan:
    - wordt de nieuwe datumvanaf default de oude datumvanaf +1 jaar
    - wordt deze datumtotmet op de oude kaart automatisch gevuld met de nieuwe datumvanf minus 1 dag.
  - vanaf een rij met een gevulde datumtotmet dan:
    - wordt de nieuwe datumvanaf default de oude datumtotmet +1 dag
    - wordt de nieuwe datumvtotmet default de oude datumtotmet +1 jaar.
- met de wizardknop onderaan de lijst met rekenregels binnen het detailscherm van een specifieke legessoort (beheertegel _Legesdefinitie_). Met deze optie wordt de meest recente set rekenregels van één legessoort gekopieerd.
- met de _Kopieer legesrekenregels_ vanuit het Operations-portaal onder kolom _Overig_. Met deze optie worden de meest recente sets rekenregels over alle legessoorten gekopieerd.

In beide wizard-gevallen wordt de uitvoer van kopieerwizard door een runnable gedaan (de taak wordt in een separaat proces zonder userinterface uitgevoerd). OpenWave controleert dat maar één iemand tegelijk deze wizard kan aanroepen:

Als de runnable begint wordt de _Datum_ van de instelling _Sectie: Operations Item: KopierenLegesRekenRegels_ gevuld met timestamp. De kolom _Tekst_ met medewerkerscode en _Getal1_ met 1. Indien klaar dan wordt _Getal1_ op null gezet. Zolang _Getal1_ de waarde 1 heeft, zal niemand de wizard kunnen uitvoeren (er verschijnt wel keurig een mededeling).

In de [operationslog](/docs/probleemoplossing/portalen_en_moduleschermen/servicecentrum/kolom_logs/operationlog.md) wordt ook een kaart aangemaakt onder code _KopierenLegesRekenRegels_ waarin het aantal gekopieerde rijen wordt bijgehouden. In de memo staat begin- en eindkey van de nieuwe aangemaakte rijen in tblegesberekeningen en de keys va de betrokken legessoorten waarbij nieuwe rijen zijn aangemaakt.

## Kopiëren van de rekenregels bij één legessoort

Het programma zoekt bij die betreffende legessoort naar de kaart in tblegesberekeningen met de grootste (jongste) dddatumvanaf waarvoor geldt dat de rekenregel niet is vervallen. De datumtotmet mag leeg zijn. Alle kaarten met diezelfde dddatumvanaf worden gekopieerd met ophoging van één jaar (zowel ddatumvanaf als - mits niet null - dddatumtotmet worden een jaar opgehoogd). Indien de oude datumtotmet leeg was, dan krijgt deze de waarde van de nieuwe datumvanaf minus 1 dag. De nieuwe datumtotmet kan wel weer leeg zijn.

## Kopiëren van rekenregels bij alle legessoorten

Het programma kopieert alle rekenregels uit tblegesberekeningen waarvoor geldt dat:

- de bijbehorende legessoort niet vervallen is
- de rekenregel zelf niet vervallen is
- de datumvanaf in het verleden ligt
- de datumtotmet in de toekomst ligt
- en er nog geen kaart bestaat bij de legessoort met een datumvanaf >= datumtotmet

De nieuwe datum vanaf (dddatumvanaf) wordt de oude datumtotmet (dddatumtotmet) + 1 dag. De nieuwe datumtotmet ((dddatumtotmet) wordt met een jaar verhoogd.
