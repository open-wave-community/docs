# Sidebar (zijbalk)

Indien de instelling *Sectie: OWB* en *Item: SidebarGebruiken* aangevinkt is, dan worden de portals niet meer als browsertabbladen getoond (tenzij… zie onderaan deze pagina), maar in een sidebar (zijbalk) gegroepeerd op portalname binnen één browsertabblad.

## Werking

Default is de zijbalk voorzien van een 'zweef-effect' (hover-effect). Dit betekent dat hij openvouwt als je er overheen veegt met de muis indien hij ingeklapt is.

![zijbalk_geopend](/img/applicatiebeheer/instellen_inrichten/zijbalk_geopend.png.md){ class="media" loading="lazy" alt="" width="400" }

Omgekeerd klapt de zijbalk in, wanneer de muis over een opengevouwen zijbalk bewogen wordt.

![zijbalk_ingeklapt_na_hoover](/img/applicatiebeheer/instellen_inrichten/zijbalk_ingeklapt_na_hoover.png.md){ class="media" loading="lazy" alt="" width="400" }

Door op het tabje met het pijltje te klikken, kun je de zijbalk volledig verbergen.

![zijbalk_lipje_pijltje](/img/applicatiebeheer/instellen_inrichten/zijbalk_lipje_pijltje.png.md){ class="media" loading="lazy" alt="" width="200" }

![zijbalk_helemaal_ingeklapt_met_pijltje](/img/applicatiebeheer/instellen_inrichten/zijbalk_helemaal_ingeklapt_met_pijltje.png.md){ class="media" loading="lazy" alt="" width="400" }

Het hover-effect kan uitgezet worden door één maal in het blauw van de opengeklapte zijbalk te klikken. Daarmee wordt de zijbalk vastgezet.

![zijbalk_vastmaken_met_klik](/img/applicatiebeheer/instellen_inrichten/zijbalk_vastmaken_met_klik.png.md){ class="media" loading="lazy" alt="" width="400" }

De zijbalk klapt dan niet meer dicht als de muis er overheen bewogen wordt, maar reageert alleen nog op het klikken op het tabje met het pijltje. De zijbalk kan weer 'losgemaakt' worden, door nogmaals op de opengevouwen zijbalk te klikken (op dezelfde manier dus als waarop je hem vastzet).

### pinSidebar

Indien de instelling *Sectie: OWB* en *Item: pinSidebar* aangevinkt is, dan zet de zijbalk zich vast aan de zijkant van het scherm.

Het uitstekende pijltje van de zijbalk zal vervangen worden door een slotje op het moment dat u op de zijbalk klikt. Nu zullen zichtbare lijst-, detail-, wizard- of portaalschermen zich aanpassen aan de nieuwe breedte van het scherm.

Na een tweede klik zal het slotje wederom een pijltje worden en zal de zijbalk weer loskomen.

### Opschriften en hint configureren

De opschriften en de hint op de zijbalk zijn als volgt te beïnvloeden via het detailscherm van de [portalnames](/docs/instellen_inrichten/portaldefinitie/portalnaam.md):

![sidebar](/img/applicatiebeheer/instellen_inrichten/sidebar.png.md)class="media" loading="lazy" alt="" width="200"

  - **ad 1: home** Per definitie het openingsportaal. Geen hint. Opschriften zijn niet aanpasbaar.
  - **ad 2: portal groepsnaam** Deze naam kan opgegeven worden in de kolom *sidebar:groepsnaam (tbportalnames.dvtablabelgroup).* Hier kan de naam van portalgroep ingegeven worden bijvoorbeeld Omgevingzaken of Handhaving of Beheer. Een aantal portalgroepen heeft geen subportals zoals beheer: zij hebben maar één element. De zaakportalen en de inrichtingen hebben wel subportals: elke geopende zaak of inrichting heeft een eigen element onder de groep. Indien de groepsnaam leeg is wordt de naam van het portal zelf gebruikt.
  - **ad 3: elementlabel** Hier staan de verschillende elementen van een portalgroep. In OpenWave zijn dat dus de zaakportalen voor Inrichtingen, Omgevingszaken, handhavingen, APV/Overige. Milieu/gebruik en Bouw/sloop. Het label opschrift kan in SQL opgegeven worden in de kolom *sidebar:Elementlabel (tbportalnames.dvtablabelquery)* bij de portalname. In de SQL kan de variabele {id} worden gebruikt die het programma dynamisch vervangt met de dnkey van de hoofdtabel van het aangeroepen portal. De SQL mag geen puntkomma's bevatten en moet beginnen met 'select' en de resultset moet bestaan uit één kolom en één rij. <wrap info>**Voorbeeld:** *select dvzaakcode from vwfrmomgvergunningen where dnkeyomgvergunning = {id}*</WRAP> Indien de query een leeg resultaat oplevert wordt de eerste regel van de portalheadertekst gebruikt.
  - **ad 4: Hint** De elementnaam van een zaak/inrichtingsportaal portaal kan hierin worden verduidelijkt. De hint kan in SQL opgegeven worden in de kolom *sidebar:Hintlabel (tbportalnames.dvtablabelhintquery)* bij de portalname. In de SQL kan met {id} een variabele worden gebruikt die het programma dynamisch vervangt met de dnkey van de hoofdtatbel van het aangeroepen portal. De SQL mag geen puntkomma's bevatten en moet beginnen met 'select' en de resultset moet bestaan uit één kolom en één rij.<wrap info> **Voorbeeld:** *select dvaanvraagnaam | | ' '| | dvobjadres | | ' '| | dvobjplaats from vwfrmomgvergunningen where dnkeyomgvergunning = {id}*</WRAP> Indien de query een leeg resultaat oplevert wordt de tekst 'Dit is de hint bij …' gevolgd door een primary key nummer, geprojecteerd.
  - **ad 5: sublijst** Het tegelopschrift van de lijst die vanuit dit portal openstaat. Deze items worden opgenomen in de zijbalk indien op het detailscherm van de portaalnamen (tegel portals op beheerportaal) het aanvinkvakje *Tegellijsten opnemen als items in sidebar* is aangevinkt. Er kan maar één lijst per portaal tegelijk openstaan.

Een portal als beheer (maar geldt ook voorde portals  #zi of #zoeken of #rapportage) kan toch twee of meer worden geopend terwijl de zijbalk aanstaat, door op de beheertegel in het openingsportaal te klikken met de controltoets ingedrukt. Dan wordt een nieuw browsertabblad geopend met het beheerportaal.

### Hoveren en IPad

*Sectie: OWB en Item: sidebarHoverIpad*.
OpenWave kijkt naar of het device waarop gewerkt wordt in OpenWave een Ipad is en naar bovenstaande instelling om te bepalen of de hoverfunctionaliteit aan-/uitgezet moet worden.
Voor optimale functionaliteit op de Ipad moet de instelling wel bestaan in de configuratie, maar uitgevinkt staan. Dan zal de zijbalk altijd of open of dicht zijn. Met het pijltje in de zijbalk is deze te openen/te sluiten.

