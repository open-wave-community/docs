# Veehouderijen

Aan een milieu-inrichting/locatiedossier kunnen één of meer stallen worden gekoppeld. Er is de mogelijkheid de stal- en diergegevens te splitsen. Zodanig dat bij een inrichting meerdere stallen(delen), met bijbehorende stal(deel)gegevens, ingegeven kunnen worden. Binnen iedere stal(deel) bestaat de mogelijkheid (eventueel) meerdere diergroepen met hun emissiewaarden (1-n relatie) te noteren. De combinatie stal en dier bepaalt de Mestvarkens-eenheden en de uitstootgegevens per dier.
De coderingen worden door VROM geleverd. De coderingen en hun betekenis kunnen wijzigen vandaar dat een kolom _Richtlijnduiding_ is opgenomen. De combinatie Code en Richtlijn is uniek.

- Het NH3-cijfer is het aantal Kg per jaar wat één dier, opgeteld per staldeel, produceert.
- Het MVE-cijfer geeft aan hoeveel dieren en in die stal(deel) moeten staan voor 1 MVE.
- De geur in odeurunits wordt per seconde per dier, opgeteld per staldeel, gemeten.
- De fijnstof in grammen per dier per jaar, opgeteld per staldeel.

Er is een tabel die tussen de inrichting en de dier-stalcombinatie zit, TbMilStal. Hier kunnen de stalgegevens ingevuld worden. Per stal kunnen vervolgens een of meerdere staldelen worden aangemaakt. In ieder staldeel kunnen gegevens m.b.t. BWL codering(en), Nageschakelde technieken en PAS codering(en), aantal dieren en reductiepercentages voor stikstof, odeur en fijnstof worden opgegeven.
De berekeningen worden automatisch uitgevoerd.

Zie voor gedetailleerde beschrijving: [Vee / Stallen](/instellen_inrichten/vee_stallen.md).
