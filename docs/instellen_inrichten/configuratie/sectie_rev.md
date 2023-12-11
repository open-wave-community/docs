# Sectie REV

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de *Sectie: REV* (registratie externe veiligheid) gerangschikt op item. Zie ook *Sectie Inrichtingen en Item: REVNamespaceIdentificatie*.

## Items Configuratietabel

| Item | Kolom | Omschrijving |
|---|---|---|
| AlgemeenEndpoint | Tekst |Het algemene gedeelte van het endpoint waar de Json berichten naar toe moeten dus bijv. <https://acc.apps.geodan.nl> /public/revpreproductie/rev/api/rev/v3 |
| ApiKey | Tekst |Een sleutel die per organisatie samen met de bronhouderscode wordt geleverd door Geodan. Beide zijn nodig voor het verzenden van de Json berichten |
| Bronhouder | Tekst |Een code, bijvoorbeeld 00002, die samen met de ApiKey wordt geleverd door Geodan. Beide zijn nodig voor het verzenden van de Json berichten |
| ExportTest | Aanvinkvakje |Indien aangevinkt worden de Json berichten met de toevoeging validateOnly=true naar het endpoint verstuurd en opgeslagen in de messagelog. De exportdatum zal hierbij nooit worden gevuld |
| ImportBronObjectId | Getal1| Indien 1 dan wordt de waarde van de bronobjectID van de locatieEV-activiteit bij het samenstellen van de synchronisatielijst geinterpreteerd als een inrichtingnummer op grond waarvan OpenWave de bijbehorende dnkey uit tbmilinrichtingen kan koppelen |
| KwetsbaarGebZichtbaar | Aanvinkvakje |Indien aangevinkt dan is in het inrichtportaal de tegel *REV kwetsbare gebouwen/locaties* zichtbaar |
| Messagelog | Aanvinkvakje |Indien aangevinkt worden de Json berichten gelogd in de Messagelogtabel (mits ook de algemene instelling *Sectie: OWB en Item: Messagelog* aangevinkt is |
