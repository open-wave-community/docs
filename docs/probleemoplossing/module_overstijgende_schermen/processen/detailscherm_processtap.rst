Detailscherm Processtap
=======================

De schermidentifier is *MDDC_geefProcesDetail.xml*

Dit scherm kan worden aangeroepen vanuit de lijst met *Processtappen*,
mits doorgekozen wordt vanuit een stap die enabled is (zie kopje
Disabled/enabled bij beschrijving lijst processtappen).

Probleem
--------

Het scherm geeft een foutmelding:

-  er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie
   `Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
   die niet valide is
-  de inlogger moet kijkrechten hebben op de processtappen bij
   betreffende hoofdzaak (bijvoorbeeld zichtbaar-rechten op
   proces/checklijst bij omgeving).

Disabled/enabled
----------------

Sommige rijen kunnen disabled zijn (zie bij Lijst Processtappen) en die
rijen zijn in het detailscherm niet benaderbaar.

Muteren
-------

Sommige rijen kunnen disabled zijn (zie bij Lijst Processtappen) en die
rijen zijn in het detailscherm niet benaderbaar en dus niet muteerbaar.

Indien enabled geldt dat de kaart muteerbaar is indien:

-  de inlogger wijzigrechten heeft op de adviezen bij betreffende
   hoofdzaak
-  en die bovenliggende hoofdzaak niet is geblokkeerd
-  en de editschuif aan staat
-  en - indien de inlogger lid is van een compartiment - dan moet het
   betreffende compartiment het zaaktype van de hoofdzaak bevatten en de
   gemeente waar de omgevingszaak speelt
-  en - indien de inlogger GEEN lid is van een compartiment, dan mag de
   combinatie van het zaaktype van de hoofdzaak en de gemeente waar de
   hoofdzaak speelt in geen enkel compartiment voorkomen
-  en - indien de instelling *Sectie: Termijnbewaking* en *Item:
   AfgehandeldStapNietMuteerbaar* aangevinkt is - dan moet de
   afgehandelddatum nog leeg zijn. Dit kan overruled worden wanneer de
   inlogger geautoriseerd is om processen te verwijderen OF wanneer de
   inlogger het overrule afhandeldatum-recht heeft (zie ook hieronder
   bij subkopje *Afgehandeld datum*).

Voor de kolommen **streefdatum en omschrijving** geldt dat zij
muteerbaar zijn indien in het beheerportaal-Nieuw (tegel *Processen*)
bij de betreffende stap de eigenschappen *streefdatum aanpasbaar* en
*naam/omschrijving aanpasbaar*, aangevinkt waren/zijn op het moment dat
het proces aan de zaak werd toegevoegd.

Het **blok Voortgang** is alleen zichtbaar indien de volgende
termijnstap afhankelijk is van een ja/nee-stap (afvinkstap). De
betreffende ja/nee stap kan in dit blok worden aangevinkt of uitgevinkt.

Voor de dropdownlijst met **staat gepland voor (persoon)** geldt het
volgende:

-  de kolom is alleen zichtbaar indien de instelling *Sectie:
   Termijnbewaking* en *Item: Voorwiezichtbaar* is aangevinkt
-  de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die
   van de inlogger
-  en de medewerker moet in dienst zijn
-  en het vakje *interne medewerker* moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf
de eigenschap *overrule compartiment* aangevinkt heeft staan -, alle
overige medewerkers met deze eigenschap.

Voor de dropdownlijst met **staat gepland voor team** geldt het
volgende:

-  de kolom is alleen zichtbaar indien de instelling *Sectie:
   Termijnbewaking* en *Item: teamzichtbaar* is aangevinkt
-  het team moet aan hetzelfde compartiment gekoppeld zijn als die van
   de inlogger.

Afgehandeld datum
~~~~~~~~~~~~~~~~~

Voor de afgehandeld datum geldt dat deze in principe muteerbaar is
tenzij in het beheerportaal-Nieuw onder tegel *Processen* bij deze stap
is aangekruist *Afhandeldatum niet rechtstreeks in te vullen (maar via
action of invoerkolom)*. In dat geval zal de afgehandeld datum van deze
processtap niet handmatig door de inlogger kunnen worden aangepast. Het
vullen geschiedt dan bijvoorbeeld door de uitvoering van een action of
het vullen van een extra invoerkolom (zie hieronder).

.. warning::
    **Let op:** indien de inlogger geautoriseerd is om
   processtappen te verwijderen OF het proces overrule
   afhandeldatum-recht heeft, dan kan hij/zij WEL de afgehandeld datum
   muteren (tenzij bovenliggende zaak is geblokkeerd).

Blok action
~~~~~~~~~~~

Het blok *Action* is zichtbaar indien aan de processtap een action is
gekoppeld (beheertegel *Processen*), zie definitie
`Termijnstappen </docs/instellen_inrichten/inrichting_processen/termijnstappen.md>`__.

Met het uitvoeren van de action kan in een aantal gevallen worden
geregeld dat automatisch de afgehandeld datum wordt gevuld. De knop die
de action triggert is alleen enabled bij een lege afhandeldatum. Indien
de action *startwizard(maaknieuwezaak)* wordt aangeroepen teneinde een
vervolgzaak te kiezen, zal automatisch een groep (tbgroepvergunning)
worden aangemaakt, die de vervolgzaak verbindt aan de zaak waar de
processtap aan is gekoppeld (als deze zaak waar de processtap aan is
gekoppeld al aan een groep was verbonden, dan wordt de vervolgzaak ook
aan deze bestaande groep verbonden).

Hoe werkt de action onder water?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dee action bij de wizardknop in blok action is standaard als volgt
gedefinieerd in het detailscherm (in de mddc_geefprocesdetail.xml):
%query(termijnstappen_mddc_getdvaction,%keypointer%)%. Dit is een
systeemquery die door Openwave wordt beheerd.

OpenWave evalueert deze query. Deze query vervangt de action die bij de
aanmaak van de termijnstappen overgenomen is vanuit tbprocitems (in de
kolom dvaction) bij de betreffende termijnstap waarbij de variabelen
%keypointer% en %keyparent% worden vervangen met hun echte waardes.

*Voor evalutie* bijvoorbeeld:

startWizard(maakDocument,6578,tbdocumenten;;tbomgvergunning;%keyparent%,W)

*Na evaluatie*:

startWizard(maakDocument,6578,tbdocumenten;;tbomgvergunning;85842,W)

en vervolgens wordt de wizard gestart waarbij in dit voorbeeld een brief
op grond van documentsjabloon met dnkey 6578 wordt gemaakt.

Wanneer in de action na evaluatie nog een query aanwezig, dan wordt deze
recursief alsnog geëvalueerd.

Bijvoorbeeld *na eerste evaluatie*:

startWizard(maakDocument,%query(docsjabloonperzaaktype,%keyparent%)%,tbdocumenten;;tbomgvergunning;%keyparent%,W)

Dan *na tweede evaluatie*:

startWizard(maakDocument,8890,tbdocumenten;;tbomgvergunning;85842,W)

Blok extra invoerkolommen
~~~~~~~~~~~~~~~~~~~~~~~~~

Het blok *Extra invoerkolommen* is zichtbaar indien bij de processtap
minimaal één extra invoerkolom is gedefinieerd (beheertegel
`Processen </docs/probleemoplossing/module_overstijgende_schermen/processen.md>`__
), zie definitie
`Termijnstappen </docs/instellen_inrichten/inrichting_processen/termijnstappen.md>`__.
Per processtap kan aldaar gedefinieerd worden of er extra invoerkolommen
bij de stap actief worden. Er zijn 5 mogelijkheden: een datum, een
string (max lengte 200), een dropdown (max lengte 100), een geheel getal
of een decimaal getal. Bij de definitie van deze kolommen kan per kolom
aangegeven worden dat het wijzigen van een waarde tot gevolg heeft dat
de afgehandeld datum van de stap wordt gevuld (met de systeemdatum).

Checklistitems
~~~~~~~~~~~~~~

Het lijstje met checklistitems is alleen gevuld indien er checklistitems
bestaan die gekoppeld zijn aan de betreffende processtap.

De schermidentifier is MDLC_getProcItemCheckList.xml.

Deze checklistitems worden automatisch aangemaakt bij het nieuw invoegen
van een proces (zie
`Checklijstitems </docs/probleemoplossing/module_overstijgende_schermen/checklijsten/lijst_checklistitems.md>`__).

De kolom status van dit checklistscherm is muteerbaar indien:

-  de inlogger wijzigrechten heeft op de processtappen bij betreffende
   hoofdzaak (bijvoorbeeld wijzigrechten op proces/checklijst bij
   omgeving) en
-  die bovenliggende hoofdzaak niet is geblokkeerd.
