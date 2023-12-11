# Database functies

Op veel plekken in OpenWave kan de applicatiebeheerder SQL-statements definiëren. Bijvoorbeeld in [rapportages](/docs/instellen_inrichten/rapportages.md), [query&#039;s](/docs/instellen_inrichten/queries.md) op tegels en [documentsjablonen](/docs/instellen_inrichten/documentsjablonen.md). Om ingewikkelde statements te vermijden heeft OpenWave zelf een aantal functies op de database gedefinieerd om veel voorkomende problemen op te lossen. Deze functies kunnen opgenomen worden in de query's op dezelfde manier als de inheemse Postgres functies.

- **fn_bedrag(p_bedrag)** retourneert een string waarbij p_bedrag (een float) is omgezet in een string met een komma voor de decimale punt en een punt voor de duizendtallen. Voorbeeld: fn_bedrag(1234.56) retourneert '1.234,56' (indien fn_bedrag(0) dan retourneert deze functie 'null' of te wel een lege waarde)
- **fn_bedragn(p_bedrag)** retourneert een string waarbij p_bedrag (een float) is omgezet in een string met een komma voor de decimale punt en een punt voor de duizendtallen. Lijkt op fn_bedrag maar zal indien de waarde van p_bedrag 0 OF null is, als resultaat **0,00** retourneren Voorbeeld: fn_bedrag(1234.56) retourneert '1.234,56' en fn_bedrag(0) retourneert dus '0,00'
- **fn_datumplus(p_datum,p_plusmindagen)** retourneert een datum waarbij de invoerdatum (p_datum) is verhoogd/verlaagd met p_plusmindagen (een integer)
- **fn_ddmaandjjjj(p_datum)** retourneert een string waarbij de invoerdatum (p_datum) is omgezet naar een Nederlandse tekst bijvoorbeeld: '03 oktober 2017'
- **fn_isposinteger (p_string)** retourneert een integer met waarde 1 indien p_string (een gevulde string van max 20 tekens) omgezet kan worden naar een positief geheel getal. Anders is de resultwaarde 0. Indien p_string een nullwaarde heeft dan is ook het resultaat 0
- **fn_unaccent(p_string)** retourneert een string waarbij diakritische tekens van p_string (een string) zijn omgezet: ö wordt o et cetera
- **fn_vandaag(p_plusmindagen**) retourneert een datum waarbij de systeemdatum is verhoogd/verlaagd met p_plusmindagen (een integer).
- **fn_datediff(p_type_p_datumvanaf,p_datumtot)** retourneert een integer die afhankelijk van p_type het verschil in dagen, maanden of jaren weergeeft tussen de twee datums. P_type kan de waarde 'day' of 'month' of 'year' hebben
- **instr(p_domeinstring,p_zoekstring,[p_begin],[p_occurence])** retourneert een integer die de positie van p_zoekstring binnen p_domeinstring weergeeft vanaf p_begin (integer). P_begin en p_occurence zijn optioneel. Beide hebben 1 als defaultwaarde. P_occurence staat voor de nde keer dat p_zoekstring voorkomt vanaf p_begin in p_domeinstring. Voorbeelden:
  - instr('Altijd is kortjakje ziek', 's') resultaat: 9 (De positie van de eerste 's' geteld vanaf 1)
  - instr('Varen, varen over de baren','ren',4,2) resultaat: 24 (De positie van de tweede 'ren' geteld vanaf 4)
  - instr('Varen, varen over de baren','ren',-1) resultaat: 24 (De positie van de eerste 'ren' geteld vanaf -1 : van rechts naar links)
- **fn_isposintpolygoon (p_string)** retourneert een integer met waarde 1 indien p_string bestaat uit minimaal 3 paren coördinaten gescheiden door een spatie. Een coördinaatpaar bestaat uit twee positieve getallen gescheiden door een komma. Een correcte polygoonstring is bijvoorbeeld '1234,2345 3456,45 5678987,4321 4,4 1234,2345'. Is p_string niet correct dan wordt een 0 geretourneerd
- **fn_isposintlijnofpolygoon (p_string)** retourneert een integer met waarde 1 indien p_string bestaat uit minimaal 2 paren coördinaten gescheiden door een spatie. Een coördinaatpaar bestaat uit twee positieve getallen gescheiden door een komma. Een correcte polygoonstring is bijvoorbeeld '1234,2345 3456,45 5678987,4321 4,4'. Is p_string niet correct dan wordt een 0 geretourneerd
- **fn_dec2ana(p_tijd)** retourneert een tijd in het formaat HH:MM. P_tijd is een float. Bijvoorbeeld 26.4 wordt 26:24. 1.5 wordt 1:30. 12.12345 wordt 12:07. P_tijd moet kleiner zijn dan 100
- **fn_tijdstip(p_plusmin integer, p_interval char(1))** retourneert een tijdstip op basis van het moment dat de functie wordt aangeroepen + of - een aantal uur of dagen. Het resultaat is een timestamp. p_interval kan de waarde 'D' (dagen) of 'H' (uren)hebben. Voorbeelden:
  - Stel fn_tijdstip(0,'H') = 2021-11-30 09:10:52.307227
  - dan is fn_tijdstip(-24,'H')= 2021-11-29 09:10:52.307227
  - dan is fn_tijdstip(5,'H')= 2021-11-30 14:10:52.307227
  - dan is fn_tijdstip(-1,'D')= 2021-11-29 14:10:52.307227

LET OP: fn_tijdstip(-24,'H') kan een ander resultaat geven als fn_tijdstip(-1,'D'). Bij uren wordt rekening gehouden met overgang winter/zomertijd. Bij dagen niet.

- **fn_rechtenkolom(p_column text,p_keyrechten integer)** retourneert 'T' of 'F' als char(1). Het resultaat is de achterliggende waarde van de parameter p_column die doorgegeven moet worden als rechtentabelnaam + '.' + rechtenkolomnaam bijvoorbeeld _tbomgrechten.dlcadvins_. De parameter p_keyrechten moet de waarde hebben van dnkeyrechten uit de medewerkerstabel bij de kaart van de betreffende inlogger. Er is een systeemquery (dvcode = _geefWaardeRechtenkolom_) die deze aanroep gebruikt; deze query geeft true of false terug en kan gebruikt worden in bijv. de schermkolomdefinitie bij tags visible of edit.
- **fn_rechtenkolom(p_column text,p_mwcode char(5))** retourneert 'T' of 'F' als char(1). Het resultaat is de achterliggende waarde van de parameter p_column die doorgegeven moet worden als rechtentabelnaam + '.' + rechtenkolomnaam bijvoorbeeld _tbomgrechten.dlcadvins_. De parameter p_mwcode moet de waarde hebben van een dvcode uit de medewerkerstabel bij de kaart van de betreffende inlogger. Wanneer deze functie aangeroepen wordt vanuit een opgeslagen query in tbqueries, dan kan daartoe de systeemvariable _:keyaccount_ voor worden gebruikt).
- **fn_iscompartimentok(p_mwcode char(5),p_module char(1), p_dnkey integer)** retourneert 0 of 1 als integer. 0 indien de compartimentcheck niet klopt en 1 indien de compartimentscheck wel klopt.

In _p_mwcode_ moet de medewerkerscode van de inlogger doorgegeven worden (wanneer deze functie aangeroepen wordt vanuit een opgeslagen query in tbqueries, dan kan daartoe de systeemvariabele _:keyaccount_ voor worden gebruikt).

De parameter _p_module_ éen letter namelijk (B)ouw/sloop, hore(C)a, mili(E)/gebruik, (H)andhavimg, (I(infoaanvragen, apv/(O)verig, (V)inrichtingen of (W ) omgevingzaken.

In de parameter _p_dnkey_ dient de primary key doorgegeven te worden die hoort bij de module en die verwijst naar een rij waarvoor de compartimentcheck moet worden gedaan. OpenWave zoekt de dnkeywaarde op in vwfrmomgvergunningen c.q. vwfrmhandhavingen etcetera en evalueert daar of de kolom dnkeycompartiment overeenkomt met die van de medewerker.

Zie voor voorbeeld met betrekking tot gebruik van de functies _fn_rechtenkolom en fn_iscompartimentok_: onder kopje _De kolommen van de tabel tbsysstandardtable_ bij [Standaard Lijst- en Detailschermen](/docs/instellen_inrichten/standardlist_standarddetail.md)
