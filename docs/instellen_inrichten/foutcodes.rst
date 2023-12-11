Foutcodes/-afhandeling
======================

Als er in de uitvoer van de programmatuur een fout optreedt, verschijnt
een foutmelding in OpenWave. Deze foutmeldingen zijn, afhankelijk van
waar in het proces de fout optreedt, niet altijd even duidelijk. Voor
een deel van de programmatuur is ingebouwd dat bij optreden van een fout
door het ontbreken van een bepaalde instelling, er onder de tegel
*Ontbrekende configuratieitems* een regel verschijnt welke instelling
ontbreekt.

Hieronder een foutcodes en hun omschrijving:

+----------------------+----------------------------------------------+
| Algemene foutcodes   | Omschrijving                                 |
+======================+==============================================+
| ``100``              | Systeemfout: fout in configuratiebestand     |
+----------------------+----------------------------------------------+
| ``200``              | Systeemfout: er kan geen databaseverbinding  |
|                      | gemaakt worden                               |
+----------------------+----------------------------------------------+
| ``201``              | Systeemfout: er is verwerkingsprobleem in de |
|                      | database opgetreden                          |
+----------------------+----------------------------------------------+
| ``202``              | Systeemfout: de database kon niet worden     |
|                      | bijgewerkt                                   |
+----------------------+----------------------------------------------+
| ``203``              | Het systeem is momenteel in onderhoud,       |
|                      | probeer het later opnieuw                    |
+----------------------+----------------------------------------------+
| ``204``              | Systeemfout: ongeldige database versie voor  |
|                      | dit product                                  |
+----------------------+----------------------------------------------+
| ``205``              | Systeemfout: fout tijdens het sluiten van    |
|                      | een database statement                       |
+----------------------+----------------------------------------------+
| ``206``              | Fout tijdens het lezen uit de database       |
+----------------------+----------------------------------------------+
| ``207``              | Ontbrekende instellingen                     |
+----------------------+----------------------------------------------+
| ``208``              | Ongeldige instellingen                       |
+----------------------+----------------------------------------------+
| ``209``              | Systeemfout: de database kon niet worden     |
|                      | bijgewerkt(insert)                           |
+----------------------+----------------------------------------------+
| ``210``              | Systeemfout: de database kon niet worden     |
|                      | bijgewerkt(delete)                           |
+----------------------+----------------------------------------------+
| ``211``              | Er zijn 0 nieuwe regels aangemaakt           |
+----------------------+----------------------------------------------+
| ``212``              | Wijzigen is niet toegestaan                  |
+----------------------+----------------------------------------------+
| ``213``              | Systeemfout: de database kon niet worden     |
|                      | bijgewerkt(update)                           |
+----------------------+----------------------------------------------+
| ``299``              | Systeemfout: API versie te laag om de invoer |
|                      | te verwerken                                 |
+----------------------+----------------------------------------------+
| ``300``              | Systeemfout: ongeldige aanroep van een       |
|                      | systeemfunctie                               |
+----------------------+----------------------------------------------+
| ``301``              | Systeemfout: ongeldige xml indeling          |
+----------------------+----------------------------------------------+
| ``302``              | Systeemfout: ontbrekend xsd bestand          |
+----------------------+----------------------------------------------+
| ``303``              | Systeemfout: ontbrekend xml bestand          |
+----------------------+----------------------------------------------+
| ``400``              | Systeemfout: IO error zonder details         |
+----------------------+----------------------------------------------+
| ``401``              | Systeemfout: Samba IO error                  |
+----------------------+----------------------------------------------+
| ``402``              | Systeemfout: Bestand bestaat niet            |
+----------------------+----------------------------------------------+
| ``403``              | Systeemfout: Map bestaat niet                |
+----------------------+----------------------------------------------+
| ``405``              | Systeemfout: fout tijdens het sluiten van    |
|                      | een IO stream                                |
+----------------------+----------------------------------------------+
| ``406``              | Systeemfout: Bestandgrootte groter dan       |
|                      | toegestane limiet                            |
+----------------------+----------------------------------------------+
| ``407``              | Systeemfout: Samba verbinding maken mislukt  |
+----------------------+----------------------------------------------+
| ``408``              | Systeemfout: Foutieve hostnaam of IP adres   |
+----------------------+----------------------------------------------+
| ``625``              | Systeemfout: de xml kon niet verwerkt worden |
+----------------------+----------------------------------------------+
| ``626``              | Systeemfout: een xml waarde kon niet         |
|                      | bijgewerkt worden                            |
+----------------------+----------------------------------------------+
| ``627``              | Systeemfout: de xml kon niet omgezet worden  |
+----------------------+----------------------------------------------+
| ``630``              | Systeemfout: de webservice kon niet gebruikt |
|                      | worden                                       |
+----------------------+----------------------------------------------+
| ``693``              | Tijd conversie fout                          |
+----------------------+----------------------------------------------+
| ``694``              | Tijd/Getal conversie fout                    |
+----------------------+----------------------------------------------+
| ``695``              | Getal conversie fout                         |
+----------------------+----------------------------------------------+
| ``696``              | Tekst encryptie/decryptie fout               |
+----------------------+----------------------------------------------+
| ``697``              | Tekst zip/unzip fout                         |
+----------------------+----------------------------------------------+
| ``698``              | Datum conversie fout                         |
+----------------------+----------------------------------------------+
| ``699``              | Systeemfout zonder details                   |
+----------------------+----------------------------------------------+
| Specifieke foutcodes | Omschrijving                                 |
+----------------------+----------------------------------------------+
| ``701``              | Onbekende medewerker en/of verkeerd          |
|                      | wachtwoord                                   |
+----------------------+----------------------------------------------+
| ``702``              | Wijzigen is mislukt                          |
+----------------------+----------------------------------------------+
| ``703``              | Onvoldoende rechten                          |
+----------------------+----------------------------------------------+
| ``704``              | Onbekende zaak                               |
+----------------------+----------------------------------------------+
| ``705``              | Onbekende id                                 |
+----------------------+----------------------------------------------+
| ``706``              | Ontbrekende instellingen                     |
+----------------------+----------------------------------------------+
| ``707``              | Dms zaakcode moet gevuld zijn. Geen nieuwe   |
|                      | externe checklist mogelijk                   |
+----------------------+----------------------------------------------+
| ``708``              | Inspectietraject reeds afgerond. Geen nieuwe |
|                      | externe checklist mogelijk                   |
+----------------------+----------------------------------------------+
| ``709``              | Inspectietraject heeft geen startdatum. Geen |
|                      | nieuwe externe checklist mogelijk            |
+----------------------+----------------------------------------------+
| ``710``              | Aanmaken of ophalen checklist niet gelukt    |
+----------------------+----------------------------------------------+
| ``711``              | Digitale checklist niet bekend               |
+----------------------+----------------------------------------------+
| ``712``              | Er zijn geen checklistitems die voldoen aan  |
|                      | de filter                                    |
+----------------------+----------------------------------------------+
| ``713``              | Er is al een koppeling                       |
+----------------------+----------------------------------------------+
| ``714``              | Aanmaken is mislukt                          |
+----------------------+----------------------------------------------+
| ``715``              | Inrichting of vergunning is geblokkeerd      |
+----------------------+----------------------------------------------+
| ``716``              | Deze functionaliteit is hier nog niet        |
|                      | operationeel                                 |
+----------------------+----------------------------------------------+
| ``717``              | Geen geodata gevonden                        |
+----------------------+----------------------------------------------+
| ``718``              | HTTP request mislukt                         |
+----------------------+----------------------------------------------+
| ``719``              | Verwijderen is mislukt                       |
+----------------------+----------------------------------------------+
| ``720``              | Loggen is mislukt                            |
+----------------------+----------------------------------------------+
| ``721``              | Pagina in ontwikkeling                       |
+----------------------+----------------------------------------------+
| ``722``              | Deze zaak is nog niet bekend in het DMS      |
+----------------------+----------------------------------------------+
| ``723``              | Het opslaan van een file is mislukt          |
+----------------------+----------------------------------------------+
| ``724``              | File niet gevonden                           |
+----------------------+----------------------------------------------+
| ``725``              | Een fout is opgetreden tijdens het verzenden |
|                      | van e-mail                                   |
+----------------------+----------------------------------------------+
| ``726``              | Zaak reeds afgerond. Geen nieuwe externe     |
|                      | checklist mogelijk                           |
+----------------------+----------------------------------------------+
| ``727``              | Bestandgrootte groter dan toegestane limiet  |
+----------------------+----------------------------------------------+
| ``728``              | Password is verlopen                         |
+----------------------+----------------------------------------------+
| ``729``              | Password mag niet gelijk zijn aan loginnaam  |
+----------------------+----------------------------------------------+
| ``730``              | Unlock-pincode is verlopen of ongeldig: een  |
|                      | nieuwe code is opgestuurd                    |
+----------------------+----------------------------------------------+
| ``731``              | Unlock-pincode is verlopen of ongeldig: een  |
|                      | nieuwe code kunt u bij de                    |
|                      | applicatiebeheerder vragen                   |
+----------------------+----------------------------------------------+
| ``732``              | Device unlockcode is verlopen of ongeldig:   |
|                      | een nieuwe toegangs-pin is opgestuurd        |
+----------------------+----------------------------------------------+
| ``733``              | Device unlockcode is verlopen of ongeldig:   |
|                      | een nieuwe toegangs-pin kunt u bij de        |
|                      | applicatiebeheerder vragen                   |
+----------------------+----------------------------------------------+
| ``734``              | Uw aanmelding is niet langer geldig: probeer |
|                      | opnieuw aan te melden                        |
+----------------------+----------------------------------------------+
| ``735``              | Inrichting of vergunning is ingetrokken      |
+----------------------+----------------------------------------------+
| ``741``              | Password tekens voldoen niet aan vereiste    |
+----------------------+----------------------------------------------+
| ``742``              | Password mag niet gelijk zijn aan het oude   |
|                      | password                                     |
+----------------------+----------------------------------------------+
| ``743``              | Password lengte voldoet niet aan vereiste    |
+----------------------+----------------------------------------------+
