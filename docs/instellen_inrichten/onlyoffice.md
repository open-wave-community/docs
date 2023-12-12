# OnlyOffice

Mits geïnstalleerd kan OnlyOffice gebruikt worden om MS-Word documenten te bewerken in de Cloud (vanuit documentenlijst, creëer document en geregistreerde documenten).

## Wanneer besluit OpenWave om OnlyOffice aan te roepen

Wanneer een document wordt aangeklikt in OpenWave redeneert het programma als volgt:

 1. kan het document geopend worden met Office URI-scheme (dus gebruik maken van  de lokaal geïnstalleerde MS-Office). Dit is het geval indien:

  - vertrouwelijkheid OK
    - het document heeft de extensie DOCX of XLSX
    - EN het aangewezen document van de fileserver komt die onderdeel is van het Windows-domein van de ingelogde medewerker
    - EN het IP-adres van de huidige sessie (tbsessions) van de gebruiker voldoet aan het masker gedefinieerd in de kolom *IpRange* van een van de regels van de tabel tbipranges, waarbij de kolom dlhyperlink aangevinkt is
    - EN *Getal2* van *Sectie: Documenten, Item: OphalenViaFileserver* heeft de waarde 2 (bij een compartiment dat gebruikt van een satellite op de lokale fileserver kijkt OpenWave naar de kolom tbcompartiment dldocsfileshareofficeuri. Die moet aangevinkt zijn)
    - EN de bovenliggende zaak is niet geblokkeerd.

 2. Anders kan het document met OnlyOffice worden geopend? Dit is het geval indien:

  - vertrouwelijkheid OK
    - EN de instelling *Sectie: Documenten, Item: OnlyOffice* aangevinkt is
    - EN de extensie van dat document komt voor in de kolom *Tekst* van deze instelling (extensies gescheiden door puntkomma, dus bijv. docx;xslsx;pdf)
    - EN de instelling *Sectie: OWB, Item: TussenMapOnlyOfficeDownloadFiles* bestaat en de kolom *Tekst* eindigt op *onlyoffice/download*/
    - EN de instelling *Sectie: OWB, Item: TussenMapOnlyOfficeUploadFiles* bestaat en de kolom *Tekst* eindigt op *onlyoffice/upload*/.

 3. Kan het document worden gedownload en direct via de browser geopend? Dit is het geval indien:

  - vertrouwelijkheid OK
    - EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand via een hyperlink met IE te openen
    - EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand via een Office URI-scheme te openen
    - EN de instellingen zijn dusdanig dat het programma GEEN poging doet het bestand met OnlyOffice te openen
    - EN de extensie van het document komt voor in de kolom *Tekst* van de instelling *Sectie: OWB, Item:DocumentBrowser*. De opgesomde extensies van de instelling moeten gescheiden zijn door een puntkomma dus bijv. *pdf;png;jpg*.

 4. Anders kan het document worden gedownload naar de device van de gebruiker? Dit is het geval indien

  - vertrouwelijkheid OK.

Indien het om een geregistreerd document gaat dat wordt gedownload maar de zaak is geblokkeerd, zal OpenWave het document eerst naar pdf renderen. Dit indien het gaat om de extensies ods, odt, odf, doc, docx, xls,xlsx of txt of xml.

Indien het document wordt gedownload bepalen vervolgens de instellingen van MS-Windows Explorer op grond van de extensie van het document, of en met welk pakket het document automatisch geopend wordt.

## Een bewerker tegelijk? Alleen bij geregistreerde documenten

Indien de  instelling *Sectie: OnlyOffice en Item: eenbewerkertegelijk* NIET bestaat of niet is aangevinkt dan wordt het document in de wijzigmodus geopend (tenzij het gaat om een geregistreerd document: dan gelden de uitzonderingen hieronder). Meerdere personen tegelijk kunnen eenzelfde document wijzigen. Degene die het laatst opslaat is degene die de nieuwe versie bepaalt.

Anders, indien de  nieuwe instelling *Sectie: OnlyOffice en Item: eenbewerkertegelijk* is aangevinkt dan wordt:

  - op de registratiekaart de docplaats veranderd in L (lokaal), waarmee voor andere mensen het document alleen in readonly modus geopend kan worden
  - het document in de wijzigmodus geopend. Per definitie kan dit maar één persoon zijn
  - wordt na sluiting van het document de docplaats veranderd in S (server) waarmee het document wordt vrijgegeven voor de eerstvolgende gebruiker.

## Readonly en wijzigmodus in OnlyOffice voor geregistreerde documenten

Indien een geregistreerd document wordt geopend met OnlyOffice dan redeneert OpenWave als volgt:
Indien:

  - de bovenliggende zaak is geblokkeerd
  - OF docplaats = L (lokaal)
  - OF datum verstuurd is gevuld
  - OF de richting is B (binnenkomend)
  - OF het document is Definitief
  - OF extensie = .pdf

Dan wordt het document in readonly modus geopend in OnlyOffice.

## Conversie van documenten naar PDF via OnlyOffice

Indien *Getal1* van *Sectie: Documenten en Item: ConverteerPDF* de waarde 1 heeft dan worden documenten geconverteerd naar PDF via de OnlyOffice installatie (mits aanwezig). Indien deze instelling niet bestaat of *Getal1* heeft een andere waarde, dan wordt geconverteerd met LibreOffice.

### Document uit DMS bewerken met OnlyOffice

Indien het aangewezen document uit een DSM komt (via Stuf zaak/DMS) dan zal het gewijzigde document via updateZaakDocument_Di02 met de bestaande documentidentifier worden aangeboden aan het DMS, in plaats van voegZaakDocumentToe_Lk01.

De kolom *Tekst* van de instelling *Sectie: KoppelingDOCNAAMDMS Item: HTTPSoapAction_updateZaakDocument_Di02* moet gevuld worden met juiste soapaction: `http://www.egem.nl/StUF/sector/zkn/0310/updateZaakDocument_Di02`.

## Stroomschema bewerken document via OnlyOffice

Indien OnlyOffice geïnstalleerd en instellingen OK, dan redeneert OpenWave als volgt bij het openen van een document:

![](applicatiebeheer/instellen_inrichten/onlyoffice.png){ class="media" loading="lazy" alt="" width="700" }

## Logging door OpenOffice

In een configuration-file van OnlyOffice zelf (niet door functioneel beheerders aan te passen) kan ingesteld worden dat OnlyOffice zelf een logging bijhoudt. Dit is van invloed op de performance. Default staat deze logging uit.

Achter de tegel *Versie Informatie* op het servicecentrumportaal is dit zichtbaar op de regel Koppelingen-OnlyOffice (bijvoorbeeld: 7.1.1.23; logging off).
