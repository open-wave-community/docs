# Tegel Verbonden aan DSO-Project

## Trigger

De tegel is een trigger van de lijst [Lijst Verbonden aan DSO-zaak](tegel_verbonden_aan_dso_project/lijst_verbonden_aan_dsozaak.md) bestaande uit de zaken met een gedeeld *DSO Project* ID (zie: [Verwerking DSO STAM berichten](../programmablokken/verwerking_dso_stam_berichten.md)).
Tevens ziet men hier de via groep verbonden zaken aan de DSO-zaak waar men op staat.

  * De tegel is alleen zichtbaar voor inlogger wanneer:
    * deze aan hem/haar is toegekend
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
      * de tegel is alleen zichtbaar indien de omgevingszaak een zaak uit het DSO is (een gevulde dnkeydsoproject heeft)
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

### Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  * indien foutieve queryverwijzing (codering *omgeving_prod*)
  * indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
  * indien inlogger geen recht heeft om query uit te voeren
  * indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

### Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *omgevingdetail*
  * Kolom: *Samenhang*
  * Kopregel: *Verbonden aan DSO-Project*
  * Dynamisch tegelopschrift: *getTileContent(omgeving_dsoproject,{id})*
  * Actie: *getFlexList(SysStandardList,,{id},,omgeving_dsoproject)*
  * Onzichtbaar indien resultaat is 0 van select:
```sql
select case when dnkeydsoproject is not null then 1 else 0 end
from tbomgvergunning
where dnkey = {id}
```

