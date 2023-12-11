# Detailscherm woonplaats/ lijst openbare ruimtes

Wordt aangeroepen vanuit de detailscherm gemeente/lijst woonplaatsen vanuit tegel *Locaties* op het openingsportaal.

## Detailscherm woonplaats

Schermidentifier: MDDC_getWoonplaatsDetail.xml.

## Problemen

Het scherm geeft een foutmelding, indien:

  * er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
  * de inlogger moet lid zijn van rechtengroep die kijkrechten heeft op de locatie-adressen (tbrechten.dlaspvvsb).

## Muteren

De kolommen van de woonplaats kunnen gemuteerd worden indien de inlogger lid is van een rechtengroep die mutatierechten heeft op de locatie-adressen (tbrechten.dldpcedt).

De BAG-datum kan alleen worden gemuteerd met de *synchroniseer-met-BAG knop* links onderin.

## Trigger links onderin

De **synchroniseer-met-BAG knop voor woonplaatsidentificatie** links onderin is alleen zichtbaar en enabled indien:

  * de instelling *Sectie: KoppelingBAG  Item: Methode* en *Tekst = StUF-310* bestaat en is aangevinkt 
  * EN de inlogger lid is van een rechtengroep die BAG rechten heeft op de locatie-adressen (tbrechten.dldpclbag)
  * EN de gemeente-id van de bovenliggende gemeente moet gevuld zijn
  * EN de instelling *Sectie: KoppelingBAG * en* Item: Ontvangstadres* bestaat en kolom *Tekst* is gevuld met het endpoint voor beantwoordensynchronevraag
  * EN de instelling *Sectie: KoppelingBAG * en *Item: HTTPSoapAction_wplLv01* bestaat en kolom *Tekst* is gevuld met `[http://www.egem.nl/StUF/sector/bg/0310/wplLv01](http://www.egem.nl/StUF/sector/bg/0310/wplLv01.md)`
  * EN de stuurgegevens (kolom *Tekst*) bij *Sectie: KoppelingBAG* op *items: ontvanger_applicatie en ontvanger_organisatie en zender_applicatie en zender_organisatie* zijn gevuld.

Zie verder wplLv01-bericht bij [BAG bevraging](/docs/probleemoplossing/programmablokken/bag_bevraging.md).

## Lijst Openbare Ruimtes

Schermidentifier: MDLC_getOpenbRuimtesList.xml.

### Welke gegevens worden getoond

De openbare ruimtes uit de tabel tbopenbareruimte waarvan dnkeywoonplaats gelijk is aan de dnkey van de betrokken woonplaats. 

## Problemen

Het scherm geeft een foutmelding:

  * er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
  * de inlogger moet lid zijn van rechtengroep die kijkrechten heeft op de locatie-adressen (tbrechten.dlaspvvsb).

## Triggers

  * In het scherm: dubbel klikken op een regel opent het detailscherm van de geselecteerde openbare ruimte met daarin opgenomen de lijst van locatie-adressen die horen bij die openbare ruimte. Altijd enabled. 
  * Insertknop linksonder. Zichtbaar en Enabled indien de inlogger lid is van rechtengroep die insertrechten heeft op de locatie-adressen (tbrechten.dldpclins).
  * Deleteknop linksonder. Zichtbaar en Enabled indien de inlogger lid is van rechtengroep die deleterechten heeft op de locatie-adressen (tbrechten.dldpcldel).

## Nieuwe openbare ruimte ophalen uit BAG

In de wizard die gestart wordt met insert-knop is de mogelijkheid om een lijst van openbare ruimtes uit de BAG te halen indien:

  * De instelling *Sectie: KoppelingBAG  Item: Methode* en *Tekst = StUF-310* bestaat en is aangevinkt 
  * EN de inlogger lid is van een rechtengroep die BAG rechten heeft op de locatie-adressen (tbrechten.dldpclbag)
  * EN de woonplaats-id van de bovenliggende woonplaats moet gevuld zijn
  * EN de instelling *Sectie: KoppelingBAG * en* Item: Ontvangstadres* bestaat en kolom *Tekst* is gevuld met het endpoint voor beantwoordensynchronevraag
  * EN de instelling *Sectie: KoppelingBAG * en *Item: HTTPSoapAction_oprLv01* bestaat en kolom *Tekst* is gevuld met `[http://www.egem.nl/StUF/sector/bg/0310/oprLv01](http://www.egem.nl/StUF/sector/bg/0310/oprLv01.md)`
  * EN de stuurgegevens (kolom *Tekst*) bij *Sectie: KoppelingBAG* op *items: ontvanger_applicatie en ontvanger_organisatie en zender_applicatie en zender_organisatie* zijn gevuld.

Zie verder oprLv01-bericht bij [BAG bevraging](/docs/probleemoplossing/programmablokken/bag_bevraging.md).

