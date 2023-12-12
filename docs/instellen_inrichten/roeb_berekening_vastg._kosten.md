# Roeb berekening vastg. kosten

In het detailscherm van onderdelen/activiteiten (tbtoestemmingen) van een omgevingszaak is een lijst zichtbaar te maken waarmee met behulp van de ROEB-tabellen van het Zaakbeheerportaal de vastgestelde kosten berekend kunnen worden. Deze kosten kunnen dienen als uitgangsbedrag bij de berekening van legesregels bij een omgevingszaak, wanneer de legesregel gekoppeld is aan een activiteit/onderdeel en de bijbehorende legessoort geen bonusmalussoort is. Dat uitgangsbedrag staat dan in die gekoppelde activiteiten/onderdelenkaart (vwfrmtoestemmingen).

Het Uitgangsbedrag = indien

  - *Getal1* van de instelling *Sectie: Programma en Item: Roeb* de waarde 1 heeft dan is de volgorde :
    - dflegesherzbasis is not null dan de waarde van de kolom dflegesherzbasis (herziene kosten),
    - anders indien dflegesvastgroeb is not null dan deze berekende vastgestelde waarde op grond van de gekoppelde regels in de tabel tbroebtoest
    - anders indien dflegesvastgbasis is not null dan de waarde van de kolom dflegesvastgbasis (vastgestelde kosten)
    - en anders de waarde van de kolom dflegesopgbasis (opgegeven kosten).
  - anders (deze instelling bestaat niet of getal1 is ongelijk 1) dan:
    - dflegesherzbasis is not null dan de waarde van de kolom dflegesherzbasis (herziene kosten),
    - anders indien dflegesvastgbasis is not null dan de waarde van de kolom dflegesvastgbasis (vastgestelde kosten)
    - anders indien dflegesvastgroeb is not null dan deze berekende vastgestelde waarde op grond van de gekoppelde regels in de tabel tbroebtoest
    - en anders de waarde van de kolom dflegesopgbasis (opgegeven kosten).

De kolom *dflegesvastgroeb* is niet muteerbaar en is een optelling van de - ook weer berekende - kolom vwfrmroebtoest.dftotaalbedragincbtw voor de rijen die gekoppeld zijn aan de activiteit/onderdeel (op dnkeytoestemmingen).

LET OP: De kolom *dflegesvastgroeb* is een berekend veld in de view vwfrmtoestemmingen. Een aanpassing aan de roeb-beheertabellen (staffel, btw e.d.) hebben met terugwerkende kracht invloed!!

## Instelling zichtbaarheid blok ROEB in detailscherm onderdeel/activiteit

De lijst met berekende bedragen op grond van de ROEB-lijsten in **het blok ROEB** van het detailscherm bij onderdelen/activiteiten is alleen zichtbaar indien
de instelling *Sectie: Programma en Item: Roeb* aangevinkt is. Indien echter de zaak speelt in een compartiment, dan wordt i.p.v. naar deze instelling, gekeken naar de kolom dlroeb van het compartiment.

![](/docs/img/applicatiebeheer/instellen_inrichten/roeb.png){ class="media" loading="lazy" alt="" width="600" }

## Vullen van ROEB-lijsten in het Zaakbeheer

In beheerportaal Zaakbeheer zijn de beheertegels voor definiëren van de ROEB-lijsten terug te vinden onder kolom *Financiele afhandeling*.

### Categorie en bedrag per eenheid per periode

Onder de tegel ROEB-categorieën kan de beheerder één of meer subcategorieën per hoofdcategorie opvoeren. Per subcategorie kunnen vervolgens 1 of meer bedragen (exclusief BTW) met hun eenheden worden opgegeven: elk met een datum geldig vanaf (tbroebprijzen.dddatumvanaf). Dus bijvoorbeeld:

  - Woningen
    - Rijtjeswoningen
      - 208,10 per m3 vanaf 1-1-2015
      -  255,31 per m3 vanaf 1-1-2020

Naar welke periode OpenWave moet kijken is afhankelijk van de ontvangstdatum van de bovenliggende omgevingszaak.

### Staffel voor seriebouw

Onder de tegel ROEB-staffel kunnen de staffels opgegeven worden bij seriebouw met de kolommen *aantalvanaf* en *rekenen met* (wederom per periode). Er moet minimaal één kaart aanwezig zijn met aantalvanaf = 1 en bijgevolg rekenenmet = 1. Bijvoorbeeld:

![](/docs/img/applicatiebeheer/instellen_inrichten/roebstafel.png){ class="media" loading="lazy" alt="" width="400" }

Bovenstaand gefingeerd voorbeeld laat zien dat indien het opgegeven serieaantal tussen 41 en 51 ligt, dat dan in de periode vanaf 1-1-1980 tot 1-6-2018 gerekend moet worden met 12, maar vanaf 1-6-2018 met 13.

Naar welke periode OpenWave moet kijken is afhankelijk van de ontvangstdatum van de bovenliggende omgevingszaak.

### BTW percentages

Onder de tegel *ROEB-BTW*.

Per periode kan hier het geldende btw-percentage opgegeven worden.

Naar welke periode OpenWave moet kijken is afhankelijk van de ontvangstdatum van de bovenliggende omgevingszaak.

## Insert van nieuwe rekenregel

Een nieuwe rekenregel bij een activiteit/onderdeel (in de tabel tbroebtoest) kan worden gemaakt met de insertknop onderaan het lijstje met ROEB-rekenregels mits:

  - de gebruiker het recht heeft om een onderdeel/activiteit toe te voegen (tbomgrechten.dlcomgtstins)
    - de omgevingszaak nog niet is geblokkeerd
    - de compartimentsrechten kloppen

Met de **ontvangstdatum** van de bovenliggende omgevingszaak controleert het programma of er minimaal een subcategorie met bedrag is ingevoerd in de beheertabellen, alsmede een valide btw-percentage en een staffel met serieaantal 1.

De gebruiker dient een hoofdcategorie en daarbinnen een subcategorie aan te wijzen waarbij de mogelijkheden bepaald worden door de tbroebprijzentabel en de ontvangstdatum.

Vervolgens zal de gebruiker een serieaantal (default 1) kunnen opgeven EN - indien er sprake is van een serie - een naam voor de serie (bijvoorbeeld woningen type A).

In datzelfde scherm kan het aantal eenheden dat hoort bij de subcategorie worden ingevoerd.

Zo kan bijvoorbeeld worden opgegeven dat er 48 rijtjeswoningen worden gebouwd van type A met elk 450m3.

OpenWave haalt naast de keyverwijzing van gekozen bedrag/subcategorie, automatisch de keyverwijzing naar het btw-percentage op en automatisch de keyverwijzing naar de staffel op (dus bijv. dat voor 48 woningen van hetzelfde type gerekend met worden alsof het 12 woningen zijn) en insert de roebrekenregel.

### Berekening

In de view vwfrmroebtoest wordt de kolom dftotaalbedragincbtw als volgt berekend:

(aantalstaffel *aantaleenheden* bedragexcbwt) + ((aantalstaffel *aantaleenheden* bedragexcbwt * btwpercentage) /100).

In de view die over het onderdelen/activiteitenscherm heen ligt: vwfrmtoestemmingen is de kolom dflegesvastgroeb een optelling van deze berekende kolom dftotaalbedragincbtw van alle bijbehorende roebrekenregels.

### Wijzigen en deleten

Alleen de kolom *aantaleenheden* kan de gebruiker wijzigen in het [lijstscherm](/instellen_inrichten/standardlist_standarddetail.md) mits:

  - de gebruiker het recht heeft om een onderdeel/activiteit te wijzigen (tbomgrechten.dlcomgtstedt)
  - de omgevingszaak nog niet is geblokkeerd
  - de compartimentsrechten kloppen.

Een rij verwijderen kan mits:

  - de gebruiker het recht heeft om een onderdeel/activiteit te verwijderen (tbomgrechten.dlcomgtstdel)
  - de omgevingszaak nog niet is geblokkeerd
  - de compartimentsrechten kloppen.
