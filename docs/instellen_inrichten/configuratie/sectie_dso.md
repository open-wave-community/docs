# Sectie DSO

Hieronder de instellingen uit de configuratietabel (tbinitialisatie) van de *Sectie: DSO* voor binnenkomende berichten gerangschikt op item.

Zie [Verwerking DSO STAM berichten](/docs/probleemoplossing/programmablokken/verwerking_dso_stam_berichten.md).

Kijk voor overige DSO instellingen bij:

* Sectie: OWB items: TussenmapDSOUploadfiles
* Sectie: SWF
* Sectie: DSO-Verzoekafhandelen

## Items Configuratietabel

| Item | Kolom | Omschrijving |
|---|---|---|
| AanvullingTotNieuweZaak| Aanvinkvakje |Indien aangevinkt zal bij de verwerking van een DSO STAM-bericht met als doel *Aanvullen* wanneer er nog GEEN bestaande zaak in OpenWave is voor het verzoeknummer, een nieuwe zaak aangemaakt worden. Deze situatie doet zich (bijv.) voor indien het DSO verzoek na wijzigen van bevoegd gezag binnenkomt in OpenWave terwijl er voor het originele verzoek al aanvullingen zijn geweest: het DSO stuurt dan alleen het laatste aanvullingsbericht naar OpenWave. |
| BewaardagenTabelDsoTrigger | Getal1 |Default 31. De kaarten uit de tabel tbdsotrigger met een ddaanmaakdatum ouder dan de hier ingevoerde aantal dagen geleden, worden automatisch verwijderd. |
| KopieberichtenOpslaan | Aanvinkvakje |Alleen indien aangevinkt zal een DSO STAM-bericht dat gekwalificeerd wordt als een kopiebericht (dus o.a. met een gevulde behandeldienst anders dan die van de host) toch - in het kader van zwarte gaten bij complexe vergunningen - als zaak worden opgeslagen. |
| Kwaliteitsborger | Aanvinkvakje |Indien aangevinkt zal bij de verwerking van een DSO STAM-bericht met activiteit *bouwactiviteit technisch* een contactadres aangemaakt worden met de rol kwaliteitsborger (tbadressoort.dldsorolkwaliteitsborger = T) op grond van de aanwezigheid van vraag-ids die daarop betrekking hebben. |
| Messagelog | Aanvinkvakje |Indien aangevinkt en *Getal1* is ongelijk 1 dan worden alleen de valide trigger- en verzoekberichten gelogd in Tbmessagelog (mits de algemene instelling *Sectie: OWB en Item: Messagelog* ook aangevinkt is). Indien *Getal1* de waarde 1 heeft, dan worden ook de niet valide berichten op het DSO-endpoint gelogd. |
| | Getal1 | Zie hierboven. |
| OntvangstBevestAutoVersturen| Aanvinkvakje |Indien aangevinkt zal bij de verwerking van een DSO STAM-bericht met als doel *Initieren, Vooroverleg, Conceptverzoek* of *Aanvullen* een Ontvangstbevestigingsmail verstuurd worden. Zie  [DSO Ontvangstbevestiging sturen](/docs/probleemoplossing/programmablokken/dso_ontvangstbevestiging.md). |
| VertalingVertrouwelijkheid | Tekst |Vul bij de kolom *Tekst* de omschrijving van het vertrouwelijkheidsniveau (uit beheertabel tbvertrouwelijkheid: tegel vertrouwelkijkheidsindicatie) die geldt als de default voor vertrouwelijke DSO bijlagen indien de vertouwelijkheid (in tbomgoloberichten) de waarde T heeft. Indien niet gevonden, OF de vertouwelijkheid (in tbomgoloberichten) ius F dan zoekt OpenWave nogmaals in tbvertrouwelijkheid op grond van  de kolom *Tekst* van de Instelling *Sectie: KoppelingDOCNAARDMS Item: OloVertrouwelijkheid*, Nog niet gevonden dan wordt naar de tekst *openbaar* gezocht  |
