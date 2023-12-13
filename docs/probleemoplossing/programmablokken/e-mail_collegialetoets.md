# Email vanuit collegiale toets

Bij een geregistreerd document waar een collegiale toetsing op staat, kan vanuit het collegiale toetsing detailscherm met de knop linksonder eenmalig een email verstuurd worden naar de collegiale toetser.

## Noodzakelijke instellingen

- De instelling _Sectie: Documenten_ en _Item:CtMail_ moet aangevinkt staan
- en de bovenliggende hoofdzaak (dus bijvoorbeeld de omgevingszaak waar het document onder hangt) mag niet geblokkeerd zijn
- en de **email van de collegiale toetser** bij de medewerkerstabel moet gevuld zijn met een valide emailadres (de ontvanger van de email)
- en de **email van de inlogger** bij de medewerkerstabel moet gevuld zijn met een valide emailadres
- en de **webmailinstellingen** moeten kloppen: zie bij Instellen/Inrichten [Email](../../../instellen_inrichten/email.md)
- en bij de **Emailsjablonen** moet er voor de gewenste module een sjabloon bestaan waarbij de eigenschap _Is sjabloon voor standaardmail naar collegiale toetser?_ aangevinkt staat en _Benaderbaar vanuit tabel_ de waarde _tbcorrespcollegtoets_ heeft. **Let op**: er kan per module maar 1 sjabloon zijn met eigenschap _Is sjabloon voor standaardmail naar collegiale toetser_!
- en het veld **_Toetser gemaild_** (ddmailverstuurd) is leeg. Dit veld wordt gevuld wanneer de mail verstuurd wordt, wat betekent dat de mail maar eenmalig verstuurd kan worden.

> [!NOTE] **Goed om te weten**: er zal bij opstellen van de mail niet gekeken worden naar of er input parameters bij het sjabloon staan opgegeven, eveneens wordt er niet gekeken naar eigenschappen als _Bijlagen toevoegen_, _Documentnaam_ etc. De mail wordt niet opgeslagen namelijk.
