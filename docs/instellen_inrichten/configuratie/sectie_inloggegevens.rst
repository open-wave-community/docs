Sectie Inloggegevens

Hieronder de instellingen uit de
`configuratietabel </docs/instellen_inrichten/configuratie.md>`__
(tbinitialisatie) van de *Sectie: Inloggegevens* gerangschikt op item.
Het gaat hier om de instellingen m.b.t. wachtwoord/gebruikersnaam
vergeten.

Zie ook de instellingen bij *Sectie: Logon* voor instellingen m.b.t.
normaal inloggen. Zie
`Inloggen </docs/probleemoplossing/programmablokken/inloggen.md>`__. Zie
ook *Sectie: PreInlog*.

Items Configuratietabel
-----------------------

+-----------------------------+--------+-----------------------------+
| Item                        | Kolom  | Omschrijving                |
+=============================+========+=============================+
| Activer                     | Getal  | Het aantal uur dat een      |
| ingscode_MaxUurSindsCreatie |        | activeringscode verstuurd   |
|                             |        | per email om een nieuw      |
|                             |        | wachtwoord in te voeren,    |
|                             |        | actief is. Default 2.       |
+-----------------------------+--------+-----------------------------+
| ContactMessage              | Tekst  | OpenWave zal een boodschap  |
|                             |        | laten zien wanneer het      |
|                             |        | verzenden van email of sms  |
|                             |        | is mislukt bij              |
|                             |        | wachtwoord/gebruikersnaam   |
|                             |        | vergeten. Die boodschap     |
|                             |        | eindigt met *neem contact   |
|                             |        | op met* gevolgd door de     |
|                             |        | waarde van deze tekst.      |
|                             |        | Default: de beheerder.      |
+-----------------------------+--------+-----------------------------+
| G                           | Info   | Bodytekst van de email bij  |
| ebruikersnaamEmailTekstBody |        | gebruikersnaam vergeten     |
|                             |        | bijvoorbeeld: *Hierbij      |
|                             |        | sturen wij u uw             |
|                             |        | gebruikersnaam voor         |
|                             |        | open-wave.nl.               |
|                             |        | Gebruikersnaam =            |
|                             |        | %inlognaam%*. waarbij       |
|                             |        | OpenWave on the fly de      |
|                             |        | string %inlognaam% zal      |
|                             |        | vervangen met de            |
|                             |        | gebruikers- c.q. inlognaam. |
+-----------------------------+--------+-----------------------------+
| Gebrui                      | Tekst  | Onderwerp van de email bij  |
| kersnaamEmailTekstOnderwerp |        | gebruikersnaam vergeten     |
|                             |        | bijvoorbeeld: *Uw           |
|                             |        | inloggegevens voor          |
|                             |        | OpenWave*.                  |
+-----------------------------+--------+-----------------------------+
| In                          | Tekst  | Aanhef van de email bij     |
| logVergetenEmailTekstAanhef |        | wachtwoord c.q.             |
|                             |        | gebruikersnaam vergeten.    |
|                             |        | Bijvoorbeeld *Geachte       |
|                             |        | %account%,*. OpenWave zal   |
|                             |        | de string *%account%* on    |
|                             |        | the fly vervangen door de   |
|                             |        | achternaam, voorvoegsel en  |
|                             |        | voorletters.                |
+-----------------------------+--------+-----------------------------+
| InlogVer                    | Tekst  | Ondertekening van de email  |
| getenEmailTekstHandtekening |        | bij wachtwoord c.q.         |
|                             |        | gebruikersnaam vergeten.    |
|                             |        | Bijvoorbeeld *Met           |
|                             |        | vriendelijke groeten, de    |
|                             |        | functioneel beheerder*.     |
+-----------------------------+--------+-----------------------------+
| MaxPogingenEmail            | Getal1 | Aantal pogingen dat         |
|                             |        | OpenWave binnen een         |
|                             |        | kwartier mag doen om een    |
|                             |        | email te versturen bij      |
|                             |        | gebruikersnaam/wachtwoord   |
|                             |        | vergeten. Default 5.        |
+-----------------------------+--------+-----------------------------+
| MaxPogingenPincode          | Getal1 | Aantal pogingen dat         |
|                             |        | OpenWave binnen een         |
|                             |        | kwartier mag doen om een    |
|                             |        | sms met pincode te          |
|                             |        | versturen bij wachtwoord    |
|                             |        | vergeten. Default 5.        |
+-----------------------------+--------+-----------------------------+
| WachtwoordEmailTekstBody    | Info   | Bodytekst van de email bij  |
|                             |        | wachtwoord vergeten met een |
|                             |        | link. Bijvoorbeeld "Wanneer |
|                             |        | u op de onderstaande link   |
|                             |        | klikt kunt u uw wachtwoord  |
|                             |        | wijzigen:                   |
|                             |        | ``                          |
|                             |        | [https://rommeldam.open-wav |
|                             |        | e.nl:4444/#wachtwoordverget |
|                             |        | en/%link%](https://rommelda |
|                             |        | m.open-wave.nl:4444/#wachtw |
|                             |        | oordvergeten/%link%.md)``". |
|                             |        | U dient hier het domein van |
|                             |        | uw open-wave installatie in |
|                             |        | te voeren gevolgd door de   |
|                             |        | string                      |
|                             |        | */#                         |
|                             |        | wachtwoordvergeten/%link%*. |
|                             |        | OpenWave vervangt deze      |
|                             |        | string on the fly met een   |
|                             |        | activeringslink, waarbij de |
|                             |        | gebruiker in een scherm     |
|                             |        | komt om een nieuw           |
|                             |        | wachtwoord in te voeren.    |
+-----------------------------+--------+-----------------------------+
| Wa                          | Tekst  | Onderwerp van de email bij  |
| chtwoordEmailTekstOnderwerp |        | wachtwoord vergeten.        |
|                             |        | Bijvoorbeeld *Uw wachtwoord |
|                             |        | opnieuw instellen voor      |
|                             |        | OpenWave*.                  |
+-----------------------------+--------+-----------------------------+
