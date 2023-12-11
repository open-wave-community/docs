Zaakportaal Bouw/Sloop
======================

AanroepAction: OpenTabPage(#bouwsloop/x) waarbij x = primary key uit
tbbouwvergunningen.

Schermtype portal.

Problemen
---------

1. Het scherm ziet er raar uit (al of niet met foutmelding) of reageert
   niet:

-  de variabele x uit de aanroep verwijst niet naar een bestaande
   tbbouwvergunningen.dnkey
-  inlogger heeft geen kijkrechten voor Bouw/Sloop zaken (zie rechten:
   de inlogger behoort tot een rechtengroep waarbij *Bouw/Sloop zaken
   Zichtbaar* niet is aangevinkt)
-  de variabele x uit de aanroep verwijst naar een zaak van een gemeente
   waarvoor de inlogger geen kijkrechten rechten (zie instelling
   medewerker: alleen gemeentes en/of medewerker is lid van compartiment
   en de locatie van de zaak valt niet onder de aan het compartiment
   toegekende gemeentes)
-  alle tegels zijn disabled of onzichtbaar op conditie (zie
   `Portaldefinitie </docs/instellen_inrichten/portaldefinitie.md>`__)
-  geen enkele tegel uit dit portal is toegekend aan inlogger.

2. Medewerker a ziet meer of minder tegels dan medewerker b:

kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan
medewerker b.

Triggers
--------

Welke knop/triggers rechtsboven?

Externe link
~~~~~~~~~~~~

Knop is zichtbaar en enabled indien:

-  voor niet-compartimentszaken kolom *Logic* van de instelling *Sectie:
   ExterneLink* en *Item: BouwSloop* aangevinkt is

   -  voor compartimentszaken veld *Externe link naar DMS (portaalknop
      Externe link kijkt naar deze instelling)* bij het desbetreffende
      compartiment in het beheerportaal-Nieuw gevuld is
   -  en het Handhavingszaakrecht *starten van hyperlink vanuit portaal*
      aangevinkt is bij de rechtengroep van de inlogger. Van de kolom
      *Tekst* van bovengenoemde instelling wordt een hyperlink gemaakt,
      waarbij de variabelen in die Tekst:

      -  ``%zaakjaar%`` met het jaar van startdatum van de
         handhavingszaak wordt vervangen: YYYY
      -  ``%zaakjaar%`` met jaar en maand van startdatum wordt
         vervangen: YYYYMM
      -  ``%zaaknr%`` met de OpenWave Zaakcode (dvaanschrijfnr) van de
         bouwsloopzaak
      -  ``%dmsnr%`` met externe zaak/dms nummer (dvintzaakcode) van de
         bouwsloopzaak (indien aangevinkt is dat het DMS E-Suite is dan
         wordt de benodigde vertaalslag op deze tag uitgevoerd)
      -  ``%postcode%`` met postcode van locatie adres
      -  ``%huisnummer%`` met huisnummer van locatie adres.

Docs
~~~~

-  Indien de instelling *Sectie: Documenten Item: Documentregistratie*
   is aangevinkt, dan wordt direct de lijst met `geregistreerde
   documenten </docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten.md>`__
   geopend (op basis van tbcorrespondentie). De knop is in dit geval
   zichtbaar en enabled indien de gebruiker het recht *Inzien
   geregistreerde documenten (tbrechten.dlcbwvcorregvsb)* heeft

   -  anders, (deze instelling staat uit) dan wordt de (live-)lijst van
      opgeslagen documenten bij de zaak geopend: zie `Toon documenten en
      download </docs/probleemoplossing/programmablokken/toon_documenten_en_download.md>`__.
      De knop is in dit geval zichtbaar en enabled indien de gebruiker
      het recht *Inzien documenten buiten registratie om (dlcbwvcorvsb)*
      heeft.

Kaart
~~~~~

Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet
ingevuld zijn van de kolom *Info* van de instelling *Sectie: Programma
Item: ToonKaart* wordt met deze knop een externe kaart geopend (conform
de URL in die kolom info, waarbij %x% en %y% vervangen worden door de
locatiecoördinaten en %zoom% door *Getal2*), of een interne kaart van
OpenWave.
Zie:`Kaart </docs/probleemoplossing/module_overstijgende_schermen/kaart.md>`__.

Memo
~~~~

Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot
melding onvoldoende rechten (rechten *Bouw/Sloop Memo wijzigen*).

Locatie
~~~~~~~

Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot
melding onvoldoende rechten (hoofdscherm rechten: locatie adressen
zichtbaar).

-  *Detailscherm Bouw/Sloop*

Knop is altijd zichtbaar en enabled.

Overige triggers
~~~~~~~~~~~~~~~~

Klikken op tegel opent een vervolgscherm. Indien niet klikbaar dan is de
tegel ingesteld als disabled (zie
`Portaldefinitie </docs/instellen_inrichten/portaldefinitie.md>`__)

Gerelateerde pagina's
---------------------

-  `Detailscherm Bouw/Sloop
   zaak </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/detailscherm_bouw_sloop.md>`__
-  `Tegel Afgehandelde
   Adviezen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgehandelde_adviezen.md>`__
-  `Tegel Afgehandelde
   Processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgehandelde_stappen.md>`__
-  `Tegel Afgesloten
   Inspectiebezoeken </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgesloten_inspectiebezoeken.md>`__
-  `Tegel Afgeronde
   Inspectietrajecten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgesloten_inspectietrajecten.md>`__
-  `Tegel Afgeronde
   Overtredingen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgesloten_issues.md>`__
-  `Tegel Afgeronde zaken op dit
   adres </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgesloten_zaken_op_dit_adres.md>`__
-  `Tegel Alle
   Processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_alle_stappen.md>`__
-  `Tegel
   Contactadressen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_contactadressen.md>`__
-  `Tegel
   Dossierbehandelaars </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_dossierbehandelaars.md>`__
-  `Tegel
   Gebouwen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_gebouwen.md>`__
-  `Tegel Gekoppeld aan
   inrichting </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_gekoppeld_aan_inrichting.md>`__
-  `Tegel Geregistreerde
   Documenten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_geregistreerde_documenten.md>`__
-  `Tegel
   Installaties </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_installaties.md>`__
-  `Tegel
   Leges </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_leges.md>`__
-  `Tegel Lopende
   Inspectietrajecten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_lopende_inspectietrajecten.md>`__
-  `Tegel Lopende zaken op dit
   adres </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_lopende_zaken_op_dit_adres.md>`__
-  `Tegel Openstaande
   Adviezen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_openstaande_adviezen.md>`__
-  `Tegel Openstaande
   Inspectiebezoeken </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_openstaande_inspectiebezoeken.md>`__
-  `Tegel Openstaande
   Overtredingen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_openstaande_issues.md>`__
-  `Tegel Openstaande
   processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_openstaande_stappen.md>`__
-  `Tegel
   Preparaties </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_preparaties.md>`__
-  `Tegel
   Status </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_status.md>`__
-  `Tegel Verbonden aan
   Groep </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_verbonden_aan_groep.md>`__
