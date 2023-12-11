# Scherminformatie voor standaard insert- en kopieer

Bij de definitie van een [standaardlijst](/docs/instellen_inrichten/standardlist_standarddetail.md) (beheertegel *Tabellen Standaardapi*) kan bij de definitie van een insert-of kopieerknop een verwijzing staan naar een kaart in tbscreencolumns met daarin gedefinieerd de opmaak van een insertscherm voor de betreffende tabel.

Die verwijzing staat bij de insertknopdefinitie als tweede parameter indien de action bij die insertknop is gedefinieerd als *startWizard* en de eerste parameter de waarde *insertSysStandardRow* heeft.

Die verwijzing staat bij de kopieerknopdefinitie als tweede parameter indien de action bij die kopieerknop is gedefinieerd als *startWizard* en de eerste parameter de waarde *kopieerSysStandardRow* heeft.

De kaart met de insert- of kopieerscherminformatie in tbscreencolumns heeft een naam (dvscreenfilename) met prefix 'MDWC_insert" en die eindigt op '.xml', waarbij het tussenliggende gedeelte bij voorkeur wordt gevuld met de tabelnaam waarop de insert gaat plaatsvinden. Het kopieer- en insertscherm mogen dezelfde zijn, maar hoeft niet!!

De kolom tbscreencolumns.dvclassname heeft dezelfde waarde als die van de bijbehorende lijst (van daaruit wordt de insert of kopieer gedaan) en dvviewname heeft de naam van de tabel waarop de insert/kopieer wordt gedaan.
De plaats en inhoud van de insert- of kopieerscherm kolommen worden, net als bij een lijst- of detailscherm, geregeld in het text-veld dvscreenxml met een xml-opmaak.

Binnen de root-tag `<document>` wordt één blok `<columns>` gedefinieerd en binnen het blok `<columns>` worden vervolgens één of meer blokken `<column>` gedefinieerd..

Indien het gaat om een insert die plaatsvindt op een dochtertabel is de waarde van de foreign key al geregeld in de derde parameter van de definitie van de insertknop bij de standaardtabel.

Bij een kopieeractie is die derde parameter de dnkey van de kaart die gekopieerd moet worden.

De kolommen van de tabel waarop de insert plaatsvindt waarvoor geldt dat zij in de databasedefinitie:

* als verplicht zijn gemarkeerd (not null)
* maar geen defaultwaarde hebben
* en geen foreign key zijn

die kolommen __moeten__ in de xml-string worden opgenomen (de niet verplichte kolommen mogen natuurlijk ook).

Voor een kopieeractie geldt dit niet (alle not null kolommen hebben een waarde op de te kopiëren kaart).

De opmaak van het insert- en kopieerscherm (de xml) is hetzelfde als die van een detailscherm, waarbij:

* echter geen blokken bestaan
* op elke regel slechts één kolom kan voorkomen
* de variabele %keyparent%  desgewenst gebruikt kan worden in `<filter>`
* de variabele '%tagid(xxx)%' desgewenst gebruikt kan worden in `<filter>`. LET OP de apostrofjes: deze horen erbij. Deze variabele wordt vervangen door een eerder gekozen waarde in de tagnaam xxx (meestal dus een veldnaam)
* onderaan een extra tag <default_value> kan worden toegevoegd
* de tagnaam per definitie verwijst naar een veldnaam van de tabel waarop de insert wordt toegepast (dus NIET die van de view) __tenzij__ de tagnaam begint met de tekst 'tag'. In dat geval interpreteert OpenWave deze tag als: deze tagnaam hoef niet aan de database te worden doorgegeven, is geen database-veldnaam.

Voorbeeld:

```xml
<?xml version="1.0" encoding="UTF-8"?>
  <document>
    <!--aangeroepen vanuit api insertSysStandardRow-->
    <!--element tagnaam (m.u.v. tagnaam tag) verwijst naar de kolomnamen van tbprodwkpklant-->
    <columns>
        <column>
            <regel>1</regel>
            <tagnaam>tag</tagnaam>
            <label>Module</label>
            <divwidth>200</divwidth>
            <divheight>30</divheight>
            <edit>true</edit>
            <showhint>true</showhint>
            <wavetype>keuzelijst</wavetype>
            <source>generalwithoutemptyline</source>
            <filter>select 'W' id, 'W: Omgeving' omschrijving from tbportalnames where
                dlisbegin = 'T' union select 'H' id, 'H: Handhaving' omschrijving from
                tbportalnames where dlisbegin = 'T' union select 'O' id, 'O: APV/Overig'
                omschrijving from tbportalnames where dlisbegin = 'T' union select 'I' id,
                'I: Info-Aanvragen' omschrijving from tbportalnames where dlisbegin = 'T'
                union select 'E' id, 'E: Milieu/gebruik' omschrijving from tbportalnames
                where dlisbegin = 'T' union select 'C' id, 'C: Horeca' omschrijving from
                tbportalnames where dlisbegin = 'T'</filter>
            <nullable>false</nullable>
            <icoon/>
        </column>
        <column>
            <regel>2</regel>
            <tagnaam>dnkeyproducten</tagnaam>
            <label>Product</label>
            <divwidth>400</divwidth>
            <divheight>30</divheight>
            <edit>true</edit>
            <showhint>true</showhint>
            <wavetype>keuzelijst</wavetype>
            <source>generalwithoutemptyline</source>
            <filter>select a.dnkey id,  a.dvproductcode | | ' - '  | | coalesce(a.dvproductoms,'')  omschrijving from vwfrmkopproductenzaaktypes a  where (a.ddvervallen is null or a.ddvervallen >= fn_vandaag(0)) 
                and a.dvmoduleletter = '%tagid(tag)%' order by a.dvproductcode </filter>
            <nullable>false</nullable>
            <icoon/>
         </column>
        <column>
            <regel>3</regel>
            <tagnaam>dnkeysubproducten</tagnaam>
            <label>Subproduct</label>
            <divwidth>400</divwidth>
            <divheight>30</divheight>
            <edit>true</edit>
            <showhint>true</showhint>
            <wavetype>keuzelijst</wavetype>
            <source>generalwithemptyline</source>
            <filter>select a.dnkey id,  a.dvsubproductcode | | ' - '  | | coalesce(a.dvsubproductoms,'')  omschrijving from tbsubproducten a  where (a.ddvervallen is null or a.ddvervallen >= fn_vandaag(0)) 
                and a.dnkey in (select b.dnkeysubproducten from tbsubproductdef b where b.dnkeyproductdef in (select c.dnkeyproductdef from tbproducten c  where c.dnkey = '%tagid(dnkeyproducten)%')) order by a.dvsubproductcode </filter>
            <nullable>true</nullable>
            <icoon/>
        </column>
        <column>
            <regel>4</regel>
            <tagnaam>dnkeyproductklanten</tagnaam>
            <label>Klant</label>
            <divwidth>300</divwidth>
            <divheight>30</divheight>
            <edit>true</edit>
            <showhint>true</showhint>
            <wavetype>keuzelijst</wavetype>
            <source>generalwithoutemptyline</source>
            <filter>select dnkey id, dvklantoms omschrijving from tbproductklanten where ddvervallen is null or ddvervallen >= fn_vandaag(0) </filter>
            <nullable>false</nullable>
            <icoon/>
        </column>
        <column>
            <regel>5</regel>
            <tagnaam>dnkeyproductwerkpakketten</tagnaam>
            <label>Werkpakket</label>
            <divwidth>300</divwidth>
            <divheight>30</divheight>
            <edit>true</edit>
            <showhint>true</showhint>
            <wavetype>keuzelijst</wavetype>
            <source>generalwithoutemptyline</source>
            <filter>select dnkey id, dvwerkpakketoms omschrijving from tbproductwerkpakketten where ddvervallen is null or ddvervallen >= fn_vandaag(0) </filter>
            <nullable>true</nullable>
            <icoon/>
        </column>
        <column>
            <regel>6</regel>
            <tagnaam>dvactiviteitcode</tagnaam>
            <label>Activiteitcode</label>
            <divwidth>150</divwidth>
            <divheight>30</divheight>
            <edit>true</edit>
            <showhint>false</showhint>
            <wavetype>string</wavetype>
            <source></source>
            <filter></filter>
            <nullable>true</nullable>
            <icoon/>
            <default_value>Weetniet</default_value>
        </column>
    </columns>
  </document>
```
