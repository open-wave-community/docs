# Teams

Teams worden in het beheerportaal-Nieuw gedefinieerd vanuit de tegel *Medewerkers* of vanuit de tegel *Teams*.
![](applicatiebeheer/instellen_inrichten/teams.png){ class="media" loading="lazy" alt="" width="500" }

Teams kunnen worden toegekend aan hoofdzaken en/of aan processtappen en/of aan adviezen.

## Hoofdzaken en teams

### Team toekennen aan hoofdzaak

Hieronder nemen we als voorbeeld Omgevingszaak.

Indien *Getal1* van *Sectie: Zaakverantwoordelijke en Item: Omgeving* de waarde 2 of 3 heeft kan in de detailkaart van de omgevingszaak bovenaan in het blok *Actoren* een zaakverantwoordelijk team worden toegekend aan de zaak. Bij waarde 2 is alleen dit team zichtbaar, bij waarde 3 zijn zowel team als de zaakverantwoordelijke persoon zichtbaar en bij waarde 1 alleen de zaakverantwoordelijke persoon.

Bij waarde 2 of 3 is het team zichtbaar in de lijst (Mijn) Openstaande omgevingzaken.

Idem dito voor *Sectie: Zaakverantwoordelijke* en *Items Omgeving en Handhaving en Horeca en Infoaanvraag en MilieuGebruik en ApvOverig*.

### Tegel Mijn openstaande (Omgeving)zaken (Openingsportaal)

Hieronder weer het voorbeeld voor Omgevingszaken.

Het klikken op de tegel start een action die gedefinieerd is in het beheerportaal onder de tegel *Portaltiles* (openingsportaal - kolom: *Mijn taken* - tegel: *Mijn openstaande omgevingszaken*). De action is daar gedefinieerd als *geefFlexLijstScherm(openomgzaken,nil,nil,I,W)* of *getFlexList(openomgzaken,nil,nil,I,W)*. De vierde parameter kan de volgende waarden bevatten:

  - **I** = (hoofdletter i) = programma filtert op die openstaande omgevingszaken zaken waarvoor de inlogger gelijk is aan de actieve behandelaar (dossierbehandelaar) dan wel de zaakverantwoordelijke (dvcodeaccountman)
  - **T** = programma filtert op die openstaande omgevingszaken zaken die toegekend zijn aan een **zaakverantwoordelijk team** waar de inlogger lid van is.

Idem dito voor mijn openstaande handhavingszaken *getFlexList(OpenHandhZaken,nil,nil,I,H)* en de overige hoofdmodules.

## Processtappen en teams

### Team toekennen aan processtap

In het beheerportaal-Nieuw onder de tegel *Processen* kan aan een specifieke termijnstap een team worden toegekend.
Aan de voorkant (de processen die gebruikers zien) is de kolom **verantwoordelijk team** zichtbaar indien de instelling *Sectie: Termijnbewaking en Item: TeamZichtbaar* is aangevinkt (er is ook een instelling *Sectie: Termijnbewaking en Item: VoorWieZichtbaar*, beide kunnen aangevinkt staan).

### Tegel Mijn openstaande Processtappen of Mijn Procestaken (Openingsportaal)

Het klikken op de tegel start een action die gedefinieerd is in het beheerportaal-Nieuw onder de tegel *Portaltiles* (openingsportaal - kolom: *Mijn taken* - tegel: *Mijn openstaande processtappen*). De action is daar gedefinieerd als *geefFlexLijstScherm(OPENPROCESSTAPPEN,nil,nil,1)* of *getFlexList(OPENPROCESSTAPPEN,nil,nil,1)*.

De vierde parameter kan de volgende waarden bevatten:

  - 0 = programma filtert op de eerste niet afgehandelde stap per zaak op basis van vwfrmeersteprocesstapperzaak ongeacht wie er inlogt. vwfrmeersteprocesstapperzaak regelt dat indien er twee of meer processen aan zaak zijn gekoppeld, waarvan voor elke proces nog minimaal een stap afgehandeld moet worden, dan dan alleen de stap van het eerste proces getoond wordt.
  - 1 = programma filtert op de niet afgehandelde eerste processtappen (op basis van vwfrmeersteprocesstapperzaak) die aan de inlogger zijn toegekend in de kolom *VoorWie*. Indien deze leeg is, dan gaat het om dossierbehandelaar c.q. zaakverantwoordelijke van de bovenliggende zaak. OpenWave redeneert hierin als volgt. Indien de instelling *Sectie: Termijnbewaking en Item: ZaakverantwBovenDossierbeh* is aangevinkt dan wordt de zaakverantwoordelijke gekozen. Indien deze niet is gevuld, of de stap is niet aangevinkt dan de actieve dossierbehandelaar.
  - 2 = programma filtert op de niet afgehandelde eerste processtappen (op basis van vwfrmeersteprocesstapperzaak) van zaken waarvoor de inlogger gelijk aan de dossierbehandelaar.
  - **3** = programma filtert op de niet afgehandelde eerste processtappen (op basis van vwfrmeersteprocesstapperzaak) die in de **kolom verantwoordelijk team** toegekend zijn aan een team waarvan de inlogger lid is. Indien deze kolom leeg is, dan kijkt het programma naar het zaakverantwoordelijk team van de bovenliggende zaak.
  - 4 = als optie 1, maar nu geldt extra dat de stap NIET aan een team is toegeschreven (dus de stap zelf is niet aan een team toegekend EN er is ook geen zaakverantwoordelijk team bij de bovenliggende zaak).

  - 10 = programma filtert op de niet afgehandelde eerste processtappen (op basis van vwfrmeerstestapperproces) die aan de inlogger zijn toegekend in de kolom *VoorWie*. De vwfrmeerstestapperproces regelt dat indien er twee of meer processen aan zaak zijn gekoppeld, waarvan voor elke proces nog minimaal een stap afgehandeld moet worden, dat dan van beide processen de eerste niet afgehandelde stappen wordt getoond. In de kolom *VoorWie* staat de behandelaar die aan de stap is toegekend, tenzij deze leeg is, dan gaat het om dossierbehandelaar c.q. zaakverantwoordelijke van de bovenliggende zaak). OpenWave redeneert hierin als volgt. Indien de instelling *Sectie: Termijnbewaking en Item: ZaakverantwBovenDossierbeh* is aangevinkt dan wordt de zaakverantwoordelijke gekozen. Indien deze niet is gevuld, of de stap is niet aangevinkt dan de actieve dossierbehandelaar.
  - 20 = programma filtert op de niet afgehandelde eerste processtappen (op basis van vwfrmeerstestapperproces) van zaken waarvoor de inlogger gelijk aan de dossierbehandelaar.
  - **30** = programma filtert op de niet afgehandelde eerste processtappen (op basis van vwfrmeerstestapperproces) die in de **kolom verantwoordelijk team** toegekend zijn aan een team waarvan de inlogger lid is. Indien deze kolom leeg is, dan kijkt het programma naar het zaakverantwoordelijk team van de bovenliggende zaak.
  - 40 = als optie 10, maar nu geldt extra dat de stap NIET aan een team is toegeschreven (dus de stap zelf is niet aan een team toegekend EN er is ook geen zaakverantwoordelijk team bij de bovenliggende zaak).

## Adviezen en teams

### Team toekennen aan adviezen

In het beheerportaal-Nieuw onder de tegel *Adviesinstanties* kan aan een specifieke adviesinstantie een behandelend team worden toegekend.
Aan de voorkant (de adviezen die gebruikers zien) is de kolom **verantwoordelijk team** zichtbaar indien de instelling *Sectie: Adviezen en Item: TeamZichtbaar* is aangevinkt (er is ook een instelling *Sectie: Adviezen en Item: VoorWieZichtbaar* beide kunnen aangevinkt staan).

### Tegel Mijn Uitgezette Adviesaanvragen(Openingsportaal)

Het klikken op de tegel start een action die gedefinieerd is in het beheerportaal-Nieuw onder de tegel *Portaltiles* (openingsportaal - kolom: *Mijn taken* - tegel: *Mijn Uitgezette Adviesaanvragen*). De action is daar gedefinieerd als *getFlexList(OpenAdviezen,nil,nil,1)*.

De vierde parameter kan de volgende waarden bevatten:

  - 1 = indien de waarde 1 dan uitgezette adviesaanvragen op basis van lege adviesdatum (ddadviesdatum uit view vwfrmomgorkestrator_adv) waarvoor de inlogger de interne behandelaar is (de adviesaanvrager).
  - 2 = indien de waarde 2 dan uitgezette adviesaanvragen op basis van lege adviesdatum (ddadviesdatum uit view vwfrmomgorkestrator_adv) waarvoor de inlogger de actieve dossierbehandelaar is van de bovenliggende zaak.
  - **4** = indien de waarde 4 dan uitgezette adviesaanvragen op basis van lege adviesdatum (ddadviesdatum uit view vwfrmomgorkestrator_adv) waarvoor de inlogger behoort tot het **behandelend team**.
  - 11 = indien de waarde 11 dan uitgezette adviesaanvragen op basis van lege dateringsdatum (dddateringadvies uit view vwfrmomgorkestrator_datadv) waarvoor de inlogger de interne behandelaar is (de adviesaanvrager)
  - 12 = indien de waarde 12 dan uitgezette adviesaanvragen op basis van lege dateringsdatum (dddateringadvies uit view vwfrmomgorkestrator_datadv) waarvoor de e inlogger de actieve dossierbehandelaar is van de bovenliggende zaak.
  - **14** = indien de waarde 14 dan uitgezette adviesaanvragen op basis van lege dateringsdatum (dddateringadvies uit view vwfrmomgorkestrator_datadv) waarvoor de inlogger behoort tot het **behandelend team**.

## Collegiale toetsen en teams

### Team toekennen aan collegiale toets

Indien de instelling *Sectie: Documenten en Item: TeamZichtbaar* is aangevinkt is het verplicht om bij een collegiale toets een **behandelend team** toe te kennen. Hierbij is de behandelaar van de collegiale toets een optioneel veld.

Aan de voorkant is de kolom **team** zichtbaar in de collegiale toetsing lijstschermen, bij het aanmaken van een nieuwe collegiale toetsing en op het detailscherm van de toets.

### Tegel Team uit te voeren collegiale toetsen (Openingsportaal)

Het klikken op de tegel start een action die gedefinieerd is in het beheerportaal-Nieuw onder de tegel *Portaltiles* (openingsportaal - kolom: Mijn taken - tegel: Team uit te voeren collegiale toetsen. De action is daar gedefinieerd als getFlexList(SysStandardList,nil,nil,G,opening_tutvct).

Het programma laat de collegiale toetsen zien waarvan de inlogger lid is van het **behandelend team**. Collegiale toetsen die een andere toetser hebben dan de inlogger, maar waarbij de toetser en inlogger tot hetzelfde **behandelende team** behoren worden ook getoond.

