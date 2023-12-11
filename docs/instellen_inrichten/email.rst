E-mail SMTP instellingen
========================

Zie ook `E-mail </docs/functionaliteiten/email.md>`__

Instellingen die nodig zijn om vanuit OpenWave een SMTP-server
(uitgaande email) aan te kunnen spreken. Het gaat om de volgende kaarten
in tbinitialisatie (beheertegel
`Configuratie </docs/instellen_inrichten/configuratie.md>`__).

-  *Sectie: Web.mail* en *Item: debug*. Aan of uitvinken. Normaal uit.
-  *Sectie: Web.mail* en *Item: mime.address.strict*. Aan of uitvinken.
   Normaal aan.
-  *Sectie: Web.mail* en *Item: smtp.authentication*. Aan of uitvinken.
   Normaal aan.
-  *Sectie: Web.mail* en *Item: transport.protocol*.

   -  De kolom *Tekst* moet de waarde smtp hebben
   -  De kolom *Getal1* is de mail.smtp.port van de mailserver (meestal
      25). Indien StartTLS encryptie dan 587
   -  De instelling MOET aangevinkt staan!!!
   -  De kolom *Info* moet gevuld indien smtp.authentication aangevinkt
      is en bestaat uit de volgende onderdelen gescheiden door een
      dubbele punt (bijvoorbeeld:
      *mail.openu.nl:LOGIN:REALM:sesam:12C34)*:

      -  the host name of the mail
      -  the authentication method
      -  the authentication realm (for digest md5)
      -  the authentication username
      -  the encrypted (rem-encryptie) authentication password

   -  De kolom *Info* bestaat indien smtp.authentication uit staat,
      alleen uit the host name of the mail. \*\* Sectie: Web.mail\ *en
      Item: smtp.starttls.enable\*. Aan of uitvinken. Default = uit.
      Indien aan gevinkt dan wordt STARTTLS encryptie aangezet bij het
      versturen van mail. Let op: de poort moet dan worden ingesteld op
      \**587\*. Zie Getal1 van instelling*\ Sectie: Web.mail en Item:
      transport.protocol\*.

-  In de kolom *Tekst* van *Sectie: Web.mail en Item:
   smtp.ssl.protocols* kan de TLS-versie worden opgegeven. Aangeraden
   wordt TLSv1.2. Meerdere opties kunnen worden opgegeven gescheiden
   door een spatie bijvoorbeeld: TLSv1.1 TLSv1.2. Indien leeg gelaten
   dan wordt het aan de server overgelaten. Mogelijke opties:

   -  TLSv1
   -  TLSv1.1
   -  TLSv1.2

-  In de kolom *Tekst* van *Sectie: Web.mail en Item: smtp.ssl.trust*
   kan de mailserver als vertrouwde host worden gemarkeerd door de
   server hostnaam hierin op te slaan. Er vindt dan geen controle plaats
   op het server certificaat. Laat deze leeg indien geen problemen
   worden ervaren met het versturen en ontvangen van mail. Hierdoor
   wordt altijd op de geldigheid van het servercertificaat
   gecontroleerd.
