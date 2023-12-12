# Upload Lijst

De schermidentifier is: MDLC_getUploadList.xml.

Dit scherm kan worden aangeroepen vanuit:

- het openingsportaal. De lijst toont de uploadpogingen naar fileshare of zaak/DMS van documenten die de inlogger heeft gedaan tot 365 dagen terug over alle zaken heen.
- de detailschermen van een omgevingszaak, handhavingszaak, APV/Overig, Infoaanvraag, Bouw/sloop, Horeca en Object/Inrichtingen. De lijst toont alle uploadpogingen naar fileshare of zaak/DMS van documenten bij de zaak/inrichting van alle medewerkers zonder de uploads die gedaan zijn vanuit de adviezen en inspectietrajecten.
- de detailschermen van adviezen, bezwaar/beroep en inspectietrajecten. De lijst toont alle uploadpogingen naar fileshare of zaak/DMS van documenten bij dat specifieke advies, bezwaar/beroep of inspectietraject
- het detailscherm van een documentsjabloon (beheerportaal-Nieuw). De lijst toont alle uploadpogingen van documentsjablonen (in base64) naar de kolom dvtemplatebase64 van de tabel tbdocumenten.

De bron van de lijst is de view vwfrmupload op basis van de tabel tbupload die gevuld wordt bij het handmatig uploaden van documenten. In de tabel worden herkomst en bestemming vastgelegd van een upload. Zie [Upload document](/docs/probleemoplossing/programmablokken/upload_document.md).

Uploads gedaan door automatische processen, zoals de bijlagen bij een DSO-bericht, staan niet in deze lijst. Alleen de mislukte pogingen van automatische OLO/DSO-bijlage-uploads worden opgeslagen in de tabel tbBadExternUpload en zijn zichtbaar in de tegel _Mislukte OLO-bijlages_ op het beheerportaal-Nieuw. Zie [Verwerken DSO-bijlagen vanuit digi-koppelaar](/docs/probleemoplossing/programmablokken/upload_dso-document_vanuit_digi-koppelaar.md).

## Probleem

Het scherm geeft een foutmelding indien er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is.

### Trigger

Linksonder in het scherm is de knop refresh altijd zichtbaar en enabled.

Bij het oproepen van de lijst kan het uploadproces nog bezig zijn voor één of meer documenten (kolom status is _klaargezet_ of _Wordt momenteel geupload_). Met het refreshen kan de actuele status tevoorschijn worden gehaald.

Het programma kijkt hierbij ook naar de waarde van _Getal1_ van _Sectie: Documenten en Item: UploadlistMaxHours_. Indien deze waarde (in uren: mag ook 0.50 zijn) bestaat en groter is dan 0 dan wordt bij het uitschrijven (verversen) van de uploadijst de status van kaarten met _klaargezet_ en _wordt momenteel geupload_ veranderd in _Mislukt_ indien hun uploadproces langer dan UploadlistMaxHours uren geleden is gestart.

### Betekenis kleurbolletjes

- rood indien upload is mislukt
- groen indien upload is gelukt (verzonden)
- wit indien op het moment van oproepen van de lijst het uploaden bezig was (Wordt momenteel geüpload)
- oranje indien op het moment van oproepen van de lijst het document is klaargezet op de OpenWave server, maar het uploaden zelf nog niet is gestart.

### Betekenis kolommen

De meeste kolommen spreken voor zich.

- Doelmap:
  - indien de upload gedaan is met Stuf Zaak/DMS koppeling dan is deze kolom gevuld met de externe zaak-identifier
  - indien de upload is gedaan met CMIS-protocol dan staat hier de map van het DMS waar het document is opgeslagen
  - indien de upload is gedaan naar de fileshare dan staat hier de fileshare map waar het document is opgeslagen.
- Endpoint-omschrijving:
  - indien de upload gedaan is met Stuf Zaak/DMS koppeling dan is deze kolom gevuld met de kolom _Info_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: Ontvangstadres_Asynchroon_. Deze kolom wordt alleen gebruikt om alhier info te tonen en is niet van invloed op wat voor algoritme dan ook
  - indien de upload is gedaan met CMIS-protocol dan is deze kolom gevuld met de kolom _Info_ van de instelling _Sectie: KoppelingDOCNAARDMS_ en _Item: Ontvangstadres_cmis_. Deze kolom wordt alleen gebruikt om alhier info te tonen en is niet van invloed op wat voor algoritme dan ook
  - indien de upload is gedaan naar de fileshare dan staat hier de vaste tekst _fileshare_.
- Endpoint:
  - indien CMIS of Stuf dan het endpoint van de service waar de uploads naar toe zijn gegaan. Indien fileshare dan staat hier de rootmap zoals gedefinieerd in de kolom _Tekst_ van instelling _Sectie: Documenten_ en _Item: Documentroot_.
