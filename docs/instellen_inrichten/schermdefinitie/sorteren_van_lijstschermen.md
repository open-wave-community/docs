# Sorteren van lijstschermen

Dit hoofdstuk gaat over het instellen van sorteren van lijstschermen in de [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie/README.md)

## Sortering bij starten van een lijst

Wanneer een lijstscherm wordt gestart kijkt OpenWave naar waarde van de kolom dvsortering van de tabel waarin de schermdefinities zijn opgeslagen (beheerportaal-NIEUW de tegels _Schermkolomdefinitie rapportages, Schermkolomdefinitie standaard-api, en Schermkolomdefinitie OW-api_). Het gaat om de kolom default sortering in het blok Flexlist.

**Overigens:** hoe te weten welke schermdefinitie bij welke lijst hoort
De identifier van het scherm bijv. MDLC_getTbCompartimentList.xml komt overeen met de waarde achter de tekst
screenidentifier in het infomatieballonnetje dat tevoorschijn komt bij klikken in lijst
rechtsonder op de lichtgrijze tekst met OpenWave versie-informatie.

Wanneer in deze kolom dvsortering niets staat wordt de lijst ASC (Ascending de kleinste waarde bovenaan) gesorteerd op primary key van de onderliggende tabel. In een aantal gevallen kan de sortering op een andere kolom dan de primary key hard in de programmatuur zijn opgenomen: dit is soms het geval bij de schermen van de OW-API.

Wanneer deze kolom dvsortering wel is gevuld zal de lijst met deze order by instructie worden gestart. Bijv. _dvnaam DESC_ wordt door OpenWave uitgelegd als: zoek in de tabel of view die aan de lijst ten grondslag ligt naar de kolom dvnaam en sorteer de lijst daarop in omgekeerde volgorde (desc of descend). Ook samenstellingen zijn mogelijk: dvnaam,dvvoorletter betekent sorteren op naam en daarbinnen (bij gelijke dvnaam) op dvvoorletter.
Indien ASC of DESC NIET zijn opgenomen dan sorteert OpenWave Ascending.

Indien echter de instelling _Sectie: Programma en Item: Collation_ aangevinkt staat en in de kolom _Tekst_ is een collation gedefinieerd (in dubbele quootjes zoals "fr-FR-x-icu") dan zal OpenWave ascending of descending sorteren volgens deze collation mits:

- de kolom een stringtype is (dus de kolomnaam begint met 'dv')
  - en in de kolom sortering is nog geen _collate_ opgenomen
  - Postgres 10 of later
  - en de lijst NIET is gebaseerd op vwfrminitialisatie of tbinitialisatie (want anders kan een foute invoer van de collation niet meer ongedaan gemaakt worden).

### Collation

De sortering in OpenWave wordt geregeld met een zogenaamde collation. De standaard collation is de POSTIX of C. Dit betekent dat de sortering case-sensitive is en dat diakrieten achter in de sortering komen. Deze default standaard collation wordt gebruikt indien:

- er geen collation informatie staat in de kolom dvsortering
- en de instelling _Sectie: Programma en Item: Collation_ uitgevinkt staat of niet bestaat.

Er zijn echter collations die NIET case-sensitive zijn en waarbij ook de diakrieten op hun 'natuurlijke' plaats terechtkomen. Wanneer dit wenselijk is raden wij aan om bijv. de collation "fr-FR-x-icu" te gebruiken in de kolom _Tekst_ van de instelling _Sectie: Programma en Item: Collation_. Dus met dubbele quootjes. en deze instelling aan te vinken. OpenWave zal de lijstschermen die gesorteerd zijn op een stringveld, volgens deze collation tonen.

Wanneer een lijst gestart wordt met een order by op grond van dvsortering van de tabel tbscreencolumns, dan zal OpenWave de ingestelde collation hieraan toevoegen (mits stringveld) tenzij er al een collation is opgenomen in dvsortering. Dan gaat dat laatste geval voor.

Een voorbeeld van eigen collate in dvsortering: _dvomschrijving collate "nl_NL.utf8" DESC_.

Collate mag niet toegepast worden op de schermen van tbinitialisatie of vwfrminitialisatie zelf.

**LET OP.** De collation kan alleen van toepassing zijn op stringvelden, Dus NIET op datums en getallen.
In OpenWave kan het dus alleen op kolomnamen die beginnen met 'dv'.
Bij een collation-definitie op een datum of getal zal de de lijst NIET wordt gestart.

**LET OP.** Er zijn heel veel mogelijke collations (taalafhankelijk).
De meeste gaan daarbij uit van een UTF8 karakterset.
OpenWave gebruikt sinds versie 1.29 de UTF-karakterset (voorheen was dit de WIN1252 karakterset). Maar dat wil niet zeggen dat alle utf8 collations gebruikt kunnen worden.
Een verkeerde collation-definitie heeft tot gevolg dat de lijst NIET wordt gestart of de sortering wordt genegeerd. Vooralsnog raden wij "fr-FR-x-icu" aan.

### Sortering veranderen als de lijst reeds getoond wordt

Dit gebeurt als de gebruiker op een label klikt bovenaan de lijst.

- Indien de instelling _Sectie: Programma en Item: Collation_ uitgevinkt staat wordt de lijst ascending of descending gesorteerd op de betreffende kolomwaardes met standaard collation (dus case-sensitive).
- Indien de instelling _Sectie: Programma en Item: Collation_ aangevinkt staat en in de kolom _Tekst_ is een collation gedefinieerd (in dubbele quootjes zoals "fr-FR-x-icu") dan zal OpenWave ascending of descending sorteren volgens de collation mits:
  - de kolom een stringtype is (dus de kolomnaam begint met 'dv')
  - en de lijst NIET is gebaseerd op vwfrminitialisatie of tbinitialisatie (want anders kan een foute invoer van de collation niet meer ongedaan gemaakt worden).
