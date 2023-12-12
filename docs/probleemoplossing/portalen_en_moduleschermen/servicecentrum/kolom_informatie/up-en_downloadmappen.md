# Up- en downloadmappen

## Trigger

De tegel is een trigger voor een lijst van alle documenten die op dat moment bestaan op een van de up- en downloadmappen van de OpenWave-server. Dit zijn de mappen (die door REM bij implementatie worden aangemaakt) gedefinieerd met de instellingen:

- TussenmapUploadfiles: kolom _Tekst_ van _Sectie: OWB en Item: TussenMapUploadFiles_ mits eindigend op _/openwave/upload_/. Deze map wordt gebruikt als tussenstation indien een gebruiker een document van eigen device upload naar het opslagmedium van OpenWave: een DMS of fileshare of naar SWF.
- TussenmapDownloadfiles: kolom _Tekst_ van _Sectie: OWB en Item: TussenMapDownloadFiles_ mits eindigend op _/openwave/download_/. Deze map wordt gebruikt als tussenstation indien een gebruiker een document van het opslagmedium van OpenWave: een DMS of fileshare of van het SWF naar eigen device brengt.
- TussenmapOLOUploadfiles: kolom _Tekst_ van _Sectie: OWB en Item: TussenMapOLOUploadFiles_ mits eindigend op _/openwave/uploadolo_/. Deze map wordt gebruikt als tussenstation voor de documenten (bijlages) die met een OLO-bericht meekomen en geplaatst moeten worden in het opslagmedium van OpenWave: een DMS of fileshare.
- TussenmapDSOUploadfiles: kolom _Tekst_ van _Sectie: OWB en Item: TussenMapDSOUploadFiles_ mits eindigend op _/openwave/uploaddso_/. Deze map wordt gebruikt als tussenstation voor de documenten (bijlages) die met een DSO-bericht meekomen en geplaatst moeten worden in het opslagmedium van OpenWave: een DMS of fileshare.
- TussenmapOnlyOfficeUploadfiles: kolom _Tekst_ van _Sectie: OWB en Item: TussenMapOnlyOfficeUploadFiles_ mits eindigend op _/openwave/onlyoffice/upload_/. Deze map wordt gebruikt als tussenstation om documenten vanuit het opslagmedium van OpenWave: een DMS of fileshare naar de OnlyOffice-server te brengen.
- TussenmapOnlyOfficeDownloadfiles: kolom _Tekst_ van _Sectie: OWB en Item: TussenMapOnlyOfficeDownloadFiles_ mits eindigend op _/openwave/onlyoffice/download_/. Deze map wordt gebruikt als tussenstation om documenten vanuit de OnlyOffice-server terug te zetten in het opslagmedium van OpenWave: een DMS of fileshare.
- TussenmapGrotefiles: kolom _Tekst_ van _Sectie: OWB en Item: TussenMapGroteFiles_ mits eindigend op _/openwave/grotefiles_/. Deze map wordt gebruikt als tussenstation indien een gebruiker een een aantal documenten als zip-file vanuit het opslagmedium van OpenWave: een DMS of fileshare of van het SWF naar eigen device brengt.

In de lijst is te zien vanaf welk datum/tijdstip de documenten automatisch vernietigd worden op deze map. Dat is de creatiedatum/tijd + een aantal ingestelde uren.

Voor normale up-en downloads en DSO/OLO uploads is dat de instelling _Getal1_ van _Sectie: OWB en Item: MaxUurUpload_. Voor OnlyOffice _Getal1_ van _Sectie: OWB en Item: MaxUurOnlyOfficeUpload_.

Voor de grote zip-files _Getal1_ van _Sectie: OWB en Item: MaxUurGroteFilesUpload_.

De tegel is alleen zichtbaar voor inlogger wanneer:

- deze aan hem/haar is toegekend
- de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.

Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

De inlogger dienst beheerrechten te hebben OF het recht _Toelaten geforceerde download geregistreerd document_ (tmomgrechten.dlcomgcorregdwl).

Met dat laatste recht is alleen toegang tot de map TussenmapGrotefiles geregeld.

De inlogger met beheerrechten kan een document downloaden (waarbij de UUID-prefix wordt weggelaten) maar ook vernietigen. De inlogger met alleen _Toelaten geforceerde download geregistreerd document_ kan alleen downloaden vanaf de map TussenmapGrotefiles.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Servicecentrum_
- Kolom: _Informatie_
- Kopregel: _Up-en Downloadmappen_
- Actie: _getFlexList(getUploadDownloadMappenList)_
