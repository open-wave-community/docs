Sectie Encryption
=================

Hieronder de instellingen uit de configuratietabel (tbinitialisatie) van
de *Sectie: Encryption* gerangschikt op item. Zie `2-way encryptie van
externe
wachtwoorden </docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md>`__.

Items Configuratietabel
-----------------------

+--------+--------+--------------------------------------------------+
| Item   | Kolom  | Omschrijving                                     |
+========+========+==================================================+
| Method | Getal1 | geeft aan hoe een extern wachtwoord (t.b.v.      |
|        |        | koppeling OpenWave aan externe programma's)      |
|        |        | gecrypt kan worden opgeslagen:*Getal1* kan de    |
|        |        | waarde 1,2,of 3 bevatten. Indien een andere      |
|        |        | waarde dan 1,2,of 3 is ingevuld of wanneer de    |
|        |        | instelling niet bestaat, dan is de default       |
|        |        | encryptiemethode 1. Indien 1 dan wordt het       |
|        |        | ingebrachte wachtwoord plain opgeslagen          |
|        |        | voorafgegaan door '01\_'. Indien 2 dan wordt het |
|        |        | ingebrachte wachtwoord met de interne            |
|        |        | sleutelfunctie RemCrypt opgeslagen voorafgegaan  |
|        |        | door '02\_'. Indien 3 dan wordt het ingebrachte  |
|        |        | wachtwoord AES256 versleuteld opgeslagen         |
|        |        | voorafgegaan door '03\_'.                        |
+--------+--------+--------------------------------------------------+
