# Lijst Gemeentes

De schermidentifier is: MDLC_getGemeentesList.xml.

Dit scherm wordt aangeroepen met action *getflexList(tb33gemeente)* vanuit het openingsportaal (tegel *Locaties*).

## Welke gegevens worden getoond

De (distinct) gemeente-kolommen uit de view vwfrmwoonplaatsen, dat zijn de niet vervallen gemeente-id's met bijbehorende gemeentenamen conform de landelijke tabel 33 waaraan één of meer woonplaatsen zijn gekoppeld. Dat betekent dus dat alleen die gemeentes worden getoond waarbij een woonplaats is gedefinieerd.

## Problemen

Het scherm geeft een foutmelding:

  * er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie/README.md)) die niet valide is
  * de inlogger moet lid zijn van rechtengroep die kijkrechten heeft op de locatie-adressen (tbrechten.dlaspvvsb).

## Triggers

In het scherm: dubbel klikken op een regel opent het detailscherm van de geselecteerde gemeente met daarin opgenomen de lijst van gedefinieerde woonplaatsen bij die gemeente.
Altijd enabled.

