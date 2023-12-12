# Zaakportaal Milieu/gebruik

AanroepAction: OpenTabPage(#milieugebruikdetail/x) waarbij x = primary key uit tbmilvergunningen.
Schermtype portal.

## Problemen

1. Het scherm ziet er raar uit (al of niet met errormelding) of reageert niet:

- de variabele x uit de aanroep verwijst niet naar een bestaande tbmilvergunningen.dnkey
- inlogger heeft geen kijkrechten voor Milieu/gebruikzaken (zie rechten: de inlogger behoort tot een rechtengroep waarbij _Milieu/gebruik Zichtbaar_ niet is aangevinkt)
- de variabele x uit de aanroep verwijst naar een zaak van een gemeente waarvoor de inlogger geen kijkrechten rechten (zie instelling medewerker: alleen gemeentes en/of medewerker is lid van compartiment en de locatie van de zaak valt niet onder de aan het compartiment toegekende gemeentes)
- alle tegels zijn disabled of onzichtbaar op conditie (zie [Portaldefinitie](/instellen_inrichten/portaldefinitie/README.md))
- geen enkele tegel uit dit portal is toegekend aan inlogger.

2. Medewerker a ziet meer of minder tegels dan medewerker b:

kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan medewerker b.

## Triggers

Welke knop/triggers rechtsboven?

### Externe link

Knop is zichtbaar en enabled indien:

- voor niet-compartimentszaken kolom Logic van de instelling _Sectie: ExterneLink_ en _Item: MilieuGebruik_ aangevinkt is
  - voor compartimentszaken dient veld _Externe link naar DMS (portaalknop Externe link kijkt naar deze instelling)_ gevuld te zijn bij het desbetreffende compartiment in beheerportaal-Nieuw
  - en het Milieugebruikzaakrecht _starten van hyperlink vanuit portaal_ aangevinkt is bij de rechtengroep van de inlogger. Van de kolom _Tekst_ van bovengenoemde instelling wordt een hyperlink gemaakt, waarbij de variabelen in die Tekst:
    - `%zaakjaar%` met het jaar van ontvangstdatum van de Milieu/Gebruik zaak wordt vervangen: YYYY
    - `%zaakjaar%` met jaar en maand van ontvangstdatum wordt vervangen: YYYYMM
    - `%zaaknr%` met de OpenWave Zaakcode (dvvergnummer) van de Milieu/Gebruik zaak
    - `%dmsnr%` met externe zaak/DMS nummer (dvintzaakcode) van de Milieu/Gebruik zaak (indien aangevinkt is dat het DMS E-Suite is dan wordt de benodigde vertaalslag op deze tag uitgevoerd)
    - `%postcode%` met postcode van locatie adres
    - `%huisnummer%` met huisnummer van locatie adres.

### Docs

- Indien de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt, dan wordt direct de lijst met [geregistreerde documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md) geopend (op basis van tbcorrespondentie). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien geregistreerde documenten (tbmilvergrechten.dlcmilvergcorregvsb)_ heeft.
  - Anders, (deze instelling staat uit) dan wordt de (live-)lijst van opgeslagen documenten bij de zaak geopend: zie [Toon documenten en download](/probleemoplossing/programmablokken/toon_documenten_en_download.md). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien documenten buiten registratie om (dlcmilvergcorvsb)_ heeft.

### Kaart

- Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet ingevuld zijn van de kolom _Info_ van de instelling _Sectie: Programma Item: ToonKaart_ wordt met deze knop een externe kaart geopend (conform de URL in die kolom _Info_, waarbij %x% en %y% vervangen worden door de locatiecoordinaten en %zoom% door _Getal2_), of een interne kaart van OpenWave. Zie:[Kaart](/probleemoplossing/module_overstijgende_schermen/kaart.md).

### Memo

- Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot melding onvoldoende rechten (rechten MilieuGebruik _Memo wijzigen_).
- _Locatie_

Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot melding onvoldoende rechten (hoofdscherm rechten: _locatieadressen zichtbaar_).

- _Detailscherm MilieuGebruik_

Knop is altijd zichtbaar en enabled.

### Overige trigger

Klikken op tegel opent een vervolgscherm.

Indien niet klikbaar dan is de tegel ingesteld als disabled (zie [Portaldefinitie](/instellen_inrichten/portaldefinitie/README.md)).

## Gerelateerde Pagina's

- [Detailscherm Milieu/Gebruikszaak](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/detailscherm_milieu_gebruikszaken.md)
- [Tegel Afgehandelde Adviezen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_afgehandelde_adviezen.md)
- [Tegel Afgehandelde Processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_afgehandelde_processtappen.md)
- [Tegel Afgerond Bezwaar/Beroep](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_afgerond_bezwaar_beroep.md)
- [Tegel Afgeronde zaken op dit adres](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_afgesloten_zaken_op_dit_adres.md)
- [Tegel Alle processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_alle_processtappen.md)
- [Tegel Collegiale Toetsen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_collegiale_toetsen.md)
- [Tegel Contactadressen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_contactadressen.md)
- [Tegel Dossierbehandelaars](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_dossierbehandelaars.md)
- [Tegel Gebouwen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_gebouwen.md)
- [Tegel Gekoppeld aan inrichting](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_gekoppeld_aan_inrichting.md)
- [Tegel Gekoppeld aan inrichting](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik.md)
- [Tegel Geregistreerde Documenten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_geregistreerde_documenten.md)
- [Tegel Installaties](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_installaties.md)
- [Tegel Lopend Bezwaar/Beroep](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_lopend_bezwaar_beroep.md)
- [Tegel Lopende zaken op dit adres](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_lopende_zaken_op_dit_adres.md)
- [Tegel OLO/AIM-berichten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_olo-aim-berichten.md)
- [Tegel Openstaande Adviezen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_openstaande_adviezen.md)
- [Tegel Openstaande processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_openstaande_processtappen.md)
- [Tegel Preparaties](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_preparaties.md)
- [Tegel Proces Checklijsten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_proces_checklijsten.md)
- [Tegel Product](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_product.md)
- [Tegel Producten/Diensten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_producten_diensten.md)
- [Tegel Status](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_status.md)
- [Tegel Verbonden aan Groep](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_verbonden_aan_groep.md)
- [Tegel Wettelijke Grondslagen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_milieu_gebruik/tegel_wettelijke_grondslagen.md)
