# Financiële export (Fis export)

Zie binnen dit onderwerp ook [Kolommenoverzicht Fis](/docs/probleemoplossing/programmablokken/financiele_export/kolommen_overzicht) en [Lijst met te exporteren legesregels (vwfrmlegesexport)](/docs/probleemoplossing/programmablokken/financiele_export/lijst_met_te_exporteren_legesregels.md)

## Algemeen

In OpenWave kunnen legesregels verzameld worden in een vooraf gespecificeerd exportbestand. Het exportbestand kan daarna ingelezen worden in het financieel systeem. Het financieel systeem leest de gegevens uit het exportbestand in en is verder verantwoordelijk voor facturering en afhandeling op grond van de ingelezen legesgegevens.

In de desktopversie van Wave bestond voor de financiële export een speciaal programma (WaveExportFis.exe). In het huidige OpenWave is de programmatuur van dit programma nagebouwd en zoals op deze pagina gedefinieerd, vormgegeven. De keuzemogelijkheden voor het verzamelen van de legesregels en hoe het uiteindelijke exportbestand is opgesteld, is conform de desktop programmatuur. Dit houdt in dat het exportbestand een .txt bestand is en de inhoud de format van de journaliseringstabel heeft zoals deze in de desktop programmatuur bekend is.

## Export per gemeente

Het exporteren van de legesgegevens kan voor alle gemeentes samen (default instelling), OF per gemeente gedaan worden. Als de instelling *Sectie: Fis4AllLeges, Item: ExportPerGemeente* aangevinkt is, dan zal het programma de export per gemeente uitvoeren. Is dit het geval dan MOETEN er Fis4AllLeges instellingen bestaan voor de gemeente(s) waarvoor de export gewenst is. Stel dat voor gemeente Fictief met gemeentecode = 0000 de financiële export gedraaid moet worden dan zal het programma kijken naar de instellingen onder *Sectie: Fis4AllLeges_0000*.

**Let op:** de eigenschap **Opnemen in keuzelijst maken legesexportlijst** dient aangevinkt te zijn voor de gewenste gemeente(s). Dit kan men in het beheerportaal-Nieuw via de tegel *OIN* beheren. Bij het opstellen van de legesexportlijst kan er alleen gekozen worden uit gemeentes waarvoor deze eigenschap van toepassing is.

![](applicatiebeheer/probleemoplossing/programmablokken/oin_detail.png){ class="media" loading="lazy" alt="" width="500" }

## Werking

[<img src="/_media/docs/applicatiebeheer/probleemoplossing/programmablokken/portal_tegel.png?w=150&amp;tok=8f4c4d" class="mediaright" loading="lazy" alt="" width="150" />](/_detail/docs/applicatiebeheer/probleemoplossing/programmablokken/portal_tegel.png?id=docs%3Aapplicatiebeheer%3Aprobleemoplossing%3Aprogrammablokken%3Afinanciele_export.md)

In portaal *Operations* is onder de tegel *Fis Export*, alle functionaliteit omtrent de financiële export terug te vinden. Benodigde instellingen voor de financiële export kunnen aangemaakt worden/zijn te beheren via de tegel *Configuratie* in het beheerportaal-Nieuw. Zie [Configuratie instellingen Fis](/docs/instellen_inrichten/configuratie/sectie_fis4allleges.md) voor een overzicht van deze instellingen.
De volgende stappen dienen te worden doorlopen voor het verzamelen van de te exporteren legesgegevens en daarmee tot stand brengen van het uiteindelijke exportbestand:

  * **Samenstellen van de lijst met de te exporteren legesregels op basis van een gekozen conditie** [Lijst met te exporteren legesregels](/docs/probleemoplossing/programmablokken/financiele_export/lijst_met_te_exporteren_legesregels.md)
  * **Downloaden van het kolommenoverzicht** [Kolommenoverzicht Fis](/docs/probleemoplossing/programmablokken/financiele_export/kolommen_overzicht.md)
  * **Genereren van het exportbestand**
  * **Downloaden van het gegenereerde exportbestand**

### Samenstellen van de lijst met de te exporteren legesregels op basis van een gekozen conditie

Allereerst dienen de te exporteren legesgegevens verzameld te worden die uiteindelijk geëxporteerd moeten worden. Het maken van de zo genoemde *Lijst met te exporteren legesregels* gebeurt via een wizard waarbij gevraagd wordt voor welke gemeente de lijst moet worden opgesteld en daarna op welke conditie (alleen indien instelling *Fis4AllLeges: ExportPerGemeente* aangevinkt staat! anders gelijk door naar Opties bij het maken van de legesexportlijst). Uitgebreide uitleg over het aanmaken van de lijst is beschreven op pagina: [Lijst met te exporteren legesregels](/docs/probleemoplossing/programmablokken/financiele_export/lijst_met_te_exporteren_legesregels.md)
![](applicatiebeheer/probleemoplossing/programmablokken/fis_export_lege_lijstmetteexporterenregels.png){ class="media" loading="lazy" alt="" width="1000" }

#### Operationslog Aanmaken lijst legesexportregels

Tijdens het aanmaken van de legesexportlijst (vullen van tabel tblegesexport) wordt in de tabel tboperationslog een kaart aangemaakt met de code *Aanmaken lijst legesexportregels*. De Operationslog is terug te vinden in portaal *Operations*, kolom *Overig*, tegel *Operationslog*.

In de kolom *aantal verwerkt* in deze tabel wordt het aantal legesregels bijgehouden dat door het proces van aanmaken van de lijst is gegaan. De gebruiker zal zelf af en toe de refreshknop linksonder moeten gebruiken om deze voortgang te kunnen zien (het aanmaken van de lijst is een onafhankelijk proces zonder user-interface).

In de kolom voortgang staat *Ben bezig* OF *Klaar* OF *Afgebroken door gebruiker*. Deze laatste mogelijkheid is het geval wanneer de gebruiker tijdens het proces de kolom tboperations.dlstop op T heeft gezet (deze functionaliteit komt nog).

In de kolom LOG (te openen via knop linksonder) worden de aantallen bijgehouden en wordt aangegeven op basis van welke conditie de lijst wordt aangemaakt.

### Downloaden van het kolommenoverzicht

De gebruiker kan een kolommenoverzicht oproepen met daarin de kolommen, lengtes en hun posities zoals deze in het exportbestand zullen verschijnen. Dit overzicht is belangrijk voor de test en voor het inrichten van de importroutine van het financieel systeem. In Open Wave kunnen voor sommige kolommen vaste waardes opgegeven worden die geldig zijn voor alle regels, zoals bedrijfscode, kredietbeheerder et cetera. Indien sprake is van export per gemeente, dan zijn deze instellingen ook per gemeente.

Het is afhankelijk van een aantal instellingen welke kolommen zijn opgenomen in de uiteindelijke exportfile. Lengtes zijn in een aantal gevallen afhankelijk van instellingen en daarmee ook de kolomposities. Voor meer informatie zie [Kolommenoverzicht Fis](/docs/probleemoplossing/programmablokken/financiele_export/kolommen_overzicht.md)

### Genereren (en Downloaden) van Exportbestand

Het genereren van het exportbestand gebeurt via een wizard die aan te roepen is vanaf lijstscherm *Lijst met te exporteren legesregels*. In deze lijst bevindt zich ook de knop naar het lijstscherm waarvandaan het gegenereerde exportbestand te downloaden is. Voor meer informatie zie rest van deze pagina en ook kopjes *Wizard: Exporteer items in deze lijst (exportbestand wordt gemaakt)* en *Lijstknop: Exportbestanden (via deze lijst kan gewenste exportbestand gedownload worden)* op pagina [Lijst met te exporteren legesregels](/docs/probleemoplossing/programmablokken/financiele_export/lijst_met_te_exporteren_legesregels.md).

## Opzet van het exportbestand

Het exportbestand is een .txt bestand dat door de programmatuur regel voor regel gevuld wordt met de te exporteren legesgegevens. Hierbij worden alleen de met een blauwe of witte kleurbol aangegeven regels uit lijst *Lijst met te exporteren legesregels* doorlopen met de voor de gebruiker geldende compartimentsconditie. Elke regel in het exportbestand is opgeknipt in een aantal kolommen. Er is geen scheidingteken tussen de kolommen en elke kolom heeft een vast aantal posities.

Indien in OpenWave aanvragen van meerdere gemeentes staan is het mogelijk om de legesregels per gemeente te exporteren, waarbij de gemeentenaam onderdeel is van het uiteindelijke exportbestand. Er zal dan ook naar de instellingen voor de gekozen gemeente worden gekeken bij het bepalen van de kolommen en hun lengtes en posities in het exportbestand.

### Regels Samenvoegen versus Niet Samenvoegen

Het exportbestand bestaat uit de te exporteren legesregels waarbij OF voor iedere legesregel een aparte regel in het exportbestand bestaat, OF de legesregels behorende bij één vergunningsaanvraag als 1 regel in het exportbestand wordt opgenomen. De laatste optie wordt ook wel samenvoegen genoemd.

Het samenvoegen van regels zou het geval zijn wanneer gekozen wordt om een leges-factuur niet uit te splitsen en wanneer het opgetelde legesbedrag niet over meerdere FCL-nummers hoeft te worden verdeeld. Indien er niet gekozen wordt voor samenvoegen dan kan dezelfde vergunningsaanvraag in meerdere regels terug te vinden zijn in het exportbestand. Er is dan een kolom legessoort zichtbaar waaraan FCL-nummers gekoppeld zijn, zodat onderscheid kan worden gemaakt in bijvoorbeeld teruggave, kortings-, boetes en de normale legessoorten als bouwleges, sloopleges et cetera. Alle legesregels die bij dezelfde vergunningsaanvraag horen krijgen eenzelfde kolom notanummer. De legesregels behorende bij één zaak kunnen wel onderling verschillen in FCL, Taak en BTW code.

Het wel of niet samenvoegen is in te stellen met instelling *Sectie: Fis4AllLeges, Item: LegesSoortInTabel*. Indien aangevinkt dan zal het programma de te exporteren legesregels NIET samenvoegen. Dit betekent dat de waarde voor kolom Legessoort in het exportbestand zal worden gehaald uit de bijbehorende legessoort (dvlegessoortoms). De kolommen Taak, FCL nummer en BTW zullen ook worden opgehaald uit tblegessoort (indien hier de BTW-code niet aanwezig is dan kijkt het programma naar instelling in zelfde sectie *Item: BTWcode*).

Indien *LegesSoortInTabel* NIET is aangevinkt (OF instelling niet aanwezig), dan worden de te exporteren legesregels WEL samengevoegd. De kolom *Legessoort* is in deze situatie niet aanwezig in het exportbestand. De waarde voor FCL nummer en Taak worden gehaald uit kolom *Tekst* bij deze instelling en de waarde voor BTW wordt gehaald uit kolom *Tekst* bij instelling *Item: BTWcode*.

Als er gekozen is om de legesregels met nul bedragen (bedrag is 0, 0.0 of null) NIET op te nemen in het exportbestand, dan zal indien het bedrag voor een samengevoegde regel in totaal 0 is, deze ook niet opgenomen worden in het exportbestand. Wel zullen voor deze regels de exportdatum worden gevuld indien er gekozen wordt voor Definitieve export.

### Test of Definitief?

Bij het maken van het exportbestand wordt de gebruiker gevraagd of het gaat om een *Test* export of *Definitieve* export. Indien er gekozen wordt voor *Test* dan zal de naam van het exportbestand beginnen met *Test_* en de eerste regel van het exportbestand *TESTTESTTEST* zijn. Na het genereren van de export zullen de onderliggende legesregels niet worden voorzien van een exportdatum. De gebruiker kan het genereren van het exportbestand op basis van de lijst met te exporteren legesregels herhalen. Indien er gekozen was voor *Definitief* dan zal voor de geëxporteerde legesregels de exportdatum gevuld worden met datum van vandaag (tenzij instelling *Sectie: Fis4AllLeges, Item: ExportDatumKeuze* aangevinkt staat, dan mag de gebruiker zelf een datum kiezen). De gehele lijst met te exporteren legesregels zal leeggemaakt worden.

## Exporteren legesexportregels

Tijdens het generen van het exportbestand wordt er ook een kaart aangemaakt in de tabel tboperationslog, maar dan met code *Exporteren legesexportregels*. Deze logging is terug te vinden onder de knop *Exportbestanden* in de lijst *Lijst met te exporteren legesregels*.

In de kolom *aantal verwerkt* in deze tabel wordt het aantal legesregels bijgehouden dat door het proces van exportbestand opstellen is gegaan. De gebruiker zal zelf af en toe de refreshknop linksonder moeten gebruiken om deze voortgang te kunnen zien (het exportbestand genereren is een onafhankelijk proces zonder userinterface).

In de kolom voortgang staat *Ben bezig* OF *Bestand* OF *Afgebroken door gebruiker*. Deze laatste mogelijkheid is het geval wanneer de gebruiker tijdens het proces de kolom tboperations.dlstop op T heeft gezet (deze functionaliteit komt nog). Het exportbestand wordt na genereren als een base64 string opgeslagen in tboperationslog en is terug te vinden in blok *Bestand* in het detailscherm van de log. Hier is ook de bestandsnaam terug te vinden.

In het lijstscherm *Logboek Operations* dat te openen is vanuit *Lijst met te exporteren legesregels* bevindt zich een downloadknop (linksonder). Hiermee is het gegenereerde exportbestand te downloaden. **Via deze knop kan men dus daadwerkelijk het exportbestand verkrijgen!**.
