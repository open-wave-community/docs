# Sectie Termijnbewaking

Hieronder de instellingen uit de [configuratietabel](README.md) (tbinitialisatie) van de _Sectie: Termijnbewaking_ gerangschikt op item.

Kijk ook bij secties: _Processen en Procedures_.

## Items Configuratietabel

| Item                          | Kolom        | Omschrijving                                                          |
|-------------------------------|--------------|-----------------------------------------------------------------------|
| AfgehandeldStapNietMuteerbaar | Aanvinkvakje | Indien aangevinkt is een processtap niet meer te muteren indien de afgehandeld datum van die stap gevuld is. In het detailscherm van een stap kan een persoon met processtappen verwijderrechten de afgehandeld datum leeg maken. |
| APVOverig_BerOpschAanvProces  | Aanvinkvakje | Indien aangevinkt wordt bij een wijziging in tbtermijnbewstappen die van invloed is op het moment van indiening aanvullende gegevens, de opschortende werking daarvan doorberekend (via de hulpkolom tbovvergunningen.dndagenopschwerking) in de APV/Overige hoofdzaak. |
| Omgeving_BerOpschAanvProces   | Aanvinkvakje | Indien aangevinkt wordt bij een wijziging in tbtermijnbewstappen die van invloed is op het moment van indiening aanvullende gegevens, de opschortende werking daarvan doorberekend (via de hulpkolom tbomgvergunning.dndagenopschwerking) in de omgeving hoofdzaak. |
| Teamzichtbaar                 | Aanvinkvakje | Indien aangevinkt dan is in het lijst- en detailscherm van een processtap zichtbaar aan welk team deze is toegekend (welk team is verantwoordelijk). |
|                               | Getal1       | Indien de waarde 1 (en de instelling is aangevinkt) kan een processtap die toegekend is aan een team, alleen door een lid van dat team worden afgehandeld/gemuteerd. |
| ToelichtingZichtbaar          | Aanvinkvakje | Indien aangevinkt dan is in het lijstscherm van de processtappen bij een zaak een kolom zichtbaar van type schermknop met een vraagtekentje. Het indrukken van deze schermknop laat de toelichting zien uit de corresponderende processtapdefinitie (tbprocitems.dvtoelichting) zien, mits gevonden. |
| Vervallenzichtbaar            | Aanvinkvakje | Indien aangevinkt dan is in het lijst- en detailscherm van een processtap de kolom vervallen (dlvervallen) zichtbaar. Aanvinken van deze kolom heeft tot gevolg dat de afgehandeld datum wordt gevuld met de systeemdatum. |
| Voorwiezichtbaar              | Aanvinkvakje | Indien aangevinkt dan is in het lijst- en detailscherm van een processtap zichtbaar aan welke persoon deze is toegekend (wie is verantwoordelijk). |
| ZaakverantwBovenDossierbeh    | Aanvinkvakje | Indien aangevinkt dan is de verantwoordelijke persoon van een processtap - indien deze niet rechtstreeks is toegekend aan de stap - de zaakverantwoordelijke van de hoofdzaak. Indien niet aangevinkt OF de zaakverantwoordelijke is leeg, dan de actieve dossierbehandelaar. |
