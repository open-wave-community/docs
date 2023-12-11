Lijst Inspectie-overtredingen
=============================

De schermidentifier is: MDLC_geefOnrechtmatighedenOverzicht.xml.

De lijst kan worden aangeroepen vanuit het zaakportaal van Omgeving,
Handhavingen, APV/Overig, Bouw/sloop en Objectregistratie/Inrichtingen.
In dat geval worden alle overtredingen bij de hoofdzaak getoond ongeacht
het inspectietraject. De overtredingen zijn dan onderverdeeld in
openstaande en afgeronde overtredingen.

De lijst kan ook worden aangeroepen vanuit een specifiek
inspectietraject. In dat laatste geval zijn alleen de overtredingen bij
dat traject te zien.

Error
-----

Het scherm geeft een foutmelding:

-  er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie
   `Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__)
   die niet valide is
-  de inlogger moet kijkrechten hebben op de inspecties bij de
   betreffende hoofdzaak of inrichting.

Muteerrechten
-------------

Een kolom in de inspectie-overtredingenlijst kan worden gemuteerd
indien:

-  de inlogger lid is van een rechtengroep die wijzigrechten heeft op de
   inspecties van de betrokken module
-  en de bovenliggende zaak niet is geblokkeerd (zie onder aan pagina
   voor uitzondering)
-  en in de schermkolomdefinitie (beheer) is de eigenschap *lijst
   automatisch in editmode* aangevinkt
-  en de kolom heeft de tag op true staan in de schermkolomdefinitie
-  en - indien de inlogger lid is van een compartiment - dan moet het
   betreffende compartiment het zaaktype van de bovenliggende zaak
   bevatten en de gemeente waar die zaak speelt, waarbij de eigenschap
   *inclusief inspecties* is aangevinkt
-  en - indien de inlogger GEEN lid is van een compartiment,

   -  dan mag de combinatie van het zaaktype van de bovenliggende zaak
      en de gemeente waar die zaak speelt in geen enkel compartiment
      voorkomen
   -  OF, als dat wel het geval is, dan moet de eigenschap *inclusief
      inspecties* NIET aangevinkt staan

-  en de editschuif aan staat.

Bijzondere kolommen
~~~~~~~~~~~~~~~~~~~

De kolom **Opmerk.?** geeft aan of het veld *Interne Opmerking* gevuld
is of niet voor de overtreding. Het programma wijzigt zelf de waarde van
het achterliggende veld: als de interne opmerking gevuld is of wordt,
dan zal het veld aangevinkt zijn. Is de interne opmerking leeg/ wordt
deze leeggemaakt door de gebruiker dan wordt het veld uitgevinkt.

Automatisch synchroniseren Digitale checklisten
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Zie de voorwaarde hieronder bij de knop synchroniseren.

Als *Getal1* van de instelling *Sectie: KoppelingINSPTOETS en Item:
SynchroniseerOnrechtm* de waarde 1 heeft en de instelling is aangevinkt,
dan wordt het synchroniseren automatisch gedaan indien het detailscherm
van het bovenliggende inspectietraject opnieuw wordt uitgeschreven: dus
ook bij het openen.

Triggers
~~~~~~~~

**In het scherm**: dubbel klikken op een regel opent het detailscherm
van een inspectie-overtreding. Altijd enabled.

Triggers in **scherm linksonder**

-  Insertknop:

   -  Zichtbaar indien:

      -  inlogger insert-rechten heeft op de inspecties bij betreffende
         hoofdzaak of inrichting
      -  en de lijst \_wordt aangeroepen vanuit detailscherm
         inspectietraject \_ OF wordt aangeroepen vanuit tegel
         *Openstaande bezoeken* op zaak c.q. inrichtingsportaal terwijl
         er maar één inspectietraject bestaat
      -  en compartimentrecht is OK.

   -  Enabled indien de bovenliggende zaak/inrichting niet is
      geblokkeerd.

-  Deleteknop:

   -  Zichtbaar indien:

      -  inlogger verwijderrechten heeft op de inspecties bij
         betreffende hoofdzaak/inrichting en compartimentrecht is OK
      -  en de lijst \_wordt aangeroepen vanuit detailscherm
         inspectietraject \_ OF wordt aangeroepen vanuit tegel
         *Openstaande bezoeken* op zaak c.q. inrichtingsportaal terwijl
         er maar één inspectietraject bestaat.

   -  Enabled indien de bovenliggende zaak/inrichting niet is
      geblokkeerd.

-  Synchroniseer met Digitale checklisten:

   -  Zichtbaar en enabled indien:

      -  de instelling *Sectie: KoppelingINSPTOETS* en *Item:
         SynchroniseerOnrechtm* aangevinkt is
      -  en de bovenliggende zaak/inrichting niet is geblokkeerd
      -  en in tbinspecties.ddextchkldossierid of dvextchkdossier2id of
         dvextchkdossier3id is gevuld
      -  en de instelling *Sectie: KoppelingINSPTOETS*, *Item: Methode*
         en *Tekst: digitalechecklisten* aangevinkt is
      -  en bij *Sectie: KoppelingINSPTOETS* en *Item:
         Ontvangstadres_answers* de kolom *Tekst* is gevuld
      -  en bij *Sectie: KoppelingINSPTOETS* en *Item:
         Ontvangstadres_users* de kolom *Tekst* is gevuld
      -  en compartimentrecht is OK.

Uitzondering blokkering: Als de bovenliggende hoofdzaak is geblokkeerd
kunnen er toch overtredingen worden toegevoegd/verwijderd indien de
instelling *Sectie: InspectieMilieu* en *Item:
NietBlokkerenMetHoofdzaak* aangevinkt is.
