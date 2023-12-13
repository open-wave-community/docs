# Container Export Rapportages

## Trigger

De tegel is een trigger voor een lijst van _Containers met rapportages_ (tbexportcontainer) die via de operations (beheertegel _Operations_) al of niet gescheduled gestart kunnen worden en waarvan de resultaatsets als zip worden ingepakt en geëxporteerd zie: [Export Report Container](../../../../instellen_inrichten/export_report_container.md).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: [Beheerportaal](../../README.md)
- Kolom: [Tegels onder kolom Instellingen II](tegels_onder_kolom_instellingen_ii/README.md)
- Kopregel: _Container;Exportrapportages_
- Actie: _getFlexList(SysStandardList,,{id},,beheer_containerexportrapportages)_
