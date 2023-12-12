# Verwerking DSO STAM berichten

Zie ook:

- [Verwerken DSO-bijlagen vanuit digi-koppelaar](/docs/probleemoplossing/programmablokken/upload_dso-document_vanuit_digi-koppelaar.md)
- [Testen xml-berichten DSO / Erk.Maatreg.](/docs/instellen_inrichten/testen_dso_erkmaatreg.md)

De service laag van de OpenWave omgeving ontvangt deze DSO-berichten (een triggerbericht in xml-formaat en een verzoekbericht in xml-formaat en een Jnet/EnableU bericht in xml om een intrekking door te geven) op het endpoint /DSO/Verzoek/ als HTTPS:POST.

De luisterservice op /DSO/Verzoek -endpoint roept getAuthorisation aan met de loginnaam/pass uit de HTTPS en krijgt hierdoor een sessie identifier.

Met deze sessie identifier wordt (deze) API verwerkDSOVerzoekbericht aangeroepen met de sessie identifier als eerste en de xml als tweede parameter.

Alleen in het geval dat het binnengeschoten bericht geen verzoek- of trigger- of verzoeknotificate- of Intrekbericht is, wordt een foutcode geretourneerd (naar de digi-koppelaar).

## Loggen messagelog

De berichten worden gelogd indien de instelling _Sectie: DSO en Item: Messagelog_ aangevinkt is (beheertegel _Messagelog_). Indien aangevinkt en _Getal1_ is ongelijk aan 1, dan worden alleen de valide trigger- en verzoekberichten gelogd in Tbmessagelog (mits de algemene instelling _Sectie: OWB en Item: Messagelog_ ook aangevinkt is). Indien _Getal1_ de waarde 1 heeft, dan worden ook de niet valide berichten op het DSO-endpoint gelogd.

In geval dat het bericht valide is, maar door ontbrekende configuratie het bericht toch niet kan worden verwerkt, dan wordt de oorzaak van dit euvel in de messagelog in de kolom _Error_ getoond.

## Intrekbericht

Indien een aanvrager een verzoek heeft ingetrokken is het de digi-koppelaar (Jnet/EnableU) die in een eigen formaat deze boodschap doorgeeft:

```xml
<root>
  <oin>00000001001100415000</oin>
  <verzoeknummer>2022070500133</verzoeknummer>
  <actie>close</actie>
</root>
```

OpenWave vangt deze op en behandelt deze alsof het een verzoekbericht is met doel **intrekken**: zie hieronder.

## Trigger- of Verzoeknotificatiebericht

> Met Stam 4.0 is het begrip trigger veranderd in verzoeknotificatie. Waar u leest triggerbericht kan u hieronder ook verzoeknotificatiebericht lezen.

Het triggerbericht is vanaf versie 2.0 van de STAM qua inhoud zo beperkt dat OpenWave alleen nog het DSO verzoeknummer uit het triggerbericht opslaat in de tabel tbDSOtrigger (geen userinterface). Vroeger werd het triggerbericht gebruikt om BSN-nummer en KvK- en Vestigingsnummer van de aanvrager en gemachtigde op te slaan in afwachting van het verzoekbericht (in tbDSOtrigger). Bij de verwerking van het verzoekbericht werd vervolgens de tabel geraadpleegd bij het (over)schrijven van de aanvrager en gemachtigde. Dit laatste is dus komen te vervallen per STAM 2.0 versie.
De registratie van het DSO verzoeknummer in tbDSOtrigger blijft behouden zodat er toch voor ieder nieuw DSO aanvraag een registratie is van het binnengekomen triggerbericht bij OpenWave.

De gegevens in deze tabel tbDSOtrigger worden opgeschoond na 31 dagen tenzij anders aangegeven in kolom _Getal1_ van de instelling _Sectie: DSO en Item: BewaardagenTabelDsoTrigger_.

## Verplichte instellingen

- In de beheertabel _Adressoorten/rollen_ dient exact één kaart te bestaan waarbij het vakje _Is rol voor contactpersoon uit verzoekbericht DSO_ (tbadressoort.dldsorolcontactpers) aangevinkt is. Deze rol is bedoeld voor de contactpersoon uit het DSO-verzoekbericht.
- In de beheertabel _Adressoorten/rollen_ dient exact één kaart te bestaan met code _AVR_ die gebruikt wordt als aanvrager (initiatiefnemer).
- In de beheertabel _Adressoorten/rollen_ dient exact één kaart te bestaan met code _GEM_ die gebruikt wordt als gemachtigde.
- In de tabel met instellingen (beheertegel _Configuratie_) moet bestaan de kaart met _Sectie: Koppeling OLO_ en _Item: Dossierbehandelaar_, waarbij kolom _Tekst_ gevuld is met een waarde die overeenkomt met de code (tbmedewerkers.dvcode) van een (niet vervallen) kaart uit de medewerkerstabel. Dit wordt de default dossierbehandelaar bij ontbreken van de default-behandelaar in het zaaktype.
- In de tabel met instellingen moet bestaan de kaart met _Sectie: Koppeling OLO Item: DummyLokatiePerceelkey_ waarin _Getal2_ verwijst naar een dnkey van een kaart in tbperceeladressen die staat voor onbekend adres.

Zie ook de veronderstelde aanwezigheid van bepaalde zaaktypes hieronder in het blok _Zaaktype_.

## Verwerking Verzoekbericht

Uit de tag`<verzoeknummer>`wordt het verzoeknummer opgehaald.

### Doel

    Met STAM 4.0 is het begrip Vooroverleg veranderd in Conceptverzoek. Waar hieronder Vooroverleg staat kan ook als Conceptverzoek gelezen worden.

Uit de tag`<doel>`wordt bepaald of het bericht gaat over Initiëren, Vooroverleg, Aanvullen of Intrekken.

- Indien **Aanvullen** dan wordt de kaart gezocht in tbomgvergunning met dvlvoaanvraagnr = verzoeknummer. Indien niet gevonden of er zijn meerdere kaarten gevonden met hetzelfde verzoeknummer dan wordt de verwerking gestopt (zie kolom _Error_ in messagelog). Indien wel gevonden dan wordt een kaartje aangemaakt in tbomgdsoaanvulintrek bij de betreffende omgevingszaak (deze tabel is zichtbaar als lijstje in detailscherm omgevingszaak in blok **DSO-aanvullingen**) met het volgnummer en doel.
  - Uitzondering: indien niet gevonden maar instelling _Sectie: DSO, Item: AanvullingTotNieuweZaak_ is aangevinkt (default false) dan wordt er wel een nieuwe zaak aangemaakt. Dit kan men zo instellen om de DSO verzoeken tot een nieuwe zaak te verwerken in OpenWave waarop al 1 of meer aanvullingen zijn, die pas na het wijzigen van bevoegd gezag bij de organisatie binnenkomen. In dit geval stuurt het DSO alleen de laatste Aanvulling naar de organisatie. Als de instelling aan staat zal er een nieuwe zaak worden aangemaakt conform werking zoals beschreven op deze pagina (doel blijft _Aanvullen_). Daarnaast wordt een record in tbomgdsoaanvulintrek bij de nieuwe omgevingszaak aangemaakt. Mocht er ingesteld staan dat er automatisch een DSO ontvangstbevestigingsmail verstuurd moet worden dan zal deze van sjabloon Aanvulling zijn.
- Indien **Intrekken** dan wordt de kaart gezocht in tbomgvergunning met dvlvoaanvraagnr = verzoeknummer. Indien niet gevonden of er zijn meerdere gevonden dan wordt de verwerking gestopt (zie kolom _Error_ in messagelog). Indien wel gevonden dan wordt een kaartje aangemaakt in tbomgdsoaanvulintrek bij de betreffende omgevingszaak (deze tabel is zichtbaar als lijstje in detailscherm omgevingszaak in blok **DSO-aanvullingen**) met het volgnummer en doel.
- Indien **Vooroverleg** of **Initiëren** dan wordt in principe altijd een nieuwe kaart gemaakt in TbOmgvergunning.

### Locatie

Alleen bij Initiëren en Vooroverleg.

Uit blok `<projectlocaties>` wordt alleen de informatie uit het eerste sub blok `<projectlocatie>` gebruikt om de nieuwe zaak te koppelen aan precies één OpenWave locatie (tbperceeladressen). Als volgt:

1. OpenWave zoekt eerst op adres (waarbinnen eerst op BAG-ID nummeraanduiding, anders op postcode + huisnummer-gegevens, en anders op straat, huisnummergegevens en woonplaats)
1. Niet gevonden (of niet aanwezig in STAM-bericht) dan wordt gezocht op x- en y-coördinaat op grond van de opgegeven punt locatie in rijksdriehoek.
1. Niet gevonden (of niet aanwezig in STAM-bericht) dan wordt gezocht op kadastrale gegevens.
1. Niet gevonden (of niet aanwezig in STAM-bericht) dan wordt gezocht op punt van coördinaten ERTS, waarbij zo nodig omgerekend wordt naar rijksdriekhoek.

Niet gevonden (of niet aanwezig in STAM-bericht) valt OpenWave terug op _Getal2_ van _Sectie: Koppeling OLO Item: DummyLokatiePerceelkey_ (onbekend adres). Daar kan nog van worden afgeweken indien OpenWave (bij ontbreken van uitvoerende instantie) op grond van bevoegd gezag in de tabel tboin een gemeente-id verwijzing vindt (kolom tboin.dvgemeenteid), waarvoor een compartiment is gedefinieerd in OpenWave. In dat laatste geval zal OpenWave de waarde - mits gevuld - van kolom tbcompartiment.dnkeyswfdummyadres nemen als keyverwijzing naar tbperceeladressen. Die tbperceeladressenkaart moet bij dezelfde gemeente-id horen!

### Zaaktype

Alleen bij Initiëren en Vooroverleg.

De volgende types kunnen worden aangeleverd in het verzoekbericht:

- Aanvraag vergunning
- Melding
- Informatie
- Informatie ongewoon voorval
- Aanvraag maatwerkvoorschrift
- Melding gelijkwaardige maatregel
- Aanvraag toestemming gelijkwaardige maatregel

Het is raadzaam hier zaaktypes voor te definiëren (of bestaande te hergebruiken) in de beheertabel _Zaaktypes omgeving_ (tbsoortomgverg). Daartoe is de kolom _Verzoektype_ (dvdsotype) in het blok _DSO-type_. OpenWave zal eerst proberen vast te stellen of het DSO verzoekbericht voor een compartiment is bedoeld op grond van de locatie, uitvoerende instantie en bevoegd gezag.

![](applicatiebeheer/probleemoplossing/programmablokken/dsointierenbepalingzaaktypedummyadres.png.png){ class="media" loading="lazy" alt="" width="800" }

Indien de uitvoerende instantie (behandeldienst) in het verzoekbericht is gevuld dan is het verzoekbericht sowieso niet voor een compartiment.

Anders, indien de gevonden gemeente-id (op grond van locatieadres/bevoegd gezag) wel voorkomt in tbkopcompgem (de tabel met gemeentes per compartiment) dan is het verzoekbericht voor een compartiment. Het is in dit geval van groot belang dat de kolom tbcompartiment.dnkeyswfdummyadres met een keywaarde uit tbperceeladressen wordt gevuld, die van toepassing is op dat compartiment (dezelfde gemeente-id).

Om het zaaktype (een rij uit tbsoortomgverg) te kunnen vaststellen redeneert OpenWave als volgt:

- Indien de zaak NIET voor een compartiment is dan:
  - Indien doel = Initiëren dan wordt in deze tabel de - niet vervallen - kaart opgezocht waar Verzoektype (dvdsotype) gelijk is aan de waarde van de aangeleverde tag `<Type>` EN waarbij _Is zaaktype vooroverleg DSO_ (dlisdsovooroverleg) **NIET** is aangevinkt EN waarbij _Zaaktype is exclusief voor compartiment_ (dlW055) NIET is aangevinkt. | Dat moet er precies één zijn anders wordt de verwerking gestopt (zie kolom _Error_ in messagelog).
  - Indien doel = Vooroverleg dan wordt in deze tabel de - niet vervallen - kaart opgezocht waar Verzoektype (dvdsotype) gelijk is aan de waarde van de aangeleverde tag `<Type>` EN waarbij _Is zaaktype vooroverleg DSO_ (dlisdsovooroverleg) WEL is aangevinkt EN waarbij _Zaaktype is exclusief voor compartiment_ (dlW055) **NIET** is aangevinkt.. Dat moet er precies één zijn anders wordt de verwerking gestopt (zie kolom _Error_ in messagelog).
- Indien de zaak WEL voor een compartiment is dan:
  - Indien doel = Initiëren dan wordt in deze tabel de - niet vervallen - kaart opgezocht waar Verzoektype (dvdsotype) gelijk is aan de waarde van de aangeleverde tag `<Type>` EN waarbij _Is zaaktype vooroverleg DSO_ (dlisdsovooroverleg) NIET is aangevinkt EN waarbij _Zaaktype is exclusief voor compartiment_ (dlW055) **WEL** is aangevinkt EN waarbij in de compartimentszakentabel tbkopcompsrtomgverg bij het betreffende compartiment een rij bestaat die gerelateerd is aan deze tbsoortomgvergkaart. Indien op deze wijze geen unieke kaart gevonden in tbsoortomgverg dan redeneert OpenWave dat de zaak toch niet voor een compartiment is en zoekt opnieuw in tbsoortomgverg waarbij _Zaaktype is exclusief voor compartiment_ (dlW055) **NIET** is aangevinkt.
  - Indien doel = Vooroverleg dan wordt in deze tabel de - niet vervallen - kaart opgezocht waar Verzoektype (dvdsotype) gelijk is aan de waarde van de aangeleverde tag `<Type>` EN waarbij _Is zaaktype vooroverleg DSO_ (dlisdsovooroverleg) WEL is aangevinkt EN waarbij _Zaaktype is exclusief voor compartiment_ (dlW055) **WEL** is aangevinkt EN waarbij in de compartimentszakentabel tbkopcompsrtomgverg bij het betreffende compartiment een rij bestaat die gerelateerd is aan deze tbsoortomgvergkaart. Indien op deze wijze geen unieke kaart gevonden in tbsoortomgverg dan redeneert OpenWave dat de zaak toch niet voor een compartiment is en zoekt opnieuw in tbsoortomgverg waarbij _Zaaktype is exclusief voor compartiment_ (dlW055) **NIET** is aangevinkt.

In alle gevallen wordt bij het gevonden zaaktype uit tbsoortomgverg de fatale periode en masker van de wavezaakcode opgehaald.

### Project

Alleen bij Initiëren en Vooroverleg.

Indien de tag`<projectId>`is gevuld, zoek dan de inhoud hiervan op in TbDsoProject. Niet gevonden (maar wel gevuld) maak dan een nieuwe projectkaart in TbDsoProject (beheertegel _DSO projecten_).

In alle gevallen wordt de kolom tbomgvergunning.dlisdso gevuld met 'T'. Deze kolom bepaalt of de DSO-blokken zichtbaar zijn in de detailkaart van de omgevingzaak.

### Maak nieuw of zoek bestaande zaak in tbomgvergunning

- Indien **Initiëren of Vooroverleg** dan wordt een nieuwe zaak aangemaakt onder het gevonden zaaktype (dnkeysoortomgverg), project (dnkeydsoproject) en bij de gevonden locatie (dnkeyperceeladressen), waarbij de kolom dvlvoaanvraagnr met het verzoeknummer wordt gevuld en de kolom dlisdso met 'T'. Bij de omgevingszaak worden de niet-repetitieve gegevens overgenomen op het detailniveau van de zaak (tags: `<naam>`, `<indiendatum>`, `<ambtshalve>`, `<doel>`, `<volgnummer>` e.d.). Op grond van zaaktype (masker en fatale termijn) wordt dvzaakcode berekend en de fatale datum. Bij _Vooroverleg_ wordt de kolom ddvooroverleg gevuld met de indieningsdatum van het bericht.
- Indien **Aanvullen of Intrekken** dan wordt de omgevingszaak opgezocht op grond van verzoeknummer (op kolom dvlvoaanvraagnr) en worden de kolommen _volgnummer_ en _doel_ bijgewerkt. Bovendien wordt een kaartje aangemaakt in tbomgdsoaanvulintrek bij de betreffende omgevingszaak (deze tabel is zichtbaar als lijstje in detailscherm omgevingszaak in blok DSO-aanvullingen) met het volgnummer en doel.

### Projectlocaties

Alleen bij Initiëren en Vooroverleg.

Alle gegevens uit het blok `<projectlocaties>` worden opgenomen in de dochtertabel tbzaakkadperc bij de omgevingszaak. Omgevingstegel: _Projectlocaties\kadastrale percelen_.

Per blok `<projectlocatie>` wordt een kaart aangemaakt in deze tabel, waarbij - indien aanwezig - zowel puntcoördinaat, als polygoon (vooralsnog alleen de exterior ring), als adresgegevens, als kadastrale gegevens worden overgenomen. De puntcoördinaten en polygonen worden door OpenWave omgerekend naar het Rijksdriehoekstelsel.]]
Indien geen blok adresAanduiding in STAM-bericht en ook geen blok kadastralegegevens dan wordt de tbprojectlocaties.straatnaam gevuld met 'Getekend gebied'.

Indien de omgevingzaak is aangemaakt bij het onbekende perceeladres (DummyLokatiePerceelkey of dnkeyswfdummyadres bij compartiment) EN de instelling _Sectie: DSO-VerzoekAfhandelen en Item: Hoofdprojectlocatie_ is aangevinkt, dat wordt de kolom tbzaakkadperc.dlhoofdprojectlocatie van de eerste projectlocatie uit het STAM-bericht automatisch op T gezet.

### Bevoegd gezag

Alleen bij Initiëren en Vooroverleg.

Het OIN-nummer uit blok `<bevoegdGezag>` van de tag `<oin>` wordt opgezocht in tboin (beheertegel _OIN-nummers_). Indien deze niet bestaat wordt het OIN-nummer aangemaakt in deze tabel. In de omgevingszaak komt een verwijzing naar het tboin-record (dnkeyoinbevgez).

### Bevoegd gezag historie

Alleen bij Initiëren en Vooroverleg.

De gegevens uit het blok `<bevoegdGezagHistorie>` worden opgenomen in de dochtertabel tbomgbevgezhistorie bij de omgevingszaak. Per blok `<bevoegdGezag>` wordt een kaart aangemaakt in deze tabel (omgevingstegel _Historie DSO Bevoegd gezag_). Het OIN-nummer uit de tag `<oin>` wordt daarbij opgezocht in tboin (beheertegel _OIN-nummers_). Indien deze niet bestaat wordt het OIN-nummer aangemaakt in deze tabel. In de tbomgbevgezhistorie-kaart komt een verwijzing naar het tboin-record (dnkeyoin).

### Uitvoerende instantie

Alleen bij Initiëren en Vooroverleg.

Het OIN-nummer uit blok `<uitvoerendeInstantie>` van de tag `<oin>` wordt opgezocht in tboin (beheertegel _OIN-nummers_). Indien deze niet bestaat wordt het OIN-nummer aangemaakt in deze tabel. In de omgevingszaak komt een verwijzing naar het tboin-record (dnkeyoinuitvinst).

#### Uitvoerende instantiehistorie

Alleen bij Initiëren en Vooroverleg.

De gegevens uit het blok `<uitvoerendeInstantieHistorie>` worden opgenomen in de dochtertabel tbomguitvinsthistorie bij de omgevingszaak. Per blok `<uitvoerendeInstantie>` wordt een kaart aangemaakt in deze tabel (omgevingstegel _Historie DSO Behandeldienst_). Het OIN-nummer uit de tag `<oin>` wordt daarbij opgezocht in tboin (beheertegel _OIN-nummers_). Indien deze niet bestaat wordt het OIN-nummer aangemaakt in deze tabel. In de tbomguitvinsthistorie-kaart komt een verwijzing naar het tboin-record (dnkeyoin).

#### Dossierbehandelaar

Alleen bij _Initiëren en Vooroverleg_.

Er wordt een nieuwe kaart gemaakt in de dochtertabel tbinbehandelingbij bij de omgevingszaak met de medewerkerscode die als default behandelaar (dvcodedefbehandelaar) is toegekend aan het zaaktype (tbsoortomgverg). Indien de zaak in een compartiment wordt afgehandeld gaat het om de default behandelaar uit tbkopcompsrtomgverg (beheertegel _Compartimentrechten_). Indien deze defaultwaardes ontbreken dan valt OpenWave terug op de verplichte instelling _Sectie: Koppeling OLO_ en _Item: Dossierbehandelaar_.

#### Contactpersoon

Let op niet te verwarren met Initiatiefnemer of Gemachtigde: het gaat hier om hoe OpenWave de gegevens verwerkt uit het blok **Contactpersoon** indien aanwezig in het STAM-bericht.
Het blok **Contactpersoon** kan alleen worden opgevoerd bij het indienen van de aanvraag wanneer een vestiging of bedrijf de aanvraag indient. Het gaat dan om de volgende situaties:

- Er is geen gemachtigde en de initiatiefnemer is een bedrijf of vestiging
- Er is een gemachtigde en de gemachtigde is een bedrijf of vestiging

Zit er dus in het STAM-bericht zowel een initiatiefnemer (bedrijf) als een contactpersoon dan wordt er zowel een Aanvrager/Gemachtigde aangemaakt (het bedrijf) als een DSO contactpersoon.
Het is ook mogelijk dat een bedrijf of vestiging de aanvraag indient ZONDER een extra contact. In dat geval zal er alleen een Aanvrager/Gemachtigde bij de zaak worden aangemaakt.
De Contactpersoon aanmaken gaat vervolgens als volgt:

- Bij Initiëren en Vooroverleg en Aanvullen. De gegevens uit blok `<contactpersoon>` worden aangevuld of nieuw aangemaakt in de tabel tbcontactadressen (omgevingstegel _Contactadressen_). De relatie tussen het contactadres en de omgevingszaak ligt in de dochtertabel tbomgvergcontactennn op de kaart met dvcodeadressoort = de rol/adressoort die in de beheertabel _Adressoorten/rollen_ aangemerkt is als _Is rol voor contactpersoon uit verzoekbericht DSO_. Zie hierboven bij verplichte instellingen. Bij **Aanvullen** kijkt OpenWave of deze relatie in tbomgvergcontactennn reeds bestaat. Zo ja dan worden de contactgegevens zo mogelijk aangepast in de betrokken adreskaart van tbcontactadressen. Zo nee, - of het gaat om **Initiëren of Vooroverleg** - , dan zal een nieuwe relatie gelegd moeten worden naar een nieuw aan te maken of reeds bestaande adreskaart in OpenWave. OpenWave zoekt of de contactpersoon reeds bestaat in tbcontactadressen op de tag `<emailadres>` (moet dus wel gevuld zijn) EN op de tag `<achternaam>` (moet dus wel gevuld zijn) EN op de eerste positie van de tag `<voorletters>` (moet dus wel gevuld zijn). Indien geen unieke kaart gevonden wordt een nieuwe kaart aangemaakt in tbcontactadressen.

Wat betreft het overnemen/overschrijven van adresgegevens redeneert OpenWave chronologisch als volgt:

- als blok `<afwijkendAdres>` bestaat EN de waarde van tbcontactadressen.dvstraatnaam (postadres) is leeg dan worden de postadresgegevens overschreven met de gegevens uit dit blok
- als blok `<binnenlandsAdres>` bestaat EN de waarde van tbcontactadressen.dvveststraat (vestigingsadres) is leeg dan worden de vestigingsadresgegevens overschreven met de gegevens uit dit blok
- als tbcontactadressen.dvstraatnaam (postadres) nog steeds leeg is overschrijf dan de postadresgegevens met de waardes uit blok `<binnenlandsAdres>`
- als blok `<buitenlandsAdres>` bestaat EN de waarde van tbcontactadressen.dvbuitenladresregel1 is leeg dan worden de buitenlandadresgegevens overschreven met de gegevens uit dit blok.

#### Initiatiefnemer

_Bij Initiëren en Vooroverleg en Aanvullen._

Een BSN-nummer bestaande uit 9 nullen beschouwd OpenWave als leeg.

De gegevens uit blok `<initiatiefnemer>` (in OpenWave is dit de aanvrager) worden aangevuld of nieuw aangemaakt in de tabel tbcontactadressen (omgevingstegel _Contactadressen_). De relatie tussen het contactadres en de omgevingszaak ligt in de dochtertabel tbomgvergcontactennn op de kaart met dvcodeadressoort = AVR (zie hierboven bij verplichte instellingen). Bij **Aanvullen** kijkt OpenWave of deze relatie in tbomgvergcontactennn reeds bestaat. Zo ja dan worden de contactgegevens zo mogelijk aangepast in de betrokken adreskaart van tbcontactadressen. Zo nee, - of het gaat om **Initiëren of Vooroverleg** - , dan zal een nieuwe relatie gelegd moeten worden naar een nieuw aan te maken of reeds bestaande adreskaart in OpenWave. OpenWave kijkt in het STAM-bericht naar de aanwezigheid van BSN-nummer, KVK-nummer of vestigingsnummer en zoekt daarmee naar een bestaande (unieke) kaart in tbcontactadressen. Eerst wordt op BSN gezocht (indien meer dan 1 gevonden dan diegene met de hoogste dnkey). Geen (unieke kaart) gevonden, dan wordt op vestigingsnummer gezocht: ook hier geldt indien meer dan 1 gevonden dan diegene met de hoogste dnkey EN waarvoor geldt dat de achternaam LEEG is (achternaam komt namelijk niet mee in het STAM-bericht, er dient dus een leeg contact te zijn voor het bedrijf). Ook hier geen uniek kaart gevonden dan wordt op KvK gezocht (ook hier geldt indien meer dan 1 gevonden dan diegene met de hoogste dnkey EN waarvoor geldt dat de achternaam LEEG is).
Indien geen unieke kaart gevonden wordt, of het gaat om een bedrijf en de achternaam is niet leeg van de contact in OpenWave, dan wordt een nieuwe kaart aangemaakt in tbcontactadressen.

Wat betreft het overnemen/overschrijven van adresgegevens redeneert OpenWave chronologisch als volgt:

- De aanvrager/initiatiefnemer is een natuurlijk persoon (blok: `<natuurlijkPersoon>`):
  - als blok `<correspondentieAdres>` `<afwijkendAdres>` bestaat dan vanuit blok `<afwijkendAdres>` de postadresgegevens overnemen (indien dit een Postbusnummer betreft EN instelling _Sectie: KoppelingNHR, Item: PostbusnrInHuisnr_ is aangevinkt dan wordt als straatnaam 'Postbus' gezet en als huisnummer het postbusnummer)
  - als blok `<correspondentieAdres>` `<binnenlandsAdres>` bestaat dan vanuit blok `<binnenlandsAdres>` de postadresgegevens overnemen
  - als blok `<correspondentieAdres>` `<buitenlandsAdres>` bestaat dan uit blok `<buitenlandsAdres>` de buitenlandse adresgegevens overnemen
  - als blok `<verblijfsadres>` bestaat dan uit blok < verblijfsadres> de vestigingsadresgegevens overnemen
  - als blok `<verblijfsadresBuitenland>` bestaat EN tbcontactadressen.dvbuitenladresregel1 is null dan uit blok `<verblijfsadresBuitenland>` de buitenlandse adresgegevens overnemen.
- De aanvrager/initiatiefnemer is een niet natuurlijk persoon (blok: `<NietNatuurlijkPersoon>`):
  - als blok `<postAdres>` `<afwijkendAdres>` bestaat dan uit blok `<afwijkendAdres>` de postadresgegevens overnemen (indien dit een Postbusnummer betreft EN instelling _Sectie: KoppelingNHR, Item: PostbusnrInHuisnr_ is aangevinkt dan wordt als straatnaam 'Postbus' gezet en als huisnummer het postbusnummer)
  - als blok `<postAdres>` `<binnenlandsAdres>` bestaat dan vanuit blok `<binnenlandsAdres>` de postadresgegevens overnemen
  - als blok `<postAdres>` `<buitenlandsAdres>` bestaat dan uit blok `<buitenlandsAdres>` de buitenlandse adresgegevens overnemen
  - als blok`<bezoekadres>`bestaat dan uit blok < bezoekadres> de vestigingsadresgegevens overnemen
  - als blok`<bezoekadresBuitenland>`bestaat EN tbcontactadressen.dvbuitenladresregel1 is null dan uit blok`<bezoekadresBuitenland>`de buitenlandse adresgegevens overnemen
  - als blok `<vestiging>` `<postAdres>` `<afwijkendAdres>` bestaat EN `<adrestype>` gevuld dan vanuit blok `<afwijkendAdres>` de postadresgegevens overschrijven
  - als blok `<vestiging>` `<postAdres>` `<binnenlandsAdres>` bestaat EN `<straatnaam>` gevuld dan vanuit blok `<binnenlandsAdres>` de postadresgegevens overschrijven
  - als blok `<vestiging>` `<postAdres>` `<buitenlandsAdres>` bestaat EN `<adresBuitenland1>` gevuld dan uit blok `<buitenlandsAdres>` de buitenlandse adresgegevens overnemen
  - als blok `<vestiging>` `<locatieAdresVestiging>` bestaat EN `<straatnaam>` gevuld bestaat dan uit blok `<locatieAdresVestiging>` de vestigingsadresgegevens overnemen
  - als blok `<vestiging>``<locatieAdresBuitenland>`bestaat EN tbcontactadressen.dvbuitenladresregel1 is leeg dan uit blok`<locatieAdresBuitenland>`de buitenlandse adresgegevens overnemen.

Indien de instelling _Sectie: DSO-Verzoekafhandelen en Item: OntbrekendPostadresVullenMetVestiging_ is aangevinkt en het STAM-bericht bevat geen post- c.q. correspondentieadres bij aanvrager (initiatiefnemer) en/of gemachtigde dan zullen de verblijfs- c.q. vestiging gegevens in OpenWave zowel in het vestigingsadres als in het postadres bij de contactadreskaart worden overgenomen

#### Gemachtigde

_Bij Initiëren en Vooroverleg en Aanvullen._

Een BSN-nummer bestaande uit 9 nullen beschouwd OpenWave als leeg.

De gegevens uit blok `<gemachtigde>` worden aangevuld of nieuw aangemaakt in de tabel tbcontactadressen (omgevingstegel _Contactadressen_). De relatie tussen het contactadres en de omgevingszaak ligt in de dochtertabel tbomgvergcontactennn op de kaart met dvcodeadressoort = GEM (zie hierboven bij verplichte instellingen). Bij **Aanvullen** kijkt OpenWave of deze relatie in tbomgvergcontactennn reeds bestaat. Zo ja dan worden de contactgegevens zo mogelijk aangepast in de betrokken adreskaart van tbcontactadressen. Zo nee, - of het gaat om **Initiëren of Vooroverleg** - , dan zal een nieuwe relatie gelegd moeten worden naar een nieuw aan te maken of reeds bestaande adreskaart in OpenWave. OpenWave kijkt in het STAM-bericht naar de aanwezigheid van BSN-nummer, KVK-nummer of vestigingsnummer en zoekt daarmee naar een bestaande (unieke) kaart in tbcontactadressen. Eerst wordt op BSN gezocht (indien meer dan 1 gevonden dan diegene met de hoogste dnkey). Geen (unieke kaart) gevonden, dan wordt op vestigingsnummer gezocht: ook hier geldt indien meer dan 1 gevonden dan diegene met de hoogste dnkey EN waarvoor geldt dat de achternaam LEEG is (achternaam komt namelijk niet mee in het STAM-bericht, er dient dus een leeg contact te zijn voor het bedrijf). Ook hier geen uniek kaart gevonden dan wordt op KvK gezocht (ook hier geldt indien meer dan 1 gevonden dan diegene met de hoogste dnkey EN waarvoor geldt dat de achternaam LEEG is).
Indien geen unieke kaart gevonden wordt, of het gaat om een bedrijf en de achternaam is niet leeg van de contact in OpenWave, dan wordt een nieuwe kaart aangemaakt in tbcontactadressen.

Wat betreft het overnemen/overschrijven van adresgegevens redeneert OpenWave hetzelfde als hierboven beschreven bij de initiatiefnemer.

#### Activiteiten

_Bij Initiëren en Vooroverleg en Aanvullen en Intrekken._

De gegevens uit het blok `<projectactiviteiten>` worden opgenomen in de dochtertabel tbtoestemmingen bij de omgevingszaak (omgevingstegel _Onderdelen/Activiteiten_). Per blok `<projectactiviteit>` wordt op grond van de tag `<activiteitNaam>` gezocht of deze voorkomt in de tabel tbsrttoestemming (beheertegel _Soort Activiteit/Onderdeel_) bij de niet-vervallen kaarten. Zo nee dan wordt aldaar een nieuw record aangemaakt met de activiteitsnaam. Zo ja, en er is precies één of er zijn meerderere kandidaten dan wordt degene met de laagste (oudste) primary key genomen: in het geval van meerdere kandidaten krijgen de overige kandidaten een vervaldatum.

De primary key van de gevonden of zojuist aangemaakte kaart in tbsrttoestemming wordt in combinatie met de primary key van de omgevingszaak opgezocht in tbtoestemmingen.dnkeyomgvergunningen en tbtoestemmingen.dnkeysrttoestemming. Indien NIET gevonden dan wordt een nieuwe kaart aangemaakt in tbtoestemmingen. De projectactiviteit is hiermee gekoppeld aan de omgevingszaak. De unieke DSO activiteit-id's, waarin ook een bevoegd gezag code is opgenomen, alsmede de onderliggende subactiviteitsnaam (indien van toepassing) worden bij de activiteit van de omgevingszaak overgenomen.

#### Specificaties (vragen en antwoorden per activiteit)

Bij Initiëren en Vooroverleg en Aanvullen en Intrekken. De gegevens uit het blok `<projectactiviteit>` `<specificaties>` worden opgenomen in de dochtertabel tbdsospecificaties bij de activiteit (tbtoestemmingen) (omgevingstegel _Onderdelen/Activiteiten_: lijst in het detailscherm van activiteit). Per blok`<specificatie>`wordt op grond van de tag `<vraagId>` en de primary key in tbtoestemmingen van de activiteit gezocht of deze combinatie voorkomt in de tabel tbdsospecificates (dvdsovraagid en dnkeytoestemmingen).

Zo nee dan wordt aldaar een nieuw record aangemaakt met de vraag en antwoord gegevens.

Zo ja (doel = aanvullen) en het antwoord op de vraag wijkt af van het reeds opgeslagen antwoord, dan wordt de kolom volgnr gevuld met het volgnummer van de aanvulling en het nieuwe antwoord in de kolom dvdsoantwoord geplaatst en - indien tag`<oorsprantwoord>`gevuld - de kolom dvdsooorsprantwoord overschreven met de tag`<oorsprantwoord>`uit het bericht.

#### Mapping antwoorden uit specificaties op grond van vraagid

In de beheertabel achter de tegel _Acties op DSO-SpecVraagids_ kan ingesteld worden hoe een antwoord op een bepaalde vraagid doorgezet kan worden naar andere kolommen van de OpenWave database. Een voorbeeld met betrekking tot het plaatsen van de bouwkosten in tbtoestemmingen (activiteiten/onderdelen) in de kolom opgegeven bouwkosten (dflegesopgbasis):

Er zijn twee vraagid's (en misschien nog wel meer) die naar de bouwkosten vragen namelijk:

- 284856 indien de specificatie hoort bij activiteit _Bouwactiviteit (omgevingsplan)_ en
  - 368212 indien de specificatie hoort bij activiteit _Bouwactiviteit (technisch)_.

Beide vallen onder aanvraagtype _Aanvraag vergunning_, belangrijk, want eenzelfde vraagomschrijving bij eenzelfde activiteit kan per aanvraagtype een andere vraagid opleveren.
In de tabel (tbdsospecvraagid) moeten dus 2 kaarten worden aangemaakt met de genoemde vraagid's (dvdsovraagid). Hoewel de omschrijving vrij staat is het belangrijk zo goed mogelijk het verschil aan te geven in de kolom dvomschrijving.
In beide gevallen is het de bedoeling dat de kolom dflegesopgbasis van de tabel tbtoestemmingen moet worden gevuld: de kolom _ga naar tabel_ (dvganaartabelnaam) moet daarom gevuld worden met tbtoestemmingen.

Nu moet het programma weten bij welke dnkey van tbtoestemmingen de aanpassing moet gebeuren: de kolom _select statement_ (dvsqlprimkeyganaartabel) moet gevuld worden met een valide SQL select statement. In bovenstaande gevallen _select dnkeytoestemmingen from tbdsospecificaties where dnkey = %keypointer%_. De variabele*%keypointer%* wordt daarbij on the fly vervangen door de dnkey uit de tabel tbdsospecificaties die hoort bij de betreffende vraagid.

Nu moet OpenWave weten welke kolom(men) van tbtoestemmingen moeten worden vervangen. Er zijn vier mogelijkheden. In dit voorbeeld wordt alleen de eerste (dvedit1kolomnaam) gevuld met de gewenste kolomnaam uit tbtoestemmingen: _dflegesopgbasis_.

Tot slot moet aangegeven worden in de kolom _dvedit1waarde_ met welke waarde tbtoestemmingen.dflegesopgbasis moet worden vervangen. In _dvedit1waarde_ zal de string _%dvdsoantwoord%_ on the fly worden vervangen met het antwoord op de vraag uit het DSO STAM-bericht. Aangezien dit een characterstring is moet de beheerder zelf aangeven hoe deze string geconverteerd moet worden om in het floatfield dflegesopgbasis te passen, namelijk _replace(%dvdsoantwoord%,chr(44),'.')::float_ (de eventuele komma in het antwoord wordt eerst omgezet naar een decimale punt, en dat resultaat wordt als float opgeslagen).

Als het antwoord in een stringveld terecht moet komen dan is bijvoorbeeld %dvdsoantwoord%, maar ook substr(%dvdsoantwoord%,2,5) valide. Indien een vaste waarde (dus niet gebaseerd op het antwoord) dan moet deze geplaatst worden tussen enkele aanhalingstekens indien de kolom die vervangen moet worden een stringveld of datumveld is. Bij type float of integer geen aanhalingstekens.

**Ander voorbeeld**:

De provincie Noord-Holland heeft als extra vraag in het DSO-verzoek toegevoegd: _Aan welke weg gaat u activiteiten uitvoeren?_
Het antwoord kan niet anders dan een wegnummer bevatten._
De vraagid voor deze vraag in het DSO-verzoek = 380711._
Het is de bedoeling dat het antwoord met het wegnummer terechtkomt in tbzaakkadperc (de projectlocaties) en dat de betreffende kaart in tbzaakkadperc gelijk de status hoofdprojectlocatie krijgt.
In de tabel tbdsospecvraagid moet een kaart aangemaakt worden met _vraagid_ = 380711. De kolom _ga naar tabel_ met gevuld worden met tbzaakkadperc.

Bij de verwerking van een DSO-verzoek wordt altijd een kaart aangemaakt in tbzaakkadperc met de projectlocatie. Dit is al gebeurd voordat de specificaties worden behandeld. Het _select statement primary key van ga-naar-tabel_ om deze kaar te vinden wordt dan:

```sql
select dnkey from tbzaakkadperc where dnkeyomgvergunningen = (select dnkeyomgvergunningen from tbtoestemmingen where dnkey = (select
  dnkeytoestemmingen from tbdsospecificaties where dnkey = %keypointer%)) limit 1
```

- _Kolomnaam1_ moet gevuld worden met de kolomnaam waar het wegnummer in moet komen: _dvwegnummer_
- _Waarde1_ moet gevuld worden met het antwoord uit het DSO-bericht: _%dvdsoantwoord%_
- _Kolomnaam2_ moet gevuld worden met de kolomnaam van is hoofdprojectlocatie namelijk: _dlhoofdprojectlocatie_
- _Waarde2_ moet gevuld worden met de vaste waarde T (dlhoofdprojectlocatie is type char-veld dus tussen enkele aanhalingstekens) _'T'_.

#### Opnemen kwaliteitsborger als contactpersoon op grond van specificatie-groepen kwaliteitsborger

Indien

- er een adresrol (beheertegel _Adressoorten_) bestaat waarbij de kolom _Is rol voor kwaliteitsborger uit verzoekbericht DSO_ (dldsorolkwaliteitsborger) is aangevinkt
- EN de instelling _Sectie: DSO en Item: Kwaliteitsborger_ aangevinkt is
- EN er nog geen contactpersoon gekoppeld is aan de aangemaakte omgevingszaak met de ROL kwaliteitsborger

dan onderzoekt OpenWave de specificaties van het STAM-bericht op groepen waarin de tekst kwaliteitsborger voorkomt. De - ongestructureerde - antwoorden van de vraagid's:

- 366941 en 365921 zal OpenWave interpreteren als een KvK-nummer
- 366940 en 365920 als bedrijfsnaam
- 365923 en 366943 als een postadres (waarin straat huisnummer, woonplaats ongestructureerd voorkomen)
- 366938 en 365912 als een achternaam (waarbij voorletters, tussenvoegsel en naam ongestructureerd voorkomen)
- 365919 en 366946 als telefoon van de kwaliteitsborger
- 366944 en 365916 als email van de kwaliteitsborger.

OpenWave gaat als volgt te werk:

- OpenWave onderzoekt is of in de kaartenbak contactadressen de betreffende kwaliteitsborger al voorkomt. Dat gebeurt op de twijfelachtige combinatie KvK-nummer en Email. Indien precies één kaart gevonden dan wordt deze contactpersoon ook gekoppeld aan de aangemaakte omgevingszaak met de rol kwaliteitsborger.
- Geen bestaand contact gevonden of meerder mogelijkheden: dan maakt OpenWave een nieuwe contactadreskaart aan op grond van de ongestructureerde antwoorden, waarbij op voorhand al uitgesloten kan worden dat de kolommen _Postadres_ en _Achternaam_ juist worden gevuld. Er is dus altijd werk aan de winkel voor een mens om het contactadres goed te krijgen.

### Gevraagde bijlages per specificatie

Bij Initiëren en Vooroverleg en Aanvullen en Intrekken.

De gegevens uit de blokken `<projectactiviteit>` `<specificaties>` `<gevraagdeBijlage>` worden opgenomen in de dochtertabel tbdsogevrbijlages bij de specificatie (tbdsospecificaties) (omgevingstegel _Onderdelen/Activiteiten_: lijst in het detailscherm van specificatie bij activiteit).

Per blok `<gevraagdeBijlage>` wordt op grond van de tag `<documentsoortDSO>` en de primary key in tbdsospecificaties van het betrokken vraag/antwoord gezocht of deze combinatie voorkomt in de tabel tbdsogevrbijlages (dvdsodocumentsoort en dnkeydsospecificaties). Zo nee dan wordt aldaar een nieuw record aangemaakt met de gevraagde bijlage gegevens.

### Documenten per gevraagde bijlage per specificatie

Bij Initiëren en Vooroverleg en Aanvullen en Intrekken.

De gegevens uit de blokken `<projectactiviteit>` `<specificaties>` `<gevraagdeBijlage>` `<documenten>` worden opgenomen in de dochtertabel tbomgoloberichten bij de gevraagde bijlage (tbdsogevrbijlages) (omgevingstegel _Onderdelen/Activiteiten_: lijst in het detailscherm van gevraagde bijlages bij specificatie).

Per blok `<document>` wordt op grond van de tag `<documentId>` en de primary key in tbdsogevrbijlages van de betrokken gevraagde bijlage gezocht of deze combinatie voorkomt in de tabel tbomgoloberichten (dvolomessageid en dnkeydsogevrgbijage). Zo nee dan wordt aldaar een nieuw record aangemaakt met de documentgegevens en - indien het om een aanvulling/intrekking gaat - ook het DSO-verzoek-volgnummer.

Wanneer een nieuwe kaart wordt aangemaakt in tbomgoloberichten wordt naast de dnkeydsogevrgbijage ook de dnkeyomgvergunningen gevuld zodat de documentkaarten ook rechtstreeks te zien zijn vanaf de omgevingstegel _OLO/AIMberichten_.

Indien een aanvulling wordt verwerkt kan het zijn dat eerdere documenten zijn vervangen door andere of zelfs helemaal niet meer opgenomen zijn in het aanvullingsbericht. Deze documenten worden in de tabel tbomgoloberichten voorzien van een vervaldatum (datum dat aanvulling is binnengekomen). Indien deze vervallen documenten ook een registratie hebben in de tabel tbcorrespondentie (geregistreerde documenten) wordt ook daar een vervaldatum toegekend.

### Documenten verzoekbijlages

Bij Initiëren en Vooroverleg en Aanvullen en Intrekken.

De gegevens uit het blok `<verzoekbijlages>` (gevraagde bijlages die niet direct aan een specificatie zijn te linken) worden ook opgenomen in de tabel tbomgoloberichten, maar dan zonder connectie naar een specificatie.

Per blok `<document>` wordt op grond van de tag `<documentId>` van de betrokken verzoekbijlage gezocht of deze reeds voorkomt in de tabel tbomgoloberichten (dvolomessageid met een lege dnkeydsogevrgbijage). Zo nee dan wordt aldaar een nieuw record aangemaakt met de documentgegevens en - indien het om een aanvulling/intrekking gaat - ook het DSO-verzoek-volgnummer.

Wanneer een nieuwe kaart wordt aangemaakt in tbomgoloberichten wordt naast de dnkeydsogevrgbijage ook de dnkeyomgvergunningen gevuld zodat de documentkaarten ook rechtstreeks te zien zijn vanaf de omgevingstegel _OLO/AIMberichten_.

Indien een aanvulling wordt verwerkt kan het zijn dat eerdere documenten zijn vervangen door andere of zelfs helemaal niet meer opgenomen zijn in het aanvullingsbericht. Deze documenten worden in de tabel tbomgoloberichten voorzien van een vervaldatum (datum dat aanvulling is binnengekomen). Indien deze vervallen documenten ook een registratie hebben in de tabel tbcorrespondentie (geregistreerde documenten) wordt ook daar een vervaldatum toegekend.

### Negeren van binnenkomende kopieberichten in kader afhandelen complexe verzoeken in samenwerkingsverband

Bij het verwerken van STAM-bericht wordt eerst deze voorcheck gedaan: Indien

- Er nog geen kaart bestaat in tbomgvergunning met Dvlvoaanvraagnr = Verzoeknummer
- EN in het STAM-bericht is het OIN-nummer van de uitvoerendeInstantie gevuld
- EN dat OIN-nummer is ongelijk aan de kolom _Tekst_ van instelling _Sectie: SWF en Item: OINvanZender_ (dit is de OIN van de host: de hoofdorganisatie die OpenWave gebruikt)
- EN de instelling _Sectie: DSO en Item: KopieberichtenOpslaan_ is **NIET** aangevinkt is (of bestaat niet)

Dan gaat het om een kopiebericht dat moet worden genegeerd. In de messagelog wordt het bericht wel opgenomen met de reden waarom genegeerd.

Indien het kopiebericht toch moet worden opgeslagen (de instelling _Sectie: DSO en Item: KopieberichtenOpslaan_ is **WEL** aangevinkt, dan krijgt het verzoeknummer de postfix `_KCV`.
![DSO zwarte gaten en kopieberichten](/img/applicatiebeheer/probleemoplossing/programmablokken/dsozwartegatenenkopieberichten.png.md){class="media" loading="lazy" width="800" }

## Vervolgacties na verwerken verzoekbericht

Alleen bij Initiëren en Vooroverleg (indien Aanvullen dan vervolgactie DSO ontvangstbevestiging sturen mogelijk).

### Ophalen processtappen

Het zaaktype van de omgevingskaart kan gekoppeld zijn aan één of meer processen. De bijbehorende processtappen worden automatisch aan de nieuwe zaak toegevoegd indien het attribuut _automatisch_ bij die koppelingen aangevinkt is (beheertegel _Zaaktypes omgeving_. Detailscherm bij zaaktype en daarbinnen lijst gekoppelde processen).

### Ophalen checklijsten

Het zaaktype van de omgevingskaart kan gekoppeld zijn aan processen die automatisch aan de nieuwe zaak kunnen worden toegevoegd (zie hierboven). Indien aan een automatisch toegevoegd proces één of meer checklijsten zijn verbonden die ook de eigenschap _automatisch toevoegen_ hebben (tbkopproccheck.dlauto = 'T'), dan worden deze checklijsten automatisch toegevoegd bij de zaak.

### Automatisch aanmaken zaak in extern zaak/DMS

Dit is het geval indien:

- er GEEN sprake is van een compartiment EN de instelling _Koppeling ZAAK_ en _Item: AutoZaakDmsOmgeving_ is aangevinkt
- er WEL sprake is van een compartiment dan EN de kolom dlAutoZaakDmsOmgeving is aangevinkt bij het betreffende compartiment (beheerportaal-Nieuw).

Zie voor overige verplichte instellingen voor aanmaken zaak in extern zaak/DMS bij [Creëer zaak zaak/dms](/docs/probleemoplossing/programmablokken/creeer_zaak_zaak_dms.md).

### Automatisch aanmaken mappen op fileshare

Indien

- de zaak NIET valt onder een compartiment:
  - de instelling _Sectie: Documenten Item: OphalenViaFileserver_ aangevinkt is
  - EN de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is

OF indien

- de zaak WEL valt onder een compartiment:
  - de kolom _ophalen via fileserver_ op de detailkaart van het betreffende compartiment is aangevinkt
  - EN de kolom _Automatisch aanmaken mappen_ (dlautoaanmaakmappen) aangevinkt is bij het betreffende compartiment

dan zullen bij het aanmaken van een nieuwe zaak automatisch de omgeving_mappen genoemd in de rijen van _Sectie: Aanmaakmappen_ worden aangemaakt waarbij er een '4' voorkomt in _Getal1_ (dus indien _Getal1_ de waarde 25 heeft dan niet, indien bijv. 4 of 124 dan wel). Hierbij uitgezonderd zijn de mappen waarin de variabelen `%adviesnr%` , `%bezwaarnr%` en `%inspnr%` zijn opgenomen.
Indien OpenWave in de Cloud draait, dan moet wel de [satellite](/docs/instellen_inrichten/satellite_filesysteem.md) geïnstalleerd zijn.

### Automatisch vullen van kolom dvhyperlink

Zie: [Hyperlink](/docs/instellen_inrichten/hyperlink.md).

### Automatisch sturen van DSO Ontvangstbevestiging

Dit is het geval indien:

- instelling _Sectie: DSO en Item: OntvangstBevestAutoVersturen_ aan is gevinkt
- doel van DSO STAM-bericht Initiëren, Vooroverleg, Conceptverzoek of Aanvullen is (dus niet bij Intrekken)

Zie voor overige verplichte instellingen voor automatisch versturen van DSO ontvangstbevestiging bij
[DSO Ontvangstbevestiging sturen](/docs/probleemoplossing/programmablokken/dso_ontvangstbevestiging.md).
