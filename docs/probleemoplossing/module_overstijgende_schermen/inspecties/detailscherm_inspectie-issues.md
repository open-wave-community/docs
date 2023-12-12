# Detailscherm Inspectie overtreding

De schermidentifier is: MDDC_geefOnrechtmatigheidDetail.xml.

Dit scherm kan worden aangeroepen vanuit de Lijst Inspectie-overtreding bij een zaak/traject.

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft op de [inspecties](/docs/probleemoplossing/module_overstijgende_schermen/inspecties/lijst_inspectiebezoeken.md) bij betreffende hoofdzaak.

## Muteren

De kolommen kunnen gemuteerd worden indien:

- de inlogger wijzigrechten heeft op de inspecties bij betreffende hoofdzaak/inrichting (bijvoorbeeld wijzigrechten op inspecties bij omgeving)
- en die bovenliggende hoofdzaak niet is geblokkeerd
- en de editschuif aan staat
- en - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de hoofdzaak bevatten en de gemeente waar de omgevingszaak speelt en dan moet de eigenschap _inclusief inspecties_ bij dat zaaktype in het compartiment zijn aangevinkt
- en - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar de hoofdzaak speelt in geen enkel compartiment voorkomen tenzij de eigenschap _inclusief inspecties_ bij dat zaaktype in het compartiment NIET is aangevinkt.

De **dropdownlijst van de inspecteur** kijkt naar de kolom _Tekst_ van de instelling _Sectie: InspectieMilieu_ en _Item: Rechtengroepen_. Daar kunnen - gescheiden door puntkomma's' - de dnkeys van de rechtengroepen (tbrechten) opgesomd worden die bedoeld zijn voor de inspecteurs. Bijvoorbeeld 1.13;210;340;
Is dit het geval dan laat de dropdownlijst alleen medewerkers zien die lid zijn van deze functionele rechtengroepen. Is de instelling leeg dan bestaan er geen restricties op functionele rechtengroepen.

In alle gevallen geldt verder het volgende:

- de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
- en de medewerker moet in dienst zijn
- en het vakje _interne medewerker_ moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap: _overrule compartiment_ aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

### Wettelijke basis en overtreding

Zowel in het detailscherm van Handhavingen (tbhandhavingen) als in de Overtredingen bij inspecties (tbinsponrechtm) moet eerst de wettelijke basis gekozen worden en met dat resultaat vervolgens een overtreding die aan de wettelijke basis is verbonden. De set van overtredingen wordt op deze manier beperkt. Geldt ook voor de insertwizard bij overtredingen. Indien de waarde van een wettelijke basis wordt veranderd heeft dat automatisch tot gevolg dat de overtreding op null gezet wordt (totdat deze weer via de dropdown wordt gevuld).

### Uitzondering blokkering

Als de bovenliggende hoofdzaak is geblokkeerd kunnen er toch overtredingen worden gemuteerd indien de instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ aangevinkt is. Dat geldt dan weer niet voor inspecties gekoppeld aan inrichtingen.
