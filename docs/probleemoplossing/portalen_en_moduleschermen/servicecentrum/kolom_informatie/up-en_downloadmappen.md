# Up- en downloadmappen

## Trigger

De tegel is een trigger voor een lijst van alle documenten die op dat moment bestaan op een van de up- en downloadmappen van de OpenWave-server. Dit zijn de mappen (die door REM bij implementatie worden aangemaakt)  gedefinieerd met de instellingen:

* TussenmapUploadfiles: kolom *Tekst* van *Sectie: OWB en Item: TussenMapUploadFiles* mits eindigend op */openwave/upload*/.  Deze map wordt gebruikt als tussenstation indien een gebruiker een document van eigen device upload naar het opslagmedium van OpenWave: een DMS of fileshare of naar SWF.
* TussenmapDownloadfiles: kolom *Tekst* van *Sectie: OWB en Item: TussenMapDownloadFiles* mits eindigend op */openwave/download*/. Deze map wordt gebruikt als tussenstation indien een gebruiker een document van het opslagmedium van OpenWave: een DMS of fileshare of van het SWF naar eigen device brengt.
* TussenmapOLOUploadfiles: kolom *Tekst* van *Sectie: OWB en Item: TussenMapOLOUploadFiles* mits eindigend op */openwave/uploadolo*/. Deze map wordt gebruikt als tussenstation voor de documenten (bijlages) die met een OLO-bericht meekomen en geplaatst moeten worden in het opslagmedium van OpenWave: een DMS of fileshare.
* TussenmapDSOUploadfiles: kolom *Tekst* van *Sectie: OWB en Item: TussenMapDSOUploadFiles* mits eindigend op */openwave/uploaddso*/. Deze map wordt gebruikt als tussenstation voor de documenten (bijlages) die met een DSO-bericht meekomen en geplaatst moeten worden in het opslagmedium van OpenWave: een DMS of fileshare.
* TussenmapOnlyOfficeUploadfiles: kolom *Tekst* van *Sectie: OWB en Item: TussenMapOnlyOfficeUploadFiles* mits eindigend op */openwave/onlyoffice/upload*/. Deze map wordt gebruikt als tussenstation om documenten vanuit het opslagmedium van OpenWave: een DMS of fileshare naar de OnlyOffice-server te brengen.
* TussenmapOnlyOfficeDownloadfiles: kolom *Tekst* van *Sectie: OWB en Item: TussenMapOnlyOfficeDownloadFiles* mits eindigend op */openwave/onlyoffice/download*/. Deze map wordt gebruikt als tussenstation om documenten vanuit de OnlyOffice-server terug te zetten in het opslagmedium van OpenWave: een DMS of fileshare.
* TussenmapGrotefiles: kolom *Tekst* van *Sectie: OWB en Item: TussenMapGroteFiles* mits eindigend op */openwave/grotefiles*/. Deze map wordt gebruikt als tussenstation indien een gebruiker een een aantal documenten als zip-file vanuit het opslagmedium van OpenWave: een DMS of fileshare of van het SWF naar eigen device brengt.

In de lijst is te zien vanaf welk datum/tijdstip de documenten automatisch vernietigd worden op deze map. Dat is de creatiedatum/tijd + een aantal ingestelde uren.

Voor normale up-en downloads en DSO/OLO uploads is dat de instelling *Getal1* van *Sectie: OWB en Item: MaxUurUpload*. Voor OnlyOffice *Getal1* van *Sectie: OWB en Item: MaxUurOnlyOfficeUpload*.

Voor de grote zip-files *Getal1* van *Sectie: OWB en Item: MaxUurGroteFilesUpload*.

De tegel is alleen zichtbaar voor inlogger wanneer:

* deze aan hem/haar is toegekend
* de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.

Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

De inlogger dienst beheerrechten te hebben OF het recht *Toelaten geforceerde download geregistreerd document* (tmomgrechten.dlcomgcorregdwl).

Met dat laatste recht is alleen toegang tot de map TussenmapGrotefiles geregeld.

De inlogger met beheerrechten kan een document downloaden (waarbij de UUID-prefix wordt weggelaten) maar ook vernietigen. De inlogger met alleen *Toelaten geforceerde download geregistreerd document* kan alleen downloaden vanaf de map TussenmapGrotefiles.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Servicecentrum*
* Kolom: *Informatie*
* Kopregel: *Up-en Downloadmappen*
* Actie: *getFlexList(getUploadDownloadMappenList)*
