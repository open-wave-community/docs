Ontbrekende SysStandardSchermen in AAR
======================================

Trigger
-------

De tegel is een trigger voor het genereren van een lijst van
schermaanroepen (lijstschermen of detailschermen of filterschermen of
insertstandardrowschermen) in tbsystandardtable en/of
tbsysstandardbutton (tegel tabellen standaardapi van het de nieuwe
beheerportaal onder de kolom scherm- en tegelbeheer) die **niet** zijn
opgenomen in de AAR. Dus die niet met implementatie en updates van
OpenWave zijn aangeleverd. Dat kan zijn omdat de schermen door een
functioneel beheerder zelf zijn gedefinieerd: in de tabel
tbscreencolumns (tegel Schermkolomdefinitie tabellen standaard-api) is
de kolom dvscreenxml in dat geval gevuld met de eigen opmaak.

In bovengenoemde controlelijst is dat zichtbaar indien de kolom
*afwijkend scherm* aangevinkt is. Er gaat dus pas iets mis indien een
regel in deze lijst is opgenomen zonder dat de kolom afwijkend scherm is
gevuld. Een reden is vaak dat de verwijzing en benaming van de
feitelijke opmaakxml-file in de AAR van elkaar verschillen in
kamelennotatie.

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
-  Kolom: *Notificaties*
-  Kopregel: *Ontbrekende sysstandard;schermen in AAR*
-  Actie: *geefFlexLijstScherm(getSysStandardAARScreenProblemList)*
