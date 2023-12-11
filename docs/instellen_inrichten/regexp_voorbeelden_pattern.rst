Regexp voorbeelden pattern
==========================

Invoer in editboxen van wavetype string/timefloat kan met het attribuut
pattern worden gereguleerd (schermkolomdefinitie: de tag pattern). In
dit attribuut pattern kan men een regexpressie (regexp) opgeven die
bepaalt aan welk patroon de invoer waarde getoetst zal worden voor de
schermkolom. Voor mogelijkheden van regexp (javascript) zie o.a.
http://www.w3schools.com/jsref/jsref_obj_regexp.asp.

Een prettige testsite is https://regex101.com.

Hieronder een aantal voorbeelden:

\| regexp \| Omschrijving \| \|
-------------------------------------------------------- \|
--------------------------------------------------------------------------------------------------------------------------------------
\| --------------- \|
-------------------------------------------------------------------------------------------
\| \| ^(\\d{4})$ \| Exact 4 cijfers \| \| ^(\\d{1,4})$ \| 1 tot 4
cijfers \| \| ^(\\d{1,2}(.)\\d{1}) \| \| \\d{1,2}$ \| max 2 cijfers met
1 decimaal \| \| ^(\\d{1,9}(.\\d{0,2})?)$ \| maximaal 9 cijfers en
optioneel 2 decimalen \| \| ^-?\\d+([,.]\\d{2})?$ \| Bedrag ,met 0 of 2
decimalen en een punt of komma als decimaalscheidingteken \| \|
^(\\D{1,4})$ \| 1 tot 4 karakters, maar geen cijfers \| \| ^(.{1,8})$ \|
1 tot 8 karakters of spaties \| \| ^(\\w{1,8})$ \| 1 tot 8 alfanumerieke
karakters of underscores, geen spaties \| \| ^[\\w\\S\\s]{0,500}$ \| 1
tot 500 alfanumerieke of niet-alfanumerieke karakters of harde returns,
tabs , linefeeds en carriage returns \| \| ^([abc]{1})$ \| alleen de
letter a of b of c \| \| ^([0-9A-Za-z-]{1,100})$ \| alleen letters of
cijfers of een hyphen. Niet leeg en max 100 tekens \| \| ^([^\\\\
\_/]{1,100})$ \| Alles behalve een backslash, spatie of slash. Niet keeg
en max 100 tekens (let op 4 backslasjes nodig om een backslash uut te
sluiten) \| \| ^([abc]{3})$ \| elke combinatie van de letters a b c met
exacte lengte 3 met doublures \| \| ^([abc]{1,3})$ \| elke combinatie
van de letters a b c met maximum lengte 3 metdoublures \| \| ^(a?b?c?)$
\| combinatie van de letters a b c zonder doublures in opgegeven
volgorde \| \| ^([ABCD]{1}[1234]{1})$ \| 2 karakters, de eerste keuze
uit ABCD, de twee keuze uit 1234 \| \| ^([123456789]{1}\\d{3}\\
[ABCDEFGHIJKLMNOPQRSTUVWXYZ]{2})$ \| nederlandse postcode (let op:tussen
d{3}\\ en [ABC staat een spatie) \| \| ^(\\d{1,2}(:)\\d{1,2})$ \| 1 tot
2 cijfers, dan een dubbelepunt, gevolgd door 1 tot 2 cijfers \| \|
^(\\d{1,2}(: \| , \| .){1}\\d{1,2})$ \| 1 tot 2 cijfers, dan een
dubbelepunt of een komma of een punt, gevolgd door 1 tot 2 cijfers \| \|
^([^;]{1,150})$ \| 1 tot 150 karakters of spaties, alles behalve de
puntkomma \| \| ^[\\x00-\\x7F\\xA0-\\xFF€Š‚ƒ„…†‡ˆ‰Š‹ŒŽ‘’“”•–—~™š›œžŸ]*$
\| Alleen karakters die voorkomen in de WIN1252-karakterset. Geen
controle op maximaal aantal karakters en leeg is ook toegestaan. \|
