# Tegel CBS-gegevens

## Trigger

De tegel is een trigger voor het starten van de CBS wizard. Indien er nog geen kaart bestaat in de CBS tabel van OpenWave dan zal bij klikken op de tegel een CBS-kaart worden aangemaakt en vervolgens het [detailscherm CBS](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/tegel_cbs_gegevens/detail_cbs.md) worden geopend.

Indien de de CBS-kaart wordt aangemaakt dan worden de volgende velden automatisch (en als volgt) gevuld:

- **Gemeentenummer** met het gemeenteid
- **Uw volgnummer** met de wavezaakcode (is deze langer dan toegestaan aantal tekens (20) dan vult het programma het veld met _waarde te lang_)
- **Datum vergunning** met de jaar en maand van de besluitdatum van de vergunning (indien gevuld)
- **Ligging bouwwerk** met de straat van het adres waarop de vergunning zich afspeelt (is deze langer dan toegestaan aantal tekens (32) dan vult het programma het veld met _waarde te lang_)
- **Woonplaats** met de woonplaats van het adres waarop de vergunning zich afspeelt (is deze langer dan toegestaan aantal tekens (18) dan vult het programma het veld met _waarde te lang_)
- **Postcode gebied** met het cijfergedeelte van de postcode van het adres waarop de vergunning zich afspeelt
- **Naam opdrachtgever** met de persoons- of bedrijfsnaam van de Aanvrager (indien aanwezig) (is deze langer dan toegestaan aantal tekens (40) dan vult het programma het veld met _waarde te lang_)
- **Bruto inhoud** met totaalsom bruto inhoud van alle W011 activiteiten bij de vergunning (naar beneden afgerond)
- **Bruto vloeroppervlakte** met totaalsom bruto oppervlak van alle W011 activiteiten bij de vergunning (naar beneden afgerond)
- **Bouwkosten exl. BTW x 1000** met totaalsom bouwkosten (indien herzien gevuld dan de herziene, indien vaste kosten gevuld dan de vaste, indien opgegeven kosten gevuld dan de opgegeven kosten) van alle W011 activiteiten bij de vergunning (naar beneden afgerond op duizendtallen)

Bestaat er al wel een kaart in de tabel bij klikken op de tegel dan opent het detailscherm CBS direct.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert:
    - de omgevingszaak niet onderdeel is van een verspreide vergunning
    - en in beheer bij de soort omgevingsvergunning aangegeven is dat CBS van toepassing is
    - en er tenminste 1 onderdeel/activiteit is waarbij w011 van toepassing is
    - en de besluitdatum is gevuld en de omgevingsvergunning heeft status 'Verleend', tenzij instelling _Sectie: Programma en Item: CBSZichtbaarNegeerZaakstatus_ aangevinkt is, dan wordt er niet gekeken naar de besluitdatum en de status van de vergunning
    - en compartimentscheck is ok
  - de gebruiker het recht heeft om CBS in te zien (tbrechten.dlcextcbs11vsb)
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

### Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

### Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _omgevingdetail_
- Kolom: _Overig_
- Kopregel: _CBS-gegevens_
- Dynamisch tegelopschrift:
- Actie: _startWizard(startCBS,{id},W)_
- SQL tegel onzichtbaar indien result = 0 :

```sql
SELECT
  CASE WHEN dnkeyparentverg IS NULL
    AND (SELECT dlw011 FROM tbsoortomgverg
            WHERE dnkey = (SELECT dnkeysoortomgverg FROM tbomgvergunning WHERE dnkey = {id}))
         = 'T'
    AND (SELECT Count (dnkeytoestemming) FROM vwfrmtoestemmingen
            WHERE dlw011 = 'T' AND dnkeyomgvergunningen = {id})
         > 0
    AND ((ddbesluitdatum IS NOT NULL AND dlverleend = 'T')
        OR (SELECT Count(dnkey) FROM tbinitialisatie WHERE Lower(dvsectie) = 'programma'
              AND Lower(dvitem) = 'cbszichtbaarnegeerzaakstatus'
              AND d1logic = 'T')
              > 0)
    AND ((dnkeycompartiment IS NULL AND (SELECT dnkeycompartiment FROM tbmedewerkers
                                            WHERE Trim(dvcode) = Trim(:keyaccount))
                                         IS NULL)
        OR (dnkeycompartiment IS NOT NULL AND dnkeycompartiment =
             (SELECT dnkeycompartiment FROM tbmedewerkers
                 WHERE Trim(dvcode) = Trim(:keyaccount)))
        OR  (SELECT dloverrulecompartiment FROM tbmedewerkers
                WHERE Trim(dvcode) = Trim(:keyaccount))
            = 'T')
  THEN 1
  ELSE 0
  END
FROM   vwfrmomgvergunningen
WHERE  dnkeyomgvergunning = {id}
```
