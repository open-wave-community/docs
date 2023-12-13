# ADR-Indeling

## Trigger

De tegel is een trigger voor de tabel met indeling *Gevaarlijke stoffen volgens ADR* (Accord europeen relatif au transport international des marchandises Dangereuses par Route).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Beheer*
- Kolom: *Inrichtingen II*
- Kopregel: *ADR-indeling*
- Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbmiladropslag)*
