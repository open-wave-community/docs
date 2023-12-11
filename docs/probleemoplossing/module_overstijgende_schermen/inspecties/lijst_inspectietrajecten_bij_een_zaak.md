# Lijst Inspecties bij een Zaak

De schermidentifier is: MDLC_geefInspTrajectOverzicht.xml.

Dit scherm kan worden aangeroepen vanuit het zaakportaal van Omgeving, Handhavingen en APV/Overig, Bouw/sloop, Horeca en Objectregistratie/Inrichtingen.

## Error

Het scherm geeft een foutmelding:

* er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
* de inlogger moet kijkrechten hebben op de inspecties bij de betreffende hoofdzaak of inrichting.

## Muteerrechten

Een kolom in de inspectietrajectenlijst kan worden gemuteerd indien:

* de inlogger lid is van een rechtengroep die wijzigrechten heeft op de inspecties van de betrokken module
* EN de bovenliggende zaak niet is geblokkeerd (zie onder aan pagina voor uitzondering)
* EN in de schermkolomdefinitie (beheer) is de eigenschap *lijst automatisch in editmode* aangevinkt  
* EN de kolom heeft de tag <edit> op true staan in de schermkolomdefinitie
* EN - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de bovenliggende zaak bevatten en de gemeente waar die zaak speelt, waarbij de eigenschap *inclusief inspecties* is aangevinkt
* EN - indien de inlogger GEEN lid is van een compartiment,
  * dan mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt in geen enkel compartiment voorkomen
  * OF, als dat wel het geval is, dan moet de eigenschap *inclusief inspecties* NIET aangevinkt staan
* EN de editschuif aan staat.

## Triggers

In het scherm: dubbel klikken op een regel opent het detailscherm van een inspectietraject. Altijd enabled.

Welke triggers in **scherm linksonder**

* Insertknop:
  * Zichtbaar indien:
    * inlogger insert-rechten heeft op de inspecties bij betreffende hoofdzaak of inrichting
    * EN de lijst wordt aangeroepen vanuit de tegel *Openstaande trajecten*
    * EN compartimentsrecht OK.
  * Enabled indien de bovenliggende zaak/inrichting niet is geblokkeerd.
* Deleteknop:
  * Zichtbaar indien inlogger verwijderrechten heeft op de inspecties bij betreffende hoofdzaak/inrichting EN compartimentsrecht OK.
  * Enabled indien de bovenliggende zaak/inrichting niet is geblokkeerd.

Uitzondering blokkering:
Als de bovenliggende hoofdzaak is geblokkeerd kunnen er toch trajecten worden toegevoegd/verwijderd indien de instelling *Sectie: InspectieMilieu* en *Item: NietBlokkerenMetHoofdzaak* aangevinkt is. het programma kijkt in dat geval naar het gevuld zijn van de einddatum (tbinsecties.ddcontrole) van het inspectietraject.
