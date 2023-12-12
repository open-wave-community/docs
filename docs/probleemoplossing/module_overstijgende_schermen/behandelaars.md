# Behandelaars

De schermidentifiers voor lijst en detail zijn: MDLC_geefBehandelaarsOverzicht.xml en MDDC_geefBehandelaarDetail.xml.

Dit (lijst) scherm kan worden aangeroepen vanuit alle zaakportalen (tegel _Dossierbehandelaars_):

- De bron van de lijst is de view vwfrminbehbij (op basis van de tabel tbinbehandelingbij) met de behandelaars bij een zaak. Er is altijd maar één actieve behandelaar per zaak (kolom _actief_ is aangevinkt).
- De lijst is zichtbaar indien de inlogger lid is van een rechtengroep die bij de betreffende module (omgeving, milieu/gebruik, bouw/sloop, handhaving, APV/overig) het kijkrecht heeft op _In behandeling Bij_.

### Probleem

Het scherm geeft een foutmelding indien er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie/README.md)) die niet valide is.

### Muteren

De inlogger kan geen rijen verwijderen in deze tabel. Wanneer een dossier overgaat van de ene naar de andere behandelaar dan kan de inlogger een nieuwe regel aanmaken (mits geautoriseerd door insertrecht op _In behandeling Bij_) waarbij automatisch de eigenschap _actief_ aangevinkt wordt op de nieuwe kaart en waarbij de vorige actieve behandelaar uitgevinkt wordt en de _datum tot_ daarbij wordt gevuld met de systeemdatum. Voor de dropdownlijst met **behandelaar** geldt het volgende:

- de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
- en de medewerker moet in dienst zijn
- en het vakje _interne medewerker_ moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap _overrule compartiment_ aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

De kolommen van de detailkaart zijn niet muteerbaar.

### Overrule compartiment

Een nieuwe actieve behandelaar wordt ook toegevoegd aan bovenstaande lijst indien op het detailscherm van de hoofdzaak door een medewerker met de autorisatie _overrule compartiment_ in het blok compartiment (alleen zichtbaar indien er compartimenten zijn gedefinieerd) de zaak wordt overgedragen van het ene naar het andere compartiment, of van een compartiment naar de host (of vice versa). Aan de lijst met behandelaars wordt in dat geval de defaultbehandelaar van de zaak toegevoegd (de defaultbehandelaar van het gekozen compartiment of - indien de host is gekozen - dan de defaultbehandelaar van het zaaktype).

### Trigger

Linksonder de insertknop om een nieuwe actieve behandelaar aan de zaak toe te voegen. Zichtbaar en enabled indien de inlogger insertrecht heeft op _In behandeling Bij_ bij de betreffende module.
