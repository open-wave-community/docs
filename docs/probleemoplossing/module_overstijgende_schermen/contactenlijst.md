# ContactenLijst bij zaak

Voor de algemene lijst met adressen (adresboek op openingsportaal) zie: [Lijst alle contactadressen](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_adresboek/lijst_alle_contactadressen.md).

De schermidentifier is:

- indien de inlogger lid is van een rechtengroep die het recht _is groep voor publiek_ (tbrechten.dlaispubliekgroep) uitgevinkt heeft staan: MDLC_geefContactenOverzicht.xml
- anders (_is groep voor publiek_ staat aangevinkt) dan MDLC_geefContactenOverzicht_publiek.xml.

Dit scherm kan worden aangeroepen vanuit alle zaakportalen en het inrichtingsportaal (tegel _Contactadressen_) en toont de contactadressen die verbonden zijn aan de zaak/inrichting met hun rol daarin.
De basis van dit scherm is de view indien:

- milieu/gebruik: vwfrmmilvergcontacten
- horeca: vwfrmhorecacontacten
- bouw/sloop: vwfrmbouwcontacten
- APV/overig: vwfrmovcontacten
- omgeving: vwfrmomgcontacten
- handhaving: vwfrmhandhcontacten
- inrichting: vwfrmmilcontacten
- bezwaar/beroep: vwfrmbezwaarcontacten

## Probleem

Het scherm geeft een foutmelding: er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/instellen_inrichten/schermdefinitie/README.md)) die niet valide is.

## Rechten

Voor het tonen van de lijst vanuit een portaal moet de inlogger lid zijn van een rechtengroep die voor de betreffende module of inrichting het kijkrecht heeft op de rollen waarmee een contactadres wordt verbonden met een zaak. Dit zijn rechten die gaan over het mogen zien, maken verwijderen van de **koppelingen** tussen een zaak en een contactadres (de rollen). De rechten om een contactadres zelf te wijzigen of te maken, verwijderen staan bij de hoofrechtengroep.

### Compartimentsrechten

Indien de contactenlijst wordt aangeroepen vanuit de deelzaak bezwaar/beroep dan is het compartimentsrecht OK wanneer:

- de inlogger lid is van een compartiment en het betreffende compartiment het zaaktype van de bovenliggende zaak bevat en de gemeente waar die zaak speelt, waarbij de eigenschap inclusief bezwaar/beroep is aangevinkt
- de inlogger GEEN lid is van een compartiment, dan:
  - mag de combinatie van het zaaktype van de bovenliggende zaak en de gemeente waar die zaak speelt in geen enkel compartiment voorkomen
  - OF, als dat wel het geval is, dan moet de eigenschap _inclusief bezwaar/beroep_ NIET aangevinkt staan.

Indien de contactenlijst wordt aangeroepen vanuit een hoofdzaak dan is het compartimentsrecht OK wanneer:

- de inlogger lid is van een compartiment en het betreffende compartiment het zaaktype van de hoofdzaak bevat en de gemeente waar die zaak speelt
- de inlogger GEEN lid is van een compartiment, dan
  - mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar die zaak speelt in geen enkel compartiment voorkomen
  - OF - als dat wel het geval is - dan moet de eigenschap _inclusief inspecties_ NIET aangevinkt staan.

### Triggers

In het scherm: dubbel klikken op een regel opent het [Contactadres](/probleemoplossing/module_overstijgende_schermen/contact_adres.md)-detailscherm. Altijd enabled.

- knop linksonder **Nieuw contact**:
  - de knop is zichtbaar indien:
    - de inlogger lid is van een rechtengroep die insert rechten heeft op _Koppelingen zaak - contactadres op rol_ (voor de betreffende module). In deze wizard is vervolgens optie _Nieuw contact definiëren_ alleen zichtbar indien ook het hoofdrecht _contactadressen nieuw_ (tbrechten.dldcadins) aangevinkt is
    - en compartimentsrecht is OK.
  - de knop is enabled indien de bovenliggende zaak niet is geblokkeerd.
- knop linksonder **Verwijderen contact** (eigenlijk: verwijderen contactrol, want het contactadres zelf wordt niet verwijderd. Alleen de koppeling.):
  - de knop is zichtbaar:
    - indien de inlogger lid is van een rechtengroep die verwijderrechten heeft op _Koppelingen zaak - contactadres op rol_
    - en compartimentsrecht is OK.
  - de knop is enabled indien de bovenliggende zaak niet is geblokkeerd.
- knop linksonder **Kopieer contact**:
  - de knop is zichtbaar indien:
    - de inlogger lid is van een rechtengroep die insert rechten heeft op _Koppelingen zaak - contactadres op rol_ (voor de betreffende module)
    - en die rechtengroep moet ook het hoofdrecht _contactadressen nieuw_ (tbrechten.dldcadins) hebben
    - en compartimentsrecht is OK.
  - de knop is enabled indien de bovenliggende zaak niet is geblokkeerd.
- knop linksonder **Wijzig contactrol**:
  - de knop is zichtbaar indien:
    - de inlogger lid is van een rechtengroep die insert rechten heeft op _Koppelingen zaak - contactadres op rol_ (voor de betreffende module)
    - en compartimentsrecht is OK
    - en het gaat om contacten bij een omgevingszaak of inrichting. Dus alleen bij module = W of V.
  - de knop is enabled indien de bovenliggende zaak niet is geblokkeerd.
- knop linksonder **Inrichtingscontact toevoegen aan zaak**:
  - de knop is zichtbaar indien:
    - de inlogger lid is van een rechtengroep die insert rechten heeft op _Koppelingen zaak - contactadres op rol_ (voor de betreffende module)
    - en compartimentsrecht is OK
    - en het gaat om contacten bij een zaak met een gekoppelde inrichting (bij inrichtingen zelf dus nooit zichtbaar).
  - de knop is enabled indien de bovenliggende zaak niet is geblokkeerd.
- knop in menu opties rechtsboven: **Creëer document**:
  - de knop is zichtbaar indien:
    - de inlogger lid is van een rechtengroep die upload en creëer rechten heeft voor documenten voor de betreffende module
    - en compartimentsrecht is OK.
  - de knop is enabled indien de bovenliggende zaak niet is geblokkeerd.
