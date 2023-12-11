# Leges

De schermidentifiers voor lijst en detail zijn: MDLC_geefLegesOverzicht.xml en MDDC_geefLegesDetail.xml.

Dit (lijst) scherm kan worden aangeroepen vanuit de zaakportalen APV/Overig, Bouw/sloop, Horeca en Omgeving (tegel *Leges*):

* De bron van het lijst- en detailscherm is de view vwfrmlegesregels (op basis van de tabel tblegesregels) met de legesregels bij een zaak.
* De lijst is zichtbaar indien de inlogger lid is van een rechtengroep die bij de betreffende module (omgeving, APV/overig, bouw/sloop ) het kijkrecht heeft op *Legesregels*.

### Muteren

Om te wijzigen:

* moet de inlogger lid zijn van een rechtengroep die bij de betreffende module (omgeving, APV/overig, bouw/sloop ) het wijzigrecht heeft op *Legesregels*
* moet de bovenliggende kaart niet geblokkeerd zijn
* EN - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de bovenliggende zaak bevatten en de gemeente waar die zaak speelt
* EN - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt in geen enkel compartiment voorkomen
* EN de editschuif aan staat.

Voor de kolommen **exportdatum** en **notanummer** gelden extra rechten. Normaliter worden deze kolommen automatisch gevuld bij het exporteren van legesregels naar journaalposten in een export/importbestand. Dit gebeurt door de operatie FIS export (zie portaal Operations). Indien deze kolommen gevuld zijn blokkeren ze daarmee ook het wijzigen van de andere kolommen van de kaart.

Wanneer de kolom **automatisch berekenen** aangevinkt is (staat default aan) dan resulteert het wijzigen van een kolom in het opnieuw berekenen van de kolom legesbedrag op grond van de gekozen legessoort, ontvangstdatum en eventueel de activiteit. Zie [Legesberekening](/docs/probleemoplossing/programmablokken/legesberekening.md).

De kolom **activiteit** kan alleen worden gekozen indien het gaat om een omgevingszaak.

De kolom **mutatiedatum** is niet muteerbaar en wordt door OpenWave automatisch gevuld bij een wijziging van de legessoort, de activiteit of het legesbedrag.

Met de schermknop *herberekenen* kan het **legesbedrag** opnieuw worden berekend (op grond van gekozen legessoort, ontvangstdatum en eventueel de activiteit).

De kolom **legessoort** kan alleen worden gekozen bij het aanmaken van een nieuwe legesregel.

### Nieuwe legesregel toevoegen

De inlogger moet lid zijn van een rechtengroep die bij de betreffende module (omgeving, APV/overig, bouw/sloop) het wijzigrecht heeft op *Legesregels*.

Allereerst kijkt het programma naar de instelling op zaaktypeniveau (beheerportaal *Zaakbeheer*) of de legesregel ingevoegd mag worden. Indien bij het betreffende zaaktype *GeenLegesBijDitZaaktype* is aangevinkt dan zal de inlogger een melding krijgen.

Het programma stelt de keuzelijst van mogelijke legessoorten als volgt samen:

* OpenWave kijkt eerst of er bij het betreffende zaaktype (portaal *Zaakbeheer*) gekoppelde legessoorten zijn gedefinieerd. Zo ja, dan vormen deze legessoorten de basisset.
* Indien er geen gekoppelde legessoorten zijn bij het zaaktype dan wordt op grond van de moduleletter (BOWI of C) eerst een selectie gemaakt (legessoort-omschrijving en legessoort-gemeente-id) uit de tabel tblegessoort waarbij de legessoortkolom *vantoepassingop* dezelfde moduleletter-waarde heeft. Nu vormt deze selectie van legessoorten de basisset.
* Indien in deze basisset een legessoort-gemeente-id (dus die viercijferige code uit de gemeentabel33) voorkomt gelijk aan gemeente-id van de locatie waar de zaak speelt, dan worden alleen die legessoorten van die basisset met die gemeente-id in de keuzelijst opgenomen.
* Anders, indien de gemeente-id van de betrokken locatie niet voorkomt in die basisset, dan worden alle legessoorten van die eerste selectie in de keuzelijst opgenomen, waarbij de legessoort-gemeente-id leeg is.

LET OP: Voor het samenstellen van de basisset wordt de vervaldatum van de legessoort vergeleken met de ontvangst/begindatum/aanvraagdatum van de bovenliggende zaak waar de legesregel voor wordt aangemaakt. Dus de te kiezen legessoort is zichtbaar indien de vervaldatum daarvan leeg is of groter (jonger) dan de aanvraagdatum.

### Activiteit en omgevingzaak

Indien  de legeskaart is aangemaakt bij een omgevingszaak, dan kan de inlogger een activiteit aanwijzen (uit de tabel onderdelen/activiteiten die bij die omgevingszaak zijn gedefinieerd) op grond waarvan de legesregel is aangemaakt. Die activiteitskeuze kan van invloed zijn op legesregels die gebaseerd zijn op andere legesregels (teruggave, opslag).

### Verplicht/niet verplicht

Op zaaktypeniveau (beheerportaal *Zaakbeheer*) kan bij de definitie van een zaaktype aangegeven worden of  wel of niet een legesregel verplicht is bij het zaaktype.
Indien aldaar:

* GeenLegesBijDitZaaktype dan heeft dat tot gevolg dat de gebruiker aan de voorkant geen legesregel kan toevoegen bij het betreffende zaaktype (er komt een melding : zie hierboven bij insert).
* NietVerplichtMaarWelToegestaan (defaultwaarde) mag dat wel, maar hoeft niet.
* LegesVerplicht zal dit worden gecontroleerd bij het afsluiten van de zaak. De zaak kan niet worden afgesloten (althans niet via de normale weg met wizard sluitzaak) indien er geen legesregel is opgenomen bij de zaak.

### Berekening legesbedrag

Dit gebeurt op grond van de rekenregels die bij de gekozen legessoort zijn gedefinieerd (beheertegel *Legesdefinitie*). Zie [Legesberekening](/docs/probleemoplossing/programmablokken/legesberekening.md).

### Triggers in lijstscherm linksonder

* Insertknop:
  * Zichtbaar indien de inlogger insertrecht heeft op *Legesregels* bij de betreffende module.
  * Enabled indien de bovenliggende zaak niet is geblokkeerd.
* Deleteknop:
  * Zichtbaar indien de inlogger verwijderrecht heeft op *Legesregels* bij de betreffende module.
  * Enabled indien de bovenliggende zaak niet is geblokkeerd.

### Triggers in detailscherm

* De schermknop **Herberekenen** (rekenmachientje):
  * Zichtbaar altijd.
  * Enabled indien:
    * de inlogger wijzigrechten heeft
    * de kolom exportdatum leeg is
    * de bovenliggende zaak niet is geblokkeerd.
