# Sectie Logon

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de _Sectie: Logon_ gerangschikt op item. Zie [Inloggen](/docs/probleemoplossing/programmablokken/inloggen?s%5b%5d=device.md). Zie ook de instellingen bij _Sectie: Inloggegevens_ voor instellingen m.b.t. wachtwoord vergeten.

## Items Configuratietabel

| Item     | Kolom        | Omschrijving      |
| -------- | ------------ | ----------------- |
| 2-factor | Aanvinkvakje | Indien aangevinkt |

en op de medewerkerskaart de kolom _2-factor type_ is ingevuld met de waarde 1 (email) of 2 (sms)

en op de medewerkerskaart de kolom _2-factor auth. opheffen_ NIET is aangevinkt

en het IP-adres waar vanuit wordt ingelogd voldoet aan geen enkel masker gedefinieerd in de kolom dviprange van de tabel tbipranges (beheerportaal-Nieuw) waarvoor geldt dat de kolom _dlskip2factor_ de waarde 'T' heeft (aangevinkt is) en vervaldatum leeg,

DAN zal de gebruiker met 2-factor moeten inloggen. |
| AfzenderAdres | Tekst |Deze instelling verwijst naar het afzenderadres van waar 2-factor unlock-codes worden verstuurd bij de huidige inlogmethode (indien de tekst leeg is dan zal het afzenderadres bepaald worden door het e-mailadres dat staat bij de kaart van de medewerker die de unlock-code opvraagt)

en naar het afzenderadres van waar de gebruikersnaam vergeten, wachtwoord vergeten en 2-factor unlock-codes worden verstuurd bij de nieuwe inlogmethode.

In dit laatste geval zal indien de tekst leeg is OF de instelling niet bestaat, de afzender <noreply@openwave.nl> zijn. |
| bcrypt_costs | Getal1 | Het aantal costs waarmee een nieuw password wordt gecrypt. Default 10. |
| ExternOLOLogin | Tekst |HTTPS authenticatienaam waarmee een extern REM programma zoals DUSK OpenWave API's kan aanroepen voor de verwerking van OLO-berichten en bijlages Deze moet overeenkomen met een medewerkerslogin. |
| ExternOLOPass | Tekst |HTTPS (plain) authenticatiepassword (basic) waarmee een extern REM programma zoals DUSK OpenWave API's kan aanroepen voor de verwerking van OLO-berichten en bijlages. Deze moet overeenkomen met een medewerkerspassword bij de genoemde medewerkerslogin. |
| Logo | Aanvinkvakje |Indien aangevinkt dan zal de tekst in het Tekstblok bepalen waar het logo zich zal bevinden. Indien uitgevinkt dan zal een default koptekst getoond zijn. |
| | Tekst | Geeft de positie aan van het logo. Mogelijke waardes zijn top (default) of left. Voor het scherm van de loginverklaringen zal het logo altijd _top_ worden uitgelijnd ongeacht welke waarde _Tekst_ heeft. |
| | Getal2 |Deze waarde bepaald de breedte van het logo, mits deze aan de linkerkant (left) is gepositioneerd. Default:195. |
| Minimumwachtwoordcomplexiteit | Getal1 |defaultwaarde = 3. Alleen 0,1,2,3 of 4. Geeft de mate van verplichte complexiteit aan bij het definiëren van een nieuw wachtwoord door de inlogger.

0 # too guessable: risky password. (guesses < duizend)

1 = very guessable: protection from throttled online attacks. (guesses < 1 miljoen)

2 = somewhat guessable: protection from unthrottled online attacks. (guesses < 100 miljoen)

3 = safely unguessable: moderate protection from offline slow-hash scenario. (guesses < 10 miljard)

4 = very unguessable: strong protection from offline slow-hash scenario. (guesses >= 10 miljard) |
| Pass_MinLength | Getal1 |Minimale lengte van een password. Default 9. |
| Password_MaxDagenSindsCreatie | Getal1 |Het aantal dagen dat een password geldig is. De datum dat een nieuw password wordt toegekend, wordt opgeslagen in de medewerkerstabel (dddatumpassword). Defaultwaarde = 365.

Nadat is ingelogd ontstaat er een sessie. Deze sessie is een aantal uren geldig conform de instelling onder _Getal1 van Sectie: Sessie Item: MaxUurSindsAanroep_ (default 12). Is de sessie verlopen moet opnieuw worden ingelogd. |
| WachtAantalMilliseconden | Getal1 |Het aantal milliseconden dat wordt gewacht na een foute inlogpoging alvorens een nieuwe poging kan worden gedaan. Default 3000. |
