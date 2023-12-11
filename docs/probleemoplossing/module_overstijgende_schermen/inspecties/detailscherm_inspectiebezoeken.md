# Detailscherm Inspectie bezoek

De schermidentifier is: MDDC_geefInspBezoekDetail.xml.

Dit scherm kan worden aangeroepen vanuit de Lijst Inspectiebezoeken bij een zaak/traject.

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft op de inspecties bij betreffende hoofdzaak.

## Muteren

De kolommen kunnen gemuteerd worden indien:

- de inlogger wijzigrechten heeft op de inspecties bij betreffende hoofdzaak/inrichting (bijvoorbeeld wijzigrechten op inspecties bij omgeving)
- en die bovenliggende hoofdzaak niet is geblokkeerd
- en de editschuif aan staat
- en - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de hoofdzaak bevatten en de gemeente waar de hoofdzaak speelt en dan moet de eigenschap _inclusief inspecties_ bij dat zaaktype in het compartiment zijn aangevinkt
- en - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar de hoofdzaak speelt in geen enkel compartiment voorkomen tenzij de eigenschap _inclusief inspecties_ bij dat zaaktype in het compartiment NIET is aangevinkt. |

De **dropdownlijst van de inspecteur** kijkt naar de kolom _Tekst_ van de instelling _Sectie: InspectieMilieu_ en _Item: Rechtengroepen_. Daar kunnen - gescheiden door puntkomma's' - de dnkeys van de rechtengroepen (tbrechten) opgesomd worden die bedoeld zijn voor de inspecteurs. Bijvoorbeeld 1.13;210;340;
Is dit het geval dan laat de dropdownlijst alleen medewerkers zien die lid zijn van deze functionele rechtengroepen. Is de instelling leeg dan bestaan er geen restricties op functionele rechtengroepen.

In alle gevallen geldt verder het volgende:

- de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
- en de medewerker moet in dienst zijn
- en het vakje _interne medewerker_ moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap: _overrule compartiment_ aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

De **dropdownlijst van soort bezoek** kijkt eerst of er gekoppelde inspectie soortbezoeken hangen aan de aanleiding van het inspectietraject waar het bezoek onder valt. Zo ja dan is er alleen te kiezen uit de in beheer aangegeven inspectie soortbezoeken voor de inspectietrajectsoort. Is dit niet het geval dan worden alle inspectie soortbezoeken getoond uit de codetabel in beheer zonder vervaldatum en met module corresponderend met module van de zaak waaronder het inspectiebezoek hangt.

Uitzondering blokkering: Als de bovenliggende hoofdzaak is geblokkeerd kunnen er toch bezoeken worden gemuteerd indien de instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ aangevinkt is. Dat geldt dan weer niet voor inspecties gekoppeld aan inrichtingen.

## Triggers rechtsboven

Welke triggers **rechtsboven** bij menu opties:

- Creëer document (zie verder bij [Creëer document](/docs/probleemoplossing/programmablokken/creeer_document.md)):
  - Zichtbaar indien de inlogger lid is van een rechtengroep die bij hoofdzaak/inrichting het recht creëren van documenten heeft en Compartimentsrecht is OK.
  - De knop is disabled indien de bovenliggende zaak geblokkeerd is.

## Triggers linksonder

Welke triggers in scherm **linksonder**

- Creëer document (zie verder bij [Creëer document](/docs/probleemoplossing/programmablokken/creeer_document.md)):
  - Zichtbaar indien de inlogger lid is van een rechtengroep die bij hoofdzaak/inrichting het recht creëren van documenten heeft en Compartimentsrecht is OK.
  - De knop is disabled indien de bovenliggende zaak geblokkeerd is.
- Creëer email (zie verder bij [Creëer email](/docs/probleemoplossing/programmablokken/creeer_email.md)):
  - Zichtbaar en enabled indien de inlogger lid is van een rechtengroep die documenten mag creëren.
  - en de omgevingszaak is niet geblokkeerd.
  - Klikken op het email-icoon start de wizard _maak email_. Er kan gekozen worden uit mailsjablonen mits deze gedefinieerd zijn aan de beheerkant onder de tegel _Emailsjablonen_. Voor meer informatie over het definiëren van mailsjablonen zie [Emailsjablonen](/docs/instellen_inrichten/emailsjablonen.md).

Uitzondering blokkering: Als de bovenliggende hoofdzaak is geblokkeerd kunnen er toch bezoeken worden gemuteerd en documenten worden gecreëerd indien de instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ aangevinkt is.
