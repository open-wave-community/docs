Detailscherm proces
===================

Naam
----

De procesnaam is de naam waaronder het proces zichtbaar is in
keuzemenu’s en in het termijn bewakingsscherm.

Compartiment
------------

Een proces kan gelden voor een specifiek compartiment. Dat betekent dat
alleen bij zaken die spelen in dat compartiment het proces gebruikt kan
worden. Bijgevolg moet dus elk compartiment eigen processen definiëren.
Omgekeerd geldt dus ook dat processen met een leeg compartiment alleen
door de host-organisatie gebruikt kunnen worden.

Volgnummer
----------

Het volgnummer van een proces is van belang. Processen kunnen gestapeld
worden: dus nadat het ene proces is gekozen kan een tweede of een derde
proces worden toegevoegd. Bij het toevoegen of stapelen van processen
zal het programma de termijnstappen invoegen op basis van het volgnummer
van het proces. Er zijn daar twee beperkingen:

-  Er kan geen proces ingevoegd worden met een lager volgnummer dan de
   eerst gekozen proces tenzij de instelling *Sectie: Processen en Item:
   VolgordeVrij* is aangevinkt.
-  Er kan niet twee keer dezelfde proces worden ingevoegd tenzij de
   eigenschap *Meer keer oproepbaar* aangevinkt staat.

Van toepassing op
-----------------

Deze kolom geeft aan onder welke module het proces valt: W =
Omgevingzaken, O = APV/Overig, H = Handhavingen, I = InfoAanvragen, C =
Horeca, E - Milieu/gebruik.

Meer keer oproepbaar
--------------------

Indien deze optie staat aangevinkt heeft dat tot gevolg dat het
betrokken proces meer dan een keer in de termijnbewakingsproces kan
worden opgenomen. Het volgnummer is in dat geval niet meer van belang.
Wanneer een proces voor een tweede of derde keer wordt opgenomen in het
termijnbewakingsproces bij een handhavingszaak of vergunningsaanvraag,
komt deze onderaan.

Stappen chronologisch afwerken
------------------------------

Indien deze optie is aangevinkt (dlmoetstapvoorstap) dan heeft dat tot
gevolg dat de processtappen bij dat proces bij een zaak één voor één
moeten worden afgehandeld. Alleen de stappen met een reeds gevulde
afgehandeld datum en de stap met de eerstvolgende LEGE afgehandeld datum
zijn muteerbaar. De overige stappen zijn wel zichtbaar, maar disabled.
OpenWave gaat er vanuit dat de streefdatums per proces verschillend zijn
(dus de termijnen van stap a naar stap b altijd minimaal een dag).

Bovendien werkt dit alleen goed indien de opeenvolgende stappen ook qua
streefdatum chronologisch oplopend zijn (dus als stap a verwijst naar
stap b als volgende stap en stap b verwijst naar stap c, dan moeten de
streefdatum van c groter zijn dan die van b en die van b moet groter
zijn dan die van a.

Termijnstappen
--------------

Zie
`Termijnstappen </docs/instellen_inrichten/inrichting_processen/termijnstappen.md>`__.

Afvinkstappen
-------------

Zie
`Afvinkstappen </docs/instellen_inrichten/inrichting_processen/afvinkstappen.md>`__.

Gekoppeld aan checklijsten
--------------------------

Hier kan het proces gekoppeld worden aan één of meer checklijsten.
Hierbij kan alleen gekozen worden uit de checklijsten die voor dezelfde
module zijn gemaakt, als waar het proces aan gekoppeld is. De items van
de gekoppelde checklijsten worden automatisch toegevoegd aan een zaak op
het moment dat een nieuw proces aan een zaak wordt toegevoegd.
