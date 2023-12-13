# Zoekportaal

Wordt aangeroepen door de action: OpenTabPage(#zoeken).

Dit portaal is bedoeld voor tegels die zoekwizards starten, waarmee een bepaalde zaak of inrichting gevonden kan worden. De hieronder besproken zoektegels kunnen ook op andere portalen worden geplaatst, waarbij de _action_ hetzelfde blijft.

## Problemen

### Het scherm ziet er raar uit (al of niet met foutmelding) of reageert niet

- er zijn geen tegels gedefinieerd onder portalname _Zoeken_ (Zie [Portal Definitie](../../instellen_inrichten/portaldefinitie/README.md))
- alle tegels zijn disabled of onzichtbaar of onzichtbaar_op_conditie
- geen enkele tegel uit dit portal is toegekend aan een inlogger.

### Het opschrift op een of meer tegels is niet zichtbaar

- ontbreken vaste tekst bij definitie portaltegel
- OF fout in dynamische queryverwijzing bij tegeldefinitie
  - indien foutieve queryverwijzing blijft tegel leeg
  - indien query zelf niet correct is, blijft tegel leeg
  - indien inlogger geen recht heeft om query uit te voeren blijft de tegel ook leeg.

## Zoektegels onder kolom Hoofdzaken

### Zoeken via zaaknummers

De tegeldefinitie is als volgt:

- Kopregel:
- Vast Opschrift: _zoeken via zaaknummers_
- Dynamisch tegelopschrift:
- Actie:
  - \*startWizard(ZoekZaakViaZaaknummer,**\*1**)) door die parameter 1 blijft het laatste scherm van de zoekwizard (met de zaken die aan de criteria voldoen) open staan nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent
  - OF _startWizard(ZoekZaakViaZaaknummer)_ het zoekwizardscherm wordt gesloten nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent.

De gebruiker tikt een reeks karakters in waar het programma een puntkomma voor plakt. Vervolgens kijkt het programma of deze reeks voorkomt in de aan elkaar geplakte kolommen dvzaakcode, dvolonummer, dvdmszaakcode, dvintzaakcode en dvzaaknrbevgezag (voorafgegaan en gescheiden door een puntkomma) van _vwfrmalleaanvragen_.
Het programma maakt geen onderscheid in hoofd/kleine letters en houdt rekening met de kijkrechten op de modules en de kijkrechten op alleen gemeentes (tabel tbmedewerkers).

### Zoeken via adres

De tegeldefinitie is als volgt:

- Kopregel:
- Vast Opschrift: _zoeken via adres_
- Dynamisch tegelopschrift:
- Actie:
  - \*startWizard(ZoekZaakViaAdres,**\*1**) door die parameter 1 blijft het laatste scherm van de zoekwizard (met de zaken die aan de criteria voldoen) open staan nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent
  - OF _startWizard(ZoekZaakViaAdres)_ het zoekwizardscherm wordt gesloten nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent.

De gebruiker wijst gemeente (het programma houdt al rekening met de kijkrechten op alleen gemeentes), woonplaats en straat aan en - niet verplicht - geeft het domein van huisnummers in. Vervolgens filtert het programma de rijen die voldoen aan deze criteria uit _vwfrmalleaanvragen_.
Het programma houdt rekening met de kijkrechten op de modules en de kijkrechten op alleen gemeentes (tabel tbmedewerkers).

### Zoeken via betreft

De tegeldefinitie is als volgt:

- Kopregel:
- Vast Opschrift: _zoeken via betreft_
- Dynamisch tegelopschrift:
- Actie:
  - \*startWizard(ZoekZaakViaBetreftDatum,**\*1**) door die parameter 1 blijft het laatste scherm van de zoekwizard (met de zaken die aan de criteria voldoen) open staan nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent
  - OF _startWizard(ZoekZaakViaBetreftDatum)_ het zoekwizardscherm wordt gesloten nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent.

De gebruiker wijst module aan en tikt een aantal 'betreft' karakters in en - niet verplicht - een datumdomein. Vervolgens filtert het programma de rijen die voldoen aan deze criteria uit _vwfrmalleaanvragen_, waarbij de ingetikte karakterreeks moet voorkomen in de kolom dvbetreft. Het datumdomein wordt vergeleken met de kolom ddaanvraag.
Het programma maakt geen onderscheid in hoofd/kleine letters en houdt rekening met de kijkrechten op de modules en de kijkrechten op alleen gemeentes (tabel tbmedewerkers).

### Zoeken via contact

De tegeldefinitie is als volgt:

- Kopregel:
- Vast Opschrift: _zoeken via contact_
- Dynamisch tegelopschrift:
- Actie:
  - \*startWizard(ZoekZaakViaContact,**\*1**) door die parameter 1 blijft het laatste scherm van de zoekwizard (met de zaken die aan de criteria voldoen) open staan nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent
  - OF _startWizard(ZoekZaakViaContact)_ het zoekwizardscherm wordt gesloten nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent.

De gebruiker geeft al of niet met wildcards een selectie aan op contactadresgegevens. Het programma toont een vervolgens een doorkieslijst van personen/bedrijven uit tbcontactadressen die aan de criteria voldoen. Het programma maakt geen onderscheid in hoofd/kleine letters en negeert diakritische tekens bij de kolommen achternaam en bedrijfsnaam. De gebruiker kies vervolgens een of meer rijen uit de contactenlijst en kan daarna (niet verplicht) module en datumdomein opgeven.
Vervolgens filtert het programma de rijen uit vwfrmalleaanvragen op zaken die een koppeling hebben met een of meer van de de gekozen contacten. Het datumdomein wordt vergeleken met de kolom ddaanvraag. Het programma houdt rekening met de kijkrechten op de modules en de kijkrechten op alleen gemeentes (tabel tbmedewerkers).

### Zoeken via perceelinfo (projectlocaties

De tegeldefinitie is als volgt:

- Kopregel:
- Vast Opschrift: _Zoeken via perceelinfo; (project;locaties)_
- Dynamisch tegelopschrift:
- Actie: _startWizard(ZoekZaakViaPerceelinfo,1)_

De gebruiker wijst hier een kadastrale gemeentecode, kadastrale sectie en kadastrale perceelnummer aan. De drie attributen worden als keuzelijstjes weergegeven waarbij als eerst kadastrale gemeentecode gekozen dient te worden alvorens de keuzeopties voor kadastrale sectie respectievelijk kadastrale perceelnummer worden opgehaald.

Indien gewenst kan men ook de drie zoekwaardes leeglaten, alleen op kadastrale gemeentecode zoeken, OF alleen op de combinatie gemeentecode en sectie.

**Let op**: deze functie is bedoelt om omgeving en handhavingzaken te kunnen opzoeken op basis van bij die zaken opgeslagen kadastrale percelen/projectlocaties (tbzaakkadperc). De opties in de dropdown keuzelijstjes van de invoerwaardes komen dus 1 op 1 overeen met de waardes in kadastrale percelen/projectlocaties bij zaken (dus in tabel tbzaakkadperc) voor deze drie attributen. Het programma houdt rekening met de kijkrechten op de zaakmodules Omgeving en Handhaving: alleen voor deze zaakmodules zijn kadastrale percelen/projectlocaties van toepassing.

Een voorbeeld:
Stel men kies als zoekwaarde voor kadastrale gemeente code ‘EDE01’ dan zal men bij kadastrale sectie alleen kunnen kiezen uit waardes zoals deze in tbzaakkadperc voorkomen waar de gemeentecode ‘EDE01’ is.

Na kiezen van de zoekwaardes (of deze eventueel niet vullen) zal bij klikken op volgende een lijstscherm getoond worden met hierin het zoekresultaat. In deze lijst kan men met behulp van de zoekbalk onderin het scherm, de zoekopdracht desgewenst verfijnen. Dubbelklik op een regel in de resultaatlijst geeft het openen van het zaakportaal van de geselecteerde zaak.

## Zoektegels onder kolom Inrichting

### Zoeken via nummer/naam

De tegeldefinitie is als volgt:

- Kopregel:
- Vast Opschrift: _Zoeken via naam/nummer_
- Dynamisch tegelopschrift:
- Actie:
  - \*startWizard(zoekInrichtingopNaam,**\*1**) door die parameter 1 blijft het laatste scherm van de zoekwizard (met de zaken die aan de criteria voldoen) open staan nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent
  - OF _startWizard(zoekInrichtingopNaam)_ het zoekwizardscherm wordt gesloten nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent.

De gebruiker geeft een selectie op inrichtingsgegevens. Vervolgens filtert het programma de rijen die voldoen aan deze criteria uit _vwfrmmilinrichtingen_, waarbij geen onderscheid wordt gemaakt in hoofd/kleine letters en diakritische tekens worden genegeerd bij de inrichtingsnaam.
Het programma houdt rekening met de kijkrechten op de module inrichtingen en de kijkrechten op alleen gemeentes (tabel tbmedewerkers).

## Zoektegels onder kolom Inspecties

### Zoeken op zaaknummer

De tegeldefinitie is als volgt:

- Kopregel:
- Vast Opschrift: _zoeken op zaaknummer_
- Dynamisch tegelopschrift:
- Actie:
  - \*startWizard(ZoekInspectieViaZaaknummer,**\*1**)) door die parameter 1 blijft het laatste scherm van de zoekwizard (met de zaken die aan de criteria voldoen) open staan nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent
  - OF _startWizard(ZoekInspectieViaZaaknummer)_ het zoekwizardscherm wordt gesloten nadat de gebruiker een keuze heeft gemaakt en het gekozen zaakportaal opent.

De gebruiker tikt een reeks karakters in waar het programma een puntkomma voor plakt. Vervolgens kijkt het programma of deze reeks voorkomt in de aan elkaar geplakte kolommen dvwaveinspectiezaakcode, dvintzaakcode (voorafgegaan en gescheiden door een puntkomma) van _vwfrminspecties_.
Het programma maakt geen onderscheid in hoofd/kleine letters en houdt rekening met de kijkrechten op de modules en de kijkrechten op alleen gemeentes (tabel tbmedewerkers).
