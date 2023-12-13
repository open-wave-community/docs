# Gemiste DSO-Verzoeken

## Trigger

De tegel is een trigger voor de weergave van de tabel tbgemisteverzoeken,  die periodiek wordt aangevuld vanuit de taskscheduler met de aanroep van de callable importDSOGemisteVerzoeken. Het gaat om DSO STAM-berichten die - mogelijk ten onterechte - niet terug te vinden zijn in OpenWave. Zie: [DSO Gemiste Verzoeken](../programmablokken/dso_gemiste_verzoeken.md)

Voor het ophalen van gerelateerde verzoeken (verzoeken die door een andere bevoegd gezag of behandeldienst worden behandeld, maar wel spelen op dezelfde locatie) bij een omgevingzaak: Zie: [DSO Gerelateerde Zaken](../programmablokken/dso_gerelateerde_zaken.md).

- De tegel DSO gemiste verzoeken is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Servicecentrum*
- Kolom: *Notificaties/
- Kopregel: *Gemiste DSO verzoeken*
- Actie: *getFlexList(SysStandardList,nil,nil,,beheer_gemistedsoverzoeken)*
