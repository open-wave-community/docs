# Tegel Product

## Trigger

De tegel is een trigger voor een detailscherm van het _Product_ bij een omgevingszaak (zie: [Producten Klanten en Werkpakketten](/instellen_inrichten/producten_klanten_werkpakketten.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval betekent dat dat de instelling _Sectie: Product/Dienst Item:Omgeving_ aangevinkt moet zijn en dat _Getal1_ leeg is (zie hieronder bij SQL-conditie).
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _omgeving_prod_)
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _omgevingdetail_
- Kolom: _Overig_
- Kopregel: _Product_
- Dynamisch tegelopschrift: _getTileContent(omgeving_prod,{id})_
- Actie: _getFlexDetail(SysStandardDetail,{id},omg_producttegel)_
- SQL:

```sql
select case when d1logic = 'F' then 0
         when d1logic = 'T' and dfnumber1 = 1 then 0
         else 1 end
  from tbinitialisatie
  where upper(dvsectie) = 'PRODUCT/DIENST'
  and upper(dvitem) = 'OMGEVING'
```
