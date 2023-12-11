Lijst Processtappen
===================

De schermidentifier is *MDLC_geefProcessenOverzicht.xml*.

Deze lijst kan worden aangeroepen vanuit het zaakportaal Omgeving,
Handhavingen, Bouw/sloop, Milieu/gebruik en APV/Overig, Infoaanvraag en
Horeca. De lijst toont de termijnbewakingsstappen bij een zaak.
Afhankelijk van de invulling van zogenaamde ja/nee-stappen
(afvinkstappen) zijn sommige termijnstappen niet in gebruik en niet
zichtbaar.

Deze niet in gebruik termijnstappen kunnen toch zichtbaar gemaakt worden
indien de instelling *Sectie: Processen en Item:
StappenNietIngebruikTonen* is aangevinkt. Dan worden de regels die niet
benaderd kunnen worden vanwege een afvinkstap toch getoond, maar dan
disabled en default met een opacity van 0,5. Deze opacityschaal kan zo
nodig worden bijgesteld door *Getal1* van bovenstaande instelling te
vullen met een waarde groter dan 0 en kleiner of gelijk 1.

Bijzondere Regels
-----------------

In de beheer- bij de definitie van de processen kunnen twee soorten
termijnstappen worden gedefinieerd die niet aan de voorkant terug te
vinden zijn:

-  Een stap met de naam *Startregel* waarbij volgnummer de waarde 0
   heeft, wordt door OpenWave niet opgenomen bij de uit te voeren
   processtappen, maar enkel onder water gebruikt om twee processen aan
   elkaar te koppelen.
-  Een stap met de naam *Tussenregel* wordt wel opgenomen bij de uit te
   voeren processtappen, maar is altijd onzichtbaar. Deze stap krijgt
   bij de aanroep van de wizard *SluitZaak* automatisch als
   afhandeldatum de streefdatum van die zaak. De *Tussenregel* wordt ook
   niet opgenomen in de vwfrmeersteprocesstapperzaak en ook niet in de
   vwfrmeerstestapperproces, zodat er geen openstaande taak op deze stap
   kan staan. Zie ook
   `Termijnstappen </docs/instellen_inrichten/inrichting_processen/termijnstappen.md>`__
   bij kopje *Tussenregel*.

Probleem
--------

Het scherm geeft een foutmelding:

-  er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie
   `Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
   die niet valide is
-  de inlogger moet kijkrechten hebben op de processtappen bij
   betreffende hoofdzaak.

Disabled/enabled - Chronologisch afhandelen
-------------------------------------------

Sommige rijen kunnen disabled zijn (zij zijn dan zichtbaar in een
zachtgrijze tint) en derhalve niet muteerbaar. Dit kan in drie gevallen:

-  de rij is disabled vanwege een niet gevulde ja/nee stap (afvinkstap)
-  en/OF in het beheerportaal is bij de definitie van het proces de
   kolom *Stappen chronologisch afwerken* (dlmoetstapvoorstap)
   aangevinkt. Dat heeft dan tot gevolg dat de processtappen bij dat
   proces bij een zaak één voor één moeten worden afgehandeld. Alleen de
   stappen met een reeds gevulde afgehandeld datum en de stap met de
   eerstvolgende LEGE afgehandeld datum zijn in dat geval enabled. De
   overige stappen zijn in dat geval wel zichtbaar, maar disabled.
-  en/OF de stap is toegekend aan een team, maar de inlogger is geen lid
   van dat team, terwijl:

   -  en de instelling *Sectie: Termijnbewaking* en *Item:
      Teamzichtbaar* is aangevinkt
   -  en *Getal1* van de instelling *Sectie: Termijnbewaking* en *Item:
      Teamzichtbaar* de waarde 1 heeft.

Muteren
-------

Een rij kan gemuteerd worden indien:

-  de inlogger wijzigrechten heeft op de processtappen bij betreffende
   hoofdzaak (bijvoorbeeld wijzigrechten op proces/checklijst bij
   omgeving)
-  en die bovenliggende hoofdzaak niet is geblokkeerd
-  en in de schermkolomdefinitie (beheer) is de eigenschap
   *lijst_automatisch in editmode* aangevinkt
-  en de kolom heeft de tag op true staan in de schermkolomdefinitie
-  en - indien de inlogger lid is van een compartiment - dan moet het
   betreffende compartiment het zaaktype van de bovenliggende zaak
   bevatten en de gemeente waar die zaak speelt
-  en - indien de inlogger GEEN lid is van een compartiment, dan mag de
   combinatie van het zaaktype van de bovenliggende zaak en de gemeente
   waar die zaak speelt in geen enkel compartiment voorkomen
-  en de editschuif aan staat
-  en de stap is Enabled (zie hierboven)
-  en - indien de instelling *Sectie: Termijnbewaking en Item:
   AfgehandeldStapNietMuteerbaar* aangevinkt is - dan moet de
   afgehandeld datum leeg zijn.

De kolommen **afgehandeld datum** en **verantwoordelijke** kunnen in
principe voor alle rijen worden aangepast. Voor de **afgehandeld datum**
geldt echter dat indien in het beheerportaal-Nieuw onder tegel
*Processen* bij deze stap is aangekruist *Afhandeldatum niet
rechtstreeks in te vullen (maar via action of invoerkolom)* dan zal de
afgehandeld datum van deze processtap niet handmatig door de inlogger
kunnen worden aangepast. Het vullen geschiedt dan bijvoorbeeld door de
uitvoering van een action of het vullen van een invoerkolom. De inlogger
moet daartoe via het detailscherm van de stap de action starten (het
blok *Action* is dan zichtbaar), via de lijst termijnstappen op de knop
met drie puntjes klikken of een extra invoerkolom vullen (dat blok is
dan ook zichtbaar in het detailscherm van de stap). De afgehandeld datum
wordt daarmee automatisch gevuld indien goed gedefinieerd.

Voor de kolommen **streefdatum** en **omschrijving** geldt dat zij
muteerbaar zijn indien in het beheerportaal-Nieuw (tegel *Processen*)
bij de betreffende stap de eigenschappen *streefdatum aanpasbaar* en
*naam/omschrijving aanpasbaar*, aangevinkt waren/zijn op het moment dat
het proces aan de zaak werd toegevoegd. Het muteerbaar zijn is hierbij
dus afhankelijk van kolom en regel. De kolom *Ja/nee* (de eerste kolom)
is altijd muteerbaar. Het gaat hier om de afvinkstap die bij de
termijnstap hoort.

Zichtbaarheid kolommen
----------------------

-  Voor de dropdownlijst met **verantwoordelijke (persoon)** geldt het
   volgende:

   -  de kolom is alleen zichtbaar indien de instelling *Sectie:
      Termijnbewaking* en *Item: Voorwiezichtbaar* is aangevinkt
   -  de dropdownlijst bestaat uit de medewerkers die aan hetzelfde
      compartiment gekoppeld zijn als die van de inlogger
   -  en de medewerker moet in dienst zijn
   -  en het vakje *interne medewerker* moet aangevinkt zijn.

-  Aan deze lijst worden toegevoegd - maar alleen indien de inlogger
   zelf de eigenschap: *overrule compartiment* aangevinkt heeft staan -,
   alle overige medewerkers met deze eigenschap.
-  Voor de dropdownlijst met **verantwoordelijk team** geldt het
   volgende:

   -  de kolom is alleen zichtbaar indien de instelling *Sectie:
      Termijnbewaking* en *Item: teamzichtbaar* is aangevinkt
   -  de dropdownlijst bestaat uit teams die aan hetzelfde compartiment
      gekoppeld zijn als die van de inlogger.

-  Indien de instelling *Sectie: Termijnbewaking en Item:
   Vervallenzichtbaar* wordt aangevinkt dan is de kolom **vervallen**
   (dlvervallen) als aanvinkvakje zichtbaar in de lijst met
   processtappen onder de kolom met label X. Het aanvinken van de
   vervallenkolom - dit kan alleen indien ook de afgehandeld datum op
   die rij te muteren is - heeft tot gevolg dat indien de afgehandeld
   datum nog leeg was, deze wordt gevuld met de systeemdatum. Het
   uitvinken heeft NIET tot gevolg dat de afgehandeld datum leeg wordt
   gemaakt.
-  Vraagtekenknop: zie hieronder bij triggers in lijst.

Triggers in de lijst
--------------------

-  Dubbel klikken op een regel (buiten de kolom afgehandeld) opent het
   detailscherm van een processtap. Altijd enabled.
-  Vraagtekentje-knop. Zichtbaar en enabled indien de instelling
   *Sectie: Termijnbewaking en Item: ToelichtingZichtbaar* aangevinkt
   wordt. Er wordt dan een kolom met een vraagteken-knop op de regels
   zichtbaar die een gevulde kolom dvprocitemtoelichting hebben. Deze
   toelichting-kolom is bij de aanmaak van de processtappen bij een zaak
   overgenomen uit de bijbehorende processtap-definitie (beheertegel
   *Processen*).

Triggers in het scherm linksonder
---------------------------------

-  Insertknop (alleen processen die gekoppeld zijn aan hetzelfde
   compartiment als die van de inlogger):

   -  Altijd zichtbaar indien Compartiment OK.
   -  Enabled indien:

      -  inlogger insert-rechten heeft op de processtappen bij
         betreffende hoofdzaak
      -  en die bovenliggende hoofdzaak niet is geblokkeerd.

-  Deleteknop:

   -  Altijd zichtbaar indien Compartiment OK
   -  Enabled indien:

      -  inlogger verwijderrechten heeft op de processtappen bij
         betreffende hoofdzaak
      -  en die bovenliggende hoofdzaak niet is geblokkeerd.

-  Bewerk ja/nee stappen:

   -  Zichtbaar indien de instelling *Sectie: Processen Item:
      AfvinkstappenGeenEigenScherm* NIET is aangevinkt. \|
   -  Enabled indien er ja/nee-stappen bestaan bij de getoonde
      procedures.

-  Checklist:

   -  Zichtbaar en enabled indien er tenminste één checklistitem bestaat
      dat gekoppeld is aan een procedure en aan de hoofdzaak.

Triggers rechtsboven in menu Opties
-----------------------------------

-  **Toon alle stappen** (Klikken op deze knop betekent een resfresh van
   het scherm waardoor alle processtappen getoond worden (dus zowel de
   openstaande als de afgehandelde processtappen):

   -  alleen zichtbaar als op het lijstscherm de OPENSTAANDE
      processtappen worden getoond
   -  dit betekent dat OF de tegel die de lijst oproept is gestart met
      aanroep
      \*getFlexList(TBTERMIJNBEWSTAPPEN,TBOMGVERGUNNING,{id},\ **O**,W)\*,
      OF er is net op de knop \*Toon openstaande stappen\* geklikt.

-  **Toon openstaande stappen** (Klikken op deze knop betekent een
   resfresh van het scherm waardoor alleen nog de openstaande
   processtappen getoond worden:

   -  alleen zichtbaar als op het lijstscherm ALLE processtappen worden
      getoond
   -  dit betekent dat OF de tegel die de lijst oproept is gestart met
      aanroep
      \*getFlexList(TBTERMIJNBEWSTAPPEN,TBOMGVERGUNNING,{id},\ **nil**,W)\*,
      OF er is net op de knop \*Toon openstaande stappen\* geklikt.

-  Voor beide knoppen geldt dat deze NIET zichtbaar zijn als het
   lijstscherm gestart is met de actie voor het tonen van de
   Afgehandelde processtappen:
   \*getFlexList(TBTERMIJNBEWSTAPPEN,TBOMGVERGUNNING,{id},\ **A**,W)\*.

N.b. De aanroepen zijn hier als voorbeeld uitgeschreven voor de module W
(omgeving).

Welke processen kunnen worden aangemaakt?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Indien processen zijn verbonden aan de soort hoofdzaak (beheer
zaaktypes) dan kan de gebruiker alleen kiezen uit dit rijtje met de
extra restrictie dat het volgordenummer groter is dan die van de reeds
opgenomen processen bij de zaak. Indien echter de instelling *Sectie:
Processen en Item: VolgordeVrij* aangevinkt is dan wordt bij het
toevoegen van een nieuw proces bij een zaak NIET meer gekeken naar het
procesvolgnummer.

In alle gevallen wordt een nieuw proces onderaan de lijst ingevoegd aan
het op dat moment enablede eindpunt (er kunnen namelijk meer eindpunten
zijn, die disabled/enabled worden met de afvinkstappen). In principe kan
een proces maar één keer worden opgenomen bij een zaak tenzij het
attribuut bij de procesdefinitie *meer keer oproepbaar* aangevinkt is.
Verder geldt dat alleen gekozen kan worden uit processen die gekoppeld
zijn aan hetzelfde compartiment als die van de inlogger.

Betekenis kleurenbolletjes
--------------------------

.. _2e-kolom-van-links:

2e kolom van links
~~~~~~~~~~~~~~~~~~

-  geen kleurenbolletje: de termijnstap is wel zichtbaar, maar niet in
   gebruik (door de invulling van een bovenliggende ja/nee-stap)
-  rood: de stap is nog niet afgehandeld en de streefdatum is kleiner
   dan vandaag
-  oranje: de stap is nog niet afgehandeld en de streefdatum is groter
   dan vandaag maar kleiner of gelijk aan overmorgen
-  wit: de stap is nog niet afgehandeld en de streefdatum is groter dan
   overmorgen
-  groen: afgehandeld datum is ingevuld.

Kolom met label check
~~~~~~~~~~~~~~~~~~~~~

-  geen kleurenbolletje:

   -  OF de termijnstap is niet in gebruik (door de invulling van een
      bovenliggende ja/nee-stap)
   -  OF er zijn geen checklistitems verbonden aan de stap

-  rood: er zijn checklistitems verbonden aan de stap waarvan er
   tenminste één is afgekeurd
-  wit: er zijn checklistitems verbonden aan de stap waarvan er
   tenminste één de status onbekend heeft
-  groen: er zijn checklistitems verbonden aan de stap die alle
   goedgekeurd zijn.

Betekenis linkerkolom met aanvinkvakje
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  geen vakje zichtbaar:

   -  OF de volgende termijnstap is niet afhankelijk van een ja/nee-stap
   -  OF de stap zelf is niet in gebruik vanwege een voorliggende
      ja/nee-stap

-  aangevinkt: de volgende stap is afhankelijk van een ja/nee-stap die
   in dit geval is aangevinkt (met Ja is beantwoord)
-  leeg vakje: de volgende stap is afhankelijk van een ja/nee-stap die
   in dit geval NIET is aangevinkt (met Nee is beantwoord).

Wat gebeurt er bij verwijderen?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Van de gekozen procedure (keuze moet alleen gemaakt worden indien er
processtappen uit meer dan één procedure getoond worden) worden alle
processtappen verwijderd. De processtappen worden verwijderd inclusief
de checklistitems die waren verbonden aan de bijbehorende
termijnbewakingstappen en inclusief de checklistitems die alleen waren
verbonden aan de hoofdzaak en aan hetzelfde procedurenummer.
