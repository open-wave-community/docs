# DSO Ontvangstbevestiging sturen

Op deze pagina staat beschreven de mogelijkheid om (al dan niet automatisch) als reactie op een binnengekomen DSO verzoek en/of aanvulling op een verzoek (STAM-bericht), een ontvangstbevestigingsmail te sturen vanuit OpenWave.

De benodigde instellingen worden genoemd en de werkwijze van de programmatuur wordt beschreven: zowel voor het automatisch als het handmatig kunnen versturen van een DSO ontvangstbevestiging.

## Benodigde instellingen

Het versturen van de DSO ontvangstbevestiging vereist een aantal instellingen:

- **Mailsjablonen**: er dienen 1 of meer mailsjablonen aangemaakt te worden zoals men gewend is via tegel _Emailsjablonen_ in het beheer. Bijvoorbeeld 1 sjabloon voor de DSO initiële aanvragen (doel = Initieren, Vooroverleg of Conceptverzoek) en 1 voor de DSO aanvullingen (doel = Aanvullen). Optioneel kan er voor ieder DSO zaaktype, aparte mailsjablonen gedefinieerd worden. Dit hoeft echter niet. Men kan het sjabloon/de sjablonen definiëren zoals men gewend is. Waarbij volgende zaken goed zijn om aan te denken:

  - Indien de ontvangstbevestiging opgeslagen moet worden, kan dat door bij de mailsjabloondefinitie **Autom. upload** aan te vinken
    - Goed om te weten: vooral bij aanvullingen (indien er meer dan 1 binnenkomt en/of handmatig meerdere keren verstuurd) maar ook bij initiële ontvangstbevestiging (indien handmatig meerdere keren verstuurd) kan het zijn dat deze meerdere keren verstuurd wordt. Het is dus zaak om de documentnaam zorgvuldig te definiëren. Bijvoorbeeld door datum en/of briefnummer in de documentnaam op te nemen.
  - Bij de sjabloondefinitie kan tevens aangegeven worden of de body en het onderwerp wijzigbaar zijn voor de gebruiker tijdens opstellen van de mail
    - (**Let op alleen van toepassing bij handmatig versturen, bij automatisch versturen is de tekst van de mail nooit wijzigbaar**)
  - N.b. invulparameters kunnen niet opgegeven worden: de mail moet zonder tussenkomst van gebruiker op te stellen zijn

- **Sjabloonverwijzing bij DSO zaaktype opgeven**. Na aanmaken van de mailsjablonen zal naar deze verwezen moeten worden bij de Zaaktypedefinities (_Zaakbeheer_) waarvoor is aangegeven dat ze aan DSO verzoektypes verbonden zijn. Per zaaktypedefinitie is:
  - in veld **Ontvangstmail initieel (tbemailsjabloon.dnkey)** de dnkey van het mailsjabloon op te geven voor DSO ontvangstbevestiging op **Initiële aanvragen**.
  - in veld **Ontvangstmail aanvulling (tbemailsjabloon.dnkey)** de dnkey van het mailsjabloon op te geven voor DSO ontvangstbevestiging op **Aanvullingen**.
- Voor handmatig versturen van de DSO ontvangstbevestiging geldt dat de gebruiker het recht moet hebben voor creëren van documenten. Daarnaast moet ingesteld zijn wat de afzender van de mail is (gelijk aan overige mailfunctionaliteit in OpenWave: of de inlogger of het noreply mailadres).
- Voor automatisch versturen van DSO ontvangstbevestiging dient instelling _Sectie: DSO en Item: OntvangstBevestAutoVersturen_ aangevinkt te zijn. Daarnaast geldt dat er geen rechten controle is. Wel dient het **noreply mailadres** achterhalen te zijn: kolom _Tekst_ bij instelling _Sectie: Programma en Item: NoReplyEmailadres_ (indien niet compartiment). Voor compartiment is dat veld _tbcompartiment.dvnoreplyemailadres_.
- Indien aangegeven dat de mail opgeslagen moet worden, dan wordt na opslaan eventueel een record aangemaakt in tbcorrespondentie indien:
  - geen compartimentzaak dan indien _Getal1_ van _Sectie: Documenten Item: Documentregistratie_ de waarde 1 heeft (maakt niet uit of de instelling is aangevinkt of niet)
  - indien wel compartimentzaak dan indien _tbcompartiment.dldocregallehandmuploads_ de waarde T heeft.

**LET OP:** uiteraard moet er wel vanuit OpenWave gemaild kunnen worden. Hiervoor bestaan standaard mailinstellingen. Indien er al gemaild wordt naar de BAG en/of adviesinstanties of vanuit MaakEmail, dan zijn deze instellingen al goed ingeregeld.
Zie ook [sectie webmail](/instellen_inrichten/configuratie/sectie_web.mail.md).

## Werkwijze

### Automatisch versturen van DSO ontvangstbevestiging

Bij het verwerken van DSO STAM-berichten (aanvragen uit het DSO) kan indien zo ingesteld, automatisch een DSO ontvangstbevestigingsmail verstuurd worden naar de [Geadresseerde(n)](/probleemoplossing/programmablokken/dso_ontvangstbevestiging#geadresseerde_n.md) van het verzoek.
Dit is het geval indien:

- instelling _Sectie: DSO en Item: OntvangstBevestAutoVersturen_ aan is gevinkt
- doel van DSO STAM-bericht Initiëren, Vooroverleg, Conceptverzoek of Aanvullen is (dus niet bij Intrekken)

Zie overige instellingen/vereisten kopje: [Benodigde instellingen](/probleemoplossing/programmablokken/dso_ontvangstbevestiging#benodigde_instellingen.md).

Het automatisch versturen gebeurd zonder userinterface en is daarmee niet zichtbaar voor de gebruiker. Bij het verwerken van het STAM-bericht zal na het aanmaken van nieuwe zaak (indien Doel = Initieren, Vooroverleg of Conceptverzoek), indien bovengenoemde configuratie instelling aan staat gepoogd worden de DSO ontvangstbevestiging te versturen. Idem dito bij verwerken van STAM-bericht maar doel = Aanvullen, zal met bovengenoemde instelling gepoogd worden voor de aanvulling de DSO ontvangstbevestiging te sturen.

Bij het zaaktype van de (nieuwe) zaak zal de programmatuur het gewenste sjabloon ophalen en de mail opstellen met als onderwerp en body zoals aangegeven in het sjabloon. Indien aangegeven bij het sjabloon zal de gegenereerde mail al dan niet ook opgeslagen en eventueel geregistreerd worden.

Omdat er geen userinterface is bij het verwerken van een DSO STAM-bericht zal het ontbreken van gegevens/niet kunnen opstellen van de mail en de reden daarvoor, genoteerd worden in het beheer bij _Ontbrekende configuratieitems_. Dit is voor beheerders in te zien maar niet voor behandelaar van de zaak.

De behandelaar van de zaak kan controleren of het versturen van de DSO ontvangstbevestiging gelukt is door te kijken of de gewenste verstuurdatum gevuld is: zie uitleg kopje [Controle op versturen DSO ontvangstbevestiging](/probleemoplossing/programmablokken/dso_ontvangstbevestiging#controle_op_versturen_dso_ontvangstbevesting.md)

### Handmatig versturen van DSO ontvangstbevestiging

DSO ontvangstbevestigingen zijn door handmatige actie van de gebruiker te versturen, ongeacht het wel of niet ingesteld zijn van automatisch versturen van DSO ontvangstbevestiging. Vanzelfsprekend kan het handmatig versturen van DSO ontvangstbevestigingen alleen plaatsvinden bij DSO zaken (tbomgvergunning.dlisdso is T).

In de standaard uitlevering is er voor het mailen van de initiële ontvangstbevestiging een knop aanwezig in blok _DSO_ in het detailscherm van de zaak. Tevens is daar de datum te zien waarop de ontvangstbevestiging voor het laatst verstuurd is.

In de lijst met **DSO Aanvullingen** is er per regel (mits het doel _Aanvullen_ is) een knop zichtbaar om de ontvangstbevestiging per Aanvulling te kunnen versturen. Ook hier is een datumveld zichtbaar waarop de ontvangstbevestiging voor het laatst verstuurd is.
Deze twee knoppen roepen beiden de wizard _StuurDSOOntvangstbevestiging_ aan.

Het is mogelijk de wizard aan te roepen via een actie achter een processtap of achter een tegel. Acties achter een processtap en/of tegel dienen naar wens door de beheerder aangemaakt te worden. Zie uitgewerkte voorbeelden onder kopje **Action** bij [Termijnstappen](/instellen_inrichten/inrichting_processen/termijnstappen.md) en voorbeeld aanroep onder kopje **startWizard** bij [Actions](/instellen_inrichten/actions.md).

Na aanroepen van de wizard zal deze een ontvangstbevestigingsmail genereren en sturen naar aanvrager/gemachtigde als reactie op het binnengekomen DSO verzoekbericht.
Er zijn drie mogelijkheden qua aanroep van de wizard:

- 1. **Initieel ontvangstmail genereren en versturen (zonder sluiten processtap)**. Deze aanroep zit achter de knop in het blok DSO van de omgevingszaak en zal de ontvangstbevestiging Initieel versturen en indien geslaagd, de verstuurdatum (opnieuw) vullen met datum van versturen.
- 2. **Initieel ontvangstmail genereren en versturen met sluiten processtap**. Deze aanroep kan men instellen bij actie achter processtap en zal de ontvangstbevestiging Initieel versturen en indien geslaagd, de verstuurdatum (opnieuw) vullen met datum van versturen. Vervolgens zal de processtap waarvandaan de wizard gestart is, afgesloten worden.
- 3. **Aanvulling ontvangstmail versturen** (nooit vanuit processtap). Deze aanroep zit achter de knoppen in de lijst **DSO Aanvullingen** en zal de ontvangstbevestiging Aanvullen versturen en indien geslaagd, de verstuurdatum (opnieuw) van de aanvullingsregel vullen met datum van versturen.

De wizard toont bij start een melding als er gegevens ontbreken zoals rechtencontrole niet oké (de gebruiker moet het recht hebben voor _Creëren van documenten (tbomgrechten.dlcomgcorins)_), er geen valide dnkeymailsjabloon is opgegeven bij de zaaktypedefinitie, als er geen [Geadresseerde(n)](/probleemoplossing/programmablokken/dso_ontvangstbevestiging#geadresseerde_n.md) te bepalen is enzovoorts.
In dat geval kan de gebruiker alleen nog annuleren.

Indien de verstuurdatum al gevuld is voor de mail zal de wizard een melding tonen dat de mail al verstuurd is. De gebruiker kan in dit geval annuleren OF toch uitvoeren: dan wordt de mail nogmaals verstuurd en de verstuurdatum overschreven.

Na eventueel tonen van melding scherm, zal de wizard gelijk de mail genereren en het voorbeeld aan de gebruiker tonen. Welk mailsjabloon van toepassing is, is opgegeven bij de zaaktypedefinitie van de onderliggende omgevingszaak. Alleen indien bij het mailsjabloon zo ingesteld kan de gebruiker de body en onderwerp nog wijzigen.

Anders dan bij **Creëer email** kan de gebruiker niet zelf de contactpersoon kiezen en kunnen er ook geen bijlagen worden gekozen.
De mail wordt eventueel (alleen indien zo opgeven bij het sjabloon: geen actieve keuze) op de documentopslag geplaatst en indien zo ingesteld als geregistreerd document opgeslagen.

Na uitvoeren van de wizard kan de inlogger controleren of het versturen van de DSO ontvangstbevestiging gelukt is door te kijken of de gewenste verstuurdatum gevuld is: zie uitleg kopje [Controle op versturen DSO ontvangstbevestiging](/probleemoplossing/programmablokken/dso_ontvangstbevestiging#controle_op_versturen_dso_ontvangstbevesting.md).

## Geadresseerde(n)

De ontvanger en CC van de DSO ontvangstbevestiging kunnen niet worden gekozen maar worden als volgt bepaald door de programmatuur:

- indien er een **Gemachtigde** is (contactpersoon met rol _GEM_) met gevuld mailadres dan zal deze de ontvanger zijn
- is er geen gemachtigde maar wel een **Aanvrager** (contactpersoon met rol _AVR_) met gevuld mailadres dan zal deze de ontvanger zijn
- is er zowel een gemachtigde als een aanvrager met gevuld mailadres dan wordt de mail gestuurd naar de gemachtigde met in de CC de aanvrager
- Zijn beiden niet aanwezig/ geen mailadres gevuld dan kan de mail niet verstuurd worden

## Controle op versturen DSO ontvangstbevestiging

Ongeacht of de mail wordt opgeslagen zal voor de behandelaar van de zaak altijd te controleren zijn of de mail ook daadwerkelijk verstuurd is:

- In geval van initieel DSO verzoek zal nieuw veld **Ontvangstmail** gevuld worden in het detailscherm van de omgevingszaak.
- In geval van aanvulling DSO verzoek zal nieuw veld **Verstuurdatum Ontvangstmail** gevuld worden in de lijst van _DSO aanvullingen_ (zichtbaar in detailscherm van de omgevingszaak)
- Indien de verwachte verstuurdatum leeg blijft, dan is er dus iets misgegaan bij het versturen van de ontvangstbevestiging. In het beheer bij _Ontbrekende configuratie items_ wordt genoteerd indien de programmatuur niet de benodigde instellingen kan vinden. Daar kan men terugvinden waarom de mail niet verstuurd wordt
