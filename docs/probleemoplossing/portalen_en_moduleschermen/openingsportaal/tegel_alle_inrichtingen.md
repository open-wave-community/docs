# Tegel Alle Inrichtingen

## Trigger

De tegel is een trigger voor de lijst van alle inrichtingen uit OpenWave.

Voor meer informatie over de lijst Alle Inrichtingen (zie [Lijst Alle inrichtingen](/docs/probleemoplossing/module_overstijgende_schermen/zaken_inrichtingen_locaties/inrichtingen.md)). Voor de definitie van de lijst en knoppen en filter: zie beheerportaal-Nieuw _Tabellen standaardapi_ (tbstandardtable.dvcode = _opening_alleinrichtingen_).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

- indien foutieve query verwijzing
- indien query zelf niet correct (zie [Queries](/docs/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Opening_
- Kolom: _Hoofdzaken_
- Kopregel:
- Vast Opschrift:_Alle inrichtingen_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(SysStandardList,nil,nil,G,opening_alleinrichtingen)_

## Zelf in te stellen beperking op grond van gemeentecodes

Aan medewerkers kan een beperkende opsomming toegekend kan worden van locaties waarvan zij de inrichtingen mogen zien. Dit gebeurt in het detailscherm van de medewerkerstabel in de kolom: _Alleen data van de gemeentes: (gemeente-ids gescheiden door puntkomma)_. De lijst van alle zaken kan hierop worden gefilterd indien in het blok _where clausule bij lijst_ in de tabel tbsysstandardtable (zie beheerportaal-Nieuw onder kolom scherm- en tegelbeheer _Tabellen standaardapi_) bij de kaart met dvcode = _opening_alleinrichtingen_) het volgende wordt ingebracht.

```sql
case when (select dvalleengemeentes from tbmedewerkers
           where trim(dvcode) = trim(: keyaccount)) is not null
     then instr((select dvalleengemeentes | | chr(59) from tbmedewerkers
                 where trim(dvcode) = trim(: keyaccount)), dvgemeenteid | | chr(59)) > 0
     else 1 = 1
     end
```

Let op: dit kan vertragend werken.

## Zelf in te stellen beperking op grond van compartiment

Zo zou ook de lijst gefilterd kunnen worden op grond van het compartiment waaraan de inlogger is verbonden. Met onderstaand voorbeeld worden alleen die zaken getoond die spelen in de gemeentes van dat compartiment. Indien de inlogger geen lid is van een compartiment worden alle zaken getoond.

```sql
case when (select dnkeycompartiment from tbmedewerkers
           where trim(dvcode) = trim(: keyaccount)) is not null
     then dvgemeenteid in (select dvgemeenteid from vwfrmkopcompgem
                           where dnkeycompartiment = (select dnkeycompartiment from tbmedewerkers
                                                      where trim(dvcode) = trim(: keyaccount)))
     else 1 = 1
     end
```
