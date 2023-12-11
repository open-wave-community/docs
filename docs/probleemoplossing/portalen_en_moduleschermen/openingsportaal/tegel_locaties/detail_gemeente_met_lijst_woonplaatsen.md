# Detailscherm gemeente/ lijst woonplaatsen

Wordt aangeroepen vanuit de Lijst *Gemeentes* vanuit tegel *Locaties* op het openingsportaal.

## Detailscherm gemeente

Schermidentifier: MDDC_getGemeenteDetail.xml. 

## Problemen

Het scherm geeft een foutmelding, indien:

  * er mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) is die niet valide is.
  * de inlogger moet lid zijn van rechtengroep die kijkrechten heeft op de locatie-adressen (tbrechten.dlaspvvsb).

### Muteren

De kolommen van de gemeente kunnen NIET gemuteerd worden (ook niet als de editschuif wordt aangezet).

## Lijst Woonplaatsen

Schermidentifier: MDLC_getWoonplaatsenList.xml.

#### Welke gegevens worden getoond

De woonplaatsen uit de view vwfrmwoonplaatsen waarvan dvgemeenteid gelijk is aan de gemeente-id van het detailscherm gemeente. 

#### Problemen

Het scherm geeft een foutmelding:

  * er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
  * de inlogger moet lid zijn van rechtengroep die kijkrechten heeft op de locatie-adressen (tbrechten.dlaspvvsb).

#### Triggers

  * In het scherm: dubbel klikken op een regel opent het detailscherm van de geselecteerde woonplaats met daarin opgenomen de lijst van gedefinieerde openbare ruimtes bij die woonplaats. Altijd enabled. 
  * Insertknop linksonder. Zichtbaar en Enabled indien de inlogger lid is van rechtengroep die insertrechten heeft op de locatie-adressen (tbrechten.dldpclins).
  * Deleteknop linksonder. Zichtbaar en Enabled indien de inlogger lid is van rechtengroep die deleterechten heeft op de locatie-adressen (tbrechten.dldpcldel).

#### Nieuwe woonplaats bij andere gemeente

Met de insertknop zal een wizard worden gestart die de gebruiker eerst laat kiezen uit de volledige gemeentetabel (beheertegel *Gemeentes*) rekening houdend met ingangsdatum en vervaldatum. Vervolgens kan de gebruiker een woonplaatsnaam opgeven bij de gekozen gemeente. De gekozen gemeente kan dus een andere zijn dan die van het actieve detailscherm, zodat de nieuw opgevoerde woonplaats niet direct zichtbaar is. Daartoe moet de gebruiker opnieuw de juiste gemeente kiezen uit de lijst.

