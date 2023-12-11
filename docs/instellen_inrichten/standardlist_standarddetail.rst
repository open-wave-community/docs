Standaard Lijst- en Detailschermen
==================================

Portal beheerportaal-Nieuw. Tegel *Tabellen standaardAPI*.

Screenidentifiers (beheertegel *Schermkolomdefinitie tabellen
standaard-API*)

-  MDLC_getVwFrmSysStandardtableList.xml
-  MDDC_getVwFrmSysStandardtableDetail.xml
-  MDFC_getVwFrmSysStandardtableList.xml

Tabellen:

-  tbSysStandardTable/VwfrmSysstandardTable
-  tbSysstandardButton

Omschrijving
------------

Met behulp van de tabel tbSysStandardTable kan een applicatiebeheerder
zelf nieuwe schermen op bestaande OpenWave tabellen/views definiëren.

De kaarten in de tabel tbSysStandardTable hebben een unieke codering.
Elke kaart is een representatie van hoe een bepaalde view of tabel uit
de OpenWave database moet worden getoond met die restrictie dat altijd
gerenderd wordt conform de opmaak van een OpenWave-lijstscherm en
OpenWave-detailscherm. Naast het definiëren van de tabel/view die
getoond moet worden, en met welke parent, worden ook de verwijzing(en)
naar de bijbehorende schermkolomdefinitie(s) vastgelegd in de kaart. In
de dochtertabel tbSysstandardButton kunnen tenslotte de knoppen
linksonder op de te leveren lijst-of detailpagina worden gedefinieerd
met bijbehorende action. Eventueel kan ook een filter op het lijstscherm
worden getoond. Zie hiervoor onderaan deze pagina *Voorbeeld
filterdefinitie*.

Aanroep
-------

-  Aanroep voor het tonen van een **lijstscherm** op basis van de
   informatie van een kaart in tbSysStandardTable (dus bijvoorbeeld een
   action op een tegel):
   *getFlexList(SysStandardList,nil,nil,G,DitIsDeUniekeCodering)*
-  OF aanroep van een blok in een detailscherm, wanneer in dat blok een
   lijstscherm getoond moet worden: Dan moet de tag type van dat blok in
   de xml-definitie van dat detailscherm gevuld worden met bijv.
   *getFlexList(SysStandardList,,%keypointer%,,beheer_kopcompgem)*

Waarbij
~~~~~~~

-  de methode getFlexList() aangeeft dat het resultaat van de aanroep
   een lijstscherm is

   -  de eerste parameter *SysStandardList* aangeeft dat alle informatie
      verder op te halen is in de tabel tbSysStandardTable op basis van
      dvcode = param 5 (dus in de voorbeeldaanroep beheer_kopcompgem of
      DitIsDeUniekeCodering)
   -  de tweede parameter wordt genegeerd. Kan dus leeg zijn
   -  de derde parameter (hier alleen gevuld in tweede voorbeeld) wordt
      alleen gevuld met de waarde van de primary key van de parenttable
      indien van toepassing (welke parenttable: dat staat in de
      betrokken kaart van tbsysstandardtable)
   -  de vierde parameter (hier in het eerste voorbeeld de waarde 'G')
      leeg mag zijn. De vulling met een 'A' of een 'G' betekent dat de
      lijst op moet starten met alle kaarten of alleen de geldige
      kaarten, indien gebruik gemaakt wordt van box vervallen kaarten
      onzichtbaar in de tbSysStandardTable-kaart
   -  de vijfde parameter, met hier de waarde *DitIsDeUniekeCodering*,
      geeft aan in welke kaart van tbSysStandardTable de gewenste
      informatie staat: tbSysStandardTable.dvcode =
      *DitIsDeUniekeCodering* of *beheer_kopcompgem*
   -  optioneel kan nog aangevuld worden tot de negende parameter:
      paramtype. Dit is alleen van toepassing als er bij het lijstscherm
      een filter xml gedefinieerd is en gebruik wordt gemaakt van een
      query afweging bij een van de tags ``<visible>`` in het filter
      xml. De waarde van parameter 9 mag leeg zijn indien ``<visible>``
      true is of gevuld met waarde '1' indien ``<visible>`` waarde false
      moet krijgen.
   -  Aanroep voor het tonen van een **detailscherm** op basis van de
      informatie van een kaart in tbSysStandardTable (dus bijvoorbeeld
      een action op een tegel of knop) :
      *getFlexdetail(SysStandardDetail,1234,DitIsDeUniekeCodering)*
      waarbij:
   -  de methode getFlexDetail() aangeeft dat het resultaat van de
      aanroep een detailscherm is
   -  de eerste parameter *SysStandardDetail* aangeeft dat alle
      informatie verder op te halen is in tabel tbSysStandardTable op
      basis van dvcode = param 3
   -  de tweede parameter de waarde van de primary key bevat van de
      tabel waarvan het detailscherm wordt opgevraagd
   -  de derde parameter, met hier de waarde *DitIsDeUniekeCodering*,
      geeft aan in welke kaart van tbSysStandardTable de gewenste
      informatie staat: tbSysStandardTable.dvcode =
      *DitIsDeUniekeCodering*.

De kolommen van de tabel tbsysstandardtable
-------------------------------------------

-  **Identifier** (dnkey). Primary key van de tabel.
-  **Unieke codering voor tabel** (dvcode). De unieke codering van de
   kaart die bij de action-aanroep getfexlist(sysStandardList,,,,code)
   als vijfde parameter moet worden meegegeven en bij de aanroep
   getfexdetail(sysStandardDetail,,code) als derde parameter.
-  **Systeem-categorie** (dnkeysysstandardcat). Foreign key naar de
   tabel tbsysstandaardcategorie om de standaardapi's beter in te delen.
   Niet verplicht.
-  **Systeemkaart** (dlsystem). Niet muteerbaar. T of F. Indien T dan is
   de betreffende kaart voor de OpenWave-applicatie onmisbaar en mag de
   kaart niet verwijderd worden.
-  **Hoofdtabel- of viewnaam** (dvmaintablename). De naam van de view of
   tabel waarvan een of meer kaarten in lijst of detail getoond moeten
   worden.
-  **Kolomnaam van de primary key** (dvmainprimkeyname). De kolom naam
   van de primary key van de hoofdtabel/view.
-  **Tabelnaam waarop hoofdtabel/view is gebaseerd**
   (dvmainbasetablename). Indien de hoofdtabel een view is dan dient
   hier de naam van de onderliggende hoofdtabel van die view genoteerd
   te worden. Indien de hoofdtabel een tabel is, dan staat hier
   hetzelfde als in de kolom *Hoofdtabel- of viewnaam*.
-  **Kolomnaam foreign key uit deze achterliggende tabel**
   (dvmainbaseforeignkeyname). Deze kolom alleen invullen indien ook de
   kolom *parenttabelnaam* wordt gevuld. Het gaat in dat geval om het
   weergeven van een lijst op basis van *Hoofdtabel- of viewnaam*
   waarbij deze lijst gelimiteerd is door een foreign key naar de
   parenttabel (bijv. de medewerkers van een rechtengroep). Hier dus de
   kolomnaam van de foreign key invullen uit de achterliggende tabel
   (dvmainbasetablename).
-  **Parenttabelnaam** (dvparenttablename). De naam van de tabel (of
   view) die als parent fungeert voor de hoofdtabel/view.
-  **Kolomnaam foreign key (uit hoofdtabel/view)**
   ((dvmainforeignkeyname). Ook deze kolom alleen invullen indien ook de
   kolom *parenttabelnaam* wordt gevuld. Het gaat in dat geval om het
   weergeven van een lijst op basis van Hoofdtabel- of viewnaam waarbij
   deze lijst gelimiteerd is door een foreign key naar de parenttabel
   (bijv. de medewerkers van een rechtengroep). Hier dus de kolomnaam
   van de foreign key invullen uit de hoofdtabel/view (dvmaintablename).
-  **Kolomnaam blokkering uit
   parenttabel**\ (dvparentblokkeringfieldname). Betekent dat indien de
   achterliggende waarde van deze kolom gevuld is - en parenttable is
   van toepassing- , dat dan geen wijzigingen en inserts en deletes bij
   deze tabel kunnen plaatsvinden.
-  **Kolomnaam blokkering (uit
   hoofdtabel/view)**\ (dvblokkeringfieldname ). Betekent dat indien de
   achterliggende waarde van deze kolom gevuld is, dat dan geen
   wijzigingen en deletes bij deze kaart kunnen plaatsvinden.
-  **Schermidentifier voor lijst** (dvlistscreenfilename). De unieke
   naam met de schermkolominformatie die verwijst naar
   tbscreencolumns.dvscreenfilename (beheertegel *Schermkolomdefinitie
   tabellen standaard-api*).

..

   [!WARNING] **Let op:** de conventie in OpenWave voor lijsten is
   MDLC_getXXXXXXXXList.xml. Met de knop achter deze kolomnaam wordt
   naar de betreffende schermkaart in tbscreencolumns genavigeerd.
   Indien er nog geen kaart bestaat wordt deze automatisch aangemaakt.

-  **Schermidentifier voor detail** (dvdetailscreenfilename). De unieke
   naam met de schermkolominformatie die verwijst naar
   tbscreencolumns.dvscreenfilename (beheertegel *Schermkolomdefinitie
   tabellen standaard-api*).

..

   [!WARNING] **Let op:** de conventie in OpenWave voor detailschermen
   is MDDC_getXXXXXXXXDetail.xml. Met de knop achter deze kolomnaam
   wordt naar de betreffende schermkaart in tbscreencolumns genavigeerd.
   Indien er nog geen kaart bestaat wordt deze automatisch aangemaakt.

-  **Schermidentifier voor filter** (dvfilterscreenfilename). De unieke
   naam met de schermkolominformatie die verwijst naar
   tbscreencolumns.dvscreenfilename (beheertegel *Schermkolomdefinitie
   tabellen standaard-api*).

..

   [!WARNING] **Let op:** de conventie in OpenWave voor filterschermen
   is MDFC_getXXXXXXXXList.xml. Met de knop achter deze kolomnaam wordt
   naar de betreffende schermkaart in tbscreencolumns genavigeerd.
   Indien er nog geen kaart bestaat wordt deze automatisch aangemaakt.

-  **Kijkrechtenkolom (bijv. tbomgrechten.dlcomgadvvsb)**
   (dvauthvisiblefield). Een verwijzing naar een rechtenkolom waarvan de
   waarde T moet zijn voor de inlogger om de gevraagde lijst of
   detailpagina te bekijken. Indien ingevuld gaat deze kolom voor op de
   kolom *tbqueries.dvcode kijkrechten*.
-  **Muteerrechtenkolom (bijv. tbomgrechten.dlcomgadvedt)**
   (dvautheditfield). Een verwijzing naar een rechtenkolom waarvan de
   waarde T moet zijn voor de inlogger om de gevraagde lijst of
   detailpagina te muteren. Indien ingevuld gaat deze kolom voor op de
   kolom *tbqueries.dvcode wijzigrechten*.
-  **tbqueries.dvcode kijkrechten (result = true)**
   (dvauthvisiblequerycode). Een verwijzing naar tbqueries.dvcode alwaar
   de SQL-statement een true of een false moet geven, hetgeen aangeeft
   of de inlogger de gevraagde lijst of detailpagina mag bekijken.
   Indien echter de kolom *Kijkrechtenkolom (bijv.
   tbomgrechten.dlcomgadvvsb)* is gevuld dan wordt deze querykolom
   genegeerd.
-  **tbqueries.dvcode wijzigrechten (result = true)**
   (dvautheditquerycode). Een verwijzing naar tbqueries.dvcode alwaar de
   SQL-statement een true of een false moet geven, hetgeen aangeeft of
   de inlogger de gevraagde lijst of detailpagina in beginsel mag
   muteren (in de schermkolomdefinitie wordt daar per cel/kolom
   geautoriseerd). Indien echter de kolom *Muteerrechtenkolom (bijv.
   tbomgrechten.dlcomgadvedt)* is gevuld dan wordt deze querykolom
   genegeerd.

Voorbeeld met gebruik *fn_rechtenkolom en fn_iscompartimentok*

In de kolom dvauthvisiblequerycode wordt naar een query uit tbqueries
verwezen bijv. met de code *omgeving_milalertmuteren*

De query met dvcode = *omgeving_milalertmuteren* kan dan als volgt
gedefinieerd zijn:

| select case when (fn_iscompartimentok(:keyaccount, 'W',{id}) = 1) and
  (fn_rechtenkolom('tbomgrechten.dlbomgmemoedt',:keyaccount) = 'T' )
  then 'true'
| else 'false' end De query maakt gebruik van twee OpenWave functies:

*fn_iscompartimentok* kijkt op grond van de inlogger, de module en de
dnkey van de kaart of de compartimentsrechten in de weg zitten. De
string *:keyaccount* wordt onder water altijd vervangen door de dvcode
van de inlogger. De string *(id)* altijd door de dnkey van de kaart waar
de gebruiker op staat in de hoofdtabel (*dvmaintablename*).

*fn_rechtenkolom* kijkt op grond van de aangegeven rechtenkolom
(rechtentabel gevolgd door een punt gevolgd door de kolomnaam) of de
inlogger (*:keyaccount*) wijzigrechten heeft volgens die rechtenkolom .

Zie ook `Database
functies </docs/instellen_inrichten/openwave_database-functies.md>`__

-  **Module/schermgroepcode** (dvmodulescreengroup). Vrij te gebruiken.
   Alleen indien een vervolgaction van een standaardapi-lijst of detail
   een interne OW-API aanroept, met een verplichte parameter dvmodule,
   dan is een waarde in deze kolom ook verplicht (dvmodulescreengroup is
   dan B,C,E,H,I,O,V of W). Dit is bijvoorbeeld het geval bij een
   wijziging op een kolom (met de interne API-aanroep setcolumnvalue) op
   een detail of lijstscherm van een (dochter)tabel van tbomgvergunning
   (W), tbhandhavingen (H), tbinfoaanvragen (I), tbovvergunningen (O) en
   tbmilinrichtingen (V)en tbmilvergunnngen (E) en tbhorecavergunningen
   (C) en tbbouwvergunningen (B), Bij beheertabellen kan deze kolom dus
   leeg blijven.
-  **Datumkolomnaam box vervallen** (dvvervallenboxfieldname). Indien
   gevuld met een datumkolomnaam van de hoofdtabelview dan zal onderaan
   in de lijstweergave van die tabel/view een aanvinkbox *vervallen
   kaarten onzichtbaar* zijn. Indien onzichtbaar aangevinkt dan zal de
   lijst gefilterd worden op deze kolom is null.
-  **Zoekbox?** (dlzoekbox). Indien aangevinkt dan zal een zoekbox
   onderaan de lijstweergave zichtbaar zijn.
-  **Action;bij dubbel klik; op lijstregel** (dvactionselectlineinlist).
   De action die wordt aangeroepen wanneer de inlogger in de
   lijstweergave dubbelklikt op een regel. De phrase *{id}* zal daarbij
   door OpenWave automatisch vervangen worden door de waarde van de
   primary key (kolom dvmainprimkeyname) uit de hoofdtabel/view.
   Voorbeeld: *getFlexdetail(SysStandardDetail,{id},beheer_rechtsvorm)*
   zal door OpenWave doorgezet worden als bijv.
   *getFlexdetail(SysStandardDetail,1234,beheer_rechtsvorm)*.
-  **Detailvenster openen na insert met sysStandardRow?**
   (dldetailopenennainsert). Indien 'T' dan wordt na een insert met
   insertSysStandardRow (zie hieronder bij sysstandardbuttons) de action
   getFlexdetail(SysStandardDetail,{id},dvcode) uitgevoerd, waarbij
   dvcode wordt vervangen met de waarde van dvcode van de betreffende
   sysstandardtablekaart en {id} met de nieuwe dnkey aangemaakt met de
   insert.
-  **Where clausule;bij lijst** (dvwhere). Indien het gaat om een lijst
   dan kan hier een extra where clausule worden opgegeven waaraan de
   hoofdtabel/view moet voldoen. Bijvoorbeeld bij een medewerkerslijst
   kan hier staan: where dvgeslacht = 'M'. De phrases:

   -  *:keyaccount* zal door OpenWave automatisch worden vervangen door
      tbmedewerkers.dvcode van de inlogger.
   -  *%keyaccount%* idem
   -  *%inlogger%* idem
   -  *%keyparent%* met de primary key van de bovenliggende tabel indien
      de standaardlijst wordt aangeroepen in een blok vanuit een
      detailscherm

Uitgewerkt voorbeeld
--------------------

Een tegel in het beheerportaal waarmee een lijst van rechtengroepen kan
worden opgeroepen, waarbij doorgeklikt kan worden naar een detailscherm
van een rechtengroep en waarbij in dat detailscherm weer een lijst is
opgenomen van de actieve medewerkers die onder die rechtengroep vallen.
Geen muteermogelijkheden.

.. _1-maak-tegel:

1. Maak tegel
~~~~~~~~~~~~~

1. Maak tegel met opschrift *Test_Rechtengroepen* onder een kolom van
   beheerportaal-Nieuw.
2. Als action:
   *getFlexList(SysStandardList,nil,nil,nil,Test_Rechtengroepen)*.
3. Ken de tegel toe aan u zelf.

.. _2-maak-sysstandardtable-kaart-voor-de-lijst--en-detailgegevens-met-code-test_rechtengroepen:

2. Maak sysstandardtable kaart voor de lijst- en detailgegevens met code //Test_Rechtengroepen//
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Maak een nieuwe kaart in tbsysstandardtable (beheertegel *Tabellen
standaardAPI*):

-  **Code**: Test_Rechtengroepen
-  **Hoofdtabel of viewnaam**: tbrechten
-  **Kolomnaam van de primary key**: dnkey
-  **Tabelnaam waarop hoofdtabel/view is gebaseerd**: tbrechten
-  **Schermidentifier voor lijst**: MDLC_getTest_RechtengroepenList.xml
-  **Schermidentifier voor detail**:
   MDDC_getTest_RechtengroepenDetail.xml
-  **Tbqueries.dvcode voor kijkrechten**: sysstandaard_isbeheerder
-  **Action;bij dubbel klik; op lijstregel**:
   getFlexdetail(SysStandardDetail,{id},Test_Rechtengroepen)

De overige kolommen van deze kaart kunnen leeg blijven.

De API getflexlist zal alle data van de kaart ophalen uit tbrechten.
Maar eerst wordt een rechtencheck gedaan door het statement uit
tbqueries (beheerportaal) met dvcode = *sysstandaard_isbeheerder* te
evalueren. Die behoort tot de systeemqueries van OpenWave en bestaat
dus. Het SQL-statement:

.. code:: sql

   select case when dnbeheerniveau = 99 then 'true' else 'false' end
            from tbmedewerkers where trim(dvcode) = trim(:keyaccount)

.. _3-maak-lijstschermkolomdefinitie-voor-mdlc_gettest_rechtengroepenlistxml:

3. Maak lijstschermkolomdefinitie voor MDLC_getTest_RechtengroepenList.xml
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Maak een nieuwe kaart in tbscreencolumns via de beheertegel
*Schermkolomdefinitie tabellen standaard-api*:

-  **Schermidentifier**: xml-filename :
   MDLC_getTest_RechtengroepenList.xml
-  **klasse**: sysStandard
-  **api**: getSysStandardList
-  **view/tabel**: tbrechten

Na opslaan en edit:

-  **in de kolom SQL kopregel1** : select 'Test_Rechtengroepen' from
   tbportalnames where dlisbegin = 'T'

In de kolom **Kolominformatie Toggle F11** moet vervolgens de layout van
het lijstscherm gedefinieerd worden in xml-formaat met een of meer
kolommen uit tbrechten.

.. code:: xml

   <document>
       <!--tagnaam slaat op een kolom uit tbrechten-->
       <column tagnaam="dvgroep">
           <label>Groep</label>
           <index>1</index>
           <length>200</length>
           <wavetype>string</wavetype>
           <icoon/>
           <showhint>false</showhint>
       </column>
       <column tagnaam="dvgroepoms">
           <label>Omschrijving</label>
           <index>2</index>
           <length>400</length>
           <wavetype>string</wavetype>
           <icoon/>
           <showhint>false</showhint>
         </column>
         <column tagnaam="ddvervaldatum">
           <label>Niet meer geldig sinds</label>
           <index>5</index>
           <length>100</length>
           <wavetype>datum</wavetype>
           <icoon/>
           <showhint>false</showhint>
       </column>
      </document>

.. _4-maak-detailschermkolomdefinitie-voor-mddc_gettest_rechtengroependetailxml:

4. Maak detailschermkolomdefinitie voor MDDC_getTest_RechtengroepenDetail.xml
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Maak een nieuwe kaart in tbscreencolumns via de beheertegel
*Schermkolomdefinitie tabellen standaard-api*:

-  **identifier scherm**: xml-filename:
   MDDC_getTest_RechtengroepenDetail.xml
-  **klasse**: sysStandard
-  **api**: getSysStandardDetail
-  **view/tabel**: tbrechten

Na Opslaan:

-  **in de kolom SQL kopregel1**: select 'Test_Rechtengroep' from
   tbportalnames where dlbegin = 'T'

In de kolom **Kolominformatie Toggle F11** moet vervolgens de layout van
het detailscherm gedefinieerd worden in xml-formaat met een of meer
kolommen uit tbrechten.

.. code:: xml

   <?xml version="1.0" encoding="UTF-8"?>
     <document>
       <!--schermdata voor sysstandardapi met code Test_Rechtengroepen-->
       <!--element tagnaam verwijst naar de kolomnamen van tbrechten -->
       <screenwidth>900</screenwidth>
       <columns>
             <blok>
               <label>Rechtengroep</label>
               <width>100</width>
               <height>130</height>
               <type>doorlopend</type>
               <column>
                   <regel>1</regel>
                   <tagnaam>dvgroep</tagnaam>
                   <label>Groepsnaam</label>
                   <divwidth>200</divwidth>
                   <divheight>30</divheight>
                   <edit>false</edit>
                   <showhint>false</showhint>
                   <wavetype>string</wavetype>
                   <source/>
                   <filter/>
                   <refresh>false</refresh>
                   <backcolor/>
                   <fontcolor/>
                   <nullable>false</nullable>
                   <icoon/>
               </column>
               <column>
                   <regel>1</regel>
                   <tagnaam>ddvervaldatum</tagnaam>
                   <label>Niet meer geldig sinds</label>
                   <divwidth>100</divwidth>
                   <divheight>30</divheight>
                   <edit>false</edit>
                   <showhint>false</showhint>
                   <wavetype>datum</wavetype>
                   <source/>
                   <filter/>
                   <refresh>true</refresh>
                   <backcolor/>
                   <fontcolor/>
                   <nullable>true</nullable>
                   <icoon/>
               </column>
               <column>
                   <regel>2</regel>
                   <tagnaam>dvgroepoms</tagnaam>
                   <label>Omschrijving</label>
                   <divwidth>500</divwidth>
                   <divheight>30</divheight>
                   <edit>false</edit>
                   <showhint>false</showhint>
                   <wavetype>string</wavetype>
                   <source/>
                   <filter/>
                   <refresh>false</refresh>
                   <backcolor/>
                   <fontcolor/>
                   <nullable>true</nullable>
                   <icoon/>
               </column>
             </blok>
             <blok>
               <label>Medewerkers</label>
               <width>100</width>
               <height>150</height>
               <type>getFlexList(SysStandardList,,%keypointer%,,Test_MWPerRechtengroep)</type>
           </blok>
         </columns>
     </document>

In het blok met label *Medewerkers* wordt met de action
*getFlexList(SysStandardList,,%keypointer%,,Test_MWPerRechtengroeplabel)*
verwezen naar een lijst (die alhier dus als *een lijst in een detail*
zal worden getoond) waarvan de gegevens staan in een andere kaart van
tbsysstandardtable namelijk die met dvcode =
'Test_MWPerRechtengroeplabel'.

De phrase *%keypointer%* in de schermlayout van een detailscherm zal
daarbij door OpenWave automatisch vervangen worden door de waarde van de
primary key van de detailkaart. In dit voorbeeld de dnkey van de
rechtenkaart. Deze wordt dus doorgegeven als derde parameter aan
getFlexList() zodat OpenWave weet dat alleen die medewerkers getoond
moeten worden met een dnkeyrechtengroep gelijk aan die dnkey.

.. _5-maak-sysstandardtable-kaart-voor-de-lijst--en-detailgegevens-met-code-test_mwperrechtengroep:

5. Maak sysstandardtable kaart voor de lijst- en detailgegevens met code Test_MWPerRechtengroep
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Maak een nieuwe kaart in tbsysstandardtable (beheertegel *Tabellen
standaardAPI*):

-  **Code**: Test_MWPerRechtengroep
-  **Hoofdtabel of viewnaam**: vwfrmmedewerkers
-  **Kolomnaam van de primary key**: dvcode
-  **Tabelnaam waarop hoofdtabel/view is gebaseerd**: tbmedewerkers
-  **Kolomnaam foreign key uit deze achterliggende tabel**: dnkeyrechten
-  **Parenttabelnaam**: tbrechten
-  **Kolomnaam foreign key (uit hoofdtabel/view)**: dnkeyrechten
-  **Schermidentifier voor lijst**:
   MDLC_getTest_MWPerRechtengroepList.xml
-  **Tbqueries.dvcode voor kijkrechten**: sysstandaard_isbeheerder

De overige kolommen van deze kaart kunnen leeg blijven (dus geen
detailscherm voor de medewerkers).

.. _6-maak-lijstschermkolomdefinitie-voor-mdlc_gettest_mwperrechtengroeplistxml:

6. Maak lijstschermkolomdefinitie voor MDLC_getTest_MWPerRechtengroepList.xml
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Maak een nieuwe kaart in tbscreencolumns via de beheertegel
*Schermkolomdefinitie tabellen standaard-api*:

-  **Schermidentifier**: xml-filename:
   MDLC_getTest_MWPerRechtengroepList.xml
-  **klasse**: sysStandard
-  **api**: getSysStandardList
-  **view/tabel**: vwfrmmedewerkers

Na Opslaan en edit: In de kolom **Kolominformatie Toggle F11** moet
vervolgens de layout van het lijstscherm gedefinieerd worden in
xml-formaat met een of meer kolommen uit vwfrmmedewerkers.

.. code:: xml

   <document>
       <!--tagnaam slaat op een kolom uit vwfrmmedewerkers-->
       <column tagnaam="dvcode">
           <label>Codering</label>
           <index>1</index>
           <length>100</length>
           <wavetype>string</wavetype>
           <icoon/>
           <showhint>false</showhint>
       </column>
       <column tagnaam="dvmedewvoluit">
           <label>Naam</label>
           <index>2</index>
           <length>400</length>
           <wavetype>string</wavetype>
           <icoon/>
           <showhint>false</showhint>
         </column>
         <column tagnaam="ddvervaldatum">
           <label>Niet meer in dienst sind</label>
           <index>5</index>
           <length>100</length>
           <wavetype>datum</wavetype>
           <icoon/>
           <showhint>false</showhint>
       </column>
      </document>

Controle op valide schermverwijzingen
-------------------------------------

In het servicecentrumportaal onder de kolom notificaties is een tegel
*Ontbrekende sysstandardschermen in AAR* gedefinieerd. Met deze tegel
wordt een lijst gegenereerd van schermaanroepen (lijstschermen of
detailschermen of filterschermen of insertstandardrowschermen) in
tbsystandardtable en/of tbsysstandardbutton (dus in de tabel achter de
tegel *tabellen standaardapi* van het de nieuwe beheerportaal onder de
kolom scherm- en tegelbeheer) die niet zijn opgenomen in de AAR.

Dit zijn schermen die niet met implementatie en updates van OpenWave
zijn aangeleverd. Dat kan zijn omdat de schermen door een functioneel
beheerder zelf zijn gedefinieerd: in de tabel tbscreencolumns (tegel
*Schermkolomdefinitie tabellen standaard-api*) is de kolom dvscreenxml
in dat geval gevuld met de eigen opmaak. In bovengenoemde controlelijst
is dat zichtbaar indien de kolom **Afwijkend scherm** aangevinkt is. Er
gaat dus pas iets mis indien een regel in deze lijst is opgenomen zonder
dat de kolom *Afwijkend scherm* is gevuld. Een reden is vaak dat de
verwijzing en benaming van de feitelijke opmaakxml-file in de AAR van
elkaar verschillen in kamelennotatie.

Filterdefinitie bij lijstscherm
-------------------------------

Zie: `Scherminformatie voor filterblokken op
lijstschermen </docs/instellen_inrichten/schermdefinitie/scherminformatie_voor_filterblokken.md>`__.
Indien er gewenst is dat het lijstscherm gefilterd kan worden zal er een
filter xml moeten worden gedefinieerd. De naam van de xml moet beginnen
net 'MDFC\*' en de rest van de naam moet gelijk zijn als de xml-naam van
het lijstscherm (zonder de prefix MDDLC\*).

Ga naar gewenste kaart in tbsysstandardtable (beheertegel: *Tabellen
standaardAPI*):

-  Zet bij **Schermidentifier voor filter** (bijv.:
   MDFC_getTest_MWPerRechtengroepList.xml want in voorbeeld is de
   lijst.xml MDLC_getTest_MWPerRechtengroepList.xml)
-  Klik op de knop 'Ga naar schermdefinitie'
-  In de kolom **Kolominformatie Toggle F11** moet vervolgens de layout
   van het filterscherm gedefinieerd worden in xml-formaat met een of
   meer kolommen uit het lijstscherm. In het voorbeeld worden twee
   filters gemaakt.

Knoppen op lijst- en detailschermen
-----------------------------------

Knoppen die binnen een detailscherm dat door tbsysstandardtable wordt
gedefinieerd- bijv. achter een specifieke kolom - moeten verschijnen,
worden in de xml van dat detailscherm gedefinieerd inclusief de actions
die aan die knoppen verbonden moeten zijn: dus - in bovenstaand
voorbeeld - in de MDFC_getTest_MWPerRechtengroepList.xml. Zie
`Scherminformatie voor
detailschermen </docs/instellen_inrichten/schermdefinitie/scherminformatie_voor_detailschermen.md>`__.

De knoppen die linksonder op het gedefinieerde lijst- of detailscherm
moeten komen, kunnen binnen de detailkaart van tbSysStandardTable in het
blok *Knoppen* worden gedefinieerd. Deze informatie wordt in de tabel
tbSysstandardButton opgeslagen: een dochtertabel van tbsysstandardtable.

Per knop zijn de volgende kolommen beschikbaar:

-  Blok Identifier:

   -  **Systeemkaart** (dlsystem). Indien aangevinkt dan is de kaart bij
      een update door REM aangemaakt en onontbeerlijk voor goede werking
      van het programma. Niet aankomen dus.

-  Blok Knop:

   -  **Hint**. Deze tekst verschijnt als hint bij de knop, of als
      omschrijving van de knop indien onderdeel van itemlist.
   -  **Lijst of Detail**. Een L of een D. Indien L dan is de knop
      zichtbaar op het gedefinieerde lijstscherm. Bij D dus alleen op
      het detailscherm.
   -  **Linksonder of Itemlijst**. Een L of een I. Indien L dan
      verschijnt de knop met een icoon linksonder aan de pagina. Indien
      I dan verschijnt de knop als item met als omschrijving de Hint in
      een itemlijst rechtsboven aan de pagina.
   -  **Icoonnummer** Alleen van toepassing indien (L)inksonder. Hier
      moet een nummer komen uit de
      lijst:`Iconenlijst </docs/instellen_inrichten/schermdefinitie/iconenlijst.md>`__.
   -  **Volgorde**. Met deze numerieke waarde kan de volgorde van de
      knoppen van links naar rechts of - indien itemlist- van boven naar
      beneden bepaald worden.
   -  **Refresh**. Indien aangevinkt dan zal het scherm na het uitvoeren
      van de action bij de knop opnieuw worden uitgeschreven.

-  Blok Rechten:

   -  **Action execute-rechtenkolom** (dvauthexecutefield). Een
      verwijzing naar een rechtenkolom waarvan de waarde T moet zijn
      voor de inlogger om de de action die aan de knop vastzit te mogen
      uitvoeren. Indien ingevuld gaat deze kolom voor op de kolom
      *tbqueries.dvcode action*\ rechten.
   -  **tbqueries.dvcode action execute (result = true)**
      (dvauthexecutequerycode). Een verwijzing naar tbqueries.dvcode
      alwaar de SQL-statement een true of een false moet geven, hetgeen
      aangeeft of de inlogger de action bij de knop mag uitvoeren.
      Indien echter de kolom *execute-rechtenkolom (bijv.
      tbomgrechten.dlcomgadvvsb)* is gevuld dan wordt deze querykolom
      genegeerd.

-  Blok Action en parameters. De eerste kolom is de naam van de aan te
   roepen methode. De volgende kolommen worden gevuld met één of meer
   vereiste parameters. Voor alle action/parameters geldt dat 'on the
   fly' OpenWave de variabelen:

   -  %:keyaccount% zal vervangen met de waarde van tbmedewerkers.dvcode
      van de inlogger
   -  %inlogger% met de waarde van tbmedewerkers.dvcode van de inlogger
   -  %keypointer% met de waarde van de primary key van de kaart waar de
      gebruiker op dat moment op staat (alleen bij knoppen op een
      detailscherm)
   -  %keyparent% met de waarde van de primary key van de
      parenttabelkaart
   -  %query(querynaam)% wordt vervangen door resultaat van de query met
      naam querynaam (alleen bij knoppen op een detailscherm)
   -  %query(querynaam,%keypointer%)% wordt vervangen door resultaat van
      de query met naam querynaam, waarbij de string {id} in de query
      eerst wordt vervangen met de waarde van de primary key van de
      kaart waar de gebruiker op dat moment op staat (alleen bij knoppen
      op een detailscherm)
   -  { + kolomnaam uit hoofdview/tabel + } wordt vervangen door de
      achterliggende waarde van die kolomnaam voor de actieve rij (zowel
      detail als lijstscherm). Dus stel dat de hoofdview/tabel =
      tbomgvergunning en een van de parameters heeft de waarde
      {dvzaakcode} dan zal die parameter vervangen worden met de
      achterliggende waarde van dvzaakcode voor de actieve rij.

Voorbeeld knop Standaard insertscherm
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Om een knop te maken met als doel een standaard insert op een tabel moet
bij de knopdefinitie de action startWizard aangeroepen worden met:

-  als eerste parameter de tekst *insertSysStandardRow*
-  als tweede parameter de schermnaam van een xml waarin het
   insertscherm is gedefinieerd. Bijv. MDWC\ *insertTbKopCompGem.xml.
   Deze naam moet beginnen met 'MDWC*' en eindigen op '.xml'. De xml met
   daarin de scherminformatie moet opgenomen worden in de tabel
   tbscreencolumns. OpenWave maakt zelf een kaart aan in deze tabel als
   deze niet bestaat. Indien (insertSysStandardRow) zal het programma op
   het detailscherm van de knop achter de tweede parameter een
   verwijsknop naar deze screencolumns kaart plaatsen
-  de derde parameter is LEEG indien de tabel waarop een insert
   plaatsvindt GEEN parenttabel heeft. Indien deze tabel echter wel een
   parenttabel heeft dan moet deze parameter gevuld worden met de tekst
   %keyparent%. De tekst %keyparent% wordt door OpenWave 'on the fly'
   vervangen met de primary key van de parenttabel
-  als vierde parameter een verwijzing naar de unieke codering van de
   kaart uit tbsysstandardtabel waar deze knopdefinitie bij hoort.

Voor de opmaak van het insertscherm (de xml) zie: `Scherminformatie voor
standaard insert- en
kopieer </docs/instellen_inrichten/schermdefinitie/scherminfomatie_voor_standaard_insertschermen.md>`__.

Voorbeeld knop Standaard verwijderen van een kaart
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Om een knop te maken met als doel een standaard verwijderactie op een
kaart van een tabel moet bij de knopdefinitie de action startWizard
aangeroepen worden met:

-  als eerste parameter de tekst *deleteSysStandardRow*
-  als tweede parameter de tabelnaam gevolgd door een punt gevolgd door
   *{id}* die *{id}* wordt on the fly' door OpenWave vervangen met
   primary key van de kaart die verwijderd moet worden
-  als derde parameter een kolomnaam uit de view of tabel die aan de
   lijst ten grondslag ligt, waarvan de achterliggende waarde gebruikt
   wordt voor de *weet u zeker* tekst
-  als vierde parameter de code uit tbsysstandardtable die verwijst naar
   de kaart waar de betreffende standaardlijst in is gedefinieerd.

Deze methode deleteSysStandardRow kijkt naar de voorwaarden gedefinieerd
in de kaart uit tbsysstandardtable met dvcode = de vierde parameter.

In deze kaart kan de *Kolomnaam blokkering uit parenttabel* gevuld zijn,
hetgeen betekent dat indien de achterliggende waarde van deze kolom
gevuld is - en parenttable is van toepassing- , dat dan de
verwijderactie niet door kan gaan. In deze kaart kan de *Kolomnaam
blokkering uit hoofdtabel/view* gevuld zijn, hetgeen betekent dat indien
de achterliggende waarde van deze kolom gevuld is, dat dan de
verwijderactie niet door kan gaan.

In de dochtertabel tbsysstandardbutton is bij de betreffende
deletesysstandardrowkaart gedefinieerd naar welke rechten het programma
dient te kijken.

Voor verwijderacties op de hoofdtabellen houdt OpenWave rekening met
compartiment.

OpenWave waarschuwt ook met naam en toenaam dat een verwijderactie niet
plaats kan vinden indien er een foreign key in de weg zit.

Zie verder over het gebruik en mogelijkheden van actions:
`Actions </docs/instellen_inrichten/actions.md>`__.
