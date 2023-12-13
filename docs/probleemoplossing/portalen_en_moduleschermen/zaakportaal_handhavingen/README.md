# Zaakportaal Handhavingen

AanroepAction: OpenTabPage(#handhavingdetail/x) waarbij x = primary key uit tbhandhavingen.
Schermtype portal.

## Problemen

1. Het scherm ziet er raar uit (al of niet met foutmelding) of reageert niet:

- de variabele x uit de aanroep verwijst niet naar een bestaande tbhandhavingen.dnkey
- inlogger heeft geen kijkrechten voor Handhavingszaken (zie rechten: de inlogger behoort tot een rechtengroep waarbij _Handhavingen Zichtbaar_ niet is aangevinkt)
- de variabele x uit de aanroep verwijst naar een zaak van een gemeente waarvoor de inlogger geen kijkrechten rechten (zie instelling medewerker: alleen gemeentes en/of medewerker is lid van compartiment en de locatie van de zaak valt niet onder de aan het compartiment toegekende gemeentes)
- alle tegels zijn disabled of onzichtbaar op conditie (zie [Portaldefinitie](../../../instellen_inrichten/portaldefinitie/README.md))
- geen enkele tegel uit dit portal is toegekend aan inlogger.

  2)Medewerker a ziet meer of minder tegels dan medewerker b:

kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan medewerker b.

## Triggers

Welke knop/triggers rechtsboven?

### Externe link

Knop is zichtbaar en enabled indien:

- voor niet-compartimentszaken kolom _Logic_ van de instelling _Sectie: ExterneLink_ en _Item: Handhaving_ aangevinkt is
  - voor compartimentszaken veld _Externe link naar DMS (portaalknop Externe link kijkt naar deze instelling)_ bij het desbetreffende compartiment in beheerportaal-Nieuw gevuld is
  - en het Handhavingszaakrecht _starten van hyperlink vanuit portaal_ aangevinkt is bij de rechtengroep van de inlogger. Van de kolom _Tekst_ van bovengenoemde instelling wordt een hyperlink gemaakt, waarbij de variabelen in die Tekst:
    - `%zaakjaar%` met het jaar van startdatum van de handhavingszaak wordt vervangen: YYYY
    - `%zaakjaar%` met jaar en maand van startdatum wordt vervangen: YYYYMM
    - `%zaaknr%` met de OpenWave Zaakcode (dvaanschrijfnr) van de handhavingszaak
    - `%dmsnr%` met externe zaak/dms nummer (dvintzaakcode) van de handhavingszaak (indien aangevinkt is dat het DMS E-Suite is dan wordt de benodigde vertaalslag op deze tag uitgevoerd)
    - `%postcode%` met postcode van locatie adres
    - `%huisnummer%` met huisnummer van locatie adres.

### Docs

- Indien de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt, dan wordt direct de lijst met [geregistreerde documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md) geopend (op basis van tbcorrespondentie). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien geregistreerde documenten (tbhhrechten.dlchahcorregvsb)_ heeft.
  - Anders, (deze instelling staat uit) dan wordt de (live-)lijst van opgeslagen documenten bij de zaak geopend: zie [Toon documenten en download](../programmablokken/toon_documenten_en_download.md). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien documenten buiten registratie om (dlchahcorvsb)_ heeft.

### Kaart

Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet ingevuld zijn van de kolom _Info_ van de instelling _Sectie: Programma Item: ToonKaart_ wordt met deze knop een externe kaart geopend (conform de URL in die kolom _Info_, waarbij %x% en %y% vervangen worden door de locatiecoördinaten en %zoom% door _Getal2_), of een interne kaart van OpenWave. Zie:[Kaart](/probleemoplossing/module_overstijgende_schermen/kaart.md).

### Memo

Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot melding onvoldoende rechten (rechten Handhavingen _Memo wijzigen_).

### Locatie

Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot melding onvoldoende rechten (hoofdscherm rechten: locatieadressen zichtbaar).

### Detailscherm Handhavingen

Knop is altijd zichtbaar en enabled.

## Overige triggers

Klikken op tegel opent een vervolgscherm.

Indien niet klikbaar dan is de tegel ingesteld als disabled (zie
[Portaldefinitie](../../../instellen_inrichten/portaldefinitie/README.md)).

## Gerelateerde Pagina's

- [Detailscherm Handhavingszaak](detailscherm_handhavingen.md)
- [Tegel Afgehandelde Adviezen](tegel_afgehandelde_adviezen.md)
- [Tegel Afgeronde Inspectietrajecten](tegel_afgehandelde_inspectietrajecten.md)
- [Tegel Afgehandelde Processtappen](tegel_afgehandelde_processtappen.md)
- [Tegel Afgeronde Overtredingen](tegel_afgeronde_issues.md)
- [Tegel Afgeronde zaken bij dit project](tegel_afgeronde_zaken_bij_dit_project.md)
- [Tegel Afgesloten Inspectiebezoeken](tegel_afgesloten_inspectiebezoeken.md)
- [Tegel Afgeronde zaken op dit adres](tegel_afgesloten_zaken_op_dit_adres.md)
- [Tegel Afgesloten Inspectiebezoeken](tegel_afgesloten_inspectiebezoeken.md)
- [Tegel Afgesloten zaken op dit adres](tegel_afgesloten_zaken_op_dit_adres.md)
- [Tegel Alert](tegel_alert.md)
- [Tegel Alert bij Inrichting](tegel_alert_bij_inrichting.md)
- [Tegel Alle Processtappen](tegel_alle_processtappen.md)
- [Tegel Bestuurlijke Maatregelen](tegel_bestuurlijke_maatregelen.md)
- [Tegel Collegiale Toetsen](tegel_collegiale_toetsen.md)
- [Tegel Dwangsom](tegel_dwangsom.md)
- [Tegel Geregistreerde Documenten](tegel_geregistreerde_documenten.md)
- [Tegel Kadastrale Percelen](tegel_kadastrale_percelen.md)
- [Tegel Lopende Inspectietrajecten](tegel_lopende_inspectietrajecten.md)
- [Tegel Lopende zaken bij dit project](tegel_lopende_zaken_bij_dit_project.md)
- [Tegel Lopende zaken op dit adres](tegel_lopende_zaken_op_dit_adres.md)
- [Tegel Openstaande Adviezen](tegel_openstaande_adviezen.md)
- [Tegel Openstaande Inspectiebezoeken](tegel_openstaande_inspectiebezoeken.md)
- [Tegel Openstaande Overtredingen](tegel_openstaande_issues.md)
- [Tegel Openstaande processtappen](tegel_openstaande_processtappen.md)
- [Tegel Proces Checklijsten](tegel_proces_checklijsten.md)
- [Tegel Product](tegel_product.md)
- [Tegel Producten/Diensten](tegel_producten_diensten.md)
- [Tegel Status](tegel_status.md)
- [Tegel Afgehandelde Invorderingen](tegel_tegel_afgehandelde_invorderingen.md)
- [Tegel Afgerond Bezwaar/Beroep](tegel_tegel_afgerond_bezwaar_beroep.md)
- [Tegel Contactadressen](tegel_tegel_contactadressen.md)
- [Tegel Dossierbehandelaars](tegel_tegel_dossierbehandelaars.md)
- [Tegel Gekoppeld aan Inrichting](tegel_tegel_gekoppeld_aan_inrichting.md)
- [Tegel Lopend Bezwaar/Beroep](tegel_tegel_lopend_bezwaar_beroep.md)
- [Tegel Openstaande Invorderingen](tegel_tegel_openstaande_invorderingen.md)
- [Tegel Verbonden aan Groep](tegel_tegel_verbonden_aan_groep.md)
- [Tegel Uren](tegel_uren.md)
