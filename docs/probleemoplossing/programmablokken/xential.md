# Xential

## Beschrijving

Er kan een koppeling gelegd worden met de Xential-sjabloongenerator. Dat betekent dat vanuit OpenWave een sjabloon van Xential wordt aangeroepen met de nodige merge-data. De gebruiker bewerkt dit document vervolgens ter plekke in Xential waarbij de merge-data door Xential reeds in het sjabloon zijn verwerkt.

Met de Xential opdracht _creeer document_ wordt het samengestelde document terug naar OpenWave verzonden en OpenWave plaatst het document vervolgens op de aangewezen plaats (fileserver of DMS) en - indien zo ingesteld - registreert het document in tbcorrespondentie.

## Noodzakelijke instellingen

### Endpoints en credentials

Zie [Sectie Xential](/instellen_inrichten/configuratie/sectie_xential.md) voor de instellingen in de configuratietabel (tbinitialisatie) met betrekking tot endpoints en credentials.

### Sjabloon verwijzing

Een OpenWave sjabloon (beheerportaal-Nieuw, kolom: Werkbeheer, tegel: Documentsjablonen) kan aangemerkt worden als Xentialsjabloon door de kolom _naam sjabloon in Xential_ (dvnaaminexternsjablprog) te vullen. Dit moet gebeuren met de Xential-groepsnaam gevolgd door /../ gevolgd door de Xential templatenaam. Bijvoorbeeld: _ditiseengroep/../testtemplate_.

Aangezien OpenWave zorg draagt voor de opslag van het samengestelde Xentialdocument en de registratie daarvan, zijn alle OpenWave-sjabloonkolommen nog steeds geldig.

Alleen de queries die gebruikt worden om een OpenWave sjabloon te mergen met kolommen uit de database krijgen bij een Xentialsjabloon een andere functie namelijk om een xml samen te stellen die door Xential gebruikt gaat worden om het sjabloon te mergen.

### Queries tbv xmlopmaak

Een mergeveld in een Xentialsjabloon wordt gedefinieerd door een tag-verwijzing naar die meegeleverde xml. Bijvoorbeeld indien een kolom wavezaakcode in Xential een tagverwijzing krijgt van `<root><zaak><identificatie>` dan moet die wavezaakcode dus onder die tagbenamingen in de xml worden aangeleverd.

Indien de volgende xml naar Xential gestuurd moet worden bij aanroep van een bepaalde template:

```xml
 <root>
   <zaak>
     <identificatie>2013S0148</identificatie>
     <startdatum>2017-01-20</startdatum>
   </zaak>
   <contactgegevens>
     <handelsnaam></handelsnaam>
     <vestigingsplaats>Bronsveld</vestigingsplaats>
   </contactgegevens>
 </root>
```

dan moet formquery1 als volgt zijn gevuld:

```sql
 select
 '<root>',
 '<zaak>',
 '<identificatie>' || a.dvzaakcode || '</identificatie>',
 '<startdatum>' || a.ddaanvraag || '</startdatum>',
 '</zaak>'
 from tbomgvergunning a
 where a.dnkey = :keyvergunning
```

en moet formquery2 als volgt zijn gevuld:

```sql
 select '<contactgegevens>',
 '<handelsnaam>' || coalesce(a.dvbedrijfsnaam,'') || '</handelsnaam>',
 '<vestigingsplaats>' || coalesce(a.dvachternaam,'') || '</vestigingsplaats>',
 '</contactgegevens>',
 '</root>'
 from tbcontactadressen a
 where a.dnkey = :keyadres
```

OpenWave plakt alle regels van de resultsets van de queries achter elkaar en zo ontstaat de gewenste xml.

Indien één van de tags in de query de waarde `<docidentifier/>` bevat dan wordt deze door OpenWave gevuld met een opgehaalde **documentidentifier uit het DMS** mits
de instelling _Sectie: Xential en Item: Genereervoorafdocidentifier_ aangevinkt is en _Getal1_ van _Sectie: Xential en Item: methode_ de waarde 2 heeft (dus gegenereerde document wordt via stuf/zaak in DMS opgeslagen).

OpenWave zal in dat geval, vóórdat Xential aangeroepen wordt, bij het DMS een documentidentifier opvragen (genereerDocumentidentificatie) en de tag `<docidentifier/>` vervangen door `<docidentifier>`hierstaatdeopgehaaldewaarde`</docidentifier>`.

**LET OP:** de tag `<docidentifier/>` MOET met kleine letters!!.

Op deze wijze kan de documentidentifier gebruikt kan worden in het Xential-sjabloon.

## Werkwijze

Wanneer de gebruiker met de OpenWave-wizard _creeer document_ een sjabloon aanwijst dat gekoppeld is aan een Xential sjabloon zal OpenWave met behulp van alle ingestelde endpoints en credentials een zogenaamd ticketID opvragen, waarbij een merge-xml op basis van de formqueries door OpenWave bij Xential wordt afgeleverd.

In de openwavetabel tbupload wordt een kaart aangemaakt met een door OpenWave op dat moment uitgetrokken UUID met metadata als vertrouwelijkheid, herkomst, bestemming e.d. Deze uuid en de filenaam zoals deze is opgegeven in het wave-sjabloon worden meegestuurd met de aanvraag van de ticketid.

Xential construeert een URL voor de gebruiker waarin template en ticketid zijn opgenomen. OpenWave stuurt de gebruiker door naar deze Xential URL in een apart tabblad. Op de Xential URL is de template geopend en gemerged met de aangeleverde xml uit OpenWave. OpenWave en Xential fungeren op dat moment onafhankelijk van elkaar.

Wanneer de gebruiker in Xential de opdracht geeft om het samengestelde document daadwerkelijk te creëren, wordt de webhookservice (endpointwebhookurl) van OpenWave aangeroepen door Xential met het document en het eerder doorgegeven UUID nummer en filenaam. Xential kan daarmee afgesloten worden.

De webhookservice van OpenWave slaat het document tijdelijk op (onder het UUID nummer+ \_ + de filenaam) in de uploadmap op de OpenWave server (kolom _Tekst_ van _Sectie: OWB, Item: TussenmapUploadfiles_) en roept vervolgens de interne OpenWave API uploadfile aan met het UUID nummer.

De OpenWave API haalt op grond van het UUID nummer de herkomst- en bestemmingsgegevens op uit de tabel tbupload en plaatst het document op de fileserver of met stuf zaak/dms in het DMS.

Zo nodig (_Sectie: DocumentregistReren Item: AlleHandmatigeUploads_ is aangevinkt of tbcompartiment.dldocregallehandmuploads is _T_) wordt een registratie aangemaakt in tbcorrespondentie.

Zo nodig - bij opslag in DMS - wordt de kolom dvurl van die correspondentiekaart automatisch geconstrueerd. Zie kopje _blok url_ bij [Detailscherm Geregistreerd Document](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/detailscherm_geregistreerd_document.md)
