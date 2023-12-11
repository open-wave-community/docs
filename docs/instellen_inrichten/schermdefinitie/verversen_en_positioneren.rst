Verversen en Positioneren
=========================

Dit hoofdstuk gaat over het instellen van verversen en positioneren in
de
`Scherm(kolom)definitie </docs/instellen_inrichten/schermdefinitie.md>`__

Verversen Detailscherm
----------------------

Een detailscherm wordt in zijn geheel automatisch ververst:

-  na wijzigen van een kolom met eigenschap refresh = true
-  na het uitvoeren van action bij een knop met eigenschap refresh=
   true. Echter, indien de action een startwizard betreft die
   geannuleerd is, dan wordt het scherm NIET gerefreshed.

Verversen Lijstscherm
---------------------

Een lijst wordt in zijn geheel automatisch ververst indien:

-  binnen de lijst een cel wordt gewijzigd met de eigenschap refresh =
   true
-  bij herwonnen focus na sluiten detailscherm waarin tenminste één
   kolom is gewijzigd
-  bij herwonnen focus na sluiten detailscherm waarin een - niet
   geannuleerde - startwizard is uitgevoerd
-  bij herwonnen focus na uitvoeren action vanuit de lijst bij een knop
   met eigenschap refresh = true. Echter, indien de action een
   startwizard betreft die geannuleerd is, dan wordt het scherm NIET
   gerefreshed.

Van de lijst wordt alleen de actieve regel ververst indien:

-  binnen de lijst een cel wordt gewijzigd met eigenschap refreshregel =
   true
-  bij herwonnen focus na uitvoeren action vanuit de lijst bij een knop
   met eigenschap refreshregel = true. Echter, indien de action een
   startwizard betreft die geannuleerd is, dan wordt de regel NIET
   gerefreshed.

Verversen tegels op Portaalscherm
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Een portaalscherm wordt nooit automatisch ververst bij herwonnen focus
met uitzondering van de tegels met eigenschap
tbportaltiles.dlaltijdrefreshen = true (zie beheertegel *Portal*).
Daarnaast zijn er twee velden die invloed kunnen hebben op de manier
waarop tegels ververst worden bij herwonnen focus:

-  *Actief* (dlenabled)
-  *SQL tegel onzichtbaar indien result = 0* (dvquery)

Verschillende combinaties zijn mogelijk bij het inrichten van deze drie
velden. Dit leidt tot vier verschillende situaties:

\| Situatie 1 \|||\| \| Item \| Kolom \| Status \| Omschrijving \|
\|---\|---\|---\|---\|---\| \|Actief\| Aanvinkvakje\| True\| Indien
aangevinkt dan zal de tegel actief getoond worden en te openen zijn\|
\|SQL tegel onzichtbaar indien result = 0\| Tekst\| Gevuld|Indien gevuld
met een query en de query geeft 0 als resultaat, dan zal de tegel niet
te zien zijn in het portaal. Indien de query 2 geeft, dan zal de tegel
te zien zijn in het portaal, maar niet actief zijn. In alle andere
gevallen zal de tegel actief getoond worden\| \|Altijd verversen\|
Aanvinkvakje\| True\| Indien aangevinkt dan zullen na het sluiten van
een detail- of lijstscherm het *tegelopschrift, actief, visibility* en
de *actie* opnieuw berekend worden\|

\| Situatie 2 \|||\| \| Item \| Kolom \| Status \| Omschrijving \|
\|---\|---\|---\|---\|---\| \|Actief\| Aanvinkvakje\| True\| Indien
aangevinkt dan zal de tegel actief getoond worden en te openen zijn\|
\|SQL tegel onzichtbaar indien result = 0\| Tekst\| Gevuld|Indien gevuld
met een query en de query geeft 0 als resultaat, dan zal de tegel niet
te zien zijn in het portaal. Indien de query 2 geeft, dan zal de tegel
te zien zijn in het portaal, maar niet actief zijn. In alle andere
gevallen zal de tegel actief getoond worden\| \|Altijd verversen\|
Aanvinkvakje\| False\| Indien uitgevinkt dan zal er na het sluiten van
een detail- of lijstscherm niets van de tegel ververst worden. Een
handmatige zijbalk-verversactie is dan nodig\|

\| Situatie 3 \|||\| \| Item \| Kolom \| Status \| Omschrijving \|
\|---\|---\|---\|---\|---\| \|Actief\| Aanvinkvakje\| True\| Indien
aangevinkt dan zal de tegel actief getoond worden en te openen zijn\|
\|SQL tegel onzichtbaar indien result = 0\| Tekst\| Leeg|Als er geen
query opgegeven is dan zal er geen berekening nodig zijn en is de tegel
altijd zichtbaar\| \|Altijd verversen\| Aanvinkvakje\| True\| Indien
aangevinkt dan zullen na het sluiten van een detail- of lijstscherm het
*tegelopschrift* en de *actie* opnieuw berekend worden\|

\| Situatie 4 \|||\| \| Item \| Kolom \| Status \| Omschrijving \|
\|---\|---\|---\|---\|---\| \|Actief\| Aanvinkvakje\| False\| Indien
uitgevinkt zal de tegel uitgegrijsd getoond worden en niet te openen
zijn\| \|SQL tegel onzichtbaar indien result = 0\| Tekst\| Gevuld|Indien
gevuld met een query en de query geeft 0 als resultaat, dan zal de tegel
niet te zien zijn in het portaal. In alle andere gevallen zal de tegel
uitgegrijsd getoond worden\| \|Altijd verversen\| Aanvinkvakje\| True\|
Indien aangevinkt dan zal na het sluiten van een detail- of lijstscherm
het *tegelopschrift* en de *visibility* van de tegel ververst worden\|

Positioneren in lijst
~~~~~~~~~~~~~~~~~~~~~

Dit speelt na een insert of een delete of bij terugkeer focus na
wijziging in detail (kolomwijziging of uitgevoerde action).

Positioneren na delete
^^^^^^^^^^^^^^^^^^^^^^

De lijst wordt opnieuw uitgeschreven conform:

-  de instructies van de betreffende API
-  + de op dat moment geldende extra filter en/of zoek-instellingen
-  + de op dat moment geldende sorteervolgorde
-  + de op dat moment geldende pagina van paging

Er is GEEN actieve regel.

Positioneren na wijziging in detail
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

De lijst wordt opnieuw uitgeschreven conform:

-  de instructies van de betreffende API
-  + de op dat moment geldende extra filter en/of zoek-instellingen
-  + de op dat moment geldende sorteervolgorde
-  + de op dat moment geldende pagina van paging

Indien de actieve kaart na de wijziging:

-  voldoet aan filter/zoek en paging-pagina dan staat de focus op de
   gewijzigde kaart (regel is geel). OpenWave scrollt zo nodig (binnen
   het domein) net zo lang tot de actieve regel ook in beeld is - zo
   mogelijk – gecentreerd
-  niet voldoet aan filter/zoek en paging-pagina dan GEEN actieve regel.

Positioneren na insert
^^^^^^^^^^^^^^^^^^^^^^

De lijst wordt opnieuw uitgeschreven conform:

-  de instructies van de betreffende API
-  + de op dat moment geldende extra filter en/of zoek-instellingen
-  + de op dat moment geldende sorteervolgorde
-  + de op dat moment geldende pagina van paging

Indien de nieuwe kaart na de wijziging:

-  voldoet aan filter/zoek en paging-pagina dan staat de focus op de
   Nieuwe kaart (regel is geel). OpenWave scrollt zo nodig (binnen het
   domein) net zo lang tot de nieuwe regel ook in beeld is: liefst –
   indien mogelijk – gecentreerd
-  niet voldoet aan filter/zoek en paging-pagina dan blijft de actieve
   regel (gele) dezelfde als waar het programma op stond voordat de
   insert werd gedaan.

Positioneren na zoeken en/of filtersetting
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

De lijst wordt opnieuw uitgeschreven conform:

-  de instructies van de betreffende API
-  + de op dat moment geldende extra filter en/of zoek-instellingen
-  + de op dat moment geldende sorteervolgorde
-  paging – indien van toepassing - wordt altijd pagina 1

De eerste regel wordt de actieve gele regel.
