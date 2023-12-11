Lijst met te exporteren legesregels
===================================

Lijst met hierin de te exporteren legesregels (onderliggende view is
vwfrmlegesexport). De lijst wordt gevuld (en eventueel weer geleegd) met
behulp van de lijstknoppen. De lijst is zo opgesteld dat gebruikers
alleen de regels uit vwfrmlegesexport zien die aan de voor hun geldende
compartimentsrechten voldoen. Dit geldt ook voor de acties achter de
knoppen op het lijstscherm: afhankelijk van de ingelogde gebruiker,
hebben de acties effect op alleen de voor die gebruiker beschikbare
legesgegevens. Een gebruiker zal dus niet voor een ander compartiment de
financiële export kunnen uitvoeren/onderliggende gegevens kunnen
aanpassen.

De lijst is zichtbaar indien de inlogger het recht *Mag legesregels
exporteren (FIS export)* aan heeft staan in het detailscherm van de
medewerker.

Definitie
---------

-  Voor de definitie van de lijst en knoppen: zie beheertegel *Tabellen
   Standaardapi* (tbsysstandardtable.dvcode =
   operations_vwfrmlegesexport)
-  De lijst-schermidentifier is: MDLC_getVwfrmLegesExportList.xml (zie
   beheertegel *Schermkolomdefinitie tabellen standaard-api*)
-  De onderliggende view is: vwfrmlegesexport

Bijzondere kolommen
-------------------

-  de eerste kolom is een kleurbol die aangeeft of de legesregel
   meegenomen wordt in het exportbestand. Oranje betekent dat er
   essentiële gegevens ontbreken en de regel niet meegenomen wordt in de
   legesexport. Blauwe en witte regels worden wel meegenomen in het
   exportbestand. Witte regels zijn regels waarvoor valide gegevens zijn
   en de besluitdatum gevuld is. Blauwe regels zijn regels waarvoor
   valide gegevens zijn maar de besluitdatum niet gevuld is.

Error
-----

Het scherm geeft een foutmelding, indien:

-  er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie
   `Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
   die niet valide is
-  de inlogger heeft geen recht om leges te exporteren
   (tbmedewerkers.dlmaglegesexporteren).

|image1|\ { class="media" loading="lazy" alt="" width="1000" }

Triggers
--------

Dubbel klikken op een regel opent het detailscherm van de
legesexportregel. Altijd enabled. Op het detailscherm kan via de
schermknop linksonder het notanummer en/of debiteurennummer gewijzigd
worden. Dit zal resulteren in een gewijzigd notanummer op
legesregelniveau (tblegesregel) en/of een gewijzigd debiteurennummer op
contactadresniveau (tbcontactadressen).

Linksonder bevinden zich de knoppen: voor al deze knoppen geldt dat ze
zichtbaar zijn indien inlogger het nieuwe medewerkersrecht *Mag
legesregels exporteren (FIS export)* aangevinkt heeft staan. Hieronder
volgt een overzicht van aanwezige knoppen in het lijstscherm en hun
onderliggende acties.

Vraagtekenknop: Is er een proces bezig?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

De knop |image2|\ { class="media" loading="lazy" title="vraagteken.jpg"
alt="vraagteken.jpg" width="20" } geeft antwoord op vraag of een andere
medewerker op dat moment al bezig is een legesexportproces uit te
voeren. Bij het samenstellen van de lijst en ook bij het opstellen van
het exportbestand wordt in de configuratietabel *Getal1* van de rij met
*Sectie: Operations en Item: ExportFis* op 1 gezet. Daarmee wordt
voorkomen dat twee processen tegelijk kunnen starten. OpenWave zet deze
waarde automatisch weer op 0 als een proces wordt beëindigd.

Verversknop
~~~~~~~~~~~

Zowel het samenstellen van de lijst als het opstellen van het
exportbestand gebeurt door een zogenaamd runnable programma. Dat
betekent dat de gebruiker nadat het proces is gestart door kan gaan met
andere werkzaamheden. Onder water voert de runnable zijn taken uit. Dat
betekent ook dat de wijzigingen in de lijst niet voortdurend door die
runnable worden uitgeschreven. Met deze knop |image3|\ { class="media"
loading="lazy" alt="" width="20" } kan de lijst ververst worden. De
gebruiker kijkt naar de dan naar de actuele situatie mits de
vraagtekenknop meldt dat er geen proces meer loopt.

Wizard: Genereer nieuwe exportlijst
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met de knop |image4|\ { class="media" loading="lazy" alt="" width="20" }
*Genereer nieuwe exportlijst* wordt een scherm getoond met de volgende
doorkiesmogelijkheden (eventueel eerst voorafgegaan met de vraag: Kies
gemeente):

-  Nieuwe lijst maken: Verzenddatum beschikking gevuld
-  Nieuwe lijst maken: Besluitdatum gevuld
-  Nieuwe lijst maken: Verzenddatum Acceptgiro ligt voor…
-  Nieuwe lijst maken: Geen restrictie
-  Verwijderen van regels uit bestaande lijst (de gehele
   legesexportlijst wordt leeggemaakt)

Alle keuzes slaan op het bewerken en maken van de lijst (dus bewerken
van de tabel tblegesexport) en eventueel ontbrekende notanummers vullen
van de legesregels die doorlopen worden bij het maken van de lijst.
Hiervoor kijkt het programma naar instelling *Sectie: Fis4AllLeges,
Item: NotaNummerisKey* om te bepalen of de lege notanummers met uniek
dnkey van de bovenliggende zaak gevuld worden, of de wavezaakcode van de
bovenliggende zaak.

.. _nieuwe-lijst-maken-de-bestaande-items-in-de-lijst-die-voldoen-aan-compartiment-worden-eerst-verwijderd:

Nieuwe lijst maken:.. De bestaande items in de lijst die voldoen aan compartiment worden eerst verwijderd
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Indien de gebruiker kiest voor 1 van de vier opties *Nieuwe lijst
aanmaken* dan gaat het programma de legesregels (tblegesregels)
doorlopen en toevoegen aan de lijst met te exporteren legesregels
(tblegesexport). Op de te doorlopen legeregels zijn de volgende
condities van toepassing:

-  indien de inlogger niet gelieerd is aan een compartiment, moet de
   dnkeycompartiment bij de bovenliggende zaak van de legesregel ook
   leeg zijn
-  indien de inlogger wel gelieerd is aan een compartiment, moet de
   dnkeycompartiment bij de bovenliggende zaak van de legesregel gelijk
   zijn aan die van de inlogger (tbmedewerkers)
-  exportdatum van de legesregel is **niet gevuld**
-  de legesregel voldoet aan de gekozen conditie in de wizard. De te
   kiezen condities worden als volgt gedefinieerd:

   -  Nieuwe lijst maken: Verzenddatum beschikking gevuld: indien de
      bovenliggende zaak een APV/Overige, bouw/sloopvergunningen of
      omgevingsvergunning is, moet de verzenddatum beschikking gevuld
      zijn. Indien de bovenliggende zaak een horecavergunning of een
      info-aanvraag is, dan geen extra conditie
   -  Nieuwe lijst maken: Besluitdatum gevuld: gevulde besluitdatum
      (indien bovenliggende zaak bouw/sloop, APV/Overige,
      Horecavergunning of Omgevingsvergunning is) of gevulde afgehandeld
      datum indien bovenliggende zaak een info-aanvraag is
   -  Nieuwe lijst maken: Verzenddatum Acceptgiro ligt voor…: gevulde
      verzenddatum acceptgiro (ddlegesverzonden) bij de bovenliggende
      APV/Overige, bouw/sloopvergunning, omgevingsvergunning,
      horeca-vergunning of info-aanvraag en deze datum ligt voor de
      opgegeven waarde in het datumveld bij de wizard.
   -  Nieuwe lijst maken: geen restricties: geen extra condities.

Verwijderen van regels uit bestaande lijst (de gehele legesexportlijst wordt leeggemaakt)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Het programma zal indien deze optie gekozen is alle regels uit de
legesexportlijst(tblegesexport) verwijderen die voldoen aan compartiment
check. Dit betekent dat indien de inlogger lid is van een compartiment,
alleen de regels verwijderd worden met dnkeycompartiment is gelijk aan
dnkeycompartiment van de inlogger. Idem dito als de inloggen geen lid is
van een compartiment dan worden alleen de regels verwijderd uit
tblegesexport waarvoor geldt dnkeycompartiment is leeg.

Verwijderknop
~~~~~~~~~~~~~

Met de knop |image5|\ { class="media" loading="lazy" title="some
colspan" alt="some colspan" width="20" } kan de inlogger de actieve
legesexportregel uit de lijst verwijderen. Dit betekent niet dat de
onderliggende legesregel verwijderd wordt! Alleen de regel in
tblegesexport.

Wizard: Kolommenoverzicht
~~~~~~~~~~~~~~~~~~~~~~~~~

Met de knop |image6|\ { class="media" loading="lazy" alt="" width="20" }
wordt op basis van de configuratie instellingen een kolommenoverzicht
gegenereerd. Dit overzicht is belangrijk voor de test en voor het
inrichten van de importroutine van het financieel systeem. Er dient een
gevulde lijst met te exporteren legesregels te zijn die voldoen aan de
compartimentsrechten om het kolommenoverzicht aan te maken. Zie
`Kolommenoverzicht
Fis </docs/probleemoplossing/programmablokken/financiele_export/kolommen_overzicht.md>`__
voor uitgebreide uitleg.

Wizard: Exporteer items in deze lijst (exportbestand wordt gemaakt)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met de knop |image7|\ { class="media" loading="lazy" alt="" width="20" }
wordt op basis van de lijst met te exporteren legesregels, een
exportbestand opgesteld waarvoor geldt dat:

-  het compartiment overeenkomt met dat van de inlogger
-  de kleurbol van de regel wit of blauw is (er zijn geen ontbrekende
   gegevens die uitsluitend zijn voor financiële export).

Na het genereren van het exportbestand wordt de lijst met te exporteren
legesregels volledig leeggemaakt (dus ook regels met oranje kleurbol die
niet opgenomen worden in het exportbestand) indien er bij de export
gekozen is voor optie *Definitief*. Is er voor optie *Test* gekozen dan
blijft de lijst gevuld en kan het genereren van het exportbestand voor
de lijst herhaald worden.

Lijstknop: Exportbestanden (via deze lijst kan gewenste exportbestand gedownload worden)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Met de knop |image8|\ { class="media" loading="lazy" alt="" width="20" }
wordt een lijstscherm geopend waarin de logging terug te vinden is van
het genereren van de exportbestanden. Iedere keer als een exportbestand
gegenereerd wordt, zal een nieuwe regel in het dit scherm verschijnen.
Het exportbestand zelf ligt opgeslagen in de logging regel en is te
downloaden in het lijstscherm via de downloadknop: download het
exportbestand achter de actieve (geel gearceerde) regel.

Wizard: maakCSVvanRapport - ALLEEN indien met eigen rapport en CSV export gewerkt wordt
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Deze knop zit niet in de standaard uitlevering en dient eerst zelf
aangemaakt te worden (zie verderop hoe deze knop aan te maken)**

Met de knop |image9|\ { class="media" loading="lazy" alt="" width="20" }
wordt een wizard gestart waarbij de gebruiker een rapport aanwijst dat
vervolgens als .CSV aan de gebruiker wordt aangeboden als download.

**Het is ook mogelijk om in de aanroep van de wizard al een rapport id
mee te geven**. Indien dit het geval is, dan kan de gebruiker NIET zelf
een rapport kiezen maar wordt er altijd hetzelfde rapport gestart. Zie
bij kopje *Aanmaken van de knop* hieronder waar het vaste rapport id
opgegeven kan worden.

Er dient vooraf door functioneel beheer een (of meer) rapport
gedefinieerd te worden op basis van vwfrmlegesexport. Zo kan er naast
het regulier doorlopen van de Fis export, een export gegenereerd worden
voor financiële systemen die een .CSV als input verwachten.

**Let dus goed op dat de data in het gekozen rapport overeenkomt met de
Lijst met te exporteren legesregels!** Het vullen van de exportdatum van
de legesregels in OpenWave gebeurt namelijk niet d.m.v. deze nieuwe
wizard maar met de wizard *Exporteer items in deze lijst*.

Op basis van het gekozen rapport wordt dus een exportbestand opgesteld
waarvoor geldt dat:

-  de waarde in de kolommen omhuld worden met het teken opgegeven bij
   nieuwe instelling *Sectie: Programma en Item: RapportCSVKolomOmhuld*
   (**verplichte instelling!**)
-  de kolommen gescheiden worden met het teken opgegeven bij nieuwe
   instelling *Sectie: Programma en Item: RapportCSVKolomScheiding*
   (**verplichte instelling!**)
-  bovenstaande tekens niet hetzelfde mogen zijn
-  de kolommen in het bestand komen uit de opgegeven select in het
   aangewezen rapport
-  eventuele inputparameters opgegeven bij het rapport zijn verwerkt in
   de waardes van de kolommen
-  **header?** de header in het bestand zijn de kolomnamen zoals
   aangegeven in het rapport. Wilt u **geen header** in het bestand? Dan
   kan dit door bij de rapportdefinitie (via tegel
   *Rapportage-definitie*) het veld *Kopregels niet in Excel-export* aan
   te vinken
-  het rapport als .CSV als download wordt aangeboden aan de gebruiker
   (openen van bestand voor controle kan het beste gedaan worden met
   Notepad++).

Aanmaken van de knop
^^^^^^^^^^^^^^^^^^^^

Ga naar de standaardtabeldefinitie *operations_vwfrmlegesexport* via
beheertegel *Tabellen standaardapi*. In het detailscherm van de
definitie vindt u onderaan het knoppenoverzicht. Druk op de plusknop om
een nieuwe knop aan te maken. In het detailscherm van de nieuwe knop kan
de definitie opgegeven worden.

De nieuwe knop dient als volgt gedefinieerd te worden:

-  **hint cq omschrijving** = Rapport aanwijzen voor CSV export

-  **Lijst of detail** = L

-  **Linksonder of op Itemlijst** = L

-  **Icoonnummer** = 22

-  **Volgorde** = (bijvoorbeeld) 80

-  **tbqueries.dvcode action-rechten** = sysstandaard_isbeheerder

-  **Action en Parameters** = startWizard (eerste veld) en veld met
   label *Parameter 1* moet waarde krijgen: maakCSVvanRapport

-  **Optioneel: Parameter 2** = dnkey uit tbrapporten. **Niet
   verplicht!** zie ook hierboven genoemde tekst wanneer deze te vullen

-  De overige, hier niet genoemde velden hoeven niet gevuld te worden.

.. |image1| image:: /img/openwave/applicatiebeheer/probleemoplossing/programmablokken/fis_export_lege_lijstmetteexporterenregels.png
.. |image2| image:: /img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/vraagteken.jpg
.. |image3| image:: /img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/refresh_2.jpg
.. |image4| image:: /img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/start_wizard2.jpg
.. |image5| image:: /img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/delete.jpg
.. |image6| image:: /img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/lesgeven.png
.. |image7| image:: /img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/factuur3.jpg
.. |image8| image:: /img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/lijst2.jpg
.. |image9| image:: /img/openwave/applicatiebeheer/instellen_inrichten/schermdefinitie/start_wizard2.jpg
