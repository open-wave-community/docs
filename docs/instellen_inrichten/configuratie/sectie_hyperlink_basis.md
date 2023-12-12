# Sectie Hyperlink_basis

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de _Sectie: Hyperlink_basis_ gerangschikt op item. Deze instellingen zijn alleen van belang indien:

- gebruik gemaakt wordt van de fileserver (_Sectie: Documenten en Item: ophalenviafileserver_ is aangevinkt) voor het opslaan en ophalen van documenten
- en wanneer gebruik gemaakt wordt van Microsoft IE/ of Edge die als trusted zijn gedefinieerd voor Open-Wave
- en wanneer het IP-adres waarvandaan wordt ingelogd toegang heeft tot de fileserver.

Zie [Hyperlink](/docs/instellen_inrichten/hyperlink.md).

## Items Configuratietabel

| Item       | Kolom | Omschrijving                                                                                    |
|------------|-------|-------------------------------------------------------------------------------------------------|
| Bouw       | Tekst | In de kolom _Tekst_ staat de basismap beginnend met de documentroot (_Sectie: Documenten en Item: documentroot_) die bij het creëren van een nieuwe bouw/sloopzaak in de kolom dvhyperlink wordt geplaatst, waarbij de variabelen |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar van de ontvangst/aanvraagdatum   |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar + de twee cijfers van de maand van de ontvangst/aanvraagdatum |
|            |       | `%zaaknr%` door de Wave-zaakcode van de bouw/sloopzaak                                          |
| Handhaving | Tekst | In de kolom _Tekst_ staat de basismap beginnend met de documentroot (_Sectie: Documenten en Item: documentroot_) die bij het creëren van een nieuwe handhavingszaak in de kolom dvhyperlink wordt geplaatst, waarbij de variabelen |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar van de startdatum                |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar + de twee cijfers van de maand van de startdatum |
|            |       | `%zaaknr%` door de Wave-zaakcode van de handhavingszaak                                         |
| Horeca     | Tekst | In de kolom _Tekst_ staat de basismap beginnend met de documentroot (_Sectie: Documenten en Item: documentroot_) die bij het creëren van een nieuwe horecazaak in de kolom dvhyperlink wordt geplaatst, waarbij de variabelen |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar van de ontvangst/aanvraagdatum   |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar + de twee cijfers van de maand van de ontvangst/aanvraagdatum |
|            |       | `%zaaknr%` door de Wave-zaakcode van de horecazaak                                              |
| Info       | Tekst | In de kolom _Tekst_ staat de basismap beginnend met de documentroot (_Sectie: Documenten en Item: documentroot_) die bij het creëren van een nieuwe infoaanvraagzaak in de kolom dvhyperlink wordt geplaatst, waarbij de variabelen |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar van de ontvangst/aanvraagdatum   |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar + de twee cijfers van de maand van de ontvangst/aanvraagdatum |
|            |       | `%zaaknr%` door de Wave-zaakcode van de infoaanvraag                                            |
| Inrichtng  | Tekst | In de kolom _Tekst_ staat de basismap beginnend met de documentroot (_Sectie: Documenten en Item: documentroot_) die bij het creëren van een nieuwe inrichting in de kolom dvhyperlink wordt geplaatst, waarbij de variabele `%zaaknr%` wordt vervangen door het inrichtingsnummer |
| MilGebr    | Tekst | In de kolom _Tekst_ staat de basismap beginnend met de documentroot (_Sectie: Documenten en Item: documentroot_) die bij het creëren van een nieuwe milieu/gebruik zaak in de kolom dvhyperlink wordt geplaatst, waarbij de variabelen |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar van de ontvangst/aanvraagdatum   |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar + de twee cijfers van de maand van de ontvangst/aanvraagdatum |
|            |       | `%zaaknr%` door de Wave-zaakcode van de milieu/gebruik zaak                                     |
| Omgeving   | Tekst | In de kolom _Tekst_ staat de basismap beginnend met de documentroot (_Sectie: Documenten en Item: documentroot_) die bij het creëren van een nieuwe omgevingszaak in de kolom dvhyperlink wordt geplaatst, waarbij de variabelen |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar van de ontvangst/aanvraagdatum   |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar + de twee cijfers van de maand van de ontvangst/aanvraagdatum |
|            |       | `%zaaknr%` door de Wave-zaakcode van de omgevingszaak                                           |
| Overige    | Tekst | In de kolom _Tekst_ staat de basismap beginnend met de documentroot (_Sectie: Documenten en Item: documentroot_) die bij het creëren van een nieuwe APV/Overige-zaak in de kolom dvhyperlink wordt geplaatst, waarbij de variabelen |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar van de ontvangst/aanvraagdatum   |
|            |       | `%zaakjaar%` wordt vervangen door de vier cijfers van het jaar + de twee cijfers van de maand van de ontvangst/aanvraagdatum |
|            |       | `%zaaknr%` door de Wave-zaakcode van de APV/Overige-zaak                                        |
