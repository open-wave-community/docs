# Portalnaam

Screenidentifiers: MDLC_getPortalNamesList.xml en MDDC_getPortalNamesDetail.xml

## Welke portalnamen?

Het programma veronderstelt het bestaan van de volgende portalnamen:

- openingsportaal, althans één kaart waarbij de eigenschap _Is Beginportaal_ aangevinkt is. De naam zelf mag gewijzigd worden.
- beheer
- beheerportaal-NIEUW
- zaakbeheer
- Inrichtingenbeheer
- rapportage
- zoeken
- operations
- service centrum

en de zaakportalen:

- apvoverig
- bouwsloopdetail
- handhavingdetail
- omgevingdetail
- inrichtingdetail
- milieugebruikdetail
- horecadetail

Het weghalen van een dergelijk verplicht [portal](./README.md) kan leiden tot ernstige verstoringen. Niet doen dus. Het wijzigen van een dergelijk verplichte portalnaam kan leiden tot ernstige verstoringen. Niet doen (uitzondering dus het beginportaal).

U kunt dus wel een eigen nieuwe (unieke) portaalnaam maken ten behoeve van bijvoorbeeld tegels met links naar andere pakketten.
Stel u noemt dit portaal _Doorkiesportaal_ dan kunt u in het beginportaal ergens een tegel definiëren met een doorverwijzing naar dit doorkiesportaal. Dat wil zeggen met de action: _openTabPage(#Doorkiesportaal)_ en deze tegel toekennen aan de medewerkers die dit nieuwe portaal mogen benaderen.

## Betekenis van de kolommen

- **Is Beginportaal**. Er kan maar één van de rijen portaalnamen de eigenschap _is beginportaal_ aangevinkt hebben. Het uitvinken hiervan kan leiden tot ernstige verstoringen. Niet doen.
- **QueryTekst versneld uitschrijven**. Indien:
  - aangevinkt heeft dat tot gevolg dat de dynamische inhoud van de tegels (dus de inhoud op basis van de queries van getTileContent) bij het uitschrijven van een portaal achteraf wordt opgehaald. De gebruiker kan ondertussen de triggers van het portaal gebruiken (de knoppen en tegels zelf). De tegelinhoud wordt in één keer voor alle tegels uitgeschreven
  - niet aangevinkt (default waarde): dan zal de dynamische inhoud van de tegels één voor één worden opgehaald. Pas als alle tegels opgehaald zijn kunnen de triggers van het portaalscherm worden gebruikt.
- **(Tegel)lijsten opnemen als items in sidebar**. Is dit vakje aangevinkt dan wordt een lijst getart vanuit een portaal als item in de sidebar toegevoegd. Er kan echter maar één lijst per portaal tegelijk openstaan.
- **PortalType** ondersteunt vooralsnog alleen de waarde 1.
- **Portalheadertype** standaard waarde 1. Dit betekent dat de kopteksten van het portaalscherm door het programma gedefinieerd worden. Indien eigen kopteksten gedefinieerd zijn (zie de kolommen koptekst 1, koptekst 2 en koptekst 3) dan dient de waarde 2 te zijn.
- **Minimale breedte** (910) en hoogte (500) van portalscherm kunnen aangepast worden. De waardes 910 en 500 zijn gebaseerd op gebruik van IPad.
- Ook de **kolombreedte** (210) is gebaseerd op 5 kolommen naast elkaar voor een IPad.
- **Uitlijning van de tekst op kolomlabels**: Alleen (L)inks wordt momenteel ondersteund.
- **Uitlijning van tekst op de tegels**: Alleen (L)inks wordt momenteel ondersteund.
- **Sidebar groepsnaam** . Indien [sidebar](/instellen_inrichten/sidebar_zijbalk.md) aanstaat kan hier de naam van groep ingegeven worden bijv. Omgevingzaken of Handhaving.
- **Sidebar Label van element** onder groep. Hier kan in SQL het gewenste label opgegeven worden voor een specifiek element uit de sidebargroep bijvoorbeeld voor een specifieke omgevingszaak. In de SQL kan met {id} een variabele worden gebruikt die het programma dynamisch vervangt met de dnkey van de hoofdtabel van het aangeroepen portal. De SQL mag geen puntkomma's bevatten en moet beginnen met 'select' en de result set moet bestaan uit één kolom en één rij. Voorbeeld: _select dvzaakcode | | ' ' | | dvaanvraagnaam from vwfrmomgvergunningen where dnkeyomgvergunning = {id}_. Als de query geen resultaat geeft (het veld uit de select is leeg bv) dan geeft de sidebar de naam van de betreffende module, plus het zaaknummer.
- **Sidebar Hint van element** onder groep. Hier kan in SQL de gewenste hint opgegeven worden voor een specifiek element uit de sidebargroep bijvoorbeeld voor een specifieke omgevingszaak. In de SQL kan met {id} een variabele worden gebruikt die het programma dynamisch vervangt met de dnkey van de hoofdtabel van het aangeroepen portal. De sql mag geen puntkomma's bevatten en moet beginnen met 'select' en de result set moet bestaan uit één kolom en één rij.
- **Kopteksten Koptekst 1**. Hier kan in SQL de koptekst 1 opgegeven worden die in het portaalscherm als bovenste koptekstregel te zien zal zijn. In de SQL kan met {id} een variabele worden gebruikt die het programma dynamisch vervangt met de dnkey van de hoofdtabel van het aangeroepen portal. De SQL mag geen puntkomma's bevatten en moet beginnen met 'select' en de result set moet bestaan uit één kolom en één rij. Let op: het programma zal alleen kijken naar deze koptekst indien portaal headertype waarde 2 heeft voor dit portaal. Indien deze niet waarde 2 heeft (maar dus waarde 1) dan zal het programma kijken naar de standaard gedefinieerde kopteksten ipv de hier gedefinieerde koptekst 1.
- **Kopteksten Koptekst 2**. Hier kan in SQL de tweede koptekst opgegeven worden die in het portaalscherm als tweede koptekstregel te zien zal zijn. In de SQL kan met {id} een variabele worden gebruikt die het programma dynamisch vervangt met de dnkey van de hoofdtabel van het aangeroepen portal. De SQL mag geen puntkomma's bevatten en moet beginnen met 'select' en de resultset moet bestaan uit één kolom en één rij. Let op: het programma zal alleen kijken naar deze koptekst indien portaal headertype waarde 2 heeft voor dit portaal. Indien deze niet waarde 2 heeft (maar dus waarde 1) dan zal het programma kijken naar de standaard gedefinieerde kopteksten i.p.v. de hier gedefinieerde koptekst 2.
- **Kopteksten Koptekst 3**. Hier kan in SQL de derde koptekst opgegeven worden die in het portaalscherm als derde koptekstregel te zien zal zijn. In de SQL kan met {id} een variabele worden gebruikt die het programma dynamisch vervangt met de dnkey van de hoofdtabel van het aangeroepen portal. De SQL mag geen puntkomma's bevatten en moet beginnen met 'select' en de result set moet bestaan uit één kolom en één rij. Let op: het programma zal alleen kijken naar deze koptekst indien portaal headertype waarde 2 heeft voor dit portaal. Indien deze niet waarde 2 heeft (maar dus waarde 1) dan zal het programma kijken naar de standaard gedefinieerde kopteksten i.p.v. de hier gedefinieerde koptekst 3.

## Voorbeeld van met SQL gedefinieerde koptekst

Een voorbeeld van zelf gedefinieerde kopteksten met

- koptekst 1 = select 'Dit is een APV/Overige zaak' from tbportalnames
- koptekst 2 = select 'Met een eigen koptekst 2 ' | |dvovvergunningsnr from vwfrmovvergunningen where dnkeyovvergunning = {id}
- koptekst 3 = select 'Met een eigen koptekst 3 ' | | coalesce(dvovomschrijving,'') | | CHR(32) | | dvobjadres | | CHR(32) | | dvobjplaats from vwfrmovvergunningen where dnkeyovvergunning = {id}

geeft volgende resultaat:

![](../../img/applicatiebeheer/instellen_inrichten/portaldefinitie/2020-11-05_10_42_46-demo2_v.1.19.0.w.600_tok.99c2ee.png){ class="media" loading="lazy" alt="" width="600" }
