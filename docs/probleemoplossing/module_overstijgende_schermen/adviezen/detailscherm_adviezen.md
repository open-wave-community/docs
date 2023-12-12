# Detailscherm Adviezen

De schermidentifier is: **MDDC_geefAdviesDetail.xml**.

De schermidentifier van het achterliggende welstandsadviesscherm is **MDDC_getVwFrmAdviesWelstandDetail.xml**.

Dit scherm kan worden aangeroepen vanuit de Lijst Adviezen bij een zaak.

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft op de adviezen bij betreffende hoofdzaak.

## Defaultwaarden

- De rappeldatum is een optelling van de aanvraagdatum + hetgeen is ingevoerd in de beheer tabel adviesinstanties bij rappeldagen bij de betrokken adviesinstantie.
- De adviesvrager/behandelaar (degene die verantwoordelijk is dat het uitgezette advies op tijd binnenkomt) is:
  - de default behandelaar die is toegekend in de beheertabel bij de betrokken adviesinstantie:
    - indien deze waarde leeg is kijkt het programma naar de instelling van _Getal1_ bij _Sectie: Adviezen en Item: Adviesverantwoordelijke_
    - indien deze waarde 1 is dan is de default behandelaar/adviesvrager gelijk aan de van de inlogger
    - indien deze waarde 2 is dan is de default behandelaar/adviesvrager gelijk aan de actieve behandelaar (tbinbehandelingbij).
  - Indien bij de insert van een nieuw advies het advies echter direct wordt afgehandeld, dan wordt de adviesvrager/behandelaar gevuld met de inlogger.
- Het behandelend team (dat verantwoordelijk is dat het uitgezette advies op tijd binnenkomt) is het default team dat is toegekend in de beheertabel bij de betrokken adviesinstantie.

## Zichtbaarheid adviesvrager versus team en andere kolommen

Voor de dropdownlijst met **adviesvrager** geldt het volgende:

- de kolom is alleen zichtbaar indien de instelling _Sectie: Adviezen en Item: Voorwiezichtbaar_ is aangevinkt
- de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
- en de medewerker moet in dienst zijn
- en het vakje _interne medewerker_ moet aangevinkt zijn.
- en het vakje _is raadpleger_ mag NIET aangevinkt zijn

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap: _overrule compartiment_ aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

Voor de dropdownlijst met **behandelend team** geldt het volgende:

- de kolom is alleen zichtbaar indien de instelling _Sectie: Adviezen en Item: teamzichtbaar_ is aangevinkt
- het team moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger.

Voor de dropdownlijst met **Gekozen adviseur** geldt het volgende:

- de kolom is alleen zichtbaar indien de instelling _Sectie: Adviezen en Item: KiesAdviseur_ is aangevinkt.

De kolom **Beoordeling door Adviesgever** (tbadviezen.dvadvgeverpositief) is zichtbaar indien de instelling _Sectie: Adviezen en Item: Dvadvgeverposvisible_ wordt aangevinkt. In dat geval wordt de radiobutton kolom _Beoordeling Adviesgever_ zichtbaar naast de bestaande kolom _Beoordeling Adviesaanvrager_ (dladviespositief). In deze nieuwe kolom kan de adviesgever zelf zijn/haar beoordeling geven.

Deze nieuwe kolom heeft GEEN invloed op de lijst recent binnengekomen adviezen. Die blijft bestaan uit de adviezen waarvoor geldt dat de adviesdatum gevuld is en nog niet beoordeeld door de adviesvrager.

## Zichtbaarheid blokken

Het blok **Keten** is alleen zichtbaar indien de instelling _Sectie: Adviezen en Item: Adviesiszaak_ is aangevinkt.

## Muteren

De kolommen kunnen gemuteerd worden indien:

- de inlogger wijzigrechten heeft op de adviezen bij betreffende hoofdzaak
- en in het blok keten is de einddatum/blokkeerdatum NIET gevuld
- en die bovenliggende hoofdzaak niet is geblokkeerd
- en de editschuif aan staat
- en - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de hoofdzaak bevatten en de gemeente waar de hoofdzaak speelt
- en - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar de hoofdzaak speelt in geen enkel compartiment voorkomen.

Een voorbeeld met betrekking tot compartimentsrechten: stel de advieszaak hoort bij een omgevingszaak. Dat geldt dat vvwfrmomgvergunningen.dnkeycompartiment (van de betreffende omgevingszaak) gelijk moet zijn aan tbmedewerkers.dnkeycompartiment (van de inlogger). Dus beide gevuld met null of beide gevuld met eenzelfde waarde.

Hierop bestaan de volgende uitzonderingen:

- De kolom met de radiobutton **Advies Retour** is niet muteerbaar indien:
  - de kolom datering advies (ddadvdatering) leeg is
  - OF de inlogger is een medewerker met de eigenschap _Is ExterneAdviseur_.
- De kolom **dvintzaakcode** (zaak/DMS code) is alleen muteerbaar indien de inlogger het recht _wijzigen externe zaaknummer_ bij adviezen aangevinkt heeft staan voor de betreffende module (beheerportaal-Nieuw, tegel _Functionele rechten_).

Voorts kan het uploaden van een document bij een advies van invloed zijn op de volgende kolommen:

- Aan de kolom **uploadlog** van de betreffende advieszaak wordt een regel met systeemdatum + medewerkerscode en upgeloade filenaam toegevoegd.
- Indien de instelling _Sectie: Adviezen en Item: DateringDoorUpload_ aangevinkt is en de kolom **datering advies** (tbadviezen.ddadvdatering) is leeg dan wordt deze gevuld met de datum van upload (geldt ook voor de kolom **tbadviezen.ddadvadvies**).

Bij het afsluiten van een hoofdzaak waar het advies onder valt kan het programma vragen om openstaande adviezen automatisch van een vervaldatum te voorzien (deze vraag wordt alleen gesteld indien er nog openstaande adviezen zijn en indien de adviezen NIET gedefinieerd zijn als aparte zaken in het externe zaaksysteem).

## Muteren als host-organisatie

Indien het advies valt onder een compartiment, maar het advies is aangevraagd bij de HOST-organisatie (de adviesinstantiecode komt voor in de kolom _Tekst_ van de instelling _Sectie: Adviezen en Item: AdviescodeHostbijCompartiment_ (waarbij de coderingen gescheiden moeten zijn met een puntkomma, dus bijv. EZ;VROM;)), dan geldt dat medewerkers van de Host-organisatie (dus inloggers die niet aan een compartiment gekoppeld zijn) toch de advieskaart kunnen muteren mits:

- de inlogger advies editrechten heeft
- de bovenliggende kaart niet geblokkeerd is
- de instelling _Sectie: Adviezen en Item: DateringDoorUpload_ NIET aangevinkt is.

Indien de instelling _Sectie: Adviezen en Item: DateringDoorUpload_ WEL aangevinkt is, kunnen deze host-inloggers niet muteren, maar wel de uploadknop gebruiken.

## Kolommen dateringadvies en adviesretour

**Adviesretourdatum (tbadviezen.ddadvadvies)** is NIET zichtbaar indien _Getal1_ van de instelling _Sectie: Adviezen en Item: DateringDoorUpload_ de waarde 2 heeft en de instelling NIET aangevinkt is. Als de instelling _Sectie: Adviezen en Item: DateringDoorUpload_ is aangevinkt dan wordt de kolom _Adviesretourdatum_ onder water gevuld met de uploaddatum bij het uploaden van een adviesdocument indien deze kolom nog een lege datum had. Bij het wijzigen van de kolom _Dateringadvies_ kijkt OpenWave of de kolom adviesretourdatum een lege waarde heeft, is dat het geval dan wordt de adviesretourdatum overschreven met de waarde van dateringadvies.

**dateringadvies (tbadviezen.dddateringadvies)** is muteerbaar indien:

- de instelling _Sectie: Adviezen en Item: DateringDoorUpload_ NIET aangevinkt is
- en
  - OF bij de betreffende adviesinstantie de kolom _Autorisatie voor datering advies vereist_ (tbadviesinstanties.dlautdatadvies) NIET is aangevinkt,
  - OF bij de betreffende adviesinstantie de kolom _Autorisatie voor datering advies vereist_ (tbadviesinstanties.dlautdatadvies) WEL aangevinkt is, maar dan moet de inlogger voor de betreffende module het recht _wijzigen datering advies_ (dlcomgadvdatedt) aangevinkt hebben staan.

Als de instelling _Sectie: Adviezen en Item: DateringDoorUpload_ is aangevinkt dan wordt de kolom dddateringadvies onder water gevuld met de uploaddatum bij het uploaden van een adviesdocument indien deze kolom nog een lege datum had.

## Dropdownlijst Adviesvrager/verantwoordelijke behandelaar

Voor de dropdownlijst met **adviesvrager** geldt het volgende:

- de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
- en de medewerker moet in dienst zijn
- en het vakje _interne medewerker_ moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap: _overrule compartiment_ aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

### Extern zaak/DMS nummer

Hieronder komt het begrip externe zaak/DMS nummer voor. Daarmee wordt bedoeld de kolom externe zaak/DMS (dvintzaakcode) die voor kan komen op de advieskaart zelf en/of bij de bovenliggende hoofdzaak.

Het programma kijkt naar de advieskaart zelf indien de instelling _Sectie: Adviezen en Item: AdviesIsZaak_ is aangevinkt. In alle andere gevallen (niet aangevinkt of instelling bestaat niet) dan komt het externe zaak/DMS nummer uit de hoofdzaak van de betreffende module.

## Blok documenten

In het blok documenten kan een gebruiker met advies insert- en delete-rechten documenten koppelen aan het betreffende advies uit de tabel met geregistreerde documenten (tbcorrespondentie) die aan de hoofdzaak verbonden zijn. Vanuit deze lijst kan een gebruiker een document openen en - indien geautoriseerd - wijzigen. Voor het openen of wijzigen van een document gelden dezelfde rechten en voorwaarden als vanuit de geregistreerde documententabel zelf ([Lijst Geregistreerde Documenten bij een zaak](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/lijst_geregistreerde_documenten_bij_zaak.md)).

De koppeltabel is tbkopadviescorresp.

## Triggers

### Triggers in het scherm zelf (achter de kolommen)

#### Stuur mail aan adviesinstantie achter de kolom email verstuurd

Zie verder [Email adviesinstantie](/probleemoplossing/programmablokken/e-mail_adviesinstantie.md).

- Zichtbaar en enabled indien:
  - de inlogger wijzigrechten heeft op de advieskaart voor de betreffende module
  - en dddmsafgehandeld is leeg (alleen zichtbaar indien instelling _Sectie: Adviezen en Item: AdviesIsZaak_ aangevinkt is)
  - en de bovenliggende zaak niet is geblokkeerd (zie hierboven de uitzondering).

#### Maak zaak in zaak/DMS systeem

Achter externe zaak/DMS nummer.

- Zichtbaar en enabled indien:
  - de inlogger muteerrechten heeft op de adviezen
  - en de einddatum zaak/DMS (dddmsafgehandeld) moet leeg zijn
  - en externe zaak/DMS nummer (dvintzaakcode) een **lege waarde** heeft
  - en de bovenliggende zaak niet is geblokkeerd (zie hierboven de uitzondering)
  - en - indien de hoofdzaak NIET onder een compartiment valt - de instelling _Sectie: Koppeling Zaak_ en _Item: Methode_ en _Tekst: StUF-ZAKEN 310_ staat aangevinkt
  - en - indien de hoofdzaak WEL onder een compartiment valt - dan moet de kolom _dmsmethode_ van het betreffende compartiment in het beheerportaal-Nieuw gevuld zijn met _StUF-Zaken 310_
  - en de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan
  - en - indien de hoofdzaak NIET onder een compartiment valt - dan moet de kolom _Tekst_ van de instelling _Sectie: Koppeling ZAAK_ en _Item: ZaaktypeAdvies_ gevuld zijn (en aangevinkt)
  - en - indien de hoofdzaak WEL onder een compartiment valt - dan moet de kolom _zaaktype zaak/dmssysteem (dvdmszaaktypeadvies)_ van het betreffende compartiment in het beheerportaal-Nieuw gevuld zijn
  - en indien het advies een zelfstandige zaak is in externe zaaksysteem: de instelling _Sectie: Adviezen en Item: AdviesIsZaak_ is aangevinkt.

#### Sluit zaak in zaak/DMS systeem

Achter eind/blokkeerdatum van zaak/DMS nummer.

- Zichtbaar en enabled indien:
  - de inlogger muteerrechten heeft op de adviezen
  - en externe zaak/dms nummer (dvintzaakcode) een **gevulde** waarde heeft
  - en de bovenliggende zaak niet is geblokkeerd (zie hierboven de uitzondering)
  - en - indien de hoofdzaak NIET onder een compartiment valt - de instelling _Sectie: Koppeling Zaak_ en _Item: Methode_ en _Tekst: StUF-ZAKEN 310_ staat aangevinkt
  - en - indien de hoofdzaak WEL onder een compartiment valt - dan moet de kolom _dmsmethode_ van het betreffende compartiment in het beheerportaal-Nieuw gevuld zijn met _StUF-Zaken 310_
  - de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan
  - en Het advies een zelfstandige zaak is in externe zaaksysteem: de instelling _Sectie: Adviezen en Item: AdviesIsZaak_ is aangevinkt
  - en het resultaat in de kolom _retouradvies_ (dnkeyretouradvies) is gevuld (en in de beheertabel tbretouradvies is de kolom dvdmsresultaat gevuld).

#### Heropen/ leegmaken blokkeer/einddatum

Achter eind/blokkeerdatum van zaak/DMS nummer indien eind/blokkeerdatum is gevuld.

- Zichtbaar en enabled indien:
  - bovenstaande instellingen
  - en waarbij – indien dddmsafgehandeld is gevuld – het recht op module niveau: _Leegmaken van gevulde afhandel-intrekkingsdatum_ (dlbomgafsedt, dlbhahafsedt, dlbovvafsedt ….) is aangevinkt.

### Triggers rechtsboven in menu opties

#### Toon geregistreerde documenten (bij dit advies)

Zie [Geregistreerde Documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md).

- Zichtbaar en enabled indien:
  - de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt
  - en de gebruiker het recht _Inzien geregistreerde documenten_ bij de betreffende module aangevinkt heeft staat (bijv. tbomgrechten.dlcomgcorregvsb).

#### Creëer document

Zie [Creëer document](/probleemoplossing/programmablokken/creeer_document.md).

- Zichtbaar indien de inlogger lid is van een rechtengroep die bij hoofdzaak het recht creëren van documenten heeft
- De knop is disabled indien:
  - de bovenliggende zaak geblokkeerd is.
  - OF de einddatum zaak/dms (dddmsafgehandeld) gevuld is (alleen zichtbaar indien instelling _Sectie: Adviezen en Item: AdviesIsZaak_ aangevinkt is)
  - OF compartimentsrechten niet ok zijn.

#### Toon uploads bij dit advies

Zie [Upload Lijst](/probleemoplossing/module_overstijgende_schermen/uploads_lijst.md)).

- Zichtbaar en enabled indien:
  - de instelling _Sectie: Documenten_ en _Item: MultipleUpload_ aangevinkt is
  - en de inlogger lid is van een rechtengroep die bij hoofdzaak het recht uploaden van documenten heeft.

#### Creëer email

Zie verder bij [Creëer email](/probleemoplossing/programmablokken/creeer_email.md).

- Zichtbaar en enabled indien:
  - de inlogger lid is van een rechtengroep die bij omgevingszaak het recht _creëren van documenten_ heeft
  - de bovenliggende zaak is niet geblokkeerd.

### Triggers linksonder

#### Toon documenten

Zie [Toon documenten en download](/probleemoplossing/programmablokken/toon_documenten_en_download.md).

- Zichtbaar wanneer:
  - een van onderstaande twee beweringen waar is:
    - de instelling _Sectie: Documenten en Item: Documentregistratie_ is aangevinkt en de gebruiker het recht _Inzien geregistreerde documenten_ bij de betreffende module aangevinkt heeft staat (bijv. tbomgrechten.dlcomgcorregvsb)
    - deze instelling staat niet aan en de gebruiker het recht _Inzien documenten buiten registratie om bij de betreffende module_ aangevinkt heeft staat (bijv. tbomgrechten.dlcomgcorvsb)
  - en - wanneer de bovenliggende hoofdzaak NIET wordt behandeld in een compartiment dan:
    - moet _Sectie: Documenten_ en _Item: OphalenViaFileserver_ OF _Sectie: Documenten_ en _Item: OphalenViaDms_ aangevinkt zijn
    - en - indien OphalenViaDms - dan moet de kolom _Tekst_ bij instelling _Sectie: KoppelingDocnaardms en Item: Methode_ de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben en aangevinkt staan
    - en - wanneer de bovenliggende hoofdzaak WEL wordt behandeld in een compartiment dan:
      _moet de kolom dlfileserver of dldms in het betreffende compartiment (beheerportaal-Nieuw) aangevinkt zijn
      _ en – indien dlDms aangevinkt dan moet de kolom tbcompartiment.dvdmsmethode de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben.
- De knop is disabled indien:
  - geen fileserver en wel DMS
  - en methode is StUF-ZAKEN 310
  - en de externe zaakcode (dvintzaakcode) is leeg. Het programma kijkt naar de externe zaakcode van het advies zelf indien de instelling _Sectie: Adviezen en Item: Adviesiszaak_ aangevinkt is. Zo niet dan kijkt het programma naar de externe zaakcode van de bovenliggende hoofdzaak.

### Creëer email (2)

Zie verder bij [Creëer email](/probleemoplossing/programmablokken/creeer_email.md).

- Zichtbaar en enabled indien de inlogger lid is van een rechtengroep die documenten mag creëren
  - en de bovenliggende zaak is niet geblokkeerd.
- Klikken op het email-icoon start de wizard _Maak email_. Er kan gekozen worden uit mailsjablonen mits deze gedefinieerd zijn aan de beheerkant onder de tegel _Emailsjablonen_. Voor meer informatie over het definiëren van mailsjablonen zie [Emailsjablonen](/instellen_inrichten/emailsjablonen.md).

#### Upload document(en)

Zie [Upload document](/probleemoplossing/programmablokken/upload_document.md).

- Zichtbaar wanneer:
  - de instelling _Sectie: Documenten_ en _Item: MultipleUpload_ aangevinkt is
  - en - wanneer de bovenliggende zaak NIET wordt behandeld in een compartiment dan:
    - moet _Sectie: Documenten_ en _Item: OphalenViaFileserver_ OF _Sectie: Documenten_ en _Item: OphalenViaDms_ aangevinkt zijn
    - en - indien OphalenViaDms - dan moet de kolom _Tekst_ bij instelling _Sectie: KoppelingDocnaardms en Item: Methode_ de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben en aangevinkt staan
  - en - wanneer de bovenliggende zaak WEL wordt behandeld in een compartiment dan:
    - moet de kolom dlfileserver of dldms in het betreffende compartiment (beheerportaal-Nieuw) aangevinkt zijn
    - en – indien dlDms aangevinkt dan moet de kolom tbcompartiment.dvdmsmethode de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben.
- De knop is disabled indien:
  - geen document uploadrechten (beheerportaal-Nieuw, tegel _Functionele rechten_, blok Documenten)
  - OF de zaak geblokkeerd is
  - OF de einddatum zaak/dms (dddmsafgehandeld) is gevuld (alleen zichtbaar indien instelling _Sectie: Adviezen en Item: AdviesIsZaak_ aangevinkt is)
  - OF Compartimentrecht is niet OK
  - OF de inlogger is een _Externe adviseur_ maar heeft de betreffende adviesinstantie NIET in zijn/haar rijtje tbmedewisadviseurvoor (beheer detailscherm tegel _Medewerkers_)
  - OF - indien geen fileserver en wel DMS:
    - en methode is StUF-ZAKEN 310
    - en de externe zaakcode (dvintzaakcode) is leeg. Het programma kijkt naar de externe zaakcode van het advies zelf indien de instelling _Sectie: Adviezen en Item: AdviesIsZaak_ aangevinkt is. Zo niet dan kijkt het programma naar de externe zaakcode van de bovenliggende hoofdzaak. Zie ook de opmerking bij het kopje hierboven: _Muteren als host-organisatie_.

#### Welstandsscherm

- Zichtbaar en enabled indien de adviesinstantie (beheerportaal-Nieuw) de eigenschap _is welstandsadvies_ aangevinkt heeft staan. Zo nodig wordt een kaart aangemaakt in tbadvieswelstand, waarin extra welstandsgegevens kunnen worden genoteerd (commissie: beheertabel welstandcommissies, datum en conclusie en verslag). De conclusietekst - alleen indien het tekst vak nog leeg is - kan default na het kiezen van een conclusie, worden opgehaald uit de instellingentabel: zie: [Sectie Welstand](/instellen_inrichten/configuratie/sectie_welstand.md).

#### Urenregistratie

- Zichtbaar en enabled indien de inlogger compartimentsrechten heeft:
  - het recht uren zichtbaar aangevinkt heeft staan bij blok _Adviezen_ bij de betreffende module (beheertegel _Functionele rechten_)
  - OF het recht _mag uren van anderen muteren_ aangevinkt heeft staan op de medewerkerskaart.
