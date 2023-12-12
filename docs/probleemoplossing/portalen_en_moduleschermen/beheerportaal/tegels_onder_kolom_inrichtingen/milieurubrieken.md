# Milieurubrieken

## Trigger

De tegel is een trigger voor tonen van het overzicht van _Milieurubrieken_ als geluid bodem, veiligheid, water.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Beheer_
- Kolom: _Inrichtingen_
- Kopregel: _Milieurubrieken_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbmilrubriek)_

### Gebruik milieurubrieken

Het gebruik van milieu-rubrieken (beheertegel _Milieurubrieken_ (tbmilrubriek)) is vrijer geworden met deze versie.
Zelf gedefinieerde rubrieken worden vanaf nu ondersteund.

Hieronder de nieuwe situatie:
De tegel _Milieurubrieken_ geeft toegang tot de lijst met rubrieken: een codering en een omschrijving.
Bij elke rubriek kan aangegeven worden of deze gebruikt kan worden bij de opslagtabel (tbmilopslag), en/of de ontheffingstabel (tbhorontheffingen), en/of de certificatentabel (tbmilcertificaten) en/of de overige/diversen tabel: tbmildiversen.

Deze tabellen kunnen elk namelijk door één of meer tegels en lijsten worden ontsloten, waarbij de rubriek een belangrijk filtermiddel is. Zo kan de tabel tbmilopslag kaarten bevatten gecodeerd door de rubrieken bodem en koeling, die via twee tegels en lijsten separaat getoond kunnen worden. Zo ook zou de lijst met ontheffingen desgewenst gesplitst kunnen worden in twee tegels op grond van de rubrieken geluid of licht. en nu dus ook op zelf gedefinieerde rubrieken.

De codering van de rubriek (kolom tbmilrubriek.dvcode) speelt hierbij de volgende rol, het beste uit te leggen met een voorbeeld:
De tegel _Tanks_ op het inrichtingenportaal is nu gedefinieerd met de action: getFlexList(tbmilopslag,tbmilinrichtingen,{id},10,V). Hetgeen zoveel wil zeggen als dat het indrukken van de tegel een lijst opent op basis van tbmilopslag met kaarten die gekoppeld zijn aan de inrichting waar je op staat en waarvoor geldt dat de milieurubriekcodering de waarde 10 heeft (10 = tanks).

Wanneer de action veranderd zou worden in getFlexList(tbmilopslag,tbmilinrichtingen,{id},10-5,V) dan worden uit tbmilopslag zowel de kaarten met rubriek tanks (code = 10) als koeling getoond (code = 5).

Bij de wizard waarmee een nieuwe opslagkaart vanaf die lijst kan worden gemaakt, zal het programma o.a. vragen om een rubriek te kiezen uit tbmilrubriek, waarbij de keuze wordt beperkt tot de mogelijkheden die gedefinieerd zijn in de action van de tegel. Dus in het eerste geval valt er niets te kiezen: de rubriek van de nieuwe kaart wordt vanzelf weer tanks.
In het tweede geval is er en keuze uit Koeling of Tanks.

De nieuwe kaart wordt hierdoor vanzelf aan de bestaande lijst van de betreffende tegel toegevoegd.
Op de detailkaart van de tbmilopslag is de kolom rubriek aanpasbaar.
In dit geval is de dropdown lijst echter bepaald door de rubrieken waarvoor geldt dat het aanvinkvakje _Opslag_ gevuld is. Hier kan dus een rubriek koeling mogelijk worden veranderd in rubriek bodem (code 3), waardoor de opslagkaart vanaf dan alleen zichtbaar is achter tegels die de code 3 in de action hebben staan.

LET OP: het gebruik van de rubriekcoderingen in de action bij tegels is alleen zinvol bij:
getFlexList(tbhorontheffingen,tbmilinrichtingen,{id},Rubriekcode(s),V)
getFlexList(tbmilopskag,tbmilinrichtingen,{id},Rubriekcode(s),V)
getFlexList(tbmildiversen,tbmilinrichtingen,{id},Rubriekcode(s),V)
getFlexList(tbmilcertificaten,tbmilinrichtingen,{id},Rubriekcode(s),V)

Tbhorontheffingen werkt zoals beschreven bij tbmilopslag. De rubriek is rechtstreeks gekoppeld aan de ontheffingskaart.
Tbmildiversen en tbmilcertificaten zijn getrapt gekoppeld aan de rubriek.
Voor tbmildiversen en tbmilcertificaten geldt dat de rubriek is gekoppeld aan de soortdiversen-tabel (tbmilsrtdiversen) en de soort certificatentabel (tbmilcodecertif).
Via de beheertegels _Soorten certificaten_ en _Milieu-gegevenssoort_ kan een soort-certificaat of een milieu-gegevenssoort gekoppeld worden aan een rubriek.

getFlexList(tbmilcertificaten,tbmilinrichtingen,{id},3-10,V) betekent dat de certificaten getoond worden waarvoor geldt dat de soortcertificaat gekoppeld is aan de rubriek bodem (code 3 of aan rubriek tanks (code 10).
Bij de wizard waarmee een nieuwe certificaat vanaf die lijst kan worden gemaakt, zal het programma o.a. vragen om een soort certificaat te kiezen, waarbij de keuze wordt beperkt tot de soorten die gekoppeld zijn aan de codes genoemd in de action van de tegel.

Op de detailkaart van de tbmilcertificaten en tbmildiversen is de kolom _soort certificaat_ of _soort gegeven_ aanpasbaar waarmee vanzelf de rubriek wordt mee veranderd en dientengevolge in een ander lijst tevoorschijn komt.
