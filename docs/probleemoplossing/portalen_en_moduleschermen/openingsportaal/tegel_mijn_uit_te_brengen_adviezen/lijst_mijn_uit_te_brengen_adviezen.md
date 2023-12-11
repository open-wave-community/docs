# Lijst Mijn uit te brengen adviezen

Schermidentifier: MDLC_geefExterneAdviezenLijst.xml (voor Vaarwegzaken is dit MDLC_geefExterneAdviezenVaarwegLijst.xml).

Zie ook [Tegel Mijn uit te brengen adviezen](/docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_uit_te_brengen_adviezen.md)

## Welke gegevens worden getoond

De rijen uit de view vwowbopenstadviezenexternen (dan wel vwowbopenstadviezenexternen_vaarweg), dat zijn adviezen:

- met lege **adviesdatum (ddadviesdatum**)
- en met een gevulde rappeldatum die jonger is dan een jaar geleden
- en met een lege vervaldatum
- en met een lege blokkeerdatum (van bovenliggende zaak)
- en er moet een actieve behandelaar zijn bij bovenliggende zaak (tegel _In behandeling bij_)
- en de adviesinstantie is gedefinieerd bij één of meer medewerkers in de medewerkerstabelkolom _Is externe adviseur namens adviesinstantie_.

Boven op deze where clausules van de view is de volgende extra restrictie van kracht:

Indien instelling _Sectie: Adviezen_ en _Item: KiesAdviseur_ NIET aangevinkt is: dan worden alleen die uit te brengen adviezen getoond waarvoor de adviesinstantie voorkomt in het rijtje adviesinstanties bij het blok _is adviseur namens_ in de medewerkerskaart van de inlogger.
Is bovengenoemde instelling WEL aangevinkt dan zullen alleen die uit te brengen adviezen getoond worden waarvoor de inlogger als adviseur is toegewezen bij het advies en de adviezen waarvoor geen adviseur is toegewezen en de adviesinstantie voorkomt in het rijtje adviesinstanties bij het blok _is adviseur namens_ in de medewerkerskaart van de inlogger.

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de uit te brengen adviezen:
  - zie de criteria hierboven.
- De lijst geeft een foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ van tbinitialisatie _Sectie: Paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd zaakportaal van bovenliggende zaak
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).
