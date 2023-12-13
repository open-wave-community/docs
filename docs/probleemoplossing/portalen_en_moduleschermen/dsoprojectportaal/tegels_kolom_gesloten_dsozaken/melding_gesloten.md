# Melding (Gesloten)

## Trigger

De tegel is een trigger voor het lijstscherm van de _Afgesloten zaken van type Melding_ bij een DSO project.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert:
    - de tegel is zichtbaar als er voor dit DSO project afgesloten omgevingszaken (besluitdatum is gevuld) zijn van DSO type _Melding_ OF _Melding gelijkwaardige maatregel_ en er geen activiteiten met eigenschap _WKB_ aanwezig zijn voor deze zaken
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _dso_melding_gesloten_)
- indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _dsoprojectportaal_
- Kolom: _Afgesloten DSO-Zaken_
- Kopregel: _Melding_
- Dynamisch tegelopschrift: _getTileContent(dso_melding_gesloten,{id})_
- Actie: _getFlexList(SysStandardList,tbdsoproject,{id},nil,dso_melding_gesloten)_
- Onzichtbaar indien result van de volgende select 0 is:

```sql
select case when
    (select count(*) from tbomgvergunning
     where dnkeydsoproject = {id}
     and (lower(dvdsoverzoektype) = 'melding'
          OR lower(dvdsoverzoektype) = 'melding gelijkwaardige maatregel')
     and ddbesluitdatum is not null
     and (lower(dvdsoverzoekdoel) <> ''vooroverleg'' and lower(dvdsoverzoekdoel) <> ''conceptverzoek'')
     and dnkey not in (select dnkeyomgvergunningen from tbtoestemmingen
                       where dnkeysrttoestemming in (select dnkey from tbsrttoestemming
                                                    where dliswkb = 'T'))) >= 1
   then 1 else 0 end
```
