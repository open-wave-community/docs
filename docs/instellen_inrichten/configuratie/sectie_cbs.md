# Sectie CBS

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie/sectie_aanmaakmappen.md) (tbinitialisatie) van de _Sectie: CBS_ gerangschikt op item.

Voor meer informatie omtrent CBS export functionaliteit in OpenWave zie [CBS export](/docs/probleemoplossing/programmablokken/cbs_export/README.md)

## Items Configuratietabel

| Item                                    | Kolom        | Omschrijving        |
|-----------------------------------------|--------------|---------------------|
| `<hier staat 4-cijferige gemeentecode>` | Tekst        | Bij het opstellen van de lijst **Te exporteren CBS-gegevens** wordt voor iedere exportregel het Gemeentenummer bepaald zoals deze volgens CBS dient te worden doorgegeven. Dit is default de 4-cijferige gemeentecode aangevuld met twee voorloopnullen. Het kan echter zo zijn dat men voor bepaalde gemeentes naast de 4-cijferige gemeentecode nog een aanvullende twee laatste cijfers wilt opgeven voor dit gemeentenummer in de CBS export. **Alleen in dat geval** dient deze instelling te worden aangemaakt: men geeft deze twee laatste cijfers op in kolom _Tekst_. Per gemeente waarvoor dit gewenst is maakt men deze instelling als volgt aan waarbij het item de 4-cijferige gemeentecode is. Voorbeeld: indien gemeentecode is 0228 en de extra twee cijfers zijn 02 dan dient instelling als volgt te worden aangemaakt: _Sectie: CBS_, _Item: 0228_, _Tekst = 02_. |
| DMScode                                 | Aanvinkvakje | Indien aangevinkt dan zal het programma bij het opstellen van de CBS export voor iedere CBS exportregel kijken of er een gevulde DMS zaakcode is: zo ja dan wordt deze als waarde voor kolom **Uw volgnummer** gebruikt in het exportbestand, zo nee dan wordt de Wave zaakcode gebruikt in het exportbestand. |
