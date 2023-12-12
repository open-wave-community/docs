# Ontvankelijkheid en opschortende werking

Wanneer tijdens de ontvankelijkheidtoets de aanvrager om aanvullende gegevens wordt gevraagd, zal de periode die ligt tussen deze uitnodiging tot compleet maken en de daadwerkelijke indiening van de aanvullende gegevens opgeteld worden bij de maximale behandelingsduur van de vergunningsaanvraag.

Wanneer de daadwerkelijke indiening echter plaatsvindt na de afgesproken datum dat ze ingediend zouden moeten zijn, dan geldt als opschortende termijn het aantal dagen tussen die afgesproken datum en de uitnodiging. Dit is de opschortende werking.

In het kort komt het hierop neer dat één bepaalde processtap wordt aangewezen als de stap met de betekenis _Indiening van de gevraagde aanvullende gegevens_. Deze stap krijgt zoals alle stappen een streefdatum dat de gegevens ook daadwerkelijk ingediend worden. Het programma weet dan dat de periode die ligt tussen het (minimum van die streefdatum en de afgehandeld datum van deze indieningsstap) versus de afgehandeld datum van de direct daarvoor liggende stap beschouwd moet worden als het aantal op te schorten dagen.

Dit aantal op te schorten dagen wordt sowieso opgeteld bij de fatale datum op het basisscherm van de vergunningsaanvraag mits de instelling _Sectie: Termijnbewaking en Item: Omgeving_BerOpschAanvProces_ (bij omgevingszaken) aangevinkt is. Voor APV/Overige zaken is dit de instelling _Sectie: Termijnbewaking en Item: APVOverig_BerOpschAanvProces_.
De opschortende werking van aanvullende gegevens kan ook via de aparte tabel tbopschorten worden geregeld.
Zie hiervoor: [Opschorten/Verlengen](/docs/probleemoplossing/module_overstijgende_schermen/opschorten_verlengen.md).

Daarnaast kan dit aantal op te schorten dagen ook opgeteld worden bij de streefdatums van de processtappen die na de indiening aanvullende gegevens komen. Hiertoe moet de processtap aangewezen worden waar vanaf de opschortende werking moet worden meegeteld.

In het volgende voorbeeld het proces Ontvankelijkheid in de processtappen, waarbij er vanuit wordt gegaan dat de ontvankelijkheid-toets altijd 14 dagen duurt eventueel verhoogd met de opschortende werking.

![](/img/applicatiebeheer/instellen_inrichten/inrichting_processen/termijnstap_beoordeling.w.600_tok.f56a2b.jpeg){ class="media" loading="lazy" alt="" width="600" }

Bovenstaande stap 20 betekent:

Als er geen aanvullende gegevens nodig zijn dan moet het besluit ontvankelijkheid in stap 50 binnen 10 dagen gebeuren.
Als er wel aanvullende gegevens nodig zijn dan moet de uitnodiging voor het indienen daarvan (stap30) binnen 3 dagen gebeuren.

Verderop zullen we zien dat of er nou wel of geen aanvullende gegevens nodig zijn, de totale duur van deze ontvankelijkheid altijd 2 weken is, eventueel vermeerderd met de opschort-tijd.

De zogenaamde beslisstap - stap 25 - waarmee aangegeven wordt of er aanvullende gegevens nodig zijn: zie [Afvinkstappen](/docs/instellen_inrichten/inrichting_processen/afvinkstappen.md).

![](/img/applicatiebeheer/instellen_inrichten/inrichting_processen/afvinkstap.w.450_tok.27293b.jpeg){ class="media" loading="lazy" alt="" width="450" }

Stap 30 ziet er als volgt uit:

![](/img/applicatiebeheer/instellen_inrichten/inrichting_processen/stap30.w.600_tok.461165.jpeg){ class="media" loading="lazy" alt="" width="600" }

In deze bovenstaande stap 30 Verzoek om aanvulling staat dat de aanvrager 28 dagen de tijd heeft vanaf de daadwerkelijke uitnodigingsbrief om de gegevens aan te leveren in stap 40.

Wanneer de afgehandeld-stap wordt gevuld begint de opschortende werking-teller te lopen en deze eindigt bij het vullen van de afgehandeld datum van stap 40.

![](/img/applicatiebeheer/instellen_inrichten/inrichting_processen/stap_40.w.600_tok.dbe965.jpeg){ class="media" loading="lazy" alt="" width="600" }

Het programma weet dat bovenstaande stap 40 de stap is waar het om gaat bij de indiening van de aanvullende gegevens. Daarom is hier de optie _Deze stap is de ontvangst van de aanvullende gegevens_ aangezet.

Door _Deze stap is de ontvangst van de aanvullende gegevens_ op ja te zetten weet het programma ook - bij afspraak - dat de stap ervoor de uitnodiging daartoe is, en dat het verschil tussen de twee afgehandeld datums de opschortende werking bepaalt.

1. Wanneer de afhandeldatum eerder dan of gelijk is aan de streefdatum wordt het verschil bij de fatale datum bijgeteld.
2. Wanneer de afhandeldatum groter is dan de streefdatum wordt het verschil in dagen ook bij de fatale datum opgeteld.

Kortom:

- er is een initiële fatale datum: standaard 8 weken na indiening
- er wordt gevraagd om aanvullende gegevens en daarvoor is een termijn van 4 weken
- na 3 weken komen de gegevens binnen → dan komt er dus bij de initiële fatale datum 3 weken bij
- komen de stukken bv. na 5 weken binnen (1 week te laat dus) dan zou de fatale datum dus met 5 weken worden verlengd.

Echter er is nu een instelling bijgekomen in de Configuratie die ervoor zorgt dat er alleen 4 weken bij de fatale datum (oftewel de periode die gedefinieerd is in de streefdatum) bijgeteld wordt.
Deze instelling is: _Sectie: Processen, Item: FataleDatumMax_ (moet worden aangevinkt) en moet men zelf aanmaken indien gewenst.

Er staat dat de volgende stap 50, besluit ontvankelijkheid, 5 dagen na indiening van de aanvullende gegevens moet worden genomen.

Met het vinkje _Streefdatum verandert niet mee met invulling afhandeldatums_ wordt aangegeven dat de deadline van het 'besluit volledigheid' wordt berekend op het moment dat het proces voor het eerst wordt opgehaald, en dat deze waarde daarna niet meer aangepast wordt, behalve voor het effectueren van de opschort-periode.

Wanneer de optie _Streefdatum verandert niet mee met invulling afhandeldatums_ niet aangevinkt zou staan, en er is sprake van indiening aanvullende gegevens, dan zou volgens bovenstaande voorbeeld het 'besluit volledigheid' 5 dagen na de indiening van die aanvullende gegevens liggen vermeerderd met de opschort-periode.

Bovenstaand proces is echter zo gemaakt dat de hele ontvankelijkheid altijd een vastgestelde periode duurt, eventueel vermeerderd met de opschortperiode.

Dit komt omdat stap 50 niet afhankelijk is van een ingevulde afgehandeld datum en niet afhankelijk van de datum van indiening aanvullende gegevens, met uitzondering dan van die opschortende werking.

Het voordeel hiervan is dat een vervolgproces als een Reguliere procedure bij omgevingsvergunningen nu ook zo gemaakt kan worden dat deze altijd 6 weken duurt.

De stapeling van ontvankelijkheid en daarop de Reguliere procedure kan dan in de termijnbewaking precies 56 dagen duren en zo volledig in de pas lopen met de ontvangstdatum + fatale periode in het basisscherm.

Dit is natuurlijk een keuze:

- Wil ik altijd dezelfde ruimte hebben om een vergunningsaanvraag af te handelen: regel dan de processen in met de volgende stap gebaseerd op de streefdatum van de vorige stap of door - zoals in bovenstaand voorbeeld - de laatste stap te voorzien van het vinkje _Streefdatum verandert niet mee met invulling afhandeldatums_
- Richt ik de processen zo in, dat waar mogelijk, het behandelproces vóór de wettelijke termijn afgerond kan zijn: regel dan de processen in met de volgende stappen zoveel mogelijk gebaseerd op afgehandeld datums.

> [!IMPORTANT] **Belangrijk**
>
> - Er kan maar één bepaalde processtap wordt aangewezen als de stap met de betekenis _Indiening van de gevraagde aanvullende gegevens_. Als processen worden gestapeld (dus bijvoorbeeld de stappen van de ontvankelijkheidstoets laten volgen door stappen van de uitgebreide inhoudelijke toets) dan geldt ook dat voor alle stappen bij elkaar hooguit eentje de eigenschap _uitzondering ontvankelijkheid_ mag hebben.
> - Er mag in dezelfde opstapeling van processtappen ook maar één stap aangewezen zijn waarbij de optie _Opschortende werkingstermijn wordt bij deze stap opgeteld?_ is aangevinkt.
