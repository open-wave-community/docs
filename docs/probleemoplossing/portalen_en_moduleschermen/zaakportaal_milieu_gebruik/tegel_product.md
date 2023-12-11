# Tegel Product

## Trigger

De tegel is een trigger voor een detailscherm van het *Product* bij een Milieu/Gebruikszaak (zie: [Producten Klanten en Werkpakketten](/docs/instellen_inrichten/producten_klanten_werkpakketten.md)).

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval betekent dat dat de instelling *Sectie: Product/Dienst Item: Milieu/Gebruik* aangevinkt moet zijn en dat *Getal1* leeg is (zie hieronder bij SQL-conditie).
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *milieugebruik_prod*) 
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren. 

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *milieugebruikdetail*
  * Kolom: *Overig*
  * Kopregel: *Product*
  * Dynamisch tegelopschrift: *getTileContent(milieugebruik_prod,{id})*
  * Actie: *getFlexDetail(SysStandardDetail,{id},milgebr_producttegel)*
  * SQL: 
```sql
select case when d1logic = 'F' then 0 
            when d1logic = 'T' and dfnumber1 = 1 then 0 
            else 1 end 
  from tbinitialisatie 
  where upper(dvsectie) = 'PRODUCT/DIENST' 
  and UPPER(dvitem) = 'MILIEU/GEBRUIK'
```

