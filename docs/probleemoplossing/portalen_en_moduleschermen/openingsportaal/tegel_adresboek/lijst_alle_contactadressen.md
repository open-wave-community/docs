# Lijst alle contactadressen

De schermidentifier is:

- indien de inlogger lid is van een rechtengroep die het recht _is groep voor publiek (tbrechten.dlaispubliekgroep_) uitgevinkt heeft staan: MDLC_geefContactenOverzicht_alles.xml
- anders (_is groep voor publiek_ staat aangevinkt) dan MDLC_geefContactenOverzicht_allespubliek.xml.

Dit scherm wordt aangeroepen met action _getflexList(tbcontactadressen)_ vanuit het openingsportaal (tegel _Adresboek_).

## Welke gegevens worden getoond

Alle gegevens van vwfrmcontactadressen waarbij indien het recht _is groep voor publiek_ aangevinkt staat voor de inlogger alleen de kolommen persoonsnaam, bedrijfsnaam en geslacht zichtbaar zijn: althans zo wordt MDLC_geefContactenOverzicht_allespubliek.xml opgeleverd.

## Problemen

Het scherm geeft een foutmelding:

- er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Schermkolomdefinitie rapportages](/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_instellingen/schermkolomdefinitie_rapportages.md)) die niet valide is
- de inlogger moet lid zijn van rechtengroep die kijkrechten heeft op de contactadressen (tbrechten.dlaadrvsb).

## Filteropties

De filteropties (de lijst kan nu onder meer gefilterd worden op combinaties van achternaam, bedrijfsnaam, vestiginglaats en postadresplaats en dnkey, email en BSN) zijn alleen zichtbaar indien de lijst gestart wordt vanuit de tegel adresboek op het openingsportaal (beter gezegd: vanuit de action-aanroep getFlexList(tbcontactadressen), waarbij de inlogger het recht tbrechten.dlaispubliekgroep NIET aangevinkt heeft staan. De filter is gedefinieerd in MDFC_geefContactenOverzicht_alles.xml waarbij de invoervelden voor bedrijfsnaam, achternaam, vestigingsadres en postadres met de operator LIKE zijn gedefinieerd, hetgeen betekent dat indien de gebruiker als zoekwaarde bij bijvoorbeeld achternaam

- _jansen_ invoert, OpenWave zoekt op dvachternaam = jansen
- _jansen%_ invoert, OpenWave zoekt op dvachternaam begint met jansen
- _%jansen_ invoert, OpenWave zoekt op dvachternaam eindigt op jansen
- _%jansen%_ invoert, OpenWave zoekt op de substring jansen in dvachternaam

LET OP: OpenWave regelt dat het zoeken NIET CASE SENSITIVE gebeurt

## Triggers

- In het scherm: dubbel klikken op een regel opent het detailscherm van het geselecteerde contact. Altijd enabled. Zie [Contactadres](/probleemoplossing/module_overstijgende_schermen/contact_adres.md).
- Zoekeditbox rechtsonder in scherm: altijd aanwezig.
- pagingknoppen rechtsboven. Aanwezig indien aantal rijen groter dan de instelling _Getal1_ bij _Sectie: paging_ en _Item: pagesize_ (defaultwaarde = 100).
- De samenvoegknop linksonder is zichtbaar en enabled indien de inlogger het recht _samenvoegen contactadressen_ heeft (tbrechten.dldcasam).
- De insertknop linksonder zichtbaar indien de gebruiker het insertrecht heeft op de contactadressentabel (tbrechten.dldcadins).
- De deleteknop linksonder zichtbaar indien de gebruiker het verwijderrecht heeft op de contactadressentabel (tbrechten.dldcaddel).
