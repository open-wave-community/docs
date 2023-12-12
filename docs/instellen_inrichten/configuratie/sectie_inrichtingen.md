 Sectie Inrichtingen

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie/README.md) (tbinitialisatie) van de _Sectie: Inrichtingen_ gerangschikt op item.

## Items Configuratietabel

| Item                      | Kolom        | Omschrijving                                                              |
|---------------------------|--------------|---------------------------------------------------------------------------|
| ArtikelBijMba             | Aanvinkvakje | Indien aangevinkt zal de insertWizard die een MBA-activiteit toevoegt aan een inrichting uit twee in plaats van een scherm bestaan. Met het tweede scherm kan de gebruiker een artikel aanwijzen op grond waarvan de MBA-paragraaf in het eerste scherm is gekozen. |
|                           | Getal1       | Indien de waarde 1, dan is op het detailscherm van de MBA-activiteit van een inrichting het blok artikel vergunningplicht zichtbaar. In dat blok kan uit de artikelen behorende bij de betreffende paragraaf een artikelnummer aangewezen worden op grond waarvan de vergunningplicht geldt. |
| BevoegdgezagDoorBor       | Aanvinkvakje | Indien aangevinkt dan wordt het bevoegd gezag bij de inrichting (vwfrmmilinrichtingen.dvomsbevoegdgezag) uitsluitend bepaald door de hoogste gezag van de gekoppelde BOR-coderingen (uit tbmilivb). Indien niet aangevinkt kan het bevoegd gezag worden overschreven door het aangevinkt zijn van de kolommen IPPC en/of BRZO op de inrichtingskaart. |
| DefaultCodeRubriekAsbest  | Tekst        | De dvcode uit tbmilrubriek die als default wordt gebruikt bij het opvoeren van een nieuwe kaart in tbmilasbest. Van belang bij kleurcodering op de interne kaart. |
| DefaultCodeRubriekLucht   | Tekst        | De dvcode uit tbmilrubriek die als default wordt gebruikt bij het opvoeren van een nieuwe kaart in tbmilemlucht. Van belang bij kleurcodering op de interne kaart. |
| DefaultCodeRubriekStal    | Tekst        | De dvcode uit tbmilrubriek die als default wordt gebruikt bij het opvoeren van een nieuwe kaart in tbmilstal. Van belang bij kleurcodering op de interne kaart. |
| EndpointExportInrkrtWFS   | Tekst        | De WFS-file onder de naam _OWEXportInrkrtWFS.Json_ wordt geplaatst op deze map. Aangezien de map waarop de file geplaatst wordt benaderbaar moet zijn door het externe Geo-systeem zal deze in samenspraak met REM worden afgesproken. Waarschijnlijk op een submap van de geïnstalleerde Geoserver zie [Data Op Kaart / Export Inrichtingen als WFS](/docs/instellen_inrichten/data_op_kaart.md). |
| Kaartlayers2en3           | Aanvinkvakje | Indien aangevinkt zijn bij het opstarten van de interne kaart vanuit een inrichting de layers 2 en 3 direct geopend (layer 2: opslag, stallen en kwetsbaregebouwen/locaties, layer 3: overige water, lucht diversen, asbest). |
| REVNamespaceIdentificatie | Tekst        | Wordt gevuld met de unieke namespace die onderdeel is van de identificaties in de export Json-files naar REV. Moet beginnen met NL.IMEV. en wordt gevolgd door de bronhouderscode. Dus bijvoorbeeld NL.IMEV.00002 Zie verder sectie REV. |
