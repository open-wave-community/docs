Tegel Producten/Diensten
========================

Trigger
-------

De tegel is een trigger voor het lijstscherm van *Producten/Diensten*
bij een Infoaanvraag (zie: `Producten Klanten en
Werkpakketten </docs/instellen_inrichten/producten_klanten_werkpakketten.md>`__).

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval
      betekent dat dat de instelling *Sectie: Product/Dienst Item:
      Infoaanvragen* aangevinkt moet zijn en dat *Getal1* de waarde 1
      heeft (zie hieronder bij SQL-conditie).

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing (codering *info_producten/diensten*)
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *infodetail*
-  Kolom: *Overig*
-  Kopregel: *Producten/diensten*
-  Dynamisch tegelopschrift:
   *getTileContent(info_producten/diensten,{id})*
-  Actie:
   *getFlexList(SysStandardList,tbinfoaanvragen,{id},nil,info_producten/diensten)*
-  SQL:

.. code:: sql

   select case when d1logic = 'T' and dfnumber1 = 1 then 1 else 0 end
     from tbinitialisatie
     where upper(dvsectie) = 'PRODUCT/DIENST'
     and UPPER(dvitem) = 'INFOAANVRAGEN'

Bijzonderheden
--------------

De kolommen **Werkpakket** en **Klant** zijn alleen muteerbaar indien de
instelling *Sectie: Product/Dienst Item: Infoaanvragen* aangevinkt is
waarbij **Getal2** ongelijk is aan 1. Indien deze instelling namelijk
wel de waarde 1 heeft, dan zijn deze kolommen in de bovenliggende
detailkaart van de infoaanvraag te vullen in het blok **Klant/Wkpt**.
Die waardes worden dan vanzelf overgenomen in tbzaakproducten.

De kolom **Product** is vrijelijk te kiezen uit de gedefinieerde
producten bij het betreffende zaaktype (beheer: zaaktypes
infoaanvragen).

Echter wanneer:

-  de combinatie klant/werkpakket voorkomt in de beheertabel
   *Combinaties product/klant/werkpakket* (tbprodwkpklant)
-  en de kolom *Info* van de instelling *Sectie: Product/Dienst Item:
   Infoaanvragen* heeft de waarde 'ODR'

kan bij het nieuw opvoeren van een zaakproduct alleen gekozen worden uit
de deze rijen van tbprodwkpklant.
