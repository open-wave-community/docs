Kolommenoverzicht CBS exportbestand
===================================

Het CBS exportbestand wordt opgesteld volgens de handleiding van CBS
(van januari 2023) en zal een ASCII bestand genereren .txt waarin zoveel
regels staan als er voor de gekozen gemeente te exporteren CBS-gegevens
zijn. Zie voor meer informatie pagina `CBS
export </docs/probleemoplossing/programmablokken/cbs_export.md>`__.

Per regel in het exportbestand liggen de kolommen met hun volgorde,
lengte en positie vast. Dit kan niet gewijzigd worden.

De data van de CBS-regels wordt waar nodig afgekapt dan wel aangevuld om
aan de eisen van de lengte van de kolom te voldoen. Voor nummerieke
velden geldt dat indien het veld aangevuld moet worden dit zal gebeuren
met voorloopnullen. Voor alfanumerieke velden geldt dat indien het veld
aangevuld moet worden dit zal gebeuren met spaties achter de veldwaarde.

Het kolommenoverzicht wordt hieronder weergegeven zodat bij (testen van)
CBS exportbestand genereren men kan controleren welke waardes men op
welke plek terug kan vinden.

Kolommen overzichtstabel
------------------------

In de onderstaande tabel staan de kolommen die voorkomen in het CBS
exportbestand in volgorde van links naar rechts. In de tabel is per
kolom weergegeven wat de begin en eind posititie is, de totale lengte
van de kolom en of het een (N)ummerieke of (A)lfanumerieke waarde bevat.
In de omschrijving staat van welk veld uit vwfrmcbsexport de waarde
wordt overgenomen en eventuele bijzonderheden.

+-----------+-----------+-----------+--------+--------+-----------+
| Kolomnaam | Positie   | Positie   | Lengte | N of A | Oms       |
| +         | van       | t/m       |        |        | chrijving |
| volgorde  |           |           |        |        |           |
+===========+===========+===========+========+========+===========+
| Gemee     | 1         | 6         | 6      | N      | dvgemee   |
| ntenummer |           |           |        |        | ntevolgnr |
+-----------+-----------+-----------+--------+--------+-----------+
| Uw        | 7         | 26        | 20     | A      | dv        |
| v         |           |           |        |        | zaakrefer |
| olgnummer |           |           |        |        | entiecode |
+-----------+-----------+-----------+--------+--------+-----------+
| Datum     | 27        | 32        | 6      | N      | dvdatumv  |
| vergunnin |           |           |        |        | ergunning |
| g(JJJJMM) |           |           |        |        | (notatie: |
|           |           |           |        |        | JJJJMM)   |
+-----------+-----------+-----------+--------+--------+-----------+
| Datum     | 33        | 38        | 6      | N      | dvd       |
| star      |           |           |        |        | atumbegin |
| t(JJJJMM) |           |           |        |        | (notatie: |
|           |           |           |        |        | JJJJMM)   |
+-----------+-----------+-----------+--------+--------+-----------+
| Bouwtijd  | 39        | 42        | 4      | N      | d         |
| in        |           |           |        |        | nbouwtijd |
| werkbare  |           |           |        |        |           |
| dagen     |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| B         | 43        | 49        | 7      | N      | dnb       |
| ouwkosten |           |           |        |        | ouwkosten |
| in 1000   |           |           |        |        |           |
| euro      |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Inhoud in | 50        | 56        | 7      | N      | dnbr      |
| m3        |           |           |        |        | utoinhoud |
+-----------+-----------+-----------+--------+--------+-----------+
| Op        | 57        | 63        | 7      | N      | dnbrut    |
| pervlakte |           |           |        |        | ovloeropp |
| in m2     |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Aardwerkz | 64        | 64        | 1      | A      | indien    |
| aamheden: |           |           |        |        | dvaard    |
| Nieuwbouw |           |           |        |        | werkzaamh |
|           |           |           |        |        | is 1 dan  |
|           |           |           |        |        | X, anders |
|           |           |           |        |        | een       |
|           |           |           |        |        | spatie    |
+-----------+-----------+-----------+--------+--------+-----------+
| Aardwerkz | 65        | 65        | 1      | A      | indien    |
| aamheden: |           |           |        |        | dvaard    |
| Overig    |           |           |        |        | werkzaamh |
|           |           |           |        |        | is 2 dan  |
|           |           |           |        |        | X, anders |
|           |           |           |        |        | een       |
|           |           |           |        |        | spatie    |
+-----------+-----------+-----------+--------+--------+-----------+
| Ligging   | 66        | 97        | 32     | A      | dvliggin  |
| v/h       |           |           |        |        | gbouwwerk |
| bouwwerk  |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| W         | 98        | 115       | 18     | A      | dvw       |
| oonplaats |           |           |        |        | oonplaats |
+-----------+-----------+-----------+--------+--------+-----------+
| Postc     | 116       | 119       | 4      | N      | dnpostc   |
| odegebied |           |           |        |        | odegebied |
+-----------+-----------+-----------+--------+--------+-----------+
| Oms       | 120       | 159       | 40     | A      | dvsoortbo |
| chrijving |           |           |        |        | uwwerkoms |
| soort     |           |           |        |        |           |
| bouwwerk  |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Oms       | 160       | 199       | 40     | A      | dvbedri   |
| chrijving |           |           |        |        | jfstakoms |
| be        |           |           |        |        |           |
| drijfstak |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Naam      | 200       | 239       | 40     | A      | dvnaam    |
| Opdr      |           |           |        |        | opdrgever |
| achtgever |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Opdra     | 240       | 240       | 1      | A      | indien    |
| chtgever: |           |           |        |        | dncode    |
| Overheid  |           |           |        |        | opdrgever |
| +         |           |           |        |        | is 1 dan  |
| Co        |           |           |        |        | X, anders |
| rporaties |           |           |        |        | een       |
|           |           |           |        |        | spatie    |
+-----------+-----------+-----------+--------+--------+-----------+
| Opdra     | 241       | 241       | 1      | A      | indien    |
| chtgever: |           |           |        |        | dncode    |
| Bouwer    |           |           |        |        | opdrgever |
| v/d markt |           |           |        |        | is 2 dan  |
|           |           |           |        |        | X, anders |
|           |           |           |        |        | een       |
|           |           |           |        |        | spatie    |
+-----------+-----------+-----------+--------+--------+-----------+
| Opdra     | 242       | 242       | 1      | A      | indien    |
| chtgever: |           |           |        |        | dncode    |
| Overig    |           |           |        |        | opdrgever |
|           |           |           |        |        | is 3 dan  |
|           |           |           |        |        | X, anders |
|           |           |           |        |        | een       |
|           |           |           |        |        | spatie    |
+-----------+-----------+-----------+--------+--------+-----------+
| Aantal    | 243       | 246       | 4      | N      | dnwon     |
| Woningen  |           |           |        |        | ingenhuur |
| huur      |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Aantal    | 247       | 250       | 4      | N      | dnwoni    |
| Woningen  |           |           |        |        | ngeneigen |
| eigen     |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Aantal    | 251       | 254       | 4      | N      | dnwoo     |
| Woo       |           |           |        |        | neenhhuur |
| neenheden |           |           |        |        |           |
| huur      |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Aantal    | 255       | 258       | 4      | N      | dnwoon    |
| Woo       |           |           |        |        | eenheigen |
| neenheden |           |           |        |        |           |
| eigen     |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Aantal    | 259       | 262       | 4      | N      | dnrecrwon |
| Recreati  |           |           |        |        | ingenhuur |
| ewoningen |           |           |        |        |           |
| huur      |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Aantal    | 263       | 266       | 4      | N      | d         |
| Recreati  |           |           |        |        | nrecrwoni |
| ewoningen |           |           |        |        | ngeneigen |
| eigen     |           |           |        |        |           |
+-----------+-----------+-----------+--------+--------+-----------+
| Vrije     | 267       | 508       | 240    | A      | dvvr      |
| tekst     |           |           |        |        | ijetekst: |
| voor      |           |           |        |        | optionele |
| op        |           |           |        |        | kolom     |
| merkingen |           |           |        |        | voor het  |
|           |           |           |        |        | CBS en    |
|           |           |           |        |        | daarmee   |
|           |           |           |        |        | de enige  |
|           |           |           |        |        | kolom die |
|           |           |           |        |        | leeg mag  |
|           |           |           |        |        | zijn.     |
|           |           |           |        |        | Indien    |
|           |           |           |        |        | gevuld    |
|           |           |           |        |        | dan wordt |
|           |           |           |        |        | de waarde |
|           |           |           |        |        | van de    |
|           |           |           |        |        | kolom     |
|           |           |           |        |        | niet      |
|           |           |           |        |        | aangevuld |
|           |           |           |        |        | tot max   |
|           |           |           |        |        | lengte    |
+-----------+-----------+-----------+--------+--------+-----------+

(voor alle overige kolommen is dit wel het geval) \|
