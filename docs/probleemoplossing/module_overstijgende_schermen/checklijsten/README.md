# Checklijsten

Zowel onder processen als onder inspecties kan men met behulp van checklijsten, per checklijst items laten afvinken door de medewerker die van belang zijn bij het behandelen van de vergunning of inspectietraject.

Het overzicht van de checklijsten wordt in twee schermen verdeeld:

- checklijsten bij de processtappen van een zaak - schermidentifier: _MDLC_getVwfrmDistinctprocchklistomgList.xml_ (verschilt per module, het voorbeeld hier is van checklijsten bij processtappen van een omgevingszaak)
- checklijsten bij een inspectietraject - schermidentifier: _MDLC_getVwfrmDistinctinspchklistList.xml_)

## Doorkiezen checklijsten

Via de overzichtsschermen van de checklijsten kan men de lijst met checklistitems openen. Vandaar de titel _Doorkiezen checklijsten_.
Het overzichtsscherm van **[checklijsten bij processtappen](/docs/probleemoplossing/module_overstijgende_schermen/checklijsten/lijst_checklistitems.md)** vindt men:

- in zaakportaal Omgeving, Handhavingen, Bouw/sloop, Horeca, Info-aanvragen en APV/Overig (tegel _Proces checklijst(en)_)
- of vanuit lijstscherm _Processtappen_ (knop linksonder)

Het overzichtsscherm van **[checklijsten bij inspectietrajecten](/docs/probleemoplossing/module_overstijgende_schermen/checklijsten/detail_checklistitem.md)** vindt men:

- vanuit de knop linksonder op het detailscherm van een inspectietraject.

De checklijsten (en hun onderliggende items) van processtappen kunnen automatisch worden aangemaakt bij het nieuw invoegen van een proces bij een zaak. Dit zal gebeuren indien vinkje **Auto** (tbkopproccheck.dlauto) aangevinkt staat bij de koppeling tussen een checklijst en een proces in de procesdefinitie (te vinden achter de tegel _Processen_ in het beheerportaal-Nieuw).

Men kan voor zowel checklijsten bij inspectietrajecten als bij processtappen deze handmatig toevoegen.

## Probleem

Het scherm geeft een een foutmelding:

- er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie/README.md)) die niet valide is
  - de inlogger moet kijkrechten hebben op de processtappen bij betreffende hoofdzaak.

### Triggers Linksonder

- **Checklijst toevoegen**. Zichtbaar en enabled indien de inlogger insertrechten heeft voor processen voor de module waar men op staat.
- **Verwijder checklijst**. Zichtbaar en enabled indien de inlogger verwijderrechten heeft voor processen voor de module waar men op staat.
- **Meerdere checklijsten toevoegen**. Zichtbaar en enabled indien de inlogger insertrechten heeft voor processen voor de module waar men op staat. Deze knop is alleen zichtbaar indien vanaf processtappen de lijst is aangeroepen. Voor het aanmaken van checklijst bij een inspectietraject is deze knop dus niet zichtbaar.

### Bijzonderheden

Klikken op een regel uit de doorkieslijst opent altijd [Lijst checklijstitems](/docs/probleemoplossing/module_overstijgende_schermen/checklijsten/lijst_checklistitems.md). De aanroep bepaalt welke gegevens vervolgens in die lijst getoond worden:

**\*Checklijst overzicht bij processtappen via tegel Proces checklijst(en)**:
- indien aanroep: *getFlexList(tbchkitwerk,tbomgvergunning,%keyparent%,A,W)* dan de checklijstitems voor alle checklijsten bij alle processtappen van de zaak
*indien aanroep: _getFlexList(tbchkitwerk,tbomgvergunning,%keyparent%,A,W,,,,{id})_ dan de checklijstitems voor alle checklijsten onder dezelfde procedure als de checklijst waar men op klikt ({id} moet vervangen worden door de dnkey van de procedure)
- indien aanroep: *getFlexList(tbchkitwerk,tbomgvergunning,%keyparent%,A,W,,,,{id}-1483)\* dan alleen de checklijstitems voor de checklijst waar men op klikt ({id} moet vervangen worden door de dnkey van de procedure, 1483 in dit voorbeeld moet vervangen worden door de dnkey van de checklistnaam)
**\*Checklijst overzicht bij inspectietraject**:
- indien aanroep: *getFlexList(tbchkitwerk,tbinspecties,%keyparent%,A,W)_dan de checklijstitems voor alle checklijsten bij het inspectietraject waarvandaan men doorkiest
_ indien aanroep: _getFlexList(tbchkitwerk,tbinspecties,381225,A,W,,,,{id})_ dan alleen de checklijstitems voor de checklijst waar men op klikt ({id} moet vervangen worden de dnkey van de checklistnaam)

**N.B.**Voor bovenstaande aanroepen is als voorbeeld gebruikt de mogelijke aanroepen bij module **Omgeving (W)** en met status **Alles (A)**. De aanroepen voor dubbelklik acties op de _Doorkieslijsten_ zijn terug te vinden in het beheerportaal-Nieuw bij de _Tabellen standaardapi_. Voor iedere module is er voor zowel processen als inspecties een standaardtabel record waarbij men in blok **Action bij dubbel klik op lijstregel** de aanroep kan vinden/wijzigen indien gewenst.

Zie ook [Detailscherm Checklijstitem](/docs/probleemoplossing/module_overstijgende_schermen/checklijsten/detail_checklistitem.md) en [Lijst checklijstitems](/docs/probleemoplossing/module_overstijgende_schermen/checklijsten/lijst_checklistitems.md)
