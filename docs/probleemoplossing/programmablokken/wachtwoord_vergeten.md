# Wachtwoord/gebruikersnaam vergeten

Indien de instelling _Sectie: PreInlog en Item: GebruikersnaamVergeten_ is aangevinkt dan is de optie _gebruikersnaam vergeten_ zichtbaar in het inlogscherm. Met deze optie wordt de inlogger gevraagd een emailadres in te tikken, die vergeleken wordt met het emailadres op de medewerkerskaart. Indien OK (en uniek) wordt de loginnaam per email opgestuurd.

Indien de instelling _Sectie: PreInlog en Item: WachtwoordVergeten_ is aangevinkt dan is de optie _wachtwoord vergeten_ zichtbaar in het het inlogscherm. Met deze optie krijgt de inlogger een activeringscode per email (deze activeringscode wordt opgeslagen in de medewerkerstabel). Met die activeringscode wordt de inlogger doorgelinkt naar een scherm waarbij hij/zij een nieuw wachtwoord kan opgeven. Om de email met de activeringscode te kunnen ontvangen moet de instelling _Sectie: GenereerWachtwoord en Item: Afzender_ worden opgenomen in de configuratietabel. In de kolom _Tekst_ van dit configuratie-item moet de afzender van de activeringcode-email worden aangegeven (dit moet een valide email zijn, bijvoorbeeld: _<noreply@openwave.nl>_).

Indien voor de betreffende inlogger de 2-factor authenticatie aanstaat, zal OpenWave niet kijken naar de kolommen (in de medewerkerstabel) sms of email, maar vol gaan voor de sms-variant (immers, de activeringslink is al per email verstuurd). Indien dan OpenWave geen provider (zie web.sms instellingen) of geen 06-nummer vindt, dan komt de mededeling ontbrekende instellingen in beeld en stopt het proces.
DUS 2-factor per email gaat **NIET** samen met wachtwoordvergeten-functionaliteit.

## Procedure Gebruikersnaam vergeten

- Klik in het inlogscherm op gebruikersnaam vergeten
- Voer emailadres in en klik op _Versturen_
- Emailadres moet valide en uniek zijn in de database (tbmedewerkers.dvemail)
- Er mag niet meer dan een x aantal keer (_Getal1_ van de instelling _Sectie: Inloggegevens Item: MaxPogingenEmail_) een mail verstuurd zijn in de afgelopen 15 minuten
- Inlogscherm verschijnt, er kan ingelogd worden met gebruikersnaam en wachtwoord

### Mogelijke foutmeldingen

- Melding: _706: Ontbrekende instellingen_
- Oorzaak: De juiste web.mail-instellingen in de configuratie ontbreken.

- Melding: _Het door u opgegeven emailadres is niet valide._
- Oorzaak: Er is een ongeldig emailadres ingevoerd, bijvoorbeeld een adres zonder @.

- Melding: _Het door u opgegeven e-mailadres bestaat niet in ons systeem of is niet uniek. Probeer het nogmaals of neem contact op met OpenWave beheerder_ (dit contact is in te stellen met kolom _Tekst_ van instelling _Sectie: Inloggegevens Item: ContactMessage_)
- Oorzaak: De juiste gebruiker wordt geïdentificeerd aan de hand van het emailadres dat bij de medewerker is opgeslagen. Deze moet dus bestaan en uniek zijn in de database.

- Melding: _Het maximum aantal pogingen om inloggegevens op te vragen is overschreden. Probeer het later opnieuw._
- Oorzaak: Er is te vaak een mail verstuurd in 15 minuten.

## Procedure Wachtwoord vergeten zonder 2 Factor

- Klik in het inlogscherm op **Wachtwoord Vergeten**
- Voer emailadres in en klik op _Versturen_
- Er mag niet meer dan een x aantal keer (_Getal1_ van de instelling _Sectie: Inloggegevens Item: MaxPogingenEmail_) een mail verstuurd zijn in de afgelopen 15 minuten.
- Wanneer emailadres valide is en uniek bestaat in de database (tbmedewerkers.dvemail), dan wordt mail gestuurd met een activeringslink voor invoer nieuw wachtwoord
- Klik op link in de mail, invoerscherm verschijnt voor invoer nieuw wachtwoord (met herhaal). Er is een check of de link nog geldig is, anders foutmelding. Hoeveel uur een link geldig is instelbaar in _Getal1_ van _Sectie: Inloggegevens en Item: Activeringscode_MaxUurSindsCreatie_
- Wanneer nieuwe wachtwoord valide is (zie onder lemma inloggen), wordt deze opgeslagen
- Inlogscherm verschijnt, er kan ingelogd worden met gebruikersnaam en nieuw wachtwoord

### Mogelijke foutmeldingen zonder 2 factor

- Melding: _Deze activeringslink is niet meer geldig._
- Oorzaak: Link is niet meer geldig (instelling _Getal1_ van _Sectie: Inloggegevens en Item: Activeringscode_MaxUurSindsCreatie_. Deze zegt hoeveel uur na het ontvangen van de mail de link geldig is).

- Melding: _Het door u opgegeven nieuwe wachtwoord is niet valide._
- Oorzaak: Het wachtwoord kan worden afgekeurd op grond van diverse redenen, waaronder minimaal aantal karakters (niet instelbaar).

## Procedure Wachtwoord vergeten met 2 Factor

Dit betreft de inlogger waarvoor 2-factor aanstaat. Ter verificatie moet er nog een extra code ingevoerd worden, deze wordt per sms naar mobiel verstuurd.

NB: Ook al staat Type 2-factor voor de inlogger ingesteld op email, voor Wachtwoord vergeten zal de verificatiecode altijd via sms verstuurd worden en dat werkt dus alleen indien er een provider is (zie lemma SMS).

Zelfde stappen 1-6 als procedure Wachtwoord vergeten zonder 2FA. Dan nog extra:

- Wanneer nieuwe wachtwoord verstuurd is, dan verschijnt er invoerscherm voor invoer (pin)code
- Na akkoord (pin)code (code heeft een geldigheidsduur in uren, instelling _Getal1_ van _Sectie: Device_ en _Item: Unlock_Pin_MaxUurSindsCreatie_ default 1) dan wordt het nieuwe wachtwoord opgeslagen in database
- Inlogscherm verschijnt, er kan ingelogd worden met gebruikersnaam en nieuw wachtwoord.

### Mogelijke foutmeldingen met 2 factor

Zelfde mogelijke foutmeldingen als bij procedure Wachtwoord vergeten zonder 2Fa. Dan nog extra:

- Melding: _706: Ontbrekende instellingen_
- Oorzaak: Sms-service niet geconfigureerd.

- Melding: *Op dit account is geen mobiel telefoonnummer geregistreerd. Neem contact op met REM beheerder (De tekst REM beheerder kan vervangen worden door kolom *Tekst* van de instelling *Sectie: inloggegevens en Item: ContactMessage*)*
- Oorzaak: Er is geen mobiel telefoonnummer ingesteld op de kaart van de inlogger (dvmedewerker.dvmobiel).

- Melding: _Dit apparaat is niet geregistreerd of de registratie is verlopen. De nieuwe registratiecode kon niet naar u worden opgestuurd. Neem contact op met de beheerder_
- Oorzaak: mobiel nummer t.b.v. sms niet gevuld op de kaart van de inlogger.

- Melding: _Het maximum aantal om een registratiecode aan te vragen is overschreden. Probeer het later opnieuw._
- Oorzaak: Er is te vaak een code verstuurd binnen 15 minuten (instelling _Getal1_ van _Sectie: Inloggegevens en Item: MaxPogingenPincode_).

- Melding: _Ingevoerde code is niet geldig. Een nieuwe registratiecode is naar u opgestuurd._
- Oorzaak: Inlogger heeft foutieve code ingevoerd, er wordt nog een code verstuurd (tot MaxPogingenPincode is bereikt in 15 minuten).

## Overige condities en info

In de database in de medewerkerstabel wordt per inlogger een teller bijgehouden hoeveel keer in de afgelopen x tijd:

- Een mail met gebruikersnaam is verstuurd (als now() > ddloginnaamreset begint dnloginnaamteller weer opnieuw)
- Een mail met activeringslink voor nieuw wachtwoord is verstuurd (als now() > ddwwreset begint dnwwteller weer opnieuw)
- Een pincode is verstuurd voor wijzigen wachtwoord (als now() > ddpincodereset begint dnpincodeteller weer opnieuw)

De gegevens zijn zichtbaar in het detailscherm van de medewerkerskaart van de inlogger (alleen zichtbaar voor de beheerder).

De kolommen dvactiveringscode en ddactiveringscode worden leeg gemaakt als wachtwoord succesvol is gewijzigd.

## Email opmaak instellingen

Er is een aantal instellingen m.b.t. de onderwerp, ondertekening en bodytekst van de te versturen e-mails.
Zie hiervoor de instellingen bij [Sectie Inloggegevens](../../../instellen_inrichten/configuratie/sectie_inloggegevens.md). De meeste instellingen hebben een defaultwaarde.

Er is echter één gegeven dat per OpenWave-installatie apart moet worden aangepast: dat is de kolom _Info_ van _Sectie: Inloggegevens en Item: WachtwoordEmailTekstBody_. Daarin staat de tekst die getoond wordt in de mail die degene die het wachtwoord vergeten is krijgt te zien met daarin een activeringscode. Default staat er: Wanneer u op de onderstaande link klikt kunt u uw wachtwoord wijzigen: `[https://open-wave.nl/#wachtwoordvergeten/%link%](https://open-wave.nl/#wachtwoordvergeten/%link%.md)`. U dient het gedeelte `[https://open-wave.nl/](https://open-wave.nl/.md)` te vervangen met het domein waarop OpenWave bij u is geïnstalleerd zodat er bijvoorbeeld komt te staan: `[https://rommeldam.open-wave.nl:4444/#wachtwoordvergeten/%link%](https://rommeldam.open-wave.nl:4444/#wachtwoordvergeten/%link%.md)` (let op de slashes).
