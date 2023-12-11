Gebruikersinformatie
====================

Trigger
-------

De tegel is een trigger voor een lijst waarin de *Gegevens van
gebruikers* staan die inloggen op de omgeving. Deze lijst wordt door de
programmatuur gevuld.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal:
   `Beheerportaal </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal.md>`__
-  Kolom: `Tegels onder kolom
   Medewerkers </docs/probleemoplossing/portalen_en_moduleschermen/beheerportaal/tegels_onder_kolom_medewerkers.md>`__
-  Actie:
   *getFlexList(SysStandardList,nil,nil,nil,beheer_vwfrmgebruikersinformatie)*

Indien de instelling *Sectie: Preinlog en Item:
GebruikersinformatieOpslaan* aangevinkt is, worden een aantal browser-
en device gegevens van de inlogger anoniem (met one way gecrypte
username) opgeslagen in de tabel tbgebruikersinformatie.

Deze informatie blijft 90 dagen bestaan tenzij anders ingesteld in
*Getal1* van *Sectie: Gebruikersinformatie Item: AantalDagenOpslaan*.
