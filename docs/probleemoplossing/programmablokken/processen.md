# Processen/termijnbewaking

In een aantal schema's wordt hierachter duidelijk gemaakt hoe de termijnberekeningen bij de procesbewaking werken. Daarbij wordt gebruik gemaakt van de begrippen afvinkstappen en termijnstappen. Een termijnstap is een rij in tbtermijnbewstappen waarbij de kolom dvvoorwaardejn de waarde 'N' heeft. In dat geval heeft de regel een afgehandeld datum en streefdatum (dddeadline) die door de userinterface wordt ondersteund. Een afvinkstap is een rij in tbtermijnbewstappen waarbij de kolom dvvoorwaardejn de waarde 'T' of 'F' heeft.

In dat geval geeft de userinterface van die regel alleen de mogelijkheid tot aan- en uitvinken.

## Algoritmes

Er is een aantal triggers waarbij verschillende algoritmes worden uitgevoerd:

### Invoegen nieuw proces

Indien een nieuw proces wordt ingevoegd dan:

- worden de stappen van de beheertabel tbprocitems van het aangewezen proces gekopieerd naar tbtermijnbewakingsstappen en voorzien van de juiste volgnummers. Zie: [Invoegen stappen bij ophalen nieuw proces](/probleemoplossing/programmablokken/processen/invoegen_stappen_nieuw_proces.md)
- worden de streefdatums (tbtermijnbewstappen.dddeadline) van de ingevoegde termijnstappen opnieuw berekend. Zie: [(Her)berekenen van termijnbewakingsstappen](/probleemoplossing/programmablokken/processen/bereken_termijnbewakingsstappen.md)
- worden termijnstappen op actief/inactief gezet op grond van het al of niet aangevinkt zijn van de afvinkstappen. Zie: [Bepaal actief/inactief status van de termijnbewakingsstappen](/probleemoplossing/programmablokken/processen/bepaal_actief_inactief.md).

### Ophalen checklijsten

Indien aan een automatisch toegevoegd proces één of meer checklijsten zijn verbonden die de eigenschap _automatisch toevoegen_ hebben (tbkopproccheck.dlauto = 'T') , dan worden deze checklijsten automatisch toegevoegd onder de betreffende zaak.

### Wijzigen van afhandeldatum

Indien een afgehandeld datum wordt overschreven dan:

- wordt de kolom dvcodemedewerkers gevuld met de tbmedewerkers.dvcode van degene die op dat moment is ingelogd (en dus de wijziging heeft doorgevoerd)
- worden de streefdatums (tbtermijnbewstappen.dddeadline) van de termijnstappen met een volgnummer (dnvolgnr) groter dan die van de afgehandelde stap opnieuw berekend. Zie: [(Her)berekenen van termijnbewakingsstappen](/probleemoplossing/programmablokken/processen/bereken_termijnbewakingsstappen.md)
- wordt de opschortende werking op grond van indiening aanvullende gegevens zo nodig opnieuw bepaald en verwerkt indien het een omgevingszaak betreft. Zie: [Opschortende werking bij omgevingszaken](/probleemoplossing/programmablokken/processen/opschortende_werking_omgevingszaken.md)
- wordt mogelijk de fatale datum (tbomgvergunning.ddfataledatum) van de omgevingszaak opnieuw berekend indien:
  - de kolom dndagenopschwerking (zie hierboven berekening opschortende werking) gewijzigd is
  - de kolom tbomgvergunning.ddblokkering niet is gevuld
- wordt - indien de kolommen dvtabelnaam en dvomschrijvingvv in de tbtermijnbewstappen gevuld zijn bij de gewijzigde kaart - in de hoofdzaak de gelijknamige kolom overschreven met de nieuwe afhandeldatum of met de waarde van een extra invoerkolom.

### Wijzigen van streefdatum

Dit is mogelijk indien bij de processtapdefinitie (beheertegel _Procedures_) het item _berekende streefdatum door gebruiker aanpasbaar_ is aangevinkt (kolom dldeadlineaanpasbaar). Indien een streefdatum (dddeadline) wordt overschreven:

- worden de streefdatums (tbtermijnbewstappen.dddeadline) van de termijnstappen met een volgnummer (dnvolgnr) groter dan die van de streefdatumstap opnieuw berekend. Zie: [(Her)berekenen van termijnbewakingsstappen](/probleemoplossing/programmablokken/processen/bereken_termijnbewakingsstappen.md).

### Wijzigen van een afvinkstap

Indien een afvinkstap wordt aangevinkt of uitgevinkt dan:

- wordt de kolom dvcodemedewerkers gevuld met de tbmedewerkers.dvcode van degene die op dat moment is ingelogd (en dus de wijziging heeft doorgevoerd)
- worden de streefdatums (tbtermijnbewstappen.dddeadline) van alle termijnstappen van de betreffende procedure opnieuw berekend. Zie: [(Her)berekenen van termijnbewakingsstappen](/probleemoplossing/programmablokken/processen/bereken_termijnbewakingsstappen.md)
- worden de afgehandeld datums en streefdatums (dddeadline) van die rijen waar vanwege het afvinken of uitvinken niet (meer) naar verwezen wordt, leeggemaakt en op inactief gezet (dlingebruik = 'F'). Zie: [Leegmaken datums inactieve stappen](/probleemoplossing/programmablokken/processen/leegmaken_datums_inactieve_stappen.md).
