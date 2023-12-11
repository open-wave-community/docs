Aanmaken van nieuwe inrichting
==============================

Vanuit het archiefportaal \*Zaken/**inrichtingen\*** en vanaf scherm
*Alle inrichtingen* kan met de insertknop een nieuwe inrichting
aangemaakt worden op de straat die op dat moment actief is.

Rechten
-------

**Recht op insert inrichting.** De inlogger moet lid zijn van een
rechtengroep met insertrechten op inrichtingen
(tbmilrechten.Dlbmilinrins). Indien de inlogger lid is van een
`compartiment </docs/instellen_inrichten/compartimenten.md>`__ moeten er
bedrijfsoorten aan dat compartiment zijn toegekend (en een inrichting
kan in dat geval alleen worden aangemaakt binnen een gemeente die
toegekend is aan dat compartiment).

**Recht op aanmaak nieuw locatie:** Na keuze van de module waarvoor een
nieuwe inrichting aangemaakt moet worden kan de inlogger de locatie
aanwijzen binnen de gegeven straat. Het kan zijn dat daarbij een
huisnummer wordt ingetikt, waardoor het programma een nieuwe locatie (in
tbperceeladressen) moet aanmaken. De rechtengroep van de inlogger moet
hiervoor op het hoofdscherm rechten het recht: *locatieadressen nieuw*
(tbrechten.dldpclins) aangevinkt hebben.

Keuze bedrijfsoort
~~~~~~~~~~~~~~~~~~

Indien de inlogger lid is van een compartiment dan moet er een
bedrijfsoort worden gekozen. De mogelijke bedrijfsoorten zijn toegekend
in het compartiment. Eventueel eigen masker en lengte voor het bepalen
van het inrichtingnummer zijn per bedrijfsoort te
definiëren/gedefinieerd in het compartimentsdetailscherm.

Controle met BAG
~~~~~~~~~~~~~~~~

Deze kan automatisch worden uitgevoerd met een StUF-BG bevraging indien
de instelling *Sectie: KoppelingBAG Item: Methode en Tekst: StUF-310*
aangevinkt is. De verplichte instellingen hierbij voor de opmaak en
adressering van de stuf-berichten zijn (zie `BAG
bevraging </docs/probleemoplossing/programmablokken/bag_bevraging.md>`__):

*Sectie: KoppelingBAG*

-  Item: *HTTPSoapAction_tgoLv01*. In de kolom *Tekst* hier de waarde
   ``[http://www.egem.nl/StUF/sector/bg/0310/tgoLv01](http://www.egem.nl/StUF/sector/bg/0310/tgoLv01.md)``

   -  *Item: Ontvangstadres*. In de kolom *Tekst* het endpoint waar het
      vraagbericht naar toe moet
   -  *Item: Zender_Applicatie*. De kolom *Tekst* met de applicatie
   -  *Item: Zender_Organisatie*. De kolom *Tekst* met de organisatie
   -  *Item: Ontvanger_Applicatie*. De kolom *Tekst* met de applicatie
   -  *Item: Ontvanger_Organisatie*. De kolom *Tekst* met de organisatie

Indien het adres niet wordt aangetroffen in de BAG, dan wordt de
identificatie van het locatie adres leeggemaakt. Wel gevonden: dan
worden Datum BAG, identificatie en puntcoördinaten gevuld.

*Opmerking:* indien gewenst kunnen bepaalde huisnummers uitgesloten
worden van controle/synchronisatie met BAG. Zie de instelling
*NieuweZaakGeenBAGSync* bij `Sectie
Programma </docs/instellen_inrichten/configuratie/sectie_programma.md>`__.

Automatisch aanmaken mappen of fileshare
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien:

-  de inrichting NIET valt onder een compartiment

   -  de instelling *Sectie: Documenten Item: OphalenViaFileserver*
      aangevinkt is
   -  en de instelling *Sectie: Documenten Item:
      AutomAanmaakFileservermappen* aangevinkt is

OF indien:

-  de inrichting WEL valt onder een compartiment

   -  de kolom *Ophalen via fileserver* op de detailkaart van het
      betreffende compartiment is aangevinkt
   -  en de kolom *Automatisch aanmaken mappen* (dlautoaanmaakmappen)
      aangevinkt is bij het betreffende compartiment

dan zullen bij het aanmaken van een nieuwe inrichting automatisch de
mappen genoemd in de rijen van *Sectie: Aanmaakmappen* worden aangemaakt
waarvan item begint met 'Inrichting\_'. Hierbij uitgezonderd zijn de
mappen waarin de variabele ``%inspnr%`` is opgenomen. Indien OpenWave in
de cloud draait, dan moet wel de
`satellite </docs/instellen_inrichten/satellite_filesysteem.md>`__
geïnstalleerd zijn.

Automatisch vullen van kolom dvhyperlink
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Zie: `Hyperlink </docs/instellen_inrichten/hyperlink.md>`__.
