Tegel Inspecties Oorspronkelijke Zaak
=====================================

Deze tegel kan zichtbaar zijn indien de betreffende handhavingszaak
aangemaakt is als kopie van een andere zaak. Dit kopiëren gebeurt vanuit
een processtap, die daartoe is gemodelleerd: vanuit een dergelijke
processtap kan een actie uitgevoerd worden die een nieuwe zaak aanmaakt
als kopie op dezelfde locatie, waarbij contactpersonen worden
overgenomen naast (instelbare) andere kolommen (zie
`Termijnstappen </docs/instellen_inrichten/inrichting_processen/termijnstappen.md>`__
en blokje *Kopieer kolommen* bij `Aanmaken van nieuwe
zaak </docs/probleemoplossing/programmablokken/maak_nieuwe_zaak.md>`__.

Bij de nieuwe zaak in tbhandhavingen wordt de kolom
*dnkeygekopieerdezaak* automatisch gevuld met de dnkeywaarde van de zaak
waaruit wordt gekopieerd.

Bij de nieuwe aangemaakte zaak kunnen de inspecties van de
oorspronkelijke zaak via deze tegel benaderd worden indien:

-  de dnkeygekopieerdezaak gevuld is
-  en bij de definitie van het zaaktype van de nieuwe zaak is de kolom
   *Inspecties zichtbaar van oorspronkelijke zaak bij kopie*
   (tbsoorthhzaak.dlinspvangekopieerdezaak) aangevinkt.

Zo niet, dan is de tegel niet zichtbaar.

Trigger
-------

De tegel is een trigger voor het tonen van een lijst van geregistreerde
documenten die horen bij de **oorspronkelijke** zaak.

-  De tegel is alleen zichtbaar voor inlogger wanneer:

   -  deze aan hem/haar is toegekend
   -  en de evaluatie van het *SQL statement onzichtbaar* bij de
      tegeldefinitie een waarde ongelijk aan 0 oplevert.

-  Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

Probleem
--------

Het dynamische opschrift op tegels is niet zichtbaar:

-  indien foutieve queryverwijzing
-  indien query zelf niet correct (zie
   `Queries </docs/instellen_inrichten/queries.md>`__)
-  indien inlogger geen recht heeft om query uit te voeren
-  indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen)
   op de tegeldefinitie uitgevinkt is.

Tegeldefinitie
--------------

De tegel is standaard als volgt gedefinieerd (`Portal
Tegeldefinitie </docs/instellen_inrichten/portaldefinitie/portal_tegel.md>`__):

-  Portaal: *handhavingdetail*
-  Kolom: *Samenhang*
-  Kopregel: *Inspecties oorspronkelijke zaak*
-  Dynamisch tegelopschrift:
-  Actie:
   *getFlexList(tbinspecties,tbhandhavingen,{dnkeygekopieerdezaak},,H)*
-  SQL (zichtbaarheid):

.. code:: sql

   select
     case when a.dnkeygekopieerdezaak is not null
     and b.dlinspvangekopieerdezaak = 'T' then 1 else 0 end
   from tbhandhavingen a
     inner join tbsoorthhzaak b on (a.dnkeysoorthhzaak = b.dnkey)
   where a.dnkey = {id}
