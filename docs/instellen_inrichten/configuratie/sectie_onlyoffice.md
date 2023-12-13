# Sectie OnlyOffice

Hieronder de instellingen uit de [configuratietabel](README.md) (tbinitialisatie) van de _Sectie: OnlyOffice_ gerangschikt op item. Kijk voor overige OnlyOffice instellingen bij:

- Sectie: OWB items: TussenmapOnlyOfficeUploadfiles en TussenmapOnlyOfficeDownloadfiles
- Sectie: Documenten Item: OnlyOffice
- Sectie: Sessie items: AlwaysCreateSession en MaxMinutesSession

## Items Configuratietabel
| Item | Kolom | Omschrijving |
| ---- | ------- | ------ |
| config_language | Tekst | nl |
| | Info | Dit item bepaalt de taal van de OnlyOffice interface (INDIEN er andere talen dan Engels aanwezig zijn). Het wordt ingesteld door de _Tekst_ te vullen met twee-letterige taal-codes (nl, en, de, ru, it, etc.). Default = en |
| config_permission_download | Tekst | false |
| | Info | Mag het bestand gedownload worden of alleen bekeken en ge-edit. Default = false |
| config_permission_edit | Tekst | true |
| | Info | Mag het bestand ge-edit worden? Default = true |
| config_permission_print | Tekst | false |
| | Info | Mag het bestand geprint worden? Default = false |
| config_permission_review | Tekst | true |
| | Info | Mag het bestand gereviewed worden? Default = true |
| config_platform | Tekst | desktop |
| | Info | Defines the platform type used to access the document. Can be: optimized to access the document from a desktop or laptop computer - desktop, optimized to access the document from a tablet or a smartphone - mobile, specifically formed to be easily embedded |
| Eenbewerkertegelijk | Aanvinkvakje | Indien aangevinkt dan wordt bij het openen van een geregistreerd document via OnlyOffice op de registratiekaart de dvdocplaats veranderd in L (lokaal), waarmee voor andere mensen het document alleen in readonlymodus geopend kan worden. Vervolgens wordt het document in de wijzigmodus geopend. |
Per definitie kan dit maar één persoon zijn. Vervolgens wordt na sluiting van het document de dvdocplaats veranderd in S (server) waarmee het document wordt vrijgegeven voor de eerstvolgende gebruiker|
| show_review_changes | Tekst | true |
| | Info |Defines if the review changes panel is automatically displayed or hidden when the editor is loaded. The default value is false |
| Sleuteldomein | Tekst |De (geëncrypte) sleutel waarmee het programma de OnlyOfficetoken kan valideren |
| track_changes | Tekst | true |
| | Info |Defines if the document is opened in the review editing mode (true) or not (false) regardless of the document.permissions.review parameter (the review mode is changed only for the current user). If the parameter is undefined, the document.permissions.review value is used (for all the document users) |
