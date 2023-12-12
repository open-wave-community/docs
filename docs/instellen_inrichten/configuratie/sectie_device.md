# Sectie Device

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie/sectie_aanmaakmappen.md) (tbinitialisatie) van de *Sectie: Device* gerangschikt op item. Zie [Inloggen](/docs/probleemoplossing/programmablokken/inloggen.md).

## Items Configuratietabel

| Item | Kolom | Omschrijving |
|---|---|---|
| Unlock_Cookie_MaxDagenSindsCreatie | Getal1 |Default 365. Indien 2-factor is dit het aantal dagen dat het opgeslagen device waarvandaan wordt ingelogd, geldig blijft. Indien verlopen dan zal bij het inloggen om een unlock-code worden gevraagd die per sms of per email is opgestuurd. Deze unlock-code is evenzoveel uur geldig als ingesteld in *Unlock_Pin_MaxUurSindsCreatie*. Op de medewerkerskaart kan aangegeven worden of een gebruiker überhaupt gerechtigd is om zijn/haar device op te slaan. Indien dat niet het geval is zal dus altijd om een 2-factor unlockcode worden gevraagd. |
| Unlock_Pin_MaxUurSindsCreatie | Getal1 |Het aantal uur (default 1) dat de inlogger de tijd heeft om de unlockpincode in te voeren indien daar om gevraagd wordt bij het inloggen met 2-factor authenticatie. Mag ook een decimaal getal zijn. |
