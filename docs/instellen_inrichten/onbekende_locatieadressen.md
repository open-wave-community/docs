# Onbekende locatieadressen

Het is gebruikelijk dat naast de BAG-adressen er ook één of meerdere onbekende locatieadressen in OpenWave bestaan. Het gaat hier dan om de adressen waarop zaken (en inrichtingen) kunnen worden aangemaakt die niet op een specifiek BAG-adres plaatsvinden. Bijvoorbeeld een zaak of inrichting waarbij de locatie op meerdere plekken in een straat kan zijn, of tussen bepaalde huisnummers in ligt/een gebied omvat etc.

Deze adressen worden volgens intern bij de organisatie afgesproken werkwijze aangemaakt/onderhouden in OpenWave via de tegel *Locaties* (basistabel tbperceeladressen). Denk hierbij aan adressen met huisnummer 9999 of 0.

Voor deze onbekende adressen is het mogelijk om in verschillende werkvoorraadschermen, in de portaalschermen van Omgeving- en Handhavingszaken en in het inrichtingportaal, hier niet meer de straatnaam of adres te tonen uit tbperceeladressen, maar de omschrijving van de hoofdprojectlocatie uit de tabel tbzaakkadperc.

Zo kan er makkelijker gezocht worden op deze zaken.

## Definiëren onbekend locatieadres

Bovenstaande nieuwe functionaliteit zal alleen zichtbaar worden indien er door functioneel beheer bij de onbekende locatieadressen uit tbperceeladressen de kolom *Onbekend adres?* wordt aangevinkt. Default staat dit veld NIET aan.
Het veld is terug te vinden in het detailscherm van een locatie/perceeladres (te benaderen via tegel *Locaties*) in het blok *Status*.

Bij het aanmaken van een nieuw locatieadres kan men in de wizard het vinkje *Onbekend adres?* aanvinken. In dat geval wordt de nieuwe locatie aangemaakt met eigenschap *Onbekend adres?* aangevinkt. Indien gewenst kan men meerdere onbekende locatieadressen aanmaken in dezelfde woonplaats, straat en huisnummer mits bij het aanmaken van de locatie het veld *Huisnummer extra info* opgegeven wordt en deze een waarde bevat die nog niet voorkomt in tbperceeladressen.

## Hoofdprojectlocatie definiëren bij de zaak/inrichting

Bij een zaak (module Omgeving en module Handhaving) kunnen meerdere projectlocaties/kadastrale percelen van toepassing zijn. Hetzelfde geldt voor een inrichting in OpenWave. Deze projectlocaties/kadastrale percelen zijn op te geven via de tegel *Projectlocaties/Kadastrale percelen* in de tabel tbzaakkadperc.

In het detailscherm van zo'n projectlocatie is het vinkje **Hoofd projectlocatie?**.

Per zaak/inrichting kan er maar één projectlocatie/kadastraal perceel zijn waarbij dit vinkje aan staat. Er is dus maar één hoofdprojectlocatie per zaak/inrichting (OpenWave zorgt voor de bewaking hiervan).

Voor projectlocaties bij omgevingzaken die aangemaakt zijn op grond van stambericht DSO geldt dat indien de zaak is aangemaakt bij het onbekende perceeladres (DummyLokatiePerceelkey of dnkeyswfdummyadres bij compartiment) EN de instelling *Sectie: DSO-VerzoekAfhandelen en Item: Hoofdprojectlocatie* is aangevinkt, dat dan de kolom tbzaakkadperc.dlhoofdprojectlocatie van de eerste projectlocatie uit het STAM-bericht automatisch op T gezet wordt.

## Rechten

Per module is er een apart recht  dat bepaald of een medewerker het vinkje hoofdprojectlocatie mag aanzetten/weghalen. Het gaat hier om recht tbomgrechten.dlcomgzkphoofdedt voor de omgevingsmodule, tbhhrechten.dlbhahzkphoofdedt voor de handhavingsmodule en recht tbmilrechten.dlcmilinrzkphoofdedt voor de inrichtingsmodule.

## Omschrijving van hoofdprojectlocatie in koptekst Zaak-/Inrichtingsportaal

OpenWave redeneert als volgt indien een zaak op een onbekend adres staat (dus: tbperceeladressen.dlonbekendadres is aangevinkt) EN er is een hoofdprojectlocatie opgegeven onder de tegel *Projectlocaties/Kadastrale percelen*, dan zal in koptekst3 van het zaak/inrichtingportaal niet meer het lokatieadres uit tbperceeladressen komen te staan maar de opgegeven projectlocatieomschrijving (de kolom tbzaakkadperc.dvstraatnaam).

**Let op**: Indien er in het beheer bij de portaaldefinitie eigen gedefinieerde kopteksten zijn dan zal de eigen gedefinieerde query van koptekst 3 leidend zijn.

De kolom *Projectlocatie* is van het type combobox.

Dit betekent dat indien het veld nog leeg is, en men klikt op het veld, dat er een dropdown verschijnt met projectlocatieomschrijvingen van eerder aangemaakte  hoofdprojectlocaties bij zaken die vallen op hetzelfde onbekend perceeladres.

### Een voorbeeld

 Omgevingszaak1 speelt zich af in Gemeente X, straat Y en huisnummer 0.
 Bij deze zaak bevindt zich een projectlocatie/kadastraal perceel waarbij het Hoofdlocatie vinkje aan staat. Het veld 'Projectlocatie' heeft hier waarde
 'Bevoegd gezag, straat y, project voorbeeld'.

 Omgevingszaak2 speelt zich ook af in Gemeente X, straat Y en huisnummer 0.
 Bij deze zaak wordt een nieuwe kaart in projectlocatie/kadastraal aangemaakt. In het detailscherm zal bij veld 'Projectlocatie' (indien nog leeg) hier in
 het dropdownlijstje de keuze komen te staan voor 'Bevoegd gezag, straat y, project voorbeeld'

 Omgevingszaak 3 speelt zich af op een ANDER adres, namelijk in Gemeente X, straat K en huisnummer 0. Ook dit adres is een onbekend adres.
 In het detailscherm zal bij veld 'Projectlocatie' (indien nog leeg) hier in het dropdownlijstje NIET de keuze komen te staan voor 'Bevoegd gezag, straat y,
 project voorbeeld'. Deze komt immers niet voor bij een projectlocatie/kadastraal perceel onder een zaak die zich afspeelt op hetzelfde locatieadres.
**Let op!** Wellicht ten overvloede: er kunnen dus meerdere projectlocaties zijn per zaak/inrichting maar alleen van de hoofdprojectlocatie zal de projectlocatieomschrijving in het zaakportaal (of inrichtingportaal) in de koptekst te zien zijn.

## Omschrijving van hoofdprojectlocatie in Werkvoorraad

In de schermen

* *(Mijn)Openstaande omgevinsgzaken*
* *(Mijn)Openstaande handhavingszaken*
* *Alle zaken*
* *Alle inrichtingen*

zal in de kolom *Straatnaam/Projectlocatie*  de openbareruimtenaam uit tbperceeladressen getoond worden tenzij bij dat perceeladres de kolom dlonbekendadres is aangevinkt EN er een hoofdprojectlocatie opgegeven is onder de tegel *Projectlocaties/Kadastrale percelen*. In dat laatste geval zal de opgegeven hoofdprojectlocatieomschrijving (de kolom tbzaakkadperc.dvstraatnaam) van de zaak/inrichting getoond worden.
