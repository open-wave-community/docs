# Email vanuit adviesaanvraag

Vanuit het adviesdetailscherm met de knop achter de kolom _email verstuurd_ of met de knop _meerdere adviezen uitzetten_ linksonder vanuit het advies overzichtscherm per zaak, kan een email per adviesinstantie verstuurd worden naar de (externe) adviseur.

## Noodzakelijke instellingen

- De bovenliggende hoofdzaak (dus bijvoorbeeld de omgevingszaak waar het advies aan gekoppeld is) mag niet geblokkeerd zijn
- EN de kolom **email (dvemail) van de bijbehorende adviesinstantie** (beheertegel _Adviesinstanties_) moet gevuld zijn met een valide emailadres (de ontvanger van de email)
- EN de kolom **email van de inlogger** bij de medewerkerstabel moet gevuld zijn met een valide emailadres
- EN de **webmailinstellingen** moeten kloppen: zie bij Instellen/Inrichten [Email](../../../instellen_inrichten/email.md)
- EN de kolom _Tekst_ van instelling _Sectie: Adviezen_ en _Item: StandaardEmailTekstAanhef_ moet gevuld zijn
- EN de kolom _Info_ van instelling _Sectie: Adviezen_ en _Item: StandaardEmailTekstBody_ MAG gevuld zijn, maar hoeft niet en wordt geplakt aan de kolom _Tekst_
- EN de kolom _Tekst_ van instelling _Sectie: Adviezen_ en _Item: StandaardEmailTekstBody_ moet gevuld zijn, waarbij de variabelen in kolom _Tekst_ of _Info_ van _StandaardEmailTekstBody_ als volgt worden gevuld:
  - %omschrijving% wordt gevuld worden met omschrijving uit de advieskaart (dvomschrijving)
  - %zaaknaam% met ZaakNaam (bijvoorbeeld bouwen van een carport) van bovenliggende hoofdzaak
  - %module% met:
    - omgevingszaak
    - OF apv/overige zaak
    - OF bouw/sloopzaak
    - OF infoaanvraag
    - OF handhavingszaak
    - OF milieu/gebruikszaak
    - OF horecazaak
  - %soortvergunning% met het OpenWave zaaktype (bijvoorbeeld reguliere procedure)
  - %zaakcode% met de OpenWave zaakcodering
  - %lokatie% met adres + plaats
  - %olonummer% met OLOnr
  - %deeplink% met hyperlink naar het betreffende zaakportaal

## Voorbeeld

![Email vanuit advies](/img/applicatiebeheer/probleemoplossing/kaart/emailvanuitadvies.png){ class="media" loading="lazy" width="800" }

Het resultaat van bovenstaand voorbeeld in de body van een email:

> Geachte adviseur,
> Graag ontvangen wij uw advies m.b.t. omgevingszaaknummer 2014W0060.
> Het betreft: Plaatsen van Carport (Reguliere procedure).
> Om deze zaak rechtstreeks te raadplegen, klikt u op onderstaande link.
> `https://demo1.open-wave.nl/#omgevingdetail/7163`

Het onderwerp van de email is dus niet aanpasbaar indien de standaard mail aan adviesinstantie volgens de configuratie instellingen opgemaakt wordt.

## Email op basis van emailsjabloon

Indien gewenst kan men op basis van een eigen gedefinieerd sjabloon, de mail naar adviesinstantie laten opstellen door de programmatuur. Zo kan men zelf het onderwerp en body van de mail bepalen en via de formqueries en tags de gewenste waarden ophalen uit de onderliggende tabellen van OpenWave.

Er zal per module een mailsjabloon gemaakt moeten worden via tegel **Emailsjablonen** in het beheer. In het sjabloon dient men het vinkje **Is sjabloon voor standaardmail naar adviesinstantie?** aan te vinken en veld **Benaderbaar vanuit tabel** met waarde _tbadviezen_ te vullen en het veld **Voor module** met de gewenste moduleletter.

> [!WARNING]
> **Let op**: er kan per module maar 1 sjabloon zijn met eigenschap _Is sjabloon voor standaardmail naar adviesinstantie_!

De programmatuur kijkt bij het aanmaken van een of meerdere adviezen (en gelijk email versturen) EN bij het versturen van mail via knopje in detailscherm van het advies, of er een emailsjabloon gedefinieerd is voor de module van de hoofdzaak (Omgeving, Handhaving etc.). Zo ja dan wordt de mail opgesteld op basis van het sjabloon. Vindt de programmatuur geen sjabloon dan wordt er teruggegrepen op de oude standaard email en gekeken naar bovengenoemde configuratie instellingen voor _Aanhef_ en _Body_.

> [!INFO]
> **Goed om te weten**: indien men van een eigen sjabloondefinitie gebruik maakt zal bij opstellen van de adviesmail niet gekeken worden naar of er input parameters bij het sjabloon staan opgegeven, eveneens wordt er niet gekeken naar eigenschappen als _Bijlagen toevoegen_, _Documentnaam_ etc. De mail wordt niet opgeslagen namelijk en functionaliteit blijft gelijk aan wat men gewend is bij standaard mail aan adviesinstantie.
