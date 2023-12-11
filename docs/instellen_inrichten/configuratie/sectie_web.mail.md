# Sectie Web.mail

Hieronder de instellingen uit de [configuratietabel](/docs/instellen_inrichten/configuratie.md) (tbinitialisatie) van de *Sectie: Web.mail* gerangschikt op item. Instellingen die nodig zijn om vanuit OpenWave een SMTP-server (uitgaande email) aan te kunnen spreken. Zie [E-mail SMTP instellingen](/docs/instellen_inrichten/email.md).

## Items Configuratietabel

| Item | Kolom | Omschrijving |
|---|---|---|
| Debug | Aanvinkvakje |Indien aangevinkt loopt een debugger mee. Normaal dus uitgevinkt. |
|mime.address.strict| Aanvinkvakje |Aanzetten is aan te raden. The mail.mime.address.strict session property controls the parsing of address headers. By default, strict parsing of address headers is done. If this property is set to "false", strict parsing is not done and many illegal addresses that sometimes occur in real messages are allowed. |
|smtp.authentication| Aanvinkvakje |Aanzetten is aan te raden. De te verzenden mail wordt geauthentiseerd op het password (kolom *Info* van *transport.protocol*). |
|smtp.ssl.protocols| Tekst |In de kolom *Tekst* kan de TLS-versie worden opgegeven opgegeven. Aangeraden wordt TLSv1.2. Meerdere opties kunnen worden opgegeven gescheiden door een spatie bijvoorbeeld: TLSv1.1 TLSv1.2  Indien leeg gelaten dan wordt het aan de server overgelaten. Mogelijke opties zijn

* TLSv1

* TLSv1.1

* TLSv1.2. |
|smtp.ssl.trust| Tekst |In de kolom *Tekst* kan de mailserver als vertrouwde host worden gemarkeerd door de server hostnaam hierin op te slaan. Er vindt dan geen controle plaats op het server certificaat. Laat deze leeg indien geen problemen worden ervaren met het versturen en ontvangen van mail. Hierdoor wordt altijd op de geldigheid van het servercertificaat gecontroleerd. |
|smtp.starttls.enable| Aanvinkvakje |Default = uit. Indien aangevinkt dan wordt STARTTLS encryptie aangezet bij het versturen van mail. Let op: de poort moet dan worden ingesteld op 587. Zie *Getal1* van instelling *Sectie: Web.mail en Item: transport.protocol*. |
|transport.protocol| Aanvinkvakje |Moet aan staan, anders werkt de email niet. |
| | Getal1 |De mail.smtp.port van de mailserver (meestal 25). |
| | Tekst | Moet de waarde *smtp* hebben. |
| | Info | Indien *smtp.authentication* aangevinkt is dan bestaat de kolom uit de volgende onderdelen gescheiden door een dubbele punt (bijvoorbeeld: *mail.openu.nl:LOGIN:REALM:sesam:12C34)*:

* the host name of the mail

* the authentication method

* the authentication realm (for digest md5)

* the authentication username

* the encrypted (rem-encryptie) authentication password

indien *smtp.authentication* uit staat, dan bestaat de kolom *Info* alleen uit the host name of the mail. |
