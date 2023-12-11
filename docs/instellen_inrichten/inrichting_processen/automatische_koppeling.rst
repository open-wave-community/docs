Automatische koppeling van processen aan zaaktypes
==================================================

In het detailscherm van een zaaktype in de codetabel *Zaaktypes
Omgeving* (als het een Omgevingszaak betreft, bij andere zaaktypen
uiteraard andere codetabellen) kan enerzijds ingesteld worden welke
`processen </docs/instellen_inrichten/inrichting_processen.md>`__ van
toepassing zijn bij het aanmaken van een zaak en anderzijds of die
processen al automatisch moeten worden toegevoegd.

Wanneer geen processen zijn gekoppeld aan een zaaktype, dan kan de
gebruiker bij dat zaaktype uit alle termijnbewakingsprocessen kiezen
(met dezelfde module). Wanneer er wel regels zijn ingevoerd, dan
betekent dat dat de gebruiker bij dat zaaktype alleen kan kiezen uit die
gekoppelde processen.

In beide gevallen kijkt het programma wel naar het compartiment. Dat wil
zeggen: indien de inlogger geen lid is van een compartiment dan kunnen
alleen processen worden gekozen die ook NIET gekoppeld zijn aan een
compartiment. indien de inlogger wel lid is van een compartiment dan
kunnen alleen processen worden gekozen die hetzelfde compartiment
verbonden zijn.

Het verwijderen van een regel met de verwijderknop heeft tot gevolg dat
de verwijzing naar een proces direct wordt verwijderd. Er is hier dus
geen sprake van een vervaldatum (dezelfde regel kan daarna weer direct
worden toegevoegd).
