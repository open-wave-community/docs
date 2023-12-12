# Kolommenoverzicht CBS exportbestand

Het CBS exportbestand wordt opgesteld volgens de handleiding van CBS (van januari 2023) en zal een ASCII bestand genereren .txt waarin zoveel regels staan als er voor de gekozen gemeente te exporteren CBS-gegevens zijn. Zie voor meer informatie pagina [CBS export](/probleemoplossing/programmablokken/cbs_export/README.md).

Per regel in het exportbestand liggen de kolommen met hun volgorde, lengte en positie vast. Dit kan niet gewijzigd worden.

De data van de CBS-regels wordt waar nodig afgekapt dan wel aangevuld om aan de eisen van de lengte van de kolom te voldoen. Voor nummerieke velden geldt dat indien het veld aangevuld moet worden dit zal gebeuren met voorloopnullen. Voor alfanumerieke velden geldt dat indien het veld aangevuld moet worden dit zal gebeuren met spaties achter de veldwaarde.

Het kolommenoverzicht wordt hieronder weergegeven zodat bij (testen van) CBS exportbestand genereren men kan controleren welke waardes men op welke plek terug kan vinden.

## Kolommen overzichtstabel

In de onderstaande tabel staan de kolommen die voorkomen in het CBS exportbestand in volgorde van links naar rechts. In de tabel is per kolom weergegeven wat de begin en eind posititie is, de totale lengte van de kolom en of het een (N)ummerieke of (A)lfanumerieke waarde bevat. In de omschrijving staat van welk veld uit vwfrmcbsexport de waarde wordt overgenomen en eventuele bijzonderheden.

| Kolomnaam + volgorde                  | Positie van | Positie t/m | Lengte | N of A | Omschrijving                                                                                                                                                         |
| ------------------------------------- | ----------- | ----------- | ------ | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gemeentenummer                        | 1           | 6           | 6      | N      | dvgemeentevolgnr                                                                                                                                                     |
| Uw volgnummer                         | 7           | 26          | 20     | A      | dvzaakreferentiecode                                                                                                                                                 |
| Datum vergunning(JJJJMM)              | 27          | 32          | 6      | N      | dvdatumvergunning (notatie: JJJJMM)                                                                                                                                  |
| Datum start(JJJJMM)                   | 33          | 38          | 6      | N      | dvdatumbegin (notatie: JJJJMM)                                                                                                                                       |
| Bouwtijd in werkbare dagen            | 39          | 42          | 4      | N      | dnbouwtijd                                                                                                                                                           |
| Bouwkosten in 1000 euro               | 43          | 49          | 7      | N      | dnbouwkosten                                                                                                                                                         |
| Inhoud in m3                          | 50          | 56          | 7      | N      | dnbrutoinhoud                                                                                                                                                        |
| Oppervlakte in m2                     | 57          | 63          | 7      | N      | dnbrutovloeropp                                                                                                                                                      |
| Aardwerkzaamheden: Nieuwbouw          | 64          | 64          | 1      | A      | indien dvaardwerkzaamh is 1 dan X, anders een spatie                                                                                                                 |
| Aardwerkzaamheden: Overig             | 65          | 65          | 1      | A      | indien dvaardwerkzaamh is 2 dan X, anders een spatie                                                                                                                 |
| Ligging v/h bouwwerk                  | 66          | 97          | 32     | A      | dvliggingbouwwerk                                                                                                                                                    |
| Woonplaats                            | 98          | 115         | 18     | A      | dvwoonplaats                                                                                                                                                         |
| Postcodegebied                        | 116         | 119         | 4      | N      | dnpostcodegebied                                                                                                                                                     |
| Omschrijving soort bouwwerk           | 120         | 159         | 40     | A      | dvsoortbouwwerkoms                                                                                                                                                   |
| Omschrijving bedrijfstak              | 160         | 199         | 40     | A      | dvbedrijfstakoms                                                                                                                                                     |
| Naam Opdrachtgever                    | 200         | 239         | 40     | A      | dvnaamopdrgever                                                                                                                                                      |
| Opdrachtgever: Overheid + Corporaties | 240         | 240         | 1      | A      | indien dncodeopdrgever is 1 dan X, anders een spatie                                                                                                                 |
| Opdrachtgever: Bouwer v/d markt       | 241         | 241         | 1      | A      | indien dncodeopdrgever is 2 dan X, anders een spatie                                                                                                                 |
| Opdrachtgever: Overig                 | 242         | 242         | 1      | A      | indien dncodeopdrgever is 3 dan X, anders een spatie                                                                                                                 |
| Aantal Woningen huur                  | 243         | 246         | 4      | N      | dnwoningenhuur                                                                                                                                                       |
| Aantal Woningen eigen                 | 247         | 250         | 4      | N      | dnwoningeneigen                                                                                                                                                      |
| Aantal Wooneenheden huur              | 251         | 254         | 4      | N      | dnwooneenhhuur                                                                                                                                                       |
| Aantal Wooneenheden eigen             | 255         | 258         | 4      | N      | dnwooneenheigen                                                                                                                                                      |
| Aantal Recreatiewoningen huur         | 259         | 262         | 4      | N      | dnrecrwoningenhuur                                                                                                                                                   |
| Aantal Recreatiewoningen eigen        | 263         | 266         | 4      | N      | dnrecrwoningeneigen                                                                                                                                                  |
| Vrije tekst voor opmerkingen          | 267         | 508         | 240    | A      | dvvrijetekst: optionele kolom voor het CBS en daarmee de enige kolom die leeg mag zijn. Indien gevuld dan wordt de waarde van de kolom niet aangevuld tot max lengte |

(voor alle overige kolommen is dit wel het geval) |
