DSO Gerelateerde Zaken
======================

De lijst met DSO gerelateerde zaken is zichtbaar via de tegel *DSO
gerelateerde zaken* op het omgevingsportaal. De tegel is alleen
zichtbaar indien er gerelateerde zaken zijn bij de betreffende
omgevingzaak. De lijst wordt getoond op basis van de tabel
*tbgerelateerdezaken*. De lijst bestaat uit DSO-zaken die door een
andere bevoegd gezag of behandeldienst worden behandeld, maar wel
degelijk spelen op dezelfde locatie als de betreffende omgevingzaak. De
tabel wordt periodiek aangevuld indien zo ingesteld via de
**taskscheduler** (beheerportaal-nieuw: kolom: *Dieper beheer*) door de
aanroep van de callable *importDSOGerelateerdeZaken*.

Voor het ophalen van DSO gemiste verzoeken, waarbij het gaat om DSO
STAM-berichten die - mogelijk ten onterechte - niet terug te vinden zijn
in OpenWave: zie: `DSO Gemiste
Verzoeken </docs/probleemoplossing/programmablokken/dso_gemiste_verzoeken.md>`__

Ophalen en verwerken gerelateerde zaken
---------------------------------------

Noodzakelijke instellingen
~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Algemeen endpoint van de DSO-API verzoekafhandelen. Gedefinieerd in
   de instelling kolom *Tekst* van *Sectie: DSO en Item:
   DSO-Verzoekafhandelen* bijvoorbeeld:
   ``[https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v2](https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v2.md)``
-  Datumrange. Alleen gerelateerde zaken worden opgehaald waarvan de
   datum valt binnen de periode aantal dagen terug (en aantal dagen
   vooruit) vanaf de aanvraagdatum van de betreffende omgevingzaak. Bij
   het ontbreken van deze instelling wordt van de default waarde 3
   uitgegaan. Kolom *Getal1* van *Sectie: DSO-Verzoekafhandelen en Item:
   AantalDagenTerugGerelateerdeVerzoeken)*.
-  OIN-nummer dat hoort bij de OpenWave implementatie dat gewhitelist is
   op het REM-certificaat waarmee de DSO API-aanroep wordt
   geautoriseerd. De kolom *Tekst* van instelling *Sectie: SWF en Item:
   OINvanZender*.

Proces ophalen gerelateerde zaken
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

De callable *importDSOGerelateerdeZaken* loopt alle openstaande OpenWave
DSO-zaken na waarvoor geldt dat:

-  verzoeknummer gevuld
-  en DSO-projectid gevuld
-  en afhandel/ingetrokken-datum leeg is
-  en waarbij de startdatum (tbomgvergunning.ddaanvraag) valt binnen een
   aantal dagen terug gerekend vanaf de systeemdatum. Dat aantal dagen
   terug wordt gedefinieerd in de datumrange (zie hierboven). Indien de
   Taskscheduler elke dag de gerelateerde verzoeken ophaalt is een
   instelling van 2 dagen voldoende.

Deze datumrange-instelling bepaalt tevens de datumrange voor de aanroep
naar de DSO-API, immers: een DSO Verzoekbericht wordt direct gesplitst
in bijvoorbeeld milieudeel naar omgevingsdienst en bouwdeel naar
gemeente: dat laatste deel is dan de gerelateerde zaak (gezien vanuit de
omgevingsdienst).

Per gevonden OpenWave-DSO-zaak wordt de DSO-API *verzoeken_zoek*
aangeroepen op het algemene endpoint met in het POST-bericht (in de
body) het verzoeknummer en de ingestelde datumrange.

De DSO-API retourneert alle zaakverwijzingen binnen de opgeven
datumrange waarvan de coördinaten van de projectlocatie overeenkomen met
die van het opgegeven verzoeknummer (dus deze afweging maakt het DSO:
Openwave geeft geen coördinaten door, maar een verzoeknummer).

De DSO-API geeft nul of meer gerelateerde zaken terug. Er is een tabel
tbgerelateerdezaken waarin deze zaken mogelijk worden opgenomen.

Die afhandeling door OpenWave per gerelateerde zaakverwijzing is als
volgt:

-  Bestaat het verzoeknummer van de gerelateerde zaakverwijzing in de
   tabel tbgerelateerdezaken bij de openstaande OpenWave-DSO-zaak? \*Zo
   ja, dan wordt de gerelateerde zaakverwijzing genegeerd (is blijkbaar
   al eerder opgenomen).

   -  Zo nee, bestaat het gerelateerde verzoeknummer reeds als zaak in
      Openwave (in tbomgvergunning)?
   -  Zo nee dan wordt een nieuwe rij aangemaakt in tbgerelateerdezaken
      bij de openstaande DSO-zaak.
   -  Zo ja is die zaak een compartimentszaak en is de openstaande
      OpenWave-DSO zaak GEEN compartiment (of vice versa)

      -  Zo nee dan wordt de geretourneerde zaakverwijzing genegeerd.
      -  Zo ja, dan dan wordt een nieuwe rij aangemaakt in
         tbgerelateerdezaken bij de openstaande OpenWave-DSO-zaak.

Om dubbele uitvoering van de callable te vermijden wordt bij het starten
de *Datum* van de instelling *Sectie: Operations Item:
importDSOGerelateerdeZaken* gevuld met timestamp. De kolom *Tekst* met
medewerkerscode en *Getal1* met 1. Indien klaar dan wordt *Getal1* weer
op null gezet. In de operationslog (servicecentrum-portaal) wordt
voortgang en resultaat bijgehouden onder de code:
*importDSOGerelateerdeZaken*. De vraag-en antwoordberichten naar en van
het DSO worden gelogd indien zowel *Sectie: OWB en Item: MessageLog*
aangevinkt is als de instelling *Sectie: DSO-Verzoekafhandelen en Item:
MessageLog*.
