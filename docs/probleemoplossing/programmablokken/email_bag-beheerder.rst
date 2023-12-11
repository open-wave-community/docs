Email naar BAG beheerder
========================

Er kan automatisch een email verzonden worden naar de BAG-beheerder van
de gemeente die hoort bij de betreffende locatie bij de volgende
triggers:

-  Vanuit het **omgevingdetailscherm** (zie `Detailscherm
   omgevingszaken </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken.md>`__
   i.v.m. de voorwaarden voor het enabled zijn van de knoppen) met:

   -  de knop achter de kolom *BAG initieel email* (ddinitbag). Deze
      knop kan de aanleiding zijn tot één van de volgende berichten:

      -  **Sloopmelding afgehandeld**. Dit is het geval indien de dnkey
         van de soort omgevingszaak (beheertegel *Zaaktypes omgeving*)
         gelijk is aan *Getal2* van de instelling *Sectie: Koppeling
         OLO* en *Item: MeldingOnderdeelSlopen*
      -  **Calamiteitenmelding ontvangen**. Dit is het geval indien de
         dnkey van de soort omgevingszaak (beheertegel *zaaktypes
         omgeving*) gelijk is aan *Getal2* van de instelling *Sectie:
         EmailNaarBagBeheerder* en *Item: Calamiteitenmelding*
      -  **Ontvankelijkheid**. Dit is het geval indien geen sloopmelding
         en geen calamiteitenmelding

   -  de knop voor het afhandelen (ddbesluitdatum). Deze knop kan de
      aanleiding zijn tot één van de volgende berichten:

      -  **Calamiteitenmelding afgehandeld**. Dit is het geval indien de
         dnkey van de soort omgevingszaak (beheertegel *Zaaktypes
         omgeving*) gelijk is aan *Getal2* van de instelling *Sectie:
         EmailNaarBagBeheerder* en *Item: Calamiteitenmelding*
      -  **Vergunning verleend**. Dit is het geval indien de dnkey van
         de soort omgevingszaak (beheertegel *Zaaktypes omgeving*) NIET
         gelijk is aan *Getal2* van de instelling *Sectie: Koppeling
         OLO* en *Item: MeldingOnderdeelSlopen*, en ook NIET gelijk aan
         *Getal2* van de instelling *Sectie: EmailNaarBagBeheerder* en
         *Item: Calamiteitenmelding*

   -  de knop voor het intrekken (ddingetrokken). Deze knop kan de
      aanleiding zijn tot één van de volgende berichten:

      -  **afzien van volledige sloop**. Dit is het geval indien de
         dnkey van de soort omgevingszaak (beheertegel *Zaaktypes
         omgeving*) gelijk is aan *Getal2* van de instelling *Sectie:
         Koppeling OLO* en *Item: MeldingOnderdeelSlopen*
      -  **aanvraag ingetrokken**. Dit is het geval indien de dnkey van
         de soort omgevingszaak (beheertegel *Zaaktypes omgeving*) NIET
         gelijk is aan *Getal2* van de instelling *Sectie: Koppeling
         OLO* en *Item: MeldingOnderdeelSlopen*

   -  vullen van na-verlening-ingetrokken (ddnaverlingetrokken). Deze
      knop is aanleiding tot het bericht **omgevingsvergunning
      ingetrokken**.

-  Vanuit het **onderdelenscherm** bij een omgevingszaak met:

   -  de knop *Start Melding BAG* (ddstartnaarbag). Deze knop is
      aanleiding tot het bericht **start bouw**
   -  de knop *Gereedmelding BAG* (ddnaagBaga). Deze knop is aanleiding
      tot het bericht **bouw gereed**

-  Vanuit het **handhavingdetailscherm** met:

   -  de knop achter de kolom **BAG initieel email** (ddinitbag)
   -  de knop voor het **afhandelen** (ddeinddatum). Deze knop kan
      aanleiding zijn voor het versturen van bericht naar BAG. Dit zal
      alleen zo zijn indien BAG initieel email is verstuurd.

De volgende algemene instellingen zijn daarbij verplicht
--------------------------------------------------------

-  In de de kolom Email BAGbeheerder (dvemailbagheheerder) van de tabel
   tb33 gemeente (beheertegel *Gemeentes*) moet voor de betrokken
   gemeentes het emailadres ingevoerd worden van de BAG-beheerder.
-  De inlogger die de knop indrukt moet ook een valide mailadres hebben
   (beheertegel *Medewerkers*).
-  De webmailinstellingen moeten kloppen, zie:
   `E-mail </docs/instellen_inrichten/email.md>`__.

Opbouw emailbericht
-------------------

De email wordt opgemaakt met bovenvermeld bericht als onderwerp
voorafgegaan door de OpenWave-zaakcode en eventueel de externe zaakcode
indien er een koppeling met zaaksysteem is. Daarna volgt een vast
gedeelte + een door de inlogger zelf toe te voegen tekst. Bijvoorbeeld:

.. code:: txt

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

De hyperlink moet gedefinieerd zijn in kolom *Info* van de instelling
*Sectie: Adviezen* en *Item: StandaardEmailTekstBody* waarbij het
programma de variabele %deeplink% automatisch vervangt door
'#omgevingdetail/ + de dnkey van de omgevingszaak OF (indien start
vanuit handhavingsdetail plaats vindt) #handhavingdetail/ + de dnkey van
de handhavingszaak.
