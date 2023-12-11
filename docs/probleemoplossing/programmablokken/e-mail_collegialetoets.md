# Email vanuit collegiale toets

Bij een geregistreerd document waar een collegiale toetsing op staat, kan vanuit het collegiale toetsing detailscherm met de knop linksonder eenmalig een email verstuurd worden naar de collegiale toetser.

## Noodzakelijke instellingen

* De instelling *Sectie: Documenten* en *Item:CtMail* moet aangevinkt staan
* EN de bovenliggende hoofdzaak (dus bijvoorbeeld de omgevingszaak waar het document onder hangt) mag niet geblokkeerd zijn
* EN de **email van de collegiale toetser** bij de medewerkerstabel moet gevuld zijn met een valide emailadres (de ontvanger van de email)
* EN de **email van de inlogger** bij de medewerkerstabel moet gevuld zijn met een valide emailadres
* EN de **webmailinstellingen** moeten kloppen: zie bij Instellen/Inrichten [Email](/docs/instellen_inrichten/email.md)
* EN bij de **Emailsjablonen** moet er voor de gewenste module een sjabloon bestaan waarbij de eigenschap *Is sjabloon voor standaardmail naar collegiale toetser?* aangevinkt staat en *Benaderbaar vanuit tabel* de waarde *tbcorrespcollegtoets* heeft. **Let op**: er kan per module maar 1 sjabloon zijn met eigenschap *Is sjabloon voor standaardmail naar collegiale toetser*!
* EN het veld ***Toetser gemaild*** (ddmailverstuurd) is leeg. Dit veld wordt gevuld wanneer de mail verstuurd wordt, wat betekent dat de mail maar eenmalig verstuurd kan worden.

> [!NOTE] **Goed om te weten**: er zal bij opstellen van de mail niet gekeken worden naar of er input parameters bij het sjabloon staan opgegeven, eveneens wordt er niet gekeken naar eigenschappen als  *Bijlagen toevoegen*, *Documentnaam* etc. De mail wordt niet opgeslagen namelijk.
