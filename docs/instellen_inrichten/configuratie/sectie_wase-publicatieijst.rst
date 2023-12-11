Sectie Wase-publicatielijst

Hieronder de instellingen uit de
`configuratietabel </docs/instellen_inrichten/configuratie.md>`__
(tbinitialisatie) van de *Sectie: Wase-publicatielijst* gerangschikt op
item.

.. warning::
   er zijn meer instellingen van de *Sectie:
   Wase-publicatielijst* die gebruikt worden door de (deprecated)
   publicatielijst van Rem: een aparte installatie die aangevraagde en
   afgehandelde zaken publiceert op een kaart met doorverwijzing naar
   Open-Wave portal. Zie
   `Kaart </docs/probleemoplossing/module_overstijgende_schermen/kaart.md>`__.

Items Configuratietabel
-----------------------

+--------------------+--------+--------------------------------------+
| Item               | Kolom  | Omschrijving                         |
+====================+========+======================================+
| Map_def_lat        | Getal2 | moet gevuld zijn met de y-coördinaat |
|                    |        | (in rijksdriehoek) van het centrum   |
|                    |        | waaromheen de kaart moet starten     |
|                    |        | indien dit gegeven niet uit de       |
|                    |        | locatie gegevens gehaald kan worden  |
|                    |        | en uit de facultatieve instellingen  |
|                    |        | hieronder. Deze instelling moet      |
|                    |        | aanwezig zijn bij het starten van de |
|                    |        | Algemene Kaart                       |
+--------------------+--------+--------------------------------------+
| Map_def_lon        | Getal2 | moet gevuld zijn met de x-coördinaat |
|                    |        | (in rijksdriehoek) van het centrum   |
|                    |        | waaromheen de kaart moet starten     |
|                    |        | indien dit gegeven niet uit de       |
|                    |        | locatie gegevens gehaald kan worden  |
|                    |        | en uit de facultatieve instellingen  |
|                    |        | hieronder. Deze instelling moet      |
|                    |        | aanwezig zijn bij het starten van de |
|                    |        | Algemene Kaart                       |
+--------------------+--------+--------------------------------------+
| Map\ *def_lat*\ \* | Getal2 | Het \* in de itemnaam moet vervangen |
|                    |        | worden door een gemeente-id.         |
|                    |        | *Getal2* moet dan gevuld zijn met de |
|                    |        | y-coördinaat (in rijksdriehoek) van  |
|                    |        | het centrum van bedoelde gemeente    |
|                    |        | waaromheen de interne OpenWave-kaart |
|                    |        | moet starten indien dit gegeven niet |
|                    |        | uit de locatie gegevens gehaald kan  |
|                    |        | worden. Voorbeeld: met               |
|                    |        | *Map_def_lat_0450* wordt dus         |
|                    |        | aangegeven dat het gaat om de        |
|                    |        | y-coördinaat van het centrum van     |
|                    |        | Uitgeest. U moet dus evenzoveel      |
|                    |        | rijen aanmaken als er gemeentes zijn |
|                    |        | in uw OpenWave implementatie         |
+--------------------+--------+--------------------------------------+
| Map\ *def_lon*\ \* | Getal2 | Het \* in de itemnaam moet vervangen |
|                    |        | worden door een gemeente-id.         |
|                    |        | *Getal2* moet dan gevuld zijn met de |
|                    |        | x-coördinaat (in rijksdriehoek) van  |
|                    |        | het centrum van bedoelde gemeente    |
|                    |        | waaromheen de interne OpenWave-kaart |
|                    |        | moet starten indien dit gegeven niet |
|                    |        | uit de locatie gegevens gehaald kan  |
|                    |        | worden. Voorbeeld: met               |
|                    |        | *Map_def_lon_0450* wordt dus         |
|                    |        | aangegeven dat het gaat om de        |
|                    |        | x-coördinaat van het centrum van     |
|                    |        | Uitgeest. U moet dus evenzoveel      |
|                    |        | rijen aanmaken als er gemeentes zijn |
|                    |        | in uw OpenWave implementatie         |
+--------------------+--------+--------------------------------------+
