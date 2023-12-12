# Lijst Mijn DSO projecten

Schermidentifier: MDLC_getMijnDSOProjectenList.xml.

## Welke gegevens worden getoond

De rijen uit de view vwfrmdsoprojectoverzicht, dat zijn DSO projecten:

- waarvoor er tenminste 1 DSO zaak is in OpenWave waarvan de ingelogde medewerker de actieve behandelaar is
- indien men voor meer dan 1 van de DSO zaken de actieve behandelaar is, ziet men maar 1 regel voor het project

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de DSO projecten:
  - de inlogger heeft geen kijkrechten op omgevingszaken
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- zoekeditbox rechtsonder: altijd aanwezig
- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ bij _Sectie: paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd bijbehorend DSO projectportaal
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).

### Zichtbaarheid bepaalde kolommen

- Kolom Team (dvteamnaam):
  - alleen zichtbaar indien resultaat van query omgeving_zaakverantwteamzichtbaar is true:
    - true als instelling _Sectie: Zaakverantwoordelijke_ en _Item: Omgeving_, _Getal1_ waarde 2 of 3 heeft
    - anders false
