# Opslagvoorziening Kenmerk en Verplichting

De inrichtingstabel tbmilopslag, die onder verschillende tegels op het inrichtingsportaal benaderd kan worden (afhankelijk van gekozen rubriek) is uitgebreid met een nieuwe dochtertabel tbmilopslagverpl (onderaan het detailscherm van een opslagkaart in het blok **Verplichtingen**). Deze tabel is alleen onder bepaalde voorwaarden zichtbaar.

De tabel opslagvoorzieningen (tbmilvoorzopslag) achter de tegel **Opslagvoorziening** (kolom _Kenmerken en Verplichtingen_) van het beheerportaal _Inrichtingenbeheer_, is uitgebreid met de kolom dvKenmerkVerplichting. Een opslagvoorziening kan hiermee gekarakteriseerd worden als (K) enmerk of (V)erplichting. Deze kolom mag ook leeg zijn.

In de wizard waarmee een nieuw opslag bij een inrichting wordt gedefinieerd, is de dropdownlijst uit tbmilvoorzopslag met het kernmerk/verplichting in het eerste insertscherm opgenomen.

Bij de opslagkaart is dat kenmerk/verplichting zichtbaar (maar alleen te muteren via het beheer). Bij een inrichting kunnen dus kaarten bestaan die **geen kenmerk/verplichting** hebben, kaarten van type **Kenmerk** en kaarten van type **Verplichting**.

De gehanteerde definitie is als volgt:

- Kenmerk: hiermee wordt een installatie of voorziening bedoeld. Iets dat fysiek op de locatie aanwezig is. Bijvoorbeeld een vloeistofdichte vloer of koelinstallatie.
- Verplichting: hiermee wordt een terugkerend verplichting zoals onderzoek, rapportage, certificaat, keuring etc. bedoeld. Alles wat voor een bepaalde tijd geldig is en dus kan vervallen en dat mogelijk van toepassing is op een kenmerk.

Indien de opslagkaart het type Kernmerk heeft (dus eigenlijk: gekoppeld is aan een voorziening met het type Kenmerk), dan is onderaan de detailkaart van de opslagkaart in het blok _Verplichtingen_ het lijstje zichtbaar van Verplichtingen die aan die opslagkaart verbonden zijn.

Dit lijstje uit de tabel tbmilopslagverpl heeft twee verwijzingskolommen naar kaarten uit tbmilopslag die aan dezelfde inrichting zijn gekoppeld.
De eerste verwijzingskolom is gekoppeld aan de opslagkaart van type Kenmerk. De tweede kolom naar een kaart uit tbmilopslag van type Verplichting, maar met dezelfde inrichtingskey.

Om een nieuwe kaart aan deze tabel toe te voegen wordt een wizard gestart die:

- Controleert of de bovenliggende opslagkaart wel van type Kenmerk is
- Controleert of er andere kaarten zijn in de tabel tbmilopslag van type Verplichting en met dezelfde inrichtingskey en die nog niet bestaan in tbmilopslagverpl.

Als de controle ok is, kan de gebruiker een verplichting aanwijzen die daarmee specifiek aan die Kenmerk Opslagkaart wordt gekoppeld.
