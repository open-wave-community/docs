# Audit

Portal Servicecentrum. Tegel *Audit*.

API(s):

* getAuditList: [https://api.open-wave.nl/RemMethods/getRemMethod/428](https://api.open-wave.nl/RemMethods/getRemMethod/428.md)
* getAuditDetail: [https://api.open-wave.nl/RemMethods/getRemMethod/431](https://api.open-wave.nl/RemMethods/getRemMethod/431.md)

Screenidentifiers: MDLC_getAuditList.xml en MDDLC_getAuditDetail.xml.

Deze lijst wordt gevuld indien de [instelling](/docs/instellen_inrichten.md) aangevinkt is van *Sectie: OWB* en *Item: AuditTrail*. In kolom *Getal1* van deze instelling staat het aantal dagen dat de wijzigingen bewaard moeten blijven. Default is dat 31. Indien deze instelling onder de 7 komt, dan gaat het programma toch uit van de minimum bewaartijd van 7 dagen.
Wijzigingen in de tabel tbinitialisatie (beheertegel *Configuratie*) worden altijd opgenomen in de audit trail ongeacht of de instelling aan- of uitgevinkt is.

Indien beheerrechten (tbmedewerkers.dnbeheernveau >= 99) dan zijn via deze tegel *Audit*, de wijzigingen per kolom per tabel per medewerker per tijdstip te zien die via de reguliere invoerformulieren en wizards zijn gedaan. Tevens worden de tabelnaam en de pointer van de verwijderde kaarten en van nieuw aangemaakte kaarten genoteerd. De automatische cascade deletes van de databaseserver worden niet opgenomen: dat wil zeggen dat als bijvoorbeeld een omgevingszaak wordt verwijderd, dan is deze zaak zelf terug te vinden in de audit trail, maar alle automatisch mee verwijderde kaarten uit gerelateerde tabellen (behandelaars, adviezen, processen, checklijsten et cetera) niet.

Voor memovelden geldt dat alleen wordt gemeld dat de memo is gewijzigd, maar de wijziging zelf wordt niet overgenomen in tbaudit.

De auditgegevens zijn niet muteerbaar.
