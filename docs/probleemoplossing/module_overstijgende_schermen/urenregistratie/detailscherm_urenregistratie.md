# Detailscherm Urenregistratie

De schermidentifier is: MDDC_getUrenDetail.xml.

Dit scherm kan worden aangeroepen vanuit de _Lijst Uren_ bij een (deel)zaak of inrichting.

### Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft op de uren bij betreffende hoofd- of deelzaak.

#### Defaultwaarden

De kolom _laatste muteerder_ wordt onder water altijd gevuld met de medewerker die als laatste de kaart heeft aangemaakt.

### Muteren

De kolommen kunnen gemuteerd worden indien:

- de inlogger wijzigrechten heeft op de uren bij betreffende hoofdzaak (dus voor wijzigrechten op uren bij adviezen, insecties en bezwaarberoep wordt naar de hoofdzaak gekeken)
- en die bovenliggende hoofdzaak niet is geblokkeerd
- en de factuurdatum (tburen.ddgefactureerd) leeg is
- en de editschuif aan staat
- en de medewerker genoemd bij _voor wie_ is dezelfde als de inlogger (tenzij de inlogger het recht _mag uren van anderen muteren_ op zijn/haar medewerkerskaart aangevinkt heeft staan).

Hierop bestaan de volgende uitzonderingen:

- De kolom **voor wie** (degene die de uren gemaakt) kan alleen gemuteerd worden door een medewerker die het recht _mag uren van anderen muteren_ op zijn/haar medewerkerskaart.
- De kolom **ddgefactureerd** kan alleen gemuteerd worden door een medewerker die het recht _mag factuurdatum bij uren factureren_ op zijn/haar medewerkerskaart aangevinkt heeft staan.
- De kolom **Opdr.gever akkoord met opdracht?** deze is alleen zichtbaar in het scherm en aanpasbaar indien dit is aangegeven bij het zaaktype van de hoofdzaak in het beheer.

Voor de dropdownlijst met medewerkers **voor wie** geldt het volgende:

- de medewerker moet aan hetzelfde compartiment gekoppeld zijn als die van de inlogger
- en de medewerker moet in dienst zijn
- en het vakje _interne medewerker_ moet aangevinkt zijn.

Aan deze lijst worden toegevoegd - maar alleen indien de inlogger zelf de eigenschap _overrule compartiment_ aangevinkt heeft staan -, alle overige medewerkers met deze eigenschap.

Qua urenaantal kan een waarde tussen de 0 en 100 worden ingevoerd.

[Volledige overzicht van Urenregistratie](/docs/probleemoplossing/module_overstijgende_schermen/urenregistratie/README.md)
