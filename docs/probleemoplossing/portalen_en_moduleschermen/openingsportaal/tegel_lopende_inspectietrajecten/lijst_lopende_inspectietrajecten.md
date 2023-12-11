# Lijst Lopende Inspectietrajecten

Schermidentifier: MDLC_geefOpenInspectieTrajectenLijst.xml.

## Welke gegevens worden getoond

De rijen uit de view vwfrmopeninsptrajecten, dat zijn inspectietrajecten:

  *   waarbij de afgeronde datum (ddcontrole) leeg is of groter dan vandaag
  *   EN de bovenliggende zaak/inrichting NIET is geblokkeerd. Indien echter de instelling *Sectie: InspectieMilieu en Item: Nietblokkerenmethoofdzaak* aangevinkt is, dan mag de bovenliggende zaak WEL geblokkeerd zijn 
  *   EN de startdatum (ddrappel) is niet ouder dan het aantal dagen dat is ingesteld in *Getal2* van de instelling *Sectie: Inspecties en Item: DagenTerug_OpenInspectieLijst* (default 730). 

Boven op deze whereclausules van de view is de volgende extra restrictie van kracht:

  * Indien de de kolom *alleen gemeentes* (zie beheertegel *Medewerkers*) bij de kaart van de inlogger gevuld is, dan worden alleen die inspectietrajecten getoond waarvan de id van de locatie-gemeente (bedoeld wordt de locatie waaraan de bovenliggende zaak of inrichting is verbonden) voorkomt in die kolom *alleen gemeentes* 
  * Compartimentsrestricties. Zie hiertoe de uitleg bij de tegel waarvan deze lijst wordt aangeroepen.

## Problemen

  * De lijst is leeg of geeft maar een gedeelte van de lopende inspectietrajecten:
    * zie de criteria hierboven.
  * De lijst geeft een foutmelding:
    * Er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

  * pagingknoppen rechtsboven. aanwezig indien aantal rijen groter dan de instelling *Getal1* van tbinitialisatie *Sectie: paging* en *Item: pagesize* (defaultwaarde = 100)
  * klikken op regel opent altijd zaakportaal van bovenliggende zaak of inrichting
  * versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).

## Betekenis kleurenballetjes

  * Eerste kolom (dvinspgevaar):
    * rood indien de startdatum < = vandaag EN er is nog geen inspectiebezoek gepland
    * oranje indien startdatum < = vandaag EN er is tenminste één bezoek gepland dat nog niet is afgehandeld 
    * groen indien startdatum < = vandaag EN de geplande bezoeken zijn afgehandeld
    * wit in alle andere gevallen.
  * OLO-kolom (dvologevaar):
    * leeg indien het inspectietraject NIET gekoppeld is aan een omgevingszaak 
    * leeg indien wel gekoppeld aan omgevingszaak, maar een zonder OLO-bijlagen
    * rood betekent wel gekoppeld aan omgevingszaak met OLO-bijlagen waarvan er tenminste één bijlage is die nog niet is afgevinkt 
    * groen betekent wel gekoppeld aan omgevingszaak met OLO-bijlagen die alle zijn afgevinkt.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde iconen, zie hiervoor [Sectie OWB](/docs/instellen_inrichten/configuratie/sectie_owb.md).

