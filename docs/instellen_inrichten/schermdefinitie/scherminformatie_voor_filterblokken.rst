Scherminformatie voor filterblokken op lijstschermen
====================================================

Bij de definitie van een
`standaardlijst </docs/instellen_inrichten/standardlist_standarddetail.md>`__
(beheerapplicatie tabellen standaardapi) kan een verwijzing staan naar
een kaart in tbscreencolumns met daarin gedefinieerd de filteropties die
van toepassing zijn op het betrokken standaardlijstscherm.

De kaart met de filterinformatie in tbscreencolumns heeft dezelfde naam
(dvscreenfilename) als het bijbehorende lijstscherm, waarbij de prefix
echter niet *MDLC\_* maar *MDFC\_* is. Dus als de lijst
MDLC_getxxxList.xml als dvscreenfilename heeft, dan heeft de kaart met
de filterinformatie MDFC_getxxxList.xml als naam. De kolommen
dvclassname en dvviewname hebben bij de filterkaart dezelfde waardes als
die van de bijbehorende lijst.

De plaats en inhoud van de filterkolommen worden, net als bij een lijst-
of detailscherm, geregeld in het text-veld dvscreenxml met een
xml-opmaak.

Binnen de root-tag ``<document>`` worden evenzoveel blokken ``<filter>``
gedefinieerd als er dropdownboxen met filteropties moeten komen in het
lijstscherm.

Eén blok filter betekent dat er één dropdownbox boven aan het
lijstscherm getoond wordt. Binnen één dropdownbox kunnen verschillende
filteropties worden gedefinieerd.

De inhoud van een standaardlijstscherm wordt uiteindelijk beperkt door:

-  de restricties gepaard gaande aan de definitie van de standaardtabel
   (moeder/dochter)
-  daarbinnen op de extra *where clausule bij lijst* opgegeven bij de
   standaardtabeldefinitie
-  daarbinnen op *vervallen kaarten wel/niet* tonen
-  daarbinnen op de ingevoerde waarde van de zoekbox onderaan de lijst
-  daarbinnen op de hieronder besproken filteropties

Daarna komt de paging.

In principe regelt OpenWave op de achtergrond dat de filtering **NIET
case-sensitive** is.

Hieronder een voorbeeld van een filterdefinitie voor twee dropdownboxen.
De eerste box onder de naam Typering bestaat uit twee filteropties (een
keuzelijstje en een invoerveld). De tweede box onder de naam Modules is
een Multiselect.

.. code:: xml

   <?xml version="1.0" encoding="UTF-8"?>
     <document>
    <filter>
     <screenwidth>400</screenwidth>
     <label>Typering</label>
     <columns>
      <blok>
       <label></label>
       <width>10</width>
       <height>10</height>
       <column>
        <regel>1</regel>
        <tagnaam>dvdoctype_oms</tagnaam>
        <label>Documenttype</label>
        <wavetype>keuzelijst</wavetype>
        <divwidth>300</divwidth>
        <source>GeneralWithEmptyLine</source>
        <filter>select dvdoctype id, dvdoctype omschrijving
                                                   from tbdocumenttype where
         ddvervaldatum is null</filter>
        <operator>=</operator>
        <default_value/>
        <default_active/>
        <visible>true</visible>
       </column>
       <column>
        <regel>3</regel>
        <tagnaam>dvfilenaam</tagnaam>
        <label>Filenaam like (gebruik %)</label>
        <wavetype>string</wavetype>
        <divwidth>300</divwidth>
        <source/>
        <filter/>
        <operator>LIKE</operator>
        <default_value/>
        <default_active/>
        <visible>true</visible>
       </column>
      </blok>
                   </columns>
    </filter>
    <filter>
     <screenwidth>350</screenwidth>
     <label>Modules</label>
     <columns>
      <blok>
       <label>Modules</label>
       <width>350</width>
       <height>100</height>
       <column>
        <regel>1</regel>
        <tagnaam>dvmodule</tagnaam>
        <label>Module</label>
        <wavetype>multikeuzecheckbox</wavetype>
        <divwidth>100</divwidth>
        <source>GeneralWithoutEmptyLine</source>
        <filter>select 'W' id, 'Omgeving' omschrijving
        union select 'H' id, 'Handhaving' omschrijving
        union select 'O' id, 'APV/Overig' omschrijving
        union select 'I' id, 'Info-Aanvragen' omschrijving
        union select 'E' id, 'Milieu/gebruik' omschrijving
        union select 'C' id, 'Horeca' omschrijving
        union select 'B' id, 'Oude bouw/sloop' omschrijving
        </filter>
        <icoon/>
        <operator>IN</operator>
        <default_value/>
        <default_active/>
       </column>
      </blok>
     </columns>
    </filter>
     </document>

Beschrijving tags
-----------------

-  **``<filter>``**. Het blok filter kan dus één of meer keer voorkomen
   teneinde de filteropties te kunnen groeperen.

   -  **``<screenwidth>``** geeft de breedte in pixels van de filterbox
      aan. De waarde moet groter of gelijk zijn aan de hoogste waarde
      van de tag bij de onderliggende columns
   -  **``<label>``**. Het gaat hier om de naam waaronder de filterbox
      in het lijstscherm te zien is.
   -  **``<columns>``**. Het blok columns moet één keer voorkomen binnen
      het blok ``<filter>``.

      -  **``<blok>``**. Het blok ``<blok>`` moet één keer voorkomen
         binnen het blok ``<columns>``. **\*\ ``<label>``** moet één
         keer voorkomen binnen het blok ``<blok>`` maar het programma
         kijkt niet naar de waarde van deze tags, mag dus leeg blijven.
         \* **``<width>``** en **``<height>``** moeten één keer
         voorkomen binnen het blok ``<blok>`` en een gevulde waarde
         hebben (bijv. 10) maar die waarde heeft geen invloed op het
         beeld. **\*\ ``<column>``**. Het blok column kan 1 of meer keer
         voorkomen binnen het blok ``<blok>``. Binnen dit blok
         ``<column>`` wordt een filteroptie geregeld. \*
         **``<regel>``**. Integer. Kan gevuld worden met de volgorde van
         het blok ``<column>``. Wordt echter niet ondersteund.
         **\*\ ``<tagnaam>``** Moet verwijzen naam een kolomnaam uit de
         view/tabel die aan het lijstscherm ten grondslag ligt. Een
         tagnaam mag maar één keer in de filterdefinitie voorkomen. \*
         **``<label>``**. De naam die in de filterbox boven de
         filteroptie-regel komt. **\*\ ``<wavetype>``**. Het type
         invoer/aanwijsveld voor de filteroptie. Mogelijkheden zijn: \*
         **string**: de gebruiker kan een tekst string invoeren als
         filterwaarde **\*integer**: de gebruiker kan een geheel getal
         invoeren als filterwaarde \* **boolean**: de gebruiker kan een
         aanvinkvakje aankruisen of leeg laten. Aankruisen wil zeggen
         dat gefilterd wordt op de waarde T en leeg wil zeggen dat
         gefilterd wordt op de waarde F. Het gaat hierbij dus om de
         situatie dat de tagnaam alleen een waarde F of T kan bevatten.
         **\*keuzelijst**: de gebruiker kan kiezen voor één item uit een
         vooraf gedefinieerde lijstje (zie hieronder bij source en
         filter) als filterwaarde \_ **multikeuzecheckbox**. De
         gebruiker kan een of meer items aanvinken van een vooraf
         gedefinieerde lijst (zie hieronder bij source en filter) die
         gelden als filterwaarde (de operator wordt \_'IN'\*)
         **\*datum**: de gebruiker kan een datum kiezen uit een kalender
         \_ **keuzeboolean**: de gebruiker kan aanvinken of de
         achterliggende waarde van de tagnaam gevuld (operator is dan
         \_!= null\* ) of juist niet gevuld moet zijn (operator is dan
         \*= null\*). LET OP: de zogenaamde boolean velden in OpenWave
         (kolomnaam begint met dl en type is char(1)) hebben bijna
         altijd een defaultwaarde F, dus zijn in dat geval nooit leeg,
         **\*\ ``<dvwidth>``**. De breedte in pixels van het
         invoer/aanwijsveld voor de filteroptie.

         -  **``<source>``**. Moet alleen gevuld worden bij wavetype =
            *keuzelijst* OF bij wavetype = *multikeuzecheckbox*. De
            gebruikelijke waarde = *Generalwithoutemptyline* waarmee bij
            wavetype keuzelijst wordt aangegeven dat de gebruiker één
            optie uit de dropdownlijst (zonder lege regel) die wordt
            gedefinieerde in de tag kan kiezen en bij wavetype =
            *multikeuzecheckbox\* dat de gebruiker een of meer opties
            uit de resultaat set van de tag kan
            aanvinken.*\ **\*\ ``<filter>``**\ *. SQL-statement. Moet
            alleen gevuld worden bij wavetype = keuzelijst of bij
            wavetype = multikeuzecheckbox beide met de source =
            Generalwithoutemptyline. De resultaat set moet altijd
            bestaan uit twee kolommen met de naam* **id** *en*
            **omschrijving**\ *. De waarde van de kolom id (die de
            eindgebruiker kiest uit deze lijst) is bepalend voor de
            filteroptie. \_* **``<operator>``** *kan de waardes: \**=\_
            (is gelijk aan)
            \_ of \_!=* (is niet gelijk aan) bij wavetype keuzeboolean
            *of > (is groter dan) \_ of \_<* (is kleiner dan) *of >= (is
            groter of gelijk aan)
            \_ of \_<=* (is kleiner of gelijk aan) \*of *IN* bij
            wavetype = *multikeuzecheckbox*
         -  of LIKE (waarbij de eindgebruiker met behulp van het
            %-symbool de gewenste waarde kan opgeven). \*dvachternaam
            LIKE jansen betekent de lower(dvachternaam) moet gelijk zijn
            aan lower('jansen')
         -  dvachternaam LIKE jansen% betekent de lower(dvachternaam)
            moet beginnen met lower('jansen') \*dvachternaam LIKE
            %jansen betekent de lower(dvachternaam) moet eindigen met
            lower('jansen') \* dvachternaam LIKE %jansen% betekent dat
            lower(dvachternaam) de subsring lower('jansen') moet
            bevatten **\*\ ``<default_value>``**. Optioneel. Kan gevuld
            zijn met een opstartwaarde indien deze filteroptie bij het
            starten van de lijst direct van toepassing moet zijn. In dat
            geval moet ook de tag <default_active> de waarde *true*
            hebben. De waarde van <default_value> kan eventueel
            opgehaald worden uit een query. In dat geval moet bij de tag
            bijv. als volgt worden gedefinieerd:
            *<default_value>%query(querynaam)%</default_value>*.
         -  **``<default_active>``**. Optioneel. true of false. Indien
            de waarde *true* dan wordt verwacht dat <default_value> een
            gevulde waarde heeft. De waarde true of false kan via een
            query-aanroep worden opgehaald: bijv.
            \*<default_active>%query(querynaam)%</default_active>\_. \_
            **``<visible>``** Optioneel. true of false. Indien de waarde
            *false* dan is de filteroptie niet zichtbaar in de
            filterbox. Kan van toepassing zijn om een zelfde
            filterdefinitie in meerder gevallen te kunnen gebruiken. De
            waarde true of false kan via een query-aanroep worden
            opgehaald: bijv. *%query(querynaam)%*. Wanneer de query
            aanroep gevolgd wordt door %paramtype% bijvoorbeeld
            *%query(querynaam,%paramtype%)%* dan zal de string {id} van
            de query worden vervangen met de negende parameter van de
            bijbehorende lijstaanroep (bijv. de 1 in de aanroep
            getFlexlist(SysstandardList,nil,nil,nil,omgeving_docreg,nil,nil,nil,1).

Getrapt keuzes bij filter
-------------------------

Hieronder een voorbeeld van een dropdownfilterbox, waarin de
mogelijkheden van de filteropties van elkaar afhankelijk zijn. Het
voorbeeld is gebaseerd op de view vwfrmallezaken. De gebruiker kies
eerst een gemeente en zal op grond van die keuze vervolgens alleen een
keuze kunnen maken uit de woonplaatsen die horen bij de gekozen
gemeente. Vervolgens kan de gebruiker alleen een straat kiezen die hoort
bij de gekozen woonplaats.

.. code:: xml

   <?xml version="1.0" encoding="UTF-8"?>
     <document>
       <!--filter wordt opgehaald door api getstandardlist met dezelfde naam-->
       <!--tagnaam moet overeen komen met een tagnaam uit de opgehaalde standaardlist-->
    <filter>
     <screenwidth>350</screenwidth>
     <label>Locatie</label>
     <columns>
      <blok>
       <label>Gemeente;Woonplaats;Straat</label>
       <width>350</width>
       <height>100</height>
       <column>
        <regel>1</regel>
        <tagnaam>dvgmntcode</tagnaam>
        <label>Gemeente</label>
        <wavetype>keuzelijst</wavetype>
        <divwidth>250</divwidth>
        <source>generalwithoutemptyline</source>
        <filter>select distinct dvgemeenteid id, dvgemeentenaam as omschrijving
             from vwfrmwoonplaatsen where ddvervaldatum is null
             order by omschrijving</filter>
        <icoon/>
        <operator>=</operator>
        <default_value/>
        <default_active/>
       </column>
       <column>
        <regel>2</regel>
        <tagnaam>dnkeywoonplaats</tagnaam>
        <label>Woonplaats</label>
        <wavetype>keuzelijst</wavetype>
        <divwidth>250</divwidth>
        <source>generalwithoutemptyline</source>
        <filter>select dnkey id, dvwoonplaatsnaam as omschrijving
             from tbwoonplaats where ddvervaldatum is null
                                                       and dvwoonplaatsid ='%tagid(dvgmntcode)%'
             order by omschrijving</filter>
        <icoon/>
        <operator>=</operator>
        <default_value/>
        <default_active/>
       </column>
       <column>
        <regel>3</regel>
        <tagnaam>dnkeyopenbareruimte</tagnaam>
        <label>Straat</label>
        <wavetype>keuzelijst</wavetype>
        <divwidth>250</divwidth>
        <source>generalwithoutemptyline</source>
        <filter>select dnkey id, dvopruimtenaam as omschrijving
         from tbopenbareruimte where dnkeywoonplaats=%tagid(dnkeywoonplaats)%
                                                   and ddvervaldatum is null order by omschrijving</filter>
        <icoon/>
        <operator>=</operator>
        <default_value/>
        <default_active/>
        <visible></visible>
       </column>
      </blok>
     </columns>
    </filter>
     </document>

Met de constructie *%tagid(tagnaam van eerder in te vullen
filterelement)%* kan dus een getrapte keuze worden bewerkstelligd.

Meer voorbeelden
----------------

Wavetype boolean
~~~~~~~~~~~~~~~~

Wordt gebruikt indien de tagnaam verwijst naar een veldtype boolean die
alleen de waarde T of F kan bevatten. Het voorbeeld is gebaseerd op de
view vwfrmlokaties en komt voor in de filter
*MDFC_getOLVwfrmLokaties.xml* in de lijst *alle locaties*
(openingsportaal). Wanneer de gebruiker deze filteroptie aankruist zal
de lijst gefilterd worden op de rijen met dlonbekendadres = T of F.

De defaultwaarde kan hier gebruikt worden om het waardevakje default
aangekruist te laten zijn.

.. code:: xml

   <column>
      <regel>4</regel>
      <tagnaam>dlonbekendadres</tagnaam>
      <label>Gebruik als onbekend adres</label>
      <wavetype>boolean</wavetype>
      <divwidth>250</divwidth>
      <source></source>
      <filter></filter>
      <icoon/>
      <operator>=</operator>
      <default_value>T</default_value>
      <default_active/>
   </column>

Wavetype keuzeboolean
~~~~~~~~~~~~~~~~~~~~~

Wordt gebruikt om te filteren op het al of niet gevuld zijn van een
tagnaam. Het voorbeeld is gebaseerd op de view vwfrmmilinrichtingen en
komt voor in de filter *MDFC_getAlleInrichtingenList.xml* in de lijst
*Alle inrichtingen* (openingsportaal). Wanneer de gebruiker deze
filteroptie aankruist zal de lijst gefilterd worden op de rijen met een
gevulde ddblokkering. Er is dus geen waardevakje: de filtering wordt
helemaal geregeld dor de operator (deze is != of = ). Default_value mag
niet gevuld zijn.

.. code:: xml

   <column>
       <regel>1</regel>
       <tagnaam>ddblokkering</tagnaam>
       <label>Geblokkeerd</label>
       <wavetype>keuzeboolean</wavetype>
       <divwidth>200</divwidth>
       <source></source>
       <filter></filter>
       <icoon/>
       <operator>!=</operator>
       <default_value/>
       <default_active/>
   </column>

Wavetype multikeuzecheckbox
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Wordt gebruikt om te filteren op één of meer mogelijke waardes van
tagnaam. Die mogelijke waardes worden bepaald door de ``<filter>``. Er
is geen default_value mogelijk. De operator moet zijn: IN.

Het voorbeeld is gebaseerd op de view vwfrmalleaanvragen en komt voor in
de filter *MDFC_getAlleZakenList.xml* in de lijst *alle zaken*
(openingsportaal). Wanneer de gebruiker deze filteroptie aankruist zal
de lijst gefilterd worden het voorkomen van de aangekruiste waardes in
de de kolom dvsoortzaak.

.. code:: xml

   <column>
       <regel>1</regel>
       <tagnaam>dvsoortzaak</tagnaam>
       <label>(niet vervallen) Zaaktypes omgeving/handhaving</label>
       <wavetype>multikeuzecheckbox</wavetype>
       <divwidth>290</divwidth>
       <source>GeneralWithoutEmptyLine</source>
       <filter> select dvomschrijving id, dvomschrijving | | ' (omg)' omschrijving from
        tbsoortomgverg where ddvervaldatum is null or ddvervaldatum > fn_vandaag(0)
        union all select dvomschrijving id, dvomschrijving | | ' (hah)' omschrijving from
        tbsoorthhzaak where ddvervaldatum is null or ddvervaldatum > fn_vandaag(0)
        order by omschrijving</filter>
       <icoon/>
       <operator>IN</operator>
       <default_value/>
       <default_active/>
   </column>
