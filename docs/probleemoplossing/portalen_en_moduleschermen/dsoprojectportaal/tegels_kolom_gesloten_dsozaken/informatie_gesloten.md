# Informatie (Gesloten)

## Trigger

De tegel is een trigger voor het lijstscherm van de _Afgesloten zaken van type Informatie_ bij een DSO project.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert:
    - de tegel is zichtbaar als er voor dit DSO project afgesloten omgevingszaken (besluitdatum is gevuld) zijn van DSO type _Informatie_ OF _Informatie ongewoon voorval_ en er GEEN activiteiten met eigenschap _WKB_ aanwezig zijn voor deze zaken
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _dso_informatie_gesloten_)
- indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _dsoprojectportaal_
- Kolom: _Afgesloten DSO-Zaken_
- Kopregel: _Informatie_
- Dynamisch tegelopschrift: _getTileContent(dso_informatie_gesloten,{id})_
- Actie: _getFlexList(SysStandardList,tbdsoproject,{id},nil,dso_informatie_gesloten)_
- Onzichtbaar indien result van de volgende select 0 is:

```sql
select case when
   (select count(*)
    from tbomgvergunning
    where dnkeydsoproject = {id}
    and (lower(dvdsoverzoektype) = 'informatie' OR lower(dvdsoverzoektype) = 'informatie ongewoon voorval')
    and ddbesluitdatum is not null
    and (lower(dvdsoverzoekdoel) <> ''vooroverleg'' and lower(dvdsoverzoekdoel) <> ''conceptverzoek'')
    and dnkey not in (select dnkeyomgvergunningen from tbtoestemmingen
                      where dnkeysrttoestemming in (select dnkey from tbsrttoestemming
                                                    where dliswkb = 'T'))) >= 1
    then 1 else 0 end
```
