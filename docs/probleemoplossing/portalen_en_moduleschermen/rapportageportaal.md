# Rapportageportaal

Wordt aangeroepen door de action: OpenTabPage(#rapportage).

Dit portaal is bedoeld als doorkiesportaal voor _Rapportages_.
De tegels van dit portaal worden niet standaard uitgeleverd. De tegels met hun _action_ worden door applicatiebeheerders zelf gedefinieerd en toegekend aan één of meer medewerkers.

De hieronder besproken voorbeelden van rapportagetegels kunnen ook op andere portalen worden geplaatst, waarbij de _action_ hetzelfde blijft.

## Problemen

### Het scherm ziet er raar uit (al of niet met foutmelding) of reageert niet

- er zijn geen tegels gedefinieerd onder portalname = _Rapportage_ (Zie [Portal Definitie](../../instellen_inrichten/portaldefinitie/README.md))
- alle tegels zijn disabled of onzichtbaar of onzichtbaar_op_conditie
- geen enkele tegel uit dit portal is toegekend aan een inlogger.

### Het opschrift op een of meer tegels is niet zichtbaar

- er ontbreekt vaste tekst bij definitie portaltegel
- OF fout in dynamische queryverwijzing bij tegeldefinitie
  - indien foutieve queryverwijzing blijft tegel leeg
  - indien query zelf niet correct is, blijft tegel leeg
  - indien inlogger geen recht heeft om query uit te voeren blijft de tegel ook leeg.

### Onder dezelfde tegel ziet de ene gebruiker meer groepen of rapportages dan een andere gebruiker

- een gebruiker ziet alleen groepen waarvoor hij/zij op minimaal één van de onderliggende rapporten kijkrechten heeft: het rapportniveau van de medewerkerskaart van die gebruiker moet groter of gelijk zijn aan het vereist rapportageniveau bij de rapportdefinitie
- de gebruiker ziet alleen die rapporten van een groep waarvoor hij/zij kijkrechten heeft.

## Type rapportagetegels

Er zijn drie types:

- Tegel die direct een rapportage opent
- Tegel waarbij de gebruiker een rapportage kan kiezen uit één groep
- Tegel waarbij de gebruiker eerst een groep kiest en vervolgens een rapportage uit die groep

Zie voor indeling groepen en maken rapportages: [Rapportages](../../instellen_inrichten/rapportages.md).

### Tegel waarbij direct een rapportage wordt gestart

Hieronder een voorbeeld waarbij een rapportage zal worden gestart met primary key (tbrapporten.dnkey of id) = x. In het voorbeeld 2801

De tegel zelf is arbitrair ingedeeld in een kolom met de naam Omissies.

Het opschrift op de tegel kan gelijk zijn aan de rapportagenaam.

- Portaal: _Rapportage_
- Kolom: _Omissies_
- Kopregel:
- Vast Opschrift:_Inrichtingen zonder SBI_
- Dynamisch tegelopschrift:
- Actie: _startWizard(startReport,2801)_

### Tegel waarbij de gebruiker eerst een groep kiest en vervolgens een rapportage

Hieronder een voorbeeld waarbij de gebruiker kan kiezen uit rapportagegroepen die ingedeeld zijn met moduleletter W:

(en waarvoor geldt dat de gebruiker die de tegel aanklikt op minimaal één van de onderliggende rapporten kijkrechten heeft: het rapportniveau van de medewerkerskaart van die gebruiker moet groter of gelijk zijn aan het vereist rapportageniveau bij de rapportdefinitie).
De tegel zelf is arbitrair ingedeeld in een kolom met de naam Zaken.

- Portaal: _Rapportage_
- Kolom: _Zaken_
- Kopregel:
- Vast Opschrift:_Alle groepen van;Omgeving_
- Dynamisch tegelopschrift:
- Actie: _getFlexList(myReportGroupList,nil,nil,W)_

Indien de gebruiker uit alle groepen kan kiezen is de actie: _getFlexList(myReportGroupList)_.

### Tegel waarbij de gebruiker kies uit de rapportages van één rapportagegroep

Hieronder een voorbeeld waarbij de gebruiker kan kiezen uit de rapportages van een specifieke groep met primary key (tbrapportgroep.dnkey of id) = x. In het voorbeeld 581
(en waarvoor geldt dat de gebruiker kijkrechten heeft: het rapportniveau van de medewerkerskaart van die gebruiker moet groter of gelijk zijn aan het vereist rapportageniveau bij de rapportdefinitie). De tegel zelf is wederom arbitrair ingedeeld in een kolom met de naam Zaken. Het opschrift op de tegel kan gelijk zijn aan de rapportagegroepsnaam.

- Portaal: _Rapportage_
- Kolom: _Zaken_
- Kopregel:
- Vast Opschrift: _Omgevingvergunning Aantallen_
- Dynamisch tegelopschrift:
- Actie: \*getFlexList(myReportList,tbrapportgroep,581)
