Lijst Alle locaties
===================

Dit scherm kan worden aangeroepen vanuit het openingsportaal (zie
tegeldefinitie hieronder). De lijst toont alle locatie-adressen die in
OpenWave bekend zijn. Met behulp van de filter bovenin het scherm kan
het resultaat van de lijst gefilterd worden op Straat en Kadaster.

Werking filters in deze lijst
-----------------------------

Er zijn twee algemene filtermogelijkheden in het scherm *Alle locaties*:

-  filter op **Straat**: deze filter geeft de gebruiker de mogelijkheid
   om alleen alle locaties binnen een gemeente, woonplaats en/of straat
   te zien
-  filter op **Kadaster**: deze filter geeft de gebruiker de
   mogelijkheid alleen locaties binnen een bepaalde kadastrale gemeente,
   sectie en/of perceelnummer te zien.

Definitie
---------

-  Voor de definitie van de lijst en knoppen zie beheertegel *Tabellen
   standaardapi* (tbsysstandardtable.dvcode = opening_allelocaties).
-  De lijst-schermidentifier is: MDLC_getOLVwfrmLokaties.xml (zie
   beheertegel *Schermkolomdefinitie tabellen standaard-api*).
-  De onderliggende view is: vwfrmlokaties.
-  De schermidentifier van de filterblokken is:
   MDFC_getOLVwfrmLokaties.xml (zie beheertegel *Schermkolomdefinitie
   tabellen standaard-api*).

Bijzondere kolommen
~~~~~~~~~~~~~~~~~~~

-  de eerste kolom wordt gevuld met een stop/blokkeericoontje indien het
   adres is vervallen
-  de tweede kolom wordt gevuld met het monumenticoontje indien het
   adres aangeduid is als een monument.

Error
~~~~~

Het scherm geeft een foutmelding, indien:

-  er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie
   `Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
   die niet valide is
-  de inlogger geen kijkrechten heeft op Locatie-adressen.

Triggers
~~~~~~~~

Dubbel klikken op een regel opent het detailscherm van de locatie.
Altijd enabled. Daadwerkelijk wijzigen van de kaart echter alleen
mogelijk indien inlogger het recht heeft op perceeladressen wijzigen.

Triggers linksonder
^^^^^^^^^^^^^^^^^^^

-  Nieuw(e) locatie-adres(sen) (insert-knop):

   -  Zichtbaar indien inlogger rechten heeft voor toevoegen van
      perceeladressen.

-  Nieuw(e) locatie-adres(sen) op deze straat (insert-knop):

   -  Zichtbaar indien inlogger rechten heeft voor toevoegen van
      perceeladressen.

-  Locatieadres verwijderen (deleteknop):

   -  Zichtbaar indien inlogger rechten heeft om perceeladres te laten
      vervallen.

-  Voeg samen met ander locatieadres uit dezelfde straat:

   -  Zichtbaar indien inlogger het recht heeft om perceeladressen samen
      te voegen.
   -  Start de wizard voor samenvoegen van locatieadressen.

Aanmaken van nieuw locatieadres bij insert
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Er kan gekozen worden voor **Nieuw(e) locatie-adres(sen) op deze
straat** of **Nieuw(e) locatie-adres(sen)**. Beide knoppen starten de
wizard *insertLokatieAdres*. Indien gekozen wordt voor locatieadres
aanmaken op deze straat, dan zal het programma het adres overnemen van
de locatie in het lijstscherm waarop men staat bij klikken op knop
*Nieuw(e) locatie-adres(sen) op deze straat*. Indien gekozen voor knop
*Nieuw(e) locatie-adres(sen)* dan zal de gebruiker in de wizard
*insertLokatieAdres* eerst de locatie moeten doorgeven voor het nieuwe
locatieadres. De wizard *insertLokatieAdres* geeft drie opties voor het
toevoegen van een nieuw locatieadres (huidige werking): 1. Zelf een
adres invoeren, 2. Ophalen één adres uit BAG, 3. Haal alle nieuwe
adressen en synchroniseer bestaande met BAG.

Tegeldefinitie
~~~~~~~~~~~~~~

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Openingsportaal*
-  Kolom: *Hoofdzaken*
-  Kopregel: *Alle locaties*
-  Dynamisch tegelopschrift:
-  Actie: \*getFlexList(SysStandardList,nil,nil,G,opening_allelocaties)/
