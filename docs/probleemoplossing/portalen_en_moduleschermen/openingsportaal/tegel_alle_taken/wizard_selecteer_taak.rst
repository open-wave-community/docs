Wizard Selecteer Taak
=====================

De wizard wordt aangeroepen vanuit het openingsportaal vanuit de tegel
*Al Mijn Taken* (zie ook `Tegel Alle
Taken </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_alle_taken.md>`__)
met de action startWizard(selecteerTaak,1,1) en vanuit de tegel *Alle
Taken* met de action startWizard(selecteerTaak,1).

De wizard regelt in een aantal schermen de selectie op de view
vwfrmalletaken.

Deze view bevat de openstaande taken die gepland of begonnen zijn in het
op te geven datumbereik m.b.t.:

-  processtappen
-  uitstaande adviezen
-  inspectiebezoeken
-  fatale datums
-  verloopdatums
-  invorderingen
-  inspectietrajecten
-  bezwaar/beroepzaken

Vwfrmalletaken maakt gebruik van andere views waarvan het bereik bepaald
wordt door de volgende instellingen:

-  processtappen: Het aantal dagen terug wordt hier begrensd door de
   instelling *Getal2* van *Sectie: Processen Item:
   DagenTerug_StappenLijst*. Default is dit 365.
-  uitstaande adviezen. Het aantal dagen terug wordt hier begrensd door
   de instelling *Getal2* van *Sectie: Adviezen: Item:
   DagenTerug_OpenstaandLijst*. Default is dit 365 dagen.
-  inspectiebezoeken. Het aantal dagen terug wordt hier begrensd door de
   instelling *Getal2* van *Sectie: Inspecties: Item:
   DagenTerug_OpenBezoekenLijst*. Default is dit 365 dagen.
-  fatale en verloop- en invorderingsdatums. Het aantal dagen terug
   wordt hier begrensd door de instelling *Getal2* van *Sectie:
   Takenlijst: Item: DagenTerug_Hoofdzaken*. Default is dit 365 dagen.
-  inspectietrajecten. Het aantal dagen terug wordt hier begrensd door
   de instelling *Getal2* van *Sectie: Inspecties: Item:
   DagenTerug_OpenInspectieLijst*. Default is dit 730 dagen.

Scherm 1: Datumbereik
---------------------

De datum vanaf krijgt default de waarde van vandaag minus de waarde van
*Getal1* van de instelling *Sectie: Takenlijst en Item: DagenTerug*.

De datum totenmet krijgt default de waarde van vandaag plus de waarde
van *Getal1* van de instelling *Sectie: Takenlijst en Item:
DagenVooruit*.

DatumVanaf kan dus langer dan een jaar geleden zijn, maar het effect van
deze keuze is dus mede bepaald door bovengenoemde instellingen.

Scherm 2: Rechtengroepen
------------------------

In dit scherm kunnen één of meer (niet vervallen) rechtengroepen worden
aangevinkt waarvan in scherm 3 de medewerkers worden getoond. Default
staat de rechtengroep aangevinkt waarvan de inlogger lid is. Indien de
aanroep vanuit de tegel *Al Mijn Taken* dan is dit scherm niet zichtbaar
en wordt de rechtengroep van de inlogger onder water gekozen.

Scherm 3: Medewerkers
---------------------

In dit scherm kunnen één of meer medewerkers worden aangevinkt die lid
zijn van de in scherm 2 aangevinkte rechtengroepen. Default staat de de
inlogger zelf aangevinkt (indien de rechtengroepkeuze dit toelaat).
Alleen medewerkers waarvan de vervaldatum leeg is of groter is dan
DatumVanaf worden getoond. Indien de aanroep vanuit de tegel *Al Mijn
Taken* dan is dit scherm niet zichtbaar en wordt de medewerkerscode van
de inlogger onder water gekozen.

Scherm 4: Modules
-----------------

In dit scherm kunnen één of meer modules worden aangevinkt. Alleen die
modules worden getoond waartoe de inlogger kijkrechten heeft. Default
staan deze alle aangevinkt. Indien de aanroep vanuit de tegel *Al Mijn
Taken* dan is dit scherm niet zichtbaar en worden alle modules onder
water aangevinkt.

Scherm 5: Taaksoorten
---------------------

In dit scherm kunnen één of meer taaksoorten worden aangevinkt. Dat
zijn:

-  **processtappen** Dat zijn de eerste niet afgehandelde processtappen
   per zaak waarvoor geldt:

   -  dat de streefdatum ligt in het datumbereik
   -  dat de bovenliggende module behoort tot de aangevinkte in scherm 4
   -  dat de bovenliggende zaak niet is geblokkeerd
   -  dat de bovenliggende zaak een actieve behandelaar
      (dossierverantwoordelijke) heeft
   -  dat de processtapverantwoordelijke, bij ontbreken: de
      dossierverantwoordelijke, behoort tot de gekozen medewerkers in
      scherm 3
   -  dat de locatie gemeente waar de zaak speelt zichtbaar is voor de
      inlogger. Dat betekent dat de kolom dvalleengemeentes van
      tbmedewerkers (op de kaart van de inlogger) leeg is of anders dat
      de gemeenteid van de locatie voorkomt in deze kolom
      dvalleengemeentes.

-  **uitstaande adviezen** Dat zijn de niet afgehandelde adviezen per
   zaak waarvoor geldt:

   -  dat de adviesretourdatum (ddadviesdatum) leeg is
   -  dat de rappeldatum ligt in het datumbereik
   -  dat de advies vervaldatum leeg is
   -  dat de bovenliggende module behoort tot de aangevinkte in scherm 4
   -  dat de bovenliggende zaak niet is geblokkeerd
   -  dat de bovenliggende zaak een actieve behandelaar
      (dossierverantwoordelijke) heeft
   -  dat de adviesverantwoordelijke, bij ontbreken: de
      dossierverantwoordelijke, behoort tot de gekozen medewerkers in
      scherm 3
   -  dat de locatie gemeente waar het advies speelt zichtbaar is voor
      de inlogger. Dat betekent dat de kolom dvalleengemeentes van
      tbmedewerkers (op de kaart van de inlogger) leeg is of anders dat
      de gemeente-id van de locatie voorkomt in deze kolom
      dvalleengemeentes.

-  **inspectiebezoeken** Dat zijn de niet afgehandelde inspectiebezoeken
   per zaak/inrichting waarvoor geldt:

   -  dat de afhandelingsdatum van het inspectiebezoek
      (tbinspbezoeken.ddafgehandeld) leeg is
   -  dat de geplande bezoekdatum (tbinspbezoeken.ddgepland) ligt in het
      datumbereik
   -  dat de afhandelingsdatum van het bovenliggende inspectietraject
      (tbinspecties.ddcontrole) leeg is of groter dan vandaag
   -  dat de bovenliggende module behoort tot de aangevinkte in scherm 4
   -  dat de bovenliggende zaak/inrichting niet is geblokkeerd. Indien
      echter de instelling *Sectie: InspectieMilieu en Item:
      Nietblokkerenmethoofdzaak* aangevinkt is, dan mag de bovenliggende
      zaak WEL geblokkeerd zijn
   -  dat de bezoekende inspecteur behoort tot de gekozen medewerkers in
      scherm 3
   -  dat de locatie gemeente waar de inspectie speelt zichtbaar is voor
      de inlogger. Dat betekent dat de kolom dvalleengemeentes van
      tbmedewerkers (op de kaart van de inlogger) leeg is of anders dat
      de gemeente-id van de locatie voorkomt in deze kolom
      dvalleengemeentes.

-  **fatale datums** Dat zijn de niet afgehandelde zaken waarvoor geldt:

   -  dat zowel de besluit/einddatum als - indien van toepassing - de
      intrekkingsdatum leeg zijn
   -  dat de fatale datum valt in het datumbereik
   -  dat de zaak niet is geblokkeerd
   -  dat de bovenliggende module behoort tot de aangevinkte in scherm 4
   -  dat de dossierbehandelaar behoort tot de gekozen medewerkers in
      scherm 3
   -  dat de locatie gemeente waar de zaak speelt zichtbaar is voor de
      inlogger. Dat betekent dat de kolom dvalleengemeentes van
      tbmedewerkers (op de kaart van de inlogger) leeg is of anders dat
      de gemeente-id van de locatie voorkomt in deze kolom
      dvalleengemeentes.

-  **verloopdatums** Dat zijn de zaken waarvoor geldt:

   -  dat de ddverlopen c.q. ddvervallen c.q. ddnaverlingetrokken valt
      in het datumbereik
   -  dat de bovenliggende module behoort tot de aangevinkte in scherm 4
   -  dat de dossierbehandelaar behoort tot de gekozen medewerkers in
      scherm 3
   -  dat de locatie gemeente waar de zaak speelt zichtbaar is voor de
      inlogger. Dat betekent dat de kolom dvalleengemeentes van
      tbmedewerkers (op de kaart van de inlogger) leeg is of anders dat
      de gemeente-id van de locatie voorkomt in deze kolom
      dvalleengemeentes.

-  **invorderingen** Dat zijn de niet afgehandelde invorderingen uit
   tbhandhinvorderingen waarvoor geldt:

   -  dat de geplande betaaldatum (tbhandhinvorderingen.dddatum) valt in
      het datumbereik
   -  dat de afhandeldatum (tbhandhinvorderingen.ddafgehandeld) leeg is
   -  dat de bovenliggende module behoort tot de aangevinkte in scherm 4
   -  dat de bovenliggende zaak niet is geblokkeerd
   -  dat de dossierbehandelaar behoort tot de gekozen medewerkers in
      scherm 3
   -  dat de locatie gemeente waar de zaak speelt zichtbaar is voor de
      inlogger. Dat betekent dat de kolom dvalleengemeentes van
      tbmedewerkers (op de kaart van de inlogger) leeg is of anders dat
      de gemeente-id van de locatie voorkomt in deze kolom
      dvalleengemeentes.

-  **inspectietrajecten** Dat zijn de niet afgehandelde
   inspectietrajecten per zaak/inrichting waarvoor geldt: \*dat de
   afhandelingsdatum van het inspectietraject (tbinspecties.ddcontrole)
   leeg is

   -  dat de startdatum (tbinspecties.ddrappel) ligt in het datumbereik
      \*dat de bovenliggende module behoort tot de aangevinkte in scherm
      4
   -  dat de bovenliggende zaak/inrichting niet is geblokkeerd. Indien
      echter de instelling *Sectie: InspectieMilieu en Item:
      Nietblokkerenmethoofdzaak* aangevinkt is, dan mag de bovenliggende
      zaak WEL geblokkeerd zijn \*dat de hoofdinspecteur behoort tot de
      gekozen medewerkers in scherm 3
   -  dat de locatie gemeente waar de inspectie speelt zichtbaar is voor
      de inlogger. Dat betekent dat de kolom dvalleengemeentes van
      tbmedewerkers (op de kaart van de inlogger) leeg is of anders dat
      de gemeente-id van de locatie voorkomt in deze kolom
      dvalleengemeentes.

-  **Bezwaar/beroep** Dat zijn de niet afgehandelde beroepszaken
   (tbbezwaarberoep) per zaak waarvoor geldt:

   -  dat de uitspraakdatum (dduitspraak) leeg is
   -  dat de ingedienddatum (ddindiening) ligt in het datumbereik
   -  dat de bovenliggende module behoort tot de aangevinkte in scherm 4
   -  dat de bovenliggende zaak niet is geblokkeerd
   -  dat de bovenliggende zaak een accountmanager (dvcodeaccountman)
      heeft die behoort tot de gekozen medewerkers in scherm 3
   -  dat de locatie gemeente waar de beroepszaak speelt zichtbaar is
      voor de inlogger. Dat betekent dat de kolom dvalleengemeentes van
      tbmedewerkers (op de kaart van de inlogger) leeg is of anders dat
      de gemeente-id van de locatie voorkomt in deze kolom
      dvalleengemeentes.

Default staan deze alle aangevinkt.

Indien de aanroep vanuit de tegel *Al Mijn Taken* dan is dit scherm niet
zichtbaar en worden alle taaksoorten aangevinkt.

Scherm 6: Doorkieslijst met openstaande taken
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Deze lijst is een selectie op de view vwfrmalletaken.

Het samenstellen van deze lijst kan even duren.

De lijst is gesorteerd op datum en wordt afgekapt op 300 rijen.
