Lijst Verbonden aan DSO-zaak
============================

Schermidentifier: **MDLC_getVerbondenAanDsoZaakList.xml** (sysstandard).

Welke gegevens worden getoond
-----------------------------

De rijen komen uit de view vwfrmverbondenaandsozaak en bestaan uit alle
DSO-zaken met hetzelfde dnkeydsoproject als de zaak waarvandaan de lijst
wordt aangeroepen plus de zaken die via groep verbonden zijn aan deze
zaak.

Rechten
=======

De lijst kan alleen opgevraagd worden door een medewerker die lid is van
een rechtengroep met het recht om omgevingszaken te zien.

Uitleg kolommen
---------------

De lijst zal bestaan uit de volgende kolommen:

-  **DSO- of Zaaktype**:

   -  hier staat in het geval dat het om een DSO zaak gaat het DSO
      verzoektype
   -  indien het om een zaak gaat die via groep verbonden is dan toont
      de kolom het zaaktype van deze zaak.

-  **Zaaktype**: zaaktype van de zaak
-  **Activiteit(en)**:

   -  indien het om een omgevingszaak gaat en er zijn 1 of meer
      onderdelen/activiteiten aanwezig (tbtoestemmingen) dan staat hier
      een opsomming van de activiteitnamen gescheiden door ;
   -  anders, staat hier de tekst *n.v.t.*

-  **Omschrijving**: omschrijving van de zaak
-  **Status**: status van de zaak
-  **Datum afgerond**: besluitdatum van de zaak
-  **Beh.**: medewerkerscode van de actieve behandelaar van de zaak
-  **Team**: zaakverantwoordelijk team. Alleen zichtbaar indien *Getal1*
   waarde 2 of 3 heeft voor instelling *Sectie: Zaakverantwoordelijke ,
   Item: Omgeving*
-  **Zaakcode**: OpenWave zaakcode van de zaak
-  **DSO-nummer**: DSO-nummer van de zaak. Indien het niet om een
   DSO-zaak gaat dan is de waarde van deze kolom niet gevuld
-  **Vanuit DSO**: kleurbol die aangeeft of de zaak vanuit het DSO is
   binnengekomen
-  **DMS-nummer**: zaaknummer van externe zaaksysteem (indien gebruik
   wordt gemaakt van DMS)
-  **Mod.**: icoon die de module weergeeft van de zaak.

Problemen
---------

-  De lijst geeft een foutmelding:

   -  Er is mogelijk een zelf gedefinieerde schermindeling gebruikt
      (Schermkolomdefinitie onder Beheer) die niet valide is.

Triggers
--------

Welke zijn van toepassing op deze lijst?

-  pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de
   instelling *Getal1* van tbinitialisatie *Sectie: paging* en *Item:
   pagesize* (defaultwaarde = 100)
-  klikken op regel verwijst altijd door naar de achterliggende zaak
-  zoekeditbox rechtsonder: altijd aanwezig
-  versie-informatie rechtsonder (hierop klikken en screensource =
   tbscreencolumns geeft aan of er een afwijkende schermkolommen
   definitie gebruikt wordt)

Ga terug naar `Zaakportaal
Omgeving </docs/probleemoplossing/portalen_en_moduleschermen/zaakportaal_omgeving.md>`__
