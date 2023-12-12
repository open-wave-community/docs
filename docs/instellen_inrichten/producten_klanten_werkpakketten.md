# Producten Klanten en Werkpakketten

Er zijn twee mogelijkheden:

  - A. per zaak kan maar één product/dienst worden aangewezen
  - B. per zaak kunnen meerdere producten/diensten aangewezen worden. Deze optie is ook mogeijk vanuit een deelzaak inspecties (tbinspecties)

De gebruiker kan in geval A kiezen uit de vastgelegde mogelijke combinaties producten, subproducten, klanten en werkpakketten zoals vastgelegd in het beheerportaal *Zaakbeheer*, kolom *Financiele afhandeling* (tabel tbprodwkpklant), waarbij de productkeuze al gelimiteerd is door het zaaktype van de betreffende hoofdzaak (de mogelijke producten worden gedefinieerd per zaaktype; de mogelijke subproducten door de product keuze).

In geval B (meerdere producten per zaak) wordt in principe niet gekeken naar de mogelijke combinaties producten, subproducten, klanten en werkpakketten. De gebruiker heeft in dit geval vrijelijk keuze uit de producten behorende bij het zaaktype (in geval van inspecties: de inspectie-aanleiding) , de subproducten bij het gekozen product en alle klanten en alle werkpakketten. Zie voor de uitzondering hieronder bij kopje *Meer dan één product/dienst per zaak*.

## Eén product/dienst per zaak

Als de instelling *Sectie: Product/Dienst Item: Omgeving* aangevinkt is en *Getal1* leeg is (of 0), zal in het detailscherm van de omgevingskaart een **blok product/dienst** zichtbaar worden. Ook zal er dan een **tegel Product** in het zaakportaal van een omgevingszaak zichtbaar zijn (mits deze aan hem/haar is toegekend). De tegel toont het blok *Product/dienst* gedeelte in het detailscherm van de omgevingszaak. Het gekozen product, subproduct, klant, werkpakket worden opgenomen in de tabel tbomgvergunning.

Voor de zaakttypes bij Handhavingen, APV/Overig, Milieu.gebruik, Horeca en Infoaanvragen geldt dezelfde wijze van instellen.

## Meer dan één product/dienst per zaak

Indien in bovengenoemde instelling(en) de kolom *Getal1* de waarde 1 krijgt (en aangevinkt blijft) dan wordt:

  - het blok *Product/dienst* in het detailscherm van de zaak onzichtbaar
  - in het zaakportaal omgeving een tegel *Product/diensten* opgenomen die de mogelijkheid geeft om meer dan één combinatie product/betaler/contract per zaak toe te voegen.
  -

De gekozen producten, subproducten klanten, werkpakketten worden opgenomen in de tabel tbzaakproducten met een koppeling naar de hoofdzaak.

Indien de instelling *sectie: Product/Dienst Item:Inspecties* aangevinkt is kunnen ook vanuit het detailscherm van een inspectietraject (tbinspecties) producten/diensten worden toegevoegd. Een blok producten/diensten wordt dan zichtbaar op het detailscherm. De gekozen producten, subproducten klanten, werkpakketten worden opgenomen in de tabel tbzaakproducten met een koppeling naar de inspectiezaak.

### Extra opties

Daarnaast is de volgende optie mogelijk: Wanneer de kolom *Info* van bovenstaande instelling de waarde *ODRA* heeft, dan wordt na het kiezen van het product gekeken naar het voorkomen van dit product in de beheertabel *Combinaties product/klant/werkpakket* (tbprodwkpklant). Er zal dan alleen een klant gekozen worden waarvoor een regel bestaat in de combinatietabel voor het gekozen product. Na kiezen van de klant kan eveneens alleen een werkpakket gekozen worden waarvoor een regel bestaat in de combinatietabel voor het gekozen product en gekozen klant.

Bij Inspecties kijkt OpenWave naar de hoofdzaak waaraan het inspectietraject is verbonden. De kolom *info* wordt in dat geval bij de instelling van de module van de hoofdzaak overgenomen (dus als een inspectie is verbonden aan een omgevingzaak, dan kijkt OpenWave naar kolom *Info* van de instelling *Sectie: Product/Dienst, Item: Omgeving*.

**Let op:** voor deze instelling heeft *Getal1* de waarde 1 en is *Getal2* NIET gevuld.

Wanneer *Getal2* van bovenstaande instelling de waarde 1 krijgt, dan wordt in de detailkaart van de omgevingszaak een blok zichtbaar waarin de gebruiker  vooraf een klant en een werkpakket kan aanwijzen. Met deze instelling worden nieuwe kaarten in de tabel tbzaakproducten alvast gevuld met deze klant/werkpakket-waardes. De kolommen *klant* en *werkpakket* zijn in dat geval ook niet meer muteerbaar in tbzaakproducten.

Bij Inspecties kijkt OpenWave naar de hoofdzaak waaraan het inspectietraject is verbonden. De kolom *Getal2* wordt in dat geval bij de instelling van de module van de hoofdzaak overgenomen (dus als een inspectie is verbonden aan een omgevingzaak, dan kijkt OpenWave naar kolom *Getal2* van de instelling *Sectie: Product/Dienst, Item: Omgeving*.

De kolom *product* van tbzaakproducten is vrijelijk te kiezen uit de gedefinieerde producten bij het betreffende zaaktype (beheertegel *Zaaktypes omgeving*), of in het geval van inspecties uit de producten die gekoppeld zijn aan inspectie-aanleiding: beheerportaal-Nieuw, detailscherm van inspectietrajectsoorten (tbinspaanelding).

Echter wanneer:

  - de combinatie klant/werkpakket voorkomt in de beheertabel *Combinaties product/klant/werkpakket* (tbprodwkpklant)
  - EN de kolom *Info* van de instelling *Sectie: Product/Dienst, Item: Omgeving* heeft de waarde *ODR*

kan bij het nieuw opvoeren van een zaakproduct alleen gekozen worden uit de deze rijen van tbprodwkpklant (ook hier geldt weer dat in geval van inspecties de instelling van de hoofdmodule wordt gekozen).

## Autorisatie

Om producten/diensten te kunnen invoeren (= de omgevingszaak toekennen aan een combinatie product, klant en werkpakket) moet de inlogger het recht *Toevoegen van product/dienst* (tbomgrechten.dlcomgprdins) hebben. Voor het wijzigen moet de inlogger het recht *Wijzigen van product/dienst* (tbomgrechten.dlcomgprdedt) hebben. En voor het verwijderen van een combinatie product, klant en werkpakket bij een zaak moet de inlogger recht *Verwijderen van product/dienst* (tbomgrechten.dlcomgprddel) hebben.

Ook hier geldt dat voor prioducten/diensten verbonden aan een andere hoofdmodule OpenWave navenant kijkt naar bijv tbhhrechten.dlchahprddel

Voor het zien en wijzigen van een product/dienst bij een inspectietraject gelden de rechten voor inzien respectievelijk wijzigen van inspecties bij omgevingszaken (ongeacht de module), de zichtbaarheid van de plus-en min-knop is afhankelijk van rechten voor aanmaken en verwijderen van een inspectie bij omgeving. De daadwerkelijke rechten voor mogen aanmaken en verwijderen van product/dienst bij een inspectie zijn wel module afhankelijk. Zie ook onderaan deze pagina bij *Instellingen*.

## Definitie producten/klanten/werkpakketten

[<img src="/_media/openwave/applicatiebeheer/instellen_inrichten/productendienstenklantenwerkpakketten.jpg?w=800&amp;tok=b0b821" class="media" loading="lazy" alt="" width="800" />](/_detail/openwave/applicatiebeheer/instellen_inrichten/productendienstenklantenwerkpakketten.jpg?id=docs%3Aapplicatiebeheer%3Ainstellen_inrichten%3Aproducten_klanten_werkpakketten)

De producten worden in het zaakbeheer-portaal gedefinieerd achter de tegel *Productdefinitie* (tbproductdef) onder de kolom *Financiele afhandeling*. Een product kan via de koppeltabel tbproducten toegekend worden aan één of meer zaaktypes zoals onder tegel *Zaaktypes omgeving* (tbsoortomgverg). Binnen het detailscherm van een zaaktype kunnen dan meerdere producten worden gekozen.

Een of meer productdefinities kunnen ook worden gekoppeld aan een dnkey uit tbinspaanleiding in dezelfde koppeltabel tbproducten (*zaakbeheerprotaal, kolom: toezicht & handhaving, tegel: inspectietrajectensoorten* )

Subproducten worden in het beheerportaal *Zaakbeheer* gedefinieerd achter de tegel *Subproductdefinitie* (tbsubproducten) onder de kolom *Financiele Afhandeling*. Een subproduct kan via de koppeltabel tbsubproductdef toegekend worden aan één of meer producten. Dit gebeurt in het detailscherm van een productdefinitie.
Alle mogelijke klanten (tbproductklanten) worden gedefinieerd onder de tegel *Klanten (betalers)* onder de kolom *Financiele Afhandeling*.

Alle mogelijke werkpakketten (tbproductwerkpakketten) worden gedefinieerd onder de tegel *Werkpakketten*.

Onder de tegel *Combinatie producten, klanten en werkpakketten* kunnen nu alle bestaande combinaties gedefinieerd worden van de zaaktypes/insp.aanleiding, producten, subproducten, klanten en werkpakketten (tabel tbprodwkpklant), waarbij desgewenst aan elke combinatie een unieke code kan worden toegevoegd: de activiteitcode.

Op het detailscherm van een zaak of inspectietraject, of via een insertwizard bij meerdere producten per zaak (tbzaakproducten), kunnen de producten, subproducten en klanten en werkpakketten nu getrapt worden gekozen in zoverre is ingesteld dat de combinatie voor moet komen in de combinatietabel (tbprodklantwkp). Dit is het geval bij mogelijkheid A: per zaak kan maar één product/dienst worden aangewezen.

Bij mogelijkheid B: meerdere producten per zaak is het juist andersom: de gebruiker kiest hier in principe NIET uit de voorgeschreven mogelijkheden van de combinatietabel. De gebruiker kan kiezen uit alle producten bij het zaaktype, en daarbinnen uit alle subproducten bij het gekozen product. Verder kan de gebruiker kiezen uit alle klanten en werkpakketten. Zie hierboven voor de uitzondering.

Wat hierboven beschreven is voor omgevingszaken geldt ook voor de ander zaakmodules.

### Instellingen

  - *Sectie: Product/Dienst Item: Handhaving* en invoerrecht: tbhhrechten.dlchahprdins, muteerrecht: tbhhrechten.dlchahprdedt, verwijderrecht: tbhhrechten.dlchahprddel
  - *Sectie: Product/Dienst Item: APV/Overig* en invoerrecht: tbovrechten.dlcovvprdins, muteerrecht: tbovrechten.dlcovvprdedt, verwijderrecht: tbovrechten.dlcovvprddel
  - *Sectie: Product/Dienst Item: Horeca* en invoerrecht: tbhorrechten.dlchorprdins, muteerrecht: tbhorrechten.dlchorprdedt, verwijderrecht: tbhorrechten.dlchorprddel
  - *Sectie: Product/Dienst Item: Milieu/gebruik* en invoerrecht: tbmilvergrechten.dlcmilvergprdins, muteerrecht: tbmilvergrechten.dlcmilvergprdedt, verwijderrecht: tbmilvergrechten.dlcmilvergprddel
  - *Sectie: Product/Dienst Item: Infoaanvragen* en invoerrecht: tbinforechten.dlcinfoprdins, muteerrecht: tbinforechten.dlcinfoprdedt, verwijderrecht: tbinforechten.dlcinfoprddel
  - *Sectie: Product/Dienst Item: Inspecties* en:
      - indien bij Omgevingszaak dan invoerrecht: tbomgrechten.dlcomgprdins, verwijderrecht: tbomgrechten.dlcomgprddel
      - indien bij Handhavingszaak dan invoerrecht: tbhhrechten.dlchahprdins, verwijderrecht: tbhhrechten.dlchahprddel
      - indien bij APV/Overige zaak dan invoerrecht: tbovrechten.dlcovvprdins, verwijderrecht: tbovrechten.dlcovvprddel
      - indien bij Horecazaak dan invoerrecht: tbhorrechten.dlchorprdins, verwijderrecht: tbhorrechten.dlchorprddel
      - indien bij Infoaanvragen dan invoerrecht: tbinforechten.dlcinfoprdins, verwijderrecht: tbinforechten.dlcinfoprddel
      - indien bij Inrichtingen dan milieuvergunningrechten: invoerrecht: tbmilvergrechten.dlcmilvergprdins, verwijderrecht: tbmilvergrechten.dlcmilvergprddel
      - muteerrecht: tbomgrechten.dlcomginsedt (ongeacht de module!)
