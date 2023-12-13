# Lijst Geplande Inspectiebezoeken

Schermidentifier: MDLC_geefOpenInspectieBezoekenLijst.xml

## Welke gegevens worden getoond

De rijen uit de view vwfrmomgorkestrator_insp, dat zijn inspectiebezoeken:

- waarbij de geplande bezoekdatum (ddgepland) jonger is dan _Getal2_ van de instelling _Sectie: Inspecties en Item: DagenTerug_OpenBezoekenLijst_ dagen geleden (default 365)
- en de bovenliggende inspectietraject afgehandeld datum (ddcontrole) leeg is of groter dan vandaag
- en de afgehandeld datum van het bezoek nog leeg is
- en de bovenliggende zaak/inrichting NIET is geblokkeerd. Indien echter de instelling _Sectie: InspectieMilieu en Item: Nietblokkerenmethoofdzaak_ aangevinkt is, dan mag de bovenliggende zaak WEL geblokkeerd zijn.

Boven op deze where clausules van de view is de volgende extra restrictie van kracht:

- indien de de kolom _alleen gemeentes_ (zie beheertegel _Medewerkers_) bij de kaart van de inlogger gevuld is, dan worden alleen die inspectiebezoeken getoond waarvan de id van de locatie-gemeente (bedoeld wordt de locatie waaraan de bovenliggende zaak of inrichting is verbonden) voorkomt in die kolom _alleen gemeentes_
- indien de inlogger lid is van een [compartiment](../../../../instellen_inrichten/compartimenten.md) ziet hij/zij alleen bezoeken van zaken die gelokaliseerd zijn in de aan het compartiment toegekende gemeentes.

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de geplande inspectiebezoeken:
  - zie de criteria hierboven.
- De lijst geeft een foutmelding:
  - Er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ van tbinitialisatie _Sectie: paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd zaakportaal van bovenliggende zaak of inrichting
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).

## Betekenis kleurenballetjes

- Eerste kolom (dvbezoekgevaar):
  - rood indien de geplande bezoekdatum < = vandaag
  - wit in alle andere gevallen.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde iconen, zie hiervoor [Sectie OWB](../../../../instellen_inrichten/configuratie/sectie_owb.md).
