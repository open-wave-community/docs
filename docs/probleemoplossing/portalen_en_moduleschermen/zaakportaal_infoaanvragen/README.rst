Zaakportaal Info-aanvragen
==========================

AanroepAction: OpenTabPage(#infodetail/x) waarbij x = primary key uit
tbinfoaanvragen.

Problemen
---------

Het scherm ziet er raar uit (al of niet met errormelding) of reageert
niet:

-  de variabele x uit de aanroep verwijst niet naar een bestaande
   tbinfoaanvragen.dnkey
-  inlogger heeft geen kijkrechten voor Infozaken (zie rechten: de
   inlogger behoort tot een rechtengroep waarbij *Info-aanvragen
   Zichtbaar* niet is aangevinkt)
-  de variabele x uit de aanroep verwijst naar een zaak van een gemeente
   waarvoor de inlogger geen kijkrechten rechten (zie instelling
   medewerker: alleen gemeentes en/of medewerker is lid van compartiment
   en de locatie van de zaak valt niet onder de aan het compartiment
   toegekende gemeentes)
-  alle tegels zijn disabled of onzichtbaar op conditie (zie
   `Portaldefinitie </docs/instellen_inrichten/portaldefinitie.md>`__)
-  geen enkele tegel uit dit portal is toegekend aan inlogger.

Medewerker a ziet meer of minder tegels dan medewerker b:

Dit kan alleen indien aan medewerkers a andere tegels zijn toegekend dan
aan medewerker b.

Triggers knoppen rechtsboven
----------------------------

Externe link
~~~~~~~~~~~~

-  Knop is zichtbaar en enabled voor niet-compartimentszaken indien
   kolom *Logic* van de instelling *Sectie: ExterneLink* en *Item: Info*
   aangevinkt is. Voor compartimentszaken dient veld *Externe link naar
   DMS (portaalknop Externe link kijkt naar deze instelling)* gevuld te
   zijn bij het desbetreffende compartiment in beheerportaal-Nieuw.
   Daarnaast moet het infozaakrecht *starten van hyperlink vanuit
   portaal* aangevinkt zijn bij de rechtengroep van de inlogger. Van de
   kolom *Tekst* van bovengenoemde instelling wordt een hyperlink
   gemaakt, waarbij de variabelen in die Tekst:

   -  ``%zaakjaar%`` met het jaar van startdatum van de infoaanvraag
      wordt vervangen: YYYY
   -  ``%zaakjaar%`` met jaar en maand van startdatum wordt vervangen:
      YYYYMM
   -  ``%zaaknr%`` met de OpenWave Zaakcode (dvinfonummer) van de
      infoaanvraag
   -  ``%dmsnr%`` met externe zaak/DMS nummer (dvintzaakcode) van de
      infoaanvraag (indien aangevinkt is dat het DMS E-Suite is dan
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
   geregistreerde documenten (tbinforechten.dlcinfocorregvsb)* heeft.
-  Anders, (deze instelling staat uit) dan wordt de (live-)lijst van
   opgeslagen documenten bij de zaak geopend: zie `Toon documenten en
   download </docs/probleemoplossing/programmablokken/toon_documenten_en_download.md>`__.
   De knop is in dit geval zichtbaar en enabled indien de gebruiker het
   recht *Inzien documenten buiten registratie om (dlcinfocorvsb)*
   heeft.

Kaart
~~~~~

-  Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet
   ingevuld zijn van de kolom *Info* van de instelling *Sectie:
   Programma Item: ToonKaart* wordt met deze knop een externe kaart
   geopend (conform de URL in die kolom *Info*, waarbij %x% en %y%
   vervangen worden door de locatie coördinaten en %zoom% door
   *Getal2*), of een interne kaart van OpenWave.
   Zie:`Kaart </docs/probleemoplossing/module_overstijgende_schermen/kaart.md>`__.

Locatie
~~~~~~~

-  Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot
   melding onvoldoende rechten (hoofdscherm rechten: locatieadressen
   zichtbaar).

Memo
~~~~

-  Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot
   melding onvoldoende rechten (rechten infoaanvraag memo zichtbaar).

Detailscherm infoaanvraag
~~~~~~~~~~~~~~~~~~~~~~~~~

-  Knop is altijd zichtbaar en enabled.

Overige triggers
----------------

Klikken op tegel opent een vervolgscherm.

Indien niet klikbaar dan is de tegel ingesteld als disabled (zie
`Portaldefinitie </docs/instellen_inrichten/portaldefinitie.md>`__).

Gerelateerde Pagina's
---------------------

-  `Detailscherm
   Infoaanvraag </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/detailscherm_infoaanvraag.md>`__
-  `Tegel
   Status </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/status.md>`__
-  `Tegel Afgehandelde
   Adviezen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_afgehandelde_adviezen.md>`__
-  `Tegel Afgehandelde
   Processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_afgehandelde_stappen.md>`__
-  `Tegel Afgeronde zaken op dit
   adres </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_afgeronde_zaken_op_dit_adres.md>`__
-  `Tegel Alle
   Processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_alle_stappen.md>`__
-  `Tegel Collegiale
   Toetsen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_collegiale_toetsen.md>`__
-  `Tegel
   Contactadressen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_contactadressen.md>`__
-  `Tegel
   Dossierbehandelaars </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_dossierbehandelaars.md>`__
-  `Tegel Geregistreerde
   Documenten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_geregistreerde_documenten.md>`__
-  `Tegel
   Leges </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_leges.md>`__
-  `Tegel Lopende zaken op dit
   adres </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_lopende_zaken_op_dit_adres.md>`__
-  `Tegel Openstaande
   Adviezen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_openstaande_adviezen.md>`__
-  `Tegel Openstaande
   Processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_openstaande_stappen.md>`__
-  `Tegel Proces
   Checklijsten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_proces_checklijsten.md>`__
-  `Tegel
   Product </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_product.md>`__
-  `Tegel
   Producten/Diensten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_producten_diensten.md>`__
-  `Tegel Verbonden aan
   Groep </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_infoaanvragen/tegel_verbonden_aan_groep.md>`__
