# Detailscherm openbare ruimte/ lijst locatie-adressen

Wordt aangeroepen vanuit de detailscherm woonplaats/lijst openbare ruimtes vanuit tegel *Locaties* op het openingsportaal.

## Detailscherm openbare ruimte

Schermidentifier: MDDC_getOpenbRuimteDetail.xml.

## Problemen

Het scherm geeft een foutmelding, indien:

  * er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
  * de inlogger moet lid zijn van rechtengroep die kijkrechten heeft op de locatie-adressen (tbrechten.dlaspvvsb).

### Muteren

De kolommen van de openbare ruimte kunnen gemuteerd worden indien de inlogger lid is van een rechtengroep die mutatierechten heeft op de locatie-adressen (tbrechten.dldpcedt). De BAG-datum kan alleen worden gemuteerd met de *synchroniseer-met-BAG knop* links onderin.

### Trigger links onderin

De **synchroniseer-met-BAG knop voor openbare ruimte identificatie** links onderin is alleen zichtbaar en enabled indien:

  * de instelling *Sectie: KoppelingBAG  Item: Methode* en *Tekst = StUF-310* bestaat en is aangevinkt 
  * EN de inlogger lid is van een rechtengroep die BAG rechten heeft op de locatie-adressen (tbrechten.dldpclbag)
  * EN de woonplaats-id van de bovenliggende woonplaats moet gevuld zijn
  * EN de instelling *Sectie: KoppelingBAG * en* Item: Ontvangstadres* bestaat en kolom *Tekst* is gevuld met het endpoint voor beantwoordensynchronevraag
  * EN de instelling *Sectie: KoppelingBAG * en *Item: HTTPSoapAction_oprLv01* bestaat en kolom *Tekst* is gevuld met `[http://www.egem.nl/StUF/sector/bg/0310/oprLv01](http://www.egem.nl/StUF/sector/bg/0310/oprLv01.md)`
  * EN de stuurgegevens (kolom *Tekst*) bij *Sectie: KoppelingBAG* op *items: ontvanger_applicatie en ontvanger_organisatie en zender_applicatie en zender_organisatie* zijn gevuld.

Zie verder oprLv01-bericht bij [BAG bevraging](/docs/probleemoplossing/programmablokken/bag_bevraging.md).

## Lijst Locatie-adressen

Schermidentifier: MDLC_getLokatieAdressenList.xml.

### Welke gegevens worden getoond

De locaties uit de tabel vwfrmlokaties waarvan dnkeyopenbruimte gelijk is aan de dnkey van de betrokken openbare ruimte.

## Problemen

Het scherm geeft een foutmelding:

  * er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
  * de inlogger moet lid zijn van rechtengroep die kijkrechten heeft op de locatie-adressen (tbrechten.dlaspvvsb).

## Triggers

  * In het scherm: dubbel klikken op een regel opent het detailscherm van het geselecteerde locatieadres. Altijd enabled. Zie: [Locatie detailscherm](/docs/probleemoplossing/module_overstijgende_schermen/locatie.md)
  * Insertknop linksonder. Zichtbaar en Enabled indien de inlogger lid is van rechtengroep die insertrechten heeft op de locatie-adressen (tbrechten.dldpclins).
  * Deleteknop linksonder. Zichtbaar en Enabled indien de inlogger lid is van rechtengroep die deleterechten heeft op de locatie-adressen (tbrechten.dldpcldel).
  * Samenvoegknop links onderin. Zichtbaar en enabled indien de inlogger het samenvoegrecht lokatieadressen heeft (tbrechten.dldvgedt).

### Nieuw verblijfsobject ophalen uit BAG

In de wizard die gestart wordt met insert-knop is de mogelijkheid om een lijst van verblijfsobjecten uit de BAG te halen indien:

  * de instelling *Sectie: KoppelingBAG  Item: Methode* en *Tekst = StUF-310* bestaat en is aangevinkt 
  * EN de inlogger lid is van een rechtengroep die BAG rechten heeft op de locatie-adressen (tbrechten.dldpclbag)
  * EN de BAG identificatiecode (dvopruimteid) van de bovenliggende openbare ruimte moet gevuld zijn
  * EN de instelling *Sectie: KoppelingBAG * en* Item: Ontvangstadres* bestaat en kolom *Tekst* is gevuld met het endpoint voor beantwoordensynchronevraag
  * EN de instelling *Sectie: KoppelingBAG * en *Item: HTTPSoapAction_tgoLv01* bestaat en kolom *Tekst* is gevuld met `[http://www.egem.nl/StUF/sector/bg/0310/tgoLv01](http://www.egem.nl/StUF/sector/bg/0310/tgoLv01.md)`
  * EN de stuurgegevens (kolom *Tekst*) bij *Sectie: KoppelingBAG* op *items: ontvanger_applicatie en ontvanger_organisatie en zender_applicatie en zender_organisatie* zijn gevuld.

Zie verder tgoLv01-bericht bij [BAG bevraging](/docs/probleemoplossing/programmablokken/bag_bevraging.md).

