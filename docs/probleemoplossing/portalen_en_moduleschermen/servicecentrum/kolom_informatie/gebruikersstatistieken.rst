Gebruikerstatistieken
=====================

Trigger
-------

De tegel is een trigger voor een geanonimiseerde lijst waarin de
gebruikersgegevens staan van hen die die inloggen op de omgeving.

Deze lijst wordt door de programmatuur gevuld indien de instelling
*Sectie: Preinlog Item: GebruikersinformatieOpslaan* aangevinkt is. In
dat geval worden een aantal browser- en devicegegevens van de inlogger
anoniem (met one way gecrypte username) opgeslagen in de tabel
tbgebruikersinformatie opgeslagen. Deze informatie blijft 90 dagen
bestaan tenzij anders ingesteld in *Getal1* van *Sectie
Gebruikersinformatie Item: AantalDagenOpslaan*.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *Servicecentrum*
-  Kolom: *Informatie*
-  Kopregel: *Gebruikerstatistieken*
-  Actie:
   *getFlexList(SysStandardList,nil,nil,nil,beheer_vwfrmgebruikersinformatie)*
