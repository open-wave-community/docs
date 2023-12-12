# Zaken op dit adres of leden van groep

De schermidentifier is: MDLC_geefZakenLijst.xml.

Dit scherm kan worden aangeroepen vanuit de tegels _Afgeronde en Lopende zaken_ en de tegels _Verbonden aan groep_
vanuit de zaakportalen Omgeving, Milieu/Gebruik, Handhaving, Bouw/sloop, Infoaanvragen, Horeca en APV/Overig en vanuit het inrichtingsportaal.
De lijst toont:

- indien aangeroepen vanuit de **zaakportalen met tegel lopende zaken** dan gaat het om zaken die spelen op dezelfde locatie, dus:
  - alle rijen van vwfrmalleaanvragen met dezelfde dnkeyperceeladres als het herkomstportaal
  - en waarbij de kolom ddeind leeg is (dus besluit/afgehandeld/einddatum is leeg en de ingetrokken datum is leeg)
- indien aangeroepen vanuit de **zaakportalen met tegel afgeronde zaken** dan gaat het om:
  - alle rijen van vwfrmalleaanvragen met dezelfde dnkeyperceeladres als het herkomstportaal
  - en waarbij de kolom ddeind gevuld is (dus besluit/afgehandeld/einddatum is gevuld of de ingetrokken datum is gevuld)
- indien aangeroepen vanuit het **inrichtingsportaal met tegel lopende zaken** dan gaat het om zaken bij dezelfde inrichting, dus:
  - alle rijen van vwfrmalleaanvragen met dezelfde dnkeymilinrichtingen als het herkomstportaal
  - en waarbij de kolom ddeind leeg is (dus besluit/afgehandeld/einddatum is leeg en de ingetrokken datum is leeg)
- indien aangeroepen vanuit het **inrichtingsportaal met tegel afgeronde zaken** dan gaat het om:
  - alle rijen van vwfrmalleaanvragen met dezelfde dnkeymilinrichtingen als het herkomstportaal
  - en waarbij de kolom ddeind gevuld is (dus besluit/afgehandeld/einddatum is gevuld of de ingetrokken datum is gevuld)
  - en de geldigheidsdatum (verloopdatum c.q. vervallendatum c.q. datum ingetrokkennaverlening) is leeg of groter dan vandaag
- indien aangeroepen vanuit de **zaakportalen met tegel Verbonden aan groep** dan gaat het om zaken die bewust verbonden zijn aan dezelfde groep of om zaken die als kopie (vervolgzaak) vanuit een processtap zijn aangemaakt:

  - alle rijen van vwfrmalleaanvragen met dezelfde dnkeygroepvergunning als het herkomstportaal.

         N.B. Met een instelling kan opgegeven worden dat bij het aanmaken van de groep niet de zaakomschrijving maar het DMS-nummer van de originele zaak als waarde gepakt worden, zie [Maak nieuwe zaak](/docs/instellen_inrichten/configuratie/sectie_programma.md).

## Probleem

Het scherm geeft een foutmelding indien er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie/README.md)) die niet valide is.

## Triggers

Dubbelklikken op een regel van de lijst start een deeplink naar het zaakportaal van de betreffende zaak.
Dit geldt alleen voor zaken van de modules Omgeving, Handhaving, Milieu/Gebruik, Bouw/sloop en APV/Overig, anders komt een leeg scherm met _deze functionaliteit is nog niet beschikbaar_.

### Triggers in het scherm linksonder

- Insert knop. Voeg **deze** zaak toe aan een groep of voorval. Hiermee wordt een een nieuwe groep gedefinieerd of een al bestaande groep aangewezen, waarbij de actieve zaak automatisch als lid van deze groep wordt opgenomen. Alleen zichtbaar en enabled indien:
  - de lijst wordt aangeroepen vanuit de tegel _Verbonden aan groep_
  - en de inlogger lid is van een rechtengroep die _Koppelen aan groep/voorval_ aangevinkt heeft staan voor de betreffende module (bijv. tbomgrechten. dlbomggroepedt)
  - en de zaak waarvandaan deze trigger wordt aangeroepen nog **niet** verbonden is aan een groep (de lijst met groepsleden is nog leeg).
- Insert knop. Koppel **andere** zaak aan deze groep. Hiermee wordt een wizard wordt gestart die op basis van de invoer van een wavezaakcode de bijbehorende zaak aan de bestaande groep toevoegt. Alleen zichtbaar en enabled indien:
  - de lijst wordt aangeroepen vanuit de tegel _Verbonden aan groep_
  - en de inlogger lid is van een rechtengroep die _Koppelen aan groep/voorval_ aangevinkt heeft staan voor de betreffende module (bijv. tbomgrechten. dlbomggroepedt)
  - en de zaak waarvandaan deze trigger wordt aangeroepen **wel** is verbonden aan een groep (de lijst is gevuld met groepsleden).
- Wizard knop. Wijzig groepsnaam. Hiermee wordt een wizard gestart waarmee de groepsnaam aangepast kan worden. Alleen zichtbaar en enabled indien:
  - de lijst wordt aangeroepen vanuit de tegel _Verbonden aan groep_
  - en de inlogger lid is van een rechtengroep die _Koppelen aan groep/voorval_ aangevinkt heeft staan voor de betreffende module (bijv. tbomgrechten. dlbomggroepedt)
  - en de zaak waarvandaan deze trigger wordt aangeroepen **wel** is verbonden aan een groep (de lijst is gevuld met groepsleden).
- Deleteknop. Haal de zaak weg uit een groep/voorval. Alleen zichtbaar en enabled indien:
  - de lijst wordt aangeroepen vanuit tegel _Verbonden aan groep_
  - en de inlogger lid is van een rechtengroep die _Koppelen aan groep/voorval_ aangevinkt heeft staan voor de betreffende module
  - en de zaak waarvandaan deze trigger wordt aangeroepen wel verbonden is aan een groep ((de lijst is gevuld met groepsleden).
