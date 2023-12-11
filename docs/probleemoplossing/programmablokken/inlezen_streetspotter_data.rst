Inlezen Streetspotter data
==========================

In de kolom *Import* op het portaal *Operations* staat de ingang voor
het verwerken Streetspottergegevens onder tegel **Inlezen Streetspotter
data** (geen standaard uitgeleverde tegel).

**LET OP:** Afhankelijk van het aantal te verwerken regels kan het gaan
om een geheugen intensieve proces. Het is de bedoeling dat alleen de in
Streetspotter afwijkende inrichtingen m.b.t. OpenWave worden opgenomen
in het testbestand. Mocht er voor gekozen worden om toch een bestand met
alle inrichtingen te laten verwerken door OpenWave dan raden we aan deze
alleen na reguliere werktijd uit te voeren.

Inlezen aangeleverde Streetspotter gegevens
-------------------------------------------

OpenWave zal data uit Streetspotter doorlopen gaande inrichtingen, op
basis van de Excelfile die wordt geüpload via de wizard onder tegel
*Inlezen Streetspotter data*. Dit leidt (mogelijk) tot wijzigen van
huidige inrichtinggegevens in OpenWave dan wel tot aanmaken van nieuwe
inrichtingen in OpenWave.

Structuur files
---------------

De inlogger dient een Excelfile aan te wijzen op zijn of haar device met
daarin op 1 tabblad de te verwerken data uit Streetspotter.

In de Excelfile moet één van de eerste 5 regels een regel zijn die
bestaat uit de volgende kolommen (in de documentatie hier zijn de
kolommen gescheiden met een komma) in deze specifieke volgorde(!):

``dvinrichtingnr,dvopbidentificatiecode,dvgemeentenaam,dvobjplaats,dvobjstraat,dvobjhuisnummer,dvobjhuisletter,dvobjhuisnrtoevoeg,dvobjpostcode,dvinrichtingnaam,dvbedrijfsrtoms, dvbw_archiefnr,dfmilcat,dvhandelsnaam,dvkvknr,dvvestigingsnr,dvmelding,dvomschrijving,dvcodemedewerker,ddmelddatum``

De door OpenWave te verwerken Streetspotter data, begint direct onder
deze bovenstaande regel. Vanaf hier wordt dus de daadwerkelijk door
OpenWave te verwerken gegevens verwacht.

Het programma verwacht dat de regels gevuld zijn conform de hierboven
genoemde kolommen. Daarbij wordt een regel met een lege waarde van
dvinrichtingnr beschouwd als een nieuw aan te maken inrichting. Is
dvinrichtingnr gevuld dan wordt de regel beschouwd als het wijzigen van
een bestaande inrichting.

Verder moet (in ieder geval voor nieuwe inrichtingen) OF het
dvopbidentificatiecode gevuld zijn met BAGID voor verblijfobject dan wel
nummeraanduiding, en/OF de overige adresgegevens. Verder moet de
datumkolom *ddmelddatum* de vorm dd-mm-jjjj hebben. Dit betekent dat het
de eigenschap *Datum* heeft in Excel.

**LET OP:** tekens uit de UTF-8 karakterset die niet voorkomen OF niet
gelijk zijn aan de tekens van karakterset WIN 1252, kunnen niet verwerkt
worden in de OpenWave database. Het inleesprogramma zal bij tegenkomen
van zo'n teken in de Excel, de desbetreffende actie overslaan. Dit kan
zijn wijzigen van specifiek veld voor een inrichting maar afhankelijk
waar het teken tegengekomen wordt, ook in geheel overslaan van de
inleesregel. Dit teken kan niet opgenomen worden in de logging en zal
dus niet zichtbaar zijn als reden waarom een regel overgeslagen is/de
inrichting niet aangemaakt is. Wel wordt de teller netjes bijgehouden.

Verwerking
----------

Het starten van het verwerkingsproces (wordt gedaan met een runnable)
leidt tot:

-  aanmaken van een regel in de tabel tboperationslog (ook in portaal
   *Operations*) met codering *Streetspotter data inlezen* en het moment
   van starten
-  vullen van de *Datum* van de instelling *Sectie: Operations* *Item:
   InlezenStreetspotterData* met timestamp. De kolom *Tekst* wordt
   gevuld met medewerkerscode en *Getal1* met 1. Hiermee wordt voorkomen
   dat een tweede persoon ook een importproces Streetspotter data start.

Het programma loopt de regels in de Excel één voor één door waarbij
geldt dat als er geen gevulde inrichtingsnummer is, het een regel
betreft voor aanmaken van een nieuwe inrichting. Is het
inrichtingsnummer wel gevuld in de Excelfile dan beschouwt de
programmatuur deze als een verzoek tot update van een bestaande
inrichting.

Te verwerken gegevens zijn: inrichtingnaam, adres (alleen bestaande
adressen: er worden geen nieuwe adressen aangemaakt), soort bedrijf,
archiefnummer, milieu categorie, handelsnaam, KVK-nummer,
vestigingsnummer en het aanmaken van een nieuwe melding bij de
inrichting. De gegevens worden verwerkt in de tabellen tbmilinrichtingen
en tbmilalert.

De inleesactie wordt uitgevoerd in een separaat proces zonder
userinterface. De gebruiker kan via het lijstscherm van de operationslog
(te vinden via tegel *Operationslog*) het zogenaamde logboek
terugvinden.

Indien klaar dan wordt:

-  de einddatum/tijd op de tboperationslog-kaart gezet
-  de status op de tboperationslog-kaart gevuld met 'Klaar'
-  *Getal1* van de instelling *Sectie: Operations* *Item:
   InlezenStreetspotterData* weer op 0 gezet: de tegel wordt hiermee
   weer vrijgegeven.

Te wijzigen inrichtingen
~~~~~~~~~~~~~~~~~~~~~~~~

Voor het wijzigen van bestaande inrichtingen zal het programma de
inrichting zoeken o.b.v. het inrichtingnummer in de Excelfile. Wordt
deze niet gevonden dan zal er geen wijziging plaatsvinden en zal de
regel op de uitvallijst (in het verslag bij het logboek) komen. Wordt de
inrichting wel gevonden dan worden de volgende gegevens gewijzigd:

-  **adres** zoals gevonden via BAGID (of adresgegevens)
-  **inrichtingnaam** zoals in kolom *dvinrichtingnaam*
-  **Soort bedrijf** wordt gevuld indien er een record bestaat in de
   corresponderende codetabel voor het opgegeven
   bedrijfsoortomschrijving in kolom *dvbedrijfsrtoms*. Is
   dvbedrijfsrtoms leeg, dan zal Soort bedrijf niet overschreven worden
   met een lege waarde maar de originele waarde blijven staan
-  **Typering act. besluit** (Milieucategorie) wordt gevuld indien er
   een record bestaat in de corresponderende codetabel voor de opgegeven
   omschrijving in kolom *dfmilcat*. Is dfmilcatleeg, dan zal Typering
   act. besluit niet overschreven worden met een lege waarde maar de
   originele waarde blijven staan
-  **Brandweer archiefnummer** wordt gevuld met de tekst 'Klasse ' plus
   de waarde van kolom *dvbw_archiefnr* (mag leeg zijn)
-  **Handelsnaam** wordt gevuld met de waarde van kolom *dvhandelsnaam*
   (mag leeg zijn, indien leeg dan wordt huidige waarde van Handelsnaam
   niet overschreven). Indien in kolom *dvhandelsnaam* meerdere
   handelsnamen staan, dienen deze gescheiden te zijn door teken: #. Het
   programma zal als handelsnaam overnemen de waarde van dvhandelsnaam
   voor de eerste #
-  **KvK-nummer** wordt gevuld met de waarde van kolom *dvkvknr* (mag
   leeg zijn, indien leeg dan wordt huidige waarde van KvK-nummer niet
   overschreven)
-  **Vestigingsnummer** wordt gevuld met de waarde van kolom
   *dvvestigingsnr* (mag leeg zijn, indien leeg dan wordt huidige waarde
   van Vestigingsnummer niet overschreven)
-  wordt dfmilcat of dvbedrijfsrtoms niet gevonden dan worden de overige
   wijzigingen wel uitgevoerd voor de bestaande inrichting. Er zal een
   foutmelding gezet worden in de kolom tboperationslog.dvlog dat soort
   bedrijf/dan wel Milieucategorie niet gewijzigd kan worden. In het
   logboek is dus terug te lezen als de gegevens niet konden worden
   overgenomen.

Nieuwe inrichtingen
~~~~~~~~~~~~~~~~~~~

Bij het aanmaken van de nieuwe inrichtingen zal het programma het adres
waarop de inrichting moet worden aangemaakt, eerst proberen te vinden
via het opgegeven BAG id in de Excelfile. Wordt deze niet gevonden dan
wordt gezocht op de overige adresgegevens uit de Excelfile. Indien er
geen bestaand adres wordt gevonden in OpenWave, zal de inrichting niet
worden aangemaakt en komt de regel op de uitvallijst.

De inrichting wordt aangemaakt met de volgende gegevens waarbij de
kolomnamen verwijzen naar de Excel-gegevens:

-  **adres** zoals gevonden via BAGID (of adresgegevens)
-  **inrichtingnaam** zoals in kolom *dvinrichtingnaam*
-  **Soort bedrijf** wordt gevuld indien er een record bestaat in de
   corresponderende codetabel voor het opgegeven
   bedrijfsoortomschrijving in kolom *dvbedrijfsrtoms*
-  **Typering act.** besluit wordt gevuld indien er een record bestaat
   in de corresponderende codetabel voor de opgegeven omschrijving in
   kolom *dfmilcat*
-  **Brandweer archiefnummer** wordt gevuld met de tekst 'Klasse ' plus
   de waarde van kolom *dvbw_archiefnr* (mag leeg zijn)
-  **Handelsnaam** wordt gevuld met de waarde van kolom *dvhandelsnaam*
   (mag leeg zijn)
-  **KvK-nummer** wordt gevuld met de waarde van kolom *dvkvknr* (mag
   leeg zijn)
-  **Vestigingsnummer** wordt gevuld met de waarde van kolom
   *dvvestigingsnr* (mag leeg zijn)
-  wordt dfmilcat of dvbedrijfsrtoms niet gevonden dan wordt de
   inrichting nog steeds aangemaakt maar zal er een foutmelding gezet
   worden in de kolom tboperationslog.dvlog. In het logboek is dus terug
   te lezen als de gegevens niet konden worden overgenomen.

Nieuwe melding
~~~~~~~~~~~~~~

Indien een regel heeft geleid tot OF het aanmaken van een nieuwe
inrichting OF het wijzigen van een bestaande inrichting dan wordt er ook
een nieuwe melding aangemaakt (tbmilalert) met:

-  **code medewerker** zoals opgegeven in kolom *dvcodemedewerker*
-  **melding** zoals opgegeven in kolom *dvmelding*
-  **omschrijving** zoals opgegeven in kolom *dvomschrijving*
-  en **datum** zoals opgegeven in kolom *ddmelddatum*
-  kan OpenWave geen medewerker vinden o.b.v. de opgegegeven
   dvcodemedewerker? dan wordt er GEEN nieuwe melding aangemaakt en zal
   er een foutmelding worden gezet in de kolom tboperationslog.dvlog.

Opstellen logboekverslag
~~~~~~~~~~~~~~~~~~~~~~~~

Het verslag wordt als volgt opgesteld: indien er foutmeldingen zijn
(inrichtingen kunnen niet worden aangemaakt, inrichting is niet
gevonden, melding kan niet worden aangemaakt etc.) zullen deze bovenaan
in het verslag staan daarna volgt de volgende telling:

-  Aantal verwerkt:
   ``<aantal regels die het programma doorlopen heeft>``
-  Aantal aangepast: ``<aantal inrichtingen die gewijzigd zijn>``
-  Aantal nieuw: ``<aantal inrichtingen die aangemaakt zijn>``
-  Aantal overgeslagen: ``<aantal regels dat is overgeslagen>``
-  Aantal niet aangemaakt: ``<aantal niet aangemaakte inrichtingen>``

De uitvallijst/het verslag is terug te vinden in de memo van het
operations logboek: na uploaden van de Excelfile met de Streetspotter
data kan de voortgang van verwerking hier worden gevolgd.
