 Sectie Inloggegevens

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de _Sectie: Inloggegevens_ gerangschikt op item. Het gaat hier om de instellingen m.b.t. wachtwoord/gebruikersnaam vergeten.

Zie ook de instellingen bij _Sectie: Logon_ voor instellingen m.b.t. normaal inloggen. Zie [Inloggen](/docs/probleemoplossing/programmablokken/inloggen.md).
Zie ook _Sectie: PreInlog_.

## Items Configuratietabel

| Item | Kolom | Omschrijving |
| ---- | ----- | ------------ |
| Activeringscode_MaxUurSindsCreatie | Getal | Het aantal uur dat een activeringscode verstuurd per email om een nieuw wachtwoord in te voeren, actief is. Default 2. |
| ContactMessage | Tekst | OpenWave zal een boodschap laten zien wanneer het verzenden van email of sms is mislukt bij wachtwoord/gebruikersnaam vergeten. Die boodschap eindigt met _neem contact op met_ gevolgd door de waarde van deze tekst. Default: de beheerder. |
| GebruikersnaamEmailTekstBody | Info | Bodytekst van de email bij gebruikersnaam vergeten bijvoorbeeld: _Hierbij sturen wij u uw gebruikersnaam voor open-wave.nl. Gebruikersnaam = %inlognaam%_. waarbij OpenWave on the fly de string %inlognaam% zal vervangen met de gebruikers- c.q. inlognaam. |
| GebruikersnaamEmailTekstOnderwerp | Tekst | Onderwerp van de email bij gebruikersnaam vergeten bijvoorbeeld: _Uw inloggegevens voor OpenWave_. |
| InlogVergetenEmailTekstAanhef | Tekst | Aanhef van de email bij wachtwoord c.q. gebruikersnaam vergeten. Bijvoorbeeld _Geachte %account%,_. OpenWave zal de string _%account%_ on the fly vervangen door de achternaam, voorvoegsel en voorletters. |
| InlogVergetenEmailTekstHandtekening | Tekst | Ondertekening van de email bij wachtwoord c.q. gebruikersnaam vergeten. Bijvoorbeeld _Met vriendelijke groeten, de functioneel beheerder_. |
| MaxPogingenEmail | Getal1 | Aantal pogingen dat OpenWave binnen een kwartier mag doen om een email te versturen bij gebruikersnaam/wachtwoord vergeten. Default 5. |
| MaxPogingenPincode | Getal1 | Aantal pogingen dat OpenWave binnen een kwartier mag doen om een sms met pincode te versturen bij wachtwoord vergeten. Default 5. |
| WachtwoordEmailTekstBody | Info | Bodytekst van de email bij wachtwoord vergeten met een link. Bijvoorbeeld "Wanneer u op de onderstaande link klikt kunt u uw wachtwoord wijzigen: `[https://rommeldam.open-wave.nl:4444/#wachtwoordvergeten/%link%](https://rommeldam.open-wave.nl:4444/#wachtwoordvergeten/%link%.md)`". U dient hier het domein van uw open-wave installatie in te voeren gevolgd door de string _/#wachtwoordvergeten/%link%_. OpenWave vervangt deze string on the fly met een activeringslink, waarbij de gebruiker in een scherm komt om een nieuw wachtwoord in te voeren. |
| WachtwoordEmailTekstOnderwerp | Tekst | Onderwerp van de email bij wachtwoord vergeten. Bijvoorbeeld _Uw wachtwoord opnieuw instellen voor OpenWave_. |