# Inrichting Processen

## Pagina's Inrichten Processen

- [Afvinkstappen](afvinkstappen.md)
- [Automatische koppeling van processen aan zaaktypes](automatische_koppeling.md)
- [Detailscherm proces](detailscherm_proces.md)
- [Grafische weergave](grafische_weergave.md)
- [Procesflow en bewaking](procesflow_en_bewaking.md)
- [Termijnstappen](termijnstappen.md)

## Module, compartiment, zaaktype

Onder de tegel _Processen_ (kolom _Werkbeheer_) van portaal _beheer-Nieuw_ worden behandelingsprocessen gedefinieerd in een aantal chronologische stappen. Een proces wordt toegekend aan één **module** (dus aan de module omgevingszaken of handhavingszaken of APV/Overig e.d.). Dat betekent dat het proces alleen in zaken van die module gebruikt kan worden.
Een proces kan ook aan een **compartiment** worden toegevoegd. Dat betekent dat alleen bij zaken die spelen in dat compartiment het proces gebruikt kan worden. Bijgevolg moet dus elk compartiment eigen processen definiëren. Wanneer een proces niet aan een compartiment wordt toegekend, is het proces alleen te gebruiken bij zaken die door de host worden afgehandeld.

Een proces kan automatisch worden gekoppeld aan een **zaaktype** zodat bij het opvoeren van een nieuwe zaak onder dat zaaktype (met de hand of vanuit OLO/DSO) de bijbehorende processtappen al worden klaargezet bij de nieuwe zaak. Dit gebeurt door de hier gedefinieerde processtappen op dat moment te kopiëren naar een tweede processtappen-tabel (tbtermijnbewstappen) die gekoppeld is aan een specifieke zaak. Zo ontstaan er procestaken bij een zaak, voor een persoon of voor een team, die binnen een bepaalde termijn afgehandeld moeten worden (tegel _Mijn openstaande processtappen_ op het openingsportaal).

![](/img/applicatiebeheer/instellen_inrichten/procesdefinitie.w.800_tok.483342.png){ class="media" loading="lazy" alt="" width="800" }

Bovenstaand diagram is getekend voor processtappen bij omgevingszaken, maar is soortgelijk voor overige modules als handhaving of infoaanvragen. Wanneer de procesdefinitie wordt aangepast, worden deze aanpassingen NIET met terugwerkende kracht geeffectueerd. De aanpassingen gelden alleen voor nieuwe zaken die na het moment van aanpassing worden gemaakt.

## Termijnbewakingsstappen, afvinkstappen en processtappen

In deze Dokuwiki wordt ook gesproken over termijnbewakingsstappen en afvinkstappen. Afvinkstappen zijn processtappen waarin om een keuze gevraagd wordt. Die keuze bepaalt de voortgang van de procesflow in een bepaalde tak. In onderstaand schema is de ruit met de tekst _aanvulling nodig_ een afvinkstap.

![](/img/applicatiebeheer/instellen_inrichten/voorbeeldgrafischprocesstap.w.400_tok.caf5e9.png){ class="media" loading="lazy" alt="" width="400" }

Wanneer de eindgebruiker de vraag met Ja beantwoordt (= afvinken) is de eerstvolgende vervolgstap: _verzoek om aanvulling_, en anders _besluit ontvankelijkheid_.

Een termijnstap is een processtap die gekarakteriseerd wordt door een streefdatum en die de eindgebruiker kan afhandelen met een afhandeldatum. Streefdatums bij de processtapdefinitie worden altijd gedefinieerd in aantal dagen na de vorige stap. De streefdatum en afhandeldatum van de eerste processtap bij een specifieke zaak worden automatisch gevuld door OpenWave op basis van de startdatum van die zaak. De overige streefdatums aan de voorkant worden dus berekend op basis van deze eerste datum en de termijnen naar de volgende stappen.

### Processtappen en vervolgacties

Een processtap hoeft niet alleen gedefinieerd te worden door een naam en een termijn, waarbij de eindgebruiker de stap met het vullen van een afhandeldatum afsluit.
Er zijn ook stappen te definiëren waarbij de eindgebruiker de stap afhandelt door:

- een bepaald document te genereren
- een vervolgproces te kiezen
- een vervolgzaak aan te maken
- een bepaalde waarde in te voeren of te kiezen uit een lijst
- een bovenliggende zaak af te sluiten.

Voorbeelden hiervan staan onder de kopjes _Action en Invoerkolommen_ bij [Termijnstappen](termijnstappen.md).
