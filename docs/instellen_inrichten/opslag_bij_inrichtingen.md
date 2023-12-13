# Opslagtabel bij inrichtingen

Het inrichtingportaal kan bij verschillende implementaties van OpenWave er nogal verschillend uitzien.

Wat betreft de benadering van de tabel tbmilopslag via één of meer tegels is dit onder meer afhankelijk van de rubricering.

## Rubricering

De inrichtingstabel tbmilopslag kan onder verschillende tegels op het inrichtingsportaal benaderd worden. De aanroep op de [tegeldefinitie](./portaldefinitie/README.md) bepaalt hoe de achterliggende lijst van opslagkaarten gefilterd wordt op rubriek.

Een van de attributen van deze tbmilopslag-tabel is de kolom dnrubriek. Dit is een foreign key naar tbmilrubriek (portaal Inrichtingenbeheer, tegel Milieurubrieken onder kolom Kenmerken en verplichtingen): Zie ook: [Milieurubrieken](../probleemoplossing/portalen_en_moduleschermen/inrichtingenbeheer/tegels_kolom_kenmerken_en_verplichtingen/milieurubrieken.md). In deze tabel kunnen rubrieken worden gedefinieerd waarbij aangeven kan worden of deze rubrieken van toepassing zijn op de tabel tbmilopslag. De tabel tbmilrubriek wordt gevuld aangeleverd en daarop zijn onderstaande voorbeelden van toepassing; de functioneel beheerder kan echter zelf coderingen aanpassen en of toevoegen.

Met behulp van die rubrieken kunnen de opslagkaarten verdeeld worden over één of meer tegels. Zo kunnen de opslagkaarten die gekoppeld zijn aan de rubriek met dvcode 3 (bodem) exclusief zichtbaar gemaakt worden via de tegeldefinitie Bodem (inrichtingportaal kolom Bodem: tegel: Bodem/opslagvoorz.). De actionaanroep op de tegel is in dit geval _getFlexList(tbmilopslag,tbmilinrichtingen,{id},3,V)_. Zo zijn er ook tegels die opslagkaarten tonen met tbmilrubriek.dvcode = 10 (tanks): _getFlexList(tbmilopslag,tbmilinrichtingen,{id},10,V)_.

Wanneer onder één tegel een lijst moet verschijnen met een combinatie van kaarten uit twee of meer rubrieken dan moet dit aangegeven worden met een hypen als scheidingteken in de actiondefinitie van de tegel. Bijvoorbeeld: _getFlexList(tbmilopslag,tbmilinrichtingen,{id},3-10,V)_ geeft een lijst van opslagkaarten die OF aan de rubriek bodem (3) of aan de rubriek tanks (10) zijn gekoppeld.
Indien alle opslagkaarten onder één tegel getoond moeten worden dan moet een lege parameter opnemen in de action:

_getFlexList(tbmilopslag,tbmilinrichtingen,{id},,V)_.

Het is dus aan de organisatie zelf om te bepalen in hoeveel rubrieken c.q. tegels zij hun opslagvoorzieningen willen onderverdelen door de action op de tegeldefinitie aan te passen en overbodige tegels eventueel weg te halen en door de tabel tbmilrubriek aan te passen.

Bij de standaarduitlevering is de opslagtabel verdeeld over de tegels:

- bodem (rubriek 3)
- tanks (rubriek 10)
- koeling (rubriek 5)
- externe veiligheid (9)
- rrgs met contour (12) en rrgs zonder contour (13)
- overig opslag/installaties (11 of 0)

## Nieuwe Opslagkaart

Een nieuwe opslagkaart kan worden aangemaakt

- vanuit de lijsten achter de opslagtegels (zie hierboven)
- vanuit de lijst met EV-activiteiten per inrichting ([Tegel REV BKL Activiteiten](../probleemoplossing/portalen_en_moduleschermen/inrichtingen_portaal/tegel_rev_bkl_activiteiten.md))

In beide gevallen kan OpenWave in de wizard - naast de verplichte benaming (dvnaamopslag) - vragen om:

- rubriek (dnrubriek). Dit item wordt niet gevraagd (maar wel automatisch toegekend) indien in de codetabel tbmilrubriek (onder kolom Kenmerken en verplichtingen in het portaal Inrichtingenbeheer) een niet-vervallen rij bestaat waarbij zowel de kolom dlopslag als dlisdefault is aangevinkt.
- wijze van opslag (dnkeymilsrtopslag) Dit item wordt niet gevraagd (maar wel automatisch toegekend) indien in de codetabel tbmilsrtopslag (onder kolom Kenmerken en verplichtingen in het portaal Inrichtingenbeheer) een niet-vervallen rij bestaat waarbij de kolom dlisdefault is aangevinkt.
- voorziening (dnkeymilvoorzopslag). Dit item wordt niet gevraagd (maar wel automatisch toegekend) indien in de codetabel tbmilvoorzopslag (onder kolom Kenmerken en verplichtingen in het portaal Inrichtingenbeheer) een niet-vervallen rij bestaat waarbij de kolom dlisdefault is aangevinkt.
- status (dnkeymilstatusopslag). Dit item wordt niet gevraagd (maar wel automatisch toegekend) indien in de codetabel tbmilstatusopslag (onder kolom Kenmerken en verplichtingen in het portaal Inrichtingenbeheer) een niet-vervallen rij bestaat waarbij de kolom dlisdefault is aangevinkt.
- referentiecontour (dnkeyrevrefcontour). Dit item wordt alleen gevraagd indien de opslagkaart wordt aangemaakt vanuit de lijst met BKL/EV-activiteiten per inrichting

### Blokken in detailscherm opslagkaart m.b.t. Register externe veiligheid

Zie [Register Externe Veiligheid](./register_exrterne_veiligheid.md).

- **REV activiteit referentie contour** In dit blok kan een bestaande opslagkaart gekoppeld worden aan een bij de inrichting gedefinieerde REV EV-activiteit.
- **Kenmerken referentie contour** Dit blok is alleen zichtbaar indien de opslagkaart gekoppeld is aan een REV EV-activiteit (tbmilopslag.dnkeymilbklactiviteiten is gevuld)
- **EV-contouren** Dit blok is alleen zichtbaar indien de opslagkaart gekoppeld is aan zowel een REV EV-activiteit (tbmilopslag.dnkeymilbklactiviteiten is gevuld) als aan een referentiecontour (dnkeyrevrefcontour is gevuld).

## Blokken in detailscherm opslagkaart m.b.t. Kenmerken/verplichtingen

- **Verplichtingen** Dit blok is alleen zichtbaar indien de kolom dvkenmerkverplichting van de opslagkaart de waarde "K" heeft (kenmerk). Die keuze is afhankelijk van het gekozen item bij de codetabel tbmilvoorzopslag. Zie: [Opslagvoorziening Kenmerk en Verplichting](./opslag_kenmerk-en_verplichting.md)
