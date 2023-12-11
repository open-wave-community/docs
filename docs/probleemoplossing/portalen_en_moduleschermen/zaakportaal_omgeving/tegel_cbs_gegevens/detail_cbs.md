# Detailscherm CBS

De schermidentifier is: **MDDC_getCbsDetail.xml**.

Dit scherm kan worden aangeroepen vanuit het omgevingsdetailscherm, knop linksonder *CBS* en vanaf tegel [Tegel CBS-gegevens](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_cbs_gegevens.md) bij een omgevingszaak (tbcbs_gegevens_w011).

## Error

Het scherm geeft een foutmelding, indien:

  * er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
  * de inlogger geen kijkrechten heeft op CBS.

### Muteren

De kolommen kunnen gemuteerd worden indien:

  * de inlogger wijzigrechten heeft op CBS
  * EN die bovenliggende omgevingszaak niet is geblokkeerd 
  * EN de editschuif aan staat.

Daarop zijn de volgende uitzonderingen:

  * De kolommen *Gemeentenr* en *Uw volgnr* zijn niet muteerbaar
  * De kolom *Datum verg.(jjjjmm)* is niet muteerbaar TENZIJ instelling *Sectie: Programma, Item: CBSZichtbaarNegeerZaakstatus* is aangevinkt

De kolommen *Soort Bouwwerk (oud)* en *Bedrijfstak (oud)* zijn verouderd en alleen zichtbaar indien deze gevuld waren voor de update naar versie 1.28 van OpenWave. Ze zullen voor deze kaarten onzichtbaar worden zodra nieuwe velden *Soort Bouwwerk * en *Bedrijfstak* door de gebruiker gevuld worden. 

### Automatisch vullen van velden bij aanmaken kaart in CBS-tabel

Nog voordat het detailscherm getoond wordt, zal indien er nog geen CBS-kaart bestaat deze eerst worden aangemaakt (dit gebeurd zonder tonen van scherm aan de gebruiker).

Hierbij worden de volgende velden als volgt gevuld door de programmatuur:

  * **Gemeentenummer** met het gemeenteid
  * **Uw volgnummer** met de wavezaakcode
  * **Datum vergunning** met de jaar en maand van de besluitdatum van de vergunning (indien gevuld)
  * **Ligging bouwwerk** met de straat van het adres waarop de vergunning zich afspeelt
  * **Woonplaats** met de woonplaats van het adres waarop de vergunning zich afspeelt
  * **Postcode gebied** met het cijfergedeelte van de postcode van het adres waarop de vergunning zich afspeelt
  * **Naam opdrachtgever** met de persoons- of bedrijfsnaam van de Aanvrager (indien aanwezig)
  * **Bruto inhoud** met totaalsom bruto inhoud van alle W011 activiteiten bij de vergunning (naar beneden afgerond)
  * **Bruto vloeroppervlakte** met totaalsom bruto oppervlak van alle W011 activiteiten bij de vergunning (naar beneden afgerond)
  * **Bouwkosten exl. BTW x 1000** met totaalsom bouwkosten (indien herzien gevuld dan de herziene, indien vaste kosten gevuld dan de vaste, indien opgegeven kosten gevuld dan de opgegeven kosten) van alle W011 activiteiten bij de vergunning (naar beneden afgerond op duizendtallen)

### Triggers in het scherm zelf (achter de kolommen)

  * Indien kolom *Soort bouwwerk* gewijzigd wordt dan wordt kolom *Soort gebouwtype* leeggemaakt
  * *Soort gebouwtype* kan alleen gekozen worden indien *Soort bouwwerk* gevuld is

