# Tegel Producten/Diensten

## Trigger

De tegel is een trigger voor het lijstscherm van _Producten/Diensten_ bij een APV/Overig zaak (zie: [Producten Klanten en Werkpakketten](/docs/instellen_inrichten/producten_klanten_werkpakketten.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval betekent dat dat de instelling _Sectie: Product/Dienst Item: APV/Overig_ aangevinkt moet zijn en dat _Getal1_ de waarde 1 heeft. (zie hieronder bij SQL-conditie).
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _apvoverig_producten/diensten_)
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _apvoverigdetail_
- Kolom: _Overig_
- Kopregel: _Producten/diensten_
- Dynamisch tegelopschrift: _getTileContent(apvoverig_producten/diensten,{id})_
- Actie: _getFlexList(SysStandardList,tbovvergunningen,{id},nil,apvoverig_producten/diensten)_
- SQL: _select case when d1logic = 'T' and dfnumber1 = 1 then 1 else 0 end from tbinitialisatie where upper(dvsectie) = 'PRODUCT/DIENST' and UPPER(dvitem) = 'APV/OVERIG'_

## Bijzonderheden

De kolommen Werkpakket en Klant zijn alleen muteerbaar indien de instelling Sectie: Product/Dienst Item: 'APV/Overig' aangevinkt is waarbij **Getal2** ongelijk is aan 1. Indien deze instelling namelijk wel de waarde 1 heeft, dan zijn deze kolommen in de bovenliggende detailkaart van de APV/Overig zaak te vullen in het blok Klant/Wkpt. Die waardes worden dan vanzelf overgenomen in tbzaakproducten.

De kolom product is vrijelijk te kiezen uit de gedefinieerde producten bij het betreffende zaaktype (beheer: zaaktypes APV/Overig).

Echter wanneer

- de combinatie klant/werkpakket voorkomt in de beheertabel _Combinaties product/klant/werkpakket_ (tbprodwkpklant)
- en de kolom _Info_ van de instelling _Sectie: Product/Dienst Item: Omgeving_ heeft de waarde 'ODR'

kan bij het nieuw opvoeren van een zaakproduct alleen gekozen worden uit de deze rijen van tbprodwkpklant.
