SMS
===

Instellingen die nodig zijn om vanuit OpenWave via een telecomprovider
een sms-bericht te sturen (bij inloggen met 2-factor). Naast een valide
telefoonnummer in de kolom dvmobiel van tbmedewerkers (zonder spaties en
hyphens) gaat het om de volgende instellingen in tbinitialisatie
(beheertegel *Configuratie*).

-  De kolom *Tekst* van *Sectie: Web.sms en Item: endpoint* vullen met
   het endpoint van die telecomprovider, waarmee een contract is
   afgesloten voor het versturen van sms'jes, bijvoorbeeld
   ``https://api.spryngsms.com/api/send.php`` (oude variant) of
   ``https://rest.spryngsms.com/api/simple/message`` (nieuwe variant).
-  De kolom *Tekst* van *Sectie: Web.sms en Item: username* vullen met
   de inlognaam voor dat endpoint
-  De kolom *Tekst* van *Sectie: Web.sms en Item: password* vullen met
   het wachtwoord voor dat endpoint. Zie ook: `2-way encryptie van
   externe
   wachtwoorden </docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md>`__
-  De kolom *Tekst* van *Sectie: Web.sms en Item: sender* vullen met de
   gewenste afzender van het sms-bericht bijv. *beheer OW*. LET OP deze
   tekst mag maximaal 11 karakters bevatten.

OpenWave zendt een bericht met daarin opgenomen het telefoonnummer van
de inlogger, de unlockcode en de afzender naar het endpoint van de web
service van de telecomprovider. Die provider zet dat bericht om in een
sms.

Returncoderingen van SPRYNG (zie Messaglog)
-------------------------------------------

========== =========================
Returncode Returncodering
========== =========================
1          Succesvol ontvangen
100        Missende parameter
101        Gebruikersnaam te lang
102        Gebruikersnaam te kort
103        Wachtwoord te kort
104        Wachtwoord te lang
105        Bestemming te kort
106        Bestemming te lang
107        Afzender te lang
108        Afzender te kort
109        Inhoud te lang
110        Inhoud te kort
200        Veiligheidsfout
201        Onbekende route
202        Route toegang overtreding
203        Onvoldoende credits
800        Technische fout
========== =========================
