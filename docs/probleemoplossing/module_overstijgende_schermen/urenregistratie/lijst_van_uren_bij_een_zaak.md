# Lijst Uren bij een Zaak

De schermidentifier is:MDLC_getUrenList.xml.

Dit scherm kan worden aangeroepen vanuit de detailschermen (knop linksonder) van Omgeving, Handhavingen, Bouw/sloop, Info, Milieu/gebruik, APV/Overig, Horeca en Inrichting alsmede vanuit de detailschermen van advies, inspectie en bezwaar/beroep.

Vanuit een hoofdzaak worden alleen de uren getoond die sec bij die hoofdzaak horen (dus niet bijvoorbeeld de uren bij een advies dat bij die hoofdzaak hoort).

Vanuit een deelzaak (inspectie, advies, bezwaar/beroep) alleen de uren bij die deelzaak.

## Error

Het scherm geeft een foutmelding, indien:

* er mogelijk een zelf gedefinieerde schermindeling gebruikt wordt (zie [Scherm(kolom)definitie](/docs/instellen_inrichten/schermdefinitie.md)) die niet valide is
* de inlogger geen kijkrechten heeft op de uren bij betreffende hoofdzaak of deelzaak.

## Triggers

* dubbel klikken op een regel opent het detailscherm van een [urenregistratie](/docs/probleemoplossing/module_overstijgende_schermen/urenregistratie/detailscherm_urenregistratie.md). Altijd enabled.

### Triggers linksonder

* Insertknop:
  * Zichtbaar indien:
    * de inlogger insert-rechten heeft op uren bij betreffende hoofdzaak (dus bij adviezen, inspecties bezwaarberoep wordt naar de urenrechten van de hoofdzaak gekeken)
    * OF de inlogger heeft op zijn medewerkerskaart het recht *mag uren van anderen muteren* (tbmedewerkers.dlmagurenmuteren) aangevinkt staan
    * EN - indien de inlogger lid is van een compartiment - dan dient de combinatie zaaktype en gemeente gedefinieerd te zijn bij dat compartiment (en dus als de inlogger geen lid is van een compartiment dan mag de combinatie zaaktype/gemeente in geen enkel compartiment voorkomen).
  * Enabled indien de hoofdzaak niet is geblokkeerd.
* Deleteknop:
  * Zichtbaar indien:
    * de inlogger delete-rechten heeft op uren bij betreffende hoofdzaak (dus bij adviezen, inspecties bezwaarberoep wordt naar de urenrechten van de hoofdzaak gekeken)
    * OF de inlogger heeft op zijn medewerkerskaart het recht *mag uren van anderen muteren* (tbmedewerkers.dlmagurenmuteren) aangevinkt staan
    * EN - indien de inlogger lid is van een compartiment - dan dient de combinatie zaaktype en gemeente gedefinieerd te zijn bij dat compartiment (en dus als de inlogger geen lid is van een compartiment dan mag de combinatie zaaktype/gemeente in geen enkel compartiment voorkomen).
  * Enabled indien de hoofdzaak niet is geblokkeerd.
