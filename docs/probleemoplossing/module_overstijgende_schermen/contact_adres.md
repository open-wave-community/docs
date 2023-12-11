# Contactadres

## Scherm bepaalt welke kolommen zichtbaar en welke kolommen sowieso niet editable

De schermidentifier is indien

* Bij de rechtengroep van de inlogger de kolom *Is Groep voor publiek (tbrechten.dlaispubliekgroep)* aangevinkt is dan wordt het scherm  MDDC_geefContactDetail_publiek.xml (zeer beperkte set aan niet te muteren data) geopend.
* Anders kijkt OpenWave naar de kolom *Mag contactadres alleen wijzigen via beperkt scherm MDDC_geefContactBeperktDetail.xml  (tbmedewerkers.dleditcontactmetafwscherm)* op de medewerkerskaart van de inlogger. Indien:
  * Aangevinkt, dan wordt het scherm MDDC_geefContactBeperktDetail.xml geopend, waarin op dit moment alleen de emailkolom en de twee kolommen met telefoonnummers editable zijn.
  * Niet aangevinkt dan geldt de oude situatie en wordt het scherm MDDC_geefContactDetail.xml geopend. Qua wijzigrechten voor dit scherm wordt gekeken naar tbrechten.dldcadedt

Alle drie mogelijke schermen geven detailgegevens over de tabel tbcontactadressen, waarbij het publiekscherm alleen
de niet muteerbare kolommen persoonsnaam, bedrijfsnaam en geslacht toont.

De andere twee schermen zijn identiek, maar verschillen vooral in het editable zijn van de kolommen.

De beschrijving hieronder geldt de normale situatie: MDDC_geefContactDetail.xml

Kan worden aangeroepen vanuit de lijsten Contactpersonen bij een zaak (tegels *Contacten* op de zaakportalen en inrichtingsportaal) en vanuit de lijst met alle contacten vanuit de tegel *Adresboek* op het openingsportaal en vanuit de lijst contactpersonen op het detailscherm van bezwaar/beroep.

### Error

Het scherm geeft een foutmelding indien:

* er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
* de inlogger behoort tot een rechtengroep die geen kijkrechten heeft op contactadressen (contactadressen zichtbaar bij hoofdrechtengroep).

### Filteropties

De filteropties  (de lijst kan nu onder meer gefilterd worden op combinaties van achternaam, bedrijfsnaam , vestigingsplaats en postadresplaats en dnkey, email en BSN) zijn alleen zichtbaar indien de lijst gestart wordt vanuit de tegel *Adresboek* op het openingsportaal (beter gezegd: vanuit de actionaanroep *getFlexList(tbcontactadressen)*, waarbij de inlogger het recht tbrechten.dlaispubliekgroep NIET aangevinkt heeft staan.

De filter is gedefinieerd in MDFC_geefContactenOverzicht_alles.xml waarbij de invoervelden voor bedrijfsnaam, achternaam, vestigingsadres en postadres met de operator LIKE zijn gedefinieerd, hetgeen betekent dat indien de gebruiker als zoekwaarde bij bijv. achternaam

* *jansen* invoert, openwave zoekt op  dvachternaam = jansen
* *jansen%* invoert, openwave zoekt op  dvachternaam begint met jansen
* *%jansen* invoert, openwave zoekt op  dvachternaam eindigt op jansen
* *%jansen%* invoert, openwave zoekt op de substring jansen in dvachternaam

LET OP: OpenWave regelt dat het zoeken NIET CASE SENSITIVE gebeurt

### Muteren

De kolommen van de tabel tbcontactadressen kunnen gemuteerd worden indien:

* de inlogger behoort tot een rechtengroep die wijzigrechten heeft op contactadressen (hoofdrechtengroep)
* EN de editschuif aan staat.

De volgende kolommen zijn niet muteerbaar:

* dddatummutatie. Wordt automatisch gevuld bij wijziging
* ddcontrolegba. Wordt automatisch gevuld bij succesvolle uitwisseling via trigger ophalen BRP
* ddcontrolenhr. Wordt automatisch gevuld bij succesvolle uitwisseling via trigger ophalen NHR
* dnkey (ID OpenWave)
* dvnpnanp. Wordt automatisch gevuld met trigger genereerNpnAnp.

De volgende kolommen hebben een extra input controle bij handmatige invoer:

* bsn (dvsofinummer) moet voldoen aan de elfproef en bestaan uit 8 of 9 karakters
* dvvestigingsnr moet bestaan uit 12 karakters
* kvk-nr (dvbin) moet bestaan uit 8 karakters
* dvbriefaanhef wordt automatisch overschreven op grond van wijziging in geslacht, achternaam en voorvoegsel en gebruiksnaam. Default is dat Geachte heer, mevrouw, heer/mevrouw gevolgd door ofwel *tussenvoegsel en achternaam* dan wel *gebruiksnaam*. Het woord 'Geachte' kan vervangen worden door de inhoud van de kolom *Tekst* van de instelling *Sectie: Programma* en *Item: AanhefContactpersonen*.

### Triggers knoppen in scherm

* **Genereer NpnApn-nummer**. Deze schermknop is alleen zichtbaar indien ook de achternaam van de persoon is ingevuld. De knop roept een wizard aan die op grond van een gemeente-id een 17 cijferige  - voor OpenWave - uniek volgnummer genereert, dat gebruikt wordt bij stuf zaak/DMS koppeling indien bij aanvrager of gemachtigde als Natuurlijk Persoon het BSN-nummer ontbreekt (en ook de instelling *Sectie KoppelingZAAK Item: DefaultBSN* ontbreekt of leeg is).
* **Maak email** (achter de kolom email). Is altijd zichtbaar maar alleen enabled indien de kolom *dvemail* gevuld is. OpenWave construeert een URL met 'MAILTO:' gevolgd door het emailadres, waarna het besturingssysteem bij juiste instellingen het lokale emailprogramma zal openen met het bewuste emailadres als ontvanger en de inlogger als afzender.
* Bij ms-windows zal het protocol mailto in het configuratiescherm *\Standaardprogramma’s\Koppelingen_instellen_voor_ bestandstypes/protocollen* ingesteld moeten staan op het gebruikte emailprogramma.
* **Overname postadres in vestigingsadres** (achter de kolom woonplaats bij vestigingsadres). Altijd zichtbaar en enabled indien wijzigrechten.
* **Overname vestigingsadres in postadresadres** (achter de kolom woonplaats bij postadres). Altijd zichtbaar en enabled indien wijzigrechten.

### Triggers knoppen linksonder

* Controleer BRP/NHR. Is zichtbaar en enabled indien de inlogger behoort tot een rechtengroep die wijzig BPR/NHR heeft op contactadressen (hoofdrechtengroep). Zie: [NHR bevraging](/docs/probleemoplossing/programmablokken/nhr_bevraging.md) en [BPR (GBA) bevraging](/docs/probleemoplossing/programmablokken/bpr_bevraging.md).
