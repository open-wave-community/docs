# Sectie DUSK

Hieronder de instellingen uit de configuratietabel (tbinitialisatie) van de *Sectie: DUSK* voor verwerking van berichtverkeer via DUSK , gerangschikt op item.

Voorbeelden voor berichtverkeer via de DUSK zie:

* [Verwerking van StUF OLO/AIM berichten](/docs/probleemoplossing/programmablokken/olo_verwerking.md)
* [Verwerking zakLk01 en zakLk02 berichten](/docs/probleemoplossing/programmablokken/stuf_zaken_zaklk01_02-verwerking.md)

## Items Configuratietabel

| Item | Kolom | Omschrijving |
|---|---|---|
| WIN1252 | Aanvinkvakje |Vanaf 1.29 is de OpenWave database in karakterset UTF-8. Dit betekent dat de database een groter aantal tekens aan kan dan voorheen. Het voorheen filteren van tekens die niet konden worden opgeslagen in de OpenWave database is daarom niet meer van toepassing. Indien in uitzonderlijke geval het toch nodig is dat berichtverkeer over DUSK WEL de oude filtering toepast van tekens, dan dient men deze instelling aan te maken en aan te vinken. |
