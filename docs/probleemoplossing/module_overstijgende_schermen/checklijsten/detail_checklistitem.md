# Detailscherm Checklijstitem

De schermidentifier is: MDDC_getChkitWerkDetail.xml.

Dit scherm kan worden aangeroepen vanuit de _Lijst Checklijstitems_ bij een termijnbewakingsstap of inspectietraject.

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft op de processen bij betreffende hoofdzaak.

### Muteren

De kolommen kunnen gemuteerd worden indien:

- de inlogger wijzigrechten heeft op de processtappen bij betreffende hoofdzaak (bijvoorbeeld wijzigrechten op proces/checklijst bij omgeving)
- en die bovenliggende hoofdzaak niet is geblokkeerd
- en de editschuif aan staat
- en - indien de inlogger lid is van een compartiment - dan moet de bovenliggende zaaktype/gemeente in dat compartiment gedefinieerd zijn. Indien de inlogger geen lid is van een compartiment, dan mag de combinatie bovenliggende zaaktype/gemeente in geen enkel compartiment gedefinieerd zijn.

### Triggers in het scherm zelf achter kolommen

- **Laatste muteerder** en **Laatste mutatiedatum**:
  - velden worden automatisch gevuld indien men veld **Status** wijzigt met de medewerker code van de ingelogde gebruiker respectievelijk met de datum van vandaag

Zie ook [Checklijsten](/probleemoplossing/module_overstijgende_schermen/checklijsten/README.md) en [Lijst checklijstitems](/probleemoplossing/module_overstijgende_schermen/checklijsten/lijst_checklistitems.md)
