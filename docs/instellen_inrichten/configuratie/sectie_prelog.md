# Sectie PreInlog

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de *Sectie: PreInlog* gerangschikt op item.

## Items Configuratietabel

| Item | Kolom | Omschrijving |
|---|---|---|
| ApplicationColor | Tekst |Indien gevuld dan wordt de ingevulde tekst gebruikt als kleurthema voor OpenWave. Deze is default blauw maar kan aangepast worden middels deze instelling. De opties voor de waarde van tekst (en dus voor kleurthema's) zijn: green, red, blue, magenta, orange. De kleuropties worden benoemd in kolom *Info* |
| ApplicationLegacy| Aanvinkvakje |Indien aangevinkt dan wordt de vormgeving van OpenWave in legacy modus weergegeven. Default aangevinkt. Indien de instelling uitgevinkt wordt dan zal de weergave van OpenWave volgens nieuwe vormgeving zijn. Deze is nog in ontwikkeling in versie 1.29. Vandaar voor nu default aangevinkt |
| GebruikersinformatieOpslaan | Aanvinkvakje |Indien aangevinkt worden bij het inloggen device en browsergegevens van de inlogger opgeslagen in de tabel tbgebruikersinformatie (zie Service centrum onder tegel *Gebruikersstatistieken*). Deze informatie wordt default 90 dagen bewaard, tenzij anders ingesteld in *Getal1* van *Sectie: Gebruikersinformatie Item: AantalDagenOpslaan* |
| GebruikersnaamVergeten | Aanvinkvakje |Indien aangevinkt komt in het inlogscherm de optie *gebruikersnaam vergeten* |
| IpCheck| Aanvinkvakje | Indien deze instelling niet bestaat, of wel bestaat en is aangevinkt, wordt er bij alle verzoeken aan de webserver een IP check uitgevoerd. Dit is ter bevordering van de veiligheid en dus aan te raden. Indien deze instelling WEL bestaat en NIET is aangevinkt, zal er geen IP check worden gedaan.|
| WachtwoordVergeten | Aanvinkvakje | Indien aangevinkt komt in het inlogscherm de optie *wachtwoord vergeten* |
| getAccess | Aanvinkvakje | Vanaf 1.28 is de default inlogmethode getAcccess. Dit betekent dat indien de instelling NIET bestaat, alsnog getAccess de inlogmethode is. Indien de instelling aangevinkt is dan is getAccess ook van toepassing. Wil men toch van de oude inlogmethode (getAuthorisation) gebruik maken dan kan dit door de instelling WEL aan te maken, maar NIET aan te vinken|
| ProductNaam | Aanvinkvakje | Moet aangevinkt zijn voor de werking van getAccess |
| | Tekst | OpenWave|

