Sectie Koppeling BRP
====================

Hieronder de instellingen uit de
`configuratietabel </docs/instellen_inrichten/configuratie.md>`__
(tbinitialisatie) van de *Sectie: KoppelingBRP* gerangschikt op item.
Zie `BRP (GBA)
bevraging </docs/probleemoplossing/programmablokken/bpr_bevraging.md>`__.

Items Configuratietabel
-----------------------

+--------------------------+--------------+--------------------------+
| Item                     | Kolom        | Omschrijving             |
+==========================+==============+==========================+
| AllowAllHostnameVerifier | Aanvinkvakje | Indien aangevinkt is zal |
|                          |              | de Openwave Cloud        |
|                          |              | instemmen met een        |
|                          |              | self-signed of verlopen  |
|                          |              | (server)certificaat bij  |
|                          |              | een verbinding onder     |
|                          |              | https.                   |
+--------------------------+--------------+--------------------------+
| HTT                      | Tekst        | Soapaction voor          |
| PSoapActionStelGbavVraag |              | vraag-bericht Competent. |
|                          |              | Moet zijn:               |
|                          |              | *stelGbavVraag*.         |
+--------------------------+--------------+--------------------------+
| Messagelog               | Aanvinkvakje | Indien aangevinkt worden |
|                          |              | de uitgaande Competent   |
|                          |              | vraagberichten gelogd in |
|                          |              | de beheertabel           |
|                          |              | tbmessagelog indien ook  |
|                          |              | de algemene instelling   |
|                          |              | *Sectie: OWB en Item:    |
|                          |              | Messagelog* is           |
|                          |              | aangevinkt.              |
+--------------------------+--------------+--------------------------+
