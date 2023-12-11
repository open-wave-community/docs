Detailscherm Inspectietrajecten
===============================

Schermidentifier
----------------

MDDC_geefInspTrajectDetail.xml

Kan worden aangeroepen vanuit de Lijst Inspectietrajecten bij een Zaak
of Inrichting.

Error
~~~~~

Het scherm geeft een foutmelding, indien:

-  er mogelijk een zelf gedefinieerde schermindeling gebruikt is die
   niet valide is
-  de inlogger geen kijkrechten heeft op de inspecties bij betreffende
   hoofdzaak (bijvoorbeeld Zichtbaar-rechten op inspecties bij
   omgeving).

Automatisch aanmaken inspectietraject en Compartiment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien voor een
`compartiment </docs/instellen_inrichten/compartimenten.md>`__ is
ingesteld (beheerportaal-Nieuw tegel *Compartimenten*) dat het
compartiment een bepaald zaaktype behandelt, kan daarbij ook worden
aangegeven of dit inclusief of exclusief de deelzaken inspecties en
bezwaar/beroep is. Dat betekent dat een compartiment bijvoorbeeld een
reguliere bouwzaak afhandelt, maar dat de inspectie daarop door de
OpenWave gastheer wordt afgehandeld waarbinnen het compartiment valt.

Als bij de definitie van het zaaktype in het compartiment is opgegeven:

-  exclusief inspectie
-  en een inspecteur is aangewezen uit de lijst met medewerkers van de
   gastheer
-  en een aanleiding inspectie is opgegeven

dan zal bij het afsluiten van een zaak door het compartiment dat valt
onder het bewuste zaaktype, automatisch een inspectietraject aangemaakt
worden op naam van de opgegeven inspecteur.

Zichtbaarheid blokken
~~~~~~~~~~~~~~~~~~~~~

-  Het blok **Keten** is alleen zichtbaar indien de instelling *Sectie:
   KOPPELING ZAAK en Item: ZaaktypeInspectietraject* is aangevinkt en de
   moduleletter van de bovenliggende zaak (dus W of H, O, C of V) komt
   **NIET** voor in de kolom *Info* van die instelling. *NB Als het blok
   overal zichtbaar moet zijn, vult u bv een X is!*
-  Het blok **Digitale checklisten** is alleen zichtbaar indien de
   instelling *Sectie: koppelinginsptoets en Item: methode* is
   aangevinkt en de kolom *Tekst* de waarde *digitalechecklisten* heeft.
-  Het **blok TMLO** is alleen zichtbaar indien de kolom **Is
   Hoofdzaak** (tbinspaanleiding.dlhoofdzaak) aangevinkt is voor de
   betreffende aanleiding (beheerportaal *Zaakbeheer*, kolom *Handhaving
   en Toezicht*, tegel *Inspectietrajectsoorten*). De kolom
   bewaartermijnindagen geeft de ingestelde waarde weer uit de tabel
   tbaardbesluitsoortinsp (de koppeltabel tussen tbinspaanleiding en
   tbaardbesluit op het detailscherm van de inspectietrajectsoorten).

De kolom **vernietigingsjaar** i.v.m.
`Vernietigingslijst </docs/probleemoplossing/programmablokken/vernietigingslijst.md>`__
wordt als volgt berekend: Indien \_eeuwig bewaren is aangevinkt dan:
leeg \_ anders, indien de bewaartermijn uit tbaardbesluitsoortinsp is
gemeten vanaf startdatum (tbinspecties.ddrappel): \_indien afwijkende
bewaartermijn gevuld dan ddrappel + afwijkende termijn \_ anders, dan
ddrappel + bewaartermijn uit tbaardbesluitsoortinsp \_anders, indien de
bewaartermijn uit tbaardbesluitsoortinsp is gemeten vanaf einddatum
(ddcontrole): \_ indien afwijkende bewaartermijn gevuld dan ddcontrole +
afwijkende termijn \* anders, dan ddcontrole + bewaartermijn uit
tbaardbesluitsoortinsp.

-  Het blok **Producten/Diensten** is alleen zichtbaar indien de
   instelling *Sectie: Product/Dienst en Item: Inspecties* is
   aangevinkt. De lijst in het blok is zichtbaar indien de inlogger het
   kijkrecht op inspecties bij omgevingzaken heeft
   (tbomgrechten.dlcomginsvsb) dus ook indien de inspectiekaart aan
   bijv. een handhavingzaak is gekoppeld. De inlogger kan hier een of
   meer producten opvoeren bij de het inspectietraject op grond van de
   toegekende producten aan de betreffende inspectie-aanleiding (zie
   blok *gekoppeld aan producten* in detailscherm achter *portaal
   Zaakbeheer, kolom Handhaving & toezicht, tegel Soorten
   inspectietrajectsoorten (tbinspaanleiding)*. Zie werking `Producten
   Klanten en
   Werkpakketten </docs/instellen_inrichten/producten_klanten_werkpakketten.md>`__

Muteren
~~~~~~~

De kolommen kunnen gemuteerd worden indien:

-  de inlogger wijzigrechten heeft op de inspecties bij betreffende
   hoofdzaak/inrichting (bijvoorbeeld wijzigrechten op inspecties bij
   omgeving)
-  en die bovenliggende hoofdzaak niet is geblokkeerd
-  en de blokkeer/einddatum (dddmsafgehandeld) in blok *Keten* leeg is
-  en de editschuif aan staat
-  en - indien de inlogger lid is van een compartiment - dan moet het
   betreffende compartiment het zaaktype van de hoofdzaak bevatten en de
   gemeente waar de hoofdzaak speelt en dan moet de eigenschap
   *inclusief inspecties* bij dat zaaktype in het compartiment zijn
   aangevinkt
-  en - indien de inlogger GEEN lid is van een compartiment, dan mag de
   combinatie van het zaaktype van de hoofdzaak en de gemeente waar de
   hoofdzaak speelt in geen enkel compartiment voorkomen tenzij de
   eigenschap *inclusief inspecties* bij dat zaaktype in het
   compartiment NIET is aangevinkt. \|

Een voorbeeld met betrekking tot compartimentsrechten: stel de
inspectiedeelzaak hoort bij een omgevingszaak. Dan geldt:

-  dat vwfrmomgvergunningen.dnkeycompartiment (van de betreffende
   omgevingszaak) gevuld moet zijn en gelijk moet zijn aan
   tbmedewerkers.dnkeycompartiment (van de inlogger) en dat
   vwfrmomgvergunningen.dlinclinspecties de waarde 'T' moet hebben
-  OF dat tbmedewerkers.dnkeycompartiment (van de inlogger) leeg is en
   vwfrmomgvergunningen.dnkeycompartiment (van de betreffende
   omgevingszaak) is ook leeg
-  OF dat tbmedewerkers.dnkeycompartiment (van de inlogger) leeg is en
   vwfrmomgvergunningen.dnkeycompartiment (van de betreffende
   omgevingszaak) is gevuld, maar dat
   vwfrmomgvergunningen.dlinclinspecties de waarde 'F' heeft.

Uitzondering blokkering: als de bovenliggende hoofdzaak is geblokkeerd
kan er toch gemuteerd worden indien de instelling *Sectie:
InspectieMilieu* en *Item: NietBlokkerenMetHoofdzaak* aangevinkt is (als
de blokkeer/einddatum (dddmsafgehandeld) in blok *Keten* gevuld is, dan
is de inspectiezaak uiteindelijk toch geblokkeerd).

De **dropdownlist van de (hoofd)inspecteur** kijkt naar de kolom *Tekst*
van de instelling *Sectie: InspectieMilieu* en *Item: Rechtengroepen*.
Daar kunnen - gescheiden door puntkomma's' - de dnkeys van de
rechtengroepen (tbrechten) opgesomd worden die bedoeld zijn voor de
inspecteurs. Bijvoorbeeld 1.13;210;340;

Is dit het geval dan laat de dropdownlijst alleen medewerkers zien die
lid zijn van deze functionele rechtengroepen. Is de instelling leeg dan
bestaan er geen restricties op functionele rechtengroepen.

In alle gevallen geldt verder het volgende:

-  de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die
   van de inlogger
-  en de medewerker moet in dienst zijn
-  en het vakje *interne medewerker* moet aangevinkt zijn.
-  en het vakje *is raadpleger* moet NIET aan gevinkt zijn

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf
de eigenschap: *overrule compartiment* aangevinkt heeft staan -, alle
overige medewerkers met deze eigenschap.

De **dropdownlijst van onderwerp** kijkt eerst of er gekoppelde
inspectie onderwerpen hangen aan de aanleiding van het inspectietraject
waar het bezoek onder valt. Zo ja dan is er alleen te kiezen uit de in
beheer aangegeven inspectie onderwerpen voor de inspectietrajectsoort.
Is dit niet het geval dan worden alle inspectie onderwerpen getoond uit
de codetabel in beheer zonder vervaldatum en met module corresponderend
met de module van de zaak waaronder het inspectiebezoek hangt.

Kolom Resultaat
~~~~~~~~~~~~~~~

Er zijn twee resultaatkolommen waarvan er altijd maar eentje zichtbaar
is. Indien de kolom *Getal1* van instelling *Sectie: Inspecties en Item:
ResultaatVerplichtBijAfsluiten* **NIET** de waarde 1 heeft dan is de
combinatie van de kolommen vwfrminspecties.dnkeyinspresultaat en
dvresultaatoms zichtbaar. Het resultaat komt dan uit de tabel
tbinspresultaat.

Indien deze *Getal 1* van deze instelling **WEL** de waarde 1 heeft dan
zijn de kolommen vwfrminspecties.dnkeyaardbesluitsoortinsp en
dvaardbesluit zichtbaar. Het resultaat komt in dit geval uit de tabel
tbaardbesluit via de koppeltabel tbaardbesluitsoortinsp (koppeling op
tbinspaanleiding en tbaardbesluit). In de koppeltabel
tbaardbesluitsoortinsp op het detailscherm van een inspectietrajectsoort
(dus uit tbinspaanleiding: beheerportaal *Zaakbeheer*, kolom *Handhaving
en toezicht*, tegel *Inspectietrajectsoorten*) kunnen items uit
tbaardbesluit worden gekoppeld aan een rij van tbinspaanleiding.

Aan de voorkant bepaalt dus de keuze voor de aanleiding inspectie wat de
mogelijkheden zijn voor het resultaat. In de koppeltabel
tbaardbesluitsoortinsp worden ook de bewaartermijndagen opgegeven die
gebruikt worden bij de
`Vernietigingslijst </docs/probleemoplossing/programmablokken/vernietigingslijst.md>`__.

Koppeling Digitale checklisten
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Het blok met de koppeling naar Digitale checklisten is nu alleen
zichtbaar indien die koppeling aangevinkt staat (*Sectie:
koppelingInsptoets* en *Item: Methode* en *Tekst =
Digitalechecklisten*).

Indien de instelling *Sectie: KoppelingINSPTOETS* en *Item:
AantalLijstenPerTraject* bestaat en de waarde van kolom *Getal1* = 1 of
2, dan worden van de regels met digitale checklistitems in plaats van
drie alleen 1 of 2 regels getoond.

Indien de instelling *Sectie: KoppelingINSPTOETS* en *Item:
ExterneKeyWijzigbaar* aangevinkt is dan zijn de digitale
checklistkolommen muteerbaar, anders niet.

Externe zaak/DMS nummer en StUF zaak/DMS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Daarmee wordt bedoeld de kolom externe zaak/dms (dvintzaakcode) die voor
kan komen op de inspectietrajectkaart zelf en/of bij de bovenliggende
hoofdzaak/inrichting.

Het programma kijkt naar de inspectiekaart zelf indien deze is
gedefinieerd als zelfstandige zaak in het externe zaaksysteem. Dit is
het geval wanneer de moduleletter (W = Omgeving, H = Handhaving, O =
APV/Overig en V = Inrichtingen, C = Horeca) van de bovenliggende
zaak/inrichting NIET voorkomt in kolom *Info* van de instelling *Sectie:
Koppeling Zaak* en *Item: ZaaktypeInspectietraject*.

In de andere gevallen (moduleletter zit wel in instelling of instelling
bestaat niet) dan komt het externe zaak/DMS nummer uit de
hoofdzaak/inrichting van de betreffende module.

De StUF zaak/DMS koppeling is het geval indien daarbij:

-  wanneer het inspectietraject NIET wordt behandeld in een compartiment

   -  en *Sectie: Documenten* en *Item: OphalenViaDms* aangevinkt is
   -  en de kolom *Tekst* bij instelling *Sectie: KoppelingDocnaardms
      Item: Methode* de waarde StUF-ZAKEN 310 heeft en aangevinkt is

-  wanneer het inspectietraject WEL wordt behandeld in een compartiment

   -  en de kolom dldms in het betreffende compartiment
      (beheerportaal-Nieuw) aangevinkt is
   -  en de kolom tbcompartiment.dvdmsmethode de waarde StUF-ZAKEN 310
      heeft.

Triggers in het scherm zelf
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Sluit inspectietraject af
^^^^^^^^^^^^^^^^^^^^^^^^^

Achter de kolom afgerond. Zie `Sluiten en Nieuw aanmaken
Inspectietraject </docs/probleemoplossing/programmablokken/afsluiten_inspectietraject.md>`__

-  Altijd zichtbaar
-  enabled indien:

   -  de inlogger muteerrechten heeft op de inspecties
   -  en de bovenliggende zaak niet is geblokkeerd (zie hierboven de
      uitzondering)
   -  en dus ook de eindedatum in het blok *Keten* (dddmsafgehandeld) is
      leeg
   -  en indien het inspectietraject een zelfstandige zaak is in externe
      zaaksysteem (onder StUF zaak/DMS)

      -  dan moet het externe zaak/DMS nummer (dvintzaakcode gevuld) van
         de inspectiekaart zelf gevuld zijn
      -  en resultaat van de inspectie moet gevuld zijn (indien *Getal1*
         van de instelling *Sectie: Inspecties en Item:
         ResultaatVerplichtBijAfsluiten* de waarde 1 heeft dan via
         koppelingstabel tbaardbesluitsoortinsp en anders via
         tbinspresultaat).

Maak zaak in zaak/DMS systeem
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Achter externe zaak/dms nummer.

-  Zichtbaar en enabled indien:

   -  de inlogger muteerrechten heeft op de inspecties
   -  en de afgehandeld datum (ddcontrole) nog leeg is
   -  en indien het inspectietraject een zelfstandige zaak is in externe
      zaaksysteem (onder StUF zaak/DMS)
   -  en externe zaak/dms nummer (dvintzaakcode) van de inspectiekaart
      zelf een lege waarde heeft
   -  en de bovenliggende zaak niet is geblokkeerd (zie hierboven de
      uitzondering)
   -  en de inlogger is lid van rechtengroep die het recht wijzigen
      externe zaaknummers bij betreffende module/inrichting aangevinkt
      heeft staan (bijvoorbeeld dlcomginspdms)
   -  en *Getal1* van de instelling *Sectie: Koppeling Zaak* en *Item:
      Zender_Organisatie* is gevuld met een dnkey die verwijst naar een
      bestaand contactadres in tbcontactadressen namelijk (die van de
      zendende organisatie zelf).

Sluit/heropen zaak in zaak/DMS systeem
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Achter einddatum/blokkeerdatum van zaak/DMS nummer in het blok *Keten*.

-  Zichtbaar en enabled indien:

   -  de inlogger muteerrechten heeft op de inspecties
   -  en externe zaak/dms nummer (dvintzaakcode) een **gevulde** waarde
      heeft
   -  en de bovenliggende zaak niet is geblokkeerd
   -  en - indien de inspectiezaak NIET onder een compartiment valt - de
      instelling *Sectie: Koppeling Zaak* en *Item: Methode* en *Tekst:
      StUF-ZAKEN 310* staat aangevinkt
   -  en - indien de inspectiezaak WEL onder een compartiment valt - dan
      moet de kolom *dmsmethode* van het betreffende compartiment in het
      beheer gevuld zijn met *StUF-Zaken 310*
   -  en de inlogger is lid van rechtengroep die het recht wijzigen
      externe zaaknummers bij betreffende module/inrichting aangevinkt
      heeft staan (bijvoorbeeld dlcomginspdms)
   -  de inlogger is lid van rechtengroep die het recht *wijzigen (dms)
      afgehandelddatum* bij betreffende module/inrichting aangevinkt
      heeft staan (bijv. tbmilrechten.dlbmilinrafedt)
   -  en de inspectie een zelfstandige zaak is in externe zaaksysteem:
      De module-letter komt NIET voor in de kolom *Info* van de
      instelling *Sectie: Koppeling Zaak Item: ZaaktypeInspectietraject*
      (maar de instelling bestaat wel)
   -  en het resultaat zoals dat doorgegeven moet worden aan het
      zaak/DMS gevuld is. Indien *Getal1* van de instelling *Sectie:
      Inspecties en Item: ResultaatVerplichtBijAfsluiten* de waarde 1
      heeft dan op basis van tbaardbesluit via de koppelingstabel
      tbaardbesluitsoortinsp (op basis van de inspectie aanleiding) en
      anders via tbinspresultaat: zie beheertegel *Inspectie resultaat*.

.. _maak-nieuw-dossier-in-dig-checklist:

Maak nieuw dossier in dig. checklist
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Vinkje met plusje achter dig. checklist indien ID leeg is.

-  Zichtbaar en enabled indien:

   -  compartiment ok
   -  dig. checklist id leeg is
   -  en de instelling *Sectie: KoppelingINSPTOETS* en *Item: Methode*
      en *Tekst: digitalechecklisten* aangevinkt is
   -  en de kolom *Tekst* bij *Sectie: KoppelingINSPTOETS* en *Item:
      Ontvangstadres_checklists* is gevuld.

-  Niet enabled indien instelling *Sectie: KOPPELINGINSPToets en Item:
   DMSzaakcodeverplicht* aangevinkt is en de kolom externe zaak/dms
   (tbinspecties. dvintzaakcode) leeg is.

.. _open-dossier-in-dig-checklist:

Open dossier in dig. checklist
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Vinkje achter dig. checklist indien ID gevuld is.

-  Zichtbaar en enabled indien:

   -  compartiment ok
   -  dig. checklist id gevuld is
   -  en de instelling *Sectie: KoppelingINSPTOETS* en *Item: Methode*
      en *Tekst: digitalechecklisten* aangevinkt is
   -  en de kolom *Tekst* bij *Sectie: KoppelingINSPTOETS* en *Item:
      Navigeeradres* is gevuld.

.. _toon-opmerkingen-uit-dig-checklist:

Toon opmerkingen uit dig. checklist
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Memo-icoontje achter dig. checklist indien ID gevuld is.

-  Zichtbaar en enabled indien:

   -  dig. checklist id gevuld is
   -  en de instelling *Sectie: KoppelingINSPTOETS* en *Item: Methode*
      en *Tekst: digitalechecklisten* aangevinkt is en
   -  de kolom *Tekst* bij *Sectie: KoppelingINSPTOETS* en *Item:
      Ontvangstadres_answers* is gevuld.

.. _upload-reportpdf-uit-dig-checklist:

Upload report.pdf uit dig. checklist
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Pdf-icoontje achter dig. checklist indien ID gevuld is.

-  Zichtbaar en enabled indien:

   -  dig. checklist id gevuld is
   -  en de instelling *Sectie: KoppelingINSPTOETS* en *Item: Methode*
      en *Tekst: digitalechecklisten* aangevinkt is
   -  en (compartiments-)rechten ok
   -  en de instelling *Sectie: KoppelingINSPTOETS* en *Item:
      downloadPdf* aangevinkt is
   -  en - indien *Getal1* van deze instelling *Sectie:
      KoppelingINSPTOETS* en *Item: downloadPdf* de waarde 1 heeft - dan
      moet de datum *report is geüpload* (dddcdownloadpdf1 of
      dddcdownloadpdf2 of dddcdownloadpdf3) nog leeg zijn. Dus bij
      waarde 0 kan het rapport meerdere malen worden geüpload.

Verder moet voor de goede werking:

-  De kolom *Tekst* van de instelling *Sectie: KoppelingINSPTOETS en
   Item: Endpoint_PDF* gevuld zijn met de URL van het up te loaden
   report.pdf, waarbij het vraagtekentje door OpenWave – on the fly -
   vervangen zal worden door de betreffende digitale dossiercode
   bijvoorbeeld:
   ``[https://staging.digitalechecklisten.nl/checklists/?/report.pdf](https://staging.digitalechecklisten.nl/checklists/?/report.pdf.md)``
-  en de kolom *Tekst* van *Sectie: KoppelingINSPTOETS en Item:
   VertrouwelijkheidReport.pdf* moet gevuld zijn met een valide
   vertrouwelijkheidduiding (als tekst, dus geen keyverwijzing).
-  en de kolom *Tekst* van *Sectie: KoppelingINSPTOETS en Item:
   DoctypeReport.pdf* moet gevuld zijn met een valide documenttype (als
   tekst, dus geen keyverwijzing).

Het report.pdf uit Digitale checklisten wordt default geüpload onder de
naam: DC + *+ Dossiercode +* + datum(yyymmdd) + *+ tijd(hhmmss) +* +
report.pdf bijvoorbeeld: *DC_191096_20210816_113448_report.pdf*. Na
klikken op de knop verschijnt een wizardscherm met de default
documentnaam. Deze kan indien gewenst aangepast worden. De programmatuur
zal na klikken op *Uitvoeren* altijd controleren dat de naam eindigt op
*.pdf* en indien dit niet het geval is, deze extensie toevoegen.

Triggers rechtsboven in menu Opties
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bezoeken bij dit traject
^^^^^^^^^^^^^^^^^^^^^^^^

-  Altijd zichtbaar en enabled.

Overtredingen bij dit traject
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

-  Altijd zichtbaar en enabled.

Toon geregistreerde documenten bij dit traject
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Zie `Geregistreerde
Documenten </docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten.md>`__.

-  Zichtbaar en enabled indien:

   -  de instelling *Sectie: Documenten Item: Documentregistratie* is
      aangevinkt
   -  en de gebruiker het recht *Inzien geregistreerde documenten* bij
      de betreffende module aangevinkt heeft staat (bijv.
      tbomgrechten.dlcomgcorregvsb).

Creëer document
^^^^^^^^^^^^^^^

-  Zichtbaar indien:

   -  de inlogger lid is van een rechtengroep die bij
      hoofdzaak/inrichting het recht creëren van documenten heeft
   -  en de bovenliggende zaak niet is geblokkeerd (zie hierboven de
      uitzondering)
   -  en Compartiment OK.

-  De knop is disabled indien de bovenliggende zaak/inrichting
   geblokkeerd is (kijk naar uitzondering hierboven).

Maak nieuwe handhavingszaak van dit traject
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

-  Zichtbaar indien:

   -  de inspectiekaart nog niet is gekoppeld aan een handhavingszaak
   -  en de module ongelijk aan Handhavingen is (dus kan alleen vanuit
      Omgeving, APV/Overig of Inrichtingen of Horeca)
   -  en de inlogger lid is van een rechtengroep die insertrechten heeft
      op Handhavingen
   -  en de instelling *Sectie: Programma* en *Item: Handhaving uit
      inspectie genereren* aangevinkt is
   -  en compartiment OK.

-  De knop is disabled indien de bovenliggende zaak/inrichting
   geblokkeerd is (kijk naar uitzondering hierboven).

Door het indrukken van de knop wordt een nieuwe handhavingszaak
aangemaakt (de inlogger moet daarbij kiezen uit soort zaak en soort
overtreding) met overname van inspectietraject/bezoek/overtredingen en
contactpersonen en geregistreerde correspondentie. Daarbij geldt dat:

-  de systeemdatum (dus datum waarop je de handhavingszaak aanmaakt) de
   startdatum wordt van de handhavingszaak
-  de correspondentierecords (de geregistreerde documenten) die
   gekoppeld zijn aan het inspectietraject worden gedupliceerd en
   gekoppeld aan de nieuwe handhavingszaak (alleen de verwijzingen en
   niet het fysieke documenten). Alleen indien *Getal2* van *Sectie:
   Programma* en *Item: Handhaving uit inspectie genereren* NIET de
   waarde 1 heeft, worden deze nieuwe correspondentiekaarten ook
   gekoppeld aan de oude inspectiekaart
-  de nieuw gemaakte handhavingszaak wordt opgenomen in de sidebar en
   het handhavingsportaal de focus krijgt
-  indien *Getal2* van *Sectie: Programma, Item: Handhaving uit
   inspectie genereren <> 1* is en de instelling *Sectie: Koppeling
   Zaak, Item: AutoZaakDmsHandhaving* staat aan, dan moet er een
   DSM-zaakcode worden opgevraagd (dvintzaakcode) voor de nieuw
   gegenereerde handhavingszaak.
-  indien *Getal1* van *Sectie: Programma* en *Item: Handhaving uit
   inspectie genereren* de waarde 1 heeft, dan wordt de default
   behandelaar van de gekozen soort handhavingszaak de actieve
   behandelaar en anders (of de default is niet gevuld) wordt dat de
   inlogger
-  indien *Getal2* van *Sectie: Programma* en *Item: Handhaving uit
   inspectie genereren* de waarde 1 heeft, dan wordt het
   inspectietraject gedupliceerd (met bijbehorende bezoeken en
   overtredingen) naar de handhavingszaak. Anders wordt het
   inspectiekaart NIET gedupliceerd, maar OOK gekoppeld aan de nieuwe
   handhavingszaak. Indien de kolom *Tekst* bij dupliceren (*Getal2* =
   1) een valide ID (dnkey) bevat van tbinspresultaat dan wordt bij
   dupliceren van het inspectietraject het oude bestaande traject
   afgesloten met dat resultaat en met de systeemdatum
-  indien kolom *Info* van de instelling *Sectie: Programma Item:
   Handhaving uit inspectie genereren* de waarde *tbinsponrechtm* heeft,
   dan kan de inlogger t.b.v. de hoofdovertreding waarop de
   handhavingszaak wordt aangemaakt alleen kiezen uit de overtredingen
   die in de tabel tbinsponrechtm zijn opgenomen bij het betreffende
   inspectietraject. Echter indien kolom *Info* de waarde
   *tbinsponrechtm_openstaand* heeft dan kan de inlogger alleen kiezen
   uit de openstaande overtredingen die in de tabel tbinsponrechtm zijn
   opgenomen bij het betreffende inspectietraject. Voor beide gevallen
   geldt dat als die lijst leeg is dan kan rechtstreeks gekozen worden
   uit de items van tabel tbhandhovertreding (beheer)
-  indien de instelling *Sectie: Programma* en *Item: Openstaande
   overtredingen* aangevinkt is, dan zullen alleen de openstaande
   overtredingen overgenomen worden uit het inspectietraject waarbij de
   *Datum opgelost* leeg is of groter dan vandaag.
-  Indien de instelling *Sectie: Programma* en *Item:
   KoppelZaakInrichtingAanHandhaving* aangevinkt is, dan zal bij het
   genereren van een handhavingzaak vanuit een inspectietraject,
   hangende aan een zaak (module W,C,B of O), een gekoppelde inrichting
   opgenomen worden in de nieuwe handhavingzaak.

Toon uploads bij deze inspectie
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

-  Zichtbaar en enabled indien:

   -  de instelling *Sectie: Documenten* en *Item: MultipleUpload*
      aangevinkt is
   -  en de inlogger lid is van een rechtengroep die bij
      hoofdzaak/inrichting het recht uploaden van documenten heeft.

Maak nieuwe handhavingszaak en BOA-advies van dit traject
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

-  Zichtbaar indien:

   -  de inspectiekaart nog niet is gekoppeld aan een handhavingszaak
   -  en de module ongelijk aan Handhavingen is (dus kan alleen vanuit
      Omgeving, APV/Overig of Inrichtingen of Horeca)
   -  en de inlogger lid is van een rechtengroep die insertrechten heeft
      op Handhavingen
   -  en de instelling *Sectie: Programma* en *Item: Handhaving uit
      inspectie genereren* aangevinkt is
   -  en compartiment OK
   -  en de instelling *Sectie: Adviezen en Item: AdviescodeBoa* bestaat
      en is aangevinkt en de kolom *Tekst* van deze instelling verwijst
      naar een niet vervallen tbadviesinstanties.dvcode.

-  De knop is disabled indien de bovenliggende zaak/inrichting
   geblokkeerd is (kijk naar uitzondering hierboven).

Door het indrukken van de knop wordt een nieuwe handhavingszaak
aangemaakt zoals hierboven beschreven bij menu item *Maak nieuwe
handhavingszaak van dit traject* waarbij aan dat nieuwe handhavingszaak
direct een advies is uitgezet voor de instantie die hoort bij de
ingestelde AdviescodeBoa.

Triggers linksonder
~~~~~~~~~~~~~~~~~~~

Toon documenten
^^^^^^^^^^^^^^^

(Zie `Toon documenten en
download </docs/probleemoplossing/programmablokken/toon_documenten_en_download.md>`__).

-  Zichtbaar wanneer:

   -  een van onderstaande twee beweringen waar is:

      -  de instelling *Sectie: Documenten Item: Documentregistratie* is
         aangevinkt en de gebruiker het recht *Inzien geregistreerde
         documenten* bij de betreffende module aangevinkt heeft staan
         (bijv. tbomgrechten.dlcomgcorregvsb)
      -  deze instelling staat niet aan en de gebruiker het recht
         *Inzien documenten buiten registratie om bij de betreffende
         module* aangevinkt heeft staan (bijv.
         tbomgrechten.dlcomgcorvsb)

   -  en - wanneer het inspectietraject NIET wordt behandeld in een
      compartiment dan:

      -  moet *Sectie: Documenten* en *Item: OphalenViaFileserver* OF
         *Sectie: Documenten* en *Item: OphalenViaDms* aangevinkt zijn
      -  en - indien OphalenViaDms - dan moet de kolom *Tekst* bij
         instelling *Sectie: KoppelingDocnaardms Item: Methode* de
         waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben en aangevinkt staan

   -  en- wanneer het inspectietraject WEL wordt behandeld in een
      compartiment dan:

      -  moet de kolom dlfileserver of dldms in het betreffende
         compartiment (beheerportaal-Nieuw) aangevinkt zijn
      -  en – indien dlDms aangevinkt dan moet de kolom
         tbcompartiment.dvdmsmethode de waarde StUF-ZAKEN 310 OF CMIS
         1.0 hebben.

-  De knop is disabled indien:

   -  geen fileserver en wel DMS
   -  en methode is StUF-ZAKEN 310
   -  en de externe zaakcode (dvintzaakcode) is leeg. Het programma
      kijkt naar de externe zaakcode van het inspectietraject zelf
      indien de deze is gedefinieerd als zelfstandige zaak in het
      externe zaaksysteem. Dit is het geval wanneer de moduleletter (W =
      Omgeving, H = Handhaving, O = APV/Overig en V = Inrichtingen, C =
      Horeca) van de bovenliggende zaak/inrichting NIET voorkomt in
      kolom *Info* van de instelling *Sectie: Koppeling Zaak* en *Item:
      ZaaktypeInspectietraject*. In de andere gevallen (moduleletter zit
      wel in instelling of instelling bestaat niet) dan komt het externe
      zaak/DMS nummer uit de hoofdzaak/inrichting van de betreffende
      module.

Upload document(en)
^^^^^^^^^^^^^^^^^^^

-  Zichtbaar wanneer:

   -  de instelling *Sectie: Documenten* en *Item: MultipleUpload*
      aangevinkt is
   -  en - wanneer het inspectietraject NIET wordt behandeld in een
      compartiment dan:

      -  moet *Sectie: Documenten* en *Item: OphalenViaFileserver* OF
         *Sectie: Documenten* en *Item: OphalenViaDms* aangevinkt zijn
      -  en - indien OphalenViaDms - dan moet de kolom *Tekst* bij
         instelling *Sectie: KoppelingDocnaardms Item: Methode* de
         waarde StUF-ZAKEN 310 OF CMIS 1.0 hebben en aangevinkt staan

   -  en - wanneer het inspectietraject WEL wordt behandeld in een
      compartiment dan:

      -  moet de kolom dlfileserver of dldms in het betreffende
         compartiment (beheerportaal-Nieuw) aangevinkt zijn
      -  en – indien dlDms aangevinkt dan moet de kolom
         tbcompartiment.dvdmsmethode de waarde StUF-ZAKEN 310 OF CMIS
         1.0 hebben,

-  De knop is disabled indien:

   -  geen document uploadrechten (beheertegel *Functionele rechten*,
      blok Documenten)
   -  OF de zaak geblokkeerd is
   -  OF - indien geen fileserver en wel DMS

      -  en methode is StUF-ZAKEN 310
      -  en de externe zaakcode (dvintzaakcode) is leeg. Het programma
         kijkt naar de externe zaakcode van het inspectietraject zelf
         indien de deze is gedefinieerd als zelfstandige zaak in het
         externe zaaksysteem. Dit is het geval wanneer de moduleletter
         (W = omgeving, H = Handhaving, O = APV/Overig en V =
         Inrichtingen, C = Horeca) van de bovenliggende zaak/inrichting
         NIET voorkomt in kolom *Info* van de instelling *Sectie:
         Koppeling Zaak* en *Item: ZaaktypeInspectietraject*. In de
         andere gevallen (moduleletter zit wel in instelling of
         instelling bestaat niet) dan komt het externe zaak/DMS nummer
         uit de hoofdzaak/inrichting van de betreffende module.

Link
^^^^

-  Indien het gaat om een niet-compartimentszaak zichtbaar en enabled
   indien:

   -  de instelling *Sectie: ExterneLink* en *Item: Inspecties*
      aangevinkt is
   -  en de inlogger lid is van rechtengroep die bij
      hoofdzaak/inrichting het recht: *Starten vanuit zaakportaal van
      hyperlink* heeft.

-  Indien het WEL gaat om een compartimentszaak zichtbaar en enabled
   indien:

   -  het veld *Externe link naar DMS (portaalknop Externe link kijkt
      naar deze instelling)* gevuld is met een werkende hyperlink bij
      het compartiment in het beheerportaal-Nieuw
   -  en de inlogger lid is van rechtengroep die bij
      hoofdzaak/inrichting het recht: *Starten vanuit zaakportaal van
      hyperlink* heeft.

Van de kolom *Tekst* van bovengenoemde instelling wordt een hyperlink
gemaakt, waarbij de variabelen in die Tekst:

-  ``%zaakjaar%`` met het jaar van inspectie-trajectplandatum wordt
   vervangen (yyyy)
-  ``%zaakjaar%`` met jaar en de maand van inspectie-trajectplandatum
   wordt vervangen (yyyymm)
-  ``%zaaknr%`` met de OpenWave Zaakcode (dvwavezaakcode) van het
   inspectietraject
-  %dmsnr% met externe zaak/DMS nummer (dvintzaakcode) van het
   inspectietraject (indien aangevinkt is dat het DMS E-Suite is, dan
   zal er de benodigde vertaalslag uitgevoerd worden op het door E-Suite
   doorgegeven DMS nummer aan OpenWave om via de link op de juiste plek
   binnen E-Suite uit te komen).

Urenregistratie
^^^^^^^^^^^^^^^

-  Zichtbaar en enabled indien de inlogger:

   -  Compartiment OK
   -  en

      -  het recht *uren zichtbaar* aangevinkt heeft staan bij blok
         Inspecties bij de betreffende module (beheertegel *Functionele
         rechten*)
      -  OF het recht *mag uren van anderen muteren* aangevinkt heeft
         staan op de medewerkerskaart.

Checklijst
^^^^^^^^^^

-  Zichtbaar en enabled indien de inlogger:

   -  Compartiment OK
   -  en muteerrecht OK
   -  en er minimaal één - niet vervallen - kaart in de beheertabel
      checklisten (tbchecklistnaam) bestaat die van toepassing is op
      Inspecties (dvvantoepop = 'I') en op de betrokken module
      (dvindelenin)
   -  en als de hoofdzaak onder een compartiment valt inclusief
      inspecties, dan moet de compartimentkey overeenkomen met die van
      de checklistnaam.
