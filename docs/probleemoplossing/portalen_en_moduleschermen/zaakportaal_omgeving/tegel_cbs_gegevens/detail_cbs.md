# Detailscherm CBS

De schermidentifier is: **MDDC_getCbsDetail.xml**.

Dit scherm kan worden aangeroepen vanuit het omgevingsdetailscherm, knop linksonder _CBS_ en vanaf tegel [Tegel CBS-gegevens](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_cbs_gegevens.md) bij een omgevingszaak (tbcbs_gegevens_w011).

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft op CBS.

### Muteren

De kolommen kunnen gemuteerd worden indien:

- de inlogger wijzigrechten heeft op CBS
- en die bovenliggende omgevingszaak niet is geblokkeerd
- en de editschuif aan staat.

Daarop zijn de volgende uitzonderingen:

- De kolommen _Gemeentenr_ en _Uw volgnr_ zijn niet muteerbaar
- De kolom _Datum verg.(jjjjmm)_ is niet muteerbaar TENZIJ instelling _Sectie: Programma, Item: CBSZichtbaarNegeerZaakstatus_ is aangevinkt

De kolommen _Soort Bouwwerk (oud)_ en _Bedrijfstak (oud)_ zijn verouderd en alleen zichtbaar indien deze gevuld waren voor de update naar versie 1.28 van OpenWave. Ze zullen voor deze kaarten onzichtbaar worden zodra nieuwe velden _Soort Bouwwerk_ en _Bedrijfstak_ door de gebruiker gevuld worden.

### Automatisch vullen van velden bij aanmaken kaart in CBS-tabel

Nog voordat het detailscherm getoond wordt, zal indien er nog geen CBS-kaart bestaat deze eerst worden aangemaakt (dit gebeurd zonder tonen van scherm aan de gebruiker).

Hierbij worden de volgende velden als volgt gevuld door de programmatuur:

- **Gemeentenummer** met het gemeenteid
- **Uw volgnummer** met de wavezaakcode
- **Datum vergunning** met de jaar en maand van de besluitdatum van de vergunning (indien gevuld)
- **Ligging bouwwerk** met de straat van het adres waarop de vergunning zich afspeelt
- **Woonplaats** met de woonplaats van het adres waarop de vergunning zich afspeelt
- **Postcode gebied** met het cijfergedeelte van de postcode van het adres waarop de vergunning zich afspeelt
- **Naam opdrachtgever** met de persoons- of bedrijfsnaam van de Aanvrager (indien aanwezig)
- **Bruto inhoud** met totaalsom bruto inhoud van alle W011 activiteiten bij de vergunning (naar beneden afgerond)
- **Bruto vloeroppervlakte** met totaalsom bruto oppervlak van alle W011 activiteiten bij de vergunning (naar beneden afgerond)
- **Bouwkosten exl. BTW x 1000** met totaalsom bouwkosten (indien herzien gevuld dan de herziene, indien vaste kosten gevuld dan de vaste, indien opgegeven kosten gevuld dan de opgegeven kosten) van alle W011 activiteiten bij de vergunning (naar beneden afgerond op duizendtallen)

### Triggers in het scherm zelf (achter de kolommen)

- Indien kolom _Soort bouwwerk_ gewijzigd wordt dan wordt kolom _Soort gebouwtype_ leeggemaakt
- _Soort gebouwtype_ kan alleen gekozen worden indien _Soort bouwwerk_ gevuld is
