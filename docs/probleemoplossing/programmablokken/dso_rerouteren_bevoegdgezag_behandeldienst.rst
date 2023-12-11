DSO rerouteren bevoegd gezag/behandeldienst
===========================================

Op het detailscherm van de omgevingskaart is tussen de - niet muteerbare
- kolommen **Naam bevoegd gezag** en **Naam uitvoerende instantie** een
schermknop geplaatst, waarmee een wizard wordt aangeroepen die de
mutatie regelt en zo nodig een routeringsbericht naar het DSO stuurt. De
wizard controleert of de gebruiker het recht *wijzigen bevoegd gezag*
heeft (tbomgrechten.dlbomgbevgezedt) en of de zaak niet geblokkeerd is
en of de compartimentscheck OK is.

De gebruiker kan OF een bevoegd gezag wijziging doorvoeren OF een
behandeldienst wijzigen, maar niet alle twee tegelijk. De wizard
redeneert als volgt: Indien:

-  de zaak nog open staat (ddbesluitdatum is leeg)
-  en de kolom OLO/DSO nummer (dvlvoaanvraagnr) gevuld is
-  en de kolom (in blok DSO) dvdsoprojectid gevuld is (dan gaat het
   namelijk om een DSO-aanvraag en niet om een OLO-aanvraag)

Dan moet een wijziging ook doorgegeven worden aan het DSO: dat gebeurt
met een REST API aanroep van de DSO API-groep VerzoekAfhandelen.

In dit geval en indien de medewerker beheerrechten heeft
(tbmedewerkers.dnbeheerniveau > 98) dan zal de wizard vragen aan de
gebruiker wat te doen mocht de verwerking van de wijziging niet goed
gaan in het DSO:

-  wijziging altijd doorvoeren in OpenWave ook als het verzoek naar het
   DSO om te wijzigen NIET succesvol verwerkt is
-  wijziging alleen doorvoeren in OpenWave als het verzoek naar het DSO
   om te wijzigen succesvol verwerkt is.

Indien de DSO API aanroep - om wat voor reden dan ook - niet is
geslaagd, dan krijgt de gebruiker een melding. In de melding staat
beschreven of ondanks mislukken van DSO aanroep, in OpenWave de
wijziging wel is doorgevoerd.

Mogelijke uitkomsten van uitvoeren van de wizard
------------------------------------------------

-  Indien het gaat om een DSO-zaak en de DSO-aanroep is succesvol, dan
   worden

   -  bevoegd gezag of behandeldienst in de omgevingskaart veranderd met
      gekozen OIN-nummer (de behandeldienst mag ook leeg gelaten
      worden!!!).
   -  wordt een kaart aangemaakt in de tabel tbomghistbevgez dan wel in
      tbomghistuitvinst (de tegels *Historie DDSO Bevoegd gezag* en
      *Historie DSO Behandeldienst* op omgevingsportaal)
   -  wordt het DSO-verzoeknummer (dvlvoaanvraagnr) van de zaak voorzien
      van een postfix (indien wijziging bevoegd gezag dan met *\_BG_1*
      of, indien behandeldienst, dan met *\_BD_1*) waarbij het
      getalletje ervoor zorgt dat de kolomwaarde uniek blijft.

-  Indien het gaat om een DSO-zaak maar GEEN succesvolle DSO-aanroep,
   maar de inlogger heeft beheerrechten en heeft daardoor kunnen kiezen
   voor wijziging altijd doorvoeren in OpenWave, dan zal de
   omgevingskaart ook gewijzigd worden. In dit geval echter geen postfix
   op het verzoeknummer en ook geen aanmaak van kaart in tbomghistbevgez
   danwel in tbomghistuitvinst.
-  Indien het gaat om een DSO-zaak maar GEEN succesvolle DSO-aanroep, en
   de inlogger heeft GEEN beheerrechten dan wordt de omgevingskaart NIET
   gewijzigd. In dit geval dus ook geen postfix op het verzoeknummer en
   ook geen aanmaak van kaart in tbomghistbevgez dan wel in
   tbomghistuitvinst.
-  In alle ander gevallen (het gaat NIET om een DSO-zaak) wordt alleen
   het bevoegd gezag of behandeldienst in de omgevingskaart veranderd
   met het gekozen OIN-nummer.

De gebruiker kan in de wizard alleen die NIET vervallen OIN-nummers
kiezen uit de beheertabel tboin waarvoor geldt dat attribuut *In
dropdownlist wijzigen bevoegd gezag* c.q. *In dropdownlist wijzigen
uitvoerende instantie/behandeldienst* aangevinkt is.

.. _instellingen-mbt-verzenden-dso-bericht:

Instellingen m.b.t. verzenden DSO-bericht
-----------------------------------------

-  De kolom *Tekst* van *Sectie: DSO-Verzoekafhandelen en Item:
   AlgemeenEndpoint* moet gevuld zijn met het DSO-endpoint bijvoorbeeld:
   https://pkio.service.pre.omgevingswet.overheid.nl:443/overheid/verzoeken/api/afhandelen/v1
-  indien de zaak NIET speelt in een compartiment dan moet de kolom
   *Tekst* van instelling *Sectie: SWF en Item: OINvanZender* gevuld
   zijn met de OIN-nummer van de zendende organisatie (dus de
   organisatie die het per abuis het STAM-bericht heeft ontvangen)
-  indien de zaak WEL speelt in een compartiment dan wordt deze
   OINvanZender opgehaald in de kolom *tbcompartiment.dvswfoinzender*
   van het betreffende compartiment.

OpenWave doet verder niets na het rerouteringsbericht: het is aan de
behandelaar om te beslissen welke extra handelingen moeten worden
verricht.

StUf UpdateZaakBericht
----------------------

Een stuf updatezaakbericht met het nieuwe bevoegd gezag als extra
element wordt verzonden indien:

-  het bevoegd gezag is gewijzigd
-  en de instelling *Sectie: Koppeling Zaak en Item: UpdateZaakNaam* is
   aangevinkt waarbij de string *instantie* voorkomt in de kolom *Tekst*
   van deze instelling
-  indien de zaak WEL speelt in compartiment dan moet de kolom
   *dldmsupdatezaakbericht* van het betreffende compartiment aangevinkt
   zijn en moet de kolom *dvdmsmethode* de waarde *Stuf Zaken 310*
   hebben
-  indien de zaak NIET speelt in compartiment dan moet *Getal1* van de
   instelling *Sectie: Koppeling Zaak en Item: UpdateZaakNaam* de waarde
   1 hebben en kolom *Tekst* van *Sectie: Koppeling Zaak en Item:
   Methode* moet de waarde *Stuf Zaken 310* hebben.

..

   [!INFO] Kijk voor meer informatie over de DSO op de `DSO
   verzamelpagina </docs/functionaliteiten/dso.md>`__
