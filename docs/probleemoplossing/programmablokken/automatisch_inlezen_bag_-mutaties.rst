Automatisch inlezen BAG- mutaties
=================================

Het inlezen van BAG-mutaties per gemeente kan handmatig (zie hiertoe de
uitleg onder hoofdstuk Import BAG-Mutaties van `Inlezen BAG Extract
en/of
BAG-mutaties </docs/probleemoplossing/programmablokken/inlezen_bag-extract_en_bag-mutaties.md>`__),
maar kan ook automatisch gebeuren door de scheduler zodanig in te
stellen.

Met het geautomatiseerd verwerken wordt aan het kadaster gevraagd welke
(laatste) maandmutaties er zijn. Deze lijst wordt vervolgens gefilterd
op de daartoe aangekruiste gemeentes in tb33gemeentes
(beheerportaal-Nieuw, kolom Administratie, tegel *Gemeentes*) op de
kolom dlmaandmutatiesbag (maandmutaties BAG ophalen). De zip-bestanden
met de maandmutaties worden vervolgens gedownload en verwerkt door
dezelfde API als bij de handmatige verwerking.

Noodzakelijke instellingen
--------------------------

-  **SOAP-endpoint kadaster**. In de kolom *Tekst* van de instelling
   *Sectie: KadasterBAG en Item: SoapEndpoint* dient het betreffende
   endpoint te worden opgegeven bijvoorbeeld:
   https://service10.kadaster.nl/gds2/afgifte/productstore. Dit endpoint
   wordt gebruikt om de lijst met aanwezige maandmutaties op te halen.
-  **Download-endpoint kadaster**. In de kolom *Tekst* van de instelling
   *Sectie: KadasterBAG en Item: DownloadEndpoint* dient het betreffende
   endpoint te worden opgegeven bijvoorbeeld:
   https://service30.kadaster.nl/gds2/download/productstore. Dit
   endpoint wordt gebruikt om de zip-bestanden met maandbestanden op te
   halen ter verwerking.
-  **Login**. In de kolom *Tekst* van de instelling *Sectie: KadasterBAG
   en Item: login* dient de loginnaam te staan waarmee OpenWave toegang
   heeft tot de BAG-mutatiebestanden van het kadaster.
-  **Password**. In de kolom *Tekst* van de instelling *Sectie:
   KadasterBAG en Item: Password* dient het password te staan waarmee
   OpenWave toegang heeft tot de BAG-mutatiebestanden van het kadaster.
   Deze kan in OpenWave desgewenst geëncrypt worden opgeslagen (`2-way
   encryptie van externe
   wachtwoorden </docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md>`__).
-  **Taskscheduler**. Regel in de
   `taskscheduler </docs/instellen_inrichten/taskscheduler.md>`__ met de
   naam *importmaandkadasterBAG* die bijv. ingesteld is op één keer per
   week inlezen (dus: - gebaseerd op een cyclus van 7 dagen- : 10080
   minuten ).
-  **Messagelog**. Het opvragen van de lijst met maandmutaties kan
   gelogd worden in de messagelog mits de instelling *Sectie:
   KadasterBag en Item: Messagelog* aangevinkt is.

Verwerking
----------

OpenWave kijkt eerst of er reeds een handmatig proces loopt op grond van
*Getal1* van de instelling met *Sectie: Operations en Item: inlezenbag*.
\|Indien *Getal1* de waarde 1 heeft gaat de geschedulede task niet door.
De geschedulede taak zet zelf ook deze instelling om te verhinderen dat
tijdens de automatische verwerking een handmatig proces gestart kan
worden.

Vervolgens wordt een kaart in tboperations aangemaakt met de naam
*inlezen bag* waarin de voortgang wordt bijgehouden met betrekking tot
ophalen zipbestanden.

Op het SOAP-endpiont kadaster wordt de lijst gevraagd van de
maandbestanden van alle gemeentes (artikelnummer 2531) op grond van de
15e dag van de vorige maand tot en met de 15e van de huidige maand.

Hierop filtert OpenWave die maandbestanden eruit van die gemeentes die
aangekruist zijn in tb33gemeente (beheerportaal-Nieuw, kolom
Administratie, tegel *Gemeentes*) op de kolom dlmaandmutatiesbag
(maandmutaties BAG ophalen).

Vervolgens wordt het laatste maandzipbestand voor elk van die gemeentes
opgehaald vanaf het download endpoint. De zip-bestanden worden verwerkt
door dezelfde API als bij handmatige verwerking.

Per maandbestand (dus per gemeente) wordt een nieuwe kaart in
tboperationslog aangemaakt met de operationsnaam zoals *Verwerken
ddf3a71372e74f3dbf97ee93d3104557_BAGGEM0197M-15072023-15082023.zip*. In
de log wordt de verwerking van het zip-bestand bijgehouden.
