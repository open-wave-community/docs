# Zaakportaal APV/Overig

AanroepAction: OpenTabPage(#apvoverigdetail/x) waarbij x = primary key uit tbovvergunningen.

Schermtype portal.

## Problemen

1. Het scherm ziet er raar uit (al of niet met foutmelding) of reageert niet:

- de variabele x uit de aanroep verwijst niet naar een bestaande tbovvergunningen.dnkey
- inlogger heeft geen kijkrechten voor APV/Overige zaken (zie rechten: de inlogger behoort tot een rechtengroep waarbij _APV/Overige zaken Zichtbaar_ niet is aangevinkt)
- de variabele x uit de aanroep verwijst naar een zaak van een gemeente waarvoor de inlogger geen kijkrechten rechten (zie instelling medewerker: alleen gemeentes en/of medewerker is lid van compartiment en de locatie van de zaak valt niet onder de aan het compartiment toegekende gemeentes)
- alle tegels zijn disabled of onzichtbaar op conditie (zie [Portaldefinitie](/docs/instellen_inrichten/portaldefinitie/README.md))
- geen enkele tegel uit dit portal is toegekend aan inlogger.

2. Medewerker a ziet meer of minder tegels dan medewerker b:

kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan medewerker b.

## Triggers

Welke knop/triggers rechtsboven?

### Externe link

Indien het niet om een compartimentszaak gaat, is de knop zichtbaar en enabled indien kolom _Logic_ van de instelling _Sectie: ExterneLink_ en _Item: ApvOverig_ aangevinkt is. Gaat het wel om een compartimentszaak dan dient veld _Externe link naar DMS (portaalknop Externe link kijkt naar deze instelling)_ gevuld te zijn bij het desbetreffende compartiment in het beheerportaal-Nieuw. Daarnaast moet het APV/Overige zaakrecht _starten van hyperlink vanuit portaal_ aangevinkt zijn bij de rechtengroep van de inlogger. Van de kolom _Tekst_ van bovengenoemde instelling wordt een hyperlink gemaakt, waarbij de variabelen in die Tekst:

- `%zaakjaar%` met het jaar van startdatum van de APV/Overige zaak wordt vervangen: YYYY
- `%zaakjaar%` met jaar en maand van startdatum wordt vervangen: YYYYMM
- `%zaaknr%` met de OpenWave Zaakcode (dvvergunnngsnr) van de APV/overige zaak
- `%dmsnr%` met externe zaak/DMS nummer (dvintzaakcode) van de APV/overige zaak (indien aangevinkt is dat het DMS E-Suite is dan wordt de benodigde vertaalslag op deze tag uitgevoerd)
- `%postcode%` met postcode van locatie adres
- `%huisnummer%` met huisnummer van locatie adres.

### Docs

- Indien de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt, dan wordt direct de lijst met [geregistreerde documenten](/docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md) geopend (op basis van tbcorrespondentie). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien geregistreerde documenten (tbovrechten.dlcovvcorregvsb)_ heeft
- anders, (deze instelling staat uit) dan wordt de (live-)lijst van opgeslagen documenten bij de zaak geopend: zie [Toon documenten en download](/docs/probleemoplossing/programmablokken/toon_documenten_en_download.md). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien documenten buiten registratie om (dlcovvcorvsb)_ heeft.

### Kaart

Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet ingevuld zijn van de kolom _Info_ van de instelling _Sectie: Programma Item: ToonKaart_ wordt met deze knop een externe kaart geopend (conform de URL in die kolom _Info_, waarbij %x% en %y% vervangen worden door de locatiecoördinaten en %zoom% door _Getal2_), of een interne kaart van OpenWave. Zie:[Kaart](/docs/probleemoplossing/module_overstijgende_schermen/kaart.md).

### Memo

Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot melding onvoldoende rechten (rechten _APV/Overig Memo wijzigen_).

### Locatie

Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot melding onvoldoende rechten (hoofdscherm rechten: locatieadressen zichtbaar).

### Detailscherm APV/overig

Knop is altijd zichtbaar en enabled.

## Overige triggers

Klikken op tegel opent een vervolgscherm. Indien niet klikbaar dan is de tegel ingesteld als disabled (zie [Portaldefinitie](/docs/instellen_inrichten/portaldefinitie/README.md)).

## Detailscherm

[Detailscherm APV/Overige zaak](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/detailscherm_apv_overige_zaak.md)

## Tegels

- [Tegel Afgehandelde Adviezen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_afgehandelde_adviezen.md)
- [Tegel Afgeronde Inspectietrajecten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_afgehandelde_inspectietrajecten.md)
- [Tegel Afgehandelde Processtappen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_afgehandelde_processtappen.md)
- [Tegel Afgerond Bezwaar/Beroep](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_afgerond_bezwaar_beroep.md)
- [Tegel Afgeronde Overtredingen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_afgeronde_issues.md)
- [Tegel Afgeronde Overtredingen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_afgeronde_issues.md)
- [Tegel Afgesloten Inspectiebezoeken](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_afgesloten_inspectiebezoeken.md)
- [Tegel Afgeronde zaken op dit adres](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_afgesloten_zaken_op_dit_adres.md)
- [Tegel Alert](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_alert.md)
- [Tegel Alle processtappen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_alle_processtappen.md)
- [Tegel Collegiale Toetsen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_collegiale_toetsen.md)
- [Tegel Contactadressen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_contactadressen.md)
- [Tegel Dossierbehandelaars](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_dossierbehandelaars.md)
- [Tegel Gekoppeld aan inrichting](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_gekoppeld_aan_inrichting.md)
- [Tegel Geregistreerde Documenten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_geregistreerde_documenten.md)
- [Tegel Leges](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_leges.md)
- [Tegel Lopend Bezwaar/Beroep](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_lopend_bezwaar_beroep.md)
- [Tegel Lopende Inspectietrajecten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_lopende_inspectietrajecten.md)
- [Tegel Lopende zaken op dit adres](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_lopende_zaken_op_dit_adres.md)
- [Tegel Openstaande Adviezen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_openstaande_adviezen.md)
- [Tegel Openstaande Inspectiebezoeken](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_openstaande_inspectiebezoeken.md)
- [Tegel Openstaande Overtredingen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_openstaande_issues.md)
- [Tegel Openstaande processtappen](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_openstaande_processtappen.md)
- [Tegel Proces Checklijsten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_proces_checklijsten.md)
- [Tegel Product](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_product.md)
- [Tegel Producten/Diensten](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_producten_diensten.md)
- [Tegel Status](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_status.md)
- [Tegel Verbonden aan Groep](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_apv_overig/tegel_verbonden_aan_groep.md)
