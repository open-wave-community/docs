# Zaaktypes

In het informatiemodel Zaken (RGBZ) heeft het zaaktype een centrale plaats. Zo ook in OpenWave. Op grond van het type van een zaak wordt de behandeling daarvan in OpenWave gereguleerd met het al dan niet zichtbaar zijn van bepaalde gegevens, met de beschikbaarheid van processen, resultaten, producten/diensten en documenten.
Onderstaande tekening is gebaseerd op de zaaktypes voor de module omgeving in de tabel tbsoortomgverg.

[<img src="/_media/openwave/applicatiebeheer/instellen_inrichten/zaaktypes.png?w=1200&amp;tok=501da6" class="media" loading="lazy" alt="" width="1200" />](/_detail/openwave/applicatiebeheer/instellen_inrichten/zaaktypes.png?id=docs%3Aapplicatiebeheer%3Ainstellen_inrichten%3Azaaktypes)

Grosso modo geldt dezelfde tekening voor de zaaktypes in de ander modules:

  - tbsoorthhzaak voor de Handhavingszaken
  - tbsoortinfoaanvraag voor Infoaanvragen
  - tbsoortovverg voor AVP/overige zaken
  - tbsoorthorverg voor Horecazaken
  - tbmilverg voor Milieu/gebruik zaken

De onderverdeling in modules zit van oudsher in OpenWave. Steeds meer echter wordt het gebruik van één module ondersteunt (die van omgevingszaken), waarin alle zaaktypes m.b.t. tot VTH passen. De definitie van de zaaktypes wordt daarmee nog belangrijker.

De zaaktypes worden gedefinieerd in het portaal *Zaakbeheer* onder de tegels van kolom *Zaaktypes*.

## Kolommen van omgevingszaaktype (tbsoortomgverg)

  - **Blok zaaktype OpenWave**
    - **Identifier** (dnkey). De unieke primary key van de tabel. Bij de definitie van sommige instellingen, zoals een aantal dat valt onder de *Sectie: Koppeling OLO*, kan naar deze identifier verwezen worden om het inlezen van OLO en/of DSO berichten aan het gewenste zaaktype te kunnen koppelen.
    - **Vervaldatum** (ddvervaldatum). Indien gevuld kan na die datum het betrokken zaaktype niet meer worden gekozen bij het handmatig opvoeren van een nieuwe zaak.
    - **Volgnummer** (dnvolgnr). Hiermee kan de volgorde van de keuzelijst zaaktype-omschrijvingen beïnvloed worden bij het bij het handmatig opvoeren van een nieuwe zaak.
    - **Publiceren** (dlpubliceren). Wordt niet door de interne programmatuur van OpenWave gebruikt. Kan desgewenst gebruikt worden voor rapportagedoeleinden.  Voor automatisch publiceren gebruikt OpenWave alle instellingen voor [DROP](/docs/applicatiebeheer/instellen_inrichten/drop).
    - **Verspreidbaar als complex** (dlmagverspreiden). Indien aangevinkt kan een zaak onder dit type over meerdere adressen gaan, waarmee mogelijk de optie [Complex Verspreiden](/docs/applicatiebeheer/probleemoplossing/programmablokken/complex_zaak/complex_verspreiden) zichtbaar wordt bij de zaak.
    - **Zaaktype** (dvomschrijving). De naam waaronder het zaaktype in OpenWave bekend is.
    - **Wetsartikel** (dvwetsartikel). Wordt niet door de interne programmatuur van OpenWave gebruikt.
    - **Opdrachtgever akkoord zichtbaar bij uren schrijven** (dlurenopdrgzb). Indien aangevinkt dan is deze kolom in het detailscherm van de urenregistratie (zie: [Urenregistratie](/docs/applicatiebeheer/probleemoplossing/module_overstijgende_schermen/urenregistratie)) zichtbaar bij dit zaaktype.
    - **Blokkeren bij sluiten zaak via wizard** (dlblokkerenbijsluitenzaak). Indien aangevinkt zal het vullen van de besluitdatum van de zaak via de wizard *SluitZaak* (dus via de wizardknop achter de kolom *afhandeldatum* op detailscherm van de zaak) bij dit zaaktype, ook tot gevolg hebben dat de zaak geblokkeerd wordt (ddblokkering krijgt systeemdatum). <wrap important>**LET OP:** In dit geval wordt er geen StUF Zaak/DMS updatezaakbericht of actualiseerzaakbericht verstuurd.<wrap>
    - **Legesregel verplicht** (dllegesregelverplicht). Indien GeenLegesBijDitZaaktype dan heeft dat tot gevolg dat de gebruiker aan de voorkant geen legesregel kan toevoegen bij het betreffende zaaktype (er komt een melding). Indien NietVerplichtMaarWelToegestaan (defaultwaarde) mag dat wel, maar hoeft niet. Indien LegesVerplicht zal dit worden gecontroleerd bij het afsluiten van de zaak. De zaak kan niet worden afgesloten (althans niet via de normale weg met wizard sluitzaak) indien er geen legesregel is opgenomen bij de zaak.
    - **Zaaktype exclusief voor compartiment** (dl055). Wordt gebruikt bij  [Verwerking DSO STAM berichten](/docs/applicatiebeheer/probleemoplossing/programmablokken/verwerking_dso_stam_berichten) om een onbekende locatie te koppelen aan een ingestelde defaultwaarde
  - **Blok categorie**
    - **Soort Procedure** (dvsoortproc). De gekozen soort is bepalend voor welke informatie (welke blokken) zichtbaar zijn in het detailscherm van de omgevingszaak bij dit type (zie kopje *zichtbaarheid blokken* in [Detailscherm Omgevingszaak](/docs/applicatiebeheer/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken) ).
    - **Omschrijving zaak bij publiceren** (dvipmoms). Wordt niet door de interne programmatuur van OpenWave gebruikt en ook niet bij DROP-publicaties.
    - **Procedurenaam in OLO bericht** (dvlvotag). Er mag:
      -  precies één zaaktype zijn waarbij deze kolom de waarde *ReguliereProcedureReguliere procedure* heeft. De OLO-berichten waarbij de tag <aanvraagprocedure> gevuld is met *Reguliere procedure* worden aan dit zaaktype gekoppeld. Alleen Waterwetvergunningsaanvragen met deze aanvraagprocedure kunnen toch met aparte instelling aan een afwijkend zaaktype worden gekoppeld. Zie ook [Verwerking van StUF OLO/AIM berichten](/docs/applicatiebeheer/probleemoplossing/programmablokken/olo_verwerking)
      - precies één zaaktype zijn waarbij deze kolom de waarde *UitgereideProcedureUitgebreide procedure* heeft. De OLO-berichten waarbij de tag <aanvraagprocedure> gevuld is met *Uitgebreide procedure* worden aan dit zaaktype gekoppeld. Alleen Waterwetvergunningsaanvragen met deze aanvraagprocedure kunnen toch met aparte instelling aan een afwijkend zaaktype worden gekoppeld.
    - **Documentverwijzing zichtbaar bij gekopieerde zaak** (dldocvangekopieerdezaak). Indien aangevinkt en de tbomgvergunning.dnkeygekopeerdezaak is gevuld (hetgeen betekent dat de zaak is aangemaakt als kopie vanuit een processtap) dan wordt een tegel zichtbaar op het omgevingportaal die toegang geeft tot de lijst van geregistreerde documenten van de oorspronkelijke zaak.
    - **Activiteitsverwijzing zichtbaar bij gekopieerde zaak** (dlactvangekopieerdezaak). Indien aangevinkt en de tbomgvergunning.dnkeygekopeerdezaak is gevuld (hetgeen betekent dat de zaak is aangemaakt als kopie vanuit een processtap) dan wordt een tegel zichtbaar op het omgevingportaal die toegang geeft tot de lijst van activiteiten van de oorspronkelijke zaak.
    - **Bestuurlijke maatrgelen zichtbaar** (dlbestmaatreg). Indien aangevinkt dan is de tegel bestuurlijke maatregelen zichtbaar op het zaakportaal bij dit zaaktype.
    - **Invorderingen zichtbaar** (dlinvordering). Indien aangevinkt dan zijn de tegels opoenstaande en afgehandelde invorderingen  zichtbaar op het zaakportaal bij dit zaaktype.
  - **Blok type DSO**
    - **verzoektype DSO** (dvdsotype). De DSO verzoekberichten met doel initiëren van het overeenkomstige type worden aan dit zaaktype gekoppeld. De waarde in combinatie met het aanvinkvakje *is zaaktype vooroverleg dso* met uniek zijn. Zie kopjes *Doel* en *Zaaktype* bij  [Verwerking DSO STAM berichten](/docs/applicatiebeheer/probleemoplossing/programmablokken/verwerking_dso_stam_berichten).
    - **Ontvangstmail initieel (tbemailsjabloon.dnkey)**. Vrij invoerveld voor id van mailsjabloon (tbemailsjabloon.dnkey) die als basis geldt voor de ontvangstbevestigingsmail op DSO STAM-berichten met als doel *Initieel*. Zie voor volledige functionaliteit beschrijving: [DSO Ontvangstbevestiging sturen](/docs/applicatiebeheer/probleemoplossing/programmablokken/dso_ontvangstbevestiging).
    - **Ontvangstmail aanvulling (tbemailsjabloon.dnkey)**. Vrij invoerveld voor id van mailsjabloon (tbemailsjabloon.dnkey) die als basis geldt voor de ontvangstbevestigingsmail op DSO STAM-berichten met als doel *Aanvullen*. Zie voor volledige functionaliteit beschrijving: [DSO Ontvangstbevestiging sturen](/docs/applicatiebeheer/probleemoplossing/programmablokken/dso_ontvangstbevestiging).
    - **Is zaaktype vooroverleg dso** (dlisdsovooroverleg). Zie hierboven. Indien aangevinkt worden DSO-verzoekberichten met doel vooroverleg en overeenkomstige type aan dit zaaktype gekoppeld.
    - **Is zaaktype actieverzoek SamenwerkingsFunctionaliteit** (dlswfactieverzoek). Indien aangevinkt dan worden nieuwe binnenkomende open actieverzoeken, waarvoor een nieuwe zaak moet worden aangemaakt, onder dit zaaktype met een nieuwe samenwerkingsruimte geplaatst. Er mag maar één (niet vervallen) zaaktype zijn dat deze waarde aangevinkt heeft staan. Zie [Samenwerkingsfunctionaliteit](/docs/applicatiebeheer/instellen_inrichten/samenwerkingsfunctionaliteit).
  - **Blok Actoren**
    - **Default dossierbehandelaar** (dvcodedefbehandelaar). Zie voor de werking onder kopje *actoren en actieve behandelaar* bij [Aanmaken van nieuwe zaak](/docs/applicatiebeheer/probleemoplossing/programmablokken/maak_nieuwe_zaak).
    - **Dossierbehandelaar verplicht** (dlbehandelaarverpl). Wordt niet door de interne programmatuur van OpenWave gebruikt.
    - **Verplichte adressoort (rol)** (dvadressoortverpl). Zie kopje *Adresrollen en (hoofd) Zaaktypes* bij [Adresrollen](/docs/applicatiebeheer/instellen_inrichten/adresrollen).
    - **Default zaakverantwoordelijk team** (dnkeyteamsdefverantw). Zie voor de werking onder kopje *actoren en zaakverantwoordelijk team* bij [Aanmaken van nieuwe zaak](/docs/applicatiebeheer/probleemoplossing/programmablokken/maak_nieuwe_zaak).
  - **Blok Masker** (compartiment kan eigen masker hebben)
    - **Masker Vast gedeelte zaakcode** (dvmasker). OpenWave genereert bij elke nieuwe zaak een eigen codering: de OpenWave zaakcode. Bij omgevingszaken is dit de kolom tbomgvergunning.dvzaakcode. Deze wave zaakcode begint met dit vaste gedeelte en daaraan  wordt een teller vastgeplakt. <wrap important>**LET OP:** voor compartimentszaken wordt het masker en lengte gepakt zoals opgegeven bij het compartimentsdetailscherm voor de zaaktype-lijsten. Indien deze niet gevuld zijn dan valt het programma voor compartimentszaken terug op masker en lengte gedefinieerd bij de oorspronkelijke definitie van het zaaktype.<wrap>
    - **Lengte variabel gedeelte** (dnlenophoger). Zie hierboven. Het gaat hier om het aantal posities van de teller inclusief voorloopnullen. Indien Masker = 2021OW en teller = 4 dan zal een nieuwe zaak bij dit zaaktype een wavecode krijgen van 2021OW0001 en de volgende 2021OW0002.
    - **Icoon** (dnicoon). Wordt gebruikt in het lijstscherm *Alle zaken* onder kolom module op het openingsportaal.
  - **Blok Periodes**
    - **Fatale Default beh. periode** (dnfataleperiode). Dit aantal dagen wordt bij de startdatum van de zaak onder dit zaaktype opgeteld om de kolom ddfataledatum te berekenen. De gebruiker kan in het detailscherm van de zaak deze defaultperiode aanpassen met een keuze uit de tabel tbfataletermijnen (zie blokje *Zaaktype en fatale termijnen* onderaan deze pagina). Die fatale datum wordt door nog meer factoren beïnvloed. Zie kopje *berekening fatale datum* bij [Detailscherm Omgevingszaak](/docs/applicatiebeheer/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken).
    - **Fatale termijn waarschuwingsperiode (oranje balletje)** (dnfatwaarschuwper). Wordt gebruikt in de lijst *(mijn) openstaande omgevingzaken*. Zie kopje *betekenis kleurballetjes* bij [Lijst Mijn Openstaande omgevingszaken](/docs/applicatiebeheer/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_openstaande_omgevingszaken/lijst_mijn_openstaande_omgevingszaken).
    - **Adviezen waarschuwingsperiode (oranje balletje)** (dnadvwaarschuwper). Zie hierboven.
    - **Processtap waarschuwingsperiode (oranje balletje)** (dnprcwaarschuwper). Zie hierboven.
    - **Aantal dagen berek. publ.datum** (dnpublaanvrgper). Alleen indien de hier ingevulde waarde groter dan 0 is, zal bij het aanmaken van een nieuwe zaak onder dit type de kolom tbomgvergunning.ddpublaanvraag worden gevuld met de aanvraagdatum + deze waarde. <wrap important>**LET OP:** deze kolom heeft **niets** te maken met publiceren onder DROP.<wrap>
    - **Verlengen/Opschorten via tabel** (dltabelopschorten). Indien aangevinkt dan wordt in het detailscherm van de omgevingszaak het blok met de tbopschorten-tabel zichtbaar, waarin herhaalbaar regels kunnen worden opgenomen die van invloed zijn op de fatale termijn. Zie [Opschorten/Verlengen](/docs/applicatiebeheer/probleemoplossing/module_overstijgende_schermen/opschorten_verlengen).
    - **Verlengen/Opschorten via blokken in detail** (dlblokkenopschort). Indien aangevinkt dan worden de blokken *Verlenging;Wabo art. 3.9;lid 2* *(42dgn)* en *Verlenging* en *Opschorting;Awb art. 4.15 m.u.v. lid 1a* zichtbaar in het detailscherm van de omgevingszaak. Deze blokken zijn van invloed op de berekening van de fatale datum.
  - **Blok extern zaak/dms systeem**
    - **Extern Zaak/DMS systeem koppelen** (dlnaardms). Indien aangevinkt kunnen zaken die onder dit zaaktype zijn aangemaakt via een StUF zaak/DMS creerzaakbericht aangemaakt worden in het externe zaaksysteem. Of dat al of niet automatisch gebeurt is afhankelijk van andere instellingen. Zie o.a. [Creëer zaak zaak/DMS](/docs/applicatiebeheer/probleemoplossing/programmablokken/creeer_zaak_zaak_dms).
    - **Zaaktype code** (dvdmszaaktypecode). Onder deze externe zaaktypecodering wordt een StUF zaak/DMS creeerzaakbericht bij een zaak onder dit zaaktype verzonden. Omgekeerd, als een StUF Zaak ZakLk01 bericht bij OpenWave naar binnen wordt geschoten, wordt op grond van deze externe zaaktypecodering een zaak aangemaakt onder dit type. Zie:[Verwerking zakLk01 en zakLk02 berichten](/docs/applicatiebeheer/probleemoplossing/programmablokken/stuf_zaken_zaklk01_02-verwerking).
    - **Zaaktype omschrijving** (dvdmszaaktypecode). Kan als omschrijving van de zaak meekomen met StUF zaak/DMS creeerzaakbericht tenzij de instelling *Sectie: Koppeling Zaak en Item: AanvraagNaamipvZaaktypeoms* is aangevinkt (of bij een compartiment -indien de tbcompartiment.dlaanvrgnmipvzaaktype de waarde T heeft) dan wordt de zaakomschrijving (dvaanvraagnaam) van de omgevingszaak zelf doorgegeven.
  - **Blok CBS**
    - **CBS-bedrag (W011)** (dfcbsbedrag). Wordt vanaf versie 1.28 niet meer naar gekeken. Diende voorheen als leidraad om te bepalen of er voor de vergunning toch een W011 formulier moest worden opgesteld ondanks dat de  opgetelde vastgestelde of herziene bouwkosten per cbs11-activiteit van de vergunning niet boven de 50000 waren. De huidige voorwaarden voor W011 formulier opstellen staan beschreven onder kopje *CBS bij triggers linksonder in scherm* bij [Detailscherm Omgevingszaak](/docs/applicatiebeheer/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken).
    - **W011 ?** (dlw011). Geeft aan of de gegevens van de vergunningen van dit zaaktype mogelijk naar CBS verstuurd moeten worden. Voor de volledige afweging bepalend voor gegevens klaarzetten voor CBS zie kopje *CBS bij triggers linksonder in scherm* bij [Detailscherm Omgevingszaak](/docs/applicatiebeheer/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving/detailscherm_omgevingszaken).
  - **Blok TMLO**
    - **TMLO Classificatie code** (dvtmlocodeclass). Wordt gebruikt bij export zaken naar E-Depot.
    - **TMLO Classificatie omschrijving** (dvtmloomsclass). Wordt gebruikt bij export zaken naar E-Depot.

## Zaaktype en koppeling met documenttypes

In de koppeltabel TbZaaktypeDoctype wordt geregeld welke documenttypes (beheerportaal-Nieuw, tegel *Documenttypes* (tbdocumenttype)) bij het zaaktype van toepassing zijn. Dat wil zeggen dat op het moment dat de gebruiker gevraagd wordt een documenttype te kiezen (bij export document naar extern zaak/DMS of bij opslag naar geregistreerde documenten) dan zal OpenWave laten kiezen uit de hier gedefinieerde subset op grond van het zaaktype van de bovenliggende zaak.
Is de koppeltabel leeg voor het betrokken zaaktype dan zal de gebruiker uit de volledige tabel tbdocumenttype moeten kiezen.

## Zaaktype en gekoppelde processen

In de koppeltabel TbProceduresSoortplan wordt geregeld welke processen (beheertegel *Processen* (tbprocedures)) bij het zaaktype van toepassing zijn. Dat wil zeggen dat op het moment dat de gebruiker gevraagd wordt een proces te kiezen dan zal OpenWave laten kiezen uit de hier gedefinieerde subset op grond van het zaaktype van de bovenliggende zaak.
Is de koppeltabel leeg voor het betrokken zaaktype dan zal de gebruiker uit de volledige tabel tbprocedures moeten kiezen (in zoverre module en compartiment overeenkomstig zijn).

Indien in de koppeltabel het vakje *automatisch*  is aangevinkt, heeft dat tot gevolg dat bij het aanmaken van een nieuwe zaak onder het betreffende zaaktype het proces al automatisch wordt toegevoegd.

Als bij een bepaald zaaktype voor de host een gekoppeld (al of niet automatisch toe te voegen) proces is gedefinieerd, en datzelfde zaaktype wordt ook gebruikt bij een compartiment, waarbij voor dat compartiment ook geldt dat een gekoppeld proces is gedefinieerd, dan zijn er in dat geval twee gekoppelde processen. OpenWave negeert vanzelf bij de proceskeuze die van het compartiment als de betreffende zaak niet speelt in dat compartiment. En omgekeerd.

## Zaaktype en gekoppelde resultaten/aardbesluit

In de koppeltabel TbAardbesluitSoortZaak wordt geregeld welke resultaten portaal *Zaakbeheer*, tegel *Afhandeling/Besluit
omg/apv/bouw/milieu/gebruik* (tbaardbesluit) bij het zaaktype van toepassing zijn. Dat wil zeggen dat op het moment dat de gebruiker een zaak afsluit (met de wizard achter de afhandeldatum), OpenWave laat kiezen uit de hier gedefinieerde subset op grond van het zaaktype van de bovenliggende zaak.
Is de koppeltabel leeg is voor het betrokken zaaktype dan zal de gebruiker uit de volledige tabel tbaardbesluit moeten kiezen (in zoverre module en compartiment overeenkomstig zijn).

De koppeltabel wordt ook gebruikt voor de bewaartermijnen met betrekking tot vernietiging van zaken en documenten. Zie uitleg bij lemma: [Vernietigingslijst](/docs/applicatiebeheer/probleemoplossing/programmablokken/vernietigingslijst).

Bij omgevingszaken kan ook de koppeltabel TbOmgBewaarResultToets (een tabel tussen TbAardbesluitSoortZaak en Tbsrttoestemming) een rol spelen bij de bewaartermijnen voor het zaaktype.

## Zaaktype en koppeling met documentsoorten

In de koppeltabel TbZaaktypeDocumentsoorten wordt geregeld welke documentsoorten (beheertegel *Documentsoorten* (tbdocumentsoorten)) bij het zaaktype van toepassing zijn. Documentsjablonen zijn ingedeeld in documentsoorten. Wanneer een gebruiker een document wil creëren op basis van een sjabloon zal hij/zij eerst een keuze moeten maken uit de hier gekoppelde documentsoorten.

Is de koppeltabel leeg voor het betrokken zaaktype dan zal de gebruiker uit de volledige tabel tbdocumentsoorten moeten kiezen.

## Zaaktype en koppeling met producten/diensten

In de koppeltabel TbProducten wordt geregeld welke Product definities (beheertegel *Productdefinities* (tbproductdef)) bij het zaaktype van toepassing zijn. Zie kopje *Definitie producten/klanten/werkpakketten* bij [Producten Klanten en Werkpakketten](/docs/applicatiebeheer/instellen_inrichten/producten_klanten_werkpakketten).

## Zaaktype en DROP

In de koppeltabel TbKopPublGemZaak wordt geregeld welke gemeentes voor welke bladen op welke momenten bij het betreffende zaaktype een DROP-publicatie moeten aanmaken. Zie: [Drop](/docs/applicatiebeheer/instellen_inrichten/drop).

## Zaaktype en koppeling met legessoorten

In de koppeltabel tbkopzaaktypelegessoort kunnen legessoorten uit de tabel tblegessoorten worden gekoppeld aan het zaaktype.
Indien er GEEN legessoorten aan een zaaktype zijn gekoppeld, dan kan de gebruiker aan de voorkant bij het opvoeren van een legesregel bij een zaak van dat betreffende zaaktype, kiezen uit alle (niet vervallen) legessoorten bij de betreffende module.
Indien hier WEL legessoorten zijn gekoppeld aan een zaaktype, dan kan die gebruiker aan de voorkant alleen kiezen uit de legessoorten die bij het betreffende zaaktype zijn gedefinieerd.

<wrap important>**LET OP:** op zaaktype-niveau kan ingesteld zijn dat bij dat type GEEN legesregels opgenomen mogen worden. Dat gaat in beide gevallen voor.<wrap>

## Zaaktype en fatale termijnen

In de tabel tbfataletermijnen kunnen mogelijke behandelingstermijnen bij het zaaktype opgegeven worden. De behandelingstermijn bij bijvoorbeeld zaaktype melding (zoals door DSO naar binnen wordt geschoten) is echt afhankelijk van de inhoud. Vandaar.

Op zaaktypeniveau blijft de default behandelingstermijn bestaan (kolom dnfataleperiode). Deze default wordt gebruikt bij het handmatig toevoegen van een zaak, of indien een zaak via DSO of OLO wordt aangemaakt.

De gebruiker kan aan de voorkant in de kolom berekeningswijze fatale termijn (blok afhandeling op detailpagina van de zaak) de default fatale periode aanpassen met een keuze uit de hier gedefinieerde behandelingstermijnen bij het zaaktype.
