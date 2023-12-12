# Tegel Mijn Openstaande omgevingszaken

## Trigger

De tegel is een trigger voor de doorkieslijst [Lijst Mijn Openstaande omgevingszaken](/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_openstaande_omgevingszaken/lijst_mijn_openstaande_omgevingszaken.md)

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

  - indien foutieve queryverwijzing
  - indien query zelf niet correct (zie [Queries](/instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *Opening*
  - Kolom: *Mijn Taken*
  - Kopregel:*Mijn openstaande;Omgevingdossiers*
  - Vast Opschrift:
  - Dynamisch tegelopschrift:
  - Actie: *getFlexList(OpenOmgZaken,nil,nil,I,W)*

De 4 parameter heeft de waarde:

  - I = programma filtert op die openstaande omgevingszaken waarvoor de inlogger gelijk is aan de actieve behandelaar dan wel de zaakverantwoordelijke (dvcodeaccountman)
  - of T = programma filtert op die openstaande omgevingszaken waarvoor de inlogger behoort tot het zaakverantwoordelijk team.

