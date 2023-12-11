.. _testen-xml-berichten-dso--erkmaatreg:

Testen xml-berichten DSO / Erk.Maatreg
======================================

OpenWave ontvangt de DSO trigger- en verzoekberichten normaal gesproken
via de DIGI-koppelaar op het daartoe ingestelde HTTPS:POSTendpoint.

De Erkende maatregelen berichten worden door OpenWave opgevraagd door
aanroep van de RVO-services. Hier gaat het om het antwoordbericht op het
SOAP Request_vraagGegevensIndividueleInrichting.

OpenWave kan de genoemde xml-berichten testen op goede verwerking in
OpenWave zonder dat de hele keten van services operationeel is.

Testen DSO trigger of verzoekbericht
------------------------------------

Maak een (tijdelijke) tegel in het servicecentrum-portaal (onder kolom
*Acties*) met als action:

startWizard(uploadmultiplefiles,-1,,no_uploadfile;startaction;VerwerkDSOVerzoekBericht).

Wanneer de tegel wordt ingedrukt moet een trigger-of verzoekbericht
worden aangewezen. Dat moet een xml-bericht zijn:

-  waarvan de inhoud ingeklemd zit in de tags
   ``<verzoekXML></verzoekXML>`` waarbij de tag
   ``<verzoek><verzoeknummer>`` is gevuld
-  OF waarvan de inhoud ingeklemd zit in de tags
   ``<triggerbericht></triggerbericht>`` en de tag
   ``<trigger><verzoeknummer>`` is gevuld

en de inlogger moet insertrechten hebben om tbomgvergunning.

en de kolom *Tekst* van de instelling *Sectie: OWB en Item:
TussenMapUploadFiles* moet gevuld zijn met een map eindigend op
*Openwave/upload*/.

Is aan bovenstaande voorwaarden wel voldaan dat wordt dezelfde
programmatuur aangeroepen die normaal in de keten de DSO-berichten
verwerkt.

Belangrijk daarbij is dat indien:

-  de instelling *Sectie: DSO en Item: Messagelog* aangevinkt staat
-  en de instelling *Sectie: OWB en Item: MessageLog* staat aangevinkt

dat dan altijd een kaart tbmessagelog aangemaakt wordt, waarbij - indien
de verwerking niet goed gaat - in de kolom errorcode vermeld staat
waarom het bericht niet verwerkt kon worden.

Testen ErkendeMaatregel antwoordbericht
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Hier gaat het om het antwoordbericht op het SOAP
Request_vraagGegevensIndividueleInrichting. Maak een (tijdelijke) tegel
in het servicecentrum-portaal (onder kolom *Acties*) met als action:

startWizard(uploadmultiplefiles,-1,,no_uploadfile;startaction;VerwerkErkendeMaatregel).

Wanneer de tegel wordt ingedrukt moet het antwoordbericht met de erkende
maatregelen van een individuele inrichting worden aangewezen. Dat moet
een xml-bericht zijn waarin de tag
``<vraagGegevensIndividueleInrichtingResponse><inrichting><inrichtingIDInELoket>``
een gevuld waarde heeft.

Verder moet de inlogger moet insertrechten hebben om tbomgvergunning.

en moet de kolom *Tekst* van de instelling *Sectie: OWB en Item:
TussenMapUploadFiles* gevuld zijn met een map eindigend op
*Openwave/upload*.

Is aan bovenstaande voorwaarden wel voldaan dan:

-  wordt een kaart aangemaakt in tbekteverwerkeninr met de inrichtingsid
   en de systeemdatum (beheertegel *Erkende Maatregelen te verwerken RVO
   inrichtingids*)
-  wordt verder dezelfde programmatuur aangeroepen die normaal in de
   keten de erkende maatregelen van een inrichting verwerkt.

Indien:

-  de instelling *Sectie: ErkendeMaatregelen en Item: Messagelog*
   aangevinkt staat
-  en de instelling *Sectie: OWB en Item: MessageLog* staat aangevinkt

dan wordt altijd een kaart in tbmessagelog aangemaakt.

De foutmeldingen komen echter in de tabel tbmissingconfiguration
(beheertegel *Ontbrekende*
`configuratie-items </docs/instellen_inrichten/configuratie.md>`__).
Deze tabel wordt gevuld met de omissies indien het bericht niet konden
worden verwerkt vanwege ontbrekende instellingen.
