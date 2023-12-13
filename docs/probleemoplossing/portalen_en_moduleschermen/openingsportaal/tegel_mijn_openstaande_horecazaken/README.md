# Tegel Mijn Openstaande Horecazaken

## Trigger

De tegel is een trigger voor de doorkieslijst voor [Lijst Mijn Openstaande Horecazaken](tegel_mijn_openstaande_horecazaken/lijst_mijn_openstaande_horecazaken.md).

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

  - indien foutieve queryverwijzing
  - indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *Opening*
  - Kolom: *Mijn Taken*
  - Kopregel:
  - Vast Opschrift:*Mijn openstaande;Horecazaken*
  - Dynamisch tegelopschrift:
  - Actie: *getFlexList(OpenHorecazaken,nil,nil,I,C))*

De 4 parameter heeft de waarde:

  - I = programma filtert op die openstaande horecazaken waarvoor de inlogger gelijk is aan de actieve behandelaar dan wel de zaakverantwoordelijke (dvcodeaccountman)
  - of T = programma filtert op die openstaande horecazaken waarvoor de inlogger behoort tot het zaakverantwoordelijk team.

