Sectie SWF
==========

Hieronder de instellingen uit de
`configuratietabel </docs/instellen_inrichten/configuratie.md>`__
(tbinitialisatie) van de *Sectie: SWF* (samenwerkingsfunctionaliteit)
gerangschikt op item.

Items Configuratietabel
-----------------------

+-----------------------+--------------+-----------------------+---+
| Item                  | Kolom        | Omschrijving          |   |
+=======================+==============+=======================+===+
| ActieverzoekNwezaak   | Aanvinkvakje | Indien aangevinkt dan |   |
|                       |              | leidt elk             |   |
|                       |              | binnenkomend          |   |
|                       |              | actieverzoek tot een  |   |
|                       |              | nieuwe omgevingszaak. |   |
|                       |              | Ook indien SWF        |   |
|                       |              | ruimte-id al          |   |
|                       |              | voorkomt.             |   |
|                       |              | Compartiment heeft    |   |
|                       |              | eigen kolom           |   |
|                       |              | tbcompartiment        |   |
|                       |              | .ActieverzoekNwezaak. |   |
+-----------------------+--------------+-----------------------+---+
| AlgemeenEndpoint      | Tekst        | Hier dient het        |   |
|                       |              | algemene gedeelte van |   |
|                       |              | het endpoint van de   |   |
|                       |              | landelijke            |   |
|                       |              | samenwe               |   |
|                       |              | rkingsfunctionaliteit |   |
|                       |              | te staan bijvoorbeeld |   |
|                       |              | ``[ht                 |   |
|                       |              | tps://pkio.service.pr |   |
|                       |              | e.omgevingswet.overhe |   |
|                       |              | id.nl/](https://pkio. |   |
|                       |              | service.pre.omgevings |   |
|                       |              | wet.overheid.nl/.md)  |   |
|                       |              | overheid/samenwerken/ |   |
|                       |              | api/behandelen/v4/``. |   |
+-----------------------+--------------+-----------------------+---+
| ClientCertificaatNaam | Tekst        | In de kolom *Tekst*   |   |
|                       |              | dient de naam van het |   |
|                       |              | certificaat te staan  |   |
|                       |              | namelijk              |   |
|                       |              | *digikoppeling.open-w |   |
|                       |              | ave.nl_20210624.p12*. |   |
+-----------------------+--------------+-----------------------+---+
| CertificaatPassword   | Tekst        | In de kolom *Tekst*   |   |
|                       |              | dient het password    |   |
|                       |              | van het certificaat   |   |
|                       |              | gecrypt opgeslagen te |   |
|                       |              | worden. Deze gecrypte |   |
|                       |              | waarde wordt door REM |   |
|                       |              | aangeleverd (de       |   |
|                       |              | string begint met     |   |
|                       |              | waarde *02\_*).       |   |
+-----------------------+--------------+-----------------------+---+
| CertificaatType       | Tekst        | In de kolom *Tekst*   |   |
|                       |              | dient het type van    |   |
|                       |              | het certificaat te    |   |
|                       |              | staan namelijk        |   |
|                       |              | *PKCS12*.             |   |
+-----------------------+--------------+-----------------------+---+
| MessageLog_In         | Aanvinkvakje | Indien aangevinkt dan |   |
| komendeActieverzoeken |              | worden de berichten   |   |
|                       |              | van de operatie       |   |
|                       |              | *Ophalen Inkomende    |   |
|                       |              | Open Actieverzoeken*  |   |
|                       |              | gelogd in de          |   |
|                       |              | beheertabel           |   |
|                       |              | tbmessagelog. Dit is  |   |
|                       |              | niet altijd nodig en  |   |
|                       |              | bovendien verzwarend, |   |
|                       |              | vandaar deze          |   |
|                       |              | instelling. Uitgaande |   |
|                       |              | berichten naar        |   |
|                       |              | samenwe               |   |
|                       |              | rkingsfunctionaliteit |   |
|                       |              | vanuit de tegel       |   |
|                       |              | *Samenwerkingsruimte* |   |
|                       |              | bij een               |   |
|                       |              | omgevingszaak, worden |   |
|                       |              | wel altijd gelogd in  |   |
|                       |              | de tabel tbmessagelog |   |
|                       |              | (mits de instelling   |   |
|                       |              | *Sectie: OWB, Item:   |   |
|                       |              | MessageLog*           |   |
|                       |              | aangevinkt is).       |   |
+-----------------------+--------------+-----------------------+---+
| MessageLog_Synchr     | Aanvinkvakje | Indien aangevinkt dan |   |
| oniseerOpenSWFRuimtes |              | worden de berichten   |   |
|                       |              | van de operatie       |   |
|                       |              | *Synchro              |   |
|                       |              | niseerOpenSWFRuimtes* |   |
|                       |              | gelogd in de          |   |
|                       |              | beheertabel           |   |
|                       |              | tbmessagelog. Dit is  |   |
|                       |              | niet altijd nodig en  |   |
|                       |              | bovendien verzwarend, |   |
|                       |              | vandaar deze          |   |
|                       |              | instelling. Uitgaande |   |
|                       |              | berichten naar        |   |
|                       |              | samenwe               |   |
|                       |              | rkingsfunctionaliteit |   |
|                       |              | vanuit de tegel       |   |
|                       |              | *Samenwerkingsruimte* |   |
|                       |              | bij een               |   |
|                       |              | omgevingszaak, worden |   |
|                       |              | wel altijd gelogd in  |   |
|                       |              | de tabel tbmessagelog |   |
|                       |              | (mits de instelling   |   |
|                       |              | *Sectie: OWB, Item:   |   |
|                       |              | MessageLog*           |   |
|                       |              | aangevinkt is).       |   |
+-----------------------+--------------+-----------------------+---+
| OINvanZender          | Tekst        | In de kolom *Tekst*   |   |
|                       |              | dient het OIN-nummer  |   |
|                       |              | te staan van de       |   |
|                       |              | (hort) organisatie    |   |
|                       |              | die OpenWave gebruikt |   |
|                       |              | en die dus in de      |   |
|                       |              | whitelist voor moet   |   |
|                       |              | komen. Bijvoorbeeld   |   |
|                       |              | de omgevingsdienst    |   |
|                       |              | ODDEVALLEI zal        |   |
|                       |              | *                     |   |
|                       |              | 00000001852282229000* |   |
|                       |              | als waarde moeten     |   |
|                       |              | invullen. Een         |   |
|                       |              | compartiment heeft    |   |
|                       |              | eigen kolom:          |   |
|                       |              | tbcompar              |   |
|                       |              | timent.dvswfoinzender |   |
|                       |              | waarin een opsomming  |   |
|                       |              | van OIN-nummers -     |   |
|                       |              | gescheiden door       |   |
|                       |              | puntkomma - die bij   |   |
|                       |              | het compartiment van  |   |
|                       |              | toepassing zijn voor  |   |
|                       |              | het binnenhalen van   |   |
|                       |              | actieverzoeken        |   |
|                       |              | opgegeven kan worden. |   |
+-----------------------+--------------+-----------------------+---+
|                       | Info         | In de kolom *dvinfo*  |   |
|                       |              | kunnen OIN-nummers    |   |
|                       |              | opgesomd worden       |   |
|                       |              | gescheiden door een   |   |
|                       |              | puntkomma die - naast |   |
|                       |              | de host uit kolom     |   |
|                       |              | *Tekst* - ook worden  |   |
|                       |              | opgevraagd bij het    |   |
|                       |              | binnenhalen van       |   |
|                       |              | actieverzoeken        |   |
|                       |              | (samenwerkingsverband |   |
|                       |              | gemeentes zoals BEL). |   |
+-----------------------+--------------+-----------------------+---+
| verta                 | Getal1       | De documenten in het  |   |
| lingVertrouwelijkheid |              | SWF krijgen           |   |
|                       |              | vertro                |   |
|                       |              | uwelijkheidsindicatie |   |
|                       |              | *SV (strikt           |   |
|                       |              | vertrouwelijk)* of    |   |
|                       |              | *RV (regulier         |   |
|                       |              | vertrouwelijkheid)*.  |   |
|                       |              | Met deze instelling   |   |
|                       |              | kan men aangeven      |   |
|                       |              | welke dnkey uit       |   |
|                       |              | tbvertrouwelijkheid   |   |
|                       |              | correspondeert met de |   |
|                       |              | vertro                |   |
|                       |              | uwelijkheidsindicatie |   |
|                       |              | opgegeven in SWF.     |   |
|                       |              | Bestaat deze          |   |
|                       |              | instelling niet (of   |   |
|                       |              | is er een foutieve    |   |
|                       |              | dnkey opgegeven bij   |   |
|                       |              | *Getal1* dan wel      |   |
|                       |              | *Getal2*) dan kijkt   |   |
|                       |              | het programma naar de |   |
|                       |              | default               |   |
|                       |              | vertrouwelijkheid     |   |
|                       |              | voor OLO/DSO          |   |
|                       |              | documenten zoals      |   |
|                       |              | opgegeven in kolom    |   |
|                       |              | *Tekst* van           |   |
|                       |              | instelling *Sectie:   |   |
|                       |              | KoppelingDOCNAARDMS   |   |
|                       |              | Item:                 |   |
|                       |              | OloVertrouwelijkheid* |   |
|                       |              | (voor compartiment    |   |
|                       |              | naar                  |   |
|                       |              | tbcompartiment.dvolod |   |
|                       |              | sovertrouwelijkheid). |   |
|                       |              | In *Getal1* kan men   |   |
|                       |              | de                    |   |
|                       |              | tbve                  |   |
|                       |              | rtrouwelijkheid.dnkey |   |
|                       |              | opgeven voor          |   |
|                       |              | indicatie **SV**.     |   |
+-----------------------+--------------+-----------------------+---+
|                       | Getal2       | In *Getal2* kan men   |   |
|                       |              | de                    |   |
|                       |              | tbve                  |   |
|                       |              | rtrouwelijkheid.dnkey |   |
|                       |              | opgeven voor          |   |
|                       |              | indicatie **RV**.     |   |
+-----------------------+--------------+-----------------------+---+
