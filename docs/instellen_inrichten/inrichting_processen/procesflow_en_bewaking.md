# Procesflow en bewaking

Een [proces](/docs/instellen_inrichten/inrichting_processen.md) is een verzameling regels die samen een bepaalde procesflow begeleiden bijvoorbeeld een ontvankelijkheidtoets. De procesregels hebben daarin de vorm van een termijnbewakingstap of van een afvinkstap.

Een termijnbewakingstap heeft een deadline. Die deadline wordt berekend aan de hand van termijnen gerekend vanaf een eerdere regel. De deadline van de allereerste regel is gerelateerd aan een startpunt: de ontvangstdatum van een zaak (datum constatering bij handhavingen). De gebruiker sluit een openstaande termijnstap door de afhandeldatum van die stap te vullen (kan ook met voor gedefinieerde acties als _creëer document_ of _kies vervolgzaak_).

Afvinkstappen zijn regels in de proces die als waarde Ja of Nee kunnen krijgen (met een vinkje). Een afvinkstap kan van invloed zijn op berekening van de deadlines, omdat bepaalde termijnstappen door de afvinkstap wel of niet zichtbaar worden.

Bij iedere zaak kan handmatig gekozen worden om een bepaalde procesflow te starten: er wordt een bepaalde proces gekozen. De gekoppelde processen bij de zaaktypes zijn bepalend voor de mogelijkheden. Indien geen gekoppelde processen bij het zaaktype, dan kan de gebruiker uit alle processen kiezen van dezelfde module/compartiment. Alleen de processen met de eigenschap _meerdere keren oproepbaar_ kunnen meer dan één keer aan een zaak worden toegevoegd.

Het kan ook zijn dat processen zijn gekoppeld aan het zaaktype met attribuut _automatisch_ Deze stappen worden dan al automatisch toegevoegd bij het creëren van de zaak (met de hand, via OLO, via DSO). Er kunnen dus meerdere processen tegelijk worden gekoppeld aan een zaak. Stapelen heet dat in OpenWave. De stappen van een proces die later worden bijgevoegd komen altijd onderaan (chronologisch) terecht.

Wanneer een proces wordt toegevoegd bij een zaak worden de gedefinieerde stappen in het beheerportaal daartoe gekopieerd naar de betrokken zaak. Uitgangspunt voor het berekenen van de deadlines van de termijn bewakingsregels is de ontvangstdatum van de aanvraag/vergunning en de datum constatering bij handhavingen.

Op het openingsportaal staat de tegel _Mijn procestaken_. De tegel toont de eerstvolgende niet afgehandelde processtappen per zaak die aan de inlogger zijn toegekend. Indien een stap niet aan een specifieke medewerker is toegekend, is de actieve behandelaar degene die deze taak krijgt. Instelbaar is of OpenWave hierbij kijkt naar de eerstvolgende stap per zaak of naar de eerstvolgende stap per proces per zaak. Zie [Tegel Mijn Procestaken](/docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_procestaken.md).
De tegel _Mijn procestaken_ kan ook aan een team worden toegekend (alle leden van dat team zien dan dezelfde openstaande stappenlijst).

Wanneer er twee of meer processen aan een zaak worden gekoppeld (bijv. zienswijze behandelen volgt op het proces Reguliere vergunning) is de eerste bewakingstermijn van het tweede proces gerelateerd aan de laatste termijn van de eerste (zie startregel onder lemma _Termijnstappen_). De eerste termijn van het eerste proces is altijd gerelateerd aan de startdatum van de zaak zelf.
