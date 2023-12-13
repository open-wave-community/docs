# Tegel Activiteiten Oorspronkelijke Zaak

Deze tegel kan zichtbaar zijn indien de betreffende omgevingszaak aangemaakt is als kopie van een andere zaak. Dit kopiëren gebeurt vanuit een processtap, die daartoe is gemodelleerd: vanuit een dergelijke processtap kan een actie uitgevoerd worden die een nieuwe zaak aanmaakt als kopie op dezelfde locatie, waarbij contactpersonen worden overgenomen naast (instelbare) andere kolommen (zie [Termijnstappen](../../../instellen_inrichten/inrichting_processen/termijnstappen.md) en blokje _Kopieer kolommen_ bij [Aanmaken van nieuwe zaak](../programmablokken/maak_nieuwe_zaak.md)).

Bij de nieuwe zaak in tbomgvergunning wordt de kolom _dnkeygekopieerdezaak_ automatisch gevuld met de dnkeywaarde van de zaak waaruit wordt gekopieerd.

Bij de nieuwe aangemaakte zaak kunnen de activiteiten van de oorspronkelijke zaak via deze tegel benaderd worden indien:

- de dnkeygekopieerdezaak gevuld is
- en bij de definitie van het zaaktype van de nieuwe zaak is de kolom _Activteitsverwijzingen zichtbaar van oorspronkelijke zaak bij kopie_ (tbsoortomgverg.dlactvangekopieerdezaak) aangevinkt.

Zo niet, dan is de tegel niet zichtbaar.

## Trigger

De tegel is een trigger voor het tonen van een lijst van activiteiten die horen bij de **oorspronkelijke** zaak.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - en de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing
- indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _omgevingdetail_
- Kolom: _Samenhang_
- Kopregel: _Activiteiten oorspronkelijke zaak_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(tbtoestemmingen,tbomgvergunning,{dnkeygekopieerdezaak},,W)_
- SQL (zichtbaarheid):

```sql
select
  case when a.dnkeygekopieerdezaak is not null
  and b.dlactvangekopieerdezaak = 'T' then 1 else 0 end
from tbomgvergunning a
  inner join tbsoortomgverg b on (a.dnkeysoortomgverg = b.dnkey)
where a.dnkey = {id}
```
