# Medewerkers

Portaal beheerportaal-Nieuw. Tegel *Medewerkers (actieve of alle)*.

Screenidentifiers:

- MDLC_getMedewerkerList.xml
- MDDC_getMedewerkerDetail.xml

## Definiëren van medewerkers

De inlogger moet beheerrechten hebben: tbmedewerker.dnbeheerniveau = 99.
Alle kolommen en knoppen zijn dan toegankelijk. De kolommen komen uit de view vwfrmmedewerkers met eventueel de restrictie dat de vervaldatum (uit dienst per) leeg is of groter dan vandaag.

## Trigger op lijstscherm: Verspreiden Inlog Dig. Checklist

In bulk aanpassen inloggegevens voor digitale checklisten (vullen van kolommen dvextchklstlogin en dvextchklstpass).

Indien de instelling *Sectie: KoppelingInsptoets en Item: Methode en Tekst: DigitaleChecklisten* aangevinkt is – verschijnt een wizardknop
waarmee een wizard wordt gestart die op de eerste pagina vraagt om inlognaam en wachtwoord waarmee OpenWave de api’s kan aanroepen van digitale checklisten om o.a. dossiers aan te maken. Indien OpenWave al een bestaande gevulde combinatie kan vinden worden deze waardes als default gebruikt.

Op de tweede pagina kunnen een of meer medewerkers aangevinkt worden bij wie de ingevoerde login en wachtwoord doorgezet moet worden. Het programma vinkt daarbij default al de medewerkers aan die reeds een gevulde naam/wachtwoord hebben voor DC.

## Trigger op detailscherm: ken tegels toe

Linksonder de wizardknop (altijd zichtbaar en enabled) die een wizard start om één of meer tegels *toe te kennen aan* of *af te nemen van* de medewerker. Wijst voor zich.

Omgekeerd kan bij de portaldefinitie op het laagste niveau van de tegel een wizard gestart worden die een of meer medewerkers *toekent aan* of *afneemt van* de tegel.

## Trigger op detailscherm: Draag openstaande taken over

Rechtsboven in menu opties: de optie *Draag openstaande taken over aan andere medewerker*.

Er wordt een wizard gestart waarbij eerst één of meer modules aangewezen moeten worden en vervolgens één of meer aan te wijzen taken/rollen die bij die modules voor kunnen komen. Vervolgens wordt de persoon aangewezen die de openstaande taken van de medewerker gaat overnemen. Het kan gaan om de taken/rollen:

- **Accountmanager** bij de modules (B)ouw/sloop, Hore(C)a, mili(E)u/gebruik,(I)nfo-aanvragen, APV/(O)verig en (W)omgeving. De kolom accountmanager wordt overschreven met de nieuwe aangewezen persoon voor alle zaken bij de aangewezen modules waarvoor geldt dat:
  - de besluit/einddatum en - indien van toepassing - ingetrokken datum beide leeg zijn
  - en de zaak niet geblokkeerd is
  - en de kolom accountmanager (dvcodeaccountman) de waarde van de medewerker heeft.
- **Dossierbehandelaar** bij tbinbehandelingbij van de modules (B)ouw/sloop, Hore(C)a, mili(E)u/gebruik, (H)andhavingen, (I)nfo-aanvragen, APV/(O)verig en (W)omgeving. De einddatum van de actieve dossierbehandelaar (tbinbehandelingbij met lege einddatum) wordt overschreven met de systeemdatum en een nieuwe tbinbehandelingbij kaart wordt aangemaakt met de nieuwe aangewezen persoon voor alle zaken bij de aangewezen modules waarvoor geldt dat:
  - de besluit/einddatum en - indien van toepassing -ingetrokken datum beide leeg zijn
  - en de zaak niet geblokkeerd is
  - en de actieve behandelaar de waarde van de medewerker heeft.
- **Hoofdinspecteur** bij tbinspecties van de modules (B)ouw/sloop, Hore(C)a, (H)andhaving, APV/(O)verig (V)estiging/inrichting en (W)omgeving. De kolom hoofdinspecteur (dvcodemedewerkers) van tbinspecties wordt overschreven met de nieuwe aangewezen persoon voor alle zaken bij de aangewezen modules waarvoor geldt dat:
  - de afgehandeld datum (ddcontrole) van het inspectietraject leeg is
  - en de hoofdinspecteur de waarde van de medewerker heeft.
- **Bezoekinspecteur** bij tbinspbezoeken van de modules (B)ouw/sloop, Hore(C)a, (H)andhaving, APV/(O)verig (V)estiging/inrichting en (W)omgeving. De kolom bezoekinspecteur (dvcodemedewerkers) van tbinspbezoeken wordt overschreven met de nieuwe aangewezen persoon voor alle zaken bij de aangewezen modules waarvoor geldt dat:
  - de afgehandeld datum (ddafgehandeld) van het inspectiebezoek leeg is
  - en de bezoekinspecteur de waarde van de medewerker heeft.
- **Processtapverantwoordelijke** bij tbtermijnbewstappen van de modules (B)ouw/sloop, Hore(C)a, mili(E)/gebruik, (H)andhaving, (I)nfoaanvragen, APV/(O)verig en (W)omgeving. De kolom *staatgeplandvoor* (dvcodevoorwie) van tbtermijnbewstappen wordt overschreven met de nieuwe aangewezen persoon voor alle zaken bij de aangewezen modules waarvoor geldt dat:
  - de afgehandeld datum (ddafgehandeld) van de termijnbewakingsstap leeg is
  - en de kolom *staatgeplandvoor* (dvcodevoorwie) de waarde van de medewerker heeft.
- **Uitzetter van adviezen** bij tbadviezen van de modules (B)ouw/sloop, Hore(C)a, mili(E)/gebruik, (H)andhaving, (I)nfoaanvragen, APV/(O)verig en (W)omgeving. De kolom *interne behandelaar* (dvcodemedewerkers) van tbadviezen wordt overschreven met de nieuwe aangewezen persoon voor alle zaken bij de aangewezen modules waarvoor geldt dat:
  - de advies *ontvangstdatum* (ddadviesdatum) van het advies leeg is
  - en de kolom *interne behandelaar* (dvcodemedewerkers) de waarde van de medewerker heeft.
- **Juridisch verantwoordelijke handhaving** bij de module (H)andaving. De kolom juridisch verantwoordelijke (dvcodejurist) wordt overschreven met de nieuwe aangewezen persoon voor alle zaken bij de module Handhaving waarvoor geldt dat:
  - de einddatum leeg is
  - en de zaak niet geblokkeerd is
  - en de kolom *juridisch verantwoordelijke* de waarde van de medewerker heeft.
- **Klachtafhandelaar** bij tbklachten van de modules Hore(C)a en (V)estiging/inrichting. De kolom *klachtafhandelaar* (dvcodemedewerkers) van tbklachten wordt overschreven met de nieuwe aangewezen persoon voor alle zaken bij de aangewezen modules waarvoor geldt dat:
  - de klachtafrond datum (ddafgerond) van leeg is
  - en de kolom *klachtafhandelaar* (dvcodemedewerkers) de waarde van de medewerker heeft.
- **Juridisch verantwoordelijke bezwaar/beroep** bij tbbezwaarberoep van de modules (B)ouw/sloop, Hore(C)a, mili(E)/gebruik, (H)andhaving, APV/(O)verig en (W)omgeving. De kolom *juridisch verantwoordelijke* (dvcodejurist) van tbbezwaarberoep wordt overschreven met de nieuwe aangewezen persoon voor alle zaken bij de aangewezen modules waarvoor geldt dat:
  - de besluitdatum (dduitspraak) van de bezwaar/beroepszaak leeg is
  - en de juridisch verantwoordelijke de waarde van de medewerker heeft.
- **Collegiale toetser** bij geregistreerde documenten van de modules (B)ouw/sloop, Hore(C)a, mili(E)/gebruik, (H)andhaving, (I)nfoaanragen, APV/(O)verig en (V)estigingen (inrichtingen) en (W)omgeving. De kolom *collegiale toetser* (dvcodenwvoorwie) van tbcorrespcollegtoets wordt overschreven met de nieuwe aangewezen persoon voor alle collegiale toetsen bij de aangewezen modules waarvoor geldt dat:
  - de toetsdatum (ddddatumgetoetst) van de toets leeg is
  - en de toetser (dvcodemwvoorwie) de waarde van de medewerker heeft.

## Trigger op detailscherm: Wijzig medewerkerscode

Rechtsboven in menu opties: de optie *Wijzig medewerkerscode met terugwerkende kracht*.

De beheerder kan met deze functie een bestaande medewerkerscode wijzigen in een nieuwe unieke code.

## blokken Naam en Organisatie

- **Code** (dvcode): De primary key van de medewerkerstabel: een unieke codering van maximaal karakters. Is (nog) niet te wijzigen.
- **Uit dienst per** (ddvervaldatum): Belangrijk voor inlogprocedure en dropdownlijstjes met te kiezen medewerkers.
- **Externe financ code** (vmwexterncode): Code waaronder de medewerker bekend is in extern bijvoorbeeld financieel systeem.
- **Email** (dvemail): Belangrijk voor ontvangen van afschriften bij verzenden van email (adviezen, BAG-beheerder) en koppeling Digitale Checklisten en ontvangen van unlockcode bij 2 factor authenticatie (indien 2-factortype = 1)..
- **Mobiel** (dvmobiel): Belangrijk voor het ontvangen van unlockcode bij 2 factor authenticatie (indien 2-factortype = 2). Het nummer zonder spaties of hyphens invoeren!!
- **Aangepast kleurenschema** (dlkleurenblind): Door dit aan te vinken zal de specifieke medewerker in lijstschermen een aangepast kleurenschema zien waardoor de selectiebalk zalmkleurig is en beter contrasteert. Dit kan zorgen voor een beter overzicht wanneer iemand kleurbeperkt zicht heeft.
- **Afdeling** (dvafdeling): Keuze uit afdelingen zoals opgegeven in tbmewafdeling (beheertegel *Afdelingen*). Wordt gebruikt om bij *Te ondertekenen brieven* aan te geven voor welke afdeling de brief is. Het programma kijkt naar de afdeling bij de medewerker die de zaak in behandeling heeft waaronder de brief is aangemaakt .

## blok Rechten

- **Compartiment rechtengroep** (dnkeycompartiment): Indien een medewerker gekoppeld is aan een [compartiment](/instellen_inrichten/compartimenten.md) kan hij/zij alle zaken en inrichtingen zien van de gemeentes die aan dat compartiment zijn toegevoegd (hierna: de compartimentsgemeentes). Alleen die zaaktypes en soorten inrichtingen (bedrijfsoort) die aan het compartiment zijn toegevoegd kunnen door de medewerker worden gemuteerd in zoverre zij in een van de compartimentsgemeentes spelen.

Omgekeerd: indien een medewerker geen lid is van een compartiment ziet hij/zij alle zaken van alle gemeentes, maar kan alleen die zaaktypes muteren bij gemeente X indien deze niet aan een compartiment zijn toegekend waar gemeente X deel van uitmaakt. OpenWave zal eerst naar de compartimentsrechten kijken om te bepalen of een medewerker een bepaalde zaak mag zien en/of muteren en zo ja, dan naar de functionele rechten.

- **Mag documenten inzien tot vertrouwelijkheidsniveau** (dnkeyvertrouwelijkheid): Met deze keuzelijst gebaseerd op de beheertabel tbvertrouwelijkheid kan een niveau aan een medewerker worden toegekend dat zal worden vergeleken met - indien aanwezig - het vereiste vertrouwelijkheidsniveau van een document bij het ophalen/inzien/downloaden van dat document. Indien geen medewerkersniveau is toegekend dan gaat OpenWave uit van het niveau 0 hetgeen betekent dat de medewerker alleen documenten kan inzien waaraan geen vereist niveau is toegekend of documenten met vereist niveau 0. In Open Wave kan een vereist niveau aan een document worden toegevoegd door het document te registreren. Indien gebruik wordt gemaakt van de stuf zaak/DMS koppeling kan bij het uploaden een vertrouwelijkheidsniveau worden opgegeven. Bij het opvragen van een document via stuf zaak/DMS wordt ook het vereiste vertrouwelijkheidsniveau opgevraagd en vergeleken met dat van de medewerker.
- **Functionele rechtengroep** (dnkeyrechten): Zonder gekoppelde rechtengroep kan de gebruiker niets zien of doen.
- **Rapportniveau** (dnrapportageniveau): De medewerker ziet alleen rapportages die een *vereist autorisatie niveau* hebben dat kleiner of gelijk is dan de hier ingevulde waarde.
- **Beheerniveau** (dnbeheerniveau): De medewerker kan alleen de tegels van de beheerportalen benaderen indien de hier ingevulde waarde 99 is.
- **1=desktop, 2=browser, 3=beide** (dnmaginapp): De medewerker kan alleen in de browserversie van Open-Wave werken (zie inloggen) indien de ingevulde waarde hier 1 of 3 is.
- **Is externe adviseur** (dlisaxtadv): Indien uitgevinkt, dan is vakje *interne medewerker* vanzelf aangevinkt. Alleen interne medewerkers verschijnen in de dropdownlijstjes met te kiezen medewerkers.
- **Mag uren van andere medewerkers overschrijven** (dlmagurenmuteren): Indien aangevinkt dan heeft deze medeweker het recht om uren (tburen) van andere medewerkers te overschrijven.
- **Mag factuurdatum bij uren muteren** (dlmagurenfactmut): Indien aangevinkt kan de medewerker vanuit de lijst Ongefactureerde Uren een deel daarvan voorzien van een factuur c.q. fiatdatum. Deze lijst is oproepbaar vanaf de tegel *Te factureren uren* vanaf het hoofdportaal mits de inlogger ook het recht *mag uren van andere medewerkers overschrijven* aangevinkt heeft staan.
- **Mag DROP publiceren** (dlmagpubliceren). Indien aangevinkt kan de medewerker vanuit de lijst *Te publiceren zaken* zorg dragen voor de publicatie via DROP.
- **Overruled beperkingen compartiment** (dloverrulecompartiment): Gebruik hiervan kan tot complexe verwarrende situaties leiden. Indien aangevinkt komen bijv. in de dropdownlijstjes van de medewerkers alleen die medewerkers te staan die lid zijn van hetzelfde compartiment als de inlogger, maar nu aangevuld met de andere medewerkers die deze eigenschap aangevinkt hebben staan. Op deze wijze kan een zaak toch aan een medewerker buiten het compartiment worden toegewezen (beter is hiertoe het recht *Mag ander compartiment toekennen bij hoofdzaak* te gebruiken).
- **Mag ander compartiment toekennen bij hoofdzaak** (dlmagcompoverrulen): Hiermee is de inlogger toegestaan op het detailscherm van een hoofdzaak, de zaak toe te kennen aan een ander compartiment of aan de host.
- **Mag digitaal ondertekenen** (dlmagdigondertekenen): Geeft aan of de medewerker de kolom dlisdigondertekend mag vullen bij de geregistreerde documenten (tbcorrespondentie).
- **Mag editen moet dig. ondertekend worden** (dlmagmoetdiotaanpassen): Geeft aan of de medewerkers de kolom dlmoetdigondertekenen van de geregistreerde documenten (tbcorrespondentie) mag aanpassen.
- **Mag inrichting klaarzetten voor export REV** (dlmagrevexportzetten): Indien aangevinkt kan de medewerker op de inrichtingskaart de inrichting goedkeuren voor export naar REV door het invullen van de inrichtingskolom ddmagexport (dvcodemwmagexport wordt daarbij automatisch onder water gevuld.).
- **Is raadpleger** (dlisraadpleger). Indien aangevinkt dan komt de medewerker niet voor in de dropdownlijstjes die een medewerker koppelen aan een taak.
- **Alleen data van gemeentes** (dvalleengemeentes): In deze kolom kunnen de gemeente-ids (tabel 33 beheertegel *Gemeentes*) worden opgesomd waarvoor de medewerker gerechtigd is om data te zien. Zaken en inrichtingen zijn namelijk altijd verbonden aan een locatie en elke locatie aan een gemeente. Indien deze kolom leeg is, dan mag de medewerker in principe alle zaken/inrichtingen zien van alle gemeentes. De gemeente-ids moeten worden gescheiden door een puntkomma. Bijvoorbeeld: *0738;0358;* betekent dat de medewerker alleen zaken/inrichtingen kan zien die gelokaliseerd zijn in de gemeentes Aalburg en Aalsmeer. Deze functionaliteit blijft bestaan naast de compartimentsrechten.

## blok Login

- **Loginnaam** (dvloginnaam): Moet uniek zijn indien gevuld (mag dus wel leeg zijn).
- **Pass** (dvpasswcrypt): Het gecrypte password (bcrypt) in het aantal costs gedefinieerd door *Getal1* van de instelling *Sectie: Logon* en *Item: bcrypt*costs_ (default 10). Het password kan hier plain worden ingebracht, waarna het programma deze gecodeerd opslaat en toont als vier asterisken. De codering is niet om te keren. Indien het ingevoerde password niet aan onderstaande criteria voldoet wordt het password leeggemaakt. Invoer van het password is als volgt gereguleerd:
  - alleen karakters ASCII 32 t/m 126 dat zijn a-z A-Z 0-9 en een spatie en de tekens: !"#$%&'()\*+,-./:;⇔?@[\]^\_`{|}~ (33stuks)
  - moet ongelijk zijn aan inlognaam
  - moet ongelijk zijn aan oude password
  - lengte moet groter of gelijk zijn dan de instelling *Getal1* van *Sectie: Logon* en *Item: Pass*MinLength_ (default 9).
- **Datum password** (dddatumpassword): Wordt automatisch gevuld bij invullen van nieuw password, maar kan alhier worden overruled. Van belang bij inloggen. Het programma beschouwt een password als verlopen indien:
  - de kolom *Password verloopt nooit* NIET aangevinkt is (dlpassneverexpires = 'F')
  - en één van onderstaande items is waar:
    - (dddatumpassword is null)
    - (dddatumpassword + aantal dagen van instelling *Getal1* van *Sectie: Logon* en *Item: Password_MaxDagenSindsCreatie* (defaultwaarde 35) < = vandaag).
- **(tijdelijk) geldig tot** (ddlockedfrom): Indien tijdens het inloggen blijkt dat deze datum kleiner is dan de systeemdatum volgt een mededeling *Geldigheid tijdelijke inlog verstreken; neem contact op met de beheerder*.
- **Het password van deze medewerker verloopt nooit** (dlpassneverexpires): Indien aangevinkt zal het programma bij het inloggen niet kijken naar datum password. Indien een automatisch extern proces een login/pass heeft gekregen, omdat dat proces een Open-Wave API aanroept dan is het uitvinken van deze kolom aan te bevelen.
- **2-factor type** (dntwofactortype): Kan de waarde 1 of 2 hebben. 1 = email (default) en 2 = sms. Indien 2-factor authenticatie (instelling *Sectie: Logon* en *Item: 2-factor* is aangevinkt) dan kan bij het inloggen gevraagd worden om een unlockcode in te tikken ((zie [Inloggen](/probleemoplossing/programmablokken/inloggen.md)). Deze wordt door OpenWave of per email of per sms naar de inlogger gestuurd. Zie de kolommen dvemail en dvmobiel. Indien per sms dan moet er wel een contract zijn met een telecomprovider. Zie hiervoor sms-instellingen in het hoofdstuk: [SMS](/instellen_inrichten/sms.md).
- **Voor deze medewerker is geen 2 factor auth. nodig?** (dldeviceunlockdisabled): Indien aangevinkt zal de medewerker niet met 2-factor hoeven in te loggen (zie [Inloggen](/probleemoplossing/programmablokken/inloggen.md)) terwijl de algemene instelling *Sectie: Logon* en *Item: 2-factor* wel is aangevinkt.
- **2- factor unlockcode en datum+tijd unlockcode** (dvdeviceunlockcode en ddpinunlockcode): Zie inloggen. Worden automatisch gevuld indien de medewerker door 2-facor instelling gedwongen is bij het inloggen een unlockcode in te voeren. Indien de verstuurde email naar de medewerker met de code is mislukt, of de email is onbereikbaar dan kan de applicatiebeheerder alhier de code zien en eventueel mondeling doorgeven. Dat moet dan gebeuren binnen het aantal uur dat is opgegeven in *Getal1* van de instelling *Sectie: Device* en *Item: Unlock_Pin_MaxUurSindsCreatie* (default 1).
- **Tijdelijke geldigheid opheffen na succesvol inloggen** (dlopheffenlock): Indien aangevinkt en de inlogger heeft met succes een nieuw password aangemaakt (vanwege verlopen van de oude), dan zal op de medewerkerskaart de kolom (tijdelijk) geldig tot (tbmedewerkers.ddlockedfrom) worden leeggemaakt.
- **Deze medewerker mag geen devices registreren** (dldeviceopslagverbod): Indien aangevinkt dan wordt bij het creëren van een nieuw password door de inlogger NIET meer gevraagd of het programma het device waarvandaan hij/zij opereert moet opslaan (en dat wordt dan ook niet opgeslagen). Indien 2-factor authentication aan staat voor deze inlogger zal in dat geval elke keer om een 2-factor controle worden gevraagd.
- **Deze medewerker hoeft geen loginverklaringen af te vinken** (dlskiploginverkl): Indien aangevinkt zal het programma bij het inloggen niet kijken of er aan te vinken loginverklaringen zijn.
- **Dig.checklist login en dig.checklist pass** (dvextchklstlogin en dvextchklstpass): Allebei plain text. Gevraagd wordt naar login/pass bij digitale checklijsten met recht tot het creëren van een nieuw dossier/checklist. Moet gevuld worden bij die medewerkers die als hoofdinspecteur bij een inspectietraject gedefinieerd kunnen worden of als actieve behandelaar bij een omgevingszaak. Zie [Digitale checklijsten](/probleemoplossing/programmablokken/digitale_checklijsten.md). Het password (dvextchklstpass) wordt geencrypt opgeslagen op de database. Zie: [2-way encryptie van externe wachtwoorden](/instellen*inrichten/2way_encryptie_externe_wachtwoorden.md).

### blok Login/Wachtwoord vergeten

Diverse niet-muteerbare kolommen die OpenWave nodigt heeft ter controle van de procedure bij het aanvragen van nieuw wachtwoord.

## blok Is Adviseur namens

In het blok **Is Adviseur namens** (tbmedewisadviseurvoor) kunnen 0 of meer adviesinstanties worden aangewezen waarvoor de betrokken medewerker adviseur kan zijn. Indien gevuld dan kan de medewerker een gevulde lijst kan hebben onder de tegel: [//Mijn uit te brengen adviezen//](/probleemoplossing/portalen*en*moduleschermen/openingsportaal/tegel_mijn_uit_te_brengen_adviezen/lijst_mijn_uitte_brengen_adviezen.md) op het openingsportaal.

API: getMedewIsAdviseurVoor ([https://api.open-wave.nl/RemMethods/getRemMethod/512](https://api.open-wave.nl/RemMethods/getRemMethod/512.md)).

Screenidentifier: MDLC_getMedewIsAdviseurVoorList.xml.
Trigger linksonder: de wizardknop (altijd zichtbaar en enabled) die een wizard start waarmee adviesinstanties aan of uitgevinkt kunnen worden.

## blok Devices

In het blok **Devices** (tbmedewdevices) is zichtbaar vanuit welke IP-adressen en devices de medewerker een geslaagde 2-factor inlogpoging heeft gedaan.
Die pogingen worden bewaard conform *Getal1* van *Sectie: Device en Item: Unlock*Cookie*MaxDagenSindsCreatie* (default 365). Zie: hierboven bij 2-factor kolommen en [Inloggen](/probleemoplossing/programmablokken/inloggen.md).
API: getMedewDevicesList ([https://api.open-wave.nl/RemMethods/getRemMethod/467](https://api.open-wave.nl/RemMethods/getRemMethod/467.md)).
Screenidentifier: MDLC_getMedewDevicesList.xml.

## blok Afgevinkte loginverklaringen

In het blok **Afgevinkte loginverklaringen** (tbmwloginverklaringen) is zichtbaar wanneer de medewerker welke loginverklaringen (beheertegel *Loginverklaringen*) heeft afgevinkt bij het inloggen.

Screenidentifier: MDLC_getVwFrmMwloginverklaringenList.xml.

## blok Niet-afgevinkte loginverklaringen

In het blok **Niet afgevinkte loginverklaringen** is zichtbaar welke loginverklaringen (beheertegel *Loginverklaringen*) de medewerker nog moet afvinken bij het inloggen.

Screenidentifier: MDLC_getVwFrmOpenloginverklaringenList.xml.
