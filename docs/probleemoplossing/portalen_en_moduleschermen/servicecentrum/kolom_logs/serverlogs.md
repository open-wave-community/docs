# Serverlogs

## Trigger

De tegel is een trigger voor het starten van een wizard waarmee de meer technische logging kan worden opgehaald.

- requestlog: alle requests die naar buiten gaan
- accesslog: al het berichtenverkeer dat via poort 443 binnenkomt
- wrapperlog: alle WSAS meldingen van de API-server, bijv. certificaatmeldingen en java-errors

De gevraagde logfile wordt gedownload op de device van de gebruiker.
In kolom _Tekst_ van de instelling _Sectie Operations en Item: servernaam_accesslog_ moet de servernaam staan waar de acceslog.sh staat (bijv.: demo2.open-wave.nl).

De tegel is alleen zichtbaar voor inlogger wanneer:

- deze aan hem/haar is toegekend
- de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.

Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Servicecentrum_
- Kolom: _Logs_
- Vast opschrift: _Serverlogs_
- Actie: _startWizard(downloadServerLog)_
