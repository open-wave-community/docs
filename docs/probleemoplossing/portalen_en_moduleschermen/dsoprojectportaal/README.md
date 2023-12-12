# DSO Project portaal

AanroepAction: OpenTabPage(#dsoprojectportal/x) waarbij x = primary key uit tbdsoproject.

Het nieuwe portaal DSO projectportaal toont een overzicht van alle zaken behorende bij één DSO project (basis vwfrmdsoprojectoverzicht) en is gemaakt om voor de gebruikers meer overzicht te creëren wat er speelt onder één project als de nieuwe Omgevingswet in gaat.

Het portaal heeft een raadpleegfunctie: de zaken uit het DSO met hetzelfde project id worden getoond inclusief de bijbehorende Activiteiten, actieve behandelaars, contactgegevens, leges, geregistreerde documenten en projectlocaties van deze zaken.

Tevens is er een overzicht van de via groep aan deze DSO zaken verbonden zaken die NIET uit het DSO komen; de zogenaamde **Vervolgzaken**.

Er zal via het portaal naar de zaken genavigeerd kunnen worden, echter het daadwerkelijk wijzigen van een zaak zal in het zaakportaal plaatsvinden zoals men gewend is.

## Hoe komt men in het portaal?

Het portaal is te benaderen vanaf de tegel **Mijn DSO projecten** OF via tegel **Mijn DSO projecten (zonder Vooroverleg)**.

Standaard is de tegel _Mijn DSO projecten_ (achterliggende view vwfrmdsoprojectoverzicht) zichtbaar en aanklikbaar, mits men omgevingszaken mag zien.
De tegel opent een lijst met alle DSO projecten waarvoor de ingelogde gebruiker bij tenminste één van de achterliggende DSO zaken de actieve behandelaar is.

De tegel _Mijn DSO projecten (zonder Vooroverleg)_ is alleen zichtbaar indien men nieuwe instelling _Sectie: Programma en Item: DSOPortaalZonderVooroverleg_ aan heeft gemaakt en aangevinkt staat (tegel _Mijn DSO projecten_ wordt hiermee onzichtbaar).

Deze tegel, met achterliggende view vwfrmdsoprojectoverzichtzvo, opent ook de lijst met alle DSO projecten waarvoor de ingelogde gebruiker bij tenminste één van de achterliggende DSO zaken de actieve behandelaar is met uitzondering van de DSO projecten waarvoor alleen een Vooroverleg zaak aanwezig is.

## Problemen

Het scherm ziet er raar uit (al of niet met errormelding) of reageert niet:

- de variabele x uit de aanroep verwijst niet naar een bestaande tbdsoproject.dnkey
- inlogger heeft geen kijkrechten voor Omgevingszaken (zie rechten: de inlogger behoort tot een rechtengroep waarbij _Omgevingszaken Zichtbaar_ niet is aangevinkt)
- alle tegels zijn disabled of onzichtbaar op conditie (zie [Portaldefinitie](/docs/instellen_inrichten/portaldefinitie/README.md))
- indien er voor 1 van de zaakkolommen van dit portaal geen zichtbare tegel is, dan is de tegel zichtbaar die toont dat er voor die kolom geen zaken zijn
- geen enkele tegel uit dit portal is toegekend aan inlogger.

Medewerker a ziet meer of minder tegels dan medewerker b:

Dit kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan medewerker b.
Het kan ook voorkomen dat medewerker a andere rechten heeft dan medewerker b: in de kolom _Vervolgzaken_ wordt per tegel het voor die module gewenste recht geëvalueerd.

## Overige triggers

Klikken op tegel opent een vervolgscherm.

Indien niet klikbaar dan is de tegel ingesteld als disabled (zie [Portaldefinitie](/docs/instellen_inrichten/portaldefinitie/README.md)).

## Zie ook

- [Tegels onder kolom Afgesloten DSO-Zaken](/docs/probleemoplossing/portalen_en_moduleschermen/dsoprojectportaal/tegels_kolom_gesloten_dsozaken/README.md)
- [Tegels onder kolom Lopende DSO-Zaken](/docs/probleemoplossing/portalen_en_moduleschermen/dsoprojectportaal/tegels_kolom_lopende_dsozaken/README.md)
- [Tegels onder kolom Overig](/docs/probleemoplossing/portalen_en_moduleschermen/dsoprojectportaal/tegels_kolom_vervolgzaken/README.md)
- [Tegels onder kolom Vervolgzaken](/docs/probleemoplossing/portalen_en_moduleschermen/dsoprojectportaal/tegels_kolom_overig/README.md)
