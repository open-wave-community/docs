Lijst Adviezen bij een zaak
===========================

De schermidentifier is: **MDLC_geefAdviezenOverzicht.xml**.

Dit scherm kan worden aangeroepen vanuit het zaakportaal van Omgeving,
Handhavingen, Bouw/sloop, Info, Milieu/gebruik en APV/Overig en Horeca.
Indien (in onderstaande voorbeelden gericht op omgevingszaken) de
aanroep (action op portaltegel, zie beheerportaal-Nieuw):

-  = *getFlexList(Tbadviezen,tbomgvergunning,{id},O,W)* dan laat de
   lijst alleen de openstaande adviezen zien die horen bij de
   betreffende omgevingszaak. Openstaande adviezen zijn adviezen met een
   lege ddadviesdatum en een lege vervaldatum (ddvervallen).
-  = *getFlexList(Tbadviezen,tbomgvergunning,{id},A,W)* dan laat de
   lijst alleen de afgehandelde adviezen zien die horen bij de
   betreffende omgevingszaak. Afgehandelde adviezen zijn adviezen met
   een gevulde ddadviesdatum OF een gevulde vervaldatum (ddvervallen).
-  = *getFlexList(Tbadviezen,tbomgvergunning,{id},,W)* dan laat de lijst
   alle adviezen zien die horen bij de betreffende omgevingszaak, dus de
   afgehandelde, openstaande en vervallen.

OpenWave kan zo ingesteld staan (zie detailscherm adviezen) dat alleen
de kolom *Dateringadvies* (dddateringadvies) zichtbaar is. OpenWave is
zo in te stellen dat bij een mutatie op die dateringkolom in dat geval
vanzelf de onzichtbare ddadviesdatum gevuld wordt met dezelfde waarde.

Error
-----

Het scherm geeft een foutmelding, indien:

-  er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie
   `Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
   die niet valide is
-  de inlogger geen kijkrechten heeft op de adviezen bij betreffende
   hoofdzaak.

Muteerrechten
-------------

Een kolom in de adviezenlijst kan worden gemuteerd indien:

-  de inlogger lid is van een rechtengroep die wijzigrechten heeft op de
   adviezen van de betrokken module
-  en de bovenliggende zaak niet is geblokkeerd
-  en in de schermkolomdefinitie (beheer) is de eigenschap *lijst
   automatisch in editmode* aangevinkt
-  en de kolom heeft de tag ``<edit>`` op true staan in de
   schermkolomdefinitie
-  en - indien de inlogger lid is van een compartiment - dan moet het
   betreffende compartiment het zaaktype van de bovenliggende zaak
   bevatten en de gemeente waar die zaak speelt
-  en - indien de inlogger GEEN lid is van een compartiment, dan mag de
   combinatie van het zaaktype van de bovenliggende zaak en de gemeente
   waar die zaak speelt in geen enkel compartiment voorkomen
-  en de editschuif aan staat.

Zichtbaarheid kolommen
----------------------

-  Voor de kolom **verantwoordelijke persoon** (**Adviesvrager**) geldt
   dat de kolom is alleen zichtbaar indien de instelling *Sectie:
   Adviezen en Item: Voorwiezichtbaar* is aangevinkt.
-  Voor de kolom **verantwoordelijk team** geldt dat de kolom alleen
   zichtbaar is indien de instelling *Sectie: Adviezen* en *Item:
   teamzichtbaar* is aangevinkt.
-  Voor de kolom **categorie** geldt dat de kolom alleen zichtbaar is
   indien de instelling *Sectie: Adviezen* en *Item: categoriezichtbaar*
   is aangevinkt.

Insert
------

De insert-wizard bevat een radiobutton met vervolg. Het vervolg kan
zijn:

-  direct de zaak afhandelen, waarmee automatisch het detailscherm van
   het advies wordt geopend na het sluiten van de wizard, waarbij
   adviesdatum c.q. datering advies al worden gevuld
-  versturen email naar adviesinstantie, waarmee automatisch de
   verstuur-email-wizard wordt geopend na het sluiten van de wizard.

De vervolg-radiobutton is NIET zichtbaar indien OpenWave zo is ingesteld
dat elke nieuwe advieszaak ook een nieuwe zaak in het externe
zaaksysteem moet worden.

De te kiezen adviesinstanties zijn gefilterd op adviesinstanties die
niet zijn toegewezen aan een gemeente plus adviesinstanties die zijn
toegewezen aan de gemeente waar de zaak onder valt. Zo kan de lijst met
te kiezen adviesinstanties per gemeente verschillen. Het toewijzen van
een adviesinstantie aan een gemeente vindt plaats in het beheerportaal
in het detailscherm van de adviesinstantie.

Indien de instelling *Sectie: Adviezen en Item: Categorieverplicht* is
aangevinkt, dan

-  moet de gebruiker een categorie kiezen bij de insertwizard opgeroepen
   met de insertknop. De gebruiker kan dan kiezen uit de categorieën die
   toegekend zijn aan de eerder aangewezen adviesinstantie
   (beheerportaal-Nieuw: Kolom Gebruikers, tegel *Adviesinstanties*). Op
   detailscherm van een adviesinstantie kunnen één of meer categorieën
   worden toegekend (tegel *Adviescategorieen* onder kolom Administratie
   van beheerportaal-Nieuw).
-  wordt bij de *Meerdere adviezen uitzetten* wizard vanzelf de tweede
   pagina opgeroepen waarbij de gebruiker ook de categorieën dient te
   vullen bij de aangevinkte adviesinstanties

Automatisch aanmaken zaak in extern zaaksysteem bij insert
----------------------------------------------------------

Als de hoofdzaak NIET valt onder een compartiment dan moet hiertoe:

-  de instelling met *Sectie: Koppeling Zaak en Item: Methode*
   aangevinkt staan. De waarde van kolom *Tekst* moet zijn: StUF-ZAKEN
   310
-  en moet de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item:
   ZaaktypeAdvies* gevuld zijn en de instelling moet aangevinkt zijn
-  en *Getal1* van *Sectie: Koppeling Zaak en Item: Zender_Organisatie*
   moet gevuld zijn met een dnkey die verwijst naar een bestaand
   contactadres in tbcontactadressen (die van de zendende organisatie
   zelf).

Indien de hoofdzaak WEL valt onder een compartiment dan:

-  moet de kolom dvdmsmethode van het betreffende compartiment gevuld
   zijn met: StUF-ZAKEN 310
-  en moet de kolom dvdmszaaktypeadvies van het betreffende compartiment
   gevuld zijn
-  en moet de kolom dnkeyorganisatie het betreffende compartiment gevuld
   zijn en deze waarde is een dnkey die verwijst naar een bestaand
   contactadres in tbcontactadressen (die van de zendende organisatie
   zelf).

Betekenis kleurenballetjes
--------------------------

Eerste kolom (vwfrmadviezen.dvkleurresultaat):

-  Zwart indien gevulde vervaldatum (ddvervallen)
-  Wit indien resultaat advies is onbekend (dladviespositief = 'N')
-  Rood indien resultaat advies is negatief (dladviespositief = 'F')
-  Oranje indien resultaat advies is positief mits (dladviespositief =
   'M')
-  Groen indien resultaat advies is positief (dladviespositief = 'T').

De tweede kolom is het aantal rappeldagen vanaf de systeemdatum tot aan
de ingevulde rappeldatum van een advies. Roodgekleurd indien negatief (=
te laat). Deze wordt alleen berekend voor adviezen waarvoor zowel de
vervaldatum als de adviesretourdatum (ddadviesdatum) en de
dateringadvies (dddateringadvies) leeg zijn.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde
iconen, zie hiervoor `Sectie
OWB <https://doc.open-wave.nl/doku.php/docs:applicatiebeheer:instellen_inrichten:configuratie:sectie_owb.md>`__.

Triggers
--------

-  dubbel klikken op een regel opent het detailscherm van een advies.
   Altijd enabled.

Triggers linksonder
~~~~~~~~~~~~~~~~~~~

-  Insertknop (alleen adviesinstanties die horen bij het compartiment
   van de inlogger):

   -  Zichtbaar indien:

      -  inlogger insert-rechten heeft op de adviezen bij betreffende
         hoofdzaak
      -  en de lijst wordt aangeroepen vanuit de tegel openstaande
         adviezen
      -  en compartimentrecht OK.

   -  Enabled indien de bovenliggende zaak niet is geblokkeerd.

-  Deleteknop:

   -  Zichtbaar indien inlogger verwijderrechten heeft op de adviezen
      bij betreffende hoofdzaak en compartimentrecht OK.
   -  Enabled indien de bovenliggende zaak niet is geblokkeerd.

-  knop **Meerdere adviezen uitzetten** (zie ook `Email vanuit
   adviesaanvraag </docs/probleemoplossing/programmablokken/e-mail_adviesinstantie.md>`__):

   -  Zichtbaar indien:

      -  de instelling *Sectie: Adviezen* en *Item: AdviesIsZaak* NIET
         is aangevinkt of niet bestaat
      -  en inlogger insert-rechten heeft op de adviezen bij betreffende
         hoofdzaak
      -  en de lijst wordt aangeroepen vanuit de tegel *Openstaande
         adviezen*
      -  en compartimentrecht OK.

   -  Enabled indien de bovenliggende zaak niet is geblokkeerd.
   -  De gebruiker kan kiezen uit de lijst met niet vervallen
      adviesinstanties waarbij geldt dat indien *Getal1* van de
      instelling *Sectie: Adviezen Item: MultiSelect* de waarde 1 heeft
      (default), dan wordt de rij opgebouwd met alleen die instanties
      die nog niet voorkomen in de adviezenlijst. Bij *Getal1* = 2
      worden ook bestaande opgenomen. Voor beide geldt dat de
      adviesinstanties horen bij hetzelfde compartiment als die van de
      inlogger. Ook kan er net als bij enkelvoudig advies aanvragen
      alleen gekozen worden uit adviesinstanties behorende bij de
      gemeente waar de zaak onder valt en adviesinstanties die niet
      gekoppeld zijn aan een gemeente.
