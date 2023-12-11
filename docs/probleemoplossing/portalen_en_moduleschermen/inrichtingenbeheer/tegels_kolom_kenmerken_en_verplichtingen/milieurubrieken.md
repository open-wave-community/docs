# Milieurubrieken

## Trigger

De tegel is een trigger voor tonen van het overzicht van *Milieurubrieken* als geluid bodem, veiligheid, water.

De onderliggende tabel is tbmilrubriek. De tabel wordt onder meer gebruikt voor het indelen in groepen en tegels van opslagkaarten (tbmilopslag) zie hieronder en bij [Opslagtabel bij inrichtingen](/docs/instellen_inrichten/opslag_bij_inrichtingen.md).

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *Inrichtingenbeheer*
  * Kolom: *Kenmerken en Verplichtingen/
  * Kopregel: *Milieurubrieken*
  * Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbmilrubriek)

## Gebruik milieurubrieken

De tegel *Milieurubrieken* geeft toegang tot de lijst met rubrieken: een codering en een omschrijving. 
Bij elke rubriek kan aangegeven worden of deze gebruikt kan worden bij de opslagtabel (tbmilopslag), en/of de ontheffingstabel (tbhorontheffingen), en/of de certificatentabel (tbmilcertificaten) en/of de overige/diversen tabel: tbmildiversen.

Deze tabellen kunnen elk namelijk door één of meer tegels en lijsten worden ontsloten, waarbij de rubriek een belangrijk filtermiddel is. Zo kan de tabel tbmilopslag kaarten bevatten gecodeerd door de rubrieken bodem en koeling, die via twee tegels en lijsten separaat getoond kunnen worden. Zo ook zou de lijst met ontheffingen desgewenst gesplitst kunnen worden in twee tegels op grond van de rubrieken geluid of licht. En nu dus ook op zelf gedefinieerde rubrieken.

De codering van de rubriek (kolom tbmilrubriek.dvcode) speelt hierbij de volgende rol, het beste uit te leggen met een voorbeeld:
De tegel *Tanks* op het inrichtingenportaal is nu gedefinieerd met de action: getFlexList(tbmilopslag,tbmilinrichtingen,{id},10,V). Hetgeen zoveel wil zeggen als dat het indrukken van de tegel een lijst opent op basis van tbmilopslag met kaarten die gekoppeld zijn aan de inrichting waar je op staat EN waarvoor geldt dat de milieurubriekcodering de waarde 10 heeft (10 = tanks).

Wanneer de action veranderd zou worden in getFlexList(tbmilopslag,tbmilinrichtingen,{id},10-5,V) dan worden uit tbmilopslag zowel de kaarten met rubriek tanks (code = 10) als koeling getoond (code = 5).

Bij de wizard waarmee een nieuwe opslagkaart vanaf die lijst kan worden gemaakt, zal het programma mogelijk vragen om een rubriek te kiezen uit tbmilrubriek, waarbij de keuze wordt beperkt tot de mogelijkheden die gedefinieerd zijn in de action van de tegel. Dus in het eerste geval valt er niets te kiezen: de rubriek van de nieuwe kaart wordt vanzelf weer tanks.

In het tweede geval is er en keuze uit Koeling of Tanks. In het geval dat bij dat één van de niet-vervallen opslag-rijen (dlopslag = T) uit tbmilrubriek het aanvinkvakje *is default* (dlisdefault) is aangevinkt, zal bij een nieuwe opslagkaart NIET om een rubriekkeuze worden gevraagd. De nieuwe kaart wordt hierdoor vanzelf aan de bestaande lijst van de betreffende tegel toegevoegd.

Op de detailkaart van de tbmilopslag is de kolom rubriek aanpasbaar. 
In dit geval is de dropdown lijst echter bepaald door de rubrieken waarvoor geldt dat het aanvinkvakje *Opslag* (dlopslag) gevuld is. Hier kan dus een rubriek koeling mogelijk worden veranderd in rubriek bodem (code 3), waardoor de opslagkaart vanaf dan alleen zichtbaar is achter tegels die de code 3 in de action hebben staan.

**LET OP:** het gebruik van de rubriekcoderingen in de action bij tegels is alleen zinvol bij:

  * getFlexList(tbhorontheffingen,tbmilinrichtingen,{id},*rubriekcode(s)*,V)
  * getFlexList(tbmilopslag,tbmilinrichtingen,{id},*rubriekcode(s)*,V)
  * getFlexList(tbmildiversen,tbmilinrichtingen,{id},*rubriekcode(s)*,V)
  * getFlexList(tbmilcertificaten,tbmilinrichtingen,{id},*rubriekcode(s)*,V)

Tbhorontheffingen werkt zoals beschreven bij tbmilopslag. De rubriek is rechtstreeks gekoppeld aan de ontheffingskaart.
Tbmildiversen en tbmilcertificaten zijn getrapt gekoppeld aan de rubriek.
Voor tbmildiversen en tbmilcertificaten geldt dat de rubriek is gekoppeld aan de soortdiversen-tabel (tbmilsrtdiversen) en de soort certificatentabel (tbmilcodecertif).
Via de beheertegels *Soorten certificaten* en *Milieu-gegevenssoort* kan een soort-certificaat of een milieu-gegevenssoort gekoppeld worden aan een rubriek.

getFlexList(tbmilcertificaten,tbmilinrichtingen,{id},3-10,V) betekent dat de certificaten getoond worden waarvoor geldt dat de soortcertificaat gekoppeld is aan de rubriek bodem (code  3 of aan rubriek tanks (code 10).
Bij de wizard waarmee een nieuwe certificaat vanaf die lijst kan worden gemaakt, zal het programma o.a. vragen om een soort certificaat te kiezen, waarbij de keuze wordt beperkt tot de soorten die gekoppeld zijn aan de codes genoemd in de action van de tegel. 

Op de detailkaart van de tbmilcertificaten en tbmildiversen is de kolom *soort certificaat* of *soort gegeven* aanpasbaar waarmee vanzelf de rubriek wordt mee veranderd en dientengevolge in een ander lijst tevoorschijn komt. 

## Bijzondere kolommen

  * dlontheffing. Indien aangevinkt dan kan de rubriek gebruikt worden voor filtering op tabel tbhorontheffingen.  
  * dlopslag. Indien aangevinkt dan kan de rubriek gebruikt worden voor filtering op tabel tbmilopslag
  * dlcertificaat. Indien aangevinkt dan kan de rubriek gebruikt worden voor filtering op tabel tbmilcertificaten
  * dldiversen. Indien aangevinkt dan kan de rubriek gebruikt worden voor filtering op tabel tbmildiversen
  * dvcsscolorname. CSS kleurcode zoals Blue of magenta (zie [http://www.w3schools.com/cssref/css_colors.asp](http://www.w3schools.com/cssref/css_colors.asp.md)). Deze kleurcode wordt gebruikt bij interne kaartrepresentatie van een vlak, lijn of punt van een opslagkaart, ontheffings- of diversen-kaart.
  * dlisdefault. Er kan maar één rij van tbmilrubriek gevuld zijn met dlisdefault = 'T'. Is dat het geval en dlopslag op dezelfde rij is aangevinkt, dan kan de gebruiker bij het aanmaken van een nieuwe opslagkaart geen rubriek kiezen (die wordt dus default gevuld met de aangevinkte waarde)

