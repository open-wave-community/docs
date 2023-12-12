# Tegel Product

## Trigger

De tegel is een trigger voor een detailscherm van het Product bij een Horecazaak (zie: [Producten Klanten en Werkpakketten](/docs/instellen_inrichten/producten_klanten_werkpakketten.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval betekent dat dat de instelling _Sectie: Product/Dienst Item: Horeca_ aangevinkt moet zijn en dat getal1 leeg is. (zie hieronder bij SQL-conditie).
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _horeca_prod_)
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _horecadetail_
- Kolom: _Overig_
- Kopregel: _Product_
- Dynamisch tegelopschrift: _getTileContent(horeca_prod,{id})_
- Actie: _getFlexDetail(SysStandardDetail,{id},hor_producttegel)_
- SQL:

```sql
select case when d1logic = 'F' then 0
        when d1logic = 'T' and dfnumber1 = 1 then 0
        else 1 end
  from tbinitialisatie
  where upper(dvsectie) = 'PRODUCT/DIENST'
  and UPPER(dvitem) = 'HORECA'
```
