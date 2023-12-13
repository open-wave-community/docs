# Zaakportaal Info-aanvragen

AanroepAction: OpenTabPage(#infodetail/x) waarbij x = primary key uit tbinfoaanvragen.

## Problemen

Het scherm ziet er raar uit (al of niet met errormelding) of reageert niet:

- de variabele x uit de aanroep verwijst niet naar een bestaande tbinfoaanvragen.dnkey
- inlogger heeft geen kijkrechten voor Infozaken (zie rechten: de inlogger behoort tot een rechtengroep waarbij _Info-aanvragen Zichtbaar_ niet is aangevinkt)
- de variabele x uit de aanroep verwijst naar een zaak van een gemeente waarvoor de inlogger geen kijkrechten rechten (zie instelling medewerker: alleen gemeentes en/of medewerker is lid van compartiment en de locatie van de zaak valt niet onder de aan het compartiment toegekende gemeentes)
- alle tegels zijn disabled of onzichtbaar op conditie (zie [Portaldefinitie](../../../instellen_inrichten/portaldefinitie/README.md))
- geen enkele tegel uit dit portal is toegekend aan inlogger.

Medewerker a ziet meer of minder tegels dan medewerker b:

Dit kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan medewerker b.

## Triggers knoppen rechtsboven

### Externe link

- Knop is zichtbaar en enabled voor niet-compartimentszaken indien kolom _Logic_ van de instelling _Sectie: ExterneLink_ en _Item: Info_ aangevinkt is. Voor compartimentszaken dient veld _Externe link naar DMS (portaalknop Externe link kijkt naar deze instelling)_ gevuld te zijn bij het desbetreffende compartiment in beheerportaal-Nieuw. Daarnaast moet het infozaakrecht _starten van hyperlink vanuit portaal_ aangevinkt zijn bij de rechtengroep van de inlogger. Van de kolom _Tekst_ van bovengenoemde instelling wordt een hyperlink gemaakt, waarbij de variabelen in die Tekst:
  - `%zaakjaar%` met het jaar van startdatum van de infoaanvraag wordt vervangen: YYYY
  - `%zaakjaar%` met jaar en maand van startdatum wordt vervangen: YYYYMM
  - `%zaaknr%` met de OpenWave Zaakcode (dvinfonummer) van de infoaanvraag
  - `%dmsnr%` met externe zaak/DMS nummer (dvintzaakcode) van de infoaanvraag (indien aangevinkt is dat het DMS E-Suite is dan wordt de benodigde vertaalslag op deze tag uitgevoerd)
  - `%postcode%` met postcode van locatie adres
  - `%huisnummer%` met huisnummer van locatie adres.

### Docs

- Indien de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt, dan wordt direct de lijst met [geregistreerde documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md) geopend (op basis van tbcorrespondentie). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien geregistreerde documenten (tbinforechten.dlcinfocorregvsb)_ heeft.
- Anders, (deze instelling staat uit) dan wordt de (live-)lijst van opgeslagen documenten bij de zaak geopend: zie [Toon documenten en download](../programmablokken/toon_documenten_en_download.md). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien documenten buiten registratie om (dlcinfocorvsb)_ heeft.

### Kaart

- Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet ingevuld zijn van de kolom _Info_ van de instelling _Sectie: Programma Item: ToonKaart_ wordt met deze knop een externe kaart geopend (conform de URL in die kolom _Info_, waarbij %x% en %y% vervangen worden door de locatie coördinaten en %zoom% door _Getal2_), of een interne kaart van OpenWave. Zie:[Kaart](/probleemoplossing/module_overstijgende_schermen/kaart.md).

### Locatie

- Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot melding onvoldoende rechten (hoofdscherm rechten: locatieadressen zichtbaar).

### Memo

- Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot melding onvoldoende rechten (rechten infoaanvraag memo zichtbaar).

### Detailscherm infoaanvraag

- Knop is altijd zichtbaar en enabled.

## Overige triggers

Klikken op tegel opent een vervolgscherm.

Indien niet klikbaar dan is de tegel ingesteld als disabled (zie [Portaldefinitie](../../../instellen_inrichten/portaldefinitie/README.md)).

## Gerelateerde Pagina's

- [Detailscherm Infoaanvraag](detailscherm_infoaanvraag.md)
- [Tegel Status](status.md)
- [Tegel Afgehandelde Adviezen](tegel_afgehandelde_adviezen.md)
- [Tegel Afgehandelde Processtappen](tegel_afgehandelde_stappen.md)
- [Tegel Afgeronde zaken op dit adres](tegel_afgeronde_zaken_op_dit_adres.md)
- [Tegel Alle Processtappen](tegel_alle_stappen.md)
- [Tegel Collegiale Toetsen](tegel_collegiale_toetsen.md)
- [Tegel Contactadressen](tegel_contactadressen.md)
- [Tegel Dossierbehandelaars](tegel_dossierbehandelaars.md)
- [Tegel Geregistreerde Documenten](tegel_geregistreerde_documenten.md)
- [Tegel Leges](tegel_leges.md)
- [Tegel Lopende zaken op dit adres](tegel_lopende_zaken_op_dit_adres.md)
- [Tegel Openstaande Adviezen](tegel_openstaande_adviezen.md)
- [Tegel Openstaande Processtappen](tegel_openstaande_stappen.md)
- [Tegel Proces Checklijsten](tegel_proces_checklijsten.md)
- [Tegel Product](tegel_product.md)
- [Tegel Producten/Diensten](tegel_producten_diensten.md)
- [Tegel Verbonden aan Groep](tegel_verbonden_aan_groep.md)
