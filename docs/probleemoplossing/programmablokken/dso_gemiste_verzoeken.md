# DSO Gemiste Verzoeken

De lijst met DSO gemiste verzoeken is zichtbaar via de tegel _DSO gemiste verzoeken_ in de kolom notificaties van het servicecentrum-portaal. De lijst wordt getoond op basis van de tabel _tbgemisteverzoeken_. De lijst bestaat uit DSO-zaken (STAM-berichten) die opgenomen zouden moeten zijn in de OpenWave implementatie (op grond van bevoegd gezag of behandeldienst), maar dat niet zijn.

De tabel wordt periodiek aangevuld indien zo ingesteld via de taskscheduler (beheerportaal-nieuw: kolom: _Dieper beheer_) door de aanroep van de callable _importDSOGemisteVerzoeken_.

Voor het ophalen van gerelateerde verzoeken bij een omgevingzaak (verzoeken die door een ander bevoegd gezag of behandeldienst worden behandeld, maar wel spelen op dezelfde locatie): Zie: [DSO Gerelateerde Zaken](dso_gerelateerde_zaken.md)

## Ophalen en verwerken gemiste verzoeken

### Noodzakelijke instellingen

- Algemeen endpoint van de DSO-API verzoekafhandelen. Gedefinieerd in de instelling kolom _Tekst_ van _Sectie: DSO en Item: DSO-Verzoekafhandelen_ bijvoorbeeld: `[https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v2](https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v2.md)`
- Datumrange. Alleen verzoeken worden opgehaald die jonger zijn dan de systeemdatum minus _Aantal dagen terug_ in de kolom _Getal1_ van de instelling _Sectie: DSO-Verzoekafhandelen en Item: AantalDagenTerugGemisteVerzoeken_.
- Geografisch gebied. Het geografisch gebied wordt gedefinieerd door de kolom _Tekst_ van instelling _Sectie: DSO-Verzoekafhandelen en Item: PolygoonGemisteVerzoeken_. Dit moet een polygoon zijn in rijksdriehoek van x- en y-coördinaten:, waarbij het eerste paar gelijk is aan het laatste paar. X en y gescheiden door een komma en de paren gescheiden door een spatie. Bijvoorbeeld: _75000,550000 125000,550000 125000,515000 75000,515000 75000,550000_.

Het polygoon moet grosso modo het grondgebied bevatten van de OpenWave implementatie: dus bijvoorbeeld dat van een gemeente, of een provincie of een omgevingsdienst.

- OIN-nummer dat hoort bij de OpenWave implementatie dat gewhitelist is op het REM-certificaat waarmee de DSO API-aanroep wordt geautoriseerd. De kolom _Tekst_ van instelling _Sectie: SWF en Item: OINvanZender_ of, in geval van compartiment het veld \*OIN-nummer van compartiment t.b.v. aanmaken SWF-ruimte?
- in detailscherm van compartimentsinstellingen.

### Proces ophalen gemiste verzoeken

De callable _importDSOGemisteVerzoeken_ roept de DSO-API _verzoeken_zoek_ aan op het algemene endpoint met in het POST-bericht (in de body) het geografische gebied en de ingestelde datumrange.

Gezien de mogelijk grote geretourneerde resultset uit het DSO wordt de aanvraag gedaan in pages van 50 stuks. De DSO-API retourneert alle zaakverwijzingen binnen de opgeven datumrange waarvan de coördinaten van de project locatie vallen binnen het opgegeven grondgebied. Alles wat niet voor de OpenWave implementatie is moet er nog uitgefilterd worden. De afhandeling door OpenWave per geretourneerde zaakverwijzing is als volgt:

- Bestaat het verzoeknummer van de geretourneerde zaakverwijzing als zaak in tbomgvergunning
  - Zo ja, dan: Gaat het om intrekken of aanvullen?
    - Zo ja, Is de omgevingzaak in OpenWave al aangevuld of ingetrokken?
      - Zo ja, dan wordt een eventueel voorkomen van de zaakverwijzing in tbgemisteverzoeken verwijderd.
      - Zo nee, dan wordt een nieuwe rij aangemaakt in tbgemisteverzoeken mits deze nog niet bestaat.
    - Zo nee (wel gevonden en het gaat niet om intrekken of aanvullen), dan wordt een eventueel voorkomen van de zaakverwijzing in tbgemisteverzoeken verwijderd.
  - Zo nee, (de zaak bestaat niet in openwave), dan

Is de behandeldienst van de zaakverwijzing gevuld?
*Zo ja, Komt deze overeen met de kolom *Tekst* van instelling *Sectie: SWF en Item: OINvanZender* (dit is de OIN van de host: de hoofdorganisatie die OpenWave gebruikt)?
- Zo ja, dan wordt een nieuwe rij aangemaakt in tbgemisteverzoeken mits deze nog niet bestaat.
_Zo nee, dan wordt de geretourneerde zaakverwijzing genegeerd.
_ Zo nee (behandeldienst niet gevuld).

Komt bevoegd gezag overeen met de kolom _Tekst_ van instelling _Sectie: SWF en Item: OINvanZender_ (situatie bijv. gemeente Tiel of PNH)?
_Zo ja, dan wordt een nieuwe rij aangemaakt in tbgemisteverzoeken mits deze nog niet bestaat.
_ Zo nee, komt bevoegd gezag dan voor in kolom _Info_ van instelling _Sectie: SWF en Item: OINvanZender_ (situatie bijv. samenwerkingsverband BEL-gemeentes)?
_Zo ja, dan wordt een nieuwe rij aangemaakt in tbgemisteverzoeken mits deze nog niet bestaat.
_ Zo nee, komt bevoegd gezag dan voor in een van de rijen van tbcompartiment in de kolom tbcompartiment.dvswfoinzender (situatie bijv. compartiment Over-gemeente)?
_Zo ja, dan wordt een nieuwe rij aangemaakt in tbgemisteverzoeken mits deze nog niet bestaat.
_ Zo nee, dan wordt de geretourneerde zaak genegeerd.

Om dubbele uitvoering van de callable te vermijden wordt bij het starten de _Datum_ van de instelling _Sectie: Operations Item: importDSOGemisteVerzoeken_ gevuld met timestamp. De kolom _Tekst_ met medewerkerscode en _Getal1_ met 1. Indien klaar dan wordt _Getal1_ weer op null gezet.
In de operationslog (servicecentrum-portaal) wordt voortgang en resultaat bijgehouden onder de code: _importDSOGemisteVerzoeken_. De vraag-en antwoordberichten naar en van het DSO worden gelogd indien zowel _Sectie: OWB en Item: MessageLog_ aangevinkt is als de instelling _Sectie: DSO-Verzoekafhandelen en Item: MessageLog_.

## Ophalen en verwerken STAM-bericht van gemist verzoek

Onderaan de lijst met opgehaalde gemiste verzoeken bestaat de knop _Maak zaak van gemist verzoek_. De actie slaat op de actieve regel. OpenWave vraagt het STAM-bericht van het gemiste verzoek op en verwerkt deze tot een omgevingzaak in OpenWave (in de OpenWave API: _VerwerkDSOstambericht_).

**Noodzakelijke instellingen**

- Algemeen endpoint van de DSO-API verzoekafhandelen. Gedefinieerd in de instelling kolom _Tekst_ van _Sectie: DSO en Item: DSO-Verzoekafhandelen_ bijvoorbeeld: `[https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v2](https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v2.md)`
- OIN-nummer dat hoort bij de OpenWave implementatie dat gewhitelist is op het REM-certificaat waarmee de DSO API-aanroep wordt geautoriseerd. De kolom _Tekst_ van instelling _Sectie: SWF en Item: OINvanZender_ of, in geval van compartiment het veld \*OIN-nummer van compartiment t.b.v. aanmaken SWF-ruimte?
- in detailscherm van compartimentsinstellingen.
  - Let op: het kan zijn dat er een andere OINvanZender van toepassing is, dit indien er met meer dan 1 organisatie wordt gewerkt in OpenWave;
    - kolom _Info_ van instelling _Sectie: SWF en Item: OINvanZender_ bevat 1 of meer OIN nummers gescheiden door ;
    - en/of er bij het compartiment meer dan 1 OIN nummer bestaat: veld _OIN-nummer van compartiment t.b.v. aanmaken SWF-ruimte?_ bevat meer dan 1 OIN nummer gescheiden door ;
  - Indien er meer dan 1 OIN is waarvoor men Gemiste verzoeken wilt ophalen zal er bij het starten van de wizard gevraagd worden namens welke organisatie het gemiste verzoek opgehaald moet worden.

### Ophalen stambericht

Op het algemene endpoint wordt de API _verzoeken/’ + Verzoeknummer + ’/samenvatting’_ aangeroepen waarbij _verzoeknummer_ wordt gevuld door het DSO-verzoeknummer van het betreffende gemiste verzoek. Indien het OIN-nummer gerechtigd is, dan retourneert het DSO het originele STAM-bericht.

Indien zowel de instelling _Sectie: OWB, Item: MessageLog_ als de instelling _Sectie: DSO-Verzoekafhandelen en Item: MessageLog_ aangevinkt is, dan wordt deze vraag en antwoord gelogd.

Bij succes wordt de betreffende regel in tbgemisteverzoeken weggehaald en wordt het STAM-bericht in de eigen OpenWave API
_VerwerkDSOstambericht_ geschoten. Daar vindt de verwerking plaats conform de beschrijving [Verwerking DSO STAM berichten](verwerking_dso_stam_berichten.md).
