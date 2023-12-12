# Projectlocaties

## Trigger

De tegel is een trigger voor het lijstscherm van de _Projectlocaties_ bij een DSO project. Het lijstscherm toont distinct de projectlocaties/kadastrale percelen (geen dubbele regels voor gelijke combinatie kadaster, projectlocatie, wegdeel, vaardeel en coördinaten) van de DSO zaken met hetzelfde dnkeydsoproject.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert:
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _dso_overig_projlocaties_)
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _dsoprojectportaal_
- Kolom: _Overig_
- Kopregel: _Projectlocaties_
- Dynamisch tegelopschrift: _getTileContent(dso_overig_projlocaties,{id})_
- Actie: _getFlexList(SysStandardList,,{id},nil,dso_overig_projlocaties)_
