# Lijst Inspectie-overtredingen

De schermidentifier is: MDLC_geefOnrechtmatighedenOverzicht.xml.

De lijst kan worden aangeroepen vanuit het zaakportaal van Omgeving, Handhavingen, APV/Overig, Bouw/sloop en Objectregistratie/Inrichtingen. In dat geval worden alle overtredingen bij de hoofdzaak getoond ongeacht het inspectietraject. De overtredingen zijn dan onderverdeeld in openstaande en afgeronde overtredingen.

De lijst kan ook worden aangeroepen vanuit een specifiek inspectietraject. In dat laatste geval zijn alleen de overtredingen bij dat traject te zien.

## Error

Het scherm geeft een foutmelding:

- er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
- de inlogger moet kijkrechten hebben op de inspecties bij de betreffende hoofdzaak of inrichting.

## Muteerrechten

Een kolom in de inspectie-overtredingenlijst kan worden gemuteerd indien:

- de inlogger lid is van een rechtengroep die wijzigrechten heeft op de inspecties van de betrokken module
- en de bovenliggende zaak niet is geblokkeerd (zie onder aan pagina voor uitzondering)
- en in de schermkolomdefinitie (beheer) is de eigenschap _lijst automatisch in editmode_ aangevinkt
- en de kolom heeft de tag <edit> op true staan in de schermkolomdefinitie
- en - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de bovenliggende zaak bevatten en de gemeente waar die zaak speelt, waarbij de eigenschap _inclusief inspecties_ is aangevinkt
- en - indien de inlogger GEEN lid is van een compartiment,
  - dan mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt in geen enkel compartiment voorkomen
  - OF, als dat wel het geval is, dan moet de eigenschap _inclusief inspecties_ NIET aangevinkt staan
- en de editschuif aan staat.

### Bijzondere kolommen

De kolom **Opmerk.?** geeft aan of het veld _Interne Opmerking_ gevuld is of niet voor de overtreding. Het programma wijzigt zelf de waarde van het achterliggende veld: als de interne opmerking gevuld is of wordt, dan zal het veld aangevinkt zijn. Is de interne opmerking leeg/ wordt deze leeggemaakt door de gebruiker dan wordt het veld uitgevinkt.

#### Automatisch synchroniseren Digitale checklisten

Zie de voorwaarde hieronder bij de knop synchroniseren.

Als _Getal1_ van de instelling _Sectie: KoppelingINSPTOETS en Item: SynchroniseerOnrechtm_ de waarde 1 heeft en de instelling is aangevinkt, dan wordt het synchroniseren automatisch gedaan indien het detailscherm van het bovenliggende inspectietraject opnieuw wordt uitgeschreven: dus ook bij het openen.

### Triggers

**In het scherm**: dubbel klikken op een regel opent het detailscherm van een inspectie-overtreding. Altijd enabled.

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
    - inlogger verwijderrechten heeft op de inspecties bij betreffende hoofdzaak/inrichting en compartimentrecht is OK
    - en de lijst
      _wordt aangeroepen vanuit detailscherm inspectietraject
      _ OF wordt aangeroepen vanuit tegel _Openstaande bezoeken_ op zaak c.q. inrichtingsportaal terwijl er maar één inspectietraject bestaat.
  - Enabled indien de bovenliggende zaak/inrichting niet is geblokkeerd.
- Synchroniseer met Digitale checklisten:
  - Zichtbaar en enabled indien:
    - de instelling _Sectie: KoppelingINSPTOETS_ en _Item: SynchroniseerOnrechtm_ aangevinkt is
    - en de bovenliggende zaak/inrichting niet is geblokkeerd
    - en in tbinspecties.ddextchkldossierid of dvextchkdossier2id of dvextchkdossier3id is gevuld
    - en de instelling _Sectie: KoppelingINSPTOETS_, _Item: Methode_ en _Tekst: digitalechecklisten_ aangevinkt is
    - en bij _Sectie: KoppelingINSPTOETS_ en _Item: Ontvangstadres_answers_ de kolom _Tekst_ is gevuld
    - en bij _Sectie: KoppelingINSPTOETS_ en _Item: Ontvangstadres_users_ de kolom _Tekst_ is gevuld
    - en compartimentrecht is OK.

Uitzondering blokkering:
Als de bovenliggende hoofdzaak is geblokkeerd kunnen er toch overtredingen worden toegevoegd/verwijderd indien de instelling _Sectie: InspectieMilieu_ en _Item: NietBlokkerenMetHoofdzaak_ aangevinkt is.
