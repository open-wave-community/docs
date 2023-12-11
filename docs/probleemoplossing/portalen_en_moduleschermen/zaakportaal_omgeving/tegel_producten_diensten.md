# Tegel Producten/Diensten

## Trigger

De tegel is een trigger voor het lijstscherm van *Producten/Diensten* bij een omgevingszaak (zie: [Producten Klanten en Werkpakketten](/docs/instellen_inrichten/producten_klanten_werkpakketten.md)).

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval betekent dat dat de instelling *Sectie: Product/Dienst Item:Omgeving*  aangevinkt moet zijn en dat *Getal1* de waarde 1 heeft. (zie hieronder bij SQL-conditie).
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *Omgeving_Producten/Diensten*) 
  * indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren 
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: [Zaakportaal Omgeving](/docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving.md)
  * Kolom: *Overig*
  * Kopregel: *Producten/diensten*
  * Dynamisch tegelopschrift: *getTileContent(Omgeving_Producten/Diensten,{id})*
  * Actie: *getFlexList(SysStandardList,tbomgvergunning,{id},nil,omgeving_producten/diensten)*
  * SQL: 

```sql
select case when d1logic = 'T' and dfnumber1 = 1 then 1 else 0 end 
  from tbinitialisatie 
  where upper(dvsectie) = 'PRODUCT/DIENST' 
  and UPPER(dvitem) = 'OMGEVING'
```

## Bijzonderheden

De kolommen *Werkpakket* en *Klant* zijn alleen muteerbaar indien de instelling *Sectie: Product/Dienst Item: Omgeving* aangevinkt is waarbij **Getal2** ongelijk is aan 1. Indien deze instelling namelijk wel de waarde 1 heeft, dan zijn deze kolommen in de bovenliggende detailkaart van de omgevingszaak te vullen in het blok *Klant/Wkpt*. Die waardes worden dan vanzelf overgenomen in tbzaakproducten.

De kolom *Product* is vrijelijk te kiezen uit de gedefinieerde producten bij het betreffende zaaktype (beheertegel *Zaaktypes omgeving*).
Echter wanneer:

  * de combinatie klant/werkpakket voorkomt in de beheertabel *Combinaties product/klant/werkpakket* (tbprodwkpklant) 
  * EN de kolom *Info* van de instelling *Sectie: Product/Dienst Item: Omgeving* heeft de waarde 'ODR' 

kan bij het nieuw opvoeren van een zaakproduct alleen gekozen worden uit de deze rijen van tbprodwkpklant.

