# Zwemwater bij inrichtingen

[<img src="/_media../img/applicatiebeheer/instellen_inrichten/zwemwater_schema.png?w=600&amp;tok=b62f1c" class="media" loading="lazy" alt="" width="600" />](/_detail../img/applicatiebeheer/instellen_inrichten/zwemwater_schema.png?id=docs%3Aapplicatiebeheer%3Ainstellen_inrichten%3Azwemwater.md)

## Codetabel Zwemwater

Tabel tbmilzwemcodetabel.

In het beheerportaal *Inrichtingenbeheer* onder de tegel *Zwemcodetabel* (kolom *Overig*) kan men de keuzelijsten definiëren die de gebruiker tegen kan komen bij de tegel *Zwemplaats*, de daaronder hangende *Analyse Vragenlijst* en het blok *Zwemgelegenheid* in het inrichtingdetailscherm. De codetabel is gevuld met aangeleverde waardes, maar het is mogelijk in de codetabel zelf waardes toe te voegen of te verwijderen.

De kolommen van tbmilzwemcodetabel:

  - dvcode is de codering waarop keuzelijstitems gegroepeerd worden. Bijvoorbeeld *aard*, *lab* of *suppletie*.
  - dvomschrijving is de omschrijving van het item, dus datgeen wat je in de keuzelijst ziet.
  - ddvervaldatum is vervaldatum van de codering. Vanaf die dag kan het desbetreffende keuzelijstitem niet meer gekozen worden.

Tegeldefinitie [Zwemcodetabel](/probleemoplossing/portalen_en_moduleschermen/inrichtingenbeheer/tegels_kolom_overig/zwemcodetabel.md).

## Blok Zwemgelegenheid in het inrichting detailscherm

Dit blok is alleen zichtbaar wanneer de *dvbedrijfsrtcode* van de desbetreffende inrichting “ZWEM” is.

Deze *dvbedrijfsrtcode* is aan te maken vanuit het inrichtingenbeheer-portaal bij de tegel *Inrichting bedrijfssoort*. Wanneer er vanuit deze tegel een kaart bestaat die als code “ZWEM” heeft, is deze bij het inrichtingdetailscherm in te vullen bij het blok *Classificering*, onder de keuzelijst *Soort object/inrichting/bedrijf*. Zodoende wordt het nieuwe blok *Zwemgelegenheid* zichtbaar in het inrichtingendetailscherm, waar gegevens van de zwemgelegenheid genoteerd kunnen worden.

## (Zuiverings) Installatie en Zwemplaats

Tabellen tbmilzweminstallatie, tbmilzwemplaats en tbmilzwemanalyse.

Er zijn twee zwemwater-tegels in het inrichtingenportaal: (Zuiverings) Installatie ([Tegeldefinitie (Zuiverings) Installatie](/probleemoplossing/portalen_en_moduleschermen/inrichtingen_portaal/tegel_zuiverings_installatie)) en Zwemplaats ([Tegeldefinitie Zwemplaats](/probleemoplossing/portalen_en_moduleschermen/inrichtingen_portaal/tegel_zwemplaats)). Deze tegels zijn alleen zichtbaar mits deze aan de inlogger zijn toegekend, en de inlogger de juiste rechten heeft. Het inzien, wijzigen, aanmaken en verwijderen van gegevens is gekoppeld aan de Zwemwater-rechten bij een inrichting (*dlcmilinrzwwvsb, dlcmilinrzwwedt, dlcmilinrzwwins* en *dlcmilinrzwwdel* in tbmilrechten.md).

Er kunnen bij een zwemgelegenheid meerdere (zuiverings) installaties en meerdere zwemplaatsen toegevoegd worden. Per (zuiverings) installatie en zwemplaats kan een *Analyse Vragenlijst* toegevoegd worden. Deze is te benaderen vanuit het detailscherm van de installatie of zwemplaats. In het analyse vragenlijst detailscherm kunnen gegevens genoteerd worden die tijdens de analyse van de installatie of zwemplaats naar voren zijn gekomen.

De keuzelijsten die worden opgeroepen in het detailscherm van de zwemplaats en in het detailscherm van de analyse vragenlijst komen uit de codetabel tbmilzwemcodetabel. Hiervoor geldt net als hierboven vermeld dat het mogelijk is om zelf waardes toe te voegen of te verwijderen door de *Zwemcodetabel* in het *Inrichtingenbeheer* te benaderen.

