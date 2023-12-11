# Sectie DSO

Hieronder de instellingen uit de configuratietabel (tbinitialisatie) van de _Sectie: DSO_ voor binnenkomende berichten gerangschikt op item.

Zie [Verwerking DSO STAM berichten](/docs/probleemoplossing/programmablokken/verwerking_dso_stam_berichten.md).

Kijk voor overige DSO instellingen bij:

- Sectie: OWB items: TussenmapDSOUploadfiles
- Sectie: SWF
- Sectie: DSO-Verzoekafhandelen

## Items Configuratietabel

| Item                         | Kolom        | Omschrijving |
| ---------------------------- | ------------ | ------------ |
| AanvullingTotNieuweZaak      | Aanvinkvakje | Indien aangevinkt zal bij de verwerking van een DSO STAM-bericht met als doel _Aanvullen_ wanneer er nog GEEN bestaande zaak in OpenWave is voor het verzoeknummer, een nieuwe zaak aangemaakt worden. Deze situatie doet zich (bijv.) voor indien het DSO verzoek na wijzigen van bevoegd gezag binnenkomt in OpenWave terwijl er voor het originele verzoek al aanvullingen zijn geweest: het DSO stuurt dan alleen het laatste aanvullingsbericht naar OpenWave. |
| BewaardagenTabelDsoTrigger   | Getal1       | Default 31. De kaarten uit de tabel tbdsotrigger met een ddaanmaakdatum ouder dan de hier ingevoerde aantal dagen geleden, worden automatisch. |
| KopieberichtenOpslaan        | Aanvinkvakje | Alleen indien aangevinkt zal een DSO STAM-bericht dat gekwalificeerd wordt als een kopiebericht (dus o.a. met een gevulde behandeldienst anders dan die van de host) toch - in het kader van zwarte gaten bij complexe vergunningen - als zaak worden opgeslagen. |
| Kwaliteitsborger             | Aanvinkvakje | Indien aangevinkt zal bij de verwerking van een DSO STAM-bericht met activiteit _bouwactiviteit technisch_ een contactadres aangemaakt worden met de rol kwaliteitsborger (tbadressoort.dldsorolkwaliteitsborger = T) op grond van de aanwezigheid van vraag-ids die daarop betrekking hebben. |
| Messagelog                   | Aanvinkvakje | Indien aangevinkt en _Getal1_ is ongelijk 1 dan worden alleen de valide trigger- en verzoekberichten gelogd in Tbmessagelog (mits de algemene instelling _Sectie: OWB en Item: Messagelog_ ook aangevinkt is). Indien _Getal1_ de waarde 1 heeft, dan worden ook de niet valide berichten op het DSO-endpoint gelogd. |
|                              | Getal1       | Zie hierboven. |
| OntvangstBevestAutoVersturen | Aanvinkvakje | Indien aangevinkt zal bij de verwerking van een DSO STAM-bericht met als doel _Initieren, Vooroverleg, Conceptverzoek_ of _Aanvullen_ een Ontvangstbevestigingsmail verstuurd worden. Zie [DSO Ontvangstbevestiging sturen](/docs/probleemoplossing/programmablokken/dso_ontvangstbevestiging.md) |
| VertalingVertrouwelijkheid   | Tekst        | Vul bij de kolom _Tekst_ de omschrijving van het vertrouwelijkheidsniveau (uit beheertabel tbvertrouwelijkheid: tegel vertrouwelkijkheidsindicatie) die geldt als de default voor vertrouwelijke DSO bijlagen indien de vertouwelijkheid (in tbomgoloberichten) de waarde T heeft. Indien niet gevonden, OF de vertouwelijkheid (in tbomgoloberichten) ius F dan zoekt OpenWave nogmaals in tbvertrouwelijkheid op grond van de kolom _Tekst_ van de Instelling _Sectie: KoppelingDOCNAARDMS Item: OloVertrouwelijkheid_, Nog niet gevonden dan wordt naar de tekst _openbaar_ gezocht |
