# Samenvoegen

Met samenvoegen wordt bedoeld:

* het samenvoegen van twee inrichtingen tot één
* of het samenvoegen van twee locaties tot één
* of het samenvoegen van twee contactadressen tot één.

## Samenvoegen van twee inrichtingen

Wordt getriggerd door de knop linksonder op het tabblad inrichtingen van het zaken/inrichtingenportaal en op scherm *Alle inrichtingen* indien de inlogger het samenvoegrecht bij inrichtingen heeft (tbmilrechten.dlbmilinrsamen).

De actieve inrichting (inrichting A hieronder) is de inrichting die opgaat in een andere inrichting.

In het eerste wizardscherm moet de gebruiker een andere inrichting aanwijzen (dat is de inrichting die blijft bestaan) uit dezelfde straat.

In het tweede scherm wordt alleen om een bevestiging gevraagd.

Stel inrichting A wordt samengevoegd met inrichting B, waarbij inrichting B blijft bestaan, dan vinden bij UITVOEREN de volgende acties plaats:

* 1. Alle verwijzingen naar A, in wat voor tabel dan ook (zoals contacten, inspecties, emissies, maar ook milieu en gebruiksvergunningen ), worden vervangen door een verwijzing naar B.
* 2. Als inrichting A een hoofdvestiging is van een of meer andere inrichtingen, dan word B de nieuwe hoofdvestiging voor deze inrichtingen.
* 3. Als een kolom van de detailkaart van B geen waarde heeft, dan wordt de waarde uit A voor dezelfde kolom overgenomen. Anders niet.
* 4. Als zowel A als B een hoofd-SBI hebben, dan wordt die van B de enige hoofd-SBI.
* 5. De memo van A wordt toegevoegd onderaan de memo van B.
* 6. Inrichting A wordt verwijderd.

LET OP: de wizard gaat GEEN mappen en documenten op mappen waar die key van die inrichting in voorkomt verschuiven.
Als inrichting A gekoppeld is aan het externe zaaksysteem vervalt deze koppeling indien inrichting B ook al gekoppeld was.

## Samenvoegen van twee contactadressen

Wordt getriggerd door de knop linksonder op de lijst van het adresboek van het openingsportaal indien de inlogger het samenvoegrecht bij contactadressen heeft (tbrechten.dldcasam).

De actieve contactadreskaart (contactadres A hieronder) is het adres dat opgaat in een ander contactadres.

In het eerste wizardscherm moet de gebruiker een ander contactadres aanwijzen (dat is het contact dat blijft bestaan) op grond van invoer van de dnkey (kolom ID) van dat contactadres.

In het tweede scherm wordt alleen om een bevestiging gevraagd.

Stel contactadres A wordt samengevoegd met contactadres B, waarbij contactadres B blijft bestaan, dan vinden bij UITVOEREN de volgende acties plaats:

* 1. Alle verwijzingen naar A, in wat voor tabel dan ook (zoals contacten bij omgevingszaak, contacten bij handhaving inspectiebezoeken, correspondentie, adviesinstanties ), worden vervangen door een verwijzing naar B.
* 2. Als een kolom van contactadres B geen waarde heeft, dan wordt de waarde uit A voor dezelfde kolom overgenomen in B. Anders niet.
* 3. Contactadres A wordt verwijderd.

## Samenvoegen van twee locaties

Wordt getriggerd door de knop linksonder op de lijst van de locaties van een straat (tegel *Locaties* van het openingsportaal) indien de inlogger het samenvoegrecht bij locaties heeft (tbrechten.dldvgdedt).

De actieve locatie (locatie A hieronder) is het adres dat opgaat in een andere locatie.

In het eerste wizardscherm moet de gebruiker een ander - niet vervallen - locatieadres aanwijzen (dat is het adres dat blijft bestaan) uit dezelfde straat.

In het tweede scherm wordt alleen om een bevestiging gevraagd.

Stel locatieadres A wordt samengevoegd met adres B, waarbij locatieadres B blijft bestaan, dan vinden bij UITVOEREN de volgende acties plaats:

* 1. Alle verwijzingen naar A, in wat voor tabel dan ook (zoals omgevingszaken, inrichtingen, handhavingszaken) worden vervangen door een verwijzing naar B.
* 2. Als een kolom van locatieadres B geen waarde heeft, dan wordt de waarde uit A voor dezelfde kolom overgenomen in B met uitzondering van de kolommen huisnummer, huisletter, huislettertoevoeging en huisnrinfo en ddvervaldatum.
* 3. Locatieadres A wordt verwijderd.
