# Creëer zaak zaak/DMS

Met de schermknop *Creëer zaak* van de detailschermen van omgeving, inrichting, APV/overig en handhaving en ook op de deelzaak-detailschermen van adviezen, bezwaarberoep en inspecties, alsmede automatisch bij het verwerken van een OLO/DSO-bericht, en ook automatisch vanuit aanmaken nieuwe zaak, kan een zaak in een extern (zaaksysteem) worden aangemaakt met de stuf zaak/DMS koppeling.

Eerst wordt een zaakidentficatie opgehaald met een genereerZaakidentficatie_Di02 bericht en vervolgens wordt de zaak aangeboden met dat identificatienummer met een creeerZaak_Lk01 bericht.
Bij succes wordt de externe zaakidentificatie in OpenWave opgeslagen in de kolom extern zaak/DMS (dvintzaakcode).

## Verplichte Instellingen

* **Methode**
  * Indien de zaak NIET wordt behandeld door een compartiment dan MOET de instelling *Sectie: Koppeling ZAAK:* en *Item: Methode* aangevinkt staan en heeft als Tekst: StUF-ZAKEN 310.
  * Indien de zaak WEL wordt behandeld door een compartiment dan MOET de kolom dvdmsmethode bij de compartimentsdefinitie de waarde StUF-ZAKEN 310 hebben.
* **Action**
  * Instelling *Koppeling ZAAK Item: HTTPSoapAction_creeerZaak_Lk01*. De kolom *Tekst* moet gevuld worden met juiste soapaction:
    * Indien zaak/DMS dan `[http://www.egem.nl/StUF/sector/zkn/0310/creeerZaak_Lk01](http://www.egem.nl/StUF/sector/zkn/0310/creeerZaak_Lk01.md)`
    * Indien (oude) stufzaken dan `[http://www.egem.nl/StUF/sector/zkn/0310/zakLk01](http://www.egem.nl/StUF/sector/zkn/0310/zakLk01.md)`
  * Instelling *Koppeling ZAAK Item: HTTPSoapAction_genereerZaakIdentificatie_Di02*. De kolom *Tekst* moet gevuld worden met juiste soapaction: `[http://www.egem.nl/StUF/sector/zkn/0310/genereerZaakIdentificatie_Di02](http://www.egem.nl/StUF/sector/zkn/0310/genereerZaakIdentificatie_Di02.md)`

LET OP: de soapactions kunnen ook ingesloten moeten zijn door dubbele quootjes, dus bijv. `"[http://www.egem.nl/StUF/sector/zkn/0310/genereerZaakIdentificatie_Di02](http://www.egem.nl/StUF/sector/zkn/0310/genereerZaakIdentificatie_Di02.md)"`.

### Endpoint, credentials en stuurgegevens

Voor het endpoint en de stuurgegevens zal het programma eerst kijken naar de waarden in de blokken *stuf zaak/dms endpoint en credentials* en *stufzaak.dms stuurgegevens* van het **detailscherm van de gemeente waar de zaak speelt** (beheertegel *Gemeentes*) waarbij:

* Voor de Ontvanger_administratie geldt dat als de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsOntvangerAdm* bestaat en is aangevinkt, dat dan in het bericht het stuurgegeven ontvanger administratie gevuld wordt met de gemeente-id van de locatie waar de zaak zich afspeelt.
* Voor de Zender_administratie geldt dat als de kolom *Tekst*van de instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsZenderAdm* bestaat en is aangevinkt, dat dan in het bericht het stuurgegeven zender administratie gevuld wordt met de gemeente-id van de locatie waar de zaak zich afspeelt.

Indien alhier het endpoint vrije berichten EN het endpoint asynchroon gevuld zijn dan neemt het programma de credentials en stuurgegevens over van deze kaart.

Een uitzondering hierop is de situatie dat een zaak speelt bij een gemeente die gedefinieerd is in een compartiment terwijl de zaak zelf niet door dat compartiment wordt behandeld, maar door de host. In dat laatste geval valt OpenWave terug op de algemene stufzaak/DMS instellingen uit tbinitialisatie (beheertegel *Configuratie*). Dat is ook het geval indien in tb33gemeente geen instellingen worden gevonden: dan valt het programma terug op de volgende configuratie-instellingen van *Sectie: Koppeling ZAAK*:

* *Item: Ontvangstadres_VrijeBerichten* moet gevuld zijn met het endpoint van de ontvanger t.b.v. genereerZaakidentficatie bericht.
* *Item: Ontvangstadres_Asynchroon* moet gevuld zijn t.b.v. creeerzaak bericht.
* *Item: Ontvanger_applicatie*. De kolom *Tekst* met de ontvanger (ook verplicht).
* *Item: Ontvanger_organisatie*. De kolom *Tekst* met de organisatie (ook verplicht).
* *Item: Zender_applicatie*. De kolom *Tekst* met de ontvanger (ook verplicht).
* *Item: Zender_organisatie*. De kolom *Tekst* met de organisatie (ook verplicht).
* *Item: Ontvanger_administratie*. De kolom *Tekst* met de administratie. Echter, indien de instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsOntvangerAdm* bestaat en is aangevinkt dan wordt in het bericht het stuurgegeven ontvanger administratie gevuld met de gemeente-id van de locatie waar de zaak zich afspeelt.
* *Item: Zender_administratie*. De kolom *Tekst* met de administratie. Echter, indien de instelling *Sectie: Koppeling ZAAK* en *Item: GemeenteIDAlsZenderAdm* bestaat en is aangevinkt dan wordt in het bericht het stuurgegeven zender administratie gevuld met de gemeente-id van de locatie waar de zaak zich afspeelt.
* *Item: Zender_gebruiker*. De kolom *Tekst*met de gebruiker.
* Als de instelling *Sectie: Koppeling ZAAK* en *Item: HTTPAuthenticatieNaam* bestaat en is aangevinkt dan wordt de verzending over HTTPS geautoriseerd met:
  * authenticatienaam is kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: HTTPAuthenticatieNaam*
  * authenticatiepass is kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: HTTPAuthenticatiePass*, zie ook: [2-way encryptie van externe wachtwoorden](/docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md)
  * In de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: HTTPAuthenticatieType* kan desgewenst het authenticatietype worden ingevuld: Basic (default) of NTLM (versie 1).
  * In de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: Domein* kan desgewenst het domein worden ingevuld.
* Indien er gebruik moet worden gemaakt van een **client-certificaat** (wordt geplaatst op de CONF-map van de WSAS server) dan:
  * moet de (file)-naam van dat certificaat worden opgeslagen in de kolom *Tekst* van *Sectie: Koppeling ZAAK* en Item: ClientCertificaatNaam*
  * het certificaat password in de kolom *Tekst* van *Sectie: Koppeling ZAAK* en Item: CertificaatPassword*, zie ook: [2-way encryptie van externe wachtwoorden](/docs/instellen_inrichten/2way_encryptie_externe_wachtwoorden.md)
  * het certificaattype in de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: CertificaatType* (default PKCS12).

#### Overige instellingen

Indien de instelling  *Sectie: Koppeling ZAAK* en *Item: AllowAllHostnameVerifier* aangevinkt is zal de OpenWave Cloud instemmen met een self-signed of verlopen certificaat bij een verbinding onder https.

In de kolom *Tekst* van de instelling met *Sectie: KoppelingZAAK* en *Item: Charset* kan opgegeven worden welke charset in de https header wordt gebruikt bijv. UTF-8  (default is dat ISO-8859-1). Ongeacht de waarde van de charset-instelling kan indien gewenst ervoor gezorgd worden dat uitgaande berichten van OpenWave naar het DMS ontdaan worden van diakritische tekens indien de instelling *Sectie: KoppelingZAAK en Item: UitgaandWin1252* aangevinkt wordt.

### Mapping Status Inbehandeling

In de tabel [zaakstatussen (Zaakbeheer)](/docs/instellen_inrichten/zaakstatussen.md) moet een rij aanwezig zijn met in de kolom *codering van status in OpenWave* met de waarde *StatusInBehandeling* en met een gevulde mapping voor het externe zaaksysteem.

### Automatische aanmaak bij nieuwe zaak

* Indien omgevingszaak dan:
  * Indien de zaak NIET wordt behandeld door een compartiment dan:
    * moet de instelling *Koppeling ZAAK* en *Item: AutoZaakDmsOmgeving* aangevinkt zijn
    * EN bij beheer zaaktypes omgeving moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist.
  * Indien de zaak WEL wordt behandeld door compartiment dan:
    * moet bij het compartiment de kolom *Automatisch omgevingszaak aanmaken in zaak/dms* aangevinkt zijn
    * EN bij het betreffende zaaktype in de compartimentsdefinitie moet de externe zaaktypecode gevuld zijn.
* Indien handhavingszaak dan:
  * Indien de zaak NIET wordt behandeld door een compartiment dan:
    * moet de instelling *Koppeling ZAAK* en *Item: AutoZaakDmsHandhaving* aangevinkt zijn
    * EN bij beheer zaaktypes Handhaving moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist.
  * Indien de zaak WEL wordt behandeld door compartiment dan:
    * moet bij het compartiment de kolom *Automatisch handhavingzaak aanmaken in zaak/dms* aangevinkt zijn
    * EN bij het betreffende zaaktype in de compartimentsdefinitie moet de externe zaaktypecode gevuld zijn.
* Indien APV/overige zaak dan:
  * Indien de zaak NIET wordt behandeld door een compartiment dan:
    * moet de instelling *Koppeling ZAAK* en *Item: AutoZaakDmsApvOverg* aangevinkt zijn
    * EN bij beheer zaaktypes apv/overig moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist.
  * Indien de zaak WEL wordt behandeld door compartiment dan:
    * moet bij het compartiment de kolom *Automatisch apv/overigezaak aanmaken in zaak/dms* aangevinkt zijn
    * EN bij het betreffende zaaktype in de compartimentsdefinitie moet de externe zaaktypecode gevuld zijn.
* Indien milieu/gebruik zaak dan:
  * Indien de zaak NIET wordt behandeld door een compartiment dan:
    * moet de instelling *Koppeling ZAAK* en *Item: AutoZaakDmsMilieuGebruik* aangevinkt zijn
    * EN bij beheer zaaktypes milieu/gebruik moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist.
  * Indien de zaak WEL wordt behandeld door compartiment dan:
    * moet bij het compartiment de kolom *Automatisch milieu/gebruikzaak aanmaken in zaak/dms* aangevinkt zijn
    * EN bij het betreffende zaaktype in de compartimentsdefinitie moet de externe zaaktypecode gevuld zijn.
* Indien infoaanvraagzaak dan:
  * Indien de zaak NIET wordt behandeld door compartiment dan:
    * moet de instelling *Koppeling ZAAK* en *Item: AutoZaakDmsInfoAanvraag* aangevinkt zijn
    * EN bij beheer zaaktypes infoaanvraag moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist.
* Indien deelzaak: advieszaak dan:
  * Indien de zaak NIET wordt behandeld door compartiment dan:
    * moet de instelling *Koppeling ZAAK* en *Item: AdviesIsZaak* aangevinkt zijn
    * moet de kolom *Tekst* van de instelling *Koppeling ZAAK* en *Item: AdviesIsZaak* het externe zaaktype bevatten voor adviezen
    * moet kolom *Getal1* van de instelling *Sectie: Koppeling Zaak* en *Item: Zender_Organisatie* gevuld zijn met de ID (dnkey) van het contactadres die als aanvrager gaat gelden (dus die van de organisatie zelf)).
  * Indien de zaak WEL wordt behandeld door compartiment dan:
    * moet de instelling *Koppeling ZAAK* en *Item: AdviesIsZaak* aangevinkt zijn
    * EN bij de kolom */zaaktype_DMS_Adviezen* in de compartimentsdefinitie moet de externe zaaktypecode voor adviezen gevuld zijn
    * EN de ID (dnkey) van het contactadres van de organisatie zelf (die als aanvrager gaat fungeren) staat in de kolom dnkeyorganisatie van het compartiment (beheerportaal-Nieuw).

Zie ook [Verwerking van StUF OLO / AIM berichten](/docs/probleemoplossing/programmablokken/olo_verwerking.md) indien OLO-bericht in omgevingstabel wordt opgenomen.

### Aanmaken zaak met schermknop vanuit Omgeving

* De kolom *zaak/dms nummer* (dvintzaakcode) moet een lege waarde hebben.
* Rechten: de inlogger moet lid zijn van rechtengroep die bij de omgevingszaakrechten *wijzigen externe zaaknummers incl olonummer* aangevinkt heeft staan.
* De omgevingszaak mag niet geblokkeerd zijn.
* Zaaktype:
  * indien de zaak NIET valt onder een compartiment: bij beheer zaaktypes omgeving moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist
  * indien de zaak WEL valt onder een compartiment dan moet in de compartimentdefinitie voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn.

### Aanmaken zaak vanuit inrichting

* De kolom *zaak/dms nummer* (dvintzaakcode) moet een lege waarde hebben.
* Rechten: de inlogger moet lid zijn van rechtengroep die bij de object/inrichtingrechten *wijzigen externe zaaknummers* aangevinkt heeft staan.
* De inrichting mag niet geblokkeerd zijn.
* Zaaktype: de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: ZaaktypeInrichting* (en deze instelling moet aangevinkt zijn).
* De aanvrager (bij een inrichting de organisatie zelf) is het contactadres waarvan:
  * indien de hoofdzaak NIET valt onder een compartiment de ID (dnkey) staat in de kolom *Getal1* van de instelling *Sectie: Koppeling Zaak* en *Item: Zender_Organisatie* (moet gevuld zijn)
  * indien de hoofdzaak WEL valt onder een compartiment de ID (dnkey) staat in de kolom dnkeyorganisatie van het compartiment (beheerportaal-Nieuw).

### Aanmaken zaak vanuit APV/Overig

* De kolom *zaak/dms nummer* (dvintzaakcode) moet een lege waarde hebben.
* Rechten: de inlogger moet lid zijn van rechtengroep die bij de APV/Overigezaakrechten *wijzigen externe zaaknummers* aangevinkt heeft staan.
* De APV/Overige zaak mag niet geblokkeerd zijn.
* Zaaktype:
  * indien de zaak NIET valt onder een compartiment: bij beheer zaaktypes APV/Overig moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist
  * indien de zaak WEL valt onder een compartiment dan moet in de compartimentdefinitie voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn.

### Aanmaken zaak vanuit Infoaanvraag

* De kolom *zaak/dms nummer* (dvintzaakcode) moet een lege waarde hebben.
* Rechten: de inlogger moet lid zijn van rechtengroep die bij de Infoaanvraagzaakrechten *wijzigen externe zaaknummers* aangevinkt heeft staan.
* De infoaanvraag mag niet geblokkeerd zijn.
* Zaaktype:
  * indien de zaak NIET valt onder een compartiment: bij beheer zaaktypes infoaanvragen moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist
  * indien de zaak WEL valt onder een compartiment dan moet in de compartimentdefinitie voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn.

### Aanmaken zaak vanuit Handhavingen

* De kolom *zaak/dms nummer* (dvintzaakcode) moet een lege waarde hebben.
* Rechten: de inlogger moet lid zijn van rechtengroep die bij de Handhavingszaakrechten *wijzigen externe zaaknummers* aangevinkt heeft staan.
* De handhavingszaak mag niet geblokkeerd zijn.
* Zaaktype:
  * indien de zaak NIET valt onder een compartiment: bij beheer zaaktypes handhaving moet voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn en het aanvinkvakje aangekruist
  * indien de zaak WEL valt onder een compartiment dan moet in de compartimentdefinitie voor het betrokken wave-zaaktype de externe zaaktypecode gevuld zijn.
* De aanvrager (bij een handhaving de organisatie zelf) is het contactadres waarvan:
  * indien de hoofdzaak NIET valt onder een compartiment  de ID (dnkey) staat in de kolom *Getal1* van de instelling *Sectie: Koppeling Zaak* en *Item: Zender_Organisatie*  (moet gevuld zijn)
  * indien de hoofdzaak WEL valt onder een compartiment de ID (dnkey) staat in de kolom dnkeyorganisatie van het compartiment (beheerportaal-Nieuw).

### Aanmaken zaak vanuit deelzaak Adviezen

* De instelling *Sectie: Adviezen* en *Item: AdviesIsZaak* moet aangevinkt staan.
* De kolom *zaak/dms nummer* (dvintzaakcode) moet een lege waarde hebben.
* Rechten: de inlogger moet lid zijn van rechtengroep die bij de Adviezen bij de betrokken module (dus bijvoorbeeld adviesrechten bij handhavingen) *wijzigen externe zaaknummers* aangevinkt heeft staan.
* De bovenliggende zaak (dus de omgevingszaak, handhavingszaak et cetera, waar het advies aan gekoppeld is) mag niet geblokkeerd zijn.
* Zaaktype:
  * indien de hoofdzaak NIET valt onder een compartiment dan de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: ZaaktypeAdvies* (en deze instelling moet aangevinkt zijn)
  * indien de hoofdzaak WEL valt onder een compartiment dan de kolom dvdmszaaktypeadvies bij de compartimentsdefinitie.
* De aanvrager (bij een advieszaak de organisatie zelf) is het contactadres waarvan:
  * indien de hoofdzaak NIET valt onder een compartiment  de ID (dnkey) staat in de kolom *Getal1* van de instelling *Sectie: Koppeling Zaak* en *Item: Zender_Organisatie* (moet gevuld zijn)
  * indien de hoofdzaak WEL valt onder een compartiment de ID (dnkey) staat in de kolom dnkeyorganisatie van het compartiment (beheerportaal-Nieuw) (moet dus gevuld zijn).

### Aanmaken zaak vanuit deelzaak BezwaarBeroep

* De instelling *Sectie: Programma* en *Item: BezwaarBeroepIsZaak* moet aangevinkt staan.
* De kolom *zaak/dms nummer* (dvintzaakcode) (in blok *Keten*) moet een lege waarde hebben.
* de kolom *einddedatum* (dddmsafgehandeld) moet leeg zijn.
* Rechten: de inlogger moet lid zijn van rechtengroep die bij Bezwaar/Beroep bij de betrokken module (dus bijvoorbeeld bezwaarberoeprechten bij handhavingen) *wijzigen externe zaaknummers* aangevinkt heeft staan.
* De bovenliggende zaak (dus de omgevingszaak, handhavingszaak et cetera, waar het bezwaar/beroep aan gekoppeld is) mag niet geblokkeerd zijn.
* Zaaktype:
  * indien de bezwaarberoepzaak NIET valt onder een compartiment dan  de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: ZaaktypeBezwaarBeroep* (en deze instelling moet aangevinkt zijn)
  * indien de bezwaarberoepzaak WEL valt onder een compartiment dan de kolom dvdmszaaktypebezwaarberoep bij de compartimentsdefinitie.
* Er minimaal één contactpersoon is bij de bezwaar/beroepzaak die de rol van IND (indiener) heeft.

### Aanmaken zaak vanuit deelzaak Inspecties

* De moduleletter waar de inspectie onder valt: (W = omgeving, H = handhaving , O = APV/Overig, V= Inrichting ) komt NIET voor in de kolom *Info* van de instelling *Sectie: Koppeling Zaak* en *Item: ZaaktypeInspectietraject* (maar deze instelling bestaat wel). Indien bijvoorbeeld de kolom *Info* de waarde 'BCHOW' heeft, dan heeft dat tot gevolg dat alleen de inspecties bij een Inrichting (de ontbrekende V) zelfstandige zaken zijn voor het externe zaaksysteem.
* De kolom *zaak/dms nummer* (dvintzaakcode) moet een lege waarde hebben.
* Rechten: de inlogger moet lid zijn van rechtengroep die bij de Inspecties bij de betrokken module (dus bijvoorbeeld inspectierechten bij handhavingen) *wijzigen externe zaaknummers* aangevinkt heeft staan.
* Wat betreft blokkering: de inspectiezaak is geblokkeerd indien onderstaande item waar is:
  * de instelling *Sectie: InspectieMilieu en Item: NietBlokkerenMetHoofdzaak* is NIET aangevinkt (of bestaat niet) EN de blokkering van de onderliggende zaak is WEL gevuld.
* Zaaktype:
  * indien de hoofdzaak WEL valt onder een compartiment, maar de inspecties niet dan de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: ZaaktypeInspectietraject* (en deze instelling moet aangevinkt zijn)
  * indien de hoofdzaak NIET valt onder een compartiment dan ook de kolom *Tekst* van *Sectie: Koppeling ZAAK* en *Item: ZaaktypeInspectietraject* (en deze instelling moet aangevinkt zijn)
  * indien de hoofdzaak WEL valt onder een compartiment inclusief inspecties dan de kolom dvdmszaaktypeinspecties bij de compartimentdefinitie (moet dus gevuld zijn).
* De aanvrager (bij een inspectie de organisatie zelf) is het contactadres waarvan:
  * indien de hoofdzaak NIET valt onder een compartiment  de ID (dnkey) staat in de kolom *Getal1* van de instelling *Sectie: Koppeling Zaak* en *Item: Zender_Organisatie* (moet gevuld zijn)
  * indien de hoofdzaak WEL valt onder een compartiment de ID (dnkey) staat in de kolom dnkeyorganisatie van het compartiment (beheerportaal-Nieuw).

### Logging

De berichten kunnen gelogd worden op 2 manieren:

* Loggen in tbMessagelog (beheertegel *Messagelog*) Deze logging staat aan indien de instelling aangevinkt is van *Sectie: OWB* en *Item: MessageLog*. In kolom *Getal1* van deze instelling staat het aantal dagen dat de loggingskaarten bewaard moeten blijven. Default is dat 31.
* Indien de instelling *Sectie: OWB* en *Item: Loggen* aangevinkt is dan worden de berichten onder een door OpenWave te bepalen naam (bijvoorbeeld 1.1345123012_VanOW_naarZaak) op een logmap van de server geplaatst (om die te zien zijn dus systeembeheerrechten noodzakelijk).

### Opmaak

Bijzonderheden bij de opmaak van het creeerZaak_lk01 bericht.

* object:
  * **Kolom omschrijving** wordt gevuld met indien:  
  * omgevingszaak: de (DMS) zaaktypeomschrijving (portaal Zaakbeheer, tegel *Zaaktypes omgeving*) tenzij de instelling *koppeling Zaak en Item: AanvraagNaamipvZaaktypeoms* is aangevinkt (of bij een compartiment -indien de tbcompartiment.dlaanvrgnmipvzaaktype de waarde T heeft) dan wordt de zaakomschrijving (dvaanvraagnaam) van de omgevingszaak zelf doorgegeven
  * handhavingszaak: de (DMS) zaaktypeomschrijving (portaal Zaakbeheer, tegel *Zaaktypes handhaving*) tenzij de instelling *koppeling Zaak en Item: AanvraagNaamipvZaaktypeoms* is aangevinkt (of bij een compartiment -indien de tbcompartiment.dlaanvrgnmipvzaaktype de waarde T heeft) dan wordt de zaakomschrijving (dvomsbouwwerk) van de handhavingszaak zelf doorgegeven
  * APV/Overig: de (DMS) zaaktypeomschrijving (portaal Zaakbeheer, tegel *Zaaktypes apv/overig*) tenzij de instelling *koppeling Zaak en Item: AanvraagNaamipvZaaktypeoms* is aangevinkt (of bij een compartiment -indien de tbcompartiment.dlaanvrgnmipvzaaktype de waarde T heeft) dan wordt de zaakomschrijving (aard werkzaamheden + dvpublbouwwerk) van de APV/Overig zaak zelf doorgegeven
  * milieu/gebruik: de (DMS) zaaktypeomschrijving (portaal Zaakbeheer, tegel *Zaaktypes milieu/gebruik*) tenzij de instelling *koppeling Zaak en Item: AanvraagNaamipvZaaktypeoms* is aangevinkt (of bij een compartiment -indien de tbcompartiment.dlaanvrgnmipvzaaktype de waarde T heeft) dan wordt de zaakomschrijving (aard werkzaamheden + dvpublbouwwerk) van de milieu/gebruikzaak zelf doorgegeven
  * infoaanvraag: de (DMS) zaaktypeomschrijving (portaal Zaakbeheer, tegel *Zaaktypes infoaanvragen*) tenzij de instelling *koppeling Zaak en Item: AanvraagNaamipvZaaktypeoms* is aangevinkt (of bij een compartiment -indien de tbcompartiment.dlaanvrgnmipvzaaktype de waarde T heeft) dan wordt de zaakomschrijving (dvomschrijving) van de infozaak zelf doorgegeven
  * horecavergunning: de (DMS) zaaktypeomschrijving (portaal Zaakbeheer, tegel *Zaaktypes horeca*) tenzij de instelling *koppeling Zaak en Item: AanvraagNaamipvZaaktypeoms* is aangevinkt (of bij een compartiment -indien de tbcompartiment.dlaanvrgnmipvzaaktype de waarde T heeft) dan wordt de zaakomschrijving (het uitbaten van + soort onderneming) van de horecazaak zelf doorgegeven
  * Inrichting dan de waarde van kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en Item: ZaaktypeOmsInrichting*
  * deelzaak adviezen dan de waarde van kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en Item: ZaaktypeOmsAdvies*
  * deelzaak inspecties dan de waarde van kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: ZaaktypeOmsInspectietraject*
  * deelzaak bezwaarberoep dan de waarde van kolom *dvdmszaaktypeoms* van de tabel tbsoortbezwaar.
    * **Blok kenmerk** (kan meerdere keren voorkomen):
  * Tag kenmerk:
              *wordt default gevuld met de deeplink naar de bijbehorende OpenWave (hoofdzaak) zaak, bijv. #omgevingdetail/56478
              * indien instelling *Sectie: Koppeling ZAAK* en *Item: Kenmerk* de waarde *Zaakcode* heeft dan wordt de tag gevuld met de wavezaakcode van de hoofdzaak eventueel gevolgd door de zaakcode van de deelzaak (dus als het om een inspectiezaak gaat kan er komen te staan: 2018OW0089-2018INSP7676).
  * Tag bron met 'OpenWave'.
    * **Blok kenmerk**
  * Tag kenmerk wordt gevuld met tbomgvergunning.dvlvoaanvraagnummer indien gevuld.
  * Tag bron met 'OLO' indien dat dvlvoaanvraagnummer slaat op een OLO-zaak (in dat geval is dnkeydsoproject leeg) of met 'DSO' indien dat dvlvoaanvraagnummer slaat op een DSO-zaak (in dat geval is dnkeydsoproject gevuld).
  * Tag: zaakniveau krijgt waarde 2 en tag: deelzakenIndicatie  krijgt waarde J indien aanmaak vanuit inspectietraject waarbij de onderliggende zaak of inrichting een gevulde externe zaak/DMS code (dvintzaakcode) heeft.

* ExtraElementen
  * Dit blok (laatste onderdeel van blok object) wordt alleen opgenomen indien:
    * aanmaak vanuit inspectietraject waarbij de onderliggende zaak of inrichting een gevulde externe zaak/DMS code heeft.

 Dit gebeurt met attribuut naam="isDeelzaakVan"

* (en/of) de kolom bevoegd gezag (dnkeyoinbevgezag) is gevuld van de hoofdzaak. De organisatienaam uit de beheertabel tboin wordt hiervoor gebruikt (where dnkey = dnkeyoinbevgez). Dit gebeurt met attribuut naam gedefinieerd door de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK Item: ElementnaamBevGez*. Default heeft deze instelling de waarde *instantie*.

* isvan
  * Wordt gevuld met zaaktype van extern systeem:
  * De omschrijving van het zaaktype wordt alleen gevuld indien de instelling *Sectie: Koppeling Zaak en Item: ZaaktypeOmschrijvingVullen* aangevinkt is en die omschrijving bekend is. Deze omschrijving staat bij de definitie van de zaaktypes (beheerportaal). Voor adviezen, inspecties en inrichtingen kijkt OpenWave naar de kolom *Tekst* van de instellingen:
    * *Sectie: Koppeling Zaak en Item: ZaaktypeOmsAdvies*
    * *Sectie: Koppeling Zaak en Item: ZaaktypeOmsInspectietraject*
    * *Sectie: Koppeling Zaak en Item: ZaaktypeOmsInrichting*.

* heeftBetrekkingOp (AOA)
  * Wordt alleen opgenomen indien huisnummer en postcode (van de locatie) gevuld zijn en huisnummer ongelijk 0 of 99999.
* heeftBetrekkingOp (OPR)
  * Wordt alleen opgenomen indien (huisnummer of postcode (van de locatie) leeg is) of ( huisnummer gelijk aan 0 of 99999).
* heeftBetrekkingOp (GEM)
  * Wordt gevuld met gemeentegegevens van locatie.
* heeftBetrekkingOp (VES)
  * Wordt alleen opgenomen indien handelsnaam en/of inrichtingsnaam van (gekoppelde) inrichting gevuld is.
* heeftAlsBelanghebbende (VES)
  * Wordt alleen opgenomen indien handelsnaam en/of inrichtingsnaam van (gekoppelde) inrichting gevuld is.
* heeftAlsGemachtigde (NPS)
  * Wordt alleen opgenomen indien:
    * gemachtigde aan zaak is verbonden (dus NIET bij inrichtingen, inspecties, adviezen en handhaving)
    * EN handelsnaam/bedrijfsnaam is leeg
    * EN vestigingsnummer is leeg
    * EN RSIN-nummer is leeg.  
  * Indien het BSN-nummer van de gemachtigde leeg is, wordt gekeken naar de kolom *Tekst* van de instelling *Koppeling ZAAK en Item: DefaultBSN*. Indien gevuld, wordt in beide gevallen de tag inp.bsn gebruikt. Indien zowel de BSN-defaultwaarde als de BSN-waarde van de contactadresaart leeg is dan zal OpenWave i.p.v. de tag  inp.bsn, de tag anp.identificatie gebruiken. Deze wordt gevuld met de waarde van de kolom tbcontactadressen.dvnpnapn. Indien de instelling *Sectie: koppeling ZAAK en Item: AutoNpnAnp|Aanvinkvakje* aangevinkt is en de gemachtigde heeft een leeg vestigingsnummer EN een leeg BSN-nummer EN een leeg Kvk-nummer EN een leeg NPANP-nummer (NatuurlijkpersoonAnderePersoonsIdentificatie) dan wordt bij het versturen van een creerzaakbericht naar het DMS de kolom tbcontactadressen.dvNpnAnp eerst automatisch gevuld.
* heeftAlsGemachtigde (NNP)
  * Wordt alleen opgenomen indien:
    * gemachtigde aan zaak is verbonden (dus NIET bij inrichtingen, inspecties, adviezen en handhaving)
    * En het vestigingsnummer leeg is
    * EN
              *OF handelsnaam/bedrijfsnaam gevuld is
              * OF KvK-nummer gevuld
              * OF RSIN-nummer gevuld.
  * Indien zowel het KvK-nummer als het RSIN-nummer van de gemachtigde leeg is, wordt gekeken naar de kolom *Tekst* van de instelling *Koppeling ZAAK en Item: DefaultNNPid*.
* heeftAlsGemachtigde (VES)
  * Wordt alleen opgenomen indien:
    * gemachtigde aan zaak is verbonden (dus NIET bij inrichtingen, inspecties, adviezen en handhaving)
    * EN het vestigingsnummer gevuld is.
* heeftAlsInitiator (NPS)
  * Wordt alleen opgenomen indien:
    * initiator aan zaak is verbonden. Bij tbadviezen of tbhandhavingen of tbinspecties of tbmilinrichtingen wordt de aanvrager gedefinieerd door de instelling met *Sectie: Koppeling Zaak* en *Item: Zender_Organisatie*. In *Getal1* staat de dnkey van tbcontactadressen die als initiator moet dienen (die dus verwijst naar de organisatie zelf). Anders bij deelzaak Bezwaar/beroep kijkt OpenWave naar adresrol IND, **Anders, dan kijkt het programma naar de contactpersonen bij de zaak waarvan de adresrol overeenkomt met de opgegeven waarde van de kolom dvadressoortverpl van het betreffende zaaktype** (portaal Zaakbeheer: tegel *Zaaktypes omgeving, APV/overig* etc.). Indien er meerdere contactpersonen zijn met die rol, dan wordt degene met de hoogste dnkeywaarde gepakt. Indien de kolom dvadressoortverpl leeg is valt OpenWave terug op *Geta1l* van instelling met *Sectie: Koppeling Zaak* en *Item: Zender_Organisatie*.
    * EN handelsnaam/bedrijfsnaam leeg is
    * EN vestigingsnummer leeg is
    * EN RSIN-nummer leeg is.
  * Indien het BSN-nummer van de aanvrager leeg is, wordt gekeken naar de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK en Item: DefaultBSN*. Indien gevuld, wordt in beide gevallen de tag inp.bsn gebruikt. Indien zowel de BSN-defaultwaarde als de BSN-waarde van de contactadresaart leeg is dan zal OpenWave i.p.v. de tag  inp.bsn, de tag anp.identificatie gebruiken. Deze wordt gevuld met de waarde van de kolom tbcontactadressen.dvnpnapn. Indien de instelling *Sectie: Koppeling ZAAK en Item: AutoNpnAnp|Aanvinkvakje* aangevinkt is en de aanvrager heeft een leeg vestigingsnummer EN een leeg BSN-nummer EN een leeg Kvk-nummer EN een leeg NPANP-nummer (NatuurlijkpersoonAnderePersoonsIdentificatie) dan wordt bij het versturen van een creerzaakbericht naar het DMS de kolom tbcontactadressen.dvNpnAnp eerst automatisch gevuld.
* heeftAlsInitiator (NNP)
  * Wordt alleen opgenomen indien:
    * initiator aan zaak is verbonden. Zie hierboven bij NPS
    * En het vestigingsnummer leeg is
    * EN
              *OF handelsnaam/bedrijfsnaam gevuld is
              * OF KvK-nummer gevuld
              * OF RSIN-nummer gevuld.
  * Indien zowel het KvK-nummer als het RSIN-nummer van de gemachtigde leeg is, wordt gekeken naar de kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK en Item: DefaultNNPid*.
* heeftAlsInitiator (VES)
  * Wordt alleen opgenomen indien:
    * initiator aan zaak is verbonden. Zie hierboven bij NPS
    * EN het vestigingsnummer gevuld is.
* heeftAlsUitvoerende (MDW)
  * Wordt alleen opgenomen indien *Sectie: Koppeling ZAAK* en *Item: BehandelaarDoorgeven* aangevinkt staat en *Getal2* de waarde 2 of 3 heeft. Bij advies gaat het om de adviesverantwoordelijke, bij inspecties om de hoofdinspecteur en anders om de *actieve in behandeling bij* Indien
      **Getal1* heeft de waarde 1 dan wordt de gemeente-id van de zaak + de medewerkerscode van de dossierbehandelaar als identificatie van de medewerker gebruikt
      **Getal1* heeft de waarde 2 dan wordt de gemeente-id van de zaak + de loginnaam van de dossierbehandelaar als identificatie van de medewerker gebruikt
      **Getal1* heeft de waarde 3 dan wordt de gemeente-id van de zaak + de vaste waarde kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: Behandelaardoorgeven* gebruikt
      **Getal1* is anders dan blijft de identificatie leeg.
* heeftAlsVerantwoordelijke (MDW)
  * Wordt alleen opgenomen indien *Sectie: Koppeling ZAAK* en *Item: BehandelaarDoorgeven* aangevinkt staat en *Getal2* de waarde 1 of 3 heeft. Bij advies gaat het om de adviesverantwoordelijke, bij inspecties om de hoofdinspecteur en anders om de *actieve in behandeling bij* Indien:
      **Getal1* heeft de waarde 1 dan wordt de gemeente-id van de zaak + de medewerkerscode van de dossierbehandelaar als identificatie van de medewerker gebruikt
      **Getal1* heeft de waarde 2 dan wordt de gemeente-id van de zaak + de loginnaam van de dossierbehandelaar als identificatie van de medewerker gebruikt
      **Getal1* heeft de waarde 3 dan wordt de gemeente-id van de zaak + de vaste waarde kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: Behandelaardoorgeven* gebruikt
      **Getal1* is anders dan blijft de identificatie leeg.
* heeft (STT)
  * Wordt gevuld met de externe code en omschrijving van de tabel tbzaakstatus (beheer) voor de kaart met wavecode = 'StatusInBehandeling'
  * isGezetDoor wordt gevuld met de medewerker gegevens van de inlogger (kan hier dus ook een robot zijn). Het programma kijkt hier naar *Getal1* van de instelling *Sectie: Koppeling ZAAK* en *Item: BehandelaarDoorgeven*. De tag <identficatie> wordt gevuld met Indien
      **Getal1* heeft de waarde <> 2 en ook <> 3 dan wordt de gemeente-id van de zaak + de medewerkerscode van de dossierbehandelaar als identificatie van de medewerker gebruikt
      **Getal1* heeft de waarde 2 dan wordt de gemeente-id van de zaak + de loginnaam van de dossierbehandelaar als identificatie van de medewerker gebruikt
      **Getal1* heeft de waarde 3 dan wordt de gemeente-id van de zaak + de vaste waarde kolom *Tekst* van de instelling *Sectie: Koppeling ZAAK* en *Item: Behandelaardoorgeven* gebruikt.

### Testen met fake endpoint

De opmaak van de uitgaande berichten (genereerzaakidentificatie en creeerzaak) kan getest worden zonder dat er een luisterend ontvangstadres is, door de instelling *Sectie: Koppeling ZAAK* en *Item: TestOpFakeEndpoint* aan te vinken. Als ontvangstadres_vrijeberichten en ontvangstadres_asynchroon kan dan bijvoorbeeld [www.rem.nl](http://www.rem.nl.md) ingevoerd worden. OpenWave genereert in dit geval zelf een unieke zaakidentificatie waarmee dan een creeerzaakbericht wordt gemaakt. In de messagelog is deze te zien.
