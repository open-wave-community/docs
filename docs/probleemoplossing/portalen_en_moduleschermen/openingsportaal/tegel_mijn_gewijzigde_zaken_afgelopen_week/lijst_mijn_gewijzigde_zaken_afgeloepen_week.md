# Lijst Mijn gewijzigde zaken afgelopen week

Schermidentifier: MDLC_getGewijzigdeZakenList.xml.

Zie ook [Tegel Mijn Gewijzigde Zaken Afgelopen Week](/docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_gewijzigde_zaken_afgelopen_week.md)

## Welke gegevens worden getoond

De rijen uit de view **vwfrmgewijzigdezaken**, dat zijn zaken waarvoor geldt dat in de afgelopen week ofwel:

  * een processtap is gewijzigd (tbtermijnbewstappen.ddafgehandeld)
  * OF de registratiedatum van een document is gewijzigd (tbcorrespondentie.ddgewijzigd)
  * OF een advies is binnengekomen (tbadviezen.dddateringadvies of tbadviezen.ddadviesdatum)
  * OF een advies is vervallen (tbadviezen.ddvervallen 
  * OF een rappeldatum van een advies valt in die week terwijl er geen advies is uitgebracht.

Boven op deze definitie van bovenstaande view is de volgende extra restricties van kracht:

Alleen die gewijzigde zaken worden getoond waarvoor de inlogger:

  * ofwel de dossierbehandelaar is, 
  * ofwel de accountmanager 
  * ofwel de juridisch verantwoordelijke (deze laatste optie is alleen van toepassing bij handhavingszaken)
  * ofwel de zaak volgt. Dit houdt in dat de inlogger heeft aangegeven bij de zaak deze te willen volgen

daarbij geldt dan die inlogger niet dezelfde mag zijn als degene die een document geregistreerd heeft of een processtap heeft gewijzigd.

## Problemen

  * De lijst is leeg of geeft maar een gedeelte van de gewijzigde zaken:
    * zie de criteria hierboven.
  * De lijst geeft een foutmelding:
    * er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

  * pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling *Getal1* van tbinitialisatie *Sectie: paging* en *Item: pagesize* (defaultwaarde = 100)
  * klikken op regel opent altijd zaakportaal van bovenliggende zaak
  * versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt)
  * Excel knop om de lijst naar Excel te transporteren. Knop is zichtbaar indien zo ingesteld bij de beheerportaal-Nieuw tegel *Schermkolomdefinities* voor het scherm met de identifier MDLC_getGewijzigdeZakenList.xml.

