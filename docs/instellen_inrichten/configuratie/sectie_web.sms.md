# Sectie Web.sms

Hieronder de instellingen uit de configuratietabel (tbinitialisatie) van de *Sectie: Web.sms* gerangschikt op item.
Instellingen die nodig zijn om vanuit OpenWave een SMS-dienst aan te kunnen spreken.
Zie [SMS](/docs/instellen_inrichten/sms.md).

## Items Configuratietabel

| Item     | Kolom | Omschrijving                                                                                      |
|----------|-------|---------------------------------------------------------------------------------------------------|
| endpoint | Tekst | Het endpoint van die telecomprovider, waarmee een contract is afgesloten voor het versturen van sms'jes. |
| password | Tekst | Het wachtwoord voor dat endpoint (wordt geencrypt opgeslagen).                                    |
| sender   | Tekst | De afzender van het sms-bericht bijv. *beheer OW*. LET OP deze tekst mag maximaal 11 karakters bevatten. |
| username | Tekst | De inlognaam voor het *endpoint*.                                                                 |
