# Email naar BAG beheerder

Er kan automatisch een email verzonden worden naar de BAG-beheerder van de gemeente die hoort bij de betreffende locatie bij de volgende triggers:

- Vanuit het **omgevingdetailscherm** (zie [Detailscherm omgevingszaken](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken.md) i.v.m. de voorwaarden voor het enabled zijn van de knoppen) met:
  - de knop achter de kolom _BAG initieel email_ (ddinitbag). Deze knop kan de aanleiding zijn tot één van de volgende berichten:
    - **Sloopmelding afgehandeld**. Dit is het geval indien de dnkey van de soort omgevingszaak (beheertegel _Zaaktypes omgeving_) gelijk is aan _Getal2_ van de instelling _Sectie: Koppeling OLO_ en _Item: MeldingOnderdeelSlopen_
    - **Calamiteitenmelding ontvangen**. Dit is het geval indien de dnkey van de soort omgevingszaak (beheertegel _zaaktypes omgeving_) gelijk is aan _Getal2_ van de instelling _Sectie: EmailNaarBagBeheerder_ en _Item: Calamiteitenmelding_
    - **Ontvankelijkheid**. Dit is het geval indien geen sloopmelding en geen calamiteitenmelding
  - de knop voor het afhandelen (ddbesluitdatum). Deze knop kan de aanleiding zijn tot één van de volgende berichten:
    - **Calamiteitenmelding afgehandeld**. Dit is het geval indien de dnkey van de soort omgevingszaak (beheertegel _Zaaktypes omgeving_) gelijk is aan _Getal2_ van de instelling _Sectie: EmailNaarBagBeheerder_ en _Item: Calamiteitenmelding_
    - **Vergunning verleend**. Dit is het geval indien de dnkey van de soort omgevingszaak (beheertegel _Zaaktypes omgeving_) NIET gelijk is aan _Getal2_ van de instelling _Sectie: Koppeling OLO_ en _Item: MeldingOnderdeelSlopen_, en ook NIET gelijk aan _Getal2_ van de instelling _Sectie: EmailNaarBagBeheerder_ en _Item: Calamiteitenmelding_
  - de knop voor het intrekken (ddingetrokken). Deze knop kan de aanleiding zijn tot één van de volgende berichten:
    - **afzien van volledige sloop**. Dit is het geval indien de dnkey van de soort omgevingszaak (beheertegel _Zaaktypes omgeving_) gelijk is aan _Getal2_ van de instelling _Sectie: Koppeling OLO_ en _Item: MeldingOnderdeelSlopen_
    - **aanvraag ingetrokken**. Dit is het geval indien de dnkey van de soort omgevingszaak (beheertegel _Zaaktypes omgeving_) NIET gelijk is aan _Getal2_ van de instelling _Sectie: Koppeling OLO_ en _Item: MeldingOnderdeelSlopen_
  - vullen van na-verlening-ingetrokken (ddnaverlingetrokken). Deze knop is aanleiding tot het bericht **omgevingsvergunning ingetrokken**.
- Vanuit het **onderdelenscherm** bij een omgevingszaak met:
  - de knop _Start Melding BAG_ (ddstartnaarbag). Deze knop is aanleiding tot het bericht **start bouw**
  - de knop _Gereedmelding BAG_ (ddnaagBaga). Deze knop is aanleiding tot het bericht **bouw gereed**
- Vanuit het **handhavingdetailscherm** met:
  - de knop achter de kolom **BAG initieel email** (ddinitbag)
  - de knop voor het **afhandelen** (ddeinddatum). Deze knop kan aanleiding zijn voor het versturen van bericht naar BAG. Dit zal alleen zo zijn indien BAG initieel email is verstuurd.

## De volgende algemene instellingen zijn daarbij verplicht

- In de de kolom Email BAGbeheerder (dvemailbagheheerder) van de tabel tb33 gemeente (beheertegel _Gemeentes_) moet voor de betrokken gemeentes het emailadres ingevoerd worden van de BAG-beheerder.
- De inlogger die de knop indrukt moet ook een valide mailadres hebben (beheertegel _Medewerkers_).
- De webmailinstellingen moeten kloppen, zie: [E-mail](/docs/instellen_inrichten/email.md).

## Opbouw emailbericht

De email wordt opgemaakt met bovenvermeld bericht als onderwerp voorafgegaan door de OpenWave-zaakcode en eventueel de externe zaakcode indien er een koppeling met zaaksysteem is. Daarna volgt een vast gedeelte + een door de inlogger zelf toe te voegen tekst.
Bijvoorbeeld:

```txt
Geachte BAG-beheerder,

Dit is een automatische melding aangemaakt vanuit de OpenWave applicatie.

Hieronder de kenmerken van belang voor uw BAG-registratie.
OpenWave-zaakcode: 2012W0599
DMS-zaakcode:
Zaaknr bevoegd gezag:
Locatieadres: Flessenpad 3013 Rommeldam
Betreft: het plaatsen van twee overkappingen
Ontvankelijkheidsverklaring 2016-11-08

Om deze zaak rechtstreeks te raadplegen, klikt u op onderstaande link.
https://demo1.open-wave.nl/#omgevingdetail/59641
Dit is een zelf ingetikte aanvulling
```

De hyperlink moet gedefinieerd zijn in kolom _Info_ van de instelling _Sectie: Adviezen_ en _Item: StandaardEmailTekstBody_ waarbij het programma de variabele %deeplink% automatisch vervangt door '#omgevingdetail/ + de dnkey van de omgevingszaak OF (indien start vanuit handhavingsdetail plaats vindt) #handhavingdetail/ + de dnkey van de handhavingszaak.
