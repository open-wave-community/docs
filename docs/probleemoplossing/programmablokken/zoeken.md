# Zoeken

Zoeken kan in Openwave op vier manieren:

* via [Zaken/Inrichtingen/Locaties](/docs/probleemoplossing/module_overstijgende_schermen/zaken_inrichtingen_locaties.md) op zaken, inrichtingen of locaties. Vanuit deze drie tegels zijn alle gegevens in OpenWave te benaderen
* via het [Zoekportaal](/docs/probleemoplossing/portalen_en_moduleschermen/zoekportaal.md). Hierin wordt een aantal zoekwizards aangeboden waarmee op o.a. op zaaknummers, datums, betreft, adres, contact gezocht kan worden
* via zelfgemaakte [Rapportages](/docs/instellen_inrichten/rapportages.md). Met standaard SQL kan de hele database bevraagd worden
* door middel van de zoekbox onderaan de meeste lijstschermen.

### ad 4. Zoekbox onderaan lijstscherm

Standaard kan hierin gezocht worden op het voorkomen van de zoekstring in een van de stringkolommen. Dat zijn de kolommen waarvan de kolomnaam begint met 'dv' van de tabel/view die ten grondslag ligt aan het lijstscherm. Indien het wenselijk is om de zoekopdracht niet op alle stringkolommen van de lijst van toepassing te laten zijn, dan moet bij de betreffende definitie van het lijstscherm worden opgegeven om welke kolommen het dan gaat bij die lijst. Dit gebeurt in de kolom *Zoekkolommen* van de [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md). Die kolommen waarin wel mag worden gezocht moeten worden gedefinieerd gescheiden door een puntkomma (;) bijvoorbeeld *dvaanvraagnaam;dvobjstraat;dvobjplaats*.

Indien het wenselijk is dat ook op een datumkolom kan worden gezocht dan moet deze bij de zoekkolommen van de schermkolomdefinitie worden opgenomen. Een datumkolom begint met 'dd'. Een voorbeeld is dan *ddfataldatum;dvaanvraagnaam;dvobjstraat;dvobjplaats*.
In dat geval kan bijvoorbeeld de zoekopdracht 12-05-2016 worden gehonoreerd.
