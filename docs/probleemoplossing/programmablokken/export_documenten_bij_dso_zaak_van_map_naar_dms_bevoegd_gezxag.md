# Export DSO-Documenten naar DMS van bevoegd gezag

Indien de gebruiker geautoriseerd is met het recht _Export docs DSO zaken van speciale map naar bev. gezag_(tbomgrechten.dlcomgdocbevgez) verschijnt achter de tegel _Exportlijst docs naar bev. gezag_ op het Openingsportaal in de kolom Beheer een lijst van omgevingszaken waarvoor geldt dat:

- de besluitdatum van de omgevingszaak is gevuld
- en de zaak GEEN compartimentszaak is
- en het DSO-verzoeknummer is gevuld (dvlvoaanvraagnr)
- en het DSO projectkey gevuld (dnkeydsoproject))
- en de _Exportdatum docs naar bevoegd gez_ (ddexportdocbevgez) in het blok Afhandeling op het detailscherm nog leeg is
- en het OIN-nummer van het bevoegd gezag voorkomt in de kolom _Tekst_ van de instelling _Sectie: Programma en Item: ExportDocVanMapNaarBevoegdGez_.

Indien dit het geval is kan met de wizardknop onderaan de lijst een proces worden gestart waarbij per zaak de documenten die op een bepaalde fileserver map staan worden geëxporteerd naar het DMS van het bevoegd gezag met stuf zaak/DMS en waarbij aanvullend een updatezaakbericht wordt verstuurd om die zaak in het DMS af te sluiten. Bij succes wordt de datum ddexportdocbevgez automatisch gevuld en verdwijnt de zaak uit de lijst.
Bij afspraak geldt dat in het externe DMS de zaakidentificatiecode gelijk is aan het DSO-verzoeknummer:

De tegel op het hoofdportaal is NIET automatisch toegekend aan medewerkers. De tegel is als volgt gedefinieerd in Portal Tegeldefinitie :

- Portaal: Openingsportaal
- Kolom: Beheer
- Kopregel: Exportlijst docs;naar bev. gezag
- Actie: getFlexList(SysStandardList,,{id},,omgeving_exportnaarbevgez)

OpenWave gaat alle documenten die staan op de map ingesteld in de kolom _Toelichting_ van de instelling _Sectie: Programma en Item: ExportDocVanMapNaarBevoegdGez_ verzenden naar het externe DMS met als zaak-identificatiecode het DSO-verzoeknummer. De map moet genoteerd worden inclusief documentroot dus bijvoorbeeld \*\\Nitro\\Wave\\Omgeving\%zaakjaar%\%zaaknr%\Export\*, waarbij de variabelen:

- `%zaakjaar%` door het jaar (jjjj) van de startdatum van de omgevingszaak wordt vervangen
- `%zaakjaar%` door de jaarmaand (jjjjmm) van de startdatum
- `%zaaknr%` met de wavezaakcode van de omgevingszaak.

Het is raadzaam om deze map ook in de configuratie instellingen op te nemen (_Sectie: Aanmaakmappen en Item: Omgeving_export_). Dan kunnen documenten vanaf andere mappen met de flextree [Verplaatsen van bestanden in OpenWave (fileshare)](/probleemoplossing/programmablokken/verplaatsen_bestanden_fileshare.md) daar naar toe verplaatst worden.

Elk document wordt in het stuf zaak/DMS bericht voorzien van dezelfde attributen documenttype en vertrouwelijkheid.

Hiertoe de instelling _Sectie: Programma en Item: Exportmapdsometadata_ met in de kolom _Tekst_ het gewenste documenttype en in de kolom _Info_ de gewenste vertrouwelijkheid.

Voor de OIN-nummers die voorkomen in de kolom _Tekst_ van de instelling _Sectie: Programma en Item: ExportDocVanMapNaarBevoegdGez_ geldt dat endpoint en credentials ingevuld moeten staan in de bijbehorende kaart van tb33gemeente. OpenWave zoekt per OIN-nummer naar de kaart in de beheertabel tboin. Daar kan het OIN-nummer gekoppeld worden aan een 4-cijferige gemeentecode. Die gemeentecode heeft een unieke kaart in de beheertabel tb33gemeente.

De operatie wordt uitgevoerd als runnable (dus eenmaal gestart draait het proces op de achtergrond en is geen communicatie met de gebruiker mogelijk). De voortgang wordt wel bijgehouden in de operationslog en desgewenst in de messagelog.
Per aangetroffen document wordt:

- een genereerdocumentidentificatie_Di02
- en een voegZaakdocumenttoe_LK02 (met DSO-verzoeknummer als zaakidentificatie) verstuurd.

Bij ontvangst van bevestigingsbericht (BV03) gaat OpenWave ervanuit dat het document geplaatst is in het externe DMS.

Wanneer alle documenten van een zaak zijn verstuurd volgt een UpdateZaak_LK02 bericht met een einddatum en een resultaattype. Het resultaattype wordt uit de bestaande mappingstabel voor aardbesluit/resultaattype van OpenWave gehaald (tegel _Afhandeling/Besluit
omg/apv/bouw/milieu/gebruik_ onder kolom Afhandeling in beheerportaal Zaakbeheer).

In het detailscherm van de omgevingszaak is de kolom _Exportdatum docs naar bevoegd gez_ (ddexportdocbevgez) in het blok Afhandeling alleen zichtbaar indien de instelling _Sectie: Programma en Item: ExportDocVanMapNaarBevoegdGez_ aangevinkt is. De kolom is slechts muteerbaar (om bepaalde exportproblemen te kunnen oplossen) indien de inlogger het recht _Export docs DSO zaken van speciale map naar bev. gezag_(tbomgrechten.dlcomgdocbevgez) heeft.

## Messagelog

Indien de instelling _Sectie: OWB en Item: MessageLog_ aangevinkt is, dan zullen de genereerDocumentidentificatie_Di02 en voegZaakdocumenttoe_LK02 berichten gelogd worden.
