# Portalkolommen

Screenidentifiers: MDLC_getPortalColumnsList.xml en MDDC_getPortalColumnsDetail.xml

## Betekenis van de kolommen

* De **kolomnaam** mag aangepast worden, maar bij updatescripts van OpenWave versie x naar OpenWave versie y worden sommige kolomnamen verondersteld aanwezig te zijn om bijvoorbeeld nieuwe tegels onder te plaatsen. Indien die kolomnamen er niet meer zijn dan worden deze kolommen opnieuw aangemaakt met hun oorspronkelijke naam. Zo kunnen er doublures in kolommen ontstaan. Op zich niet erg, want de nieuwe tegels kunnen zonder gevaar verplaatst worden naar een andere kolom binnen hetzelfde portaal.
* Met de **kolomvolgorde** kan de volgorde van de kolommen horizontaal binnen een [portal](/docs/instellen_inrichten/portaldefinitie.md) worden bepaald.
* Indien de kolom **Is kolom voor van buitenaf toevoegen nieuwe tegels** is aangevinkt dan is deze kolom bedoeld om van buiten af - bijvoorbeeld met een updatescript - tegels toe te voegen. De nieuwe tegels worden dan default onder deze aangevinkte kolom geplaatst. De beheerder kan ze dan desgewenst verplaatsen naar een andere kolom. Per [portalname](/docs/instellen_inrichten/portaldefinitie/portalnaam.md) kan er maar één kolom deze eigenschap hebben. Dit wordt op de database afgevangen.

## Verplaatsen van kolom

Verplaatsen van kolommen van de ene portal naar de andere portal.

**NIET AAN TE RADEN DUS NIET DOEN!!**

Eigenwijs: de eenvoudigste manier is om op het detailscherm van de kolom de waarde van *primary key van portalname* aan te passen (met een bestaande waarde).

Dit gaat echter mis wanneer in de actions van de onderliggende tegels de variabele {id} wordt gebruikt. Die is namelijk echt gelieerd aan de primary key van de zaakportalen.

Voorbeeld: een kolom bij portaal omgevingdetail waaronder een tegel geplaatst is met een action *getFlexList(TBADVIEZEN,TBOMGVERGUNNING,{id},O,W)* kan natuurlijk verplaatst worden naar het portaal APV/Overigdetail. De tegel verhuist dan mee, terwijl die niet gedefinieerd is voor dit portaal. Het indrukken van de tegel heeft tot gevolg heeft dat adviezen worden gezocht bij een omgevingszaak met de id van een APV/Overige zaak.
