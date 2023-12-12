# Vee / Stallen

![](applicatiebeheer/instellen_inrichten/stallenenvee.png.png){ class="media" loading="lazy" alt="" width="900" }

De bruingekleurde blokken slaan op tabellen die via het beheerportaal *Inrichtingenbeheer* kunnen worden benaderd.

De blauwe blokken zijn benaderbaar via het inrichtingsportaal en aldaar de tegel *Stallen/Vee*.

Voordat een stal met één of meer diergroepen gedefinieerd kan worden bij een inrichting zullen de codetabellen in het beheerportaal met de juiste waarden gevuld moeten zijn.

## BWL-coderingen

Tabel tbmilcodebwl.

In het beheerportaal *Inrichtingenbeheer* onder de tegel *BWL-coderingen* (kolom *Registratie Vee*) kunnen deze codes worden ingevoerd met een naam en omschrijving.
Er zijn geen reductiewaardes met betrekking tot de uitstoot van staldelen waar deze codering wordt gebruikt (zie berekening uitstoot per staldeel/diergroep).
De tabel wordt ook gebruik om een default-BWL-code per stal/diersysteem te definiëren.

## Diergroepen

Tabel tbmilcodedier.

In het beheerportaal *Inrichtingenbeheer* onder de tegel *Codering Dieren* (kolom *Registratie Vee*) kunnen de diergroepen met hun betekenisvolle coderingen worden ingebracht (code A1 =  melk- en kalfkoeien ouder dan 2 jaar).

De tabel wordt gebruikt bij de definitie van de stalsysteem/dier combinaties.

### Stalsystemen

Tabel tbmilcodestal.

In het beheerportaal *Inrichtingenbeheer* onder de tegel *Codering Stallen* (kolom *Registratie Vee*) kunnen de stalsystemen met hun betekenisvolle coderingen worden ingebracht (code A1.5.1 = loopstal met sleufvloer en mestschuif (BWL 2010.24.V2) beweiden).

De tabel wordt gebruikt bij de definitie van de stalsysteem/dier combinaties.

### Combinaties Stalsysteem/dier en uitstoot

Tabel tbmilcodestaldier.

In het beheerportaal *Inrichtingenbeheer* onder de tegel *Combinatie stal/dier* (kolom *Registratie Vee*) worden de stalsystemen en diergroepen samengebracht waaraan uitstootgegevens kunnen worden toegekend:

- NH3 in Kg per jaar/dier
- Fijnstof in gram/jaar/dier
- Odeurunits per seconde/dier
- Aantal dieren dat voor de combinatie 1 MVE oplevert.

Tevens kan voor de combinatie een default BWL-codering worden gekozen uit de tabel tbmilravbwl (die bij de aanmaak van een nieuw staldeel met de bewuste stalsysteem/dier combinatie dus automatisch wordt toegevoegd).

### Stalsyteem-dier-BWL-combinaties

Tabel tbmilravbwl.

In het beheerportaal *Inrichtingenbeheer* onder de tegel *RAV-BWL-combinaties* (kolom *Registratie Vee*) kunnen BWL-coderingen gekoppeld worden aan Combinaties stalsysteem/dier. De koppeling BWL en Stalsysteem/dier in deze tabel moet uniek zijn (het programma laat alleen kiezen uit geldige opties).
Bij de definitie van de stallen bij een inrichting kan een BWL-codering aan een staldeel gekoppeld worden die afkomstig is uit deze tabel en die hoort bij het gekozen Stalsysteem/dier.

### PAS programma aanpak stikstof

Tabel tbmilcodepas.

In het beheerportaal *Inrichtingenbeheer* onder de tegel *PAS-coderingen* (kolom *Registratie Vee*) kunnen de gebruikte coderingen en omschrijvingen met betrekking tot het programma aanpak stikstof worden gedefinieerd. De op te geven reductiepercentages totaal, vloer, kelder worden NIET gebruikt in de berekening van de uitstoot van staldelen waaraan deze PAS-coderingen worden gekoppeld (zie berekening uitstoot per staldeel/diergroep). Per staldeel kunnen twee PAS-coderingen worden toegevoegd.

### Nageschakelde technieken

Tabel tbmilnagetech.

In het beheerportaal *Inrichtingenbeheer* onder de tegel *Nageschakelde technieken bij stal* (kolom *Registratie Vee*) kunnen coderingen en omschrijvingen met betrekking tot nageschakelde techniek worden gedefinieerd met hun invloed op de berekening van:

- NH3 in Kg per jaar/dier
- Fijnstof in gram/jaar/dier
- Odeurunits per seconde/dier.

Er kunnen per staldeel twee nageschakelde technieken worden opgenomen, waarbij de reductiewaarden automatisch worden verrekend.

Een nageschakelde techniek kan ook worden gekoppeld aan een BWL-codering (tabel tbmilcodebwl) maar dit heeft geen invloed op de automatische berekening.

### Staldelen/diergroepen per stal per inrichting

Tabel tbmilemstal.

Deze tabel is via het inrichtingsportaal via de tegel *Stallen/Vee* te bereiken in het detailscherm van een stal in het blok *diergroepen* c.q. *staldelen*.

Bij het aanmaken van een staldeel/diergroep moet de gebruiker kiezen uit *Combinaties Stalsysteem/dier* (tbmilcodestaldier). Aldaar kan een default BWL-codering zijn opgenomen, die dan overgenomen wordt in de eerste BWL-codering van de diergroep/staldeel.
De dropdownlijstjes bij de BWL-coderingen komen uit de tabel *Stalsyteem-dier-BWL-combinaties* (tbmilravbwl) en zijn dus afhankelijk van het stalsysteem.

### De berekeningen

De gekozen combinatie stalsysteem/dier en de beide nageschakelde technieken bepalen op grond van het ingevoerde aantal dieren automatisch de uitstoot in fijnstof, odeurunits en ammoniak. Daarnaast kan de gebruiker zelf een extra reductiepercentage (per staldeel c.q. diergroep) opvoeren voor odeur, ammoniak en fijnstof bijvoorbeeld op grond van de BWL en/of PAS-coderingen.

- **Ammoniak**  = aantaldieren *dfnh3factor van stalsysteem* (1 - (opgegeven_nh3_reductieperc/100)) + (aantaldieren *eerste-nagesch.technkNH3invloed) 	 + (aantaldieren* tweede-nagesch.techn.NH3invloed)
- **MVE** = aantaldieren / MVE getal uit stalsysteem
- **Odeur** = aantaldieren *Odeurfactor van stalsysteem* (1 - (opgegeven_odeur_reductieperc/100)) + (aantaldieren *eerste-nagesch.technkOdeurinvloed) 	 + (aantaldieren* tweede-nagesch.techn.Odeurinvloed)
- **Fijnstof** = aantaldieren *Fijnstoffactor van stalsysteem* (1 - (opgegeven fijnstof_reductieperc/100)) + (aantaldieren *eerste-nagesch.technkFijnstofinvloed) + (aantaldieren* tweede-nagesch.techn.Fijnstofinvloed).

