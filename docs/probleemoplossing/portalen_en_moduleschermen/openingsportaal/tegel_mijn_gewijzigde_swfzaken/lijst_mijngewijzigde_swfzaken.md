# Lijst Mijn Gewijzigde SWF zaken

Schermidentifier: MDLC_getMijnSWFGewijzigdeZakenList.xml.

Zie ook [Tegel Mijn Gewijzigde SWF Zaken](/docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_gewijzigde_swfzaken.md)

## Welke gegevens worden getoond

De rijen uit de view vwfrmswfgewijzigdezaken, dat zijn SWF ruimtes bij omgevingszaken:

- waarvoor er tenminste 1 wijziging is opgetreden tijdens het gescheduled synchroniseren van alle Openstaande SWF ruimtes:
  - tijdens het synchroniseren zijn 1 of meer gegevens van de SWF ruimte aangepast
  - en/OF 1 of meer ketenpartners toegevoegd/aangepast
  - en/OF 1 of meer actieverzoeken toegevoegd/aangepast
  - en/OF 1 of meer documenten toegevoegd/aangepast
  - en/OF 1 of meer nieuwe notificaties toegevoegd (inherent aan als 1 van de bovengenoemde wijzigingen heeft plaats gevonden)
- waarvan de ingelogde medewerker de actieve behandelaar is van de omgevingszaak waaronder de SWF ruimte valt
- waarvan de ingelogde medewerker in het zaakverantwoordelijk team zit van de omgevingszaak waaronder de SWF ruimte valt
- en waarvoor de wijziging nog niet aangemerkt is als Laatste wijziging gezien

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de SWF zaken:
  - de inlogger heeft geen kijkrechten op omgevingszaken
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- klikken op regel opent altijd bijbehorend Omgevingsportaal
- Detailknop linksonder:
  - opent het detailscherm van de SWF ruimte
  - Zichtbaar indien men SWF zaken mag inzien (tbomgrechten.dlcomgswfvsb is T)
- Accordeerknop: **Laatste wijziging na synchronisatie gezien: uitvinken als gewijzigd** (linksonder):
  - geselecteerde regels zullen bij drukken op deze knop hun kenmerk verliezen dat ze recent gewijzigd zijn (tbswfruimte.dlgewijzigdbijsync wordt F). Zo kan men de lijst _Mijn gewijzigde SWF zaken_ opschonen zodra men de wijzigingen heeft gezien.
  - Na klikken op de knop verdwijnen de geselecteerde regels uit de lijst (ze worden dus niet daadwerkelijk verwijderd!) en zullen deze SWF zaken via de overige SWF tegels te benaderen zijn maar niet meer in dit overzicht
  - Zichtbaar indien men SWF zaken mag wijzigen (tbomgrechten.dlcomgswfedt is T)
- zoekeditbox rechtsonder: altijd aanwezig
- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ bij _Sectie: paging_ en _Item: pagesize_ (defaultwaarde = 100)
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).

## Zichtbaarheid bepaalde kolommen

- Kolom Team (dvteamzaakverantw):
  - alleen zichtbaar indien resultaat van query omgeving_zaakverantwteamzichtbaar is true:
    - true als instelling _Sectie: Zaakverantwoordelijke_ en _Item: Omgeving_, _Getal1_ waarde 2 of 3 heeft
    - anders false
