Sectie DocumentRegistreren
==========================

Hieronder de instellingen uit de
`configuratietabel </docs/instellen_inrichten/configuratie.md>`__
(tbinitialisatie) van de *Sectie: DocumentRegistreren* gerangschikt op
item.

`Lijst Geregistreerde Documenten bij een
zaak </docs/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/lijst_geregistreerde_documenten_bij_zaak.md>`__

Items Configuratietabel
-----------------------

+--------------------------+--------------+--------------------------+
| Item                     | Kolom        | Omschrijving             |
+==========================+==============+==========================+
| All                      | Aanvinkvakje | Indien aangevinkt dan    |
| eGeselecteerdeSWFUploads |              | kunnen de geselecteerde  |
|                          |              | documenten in de         |
|                          |              | SWF-documentenlijst (via |
|                          |              | detailscherm van de      |
|                          |              | SWF-ruimte) worden       |
|                          |              | doorgezet naar de        |
|                          |              | documentopslag en worden |
|                          |              | de documenten            |
|                          |              | geregistreerd in         |
|                          |              | tbcorrespondentie. Bij   |
|                          |              | een compartiment wordt   |
|                          |              | hiertoe gekeken naar de  |
|                          |              | kolom                    |
|                          |              | tbcompartiment.dldocre   |
|                          |              | gallegeselectswfuploads. |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien de waarde 1 dan   |
|                          |              | wordt het document met   |
|                          |              | definitief = (N)ee       |
|                          |              | geregistreerd, anders    |
|                          |              | met (J)a.                |
+--------------------------+--------------+--------------------------+
| AlleHandmatigeUploads    | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | worden alle handmatige   |
|                          |              | uploads bij zaken die    |
|                          |              | NIET onder een           |
|                          |              | compartiment vallen      |
|                          |              | automatisch              |
|                          |              | geregistreerd in         |
|                          |              | tbcorrespondentie (het   |
|                          |              | automatisch registreren  |
|                          |              | van documenten die met   |
|                          |              | creerDocument worden     |
|                          |              | gemaakt bij een          |
|                          |              | NIET-compartimentszaak)  |
|                          |              | op basis van een         |
|                          |              | sjabloon is afhankelijk  |
|                          |              | of de kolom *Getal1* van |
|                          |              | instelling *Sectie:      |
|                          |              | Documenten Item:         |
|                          |              | Documentregistratie* de  |
|                          |              | waarde 1 heeft. Bij een  |
|                          |              | compartiment wordt       |
|                          |              | hiertoe gekeken naar de  |
|                          |              | kolom                    |
|                          |              | tbcompartiment.d         |
|                          |              | ldocregallehandmuploads. |
+--------------------------+--------------+--------------------------+
| AlleOLODSOUploads        | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | worden alle automatische |
|                          |              | document-uploads vanuit  |
|                          |              | OLO of DSO voor          |
|                          |              | NIET-compartimentszaken  |
|                          |              | automatisch              |
|                          |              | geregistreerd in         |
|                          |              | tbcorrespondentie. Bij   |
|                          |              | een compartiment wordt   |
|                          |              | hiertoe gekeken naar de  |
|                          |              | kolom                    |
|                          |              | tbcompartiment.d         |
|                          |              | ldocregalleolodsouploads |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien de waarde 1 dan   |
|                          |              | wordt het document met   |
|                          |              | definitief = (N)ee       |
|                          |              | geregistreerd, anders    |
|                          |              | met (J)a.                |
+--------------------------+--------------+--------------------------+
| BestaandeRe              | Aanvinkvakje | Indien aangevinkt en er  |
| gNegerenBijUploadPostfix |              | wordt een upload gedaan  |
|                          |              | van een document naar    |
|                          |              | fileshare waarbij dat    |
|                          |              | document met een postfix |
|                          |              | (n) wordt opgeslagen     |
|                          |              | (zie instelling *Getal1* |
|                          |              | = 1 van *Sectie:         |
|                          |              | Documenten en Item:      |
|                          |              | OphalenViaFileserver*)   |
|                          |              | en er blijkt een         |
|                          |              | geregistreerde           |
|                          |              | documentkaart te zijn    |
|                          |              | onder de oorspronkelijke |
|                          |              | naam (dus in             |
|                          |              | tbcorrespondentie) bij   |
|                          |              | de betreffende zaak, dan |
|                          |              | wordt die geregistreerde |
|                          |              | documentkaart NIET       |
|                          |              | bijgewerkt. Anders dus   |
|                          |              | wel.                     |
+--------------------------+--------------+--------------------------+
| BijlagenAlleenDefinitief | Aanvinkvakje | Indien aangevinkt kunnen |
|                          |              | alleen geregistreerde    |
|                          |              | documenten met de        |
|                          |              | eigenschap dvdefinitief  |
|                          |              | = J worden aangewezen    |
|                          |              | als bijlage bij een      |
|                          |              | geregistreerd document.  |
+--------------------------+--------------+--------------------------+
| ContactadresWijzigbaar   | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | in het detailscherm van  |
|                          |              | een geregistreerd        |
|                          |              | document de              |
|                          |              | dropdownkolom *uitgaande |
|                          |              | brief persoon*           |
|                          |              | muteerbaar met een       |
|                          |              | keuzelijst van           |
|                          |              | contactadressen die aan  |
|                          |              | de hoofdzaak verbonden   |
|                          |              | zijn.                    |
+--------------------------+--------------+--------------------------+
| DdOntvangstdatum         | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | kan een aangewezen       |
|                          |              | document uit de lijst    |
|                          |              | *alle documenten*        |
|                          |              | geregistreerd worden     |
|                          |              | waarbij een waarde voor  |
|                          |              | de ontvangstdatum kan    |
|                          |              | worden opgegeven (True   |
|                          |              | of False). Indien        |
|                          |              | AlleHandmatigeUploads    |
|                          |              | aangevinkt dan zal bij   |
|                          |              | handmatig uploaden van   |
|                          |              | een document ook de      |
|                          |              | ontvangstdatum moeten    |
|                          |              | worden opgegeven.        |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien bij *Getal1* de   |
|                          |              | waarde 1 is gevuld, dan  |
|                          |              | is het veld default      |
|                          |              | gevuld met de            |
|                          |              | systeemdatum.            |
+--------------------------+--------------+--------------------------+
|                          | Getal2       | Indien bij *Getal2* de   |
|                          |              | waarde 1 is gevuld, dan  |
|                          |              | is het niet verplicht om |
|                          |              | de ontvangstdatum te     |
|                          |              | vullen. Indien het leeg  |
|                          |              | is of een andere waarde  |
|                          |              | dan 1 heeft, dan is het  |
|                          |              | WEL verplicht deze te    |
|                          |              | vullen bij de upload van |
|                          |              | een document als         |
|                          |              | AlleHandmatigeUploads is |
|                          |              | aangevinkt.              |
+--------------------------+--------------+--------------------------+
| DlNaarBevoegdGezag       | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | kan een aangewezen       |
|                          |              | document uit de lijst    |
|                          |              | *alle documenten*        |
|                          |              | geregistreerd worden     |
|                          |              | waarbij een waarde voor  |
|                          |              | NaarBevoegdGezag kan     |
|                          |              | worden opgegeven (True   |
|                          |              | of False). De kolom      |
|                          |              | tbcorrespond             |
|                          |              | entie.dlmaarbevoegdgezag |
|                          |              | heeft echter geen        |
|                          |              | functie meer in de       |
|                          |              | programmatuur van        |
|                          |              | Openwave sinds versie    |
|                          |              | 1.21.                    |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | In *Getal1* kan de       |
|                          |              | default waarde voor      |
|                          |              | NaarBevoegdGezag bij     |
|                          |              | registratie worden       |
|                          |              | opgegeven: 1 = True en   |
|                          |              | anders False.            |
+--------------------------+--------------+--------------------------+
| DlNaarRegOrg             | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | kan een aangewezen       |
|                          |              | document uit de lijst    |
|                          |              | *alle documenten*        |
|                          |              | geregistreerd worden     |
|                          |              | waarbij een waarde voor  |
|                          |              | NaarRegOrg kan worden    |
|                          |              | opgegeven (True of       |
|                          |              | False). De kolom         |
|                          |              | tbcorr                   |
|                          |              | espondentie.dlmaarregorg |
|                          |              | heeft echter geen        |
|                          |              | functie meer in de       |
|                          |              | programmatuur van        |
|                          |              | Openwave sinds versie    |
|                          |              | 1.21.                    |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | In *Getal1* kan de       |
|                          |              | default waarde voor de   |
|                          |              | NaarRegOrg (Regionale    |
|                          |              | Organisatie) bij         |
|                          |              | registratie worden       |
|                          |              | opgegeven: 1 = True en   |
|                          |              | anders False.            |
+--------------------------+--------------+--------------------------+
| Documentfase             | Aanvinkvakje | Indien aangevinkt wordt  |
|                          |              | de kolom Fase met        |
|                          |              | keuzelijst zichtbaar in  |
|                          |              | het detailscherm van een |
|                          |              | geregistreerd document   |
|                          |              | en in de lijst           |
|                          |              | geregistreerde           |
|                          |              | documenten. In het       |
|                          |              | lijstscherm verschijnt   |
|                          |              | eveneens de meerkeuze    |
|                          |              | filter genaamd Fase. In  |
|                          |              | de keuzelijstjes en in   |
|                          |              | de filter verschijnen de |
|                          |              | fasen die zijn opgegeven |
|                          |              | onder de tegel           |
|                          |              | *Documentfase* in het    |
|                          |              | Zaakbeheer. Ook          |
|                          |              | verschijnt de            |
|                          |              | documentfase in de       |
|                          |              | uploadwizard voor        |
|                          |              | documenten.              |
+--------------------------+--------------+--------------------------+
| DvDocrichting            | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | kan een aangewezen       |
|                          |              | document uit de lijst    |
|                          |              | *alle documenten*        |
|                          |              | geregistreerd worden     |
|                          |              | waarbij een waarde voor  |
|                          |              | de document richting kan |
|                          |              | worden opgegeven. Indien |
|                          |              | AlleHandmatigeUploads    |
|                          |              | aangevinkt dan zal bij   |
|                          |              | handmatig uploaden van   |
|                          |              | een document ook de      |
|                          |              | richting moeten worden   |
|                          |              | opgegeven.               |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | In *Getal1* kan de de    |
|                          |              | default waarde voor de   |
|                          |              | documentrichting bij     |
|                          |              | registratie worden       |
|                          |              | opgegeven: 1 = Uitgaand, |
|                          |              | 2 = Binnenkomend en 3 is |
|                          |              | Intern.                  |
+--------------------------+--------------+--------------------------+
| DvDocType                | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | kan een aangewezen       |
|                          |              | document uit de lijst    |
|                          |              | *alle documenten*        |
|                          |              | geregistreerd worden     |
|                          |              | waarbij een waarde voor  |
|                          |              | het documenttype kan     |
|                          |              | worden opgegeven. Indien |
|                          |              | AlleHandmatigeUploads    |
|                          |              | aangevinkt dan zal bij   |
|                          |              | handmatig uploaden van   |
|                          |              | een document ook het     |
|                          |              | documenttype moeten      |
|                          |              | worden opgegeven.        |
+--------------------------+--------------+--------------------------+
|                          | Tekst        | In *Tekst* kan de de     |
|                          |              | default waarde voor      |
|                          |              | documenttype bij         |
|                          |              | handmatig registreren    |
|                          |              | van de documenten worden |
|                          |              | opgegeven: De tekst moet |
|                          |              | wel voorkomen in de      |
|                          |              | beheertabel              |
|                          |              | tbdocumenttype (kolom    |
|                          |              | dvdoctype).              |
+--------------------------+--------------+--------------------------+
| DvOmschrijving           | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | kan een aangewezen       |
|                          |              | document uit de lijst    |
|                          |              | *alle documenten*        |
|                          |              | geregistreerd worden     |
|                          |              | waarbij een waarde voor  |
|                          |              | de omschrijving kan      |
|                          |              | worden opgegeven. Indien |
|                          |              | AlleHandmatigeUploads    |
|                          |              | aangevinkt dan zal bij   |
|                          |              | handmatig uploaden van   |
|                          |              | een document ook de      |
|                          |              | omschrijving moeten      |
|                          |              | worden opgegeven.        |
+--------------------------+--------------+--------------------------+
| DvStatus                 | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | kan een aangewezen       |
|                          |              | document uit de lijst    |
|                          |              | *alle documenten*        |
|                          |              | geregistreerd worden     |
|                          |              | waarbij een waarde voor  |
|                          |              | de status (definitief    |
|                          |              | ja/nee)kan worden        |
|                          |              | opgegeven. Indien        |
|                          |              | AlleHandmatigeUploads    |
|                          |              | aangevinkt dan zal bij   |
|                          |              | handmatig uploaden van   |
|                          |              | een document ook de      |
|                          |              | status moeten worden     |
|                          |              | opgegeven.               |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | In *Getal1* kan de de    |
|                          |              | default waarde voor de   |
|                          |              | status bij registratie   |
|                          |              | worden opgegeven: 1 =    |
|                          |              | Niet definitief, 2 =     |
|                          |              | Definitief.              |
+--------------------------+--------------+--------------------------+
| DvVertrouwelijkheid      | Aanvinkvakje | Indien aangevinkt dan    |
|                          |              | kan een aangewezen       |
|                          |              | document uit de lijst    |
|                          |              | *alle documenten*        |
|                          |              | geregistreerd worden     |
|                          |              | waarbij een waarde voor  |
|                          |              | de vertrouwelijkheid kan |
|                          |              | worden opgegeven uit de  |
|                          |              | beheertabel              |
|                          |              | tbvertrouwelijkheid.     |
|                          |              | Indien                   |
|                          |              | AlleHandmatigeUploads    |
|                          |              | aangevinkt dan zal bij   |
|                          |              | handmatig uploaden van   |
|                          |              | een document ook de      |
|                          |              | vertrouwelijkheid moeten |
|                          |              | worden opgegeven.        |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | In *Getal1* kan de de    |
|                          |              | default waarde voor de   |
|                          |              | vertrouwelijkheid bij    |
|                          |              | registratie worden       |
|                          |              | opgegeven: In getal 1    |
|                          |              | moet verwezen worden     |
|                          |              | naar een valide dnkey    |
|                          |              | van de beheertabel       |
|                          |              | tbvertrouwelijkheid.     |
+--------------------------+--------------+--------------------------+
| Emailccalsbcc            | Aanvinkvakje | Indien aangevinkt dan is |
|                          |              | de defaultwaarde van de  |
|                          |              | kolom dlbcc bij een      |
|                          |              | nieuwe cc/bcc bij een    |
|                          |              | geregistreerd document   |
|                          |              | (emailverzending) T: dus |
|                          |              | het vakje onder de kolom |
|                          |              | bcc is aangevinkt.       |
+--------------------------+--------------+--------------------------+
| I                        | Aanvinkvakje | Indien aangevinkt dan    |
| nrichtingcontactpersonen |              | kan de gebruiker bij het |
|                          |              | kiezen van cc's bij een  |
|                          |              | geregistreerd document   |
|                          |              | (emailverzending) ook    |
|                          |              | putten uit de            |
|                          |              | contactpersonen van de   |
|                          |              | inrichting die aan de    |
|                          |              | hoofdzaak is gelinkt.    |
+--------------------------+--------------+--------------------------+
| Ins                      | Tekst        | Indien de waarde H zal   |
| pectiebijZowelOmgEnHandh |              | bij het registreren van  |
|                          |              | een (automatisch)        |
|                          |              | geüpload document bij    |
|                          |              | een inspectietraject,    |
|                          |              | dat zowel gekoppeld is   |
|                          |              | aan een omgevingszaak    |
|                          |              | als aan handhavingzaak,  |
|                          |              | in de registratie        |
|                          |              | (tbcorrespondentie) de   |
|                          |              | dnkey van de             |
|                          |              | handhavingzaak worden    |
|                          |              | gevuld en anders die van |
|                          |              | de omgevingszaak.        |
+--------------------------+--------------+--------------------------+
| Maxgrootteemail          | Getal1       | In *Getal1* kan de       |
|                          |              | maximale grootte         |
|                          |              | opgegeven worden van de  |
|                          |              | optelling in megabytes   |
|                          |              | van de bijlages die      |
|                          |              | meegestuurd worden       |
|                          |              | vanuit het verzenden van |
|                          |              | een email vanuit de      |
|                          |              | detailpagina van een     |
|                          |              | geregistreerd document.  |
+--------------------------+--------------+--------------------------+
| KnopMaakPDFZichtbaar     | Aanvinkvakje | Indien aangevinkt en de  |
|                          |              | extensie van het         |
|                          |              | geregistreerde document  |
|                          |              | voldoet en het document  |
|                          |              | bevindt zich op de       |
|                          |              | server (dus niet lokaal) |
|                          |              | en de bovenliggende zaak |
|                          |              | is niet geblokkeerd, dan |
|                          |              | is de knop *maakPDF*     |
|                          |              | zichtbaar.               |
+--------------------------+--------------+--------------------------+
|                          | Getal1       | Indien de waarde 1 (en   |
|                          |              | aangevinkt) zal de knop  |
|                          |              | *MaakPDF* toch           |
|                          |              | onzichtbaar zijn indien  |
|                          |              | het geregistreerde       |
|                          |              | document digitaal moet   |
|                          |              | worden ondertekend       |
|                          |              | (tbcorrespondent         |
|                          |              | ie.dlmoetdigondertekenen |
|                          |              | = T) en de instelling    |
|                          |              | Item:                    |
|                          |              | *                        |
|                          |              | MaakPDFbijOndertekening* |
|                          |              | aangevinkt is.           |
+--------------------------+--------------+--------------------------+
| MaakPDFbijOndertekening  | Aanvinkvakje | Indien aangevinkt zal    |
|                          |              | bij het digitaal         |
|                          |              | ondertekenen van een     |
|                          |              | geregistreerd document   |
|                          |              | dat zich bevindt op de   |
|                          |              | server (dus niet lokaal) |
|                          |              | dat document omgezet     |
|                          |              | worden naar PDF.         |
+--------------------------+--------------+--------------------------+
| MailAlleenPdf            | Aanvinkvakje | Indien aangevinkt zal    |
|                          |              | het programma bij het    |
|                          |              | versturen per mail van   |
|                          |              | document en bijlagen     |
|                          |              | controleren of alle      |
|                          |              | documenten wel het       |
|                          |              | formaat PDF hebben.      |
+--------------------------+--------------+--------------------------+
| MailOokOpslaanInCorresp  | Aanvinkvakje | Indien aangevinkt worden |
|                          |              | de mails die gegenereerd |
|                          |              | worden vanuit            |
|                          |              | geregistreerde           |
|                          |              | documenten naar          |
|                          |              | aanvrager en cc's zelf   |
|                          |              | ook opgeslagen als       |
|                          |              | geregistreerd document.  |
+--------------------------+--------------+--------------------------+
| Regeneratie              | Aanvinkvakje | Indien aangevinkt en de  |
|                          |              | gebruiker heeft creëer   |
|                          |              | documentrechten en een   |
|                          |              | geregistreerd document   |
|                          |              | is nog niet              |
|                          |              | definitief/verstuurd en  |
|                          |              | het geregistreerde       |
|                          |              | document is opgeslagen   |
|                          |              | in het DMS, dan is een   |
|                          |              | regeneratieknop          |
|                          |              | zichtbaar op het         |
|                          |              | detailscherm             |
|                          |              | geregistreerde           |
|                          |              | documenten, waarmee een  |
|                          |              | opgeslagen documenten    |
|                          |              | kan worden overschreven  |
|                          |              | met een nieuw            |
|                          |              | gegenereerd document op  |
|                          |              | basis van het            |
|                          |              | oorspronkelijke          |
|                          |              | sjabloon.                |
+--------------------------+--------------+--------------------------+
| S                        | Tekst        | Deze tekst wordt         |
| tandaardEmailTekstAanhef |              | gebruikt voor het        |
|                          |              | onderwerp van een email  |
|                          |              | vanuit een geregistreerd |
|                          |              | document, waarbij het    |
|                          |              | document als bijlage bij |
|                          |              | de mail wordt verstuurd. |
|                          |              | In de tekst kunnen       |
|                          |              | variabelen staan die on  |
|                          |              | the fly worden           |
|                          |              | vervangen, Zie bij lemma |
|                          |              | *Do                      |
|                          |              | cumenten/Verzendstroom*. |
+--------------------------+--------------+--------------------------+
| StandaardEmailTekstBody  | Tekst        | Deze tekst wordt         |
|                          |              | gebruikt voor de body    |
|                          |              | van een email vanuit een |
|                          |              | geregistreerd document,  |
|                          |              | waarbij het document als |
|                          |              | bijlage bij de mail      |
|                          |              | wordt verstuurd. In de   |
|                          |              | tekst kunnen variabelen  |
|                          |              | staan die on the fly     |
|                          |              | worden vervangen, Zie    |
|                          |              | bij lemma                |
|                          |              | *Do                      |
|                          |              | cumenten/Verzendstroom*. |
+--------------------------+--------------+--------------------------+
