# E-mail SMTP instellingen

Zie ook [E-mail](/functionaliteiten/email.md)

Instellingen die nodig zijn om vanuit OpenWave een SMTP-server (uitgaande email) aan te kunnen spreken. Het gaat om de volgende kaarten in tbinitialisatie (beheertegel _[Configuratie](/instellen_inrichten/configuratie/README.md)_).

- _Sectie: Web.mail_ en _Item: debug_. Aan of uitvinken. Normaal uit.
- _Sectie: Web.mail_ en _Item: mime.address.strict_. Aan of uitvinken. Normaal aan.
- _Sectie: Web.mail_ en _Item: smtp.authentication_. Aan of uitvinken. Normaal aan.
- _Sectie: Web.mail_ en _Item: transport.protocol_.
  - De kolom _Tekst_ moet de waarde smtp hebben
  - De kolom _Getal1_ is de mail.smtp.port van de mailserver (meestal 25). Indien StartTLS encryptie dan 587
  - De instelling MOET aangevinkt staan!!!
  - De kolom _Info_ moet gevuld indien smtp.authentication aangevinkt is en bestaat uit de volgende onderdelen gescheiden door een dubbele punt (bijvoorbeeld: _mail.openu.nl:LOGIN:REALM:sesam:12C34)_:
    - the host name of the mail
    - the authentication method
    - the authentication realm (for digest md5)
    - the authentication username
    - the encrypted (rem-encryptie) authentication password
  - De kolom _Info_ bestaat indien smtp.authentication uit staat, alleen uit the host name of the mail.
    ** Sectie: Web.mail*en Item: _smtp.starttls.enable\*. Aan of uitvinken. Default = uit. Indien aan gevinkt dan wordt STARTTLS encryptie aangezet bij het versturen van mail. Let op: de poort moet dan worden ingesteld op **587\*_. Zie _Getal1_ van instelling*Sectie: Web.mail en Item: transport.protocol\*.
- In de kolom _Tekst_ van _Sectie: Web.mail en Item: smtp.ssl.protocols_ kan de TLS-versie worden opgegeven. Aangeraden wordt TLSv1.2. Meerdere opties kunnen worden opgegeven gescheiden door een spatie bijvoorbeeld: TLSv1.1 TLSv1.2. Indien leeg gelaten dan wordt het aan de server overgelaten. Mogelijke opties:
  - TLSv1
  - TLSv1.1
  - TLSv1.2
- In de kolom _Tekst_ van _Sectie: Web.mail en Item: smtp.ssl.trust_ kan de mailserver als vertrouwde host worden gemarkeerd door de server hostnaam hierin op te slaan. Er vindt dan geen controle plaats op het server certificaat. Laat deze leeg indien geen problemen worden ervaren met het versturen en ontvangen van mail. Hierdoor wordt altijd op de geldigheid van het servercertificaat gecontroleerd.
