# Portaltegel

Screenidentifiers: MDLC_getPortalTilesList.xml en MDDC_getPortalTilesDetail.xml

## Betekenis van de kolommen

- De tekst van de kolom **kopregel** komt bovenaan in de tegel in blauw. Mag zonder gevaar aangepast worden. Mag Leeg zijn. Puntkomma's in deze tekst veroorzaken een nieuwe regel (wagenterugloop). De tekst insluiten in rechte vierkante haken ( [ ] ) betekent dat de tekst vet wordt afgedrukt.
- De tekst van de kolom **vast opschrift** komt onder de kopregel in de tegel in zwart. Mag zonder gevaar aangepast worden. Mag Leeg zijn. Puntkomma's in deze tekst veroorzaken een nieuwe regel (wagenterugloop). De tekst insluiten in rechte vierkante haken ( [ ] ) betekent dat de tekst vet wordt afgedrukt.
- De achterliggende waarde van de kolom **Tegelopschrift dynamisch met API gettilecontent** komt uit een geëvalueerd SQL-statement en wordt geplaatst onder het vaste opschrift in de tegel in zwart. Mag met kennis van zaken aangepast worden. Mag Leeg zijn.

Toepassing is bijvoorbeeld om aan te geven hoeveel kaarten de lijst achter de tegel bevat. De inhoud van deze kolom is altijd in de vorm van: getTileContent(codering) OF getTileContent(codering,{id}) bijvoorbeeld: _getTileContent(omgeving_chklist,{id})_. Bij tegels op zaakportalen moet de tweede vorm gebruikt worden, waarbij dynamisch {id} zal worden vervangen door de primary key van het betreffende zaakportaal (de identifier die opgenomen is in de URL van de portaalpagina).

De eerste parameter - de codering (in het voorbeeld: omgeving_chklist,) - verwijst naar een kaart in de tabel tbqueries met dezelfde codering. Het resultaat van die query wordt dus op de tegel geplaatst. Indien de gebruiker geen rechten heeft op de query of indien de query niet goed is gedefinieerd, dan blijft het dynamische opschrift op de tegel leeg of er komt te staan: _fout:xml_. Zie ook bij [Queries](/docs/instellen_inrichten/queries.md).

Toevoeging: indien er in de naam van de query haakjes voorkomen dan kan het programma deze niet interpreteren. Dit is als volgt op te lossen: stel de naam van de query is _test(kopie)_ dan zal het veld tegelopschrift gevuld moeten worden met: _getTileContent(beginarg(test(kopie))endarg)_

- De kolom **volgorde** bepaalt de verticale positie van een tegel onder een kolom.
- De kolom **hoort bij kolom**. Zie hieronder bij verplaatsen van tegels.
- Met het **aanvinkvakje actief** wordt de tegel klikbaar voor de gebruikers. Niet actief betekent wel zichtbaar (mits toegekend aan de medewerkers), maar disabled. Let op: indien de kolom _sql tegel onzichtbaar_ gevuld is, dan kan deze waarde overruled worden.
- De kolom **altijd verversen** betekent dat bij het herstel van de focus op een portaal waar de tegel bij hoort, de inhoud van deze tegel opnieuw wordt uitgeschreven.
- De inhoud van de kolom **actie** geeft aan welke API of hyperlink met het indrukken van de tegel wordt aangeroepen en met welke parameters. Zie hieronder bij hoofdstukje mogelijkheden. Er kunnen in de parameterlist variabelen gebruikt worden: (niet alle onderstaande variabelen kunnen in alle situaties gebruikt worden):
  - de variabele {id} wordt dynamisch vervangen door de primary key van het zaakportaal (de identifier die opgenomen is in de URL van de portaalpagina) waar de tegel onder valt
  - de variabele {inlogger} door de dvcode van de medewerker die ingelogd is
  - de variabele {locatieid} door de primary key van tbperceeladressen (de locatie waar een zaak aan is gekoppeld)
  - de variabele {inrichtingid} door de primary key van een tbmilinrichting.
- Met de kolom **sql tegel onzichtbaar indien result = 0** kan aangegeven worden onder welke conditie een tegel zichtbaar en enabled is, of zichtbaar maar disabled of onzichtbaar. Bijvoorbeeld: door het onderstaande statement is de tegel proceschecklijsten alleen zichtbaar bij de omgevingszaak indien er checklijstitems zijn gekoppeld aan een procedure (van die omgevingszaak) en anders niet:

```sql
select count(1) from tbchkitwerk
    where dnkeyomgvergunningen = {id}
    and dnkeyprocedure is not null;
```

- Of bijvoorbeeld de tegel mag niet zichtbaar zijn bij een bepaalde zaaktype:

```sql
select case when dnkeysoortomgverg = 134
    then 0 else 1 end
    from tbomgvergunning where dnkey = {id};
```

- In de kolom kan hiertoe een SQL-statement worden opgenomen. Het statement moet beginnen met 'select' en er mag geen puntkomma in het statement voorkomen. De variabele {id} en {inlogger} wordt dynamisch vervangen met de primary key van het zaakportaal (de identifier die opgenomen is in de URL van de portaalpagina) en de dvcode van de ingelogde medewerker waar de tegel onder valt.
- Indien het resultaat:
  - is null of het SQL-statements niet goed of de uitkomst <> 0,1 of 2 dan:
    - zichtbaar
    - attribuut enabled krijgt de de waarde van kolom _aanvinkvakje actief_ (dlenabled).
  - is 0 dan:
    - tegel is onzichtbaar
    - attribuut enabled doet niet ter zake, maar krijgt de de waarde van kolom _aanvinkvakje actief_ (dlenabled).
  - is 1 dan:
    - tegel is zichtbaar
    - attribuut enabled krijgt de de waarde van kolom _aanvinkvakje actief_ (dlenabled).
  - is 2 dan:
    - tegel is zichtbaar
    - attribuut enabled krijgt de waarde false ongeacht de waarde van kolom _aanvinkvakje actief_ (dlenabled).

## Verplaatsen van tegels

Het verplaatsen van tegels van de ene kolom naar de andere kolom kan zonder gevaar. De eenvoudigste manier is om op het detailscherm van de tegel de waarde van de keuzelijst _hoort bij kolom_ aan te passen. Die keuzelijst bevat alleen de kolomnamen die bij hetzelfde portaal zijn gedefinieerd: u kunt dus geen tegel van portaal A verplaatsen naar portaal B.

## Trigger toekennen medewerkers aan tegel

Linksonder kan met de knop _ken medewerkers toe aan tegel_ geregeld worden dat de tegel zichtbaar of onzichtbaar wordt voor de toekende medewerker. De wizard spreekt voor zich.
Omgekeerd kunnen vanuit medewerkers-detailscherm één of meer tegels toegekend worden aan een medewerker.

## Mogelijkheden van kolom actie

Zie: [Actions](/docs/instellen_inrichten/actions.md).
