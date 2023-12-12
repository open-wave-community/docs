# Ophalen met CMIS

## Instellingen

Het **endpoint** van de DMS-server die de CMIS berichten verwerkt:

- _Sectie: KoppelingDOCNAARDMS_
- _Item: Ontvangstadres_cmis_
- _Tekst_: het endpoint (bijvoorbeeld [https://doc.mijndms.nl/alfresco/cmisatom](https://doc.mijndms.nl/alfresco/cmisatom.md)).

De **loginnaam** die OpenWave moet gebruiken voor toegang tot de DMS-server met rechten om mappen te maken/verwijderen en documenten te plaatsen/verwijderen:

- _Sectie: KoppelingDOCNAARDMS_
- _Item: Login_cmis_
- _Tekst_: de loginnaam.

Het **password** dat OpenWave moet gebruiken voor toegang tot de DMS-server:

- _Sectie: KoppelingDOCNAARDMS_
- _Item: Pass_cmis_
- _Tekst_: het password

Zie ook: [2-way encryptie van externe wachtwoorden](/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md).

### Indeling

OpenWave gaat er met het CMIS-protocol van uit dat de documenten in het DMS logisch ingedeeld zijn naar op zijn minst Module en zaakcodering in een mappenstructuur achter de repository (de centrale plaats).

De weerslag van die mappenstructuur van het DMS wordt in OpenWave genoteerd met instellingen per module onder de _Sectie: AanmaakMappen_.

Als er bijvoorbeeld 5 mappen bestaan in het DMS om documenten in te delen onder een omgevingszaak dan worden er ook 5 regels gedefinieerd in OpenWave onder _Sectie: AanmaakMappen_ waarbij de kolom _Item_ begint met 'Omgeving\_'.

Bijvoorbeeld Omgeving_basis, Omgeving_OLO, Omgeving_adviezen en Omgeving_inspecties et cetera.

In de kolommen _Info_ van de betreffende regel komen de mappen van de DMS-repository te staan (in UNC-notatie). Zie voorbeeld verderop.

De kolom _Item_ begint dus afhankelijk van de module met:

- indien module = V dan 'Inrichting\_'
- indien module = W dan 'Omgeving\_'
- indien module = B dan 'Bouw\_'
- indien module = O dan 'Overige\_'
- indien module = H dan 'Handhaving\_'
- indien module = C dan 'Horeca\_'
- indien module = E dan 'MilGebr\_'
- indien module = I dan 'Info\_'

#### Zaak/Inrichting

Indien documenten worden opgevraagd vanuit het zaakportal of het detailscherm van een zaak of inrichting, dan zoekt OpenWave naar de mappen in het DMS die genoemd staan in de kolom _Info_ van de programma-instellingen onder _Sectie: AanmaakMappen_ bij de betreffende module (d.w.z. waarvan de kolom _Item_ begint met 'Omgeving*' of 'Inrichting*' of 'Handhaving' of ….) en waarbinnen de kolom _Getal1_ de waarde 4 voorkomt (bijvoorbeeld 4 of 14 of 42).

Ook de submappen hierachter worden meegenomen. Van alle documenten die OpenWave op deze mappen tegenkomt wordt een lijst gemaakt waaruit de gebruiker verder kan kiezen.

#### Advies

Indien documenten worden opgevraagd vanuit het adviesdetailscherm van een zaak dan zoekt OpenWave naar de mappen in het DMS die genoemd staan in de kolom _Info_ van de programma-instellingen onder _Sectie: AanmaakMappen_ bij de betreffende module (d.w.z. waarvan de kolom _Item_ begint met 'Omgeving*' of 'Inrichting*' of 'Handhaving' of ….) en waarbinnen het _Getal1_ de waarde 1 voorkomt (bijvoorbeeld 1 of 12 of 41).

#### Bezwaar/beroep

Indien documenten worden opgevraagd vanuit het bezwaarberoep detailscherm van een zaak dan zoekt OpenWave naar de mappen in het DMS die genoemd staan in de kolom _Info_ van de programma-instellingen onder _Sectie: AanmaakMappen_ bij de betreffende module (d.w.z. waarvan de kolom _Item_ begint met 'Omgeving*' of 'Inrichting*' of 'Handhaving' of ….) en waarbinnen het _Getal1_ de waarde 5 voorkomt (bijvoorbeeld 5 of 52 of 51).

#### Inspectie

Indien documenten worden opgevraagd vanuit het inspectiedetailscherm van een zaak of bij een inrichting dan zoekt OpenWave naar de mappen in het DMS die genoemd staan in de kolom _Info_ van de programma-instellingen onder _Sectie: AanmaakMappen_ bij de betreffende module (d.w.z. waarvan de kolom _Item_ begint met 'Omgeving*' of 'Inrichting*' of 'Handhaving' of ….) en waarbinnen het _Getal1_ de waarde 2 voorkomt (bijvoorbeeld 2 of 12 of 42).

Wilt u vanuit de basiskaart van een zaak ook alle documenten zien die horen bij de adviezen of inspecties of bezwaar/beroep van die zaak, dan moet u ervoor zorgen dat de adviezen en inspecties in de mappenstructuur in het DMS als submap achter die van de hoofdzaak komen.

In de mappen zoals die in kolom _Info_ zijn gedefinieerd zal OpenWave eerst nog een substitutie uitvoeren op de volgende variabelen:

- `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaar/beroep of inspectie (geldt niet voor de regels met _Getal1_ = 4 en waarvan kolom _Item_ begint met Inrichting\_)
- `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaar/beroep of inspectie (geldt niet voor de regels met _Getal1_ = 4 en waarvan kolom _Item_ begint met Inrichting\_)
- `%zaaknr%` met de wavezaakcode van de hoofdzaak (of met het inrichtingsnummer indien Inrichting)
- `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen bij _Getal1_ = 2)
- `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen bij _Getal1_ = 1)
- `%bezwaarnr%` met de wavezaakcode van de bezwaar/beroep kaart (dus alleen bij _Getal1_ = 5).

Voorbeeld:

OpenWave\Omgeving\%zaakjaar%\ `%zaaknr%`

wordt na substitutie bijvoorbeeld

OpenWave\Omgeving\2012\2013RP0044\

Uiteindelijk leveren deze instellingen dus een aantal mappen op waar het programma gaat kijken naar documenten bijvoorbeeld:

- OpenWave\Omgeving\2012\2013RP0044\
- OpenWave\Omgeving\2012\2013RP0044\Adviezen
- OpenWave\Omgeving\2012\2013RP0044\Inspecties
- OpenWave\Omgeving\2012\2013RP0044\OLO

Alle documenten van deze mappen worden op de Toon Documentenlijst geplaatst en kunnen eventueel gedownload worden.

### OLO-bijlagen

Dit geldt alleen voor de situatie dat OpenWave via een DIGI-koppelaar rechtstreeks berichten ontvangt van het OLO en de OLO- bijlagen door de DIGI-koppelaar op een vooraf afgesproken verplaatsmap in het DMS -bijvoorbeeld: 'Inbox'' - plaats.Elk OLO-nummer krijgt hierachter een eigen submap bijvoorbeeld: Inbox/1234.
Op die laatste map worden alle bijlagen geplaatst voor OLO-aanvraagnummer 1234.

In OpenWave wordt deze verplaatsmap ingesteld in de kolom _Tekst_ (dus bijvoorbeeld 'Inbox') van de programma- instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: VerplaatsmapOLO_.

Bij het opvragen van de documentenlijst bij een OpenWave zaak (omgeving) waarbij het OLO-nummer is gevuld, zal het programma de OLO-bijlagen die aangetroffen worden op de bijbehorende verplaatsmap verplaatsen naar de correcte map onder het Wave-zaaknummer.

Die correcte doelmap moet wel eenduidig ingesteld zijn en dat gebeurt in één van de regels in de programma-instellingen bij _Sectie: AanmaakMappen_ en waarbij _Item_ begint met 'Omgeving\_'. Op één van die regels moet _Getal2_ de waarde 1 hebben.

Er mag dus maar één regel zijn in _Sectie: AanmaakMappen_ en _Item_ begint met 'Omgeving\_' die aan deze eis voldoet.

Is bovenstaande het geval dan zal bij het opvragen van de documentenlijst bij een omgevingszaak met een gevuld OLO-nummer (en alleen daar) het programma eerst kijken op de verplaatsmap van het DMS bij het betreffende OLO-nummer. Indien daar documenten staan dan worden deze verplaatst naar de doelmap.

Mocht een document al bestaan op de doelmap, dan wordt deze overschreven. Het programma maakt de verplaatsmap (inbox + OLO-nummer) leeg.

Daarna pas wordt de reguliere Toon Documentenlijst getoond waarin dan ook de OLO-bijlagen zichtbaar zijn.
