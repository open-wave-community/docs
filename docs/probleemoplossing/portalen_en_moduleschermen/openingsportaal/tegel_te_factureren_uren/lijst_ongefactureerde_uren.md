# Lijst Ongefactureerde Uren

Schermidentifier: MDLC_getOngefactureerdeUrenList.xml.

Zie ook [Tegel Te factureren uren](/docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_te_factureren_uren.md)

## Welke gegevens worden getoond

De rijen uit de view vwfrmuren dat zijn de geschreven uren per (deel)zaak.

Boven op deze where clausules van de view zijn de volgende extra restricties van kracht:

- alleen die uren worden getoond waarvan de factuur c.q. fiatdatum (ddgefactureerd) leeg is en de kolom opdrachtgever akkoord (dlopdrachtgeverakloord) de waarde _akkoord_ of _nog niet bekend_ heeft
- indien de inlogger lid is van een compartiment, dan is dat in de koptekst zichtbaar en dan worden alleen die uren getoond:
  - die horen bij een hoofdzaak (dus rechtstreeks op bijv. een omgevingszaak) of bij een advies bij die hoofdzaak waarvan de combinatie zaaktype/gemeente in het betreffende compartiment is opgenomen
  - die horen bij een deelzaak inspectie of bezwaarberoep bij een hoofdzaak waarvan de combinatie zaaktype/gemeente in het betreffende compartiment is opgenomen en waarbij in het compartiment aangegeven is respectievelijk inclusief inspectie en inclusief bezwaar/beroep
- indien de inlogger geen lid is van een compartiment, dan worden alleen die uren getoond:
  - die horen bij een hoofdzaak (dus rechtstreeks op bijv. een omgevingszaak) of bij een advies bij die hoofdzaak waarvan de combinatie zaaktype/gemeente in geen enkel compartiment is opgenomen
  - die horen bij een deelzaak inspectie of bezwaarberoep bij een hoofdzaak waarvan de combinatie zaaktype/gemeente in een compartiment is opgenomen en waarbij in dat compartiment aangegeven is respectievelijk Exclusief inspectie en Exclusief bezwaar/beroep.

## Rechten

De lijst kan alleen opgevraagd worden door een medewerker waarbij het recht _mag uren van anderen muteren_ aangevinkt staat op zijn/haar de medewerkerskaart (tbmedewerker.dlmagurenmuteren).

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de ongefactureerde uren:
  - zie de criteria hierboven
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ van tbinitialisatie _Sectie: Paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd de urendetailkaart
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt)
- de knop _start facturatie_ rechtsonder. Alleen zichtbaar indien de medewerker het recht _mag factuurdatum bij uren muteren_ aangevinkt heeft staan op zijn/haar medewerkerskaart (tbmedewerkers.dlmagurenfactmut).

Het factureren behelst het vullen van de urenkaarten met een factuurdatum en het exporteren van die kaarten naar een Excel file onderverdeeld in gemeente-tabbladen. De knop opent een wizard waarin de gebruiker allereerst moet kiezen of een eerdere export ongedaan moet worden gemaakt (dit betekent het leegmaken van de factuurdatum op de urenkaarten wanneer deze gelijk is aan een op te geven datum) of dat een nieuwe export moet worden gestart, waarbij de gebruiker een bereik moet opgeven (datum vanaf en datum tot en met) en voor welke gemeentes. De Excel file wordt gedownload onder de naam ExportFactuurUren\_’ + datumvandaag + ‘.xslx’
