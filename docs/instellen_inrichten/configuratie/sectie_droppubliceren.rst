Sectie DROPPUBLICATIES

Hieronder de instellingen uit de configuratietabel (tbinitialisatie) van
de *Sectie: DROPPUBLICATIES* gerangschikt op item. Zie:
`Drop </docs/instellen_inrichten/drop.md>`__

Items Configuratietabel
-----------------------

+--------------------------+--------------+--------------------------+
| Item                     | Kolom        | Omschrijving             |
+==========================+==============+==========================+
| ``Al                     | Aanvinkvakje | Indien aangevinkt is zal |
| lowAllHostnameVerifier`` |              | de Openwave Cloud        |
|                          |              | instemmen met een        |
|                          |              | self-signed of verlopen  |
|                          |              | (server)certificaat bij  |
|                          |              | een verbinding onder     |
|                          |              | https                    |
+--------------------------+--------------+--------------------------+
| ``ApvOverig``            | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | het blok DROP in het     |
|                          |              | detailscherm in het      |
|                          |              | detailscherm van de      |
|                          |              | APV-Overige zaak         |
|                          |              | zichtbaar                |
+--------------------------+--------------+--------------------------+
| Endpoint_isAlive         | Tekst        | Hier kunt u de URL       |
|                          |              | opgeven van het endpoint |
|                          |              | waarvan u de verbinding  |
|                          |              | met KOOP wil testen      |
|                          |              | bijv. (alles aan elkaar  |
|                          |              | zonder spaties):         |
|                          |              | ``[http                  |
|                          |              | s://acceptatie.overheids |
|                          |              | servicebus.com/opentunne |
|                          |              | l/](https://acceptatie.o |
|                          |              | verheidsservicebus.com/o |
|                          |              | pentunnel/.md) 000000033 |
|                          |              | 32595610000/drop/3epas`` |
+--------------------------+--------------+--------------------------+
| Gebruikprojectlocaties   | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | wordt de                 |
|                          |              | hoofdprojectlocatie (uit |
|                          |              | tbzaakkadperc) met       |
|                          |              | voorrang meegewogen bij  |
|                          |              | het bepalen van de       |
|                          |              | coordinaten              |
+--------------------------+--------------+--------------------------+
| header_action            | Tekst        | De kolom dient gevuld te |
|                          |              | worden met (alles aan    |
|                          |              | elkaar zonder spaties):  |
|                          |              | ``"[http://schemas.k     |
|                          |              | oopwrp.nl/2020/01/drp/ap |
|                          |              | i/](http://schemas.koopw |
|                          |              | rp.nl/2020/01/drp/api/.m |
|                          |              | d) IDossierService/VoegD |
|                          |              | ossierToeEnPubliceer"``, |
|                          |              | Let op! er moeten quotes |
|                          |              | om de URL staan          |
+--------------------------+--------------+--------------------------+
| ``Horeca``               | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | het blok DROP in het     |
|                          |              | detailscherm van de      |
|                          |              | Horeca zichtbaar         |
+--------------------------+--------------+--------------------------+
| HTTPSo                   | Tekst        | Moet gevuld zijn met     |
| apAction_VoegDocumentToe |              | *Vo                      |
|                          |              | egDossierToeEnPubliceer* |
+--------------------------+--------------+--------------------------+
| LOCALEFEESTDAG\_%        | Datum        | Indien gevuld dan zal    |
|                          |              | OpenWave rekening houden |
|                          |              | met deze dag bij het     |
|                          |              | bepalen van het          |
|                          |              | publicatiemoment. Het is |
|                          |              | mogelijk meerdere        |
|                          |              | feestdagen op te nemen   |
|                          |              | door % te vervangen met  |
|                          |              | een benaming van de      |
|                          |              | feestdag (bv.            |
|                          |              | L                        |
|                          |              | OCALEFEESTDAG_Dierendag) |
+--------------------------+--------------+--------------------------+
| ``MessageLog``           | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | wordt het                |
|                          |              | berichtenverkeer omtrent |
|                          |              | de DROPPublicaties       |
|                          |              | gelogd in de Messagelog. |
|                          |              | Indien niet aangevinkt   |
|                          |              | en de DROP wordt         |
|                          |              | aangeroepen vanuit één   |
|                          |              | specifieke zaak          |
|                          |              | (detailpagina van één    |
|                          |              | item van de lijst DROP   |
|                          |              | op openingsportaal)      |
|                          |              | wordt toch gelogd        |
+--------------------------+--------------+--------------------------+
| ``Milieugebruik``        | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | het blok DROP in het     |
|                          |              | detailscherm van         |
|                          |              | Milieu/gebruik zichtbaar |
+--------------------------+--------------+--------------------------+
| ``Omgeving``             | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | het blok DROP in het     |
|                          |              | detailscherm van de      |
|                          |              | Omgevingszaak zichtbaar  |
+--------------------------+--------------+--------------------------+
