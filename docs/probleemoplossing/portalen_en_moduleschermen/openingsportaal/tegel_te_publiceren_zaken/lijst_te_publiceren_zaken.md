# Lijst te publiceren zaken

Schermidentifiers:

  * mdlc_getvwfrmzakentepublicerenlist.xml
  * mddc_getvwfrmzakentepublicerendetail.xml

Binnen het detailscherm:

  * MDLC_getVwFrmTePublicerenDetailsList.xml 

Zie ook lemma: [Drop](/docs/instellen_inrichten/drop.md).

## Welke gegevens worden getoond in het lijstscherm

De rijen uit de view vwfrmzakentepubliceren dat zijn (één rij per zaak):

  * omgevingszaken waarvan eerdere publicaties mislukt zijn (tbdroppublicaties.dverror gevuld)
  * en/of omgevingszaken waarvoor in de beheertabel tbkoppublgemzaak (lijst op detailpagina van zaaktypedefinitie) aangegeven is dat voor de betreffende gemeente een of meer publicatietypes gedefinieerd zijn vanaf een bepaalde datum. Die datum moet kleiner zijn dan de datum in de omgevingszaak die hoort bij het aangevinkte publicatietype. En de combinatie publicatietype/doel mag niet geregistreerd staan als reeds succesvol gepubliceerd bij de zaak (ook tbdroppublicaties: bij succes wordt de kolom *dossiernummer drop* gevuld). De publicatietypes worden getriggerd door: 
    * Aanvraag: ddaanvraagdatum
    * Ontwerp: ddontwerpbesldatum 
    * Besluit: ddbesluitdatum
    * Ingetrokken: ddingetrokken
    * Verlengd: ddverdaagdvanaf (is alleen zichtbaar indien bij het betreffende zaaktype de kolom *Verlengen/Opschorten* via blokken in detail (tbsoortomgverg.dlblokkenopschort is aangevinkt)
    * Opschorten: ddopschortingvanaf (is alleen zichtbaar indien bij het betreffende zaaktype de kolom *Verlengen/Opschorten* via blokken in detail (tbsoortomgverg.dlblokkenopschort is aangevinkt)
  * APV/Overige zaken waarvan eerdere publicaties mislukt zijn (tbdroppublicaties.dverror gevuld)
  * en/of APV/Overige zaken waarvoor in de beheertabel tbkoppublgemzaak (lijst op detailpagina van zaaktypedefinitie) aangegeven is dat voor de betreffende gemeente een of meer publicatietypes gedefinieerd zijn vanaf een bepaalde datum. En de combinatie publicatietype/doel mag niet geregistreerd staan als reeds succesvol gepubliceerd bij de zaak (tbdropublicaties). De publicatietypes worden getriggerd door: 
    * Aanvraag: ddaanvraagdatum
    * Besluit: ddbesluitdatum
    * Ingetrokken: ddingetrokken
  * Horecazaken waarvan eerdere publicaties mislukt zijn (tbdroppublicaties.dverror gevuld)
  * en/of Horecazaken waarvoor in de beheertabel tbkoppublgemzaak (lijst op detailpagina van zaaktypedefinitie) aangegeven is dat voor de betreffende gemeente een of meer publicatietypes gedefinieerd zijn vanaf een bepaalde datum. En de combinatie publicatietype/doel mag niet geregistreerd staan als reeds succesvol gepubliceerd bij de zaak (tbdropublicaties). De publicatietypes worden getriggerd door: 
    * Aanvraag: ddaanvraagdatum
    * Besluit: ddbesluitdatum
    * Ingetrokken: ddingetrokken
  * Milieugebruikzaken waarvan eerdere publicaties mislukt zijn (tbdroppublicaties.dverror gevuld)
  * en/of Milieugebruikzaken waarvoor in de beheertabel tbkoppublgemzaak (lijst op detailpagina van zaaktypedefinitie) aangegeven is dat voor de betreffende gemeente een of meer publicatietypes gedefinieerd zijn vanaf een bepaalde datum. En de combinatie publicatietype/doel mag niet geregistreerd staan als reeds succesvol gepubliceerd bij de zaak (tbdropublicaties). De publicatietypes worden getriggerd door: 
    * Aanvraag: ddaanvraagdatum
    * Besluit: ddbesluitdatum
    * Ingetrokken: ddingetrokken

Boven op deze where clausules van de view zijn de volgende extra restricties van kracht:

  *  indien de inlogger lid is van een compartiment, dan worden alleen die zaken getoond waarvan de combinatie zaaktype/gemeente voorkomt in het betreffende compartiment (en dus als de inlogger GEEN lid is van een compartiment, dan gaat het om de zaken waarvan de combinatie zaaktype/gemeente in geen enkel compartiment voorkomt).

## Rechten

De lijst kan opgevraagd worden door alle medewerkers met publicatie-recht (beheerportaal- Nieuw: medewerkersdetailscherm kolom *mag drop publiceren*).

## Problemen

  * De lijst is leeg of geeft maar een gedeelte van de te publiceren zaken:
    * zie de criteria hierboven.
  * De lijst geeft een foutmelding:
    * er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

  * pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling *Getal1* van tbinitialisatie *Sectie: Paging* en *Item: pagesize* (defaultwaarde = 100)
  * klikken op regel opent altijd het detailscherm van de zaak met de kolommen die gebruikt kunnen worden worden voor de opmaak van het publicatiebericht. Onderaan dit detailscherm staat een lijstje met de klaargezette publicaties bij de bovenliggende zaak (dus per publicatietype en doel)
  * versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt)
  * de wizardknop *publiceer* linksonderonder. Deze knop opent de wizard *publiceerZaken*
  * de knop *ga naar zaakportaal* linksonder. 

