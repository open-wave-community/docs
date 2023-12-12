# Duurzaamheid

![](/img/applicatiebeheer/probleemoplossing/programmablokken/kolommen.png){ class="media" loading="lazy" alt="" width="200" }

Aan een milieu-inrichting kunnen gegevens omtrent duurzaamheid worden geregistreerd. Naast het registreren van energie gegevens, is er ook de mogelijkheid aan te geven aan welke projecten de inrichting deelneemt, welke vervoerders van toepassing zijn en is de afvalregistratie vernieuwd.

## Energie

Het registreren van energiegegevens is uitgebreid met de volgende attributen: exact verbruik, of het om een grootverbruiker gaat en het formaat van de aansluiting. In het geval dat er een koppeling met Erkende maatregelen is, zal de energie registratie aangemaakt worden met de gegevens van de binnengekomen XML. Dit was al zo maar vanaf deze versie wordt ook het exact energie verbruik overgenomen uit het bericht.

![](/img/applicatiebeheer/probleemoplossing/programmablokken/detailscherm_energie.png){ class="media" loading="lazy" alt="" width="400" }

## Vervoer

In het beheerportaal _Inrichtingenbeheer_ kunnen vervoerders aangemaakt worden onder de tegel _Vervoerders_. Basisgegevens als het KVK-/Vestigingsnummer, bedrijfsnaam, mailadres e.d. zijn per vervoerder op te geven (en eventueel gegevens benodigd voor afvalstofvervoerders). Toegevoegd aan het detailscherm van de vervoerder is de knop om NHR controle uit te voeren. Dit werkt hier iets anders dan de NHR controle op een contact bij een zaak/inrichting. Voor de vervoerder wordt naar de woonplaats gekeken om te bepalen bij welke gemeente (tb33gemeente) de de stuurgegevens worden opgehaald. Indien de woonplaats NIET, OF meer dan 1 keer voorkomt bij de gemeentes van tabel tb33gemeente, dan zal de NHR controle niet kunnen plaatsvinden omdat er niet bepaald kan worden waar de stuurgegevens moeten worden opgehaald. Bij de inrichting kan onder de tegel _Vervoer_ aangegeven worden welk van de vervoerders bij deze inrichting van toepassing zijn. Voor de vervoerder bij de inrichting is het aantal transportkilometers op te geven. Bij de nieuwe manier van afvalstofregistraties bij een inrichting kan per afvalstofregistratie gekozen worden wie de vervoerders zijn zie hieronder bij het kopje _Afvalstoffen_.

## Projecten

Het deelnemen aan projecten van een inrichting kan geregistreerd worden onder kolom _Duurzaamheid_. Hierbij wordt een onderscheidt gemaakt tussen energie-/-vervoer en duurzaamheidsprojecten. In het beheerportaal _Inrichtingenbeheer_ kunnen projecten beheerd/aangemaakt worden onder de tegel _Projecten duurzaamheid_. Hierbij wordt er per project een keuze gemaakt of het een vervoer-, duurzaamheids- dan wel energieproject betreft.

Onder de tegels _Projecten energie_, _Projecten vervoer_ en _Projecten duurzaamheid_ bij de inrichting kan deelname aan projecten geregistreerd worden waarbij onder de tegel _Projecten energie_ alleen uit de projecten met indicatie _Energie_ uit de codetabel in het beheer gekozen kan worden. Bij de tegel _Projecten vervoer_ kan alleen uit de projecten met indicatie _Vervoer_ gekozen worden uit de codetabel in het beheer etc. Start- en einddatum van deelname kan opgegeven worden. Tevens is in te zien wat de start- en einddatum van het gehele project is.

## Afvalstoffen

![](1.29/applicatiebeheer/probleemoplossing/programmablokken/afvalstofdetail1.21.png){ class="mediaright" loading="lazy" alt="" width="400" }

In versies ouder dan 1.20 vond het registreren van afvalstoffen bij een inrichting plaats onder de kolom _Bodem_.
Dit resulteerde in een registratie in tabel tbmildiversen met als rubriek _afvalstoffen_. Deze manier van registreren blijft nog mogelijk en oude registraties zijn nog in te zien onder de tegel _Afvalstoffen_ onder kolom _Bodem_. Er kan gekozen worden om op de nieuwe manier afvalstoffen te registreren onder kolom _Duurzaamheid_ en na verloop van tijd de tegel _Afvalstoffen_ onder kolom _Bodem_ uit te zetten/inactief te maken.

Onder de tegel _Afvalstoffen_ in kolom _Duurzaamheid_ hangt een tabel specifiek voor registreren van afvalstoffen (tbmilafvalstoffen). Hier kunnen afvalstoffen geregistreerd worden waarbij er gekozen kan worden uit afvalstoffen zoals gedefinieerd in de codetabel tbmilsrtafvalstof. Deze tabel dient zelf gevuld te worden in het beheerportaal _Inrichtingenbeheer_ onder de tegel _Soort afvalstof_.
In versie 1.20 was het mogelijk om de coördinaten van de afvalstofregistratie op te geven en deze te tonen op de kaart. Deze functionaliteit is komen te vervallen en het blok _Coördinaten_ in het detailscherm van de afvalstofregistratie is onzichtbaar gemaakt. Bij registreren van afvalstoffen kunnen onder andere de volgende gegevens opgegeven worden: de Landelijke Meld Plicht (LMA), de frequentie van de afvalstofregistratie en of het een nuttige toepassing betreft. Indien het veld **Nuttige toepassing?** wordt aangevinkt zal een blok verschijnen voor het vullen van de overige gegevens omtrent nuttige toepassing. Na het vullen van de datum dat de nuttige toepassing geconstateerd is, zal zowel het vinkje _Nuttige Toepassing?_ als de constateerdatum, NIET meer te wijzigen zijn.

### Afvalstoffen - Vervoerder

Eerder werd de vervoerder gekozen uit de gekoppelde vervoerders bij de inrichting (tbmilinvervoer) van de afvalstofregistratie. Deze verwijzing naar de vervoerder is komen te vervallen: er kan nu meer dan 1 vervoerder gekozen worden mits bij deze vervoerder in de beheertabel is aangegeven dat het om een afvalstofvervoerder gaat.
Er wordt dus ook niet meer gekozen uit de gekoppelde vervoerders bij de inrichting, maar uit de opgegeven vervoerders in beheer (tegel _Vervoerders_) met indicatie afvalstof. Daarnaast is het mogelijk om de rol van de vervoerder toe te kennen. Er zijn vier mogelijke rollen: _Vervoerder (V)_, _Inzamelaar (I)_, _Handelaar (H)_ en _Bemiddelaar (B)_.
Er kan alleen gekozen worden uit de rollen zoals opgegeven bij de vervoerder in de beheertabel. Een vervoerder kan meerdere malen worden opgevoerd bij de afvalstofregistratie, maar niet meerdere malen met dezelfde rol (combinatie moet uniek zijn).

![](/img/applicatiebeheer/probleemoplossing/programmablokken/beheer_vervoerders_1.21.png){ class="media" loading="lazy" alt="" width="500" }
