# Adresrollen

Een contactpersoon wordt via een adresrol aan een zaak gekoppeld. Eén contactpersoon kan onder verschillende rollen aan eenzelfde zaak zijn verbonden.

![](/docs/img/applicatiebeheer/instellen_inrichten/adresrollen.png){ class="media" loading="lazy" alt="" width="400" }

Bovenstaande tekening kan soortgelijk ingevuld worden met tbhandhavingen en tbhandhcontactennn, tbinfoaanvragen, tbhorecavergunningen, tbovvergunningen, tbmilinrichtingen EN tbbezwaarberoep.

## Kolommen van tbadressoort

De adresrollen worden gedefinieerd in het beheerportaal-Nieuw onder de tegel *Adressoorten*.

- **Codering** (dvcode). De primary key van de tabel is een drie-letterige unieke code. Bijzondere waarden zijn:
  - **AVR** (aanvrager). OpenWave stelt de aanwezigheid van deze codering verplicht. Per hoofdzaak mag er maar één contactpersoon zijn met de rol AVR.
    - Een initiator uit een DSO of een OLO bericht of een StUF zakLk01 bericht wordt automatisch onder deze codering aan de omgevingszaak gekoppeld.
    - Indien de instelling *Sectie: Programma en Item: adresrolviazaaktype* NIET is aangevinkt, dan wordt bij het handmatig aanmaken van een nieuwe hoofdzaak verplicht een contactpersoon aangemaakt met deze AVR-rol. Dit geldt voor omgevingszaken, APV/overige zaken, horecazaken, milieu/gebruik zaken en infoaanvragen.
  - **GEM** (gemachtigde). OpenWave stelt de aanwezigheid van deze codering verplicht. Een gemachtigde uit een DSO of een OLO bericht of een StUF zakLk01 bericht wordt onder deze codering aan de omgevingszaak gekoppeld.
  - **HPC** (Handhaving primaire contactpersoon). OpenWave stelt de aanwezigheid van deze codering verplicht. Per handhavingszaak mag er maar één contactpersoon zijn met deze rol HPC.
    - bij het handmatig aanmaken van een nieuwe handhavingszaak wordt een contactpersoon aangemaakt met deze HPC-rol.
  - **MHC** (milieu hoofd contact). OpenWave stelt de aanwezigheid van deze codering verplicht. Per inrichting mag er maar één contactpersoon zijn met deze rol MHC.
- **Rol** (dvomschrijving)
- **Vervaldatum** (ddvervaldatum). Datum waar vanaf de rol niet meer gekozen kan worden bij het opvoeren van een contactpersoon.
- **Modules** (dvvantoepop). Bij welke moduleletters de rol kan worden gebruikt bij het opvoeren van een contactpersoon.
- **Deze rol van toepassing bij Bezwaar/beroep (ongeacht module)** (dlbezwaarberoep). Indien aangevinkt kan de rol gebruikt worden bij het opvoeren van een contactpersoon onder een deelzaak Bezwaarberoep.
- **Is rol voor contactpersoon uit verzoekbericht DSO** (dldsorolcontactpers). In het DSO-bericht kan naast initiator en gemachtigde ook een contactpersoon worden meegegeven. Hier kan worden aangevinkt onder welke rol deze contactpersoon moet worden toegevoegd bij de omgevingszaak. Dat mag NIET AVR en ook niet GEM zijn (dan is ook de aanvink-mogelijkheid niet zichtbaar). Er mag maar één rol voor de DSO-contactpersoon worden aangevinkt.
- **Is rol voor kwaliteitsborger uit verzoekbericht DSO**. Is bedoeld voor de kwaliteitsborger uit het DSO verzoek bericht. Er mag maar één rol worden aangevinkt.
- **Is rol voor aanvrager uit het originele DSO verzoek bij SWF advieszaak**. Bij het verwerken van de originele verzoek xml gegevens bij het aanmaken van een SWF advieszaak, zal gepoogd worden het contact bij de zaak aan te maken voor de originele aanvrager van het onderliggende DSO verzoek. Hier kan worden aangevinkt onder welke rol deze contactpersoon moet worden toegevoegd bij de omgevingszaak. Dat mag NIET AVR (dan is ook de aanvink-mogelijkheid niet zichtbaar). Er mag maar één rol voor de originele aanvrager worden aangevinkt.
- **Is rol voor gemachtigde uit het originele DSO verzoek bij SWF advieszaak**. Bij het verwerken van de originele verzoek xml gegevens bij het aanmaken van een SWF advieszaak, zal gepoogd worden het contact bij de zaak aan te maken voor de originele gemachtigde van het onderliggende DSO verzoek. Hier kan worden aangevinkt onder welke rol deze contactpersoon moet worden toegevoegd bij de omgevingszaak. Dat mag NIET AVR (dan is ook de aanvink-mogelijkheid niet zichtbaar). Er mag maar één rol voor de originele gemachtigde worden aangevinkt.
- **Is rol voor contactpersoon uit het originele DSO verzoek bij SWF advieszaak**. Bij het verwerken van de originele verzoek xml gegevens bij het aanmaken van een SWF advieszaak, zal gepoogd worden het contact bij de zaak aan te maken voor de originele contactpersoon van het onderliggende DSO verzoek. Hier kan worden aangevinkt onder welke rol deze contactpersoon moet worden toegevoegd bij de omgevingszaak. Dat mag NIET AVR (dan is ook de aanvink-mogelijkheid niet zichtbaar). Er mag maar één rol voor de originele contactpersoon worden aangevinkt.
- **OLO-mapping** (dvlvotag). Beetje dubbelop. Indien de rol is AVR dan hier invullen: `<LVO:isAangevraagdDoor>`. Indien de rol is GEM dan hier invullen: `<LVO:heeftGemachtigde>`.

## Adresrollen en (hoofd) Zaaktypes

Aan een hoofdzaaktype - met uitzondering van handhaving: daar geldt altijd adresrol HPC - bijvoorbeeld onder de beheertegel *Zaaktype omgeving*, kan een adresrol worden gekoppeld onder de kolom *Verplichte adressoort (rol)* (dvadressoortverpl). Deze kolom is van invloed in twee situaties:

  - Bij het aanmaken van een **StUF Zaak/dms creeerZaakbericht** naar een extern zaaksysteem/DMS vanuit een bepaalde (omgeving)zaak moet een initiator worden meegegeven. OpenWave kijkt naar deze kolom bij het betreffende zaaktype om te bepalen welke contactpersoon als initiator moet worden doorgegeven. Er zijn nu twee situaties:
    - Bij het zaaktype is inderdaad een adresrol opgegeven. Indien er bij de zaak onverhoopt meerdere contactpersonen zijn met diezelfde adresrol, dan neemt OpenWave degene met de hoogste dnkey. Indien er bij de zaak onverhoopt GEEN contactpersoon is met deze adresrol, dan volgt een foutmelding en gaat het creerzaakbericht niet door.
    - Bij het zaaktype is geen adresrol opgegeven (of dat kan niet zoals bij Handhaving). In dat geval gaat OpenWave er vanuit dat de organisatie zelf de initiator van de zaak is. De initiator wordt dan gedefinieerd door de instelling met *Sectie: Koppeling Zaak en Item: Zender_Organisatie*. In *Getal1* staat de dnkey van tbcontactadressen die als initiator moet dienen (die dus verwijst naar de organisatie zelf).
  - Bij het **handmatig aanmaken van een nieuwe zaak** kijkt OpenWave of de instelling *Sectie: Programma en Item: adresrolviazaaktype* is aangevinkt.
    - Zo ja - en de zaak is GEEN compartimentszaak -  dan geldt het volgende:
      - Indien bij het zaaktype waaronder de nieuwe zaak wordt aangemaakt een adresrol is aangegeven, dan moet de gebruiker een contactpersoon bij de nieuwe zaak aanmaken onder deze rol.
      - Indien bij het zaaktype waaronder de nieuwe zaak wordt aangemaakt GEEN adresrol is aangegeven, dan hoeft de gebruiker geen contactpersoon op te geven bij het aanmaken van een nieuwe zaak.
    - Zo niet, dan geldt voor alle zaaktypes dat de gebruiker verplicht een contactpersoon moet aanwijzen met de rol AVR (behalve bij handhavingszaken: daar geldt de verplichte rol HPC).

### Deelzaken en Inrichtingen en StUF creeerzaakbericht

Voor het doorgeven van een initiator bij:

  - een deelzaak Adviezen of Bezwaar/beroep of Inspectie
  - een dossierzaak op basis van een inrichting

gaat OpenWave er vanuit dat de organisatie zelf de initiator van de zaak is. De initiator wordt dan gedefinieerd door de instelling met *Sectie: Koppeling Zaak en Item: Zender_Organisatie*. In *Getal1* staat de dnkey van tbcontactadressen die als initiator moet dienen (die dus verwijst naar de organisatie zelf).

### Adresrollen en Unique constraints

Op de database is afgevangen:

  - Bij een omgevingzaak kan in de tabel tbomgcontactennn maar één rij voorkomen met de adresrol AVR
  - Bij een bouw/sloopzaak kan in de tabel tbbouwcontactennn maar één rij voorkomen met de adresrol AVR
  - Bij een APV/overige zaak kan in de tabel tbovwcontactennn maar één rij voorkomen met de adresrol AVR
  - Bij een horecazaak kan in de tabel tbhorecacontactennn maar één rij voorkomen met de adresrol AVR
  - Bij een milieu/gebruikzaak kan in de tabel tbmilvergcontactennn maar één rij voorkomen met de adresrol AVR
  - Bij een handhavingzaak kan in de tabel tbhandhcontactennn maar één rij voorkomen met de adresrol HPC
  - Bij een infoaanvraag kan in de tabel tbinfocontactennn maar één rij voorkomen met de adresrol AVR

Niet op de database, maar wel in programmacode is afgevangen:

  - Bij een [inrichting](/instellen_inrichten.md) kan in de tabel tbmilcontactennn maar één rij voorkomen met de adresrol MHC
