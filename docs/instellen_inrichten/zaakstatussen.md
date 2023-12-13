# Zaakstatussen

Portal Zaakbeheer. Tegel *Zaakstatussen*.

API(s):

  - getStandardList: [https://api.open-wave.nl/RemMethods/getRemMethod/415/](https://api.open-wave.nl/RemMethods/getRemMethod/415/.md)
  - getStandardDetail: [https://api.open-wave.nl/RemMethods/getRemMethod/416](https://api.open-wave.nl/RemMethods/getRemMethod/416.md)

Screenidentifiers: MDLC_getTbZaakStatusList.xml en MDDC_getTbZaakStatusDetail.xml.

Deze tabel wordt gebruikt als mapping voor zaak statussen en - gedeeltelijk - voor resultaatomschrijvingen, indien er sprake is van StUF berichtenuitwisseling met een extern zaaksysteem (zaak/DMS koppeling). Het gaat hierbij om de berichten **creeerZaak** ([Creëer zaak zaak/dms](/probleemoplossing/programmablokken/creeer_zaak_zaak_dms)) en **actualiseerZaakstatus** ([Wijzigen Status externe zaak met Zaak/dms](/probleemoplossing/programmablokken/wijzig_status_zaak_zaak_dms).md). Binnen deze berichten gaat het m.b.t. de status om het blok *<heeft stuf:entiteittype="ZAKSTT">*, en m.b.t. het resultaat om de tag *<omschrijving>* in het blok <resultaat>.

In deze zaakstatussen-tabel kunnen geen kaarten worden verwijderd of aangemaakt. Alleen de kolommen *statusmapping* en *resultaatmapping* kunnen worden gewijzigd door een inlogger die beheerrechten heeft (tbmedewerkers.dnbeheernveau >= 99).

OpenWave onderscheidt 5 statussen van een zaak (het aantal rijen van deze tabel) waarmee naar buiten wordt gecommuniceerd. Dat zijn:

  - StatusInBehandeling (bij aanmaken en heropenen van een zaak/inrichting)
  - StatusAfgesloten (bij afsluiten, afhandelen van een zaak/ inrichting)
  - StatusIngetrokken (bij intrekken van zaak tijdens behandeling). Deze status speelt niet bij inspectiezaken en niet bij handhavingszaken en niet bij inrichtingen
  - StatusVervallen (bij verwijderen van zaak. WORDT NOG NIET ONDERSTEUND)
  - StatusGeblokkeerd (bij blokkeren van hoofdzaak of inrichting). De *StatusGeblokkeerd* hoeft alleen te worden ingevuld, wanneer het ontvangende zaaksysteem ongewenst het uploaden van documenten blokkeert indien de zaak is afgesloten. Door het invullen van een statusmapping bij *StatusGeblokkeerd* zal het programma bij het afsluiten of intrekken van een zaak GEEN einddatum en resultaatomschrijving meesturen. Die einddatum en resultaat worden pas gezet wanneer de zaak in OpenWave geblokkeerd wordt. Indien het ontvangende zaaksysteem wel desgewenst documenten kan ontvangen bij een reeds afgesloten of ingetrokken zaak, dan hoeft de mapping van StatusGeblokkeerd NIET te worden ingevuld: het blokkeren levert dan geen actualiseerstatus-bericht op.

Een typische beeld indien StatusGeblokkeerd **WEL** een aparte mapping heeft:

![](/img/applicatiebeheer/instellen_inrichten/grid_zaakstatsusmetblokkering.png){ class="media" loading="lazy" alt="" width="700" }

Een typische beeld indien StatusGeBlokkeerd **GEEN**  aparte mapping heeft:

![](/img/applicatiebeheer/instellen_inrichten/grid_zaakstatsuszonderblokkering.png){ class="media" loading="lazy" alt="" width="700" }

## StatusInbehandeling

De waarde van de kolommen *mapping statuscodering* en *mapping statusomschrijving* van de rij *StatusInbehandeling* worden doorgegeven:

  - indien het gaat om het aanmaken van een nieuwe zaak (handmatig of automatisch vanuit de OLO)
  - indien het gaat om het toekennen van zaaknummer bij een inrichting
  - indien het om een statuswijziging gaat waarbij een gevulde einddatum (datum afgesloten/afgehandeld of datum ingetrokken) wordt leeggemaakt.

De waarde van de kolom *mapping resultaatomschrijving* blijft hier leeg, want bij *StatusInbehandeling* is in het bericht de resultaattag *omschrijving* leeg (ook de tag *einddatum* is leeg).

## StatusVervallen

Deze status wordt nog niet ondersteund. De waarde van de mappingkolommen kunnen dus leeg blijven.
De status is bedoeld om te gebruiken bij het verwijderen van een kaart in OpenWave.

## StatusIngetrokken

De waarde van de kolommen *mapping statuscodering* en *mapping statusomschrijving* van de rij *StatusIngetrokken* worden doorgegeven:

  - indien een lege intrekkingsdatum bij Omgeving, APV/Overig, Milieu/Gebruik wordt gevuld. Het gaat hier om de datum *intrekking tijdens behandeling*. Bij een inspectiezaak of Handhavingszaak is er geen datum intrekking.

De waarde van de kolom *mapping resultaatomschrijving* moet alleen worden gevuld indien de *StatusGeblokkeerd* geen eigen mapping heeft. Dat zit zo:

  - indien *StatusGeblokkeerd* ook een gevulde *mapping statuscodering* heeft dan:
    - wordt bij het intrekken een lege einddatum in het bericht opgenomen
    - MET een lege resultaatomschrijving
  - anders, (*StatusGeblokkeerd* heeft geen eigen mapping) wordt de zaak met het intrekken ook beëindigd in het externe zaaksysteem door:
    - een gevulde einddatum mee te sturen (de intrekkingsdatum)
    - MET een gevulde resultaatomschrijving (de kolom *mapping resultaatomschrijving*).

## StatusAfgesloten

De waarde van de kolommen *mapping statuscodering* en *mapping statusomschrijving* van de rij *StatusAfgesloten* worden doorgegeven:

  - indien een lege besluit/afhandeldatum bij een hoofdzaak zaak wordt gevuld
  - indien een lege afhandeldatum bij een inspectiezaak wordt gevuld EN de mapping van *StatusGeblokkeerd* is leeg
  - indien een inrichting wordt geblokkeerd EN de mapping van *StatusGeblokkeerd* is leeg.

De waarde van de kolom *mapping resultaatomschrijving* kan hier alleen gevuld worden met het resultaat bij het beëindigen van een inrichting. Dat zit zo:

  - indien StatusGeblokkeerd ook een gevulde *mapping statuscodering* heeft dan:
    - wordt bij het afsluiten/afhandelen  een lege einddatum in het bericht opgenomen
    - MET een lege resultaatomschrijving
  - anders, (StatusGeblokkeerd heeft geen eigen mapping) wordt de zaak met het afsluiten/afhandelen ook beëindigd in het externe zaaksysteem door:
    - een gevulde einddatum mee te sturen (de afhandel/besluitdatum)
    - MET een gevulde resultaatomschrijving. Die resultaatomschrijving komt:
      - indien het gaat om een omgevingszaak of APV/Overige of Milieu/Gebruik zaak van de kolom *Resultaatmapping bij zaak/dms koppeling* (dvdmsaardbesluit) uit de beheertabel *Afhandeling Besluit Omg/APV/Bouw/Milieu/Gebruik* (tbaardbesluit) bij het betreffende aard besluit
      - anders (het gaat om een handhavingszaak) van de kolom *Resultaatmapping bij zaak/dms koppeling* (dvdmsaardbesluit) uit de beheertabel *Afhandeling Handhaving* (tbhandhafronding) bij de betreffende afronding
      - anders (het gaat om een inspectiezaak) uit de kolom *Mapping resultaat bij zaak/dms koppeling* (dvdmsaardbesluit) uit de beheertabel *InspectieResultaten* (tbinspresultaat)
      - anders (het gaat om een inrichting) uit de kolom *mapping resultaatomschrijving* van deze zaakstatussentabel.

## StatusGeblokkeerd

De *StatusGeblokkeerd* hoeft alleen te worden ingevuld, wanneer het ontvangende zaaksysteem ongewenst het uploaden van documenten blokkeert indien de zaak is afgesloten. In dat geval zal bij het invullen van een statusmapping bij *StatusGeblokkeerd* het programma bij het afsluiten of intrekken van een zaak GEEN einddatum en resultaatomschrijving meesturen. Die einddatum en resultaat worden pas gezet wanneer de zaak in OpenWave geblokkeerd wordt.
Indien het ontvangende zaaksysteem wel desgewenst documenten kan ontvangen bij een reeds afgesloten of ingetrokken zaak, dan hoeft de mapping van *StatusGeblokkeerd* NIET te worden ingevuld: het blokkeren levert dan geen actualiseerstatus-bericht op.

De waarde van de kolommen *mapping statuscodering* en *mapping statusomschrijving* van de rij *StatusGeblokkeerd* worden doorgegeven:

  - indien een lege blokkeerdatum bij een zaak of inrichting wordt gevuld
  - indien een inspectiezaak wordt afgesloten EN de mapping van *StatusGeblokkeerd* is gevuld
  - indien een inrichting wordt geblokkeerd EN de mapping van *StatusGeblokkeerd* is gevuld.

De waarde van de kolom *mapping resultaatomschrijving* kan hier gevuld worden met het resultaat bij het beëindigen van een inrichting. Dat zit zo:
Met het blokkeren wordt de zaak ook beëindigd in het externe zaaksysteem door:

  - een gevulde einddatum mee te sturen (de blokkeringsdatum)
  - MET een gevulde resultaatomschrijving. Die resultaatomschrijving komt:
    - indien het gaat om een omgevingszaak of APV/Overige of Milieu/Gebruik zaak van de kolom *Resultaatmapping bij zaak/dms koppeling* (dvdmsaardbesluit) uit de beheertabel *Afhandeling Besluit Omg/APV/Bouw/Milieu/Gebruik* (tbaardbesluit) bij het betreffende aard besluit
    - anders (het gaat om een handhavingszaak) van de kolom *Resultaatmapping bij zaak/dms koppeling* (dvdmsaardbesluit) uit de beheertabel *Afhandeling Handhaving* (tbhandhafronding) bij de betreffende afronding
    - anders (het gaat om een inspectiezaak) uit de kolom *Mapping resultaat bij zaak/dms koppeling* (dvdmsaardbesluit) uit de beheertabel *InspectieResultaten* (tbinspresultaat)
    - anders (het gaat om een inrichting) uit de kolom *mapping resultaatomschrijving* van deze zaakstatussentabel.

