Lijst Mijn Openstaande Processtappen
====================================

Schermidentifier: MDLC_geefOpenstaandeStappenLijst.xml (indien
Vaarwegzaken dan MDLC_geefOpenstaandeStappenVaarwegLijst.xml).

Zie ook `Tegel Mijn
Procestaken </docs/probleemoplossing/portalen_en_moduleschermen/openingsportaal/tegel_mijn_procestaken.md>`__

Welke gegevens worden getoond
-----------------------------

Afhankelijke van de aanroep (4e parameter zie tegelbeschrijving) worden
OF de rijen uit vwfrmeersteprocesstapperzaak OF de rijen uit
vwfrmeerstestapperproces getoond.

Voor vaarwegzaken geldt rijen uit view
vwfrmeersteprocesstapperzaak_vaarweg OF rijen uit
vwfrmeerstestapperproces_vaarweg.

-  De rijen uit de view vwfrmeersteprocesstapperzaak, dat zijn
   processtappen van de eerste niet-afgehandelde stappen per zaak:

   -  waarbij het gaat om een actieve termijnstap (dus zichtbaar en
      enabled)
   -  en de streefdatum (dddeadline) van de stap is groter (jonger) dan
      Vandaag minus *Getal2* van de instelling *Sectie: Processen* en
      *Item: DagenTerug_StappenLijst*. (default 365)
   -  en de bovenliggende zaak niet is geblokkeerd.

-  De rijen uit de view vwfrmeerstestapperproces, dat zijn processtappen
   van de eerste niet-afgehandelde stappen **per proces** per zaak:

   -  waarbij het gaat om een actieve termijnstap (dus zichtbaar en
      enabled)
   -  en de bovenliggende zaak niet is geblokkeerd.

Boven op deze where clausules van de view is de volgende extra
restrictie van kracht afhankelijk van de vierde parameter van de
flexlist aanroep: getFlexList(OpenProcesstappen,nil,nil,1,nil).

De 4 parameter kan de waarden:

-  0 = programma filtert op de eerste stap per zaak op basis van
   vwfrmeersteprocesstapperzaak
-  1 = programma filtert op de inlogger op de kolom *voor wie* van de
   termijnbewakingstappen op basis van vwfrmeersteprocesstapperzaak (in
   *VoorWie* staat de behandelaar die aan de stap is toegekend, tenzij
   deze leeg is, dan gaat het om dossierbehandelaar c.q.
   zaakverantwoordelijke van de bovenliggende zaak). OpenWave redeneert
   hierin als volgt: indien de instelling *Sectie: Termijnbewaking Item:
   ZaakverantwBovenDossierbeh* is aangevinkt dan wordt de
   zaakverantwoordelijke gekozen. Indien deze niet is gevuld, of de stap
   is niet aangevinkt dan de actieve dossierbehandelaar
-  2 = programma filtert op de inlogger op de dossierbehandelaar van de
   bovenliggende zaak op basis van vwfrmeersteprocesstapperzaak
-  3 = programma filtert op de inlogger op de kolom *teamnaam* van de
   termijnbewakingstappen op basis van vwfrmeersteprocesstapperzaak (dat
   is het team dat aan de stap is toegekend, tenzij deze leeg is, dan
   gaat het om zaakverantwoordelijk team van de bovenliggende zaak). Een
   inlogger kan aan één of meer teams zijn toegekend
-  4 = als optie 1, maar nu geldt extra dat de stap NIET aan een team is
   toegeschreven (dus de stap zelf is niet aan een team toegekend en er
   is ook geen zaakverantwoordelijk team bij de bovenliggende zaak)
-  10 = programma filtert op de inlogger op de kolom *voor wie* van de
   termijnbewakingstappen op basis van vwfrmeerstestapperproces (in
   *VoorWie* staat de behandelaar die aan de stap is toegekend, tenzij
   deze leeg is, dan gaat het om dossierbehandelaar c.q.
   zaakverantwoordelijke van de bovenliggende zaak). OpenWave redeneert
   hierin als volgt. Indien de instelling *Sectie: Termijnbewaking Item:
   ZaakverantwBovenDossierbeh* is aangevinkt dan wordt de
   zaakverantwoordelijke gekozen. Indien deze niet is gevuld, of de stap
   is niet aangevinkt dan de actieve dossierbehandelaar
-  20 = programma filtert op de inlogger op de dossierbehandelaar van de
   bovenliggende zaak op basis van vwfrmeerstestapperproces
-  30 = programma filtert op de inlogger op de kolom *teamnaam* van de
   termijnbewakingstappen op basis van vwfrmeerstestapperpoces (dat is
   het team dat aan de stap is toegekend, tenzij deze leeg is, dan gaat
   het om zaakverantwoordelijk team van de bovenliggende zaak). Een
   inlogger kan aan één of meer teams zijn toegekend
-  40 = als optie 10, maar nu geldt extra dat de stap NIET aan een team
   is toegeschreven (dus de stap zelf is niet aan een team toegekend en
   er is ook geen zaakverantwoordelijk team bij de bovenliggende zaak).

Problemen
---------

-  De lijst is leeg of geeft maar een gedeelte van mijn procestaken:

   -  zie de criteria hierboven.

-  De lijst geeft een foutmelding:

   -  er is mogelijk een zelf gedefinieerde schermindeling gebruikt
      (Schermkolomdefinitie onder Beheer) die niet valide is.

Triggers
--------

Welke zijn van toepassing op deze lijst?

-  pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de
   instelling *Getal1* van tbinitialisatie *Sectie: Paging* en *Item:
   pagesize* (defaultwaarde = 100)
-  klikken op regel opent altijd zaakportaal van bovenliggende zaak
-  versie-informatie rechtsonder (hierop klikken en screensource =
   tbscreencolumns geeft aan of er een afwijkende schermkolommen
   definitie gebruikt wordt).

Betekenis kleurenballetjes
--------------------------

-  Eerste kolom (dvprocesgevaar):

   -  rood indien de streefdatum (dddeadline) < vandaag
   -  oranje indien vandaag + 2 (overmorgen) < = streefdatum > = vandaag
   -  wit in alle andere gevallen.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde
iconen, zie hiervoor `Sectie
OWB </docs/instellen_inrichten/configuratie/sectie_owb.md>`__.
