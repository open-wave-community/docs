# Tegel Product

## Trigger

De tegel is een trigger voor een detailscherm van het _Product_ bij een handhavingzaak (zie: [Producten Klanten en Werkpakketten](/instellen_inrichten/producten_klanten_werkpakketten.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval betekent dat dat de instelling _Sectie: Product/Dienst Item: Handhaving_ aangevinkt moet zijn en dat _Getal1_ leeg is (zie hieronder bij SQL-conditie).
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _handhaving_prod_)
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _handhavingdetail_
- Kolom: _Overig_
- Kopregel: _Product_
- Dynamisch tegelopschrift: _getTileContent(handhaving_prod,{id})_
- Actie: _getFlexDetail(SysStandardDetail,{id},hah_producttegel)_
- SQL:

```sql
select case when d1logic = 'F' then 0
  when d1logic = 'T' and dfnumber1 = 1 then 0 else 1 end
  from tbinitialisatie
  where upper(dvsectie) = 'PRODUCT/DIENST'
  and UPPER(dvitem) = 'HANDHAVING'
```
