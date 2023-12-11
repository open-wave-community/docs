Sectie Termijnbewaking
======================

Hieronder de instellingen uit de
`configuratietabel </docs/instellen_inrichten/configuratie.md>`__
(tbinitialisatie) van de *Sectie: Termijnbewaking* gerangschikt op item.

Kijk ook bij secties: *Processen en Procedures*.

Items Configuratietabel
-----------------------

+--------------------------+--------------+--------------------------+
| Item                     | Kolom        | Omschrijving             |
+==========================+==============+==========================+
| Afgeh                    | Aanvinkvakje | Indien aangevinkt is een |
| andeldStapNietMuteerbaar |              | processtap niet meer te  |
|                          |              | muteren indien de        |
|                          |              | afgehandeld datum van    |
|                          |              | die stap gevuld is. In   |
|                          |              | het detailscherm van een |
|                          |              | stap kan een persoon met |
|                          |              | processtappen            |
|                          |              | verwijderrechten de      |
|                          |              | afgehandeld datum leeg   |
|                          |              | maken.                   |
+--------------------------+--------------+--------------------------+
| APVO                     | Aanvinkvakje | Indien aangevinkt wordt  |
| verig_BerOpschAanvProces |              | bij een wijziging in     |
|                          |              | tbtermijnbewstappen die  |
|                          |              | van invloed is op het    |
|                          |              | moment van indiening     |
|                          |              | aanvullende gegevens, de |
|                          |              | opschortende werking     |
|                          |              | daarvan doorberekend     |
|                          |              | (via de hulpkolom        |
|                          |              | tbovvergunnin            |
|                          |              | gen.dndagenopschwerking) |
|                          |              | in de APV/Overige        |
|                          |              | hoofdzaak.               |
+--------------------------+--------------+--------------------------+
| Omg                      | Aanvinkvakje | Indien aangevinkt wordt  |
| eving_BerOpschAanvProces |              | bij een wijziging in     |
|                          |              | tbtermijnbewstappen die  |
|                          |              | van invloed is op het    |
|                          |              | moment van indiening     |
|                          |              | aanvullende gegevens, de |
|                          |              | opschortende werking     |
|                          |              | daarvan doorberekend     |
|                          |              | (via de hulpkolom        |
|                          |              | tbomgvergunn             |
|                          |              | ing.dndagenopschwerking) |
|                          |              | in de omgeving           |
|                          |              | hoofdzaak.               |
+--------------------------+--------------+--------------------------+
| Teamzichtbaar            | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | in het lijst- en         |
|                          |              | detailscherm van een     |
|                          |              | processtap zichtbaar aan |
|                          |              | welk team deze is        |
|                          |              | toegekend (welk team is  |
|                          |              | verantwoordelijk).       |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien de waarde 1 (en   |
|                          |              | de instelling is         |
|                          |              | aangevinkt) kan een      |
|                          |              | processtap die toegekend |
|                          |              | is aan een team, alleen  |
|                          |              | door een lid van dat     |
|                          |              | team worden              |
|                          |              | afgehandeld/gemuteerd.   |
+--------------------------+--------------+--------------------------+
| ToelichtingZichtbaar     | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | in het lijstscherm van   |
|                          |              | de processtappen bij een |
|                          |              | zaak een kolom zichtbaar |
|                          |              | van type schermknop met  |
|                          |              | een vraagtekentje. Het   |
|                          |              | indrukken van deze       |
|                          |              | schermknop laat de       |
|                          |              | toelichting zien uit de  |
|                          |              | corresponderende         |
|                          |              | processtapdefinitie      |
|                          |              | (tb                      |
|                          |              | procitems.dvtoelichting) |
|                          |              | zien, mits gevonden.     |
+--------------------------+--------------+--------------------------+
| Vervallenzichtbaar       | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | in het lijst- en         |
|                          |              | detailscherm van een     |
|                          |              | processtap de kolom      |
|                          |              | vervallen (dlvervallen)  |
|                          |              | zichtbaar. Aanvinken van |
|                          |              | deze kolom heeft tot     |
|                          |              | gevolg dat de            |
|                          |              | afgehandeld datum wordt  |
|                          |              | gevuld met de            |
|                          |              | systeemdatum.            |
+--------------------------+--------------+--------------------------+
| Voorwiezichtbaar         | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | in het lijst- en         |
|                          |              | detailscherm van een     |
|                          |              | processtap zichtbaar aan |
|                          |              | welke persoon deze is    |
|                          |              | toegekend (wie is        |
|                          |              | verantwoordelijk).       |
+--------------------------+--------------+--------------------------+
| Za                       | Aanvinkvakje | Indien aangevinkt dan is |
| akverantwBovenDossierbeh |              | de verantwoordelijke     |
|                          |              | persoon van een          |
|                          |              | processtap - indien deze |
|                          |              | niet rechtstreeks is     |
|                          |              | toegekend aan de stap -  |
|                          |              | de zaakverantwoordelijke |
|                          |              | van de hoofdzaak. Indien |
|                          |              | niet aangevinkt OF de    |
|                          |              | zaakverantwoordelijke is |
|                          |              | leeg, dan de actieve     |
|                          |              | dossierbehandelaar.      |
+--------------------------+--------------+--------------------------+
