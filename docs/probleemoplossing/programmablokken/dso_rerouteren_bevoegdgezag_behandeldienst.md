# DSO rerouteren bevoegd gezag/behandeldienst

Op het detailscherm van de omgevingskaart is tussen de - niet muteerbare - kolommen **Naam bevoegd gezag** en **Naam uitvoerende instantie** een schermknop geplaatst, waarmee een wizard wordt aangeroepen die de mutatie regelt en zo nodig een routeringsbericht naar het DSO stuurt. De wizard controleert of de gebruiker het recht _wijzigen bevoegd gezag_ heeft (tbomgrechten.dlbomgbevgezedt) en of de zaak niet geblokkeerd is en of de compartimentscheck OK is.

De gebruiker kan OF een bevoegd gezag wijziging doorvoeren OF een behandeldienst wijzigen, maar niet alle twee tegelijk.
De wizard redeneert als volgt:
Indien:

- de zaak nog open staat (ddbesluitdatum is leeg)
- en de kolom OLO/DSO nummer (dvlvoaanvraagnr) gevuld is
- en de kolom (in blok DSO) dvdsoprojectid gevuld is (dan gaat het namelijk om een DSO-aanvraag en niet om een OLO-aanvraag)

Dan moet een wijziging ook doorgegeven worden aan het DSO: dat gebeurt met een REST API aanroep van de DSO API-groep VerzoekAfhandelen.

In dit geval en indien de medewerker beheerrechten heeft (tbmedewerkers.dnbeheerniveau > 98) dan zal de wizard vragen aan de gebruiker wat te doen mocht de verwerking van de wijziging niet goed gaan in het DSO:

- wijziging altijd doorvoeren in OpenWave ook als het verzoek naar het DSO om te wijzigen NIET succesvol verwerkt is
- wijziging alleen doorvoeren in OpenWave als het verzoek naar het DSO om te wijzigen succesvol verwerkt is.

Indien de DSO API aanroep - om wat voor reden dan ook - niet is geslaagd, dan krijgt de gebruiker een melding. In de melding staat beschreven of ondanks mislukken van DSO aanroep, in OpenWave de wijziging wel is doorgevoerd.

## Mogelijke uitkomsten van uitvoeren van de wizard

- Indien het gaat om een DSO-zaak en de DSO-aanroep is succesvol, dan worden
  - bevoegd gezag of behandeldienst in de omgevingskaart veranderd met gekozen OIN-nummer (de behandeldienst mag ook leeg gelaten worden!!!).
  - wordt een kaart aangemaakt in de tabel tbomghistbevgez dan wel in tbomghistuitvinst (de tegels _Historie DDSO Bevoegd gezag_ en _Historie DSO Behandeldienst_ op omgevingsportaal)
  - wordt het DSO-verzoeknummer (dvlvoaanvraagnr) van de zaak voorzien van een postfix (indien wijziging bevoegd gezag dan met _\_BG_1_ of, indien behandeldienst, dan met _\_BD_1_) waarbij het getalletje ervoor zorgt dat de kolomwaarde uniek blijft.
- Indien het gaat om een DSO-zaak maar GEEN succesvolle DSO-aanroep, maar de inlogger heeft beheerrechten en heeft daardoor kunnen kiezen voor wijziging altijd doorvoeren in OpenWave, dan zal de omgevingskaart ook gewijzigd worden. In dit geval echter geen postfix op het verzoeknummer en ook geen aanmaak van kaart in tbomghistbevgez danwel in tbomghistuitvinst.
- Indien het gaat om een DSO-zaak maar GEEN succesvolle DSO-aanroep, en de inlogger heeft GEEN beheerrechten dan wordt de omgevingskaart NIET gewijzigd. In dit geval dus ook geen postfix op het verzoeknummer en ook geen aanmaak van kaart in tbomghistbevgez dan wel in tbomghistuitvinst.
- In alle ander gevallen (het gaat NIET om een DSO-zaak) wordt alleen het bevoegd gezag of behandeldienst in de omgevingskaart veranderd met het gekozen OIN-nummer.

De gebruiker kan in de wizard alleen die NIET vervallen OIN-nummers kiezen uit de beheertabel tboin waarvoor geldt dat attribuut _In dropdownlist wijzigen bevoegd gezag_ c.q. _In dropdownlist wijzigen uitvoerende instantie/behandeldienst_ aangevinkt is.

## Instellingen m.b.t. verzenden DSO-bericht

- De kolom _Tekst_ van _Sectie: DSO-Verzoekafhandelen en Item: AlgemeenEndpoint_ moet gevuld zijn met het DSO-endpoint bijvoorbeeld: <https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v1>
- indien de zaak NIET speelt in een compartiment dan moet de kolom _Tekst_ van instelling _Sectie: SWF en Item: OINvanZender_ gevuld zijn met de OIN-nummer van de zendende organisatie (dus de organisatie die het per abuis het STAM-bericht heeft ontvangen)
- indien de zaak WEL speelt in een compartiment dan wordt deze OINvanZender opgehaald in de kolom _tbcompartiment.dvswfoinzender_ van het betreffende compartiment.

OpenWave doet verder niets na het rerouteringsbericht: het is aan de behandelaar om te beslissen welke extra handelingen moeten worden verricht.

## StUf UpdateZaakBericht

Een stuf updatezaakbericht met het nieuwe bevoegd gezag als extra element wordt verzonden indien:

- het bevoegd gezag is gewijzigd
- en de instelling _Sectie: Koppeling Zaak en Item: UpdateZaakNaam_ is aangevinkt waarbij de string _instantie_ voorkomt in de kolom _Tekst_ van deze instelling
- indien de zaak WEL speelt in compartiment dan moet de kolom _dldmsupdatezaakbericht_ van het betreffende compartiment aangevinkt zijn en moet de kolom _dvdmsmethode_ de waarde _Stuf Zaken 310_ hebben
- indien de zaak NIET speelt in compartiment dan moet _Getal1_ van de instelling _Sectie: Koppeling Zaak en Item: UpdateZaakNaam_ de waarde 1 hebben en kolom _Tekst_ van _Sectie: Koppeling Zaak en Item: Methode_ moet de waarde _Stuf Zaken 310_ hebben.

> [!INFO]
> Kijk voor meer informatie over de DSO op de [DSO verzamelpagina](/functionaliteiten/dso.md)
