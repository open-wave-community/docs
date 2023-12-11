# Zaakportaal Horeca

AanroepAction: OpenTabPage(#horecadetail/x) waarbij x = primary key uit tbhorecavergunningen.

## Problemen

Het scherm ziet er raar uit (al of niet met errormelding) of reageert niet:

* de variabele x uit de aanroep verwijst niet naar een bestaande tbhorecavergunningen.dnkey
* inlogger heeft geen kijkrechten voor Horecazaken (zie rechten: de inlogger behoort tot een rechtengroep waarbij *Horecazaken Zichtbaar* niet is aangevinkt)
* de variabele x uit de aanroep verwijst naar een zaak van een gemeente waarvoor de inlogger geen kijkrechten  (zie instelling medewerker: alleen gemeentes en/of medewerker is lid van compartiment en de locatie van de zaak valt niet onder de aan het compartiment toegekende gemeentes)
* alle tegels zijn disabled of onzichtbaar op conditie (zie [Portaldefinitie](/docs/instellen_inrichten/portaldefinitie.md))
* geen enkele tegel uit dit portal is toegekend aan inlogger.

Medewerker a ziet meer of minder tegels dan medewerker b:

Dit kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan medewerker b.

## Triggers knoppen rechtsboven

### Externe link

* Knop is zichtbaar en enabled indien voor niet-compartimentszaken kolom *Logic* van de instelling *Sectie: ExterneLink* en *Item: Horeca* aangevinkt is. Voor compartimentszaken dient veld *Externe link naar DMS (portaalknop Externe link kijkt naar deze instelling)* gevuld te zijn bij het desbetreffende compartiment in het beheerportaal-Nieuw. Daarnaast moet het horecarecht *starten van hyperlink vanuit portaal* aangevinkt zijn bij de rechtengroep van de inlogger. Van de kolom *Tekst* van bovengenoemde instelling wordt een hyperlink gemaakt, waarbij de variabelen in die Tekst
  * `%zaakjaar%` met het jaar van startdatum van de horecazaak wordt vervangen: YYYY
  * `%zaakjaar%`  met jaar en maand van startdatum wordt vervangen: YYYYMM
  * `%zaaknr%`  met de OpenWave Zaakcode (dvzaakcode) van de horecazaak
  * `%dmsnr%` met externe zaak/DMS nummer (dvintzaakcode) van de horecazaak (indien aangevinkt is dat het DMS E-Suite is dan wordt de benodigde vertaalslag op deze tag uitgevoerd)
  * `%postcode%` met postcode van locatieadres
  * `%huisnummer%` met huisnummer van locatieadres.

### Docs

* Indien de instelling *Sectie: Documenten Item: Documentregistratie* is aangevinkt, dan wordt direct de lijst met [geregistreerde documenten](/docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten.md) geopend (op basis van tbcorrespondentie). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht *Inzien geregistreerde documenten (tbhorrechten.dlchorcorregvsb)* heeft.
* Anders, (deze instelling staat uit) dan wordt de (live-)lijst van opgeslagen documenten bij de zaak geopend: zie [Toon documenten en download](/docs/probleemoplossing/programmablokken/toon_documenten_en_download.md). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht *Inzien documenten buiten registratie om (dlchorcorvsb)* heeft.

### Kaart

* Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet ingevuld zijn van de kolom *Info* van de instelling *Sectie: Programma Item: ToonKaart* wordt met deze knop een externe kaart geopend (conform de URL in die kolom *Info*, waarbij %x% en %y% vervangen worden door de locatiecoordinaten en %zoom% door *Getal2*), of een interne kaart van OpenWave. Zie:[Kaart](/docs/probleemoplossing/module_overstijgende_schermen/kaart.md)

### Locatie

* Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot melding onvoldoende rechten (hoofdscherm rechten: locatieadressen zichtbaar)

### Memo

* Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot melding onvoldoende rechten (rechten horecazaak memo zichtbaar)

### Detailscherm omgeving

* Knop is altijd zichtbaar en enabled

## Overige triggers

Klikken op tegel opent een vervolgscherm.

Indien niet klikbaar dan is de tegel ingesteld als disabled (zie [Portaldefinitie](/docs/instellen_inrichten/portaldefinitie.md)).

## Gerelateerde Pagina's

* [Detailscherm Horecazaak](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/detailscherm_horecazaak.md)
* [Tegel Afgehandelde Adviezen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_afgehandelde_adviezen.md)
* [Tegel Afgehandelde Processtappen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_afgehandelde_stappen.md)
* [Tegel Afgerond Bezwaar/Beroep](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_afgerond_bezwaar_beroep.md)
* [Tegel Afgeronde Overtredingen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_afgeronde_overtredingen.md)
* [Tegel Afgeronde trajecten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_afgeronde_trajecten.md)
* [Tegel Afgeronde zaken op dit adres](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_afgeronde_zaken_op_dit_adres.md)
* [Tegel Afgesloten bezoeken](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_afgesloten_bezoeken.md)
* [Tegel Alert](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_alert.md)
* [Tegel Alle Processtappen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_alle_stappen.md)
* [Tegel Collegiale Toetsen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_collegiale_toetsen.md)
* [Tegel Contactadressen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_contactadressen.md)
* [Tegel Dossierbehandelaars](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_dossierbehandelaars.md)[Tegel Exploitatievergunningen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_exploitatievergunning.md)
* [Tegel Gekoppeld aan inrichting](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_gekoppeld_aan_inrichting.md)
* [Tegel Geregistreerde Documenten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_geregistreerde_documenten.md)
* [Tegel Leges](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_leges.md)
* [Tegel Lopend Bezwaar/Beroep](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_lopend_bezwaar_beroep.md)
* [Tegel Lopende trajecten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_lopende_trajecten.md)
* [Tegel Lopende zaken op dit adres](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_lopende_zaken_op_dit_adres.md)
* [Tegel Openstaande Adviezen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_openstaande_adviezen.md)
* [Tegel Openstaande Bezoeken](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_openstaande_bezoeken.md)
* [Tegel Openstaande Overtredingen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_openstaande_overtredingen.md)
* [Tegel Openstaande Processtappen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_openstaande_stappen.md)
* [Tegel Overzichtsscherm](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_overzichtsscherm.md)
* [Tegel Proces Checklijsten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_proces_checklijsten.md)
* [Tegel Product](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_product.md)
* [Tegel Producten/Diensten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_producten_diensten.md)
* [Tegel Speelautomaten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_speelautomaten.md)
* [Tegel Status](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_status.md)
* [Tegel Terrasvergunning](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_terrasvergunning.md)
* [Tegel Verbonden aan Groep](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_horeca/tegel_verbonden_aan_groep.md)
