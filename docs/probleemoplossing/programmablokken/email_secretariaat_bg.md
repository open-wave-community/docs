# Email secretariaat bevoegd gezag/DIV vanuit geregistreerde documenten

**LET OP:** Deze functie is deprecated sinds versie 1.21. De kolom Naar
DIV/bevoegd gezag? (tbcorrespondentie.dlbevoegdgezag) is niet meer standaard in
het scherm opgenomen. Indien dit wel wordt gedaan (afwijkend scherm) is
onderstaande beschrijving nog steeds valide.

Vanuit het
[lijstscherm geregistreerde documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/lijst_geregistreerde_documenten_bij_zaak.md)
per zaak linksonder kan een email aan het secretariaat van het bevoegd gezag
(dat kan ook de eigen DIV afdeling zijn) verstuurd worden met daarin een
downloadlink naar de zaak en een opsomming van geregistreerde documenten met het
attribuut _naar bevoegd gezag aangevinkt (dlnaarbevoegdgezag)_. Met de link kan
het secretariaat de bedoelde documenten veilig downloaden. Het filter in de
lijst kan gebruikt worden om de lijst snel te filteren op deze eigenschap.
Onderaan de lijst is een downloadknop die het geselecteerde document download.
Deze knop is vooralsnog alleen zichtbaar indien de gebruiker het recht _Toelaten
geforceerde download geregistreerd document_ voor de betreffende module (bijv.
tbomgrechten.dlcomgcorregdwl).

ZIE voor een andere benadering documenten/verzendstroom het lemma
[Documenten/Verzendstroom](documenten_verzendstroom).

## Noodzakelijke instellingen

- De kolom **emailsecretariaat** (tb33gemeente.dvemailsecretariaat) van de
  gemeente (beheertegel _Gemeentes_) waar de zaak speelt moet gevuld zijn met
  een valide emailadres (de ontvanger van de email)
- EN de kolom **email van de inlogger** bij de medewerkerstabel moet gevuld zijn
  met een valide emailadres
- EN de **webmailinstellingen** moeten kloppen: zie bij Instellen/Inrichten
  [Email](../../../instellen_inrichten/email.md)
- EN de kolom _Tekst_ van instelling _Sectie: Documenten_ en _Item:
  StandaardEmailTekstAanhef_ moet gevuld zijn
- EN de kolom _Info_ van instelling _Sectie: Documenten_ en _Item:
  StandaardEmailTekstBody_ moet gevuld zijn met een deeplinkverwijzing naar het
  zaakportaal bijvoorbeeld:
  `[https://demo1.open-wave.nl/%deeplink%](https://demo1.open-wave.nl/%deeplink%)`
- EN de kolom _Tekst_ van instelling _Sectie: Documenten_ en _Item:
  StandaardEmailTekstBody_ moet gevuld zijn, waarbij de variabelen in kolom
  _Tekst_ of _Info_ van _StandaardEmailTekstBody_ als volgt worden gevuld:
  - %zaaknaam% met ZaakNaam (bijvoorbeeld bouwen van een carport) van
    bovenliggende hoofdzaak
  - %module% met:
    - omgevingszaak
    - OF apv/overige zaak
    - OF bouw/sloopzaak
    - OF infoaanvraag
    - OF handhavingszaak
    - OF milieu/gebruikszaak
    - OF horecazaak
    - OF inrichting
  - %soortvergunning% met het OpenWave zaaktype (bijvoorbeeld reguliere
    procedure)
  - %zaakcode% met de OpenWave zaakcodering
  - %dmszaakcode% met de externe zaak/DMS codering
  - %lokatie% met adres + plaats
  - %gemeente% met de gemeentenaam
  - %olonummer% met OLOnr
  - %deeplink% met hyperlink naar het betreffende zaakportaal.

## Voorbeeld email

![Emaildocumenten_download](../../img/applicatiebeheer/probleemoplossing/programmablokken/emaildocumentendownlaod.png){ class="media" loading="lazy" alt="" width="600" }

Het resultaat van bovenstaand voorbeeld in de body van een email:

```txt
Geachte secretariaatsmedewerker,

U kunt de zaakdocumenten m.b.t. zaakcode: 2014W0060. downloaden door onderstaande link te volgen.\\
Het betreft: Plaatsen van Carport (Reguliere procedure).\\
Bij u in het zaaksysteem mogelijk bekend onder nummer: 123456.\\

https://demo1.open-wave.nl/#omgevingdetail/7163

Het gaat om de volgende documenten:
aanvraag.docx - aanvraag - openbaar
beschikking.docx - beschikking - beperkt openbaar
```

Het onderwerp van de email is dus niet aanpasbaar. De opsomming van documenten
gebeurt ook automatisch (de geregistreerde documenten met eigenschap
dlnaarbevoegdgezag = 'T').

## Voorbeeld maken eigen tegel secretariaat/DIV met download-optie

De link in bovenstaand voorbeeld verwijst naar het zaakportaal alwaar de
opgesomde documenten onder de tegel _Geregistreerde documenten_ zijn op te
halen. De secretariaat/DV medewerker heeft een downloadknop tot zijn/haar
beschikking en kan filteren op 'bevoegd gezag/DIV' om de lijst te beperken.

Als dit niet genoeg is kan de applicatiebeheerder zelf een tegel maken op dit
portaal specifiek voor het secretariaat/DIV met daaronder een lijst van de
geregistreerde documenten met de eigenschap dlbevoegdgezag = 'T'. Hieronder een
voorbeeld voor omgevingszaken.

1. Maak in het omgevingsportaal een nieuwe tegel bijv. onder de kolom _Overig_
   met als kopregel _Te versturen stukken_ en als action
   _getFlexList(SysStandardList,tbomgvergunning,{id},,omg_vwfrmcorrespondentie_bg)_.

Hier staat dus eigenlijk dat in de standaardApi-tabel (onder beheertegel
_Tabellen standaardApi_) onder dvcode = _omg_vwfrmcorrespondentie_bg_ alle
informatie staat over wat onder die tegel getoond gaat worden. De tegel moet
alleen worden toegekend aan medewerkers van het secretariaat/DIV.

2. Maak in de genoemde standaardApi-tabel een nieuw record met dvcode =
   _omg_vwfrmcorrespondentie_bg_:

- Hoofdtabel- of viewnaam: vwfrmcorrespondentie
- Kolomnaam van de primary key: dnkey
- Tabelnaam waarop hoofdtabel/view is gebaseerd: tbcorresondentie
- Kolomnaam foreign key uit deze achterliggende tabel: dnkeyomgvergunningen
- Parenttabelnaam: tbomgvergunning
- Kolomnaam foreign key (uit hoofdtabel/view): dnkeyomgvergunningen
- Schermidentifier voor lijst: MDLC_getGeregistreerdeDocumentenList.xml
- Schermidentifier voor detail: MDDC_getGeregistreerdeDocumentenDetail.xml
- Kijkrechtenkolom: tbomgrechten.dlcomgcorvsb
- Action bij dubbel klikken op regel:
  getFlexdetail(SysStandardDetail,{id},omg_vwfrmcorrespondentie_bg)
- where clausule bij lijst: dlnaarbevoegdgezag = 'T'

3. Maak bij dit record een knop download:

- Hint cq itemomschrijving: download
- (L)ijst of (D)etail: L
- (L)inksonder of (I)temlist: L
- Icoonnummer: 43
- Action execute-rechtenkolom: tbomgrechten.dlcomgcorvsb
- Action: startwizard
- param1: haalGeregistreerdDocument
- param2: %keypointer%
- param3: W;forceerdownload
- param4: %query(omgeving_haalregdocparam4,%keypointer%)%

4. Tot slot maak de de genoemde query bij param4 van downloadknop met de naam
   _omgeving_haalregdocparam4_ in de beheertabel tbqueries:

```sql
select coalesce(dvgemeenteid,'') | | chr(59) | |
   case when dnkeycompartiment is null then '' else cast(dnkeycompartiment as character varying(10)) end | |
   chr(59) | | 'false'
   from vwfrmomgvergunningen where dnkeyomgvergunning =
     (select dnkeyomgvergunningen from tbcorrespondentie where dnkey = {id})
```
