Zaakportaal Milieu/gebruik
==========================

AanroepAction: OpenTabPage(#milieugebruikdetail/x) waarbij x = primary
key uit tbmilvergunningen. Schermtype portal.

Problemen
---------

1. Het scherm ziet er raar uit (al of niet met errormelding) of reageert
   niet:

-  de variabele x uit de aanroep verwijst niet naar een bestaande
   tbmilvergunningen.dnkey
-  inlogger heeft geen kijkrechten voor Milieu/gebruikzaken (zie
   rechten: de inlogger behoort tot een rechtengroep waarbij
   *Milieu/gebruik Zichtbaar* niet is aangevinkt)
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

-  voor niet-compartimentszaken kolom Logic van de instelling *Sectie:
   ExterneLink* en *Item: MilieuGebruik* aangevinkt is

   -  voor compartimentszaken dient veld *Externe link naar DMS
      (portaalknop Externe link kijkt naar deze instelling)* gevuld te
      zijn bij het desbetreffende compartiment in beheerportaal-Nieuw
   -  en het Milieugebruikzaakrecht *starten van hyperlink vanuit
      portaal* aangevinkt is bij de rechtengroep van de inlogger. Van de
      kolom *Tekst* van bovengenoemde instelling wordt een hyperlink
      gemaakt, waarbij de variabelen in die Tekst:

      -  ``%zaakjaar%`` met het jaar van ontvangstdatum van de
         Milieu/Gebruik zaak wordt vervangen: YYYY
      -  ``%zaakjaar%`` met jaar en maand van ontvangstdatum wordt
         vervangen: YYYYMM
      -  ``%zaaknr%`` met de OpenWave Zaakcode (dvvergnummer) van de
         Milieu/Gebruik zaak
      -  ``%dmsnr%`` met externe zaak/DMS nummer (dvintzaakcode) van de
         Milieu/Gebruik zaak (indien aangevinkt is dat het DMS E-Suite
         is dan wordt de benodigde vertaalslag op deze tag uitgevoerd)
      -  ``%postcode%`` met postcode van locatie adres
      -  ``%huisnummer%`` met huisnummer van locatie adres.

Docs
~~~~

-  Indien de instelling *Sectie: Documenten Item: Documentregistratie*
   is aangevinkt, dan wordt direct de lijst met `geregistreerde
   documenten </docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten.md>`__
   geopend (op basis van tbcorrespondentie). De knop is in dit geval
   zichtbaar en enabled indien de gebruiker het recht *Inzien
   geregistreerde documenten (tbmilvergrechten.dlcmilvergcorregvsb)*
   heeft.

   -  Anders, (deze instelling staat uit) dan wordt de (live-)lijst van
      opgeslagen documenten bij de zaak geopend: zie `Toon documenten en
      download </docs/probleemoplossing/programmablokken/toon_documenten_en_download.md>`__.
      De knop is in dit geval zichtbaar en enabled indien de gebruiker
      het recht *Inzien documenten buiten registratie om
      (dlcmilvergcorvsb)* heeft.

Kaart
~~~~~

-  Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet
   ingevuld zijn van de kolom *Info* van de instelling *Sectie:
   Programma Item: ToonKaart* wordt met deze knop een externe kaart
   geopend (conform de URL in die kolom *Info*, waarbij %x% en %y%
   vervangen worden door de locatiecoordinaten en %zoom% door *Getal2*),
   of een interne kaart van OpenWave.
   Zie:`Kaart </docs/probleemoplossing/module_overstijgende_schermen/kaart.md>`__.

Memo
~~~~

-  Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot
   melding onvoldoende rechten (rechten MilieuGebruik *Memo wijzigen*).
-  *Locatie*

Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot
melding onvoldoende rechten (hoofdscherm rechten: *locatieadressen
zichtbaar*).

-  *Detailscherm MilieuGebruik*

Knop is altijd zichtbaar en enabled.

Overige trigger
~~~~~~~~~~~~~~~

Klikken op tegel opent een vervolgscherm.

Indien niet klikbaar dan is de tegel ingesteld als disabled (zie
`Portaldefinitie </docs/instellen_inrichten/portaldefinitie.md>`__).

Gerelateerde Pagina's
---------------------

-  `Detailscherm
   Milieu/Gebruikszaak </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/detailscherm_milieu_gebruikszaken.md>`__
-  `Tegel Afgehandelde
   Adviezen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_afgehandelde_adviezen.md>`__
-  `Tegel Afgehandelde
   Processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_afgehandelde_processtappen.md>`__
-  `Tegel Afgerond
   Bezwaar/Beroep </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_afgerond_bezwaar_beroep.md>`__
-  `Tegel Afgeronde zaken op dit
   adres </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_afgesloten_zaken_op_dit_adres.md>`__
-  `Tegel Alle
   processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_alle_processtappen.md>`__
-  `Tegel Collegiale
   Toetsen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_collegiale_toetsen.md>`__
-  `Tegel
   Contactadressen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_contactadressen.md>`__
-  `Tegel
   Dossierbehandelaars </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_dossierbehandelaars.md>`__
-  `Tegel
   Gebouwen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_gebouwen.md>`__
-  `Tegel Gekoppeld aan
   inrichting </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_gekoppeld_aan_inrichting.md>`__
-  `Tegel Gekoppeld aan
   inrichting </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik.md>`__
-  `Tegel Geregistreerde
   Documenten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_geregistreerde_documenten.md>`__
-  `Tegel
   Installaties </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_installaties.md>`__
-  `Tegel Lopend
   Bezwaar/Beroep </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_lopend_bezwaar_beroep.md>`__
-  `Tegel Lopende zaken op dit
   adres </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_lopende_zaken_op_dit_adres.md>`__
-  `Tegel
   OLO/AIM-berichten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_olo-aim-berichten.md>`__
-  `Tegel Openstaande
   Adviezen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_openstaande_adviezen.md>`__
-  `Tegel Openstaande
   processtappen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_openstaande_processtappen.md>`__
-  `Tegel
   Preparaties </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_preparaties.md>`__
-  `Tegel Proces
   Checklijsten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_proces_checklijsten.md>`__
-  `Tegel
   Product </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_product.md>`__
-  `Tegel
   Producten/Diensten </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_producten_diensten.md>`__
-  `Tegel
   Status </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_status.md>`__
-  `Tegel Verbonden aan
   Groep </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_verbonden_aan_groep.md>`__
-  `Tegel Wettelijke
   Grondslagen </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_wettelijke_grondslagen.md>`__
