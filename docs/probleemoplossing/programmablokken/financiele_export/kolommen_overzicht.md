# Kolommenoverzicht Fis

Het kolommenoverzicht ten behoeve van de financiële export kan worden opgesteld door klikken op knop ![](/img/applicatiebeheer/instellen_inrichten/instellen_inrichten/schermdefinitie/lesgeven.png){ class="media" loading="lazy" alt="" width="20" } in de lijst: _[Lijst met te exporteren legesregels (vwfrmlegesexport)](/docs/probleemoplossing/programmablokken/financiele_export/lijst_met_te_exporteren_legesregels.md)_. De knop roept de wizard aan die een tekstbestand genereert van het kolommenoverzicht zoals het Fis exportbestand opgebouwd zal worden. Dit overzicht is belangrijk voor de test en voor het inrichten van de importroutine van het financieel systeem. De gebruiker kan hierin zien welke kolommen er in het uiteindelijke exportbestand zullen voorkomen (en met welke lengte en op welke positie). De wizard is aan te roepen nadat de lijst _Lijst met te exporteren legesregels (vwfrmlegesexport)_ gevuld is.

Om het kolommenoverzicht te kunnen maken moet bij de gebruiker het medewerkersrecht _Mag legesregels exporteren ([Fis export](/docs/probleemoplossing/programmablokken/financiele_export/README.md))_ aangevinkt staan.

De wizard controleert eerst of er te exporteren legesregels zijn en of aan voorwaarden wordt voldaan. Indien dit niet het geval is zal er voor de gebruiker een scherm verschijnen met daarin getoond waarom het kolommenoverzicht niet gegenereerd mag/kan worden. Indien er wel aan de voorwaarden wordt voldaan krijgt de gebruiker geen scherm te zien maar zal het gemaakte kolommenoverzicht als download aan de gebruiker worden aangeboden.

## Mogelijke kolommen

In de onderstaande tabel staan de kolommen die kunnen voorkomen in de exporttabel in volgorde van links naar rechts. De opgenomen kolommen, hun lengtes en hun posities zijn afhankelijk van de instellingen van de gekozen gemeente (indien geen gekozen gemeente dan afhankelijk van de default instellingen). In de tabel is te zien welke kolommen altijd aanwezig zullen zijn in het exportbestand (Aanwezig = ja) en welke kolommen eventueel aanwezig zijn (Aanwezig = ja/nee). De startposities liggen in principe vast en zijn alleen afhankelijk van welke kolom de voorgaande kolom is (en de lengte van deze kolom). Aangezien een deel van de kolommen een lengte heeft die afhankelijk is van instellingen, zijn de startposities hieronder deels aangegeven als _Variabel_. De genoemde database velden komen uit vwfrmlegesexport, tenzij anders aangegeven. De genoemde instelling zijn terug te vinden onder _Sectie: Fis4AllLeges_.

| **Kolomnaam** | **Aanwezig** |**Start positie**| **Lengte** | **Omschrijving** | |
| Bedrijfscode | ja | 1 | 2 |Waarde wordt opgehaald uit _Tekst_ bij _Item: Bedrijfscode_ en eventueel aangevuld met voorloopnullen tot lengte 2| |
| BedrijfsFCLcode | ja | 3 | 2 |Waarde wordt opgehaald uit _Tekst_ bij _Item: BedrijfsFCLcode_ en eventueel aangevuld met voorloopnullen tot lengte 2| |
| Notasoort | ja | 5 | 3 |Waarde wordt default opgehaald uit _Tekst_ bij _Item: Notasoort_ en eventueel aangevuld met voorloopnullen tot lengte 3. Indien gewenst kan er voor modules _horeca, info en apv_ een aparte notasoort ingesteld worden: _Notasoort_naammodule_. Indien instelling(en) niet bestaan of een lege tekst hebben dan zal notasoort waarde 000 krijgen| |
| Bedragsoort | ja | 8 | 2 |Afhankelijk van of het bedrag is de waarde CR (negatief bedrag) of DB (positief bedrag) | |
| Bedrag | ja | 10 | 9 |Waarde is: dflegesbedrag *100 (indien negatief getal, dan haal – weg) eventueel aangevuld met voorloopnullen tot lengte 9. Indien regels samengevoegd worden is hier het opgetelde bedrag van de legesregels opgenomen| |
| FCLnummer | ja | 19 |default 8|Indien regels samenvoegen dan wordt waarde opgehaald uit *Tekst* bij *Item: LegesSoortInTabel*, indien NIET samenvoegen dan wordt waarde opgehaald uit dvreknr van de legessoort. Voor beide gevallen geldt dat eerste deel van de gevonden string (voor eerste '-' teken) als waarde wordt genomen en eventueel aangevuld met voorloopnullen tot lengte: waarde van *Getal2* bij instelling *LengteFCL*. Is deze er niet dan de default lengte| |
| ECL | ja | Variabel |default 5|Waarde wordt opgehaald uit *Tekst* bij *Item: ECL* en eventueel aangevuld met voorloopnullen tot lengte zie *Getal2*. Indien *Getal2* niet gevuld dan de default lengte| |
|Inkomsten/uitgaven| ja | Variabel | 1 |Waarde is altijd I (inkomsten) | |
| BTWcode | ja | Variabel | 2 |Indien NIET samenvoegen dan wordt de BTW code eerste gezocht in dvreknr bij de legessoort (deel achter -BTW= ) indien niet gevonden OF indien WEL samenvoegen dan wordt de waarde gehaald uit *Tekst* bij *Item: BTWcode* en eventueel aangevuld met voorloopnullen tot lengte 2| |
| Debiteurennummer | ja | Variabel | 9 |Waarde is dvdebiteurnr van de legesregel aangevuld met voorloopnullen tot lengte 9| |
| Notanummer | ja | Variabel |default 9|Waarde is dvnotanummer van de legesregel aangevuld met voorloopnullen tot lengte: indien *Getal2* van instelling *NotaNummerIsKey* gevuld dan deze waarde anders default lengte| |
| Omschrijving | ja | Variabel | 50 |Waarde is altijd: ‘t.b.v. ‘ + dvbetreft (vwfrmalleaanvragen) waarbij de lengte afgekapt, respectievelijk aangevuld wordt met spaties tot lengte 50| |
| Kredietbeheerder | ja | Variabel | 5 |Waarde wordt opgehaald uit *Tekst* bij *Item: Kredietbeheerder* en eventueel aangevuld met voorloopnullen tot lengte 5| |
| Teken | ja | Variabel | 1 |Indien het bedrag negatief is, is waarde van Teken: -, anders is de waarde een spatie| |
| Void1 | ja | Variabel | 13 |Altijd 13 spaties| |
| Taak | ja | Variabel |default 5|Indien NIET samenvoegen dan wordt waarde gehaald uit dvreknr van de legessoort, indien WEL samenvoegen dan wordt waarde gehaald uit*Tekst\* _Item: LegesSoortInTabel_. Voor beide situaties geldt voor waarde Taak het deel van de string na eerste '-' teken tot aan eventueel tweede '-' teken. De lengte wordt eventueel aangevuld met voorloopnullen/afgekapt tot de waarde van _Getal1_ bij _Item: LengteTaak_. Indien niet aanwezig dan default lengte | |
| Void2 | ja | Variabel | 8 |Altijd 8 spaties| |
| Pakketnaam | ja | Variabel | 10 |Altijd waarde: Wave aangevuld met spaties tot lengte| |
| Tekst | ja | Variabel | 50 |Waarde is dvsoortzaak (vwfrmalleaanvragen) waarbij de lengte afgekapt, respectievelijk aangevuld wordt met spaties tot legnte 50| |
| Datum | ja | Variabel | 10 |Het programma kijkt naar instelling item _Datumformaat_ bij _Tekst_ of er een alternatieve datumnotatie is (bijvoorbeeld jjjjmmdd). Default is de notatie dd-mm-yyyy. De waarde is OF de ontvangstdatum van de bovenliggende zaak (default), OF de verzenddatum acceptgiro. Dat laatste is het geval wanneer instelling _Item: DatumAcceptgiroVerzondenInExport’_ AAN staat | |
| Void3 | ja | Variabel | 2 |Altijd 2 spaties| |
| | | | | **Alleen in het geval dat de per gemeente in te stellen instelling Item: Controle op ‘A’ staat (aanvrager) worden de kolommen uitgebreid met de volgende 6 debiteurgegevens** | |
| Debiteurnaam |ja/nee| Variabel | 100 |Naam van debiteur(dvdebiteurnaam,). Wordt aangevuld met spaties/ afgekapt tot lengte 100| |
| Debiteuradres |ja/nee| Variabel | 50 |Debiteuradres (dvdebcontadres). Wordt aangevuld met spaties/ afgekapt tot lengte 50| |
| Bedrijfnaam |ja/nee| Variabel | 100 |Bedrijfsnaam debiteur(dvdebbedrijfsnaam). Wordt aangevuld met spaties/ afgekapt tot lengte 100| |
| Postcode |ja/nee| Variabel | 10 |Postcode debiteur (dvdebpostcode). Wordt aangevuld met spaties/ afgekapt tot lengte 10| |
| Woonplaats |ja/nee| Variabel | 40 |Woonplaats debiteur (dvdebwoonplaats,). Wordt aangevuld met spaties/ afgekapt tot lengte 40| |
| BSNnummer |ja/nee| Variabel | 9 |BSN-nummer debiteur (dvdebbsnnummer). Wordt aangevuld met spaties/ afgekapt tot lengte 9. Indien _Item: BedrijfsIdInExport_ aangevinkt staat en bedrijfsnaam is gevuld, dan zullen er altijd 9 spaties staan ipv dvdebbsnnummer | |
| | | | | **Alleen in het geval dat de per gemeente in te stellen instelling Item: LegessoortInTabel aangevinkt staat worden de kolommen uitgebreid met de kolom Legessoort** | |
| Legessoort |ja/nee| Variabel | 40 |Waarde is dvlegessoortoms aangevuld met spaties/afgekapt tot lengte 40| |
| | | | | **Alleen in het geval dat de per gemeente in te stellen instelling Item: Controle op ‘A’ staat (aanvrager) en de kolom Getal2 heeft de waarde 1, dan worden de kolommen uitgebreid met de volgende 10 debiteurgegevens** | |
| Debiteurstraat |ja/nee| Variabel | 100 |Straatnaam debiteuradres (dvdebiteurstraat). Wordt aangevuld met spaties/ afgekapt tot lengte 100| |
| Debiteurhnr |ja/nee| Variabel | 5 |Huisnummer debiteuradres (dvdebiteurhnr). Wordt aangevuld met spaties/ afgekapt tot lengte 5| |
| Debiteurhlt |ja/nee| Variabel | 1 |Huisletter debiteuradres (dvdebiteurhlt). Wordt aangevuld met spaties/ afgekapt tot lengte 1| |
| Debiteurhtv |ja/nee| Variabel | 4 |Huisnummer toevoeging debiteuradres (dvdebiteurhtv). Wordt aangevuld met spaties/ afgekapt tot lengte 4| |
| Debiteurvoorl |ja/nee| Variabel | 10 |Voorletters van debiteur (dvdebiteurvoorl). Wordt aangevuld met spaties/ afgekapt tot lengte 10. Indien instelling _Item: VoorlettersZonderPuntjes_ AAN: dan worden de punten in dvdebiteurvoorl niet opgenomen in het exportbestand (voorbeeld: 'A.P.R.' wordt dan 'APR') | |
| Debiteurtvgsl |ja/nee| Variabel | 10 |Tussenvoegsel van debiteur (dvdebiteurtvgs). Wordt aangevuld met spaties/ afgekapt tot lengte 10| |
| Debiteurachtern |ja/nee| Variabel | 100 |Achternaam van debiteur (dvdebiteurachtern). Wordt aangevuld met spaties/ afgekapt tot lengte 100| |
| Debiteurgeslacht |ja/nee| Variabel | 1 |Geslacht van debiteur (dvdebiteurgeslacht). Indien niet aanwezig dan staat hier 1 spatie| |
| Debiteurpccijfer |ja/nee| Variabel | 4 |Waarde is het cijfergedeelte van de debiteurpostcode(dvdebiteurpccijfer). Indien niet aanwezig dan staan hier 4 spaties| |
| Debiteurpcletter |ja/nee| Variabel | 2 |Waarde is het lettergedeelte van de debiteurpostcode (dvdebiteurpcletter). Indien niet aanwezig dan staan hier twee spaties| |
| | | | | **Alleen als de instelling Item: ContactId aangevinkt staat, wordt de kolom ID toegevoegd** | |
| ID |ja/nee| Variabel | 10 |Waarde is dnkeycontactadres (debiteurencontact) aangevuld met spaties tot lengte 10| |
| | | | | **Alleen als de instelling Item: BedrijfsIdInExport aangevinkt staat, worden de kolommen Vestigingsnummer en KvK nummer toegevoegd aan het export bestand. Als deze instelling is aangevinkt, en de bedrijfsnaam van de debiteur is gevuld, dan wordt het BSN-nummer van een eventuele contactpersoon bij dit bedrijf niet opgenomen in het exportbestand** | |
| Vestigingsnr |ja/nee| Variabel | 12 |Waarde is dvdebvestigingsnr aangevuld met spaties tot lengte 12| |
| KvKnr |ja/nee| Variabel | 8 |Waarde is dvdebkvknummer aangevuld met spaties tot lengte 8| |
| | | | | **Alleen als de instelling Item: DMSNummerInExport aangevinkt staat, wordt de kolom zaakcode toegevoegd aan het exportbestand** | |
| Zaakcode |ja/nee| Variabel | 40 |Waarde is dvintzaakcode aangevuld met spaties tot lengte 40| |
