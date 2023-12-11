# Detailscherm Adviezen

De schermidentifier is: **MDDC_geefAdviesDetail.xml**.

De schermidentifier van het achterliggende welstandsadviesscherm is **MDDC_getVwFrmAdviesWelstandDetail.xml**.

Dit scherm kan worden aangeroepen vanuit de Lijst Adviezen bij een zaak.

## Error

Het scherm geeft een foutmelding, indien:

* er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
* de inlogger geen kijkrechten heeft op de adviezen bij betreffende hoofdzaak.

## Defaultwaarden

* De rappeldatum is een optelling van de aanvraagdatum + hetgeen is ingevoerd in de beheer tabel adviesinstanties bij rappeldagen bij de betrokken adviesinstantie.
* De adviesvrager/behandelaar (degene die verantwoordelijk is dat het uitgezette advies op tijd binnenkomt) is:
  * de default behandelaar die is toegekend in de beheertabel bij de betrokken adviesinstantie:
    * indien deze waarde leeg is kijkt het programma naar de instelling van *Getal1* bij *Sectie: Adviezen en Item: Adviesverantwoordelijke*
    * indien deze waarde 1 is dan is de default behandelaar/adviesvrager gelijk aan de van de inlogger
    * indien deze waarde 2 is dan is de default behandelaar/adviesvrager gelijk aan de actieve behandelaar (tbinbehandelingbij).
  * Indien bij de insert van een nieuw advies het advies echter direct wordt afgehandeld, dan wordt de adviesvrager/behandelaar gevuld met de inlogger.
* Het behandelend team (dat verantwoordelijk is dat het uitgezette advies op tijd binnenkomt) is het default team dat is toegekend in de beheertabel bij de betrokken adviesinstantie.

## Zichtbaarheid adviesvrager versus team en andere kolommen

Voor de dropdownlijst met **adviesvrager** geldt het volgende:

* de kolom is alleen zichtbaar indien de instelling *Sectie: Adviezen en Item: Voorwiezichtbaar* is aangevinkt
* de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
* en de medewerker moet in dienst zijn
* en het vakje *interne medewerker* moet aangevinkt zijn.
* en het vakje *is raadpleger* mag NIET aangevinkt zijn

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap: *overrule compartiment* aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

Voor de dropdownlijst met **behandelend team** geldt het volgende:

* de kolom is alleen zichtbaar indien de instelling *Sectie: Adviezen en Item: teamzichtbaar* is aangevinkt
* het team moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger.

Voor de dropdownlijst met **Gekozen adviseur** geldt het volgende:

* de kolom is alleen zichtbaar indien de instelling *Sectie: Adviezen en Item: KiesAdviseur* is aangevinkt.

De kolom **Beoordeling door Adviesgever** (tbadviezen.dvadvgeverpositief) is zichtbaar indien de instelling *Sectie: Adviezen en Item: Dvadvgeverposvisible* wordt aangevinkt. In dat geval wordt de radiobutton kolom *Beoordeling Adviesgever* zichtbaar naast de bestaande kolom *Beoordeling Adviesaanvrager* (dladviespositief). In deze nieuwe kolom kan de adviesgever zelf zijn/haar beoordeling geven.

Deze nieuwe kolom heeft GEEN invloed op de lijst recent binnengekomen adviezen. Die blijft bestaan uit de adviezen waarvoor geldt dat de adviesdatum gevuld is EN nog niet beoordeeld door de adviesvrager.

## Zichtbaarheid blokken

Het blok **Keten** is alleen zichtbaar indien de instelling *Sectie: Adviezen en Item: Adviesiszaak* is aangevinkt.

## Muteren

De kolommen kunnen gemuteerd worden indien:

* de inlogger wijzigrechten heeft op de adviezen bij betreffende hoofdzaak
* EN in het blok keten is de einddatum/blokkeerdatum NIET gevuld
* EN die bovenliggende hoofdzaak niet is geblokkeerd
* EN de editschuif aan staat
* EN - indien de inlogger lid is van een compartiment - dan moet het betreffende compartiment het zaaktype van de hoofdzaak bevatten en de gemeente waar de hoofdzaak speelt
* EN - indien de inlogger GEEN lid is van een compartiment, dan mag de combinatie van het zaaktype van de hoofdzaak en de gemeente waar de hoofdzaak speelt in geen enkel compartiment voorkomen.

Een voorbeeld met betrekking tot compartimentsrechten: stel de advieszaak hoort bij een omgevingszaak. Dat geldt dat vvwfrmomgvergunningen.dnkeycompartiment (van de betreffende omgevingszaak) gelijk moet zijn aan tbmedewerkers.dnkeycompartiment (van de inlogger). Dus beide gevuld met null of beide gevuld met eenzelfde waarde.

Hierop bestaan de volgende uitzonderingen:

* De kolom met de radiobutton **Advies Retour** is niet muteerbaar indien:
  * de kolom datering advies (ddadvdatering) leeg is  
  * OF de inlogger is een medewerker met de eigenschap *Is ExterneAdviseur*.
* De kolom **dvintzaakcode** (zaak/DMS code) is alleen muteerbaar indien de inlogger het recht *wijzigen externe zaaknummer* bij adviezen aangevinkt heeft staan voor de betreffende module (beheerportaal-Nieuw, tegel *Functionele rechten*).

Voorts kan het uploaden van een document bij een advies van invloed zijn op de volgende kolommen:

* Aan de kolom **uploadlog** van de betreffende advieszaak wordt een regel met systeemdatum + medewerkerscode en upgeloade filenaam toegevoegd.
* Indien de instelling *Sectie: Adviezen en Item: DateringDoorUpload* aangevinkt is EN de kolom **datering advies** (tbadviezen.ddadvdatering) is leeg dan wordt deze gevuld met de datum van upload (geldt ook voor de kolom **tbadviezen.ddadvadvies**).

Bij het afsluiten van een hoofdzaak waar het advies onder valt kan het programma vragen om openstaande adviezen automatisch van een vervaldatum te voorzien (deze vraag wordt alleen gesteld indien er nog openstaande adviezen zijn EN indien de adviezen NIET gedefinieerd zijn als aparte zaken in het externe zaaksysteem).

## Muteren als host-organisatie

Indien het advies valt onder een compartiment, maar het advies is aangevraagd bij de HOST-organisatie (de adviesinstantiecode komt voor in de kolom *Tekst* van de instelling *Sectie: Adviezen en Item: AdviescodeHostbijCompartiment* (waarbij de coderingen gescheiden moeten zijn met een puntkomma, dus bijv. EZ;VROM;)), dan geldt dat medewerkers van de Host-organisatie (dus inloggers die niet aan een compartiment gekoppeld zijn) toch de advieskaart kunnen muteren mits:

* de inlogger advies editrechten heeft
* de bovenliggende kaart niet geblokkeerd is
* de instelling *Sectie: Adviezen en Item: DateringDoorUpload* NIET aangevinkt is.

Indien de instelling *Sectie: Adviezen en Item: DateringDoorUpload* WEL aangevinkt is, kunnen deze host-inloggers niet muteren, maar wel de uploadknop gebruiken.

## Kolommen dateringadvies en adviesretour

**Adviesretourdatum (tbadviezen.ddadvadvies)** is NIET zichtbaar indien *Getal1* van de instelling *Sectie: Adviezen en Item: DateringDoorUpload* de waarde 2 heeft EN de instelling NIET aangevinkt is. Als de instelling *Sectie: Adviezen en Item: DateringDoorUpload* is aangevinkt dan wordt de kolom *Adviesretourdatum* onder water gevuld met de uploaddatum bij het uploaden van een adviesdocument indien deze kolom nog een lege datum had. Bij het wijzigen van de kolom *Dateringadvies* kijkt OpenWave of de kolom adviesretourdatum een lege waarde heeft, is dat het geval dan wordt de adviesretourdatum overschreven met de waarde van dateringadvies.

**dateringadvies (tbadviezen.dddateringadvies)** is muteerbaar indien:

* de instelling *Sectie: Adviezen en Item: DateringDoorUpload* NIET aangevinkt is
* EN
  * OF bij de betreffende adviesinstantie de kolom *Autorisatie voor datering advies vereist* (tbadviesinstanties.dlautdatadvies) NIET is aangevinkt,
  * OF bij de betreffende adviesinstantie de kolom *Autorisatie voor datering advies vereist* (tbadviesinstanties.dlautdatadvies) WEL aangevinkt is, maar dan moet de inlogger voor de betreffende module het recht *wijzigen datering advies* (dlcomgadvdatedt) aangevinkt hebben staan.

Als de instelling *Sectie: Adviezen en Item: DateringDoorUpload* is aangevinkt dan wordt de kolom dddateringadvies onder water gevuld met de uploaddatum bij het uploaden van een adviesdocument indien deze kolom nog een lege datum had.

## Dropdownlijst Adviesvrager/verantwoordelijke behandelaar

Voor de dropdownlijst met **adviesvrager** geldt het volgende:

* de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
* en de medewerker moet in dienst zijn
* en het vakje *interne medewerker* moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap: *overrule compartiment* aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

### Extern zaak/DMS nummer

Hieronder komt het begrip externe zaak/DMS nummer voor. Daarmee wordt bedoeld de kolom externe zaak/DMS (dvintzaakcode) die voor kan komen op de advieskaart zelf en/of bij de bovenliggende hoofdzaak.

Het programma kijkt naar de advieskaart zelf indien de instelling *Sectie: Adviezen en Item: AdviesIsZaak* is aangevinkt. In alle andere gevallen (niet aangevinkt of instelling bestaat niet) dan komt het externe zaak/DMS nummer uit de hoofdzaak van de betreffende module.

## Blok documenten

In het blok documenten kan een gebruiker met advies insert- en delete-rechten documenten koppelen aan het betreffende advies uit de tabel met geregistreerde documenten (tbcorrespondentie) die aan de hoofdzaak verbonden zijn. Vanuit deze lijst kan een gebruiker een document openen en - indien geautoriseerd - wijzigen. Voor het openen of wijzigen van een document gelden dezelfde rechten en voorwaarden als vanuit de geregistreerde documententabel zelf ([Lijst Geregistreerde Documenten bij een zaak](/docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/lijst_geregistreerde_documenten_bij_zaak.md)).

De koppeltabel is tbkopadviescorresp.

## Triggers

### Triggers in het scherm zelf (achter de kolommen)

#### Stuur mail aan adviesinstantie achter de kolom email verstuurd

Zie verder [Email adviesinstantie](/docs/probleemoplossing/programmablokken/e-mail_adviesinstantie.md).

* Zichtbaar en enabled indien:
  * de inlogger wijzigrechten heeft op de advieskaart voor de betreffende module
  * EN dddmsafgehandeld is leeg (alleen zichtbaar indien instelling *Sectie: Adviezen en Item: AdviesIsZaak* aangevinkt is)
  * EN de bovenliggende zaak niet is geblokkeerd (zie hierboven de uitzondering).

#### Maak zaak in zaak/DMS systeem

Achter externe zaak/DMS nummer.

* Zichtbaar en enabled indien:
  * de inlogger muteerrechten heeft op de adviezen
  * EN de einddatum zaak/DMS (dddmsafgehandeld) moet leeg zijn
  * EN externe zaak/DMS nummer (dvintzaakcode) een **lege waarde** heeft
  * EN de bovenliggende zaak niet is geblokkeerd (zie hierboven de uitzondering)
  * EN - indien de hoofdzaak NIET onder een compartiment valt - de instelling *Sectie: Koppeling Zaak* en *Item: Methode* en *Tekst: StUF-ZAKEN 310* staat aangevinkt
  * EN - indien de hoofdzaak WEL onder een compartiment valt - dan moet de kolom *dmsmethode* van het betreffende compartiment in het beheerportaal-Nieuw gevuld zijn met *StUF-Zaken 310*
  * EN de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan
  * EN - indien de hoofdzaak NIET onder een compartiment valt - dan moet de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: ZaaktypeAdvies* gevuld zijn (en aangevinkt)
  * EN - indien de hoofdzaak WEL onder een compartiment valt - dan moet de kolom *zaaktype zaak/dmssysteem (dvdmszaaktypeadvies)* van het betreffende compartiment in het beheerportaal-Nieuw gevuld zijn
  * EN indien het advies een zelfstandige zaak is in externe zaaksysteem: de instelling *Sectie: Adviezen en Item: AdviesIsZaak* is aangevinkt.

#### Sluit zaak in zaak/DMS systeem

Achter eind/blokkeerdatum van zaak/DMS nummer.

* Zichtbaar en enabled indien:
  * de inlogger muteerrechten heeft op de adviezen
  * EN externe zaak/dms nummer (dvintzaakcode) een **gevulde** waarde heeft
  * EN de bovenliggende zaak niet is geblokkeerd (zie hierboven de uitzondering)
  * EN - indien de hoofdzaak NIET onder een compartiment valt - de instelling *Sectie: Koppeling Zaak* en *Item: Methode* en *Tekst: StUF-ZAKEN 310* staat aangevinkt
  * EN - indien de hoofdzaak WEL onder een compartiment valt - dan moet de kolom *dmsmethode* van het betreffende compartiment in het beheerportaal-Nieuw gevuld zijn met *StUF-Zaken 310*
  * de inlogger is lid van rechtengroep die het recht wijzigen externe zaaknummers bij betreffende module/inrichting aangevinkt heeft staan
  * EN Het advies een zelfstandige zaak is in externe zaaksysteem: de instelling *Sectie: Adviezen en Item: AdviesIsZaak* is aangevinkt
  * EN het resultaat in de kolom *retouradvies* (dnkeyretouradvies) is gevuld (EN in de beheertabel tbretouradvies is de kolom dvdmsresultaat gevuld).

#### Heropen/ leegmaken blokkeer/einddatum

Achter eind/blokkeerdatum van zaak/DMS nummer indien eind/blokkeerdatum is gevuld.

* Zichtbaar en enabled indien:
  * bovenstaande instellingen
  * EN waarbij – indien dddmsafgehandeld is gevuld – het recht op module niveau: *Leegmaken van gevulde afhandel-intrekkingsdatum* (dlbomgafsedt, dlbhahafsedt, dlbovvafsedt ….) is aangevinkt.

### Triggers rechtsboven in menu opties

#### Toon geregistreerde documenten (bij dit advies)

Zie [Geregistreerde Documenten](/docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten.md).

* Zichtbaar en enabled indien:
  * de instelling *Sectie: Documenten Item: Documentregistratie* is aangevinkt
  * EN de gebruiker het recht *Inzien geregistreerde documenten* bij de betreffende module aangevinkt heeft staat (bijv. tbomgrechten.dlcomgcorregvsb).

#### Creëer document

Zie [Creëer document](/docs/probleemoplossing/programmablokken/creeer_document.md).

* Zichtbaar indien de inlogger lid is van een rechtengroep die bij hoofdzaak het recht creëren van documenten heeft
* De knop is disabled indien:
  * de bovenliggende zaak geblokkeerd is.
  * OF de einddatum zaak/dms (dddmsafgehandeld) gevuld is (alleen zichtbaar indien instelling *Sectie: Adviezen en Item: AdviesIsZaak* aangevinkt is)
  * OF compartimentsrechten niet ok zijn.

#### Toon uploads bij dit advies

Zie [Upload Lijst](/docs/probleemoplossing/module_overstijgende_schermen/uploads_lijst.md)).

* Zichtbaar en enabled indien:
  * de instelling *Sectie: Documenten* en *Item: MultipleUpload* aangevinkt is
  * EN de inlogger lid is van een rechtengroep die bij hoofdzaak het recht uploaden van documenten heeft.

#### Creëer email

Zie verder bij [Creëer email](/docs/probleemoplossing/programmablokken/creeer_email.md).

* Zichtbaar en enabled indien:
  * de inlogger lid is van een rechtengroep die bij omgevingszaak het recht *creëren van documenten* heeft
  * de bovenliggende zaak is niet geblokkeerd.

### Triggers linksonder

#### Toon documenten

Zie [Toon documenten en download](/docs/probleemoplossing/programmablokken/toon_documenten_en_download.md).

* Zichtbaar wanneer:
  * een van onderstaande twee beweringen waar is:
    * de instelling *Sectie: Documenten en Item: Documentregistratie* is aangevinkt EN de gebruiker het recht *Inzien geregistreerde documenten* bij de betreffende module aangevinkt heeft staat  (bijv. tbomgrechten.dlcomgcorregvsb)
    * deze instelling staat niet aan EN de gebruiker het recht *Inzien documenten buiten registratie om bij de betreffende module* aangevinkt heeft staat  (bijv. tbomgrechten.dlcomgcorvsb)
  * EN - wanneer de bovenliggende hoofdzaak NIET wordt behandeld in een compartiment dan:
    * moet *Sectie: Documenten* en *Item: OphalenViaFileserver* OF *Sectie: Documenten* en *Item: OphalenViaDms* aangevinkt zijn
    * EN - indien OphalenViaDms - dan moet de kolom *Tekst* bij instelling *Sectie: KoppelingDocnaardms en Item: Methode* de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben en aangevinkt staan
    * EN - wanneer de bovenliggende hoofdzaak WEL wordt behandeld in een compartiment dan:
              *moet de kolom dlfileserver of dldms in het betreffende compartiment (beheerportaal-Nieuw) aangevinkt zijn
              * EN – indien  dlDms aangevinkt dan moet de kolom tbcompartiment.dvdmsmethode de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben.
* De knop is disabled indien:
  * geen fileserver en wel DMS
  * EN methode is StUF-ZAKEN 310
  * EN de externe zaakcode (dvintzaakcode) is leeg. Het programma kijkt naar de externe zaakcode van het advies zelf indien de instelling *Sectie: Adviezen en Item: Adviesiszaak* aangevinkt is. Zo niet dan kijkt het programma naar de externe zaakcode van de bovenliggende hoofdzaak.

### Creëer email (2)

Zie verder bij [Creëer email](/docs/probleemoplossing/programmablokken/creeer_email.md).

* Zichtbaar en enabled indien de inlogger lid is van een rechtengroep die documenten mag creëren
  * EN de bovenliggende zaak is niet geblokkeerd.
* Klikken op het email-icoon start de wizard *Maak email*. Er kan gekozen worden uit mailsjablonen mits deze gedefinieerd zijn aan de beheerkant onder de tegel *Emailsjablonen*. Voor meer informatie over het definiëren van mailsjablonen zie [Emailsjablonen](/docs/instellen_inrichten/emailsjablonen.md).

#### Upload document(en)

Zie [Upload document](/docs/probleemoplossing/programmablokken/upload_document.md).

* Zichtbaar wanneer:
  * de instelling *Sectie: Documenten* en *Item: MultipleUpload* aangevinkt is
  * EN - wanneer de bovenliggende zaak NIET wordt behandeld in een compartiment dan:
    * moet *Sectie: Documenten* en *Item: OphalenViaFileserver* OF *Sectie: Documenten* en *Item: OphalenViaDms* aangevinkt zijn
    * EN - indien OphalenViaDms - dan moet de kolom *Tekst* bij instelling *Sectie: KoppelingDocnaardms en Item: Methode* de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben en aangevinkt staan
  * EN - wanneer de bovenliggende zaak WEL wordt behandeld in een compartiment dan:
    * moet de kolom dlfileserver of dldms in het betreffende compartiment (beheerportaal-Nieuw) aangevinkt zijn
    * EN – indien  dlDms aangevinkt dan moet de kolom tbcompartiment.dvdmsmethode de waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben.
* De knop is disabled indien:
  * geen document uploadrechten (beheerportaal-Nieuw, tegel *Functionele rechten*, blok Documenten)
  * OF de zaak geblokkeerd is
  * OF de einddatum zaak/dms (dddmsafgehandeld) is gevuld (alleen zichtbaar indien instelling *Sectie: Adviezen en Item: AdviesIsZaak* aangevinkt is)
  * OF Compartimentrecht is niet OK
  * OF de inlogger is een *Externe adviseur* maar heeft de betreffende adviesinstantie NIET in zijn/haar rijtje tbmedewisadviseurvoor (beheer detailscherm tegel *Medewerkers*)
  * OF - indien geen fileserver en wel DMS:
    * EN methode is StUF-ZAKEN 310
    * EN de externe zaakcode (dvintzaakcode) is leeg. Het programma kijkt naar de externe zaakcode van het advies zelf indien de instelling *Sectie: Adviezen en Item: AdviesIsZaak* aangevinkt is. Zo niet dan kijkt het programma naar de externe zaakcode van de bovenliggende hoofdzaak. Zie ook de opmerking bij het kopje hierboven: *Muteren als host-organisatie*.

#### Welstandsscherm

* Zichtbaar en enabled indien de adviesinstantie (beheerportaal-Nieuw) de eigenschap *is welstandsadvies* aangevinkt heeft staan. Zo nodig wordt een kaart aangemaakt in tbadvieswelstand, waarin extra welstandsgegevens kunnen worden genoteerd (commissie: beheertabel welstandcommissies, datum en conclusie en verslag). De conclusietekst - alleen indien het tekst vak nog leeg is - kan default na het kiezen van een conclusie, worden opgehaald uit de instellingentabel: zie: [Sectie Welstand](/docs/instellen_inrichten/configuratie/sectie_welstand.md).

#### Urenregistratie

* Zichtbaar en enabled indien de inlogger compartimentsrechten heeft:
  * het recht uren zichtbaar aangevinkt heeft staan bij blok *Adviezen* bij de betreffende module (beheertegel *Functionele rechten*)
  * OF het recht *mag uren van anderen muteren* aangevinkt heeft staan op de medewerkerskaart.
