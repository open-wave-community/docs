# Tegel Geplande Inspectiebezoeken

## Trigger

De tegel is een trigger voor de doorkieslijst _Geplande inspectiebezoeken_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

- indien foutieve query verwijzing
- indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren
- indien de kolom _altijd verversen_ (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Opening_
- Kolom: _Deelzaken_
- Kopregel:_Geplande;inspectiebezoeken_
- Vast Opschrift:
- Dynamisch tegelopschrift
- Actie: \*geefFlexList(OPENINSPBEZOEKEN,nil,nil,**_0_**,nil)*of*geefFlexList(OPENINSPBEZOEKEN,nil,nil,**_3_**,nil)\*

De parameter 0 geeft aan dat alle geplande/lopende inspectiebezoeken moeten worden getoond, waarbij:

- indien de inlogger lid is van een [compartiment](/instellen_inrichten/compartimenten.md), alleen die bezoeken getoond worden die horen bij zaken die spelen in een gemeente die onderdeel is van dat compartiment (dus ook bij zaaktypes die niet onder het compartiment vallen)
- indien de inlogger GEEN lid is van een compartiment dan is er geen compartimentsrestrictie.

De parameter 3 geeft aan dat alle geplande/lopende inspectiebezoeken moeten worden getoond, waarbij:

- indien de inlogger lid is van een compartiment, alleen die bezoeken worden getoond die horen bij zaken die vallen onder het compartiment (dus combinatie gemeente en zaaktype zijn gedefinieerd in dat compartiment en waarbij in de compartimentsdefinitie bij de zaak _inclusief inspectie_ is aangevinkt)
- indien de inlogger GEEN lid is van een compartiment, alleen die bezoeken worden getoond die horen bij zaken waarvan de combinatie gemeente en zaaktype en _inclusief inspectie_ in geen enkel compartiment voorkomt.
