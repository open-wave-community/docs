# Serverlogs

## Trigger

De tegel is een trigger voor het starten van een wizard waarmee de meer technische logging kan worden opgehaald.

* requestlog: alle requests die naar buiten gaan
* accesslog: al het berichtenverkeer dat via poort 443 binnenkomt
* wrapperlog: alle WSAS meldingen van de API-server, bijv. certificaatmeldingen en java-errors

De gevraagde logfile wordt gedownload op de device van de gebruiker.
In kolom *Tekst* van de instelling *Sectie Operations en Item: servernaam_accesslog* moet de servernaam staan waar de acceslog.sh staat (bijv.: demo2.open-wave.nl).

De tegel is alleen zichtbaar voor inlogger wanneer:

* deze aan hem/haar is toegekend
* de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.

Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Servicecentrum*
* Kolom: *Logs*
* Vast opschrift: *Serverlogs*
* Actie: *startWizard(downloadServerLog)*
