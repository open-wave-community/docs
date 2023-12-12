# Zaakportaal Omgeving

AanroepAction: OpenTabPage(#omgevingdetail/x) waarbij x = primary key uit tbomgvergunningen.

voor detailscherm van tbomgvergunning zie: [Detailscherm Omgevingszaak](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken.md)

## Problemen

Het scherm ziet er raar uit (al of niet met foutmelding) of reageert niet:

- de variabele x uit de aanroep verwijst niet naar een bestaande tbomgvergunning.dnkey
- inlogger heeft geen kijkrechten voor Omgevingszaken (zie rechten: de inlogger behoort tot een rechtengroep waarbij _Omgevingszaken Zichtbaar_ niet is aangevinkt)
- de variabele x uit de aanroep verwijst naar een zaak van een gemeente waarvoor de inlogger geen kijkrechten rechten (zie instelling medewerker: alleen gemeentes en/of medewerker is lid van compartiment en de locatie van de zaak valt niet onder de aan het compartiment toegekende gemeentes)
- alle tegels zijn disabled of onzichtbaar op conditie (zie [Portaldefinitie](/instellen_inrichten/portaldefinitie/README.md))
- geen enkele tegel uit dit portal is toegekend aan inlogger.

Medewerker a ziet meer of minder tegels dan medewerker b:

Dit kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan medewerker b.

## Triggers knoppen rechtsboven

### Externe link

Knop is zichtbaar en enabled voor niet-compartimentszaken indien kolom _Logic_ van de instelling _Sectie: ExterneLink_ en _Item: Omgeving_ aangevinkt is. Voor compartimentszaken dient veld _Externe link naar DMS (portaalknop Externe link kijkt naar deze instelling)_ gevuld te zijn bij het desbetreffende compartiment in het beheerportaal. Daarnaast moet het omgevingszaakrecht _starten van hyperlink vanuit portaal_ aangevinkt zijn bij de rechtengroep van de inlogger. Van de kolom _Tekst_ van bovengenoemde instelling wordt een hyperlink gemaakt, waarbij de variabelen in die Tekst

- `%zaakjaar%` met het jaar van startdatum van de omgevingszaak wordt vervangen: YYYY
  - `%zaakjaar%` met jaar en maand van startdatum wordt vervangen: YYYYMM
  - `%zaaknr%` met de OpenWave Zaakcode (dvzaakcode) van de omgevingszaak
  - `%dmsnr%` met externe zaak/dms nummer (dvintzaakcode) van de omgevingszaak (indien aangevinkt is dat het DMS E-Suite is dan wordt de benodigde vertaalslag op deze tag uitgevoerd)
  - `%postcode%` met postcode van locatie adres
  - `%huisnummer%` met huisnummer van locatie adres.

### Docs

- Indien de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt, dan wordt direct de lijst met [geregistreerde documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md) geopend (op basis van tbcorrespondentie). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien geregistreerde documenten (tbomgrechten.dlcomgcorregvsb)_ heeft.
  - Anders, (deze instelling staat uit) dan wordt de (live-)lijst van opgeslagen documenten bij de zaak geopend: zie [Toon documenten en download](/probleemoplossing/programmablokken/toon_documenten_en_download.md). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien documenten buiten registratie om (dlcomgcorvsb)_ heeft.

### Kaart

Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet ingevuld zijn van de kolom _Info_ van de instelling _Sectie: Programma Item: ToonKaart_ wordt met deze knop een externe kaart geopend (conform de URL in die kolom _Info_, waarbij %x% en %y% vervangen worden door de locatiecoördinaten en %zoom% door _Getal2_), of een interne kaart van OpenWave. Zie:[Kaart](/probleemoplossing/module_overstijgende_schermen/kaart.md).

### Locatie

Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot melding onvoldoende rechten (hoofdscherm rechten: _locatieadressen zichtbaar_).

### Memo

Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot melding onvoldoende rechten (rechten omgevingszaak _memo zichtbaar_).

### Detailscherm omgeving

Knop is altijd zichtbaar en enabled.

## Overige triggers

Klikken op tegel opent een vervolgscherm.

Indien niet klikbaar dan is de tegel ingesteld als disabled (zie [Portaldefinitie](/instellen_inrichten/portaldefinitie/README.md)).

## Gerelateerde Pagina's

- [Detailscherm Omgevingszaak](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken.md)
- [Tegel Activiteiten Oorspronkelijke Zaak](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_activiteiten_oorspronkelijke_zaak.md)
- [Tegel Afgehandelde Adviezen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgehandelde_adviezen.md)
- [Tegel Afgeronde Inspectietrajecten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgehandelde_inspectietrajecten.md)
- [Tegel Afgehandelde processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgehandelde_processtappen.md)
- [Tegel Afgerond Bezwaar/Beroep](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgerond_bezwaar_beroep.md)
- [Tegel Afgeronde Overtredingen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgeronde_issues.md)
- [Tegel Afgeronde zaken bij dit project](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgeronde_zaken_bij_dit_project.md)
- [Tegel Afgesloten Inspectiebezoeken](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgesloten_inspectiebezoeken.md)
- [Tegel Afgeronde zaken op dit adres](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgesloten_zaken_op_dit_adres.md)
- [Tegel Afgesloten Inspectiebezoeken](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgesloten_inspectiebezoeken.md)
- [Tegel Afgeronde zaken op dit adres](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_afgesloten_zaken_op_dit_adres.md)
- [Tegel Alert](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_alert.md)
- [Tegel Alle processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_alle_processtappen.md)
- [Tegel Bestemmingplantoets (vigerend)](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_bestemmingplantoets_vigerend.md)
- [Tegel Bestemmingplantoets (in voorbereiding)](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_bestemmingsplantoets_invoorb.md)
- [Tegel Bestuurlijke Maatregelen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_bestuurlijke_maatregelen.md)
- [Tegel CBS-gegevens](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_cbs_gegevens.md)
- [Tegel Collegiale Toetsen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_collegiale_toetsen.md)
- [Tegel Contactadressen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_contactadressen.md)
- [Tegel Documenten Oorspronkelijke Zaak](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_documenten_oorspronkelijke_zaak.md)
- [Tegel Dossierbehandelaars](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_dossierbehandelaars.md)
- [Tegel DSO Historie Bevoegd Gezag](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_dso_bevoeg_gezag_historie.md)
- [Tegel DSO Historie Behandeldienst](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_dso_historie_behandeldienst.md)
- [Tegel Erkende Maatregelen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_erkende_maatregelen.md)
- [Tegel Gekoppeld aan inrichting](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_gekoppeld_aan_inrichting.md)
- [Tegel Geregistreerde Documenten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_geregistreerdee_doucmenten.md)
- [Tegel DSO Gerelateerde Zaken](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_gerelateerde_zaken.md)
- [Tegel Installaties](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_installaties.md)
- [Tegel Projectlocaties/Kadastrale Percelen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_kadastrale_percelen.md)
- [Tegel Leges](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_leges.md)
- [Tegel Lopend Bezwaar/Beroep](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_lopend_bezwaar_beroep.md)
- [Tegel Lopende Inspectietrajecten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_lopende_inspectietrajecten.md)
- [Tegel Lopende zaken bij dit project](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_lopende_zaken_bij_dit_project.md)
- [Tegel Lopende zaken op dit adres](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_lopende_zaken_op_dit_adres.md)
- [Tegel OLO/AIM/DSO-berichten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_olo-aim_berichten.md)
- [Tegel onderdelen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_onderdelen.md)
- [Tegel Openstaande Adviezen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_openstaande_adviezen.md)
- [Tegel Openstaande Inspectiebezoeken](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_openstaande_inspectiebezoeken.md)
- [Tegel Openstaande Invorderingen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_openstaande_invorderingen.md)
- [Tegel Openstaande Overtredingen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_openstaande_issues.md)
- [Tegel Openstaande processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_openstaande_processtappen.md)
- [Tegel Preparaties](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_preparaties.md)
- [Tegel Proces Checklijsten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_proces_checklijsten.md)
- [Tegel Product](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_product.md)
- [Tegel Producten/Diensten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_producten_diensten.md)
- [Tegel Samenwerkingsruimtes](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_samenwerkingsruimtes.md)
- [Tegel Status](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_status.md)
- [Tegel Uren](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_uren.md)
- [Tegel Verbonden aan DSO-Project](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_verbonden_aan_dso_project.md)
- [Tegel Verbonden aan Groep](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_verbonden_aangroep.md)
