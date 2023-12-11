# Sectie Processen

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de _Sectie: Processen_ gerangschikt op item.
Kijk ook bij secties: _[Termijnbewaking](/docs/instellen_inrichten/configuratie/sectie_termijnbewaking.md) en [Procedures](/docs/instellen_inrichten/configuratie/sectie_procedures.md)_.

## Items Configuratietabel

| Item                             | Kolom        | Omschrijving |
| -------------------------------- | ------------ | ----------------------------------------- |
| AfhandelaarNietGevuld            | Aanvinkvakje | Indien deze instelling aanstaat dan wordt het veld _Afhandelaar_ leeg gemaakt als de afhandeldatum verwijderd wordt bij een processtap. |
| AfvinkstappenGeenEigenScherm     | Aanvinkvakje | Indien aangevinkt dan is de knop linksonder op de processtappenlijst waarmee een aparte lijstscherm voor afvinkstappen opgeroepen kan worden, niet zichtbaar. Een afvinkstap kan namelijk ook worden aan- of uitgevinkt via het detailscherm van een processtap die als eerste kolom in de lijst een gevuld of leeg aanvinkvakje heeft. |
| DagenTerug_StappenLijst          | Getal2       | De hier ingevulde waarde slaat op het aantal dagen terug dat het programma terug gaat in de tijd bij de lijst _mijn openstaande stappen_ op het openingsscherm. Default waarde = 365.                                                                   |
| FataleDatumMax                   | Aanvinkvakje | Indien deze instelling aanstaat dan wordt indien de stap voor ontvangen van aanvullende gegevens LATER dan de aangegeven streefdatum wordt afgehandeld, de fatale datum aangepast met de vooraf opgegeven maximale tijd voor deze stap i.p.v. de daadwerkelijk tijdsperiode. |
| KoppelbaarAanMeerdanEenChecklist | Aanvinkvakje | Indien deze instelling aanstaat dan kan een proces aan meerdere checklijsten worden gekoppeld.   |
| StappenNietInGebruikTonen        | Aanvinkvakje | Indien aangevinkt dan zullen de stappen op de processenlijst bij een zaak die niet in gebruik zijn (vanwege een keuze bij een afvinkstap) toch getoond worden, maar dan disabled en zonder streefdatum en met een lage doorzichtigheidsgraad (opacity). |
|                                  | Getal1       | De waarde slaat op de opacity van de niet in gebruik zijnde processtappen, die toch getoond worden (aanvinkvakje aanzetten). De waarde ligt tussen 0 en 1. Default = 0.5. |
| VolgordeVrij                     | Aanvinkvakje | Indien aangevinkt dan wordt bij het toevoegen van een nieuw proces bij een zaak NIET meer gekeken naar het procesvolgnummer. Indien deze instelling niet bestaat of is uitgevinkt dan kunnen alleen maar processen worden toegevoegd met een hoger procesvolgnummer dan de reeds bestaande proces(sen) bij een zaak, tenzij het een proces betreft dat meerdere keren toegevoegd kan worden bij een zaak. In dit laatste geval wordt bij het tweede of volgende keren toevoegen van zo'n proces ook niet meer naar het volgordenummer gekeken. |
