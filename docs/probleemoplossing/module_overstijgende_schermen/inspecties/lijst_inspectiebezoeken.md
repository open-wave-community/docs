# Lijst Inspectiebezoeken

De schermidentifier is: MDLC_geefInspBezoekOverzicht.xml.

De lijst kan worden aangeroepen vanuit het zaakportaal van Omgeving, Handhavingen, Bouw/sloop, APV/Overig en Objectregistratie/Inrichtingen. In dat geval worden alle bezoeken bij de hoofdzaak getoond ongeacht het inspectietraject. De bezoeken zijn dan onderverdeeld in openstaande en afgeronde bezoeken.

De lijst kan ook worden aangeroepen vanuit een specifiek inspectietraject. In dat laatste geval zijn alleen de bezoeken bij dat traject te zien.

## Error

Het scherm geeft een foutmelding:

- er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
- de inlogger moet kijkrechten hebben op de inspecties bij de betreffende hoofdzaak of inrichting.

## Muteerrechten

Een kolom in de inspectiebezoekenlijst kan worden gemuteerd indien:

- de inlogger lid is van een rechtengroep die wijzigrechten heeft op de inspecties van de betrokken module
- en de bovenliggende zaak niet is geblokkeerd (zie onder aan pagina voor uitzondering)
- en in de schermkolomdefinitie (beheer) is de eigenschap _lijst automatisch in editmode_ aangevinkt
- en de kolom heeft de tag `<edit>` op true staan in de schermkolomdefinitie
- en - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de bovenliggende zaak bevatten en de gemeente waar die zaak speelt, waarbij de eigenschap _inclusief inspecties_ is aangevinkt
- en - indien de inlogger GEEN lid is van een compartiment,
  - dan mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt in geen enkel compartiment voorkomen.
  - OF, als dat wel het geval is, dan moet de eigenschap _inclusief inspecties_ NIET aangevinkt staan
- en de editschuif aan staat.

## Triggers

**In het scherm**: dubbel klikken op een regel opent het detailscherm van een inspectiebezoek. Altijd enabled.

Triggers in **scherm linksonder**

- Insertknop:
  - Zichtbaar indien:
    - inlogger insert-rechten heeft op de inspecties bij betreffende hoofdzaak of inrichting
    - en de lijst
      _wordt aangeroepen vanuit detailscherm inspectietraject
      _ OF wordt aangeroepen vanuit tegel _Openstaande bezoeken_ op zaak c.q. inrichtingsportaal terwijl er maar één inspectietraject bestaat
    - en compartimentrecht is OK.
  - Enabled indien de bovenliggende zaak/inrichting niet is geblokkeerd.
- Deleteknop:
  - Zichtbaar indien:
    - inlogger verwijderrechten heeft op de inspecties bij betreffende hoofdzaak/inrichting
    - en de lijst
      _wordt aangeroepen vanuit detailscherm inspectietraject
      _ OF wordt aangeroepen vanuit tegel _Openstaande bezoeken_ op zaak c.q. inrichtingsportaal terwijl er maar één inspectietraject bestaat
    - en compartimentrecht is OK.
  - Enabled indien de bovenliggende zaak/inrichting niet is geblokkeerd.

Uitzondering blokkering:
Als de bovenliggende hoofdzaak is geblokkeerd kunnen er toch bezoeken worden toegevoegd/verwijderd indien de instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ aangevinkt is.
