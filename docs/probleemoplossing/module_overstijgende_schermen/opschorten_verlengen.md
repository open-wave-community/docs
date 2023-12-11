# Opschorten/Verlengen

De schermidentifiers voor lijst en detail zijn: MDLC_getOpschortenList.xml en MDDC_getOpschortenDetail.xml. De bron van het lijst- en detailscherm is de view vwfrmopschorten (op basis van de tabel tbopschorten).

## Zichtbaarheid

### Aparte blokken verlenging en opschorten

Indien wordt overgegaan wordt tot het gebruik van de tabel tbopschorten, waarin verlengingen en opschortingen herhaalbaar kunnen worden opgenomen, is het zinvol de aparte blokken waarin dit ook deels geregeld kan worden, onzichtbaar te maken. Bij de omgevingszaak-detailkaart gaat hierbij om de bestaande blokken:

- Verlenging;Wabo art. 3.9;lid 2 (42dgn)
- Verlenging
- Opschorting;Awb art. 4.15 m.u.v. lid 1a

en bij Handhaving om het bestaande blok:

- Verlenging; Awb art. 4.14; lid 3

Deze blokken kunnen zichtbaar/onzichtbaar gemaakt worden door in het beheerportaal _Zaakbeheer_ onder de tegel _Zaaktypes Omgeving_ en _Zaaktypes Handhaving_ per type de kolom **Verlengen/Opschorten** via blokken in detail (dlblokkenopschort) aan/uit te vinken.

### Blok t.b.v. tabel tbopschorten

De tabel tbopschorten kan zichtbaar gemaakt worden als lijstje in het blok opschorten binnen de detailschermen van de hoofdzaak, door in het beheer onder de tegels _Zaaktypes Omgeving_ en _Zaaktypes Handhaving_ en _Zaaktypes APV/Overig_ en _Zaaktypes Milieu/gebruik_ en _Zaaktypes Horeca_ per type de kolom **Verlengen/opschorten** via tabel (dltabelopschorten) aan te vinken.

## Rechten muteren

Er zijn geen aparte rechten op deze tabel: wijzigrechten op de hoofdzaak maakt dat een gebruiker regels kan toevoegen, wijzigen en verwijderen.

Indien een einddatum of termijn van een bepaalde regel, ondanks rechten, niet kan worden aangepast, zal de opschortregel gekoppeld zijn aan een codering met een vaste - niet muteerbare - defaulttermijn.

## Insert

Bij een insert op de tabel tbopschorten moet een keuze gemaakt worden uit een codetabel (tbcodeopschort).

In het beheerportaal _Zaakbeheer_ is onder de kolom _Afhandeling_ de tegel _Opschorting Verlenging_ opgenomen ten behoeve van het vullen van deze codetabel tbcodeopschort, met daarin de verschillende wetsartikelen op grond waarvan de behandeling van een zaak verlengd, opgeschort, verdaagd kan worden en waarvan de inhoud van invloed is op de berekening van de fatale termijn.

In deze codetabel kan een default opschort/verlengtermijn worden opgegeven en tevens kan aangegeven worden of de gebruiker deze termijn aan de voorkant kan aanpassen. Deze default opschort/verlengtermijn overruled de eventueel voorgestelde einddatum.

## Fatale datum hoofdzaak

De optelling van de termijnen van de regels uit de tabel tbopschorten die gekoppeld zijn aan één hoofdzaak worden na elke wijziging, insert of delete gesaldeerd in de fatale datum kolom van die hoofdzaak.

Indien de opschortende werking door uitvraag van aanvullende gegevens ook in deze tabel tbopschorten geregeld gaat worden, dan zijn er twee instellingen die ervoor waken dat de opschortende werking van indiening aanvullende gegevens via processtap, mogelijk leidt tot doublure van de opschortende termijn in de fatale datum van de hoofdzaak.
Het gaat om:

- _Sectie: Termijnbewaking en Item: Omgeving_BerOpschAanvProces_
- _Sectie: Termijnbewaking en Item: APVOverig_BerOpschAanvProces_

Indien aangevinkt wordt bij een wijziging in tbtermijnbewstappen die van invloed is op het moment van indiening aanvullende gegevens, de opschortende werking daarvan doorberekend (via de hulpkolom dndagenopschwerking) in de APV/Overige hoofdzaak c.q. Omgeving hoofdzaak.

### Berekening termijn, einddatum per opschortregel

Bij een wijziging binnen één regel van tbopschorten redeneert OpenWave als volgt:

- Een wijziging op de startdatum heeft tot gevolg dat de einddatum opnieuw berekend wordt op grond van de ingevulde termijn: geen wijziging in de termijn.
- Een wijziging van de termijn heeft tot gevolg dat de einddatum opnieuw berekend wordt (startdatum + termijn).
- Een wijziging van de einddatum heeft tot gevolg dat de termijn opnieuw berekend wordt.(einddatum minus startdatum).

## Triggers in lijstscherm linksonder

- Insertknop:
  - Zichtbaar indien:
    - de inlogger wijzigrechten heeft op de bovenliggende hoofdzaak
    - de inlogger hoort bij het compartiment waar de zaak onder valt.
  - Enabled indien de bovenliggende zaak niet is geblokkeerd.
- Deleteknop:
  - Zichtbaar indien:
    - de inlogger wijzigrechten heeft op de bovenliggende hoofdzaak
    - de inlogger hoort bij het compartiment waar de zaak onder valt.
  - Enabled indien de bovenliggende zaak niet is geblokkeerd.
