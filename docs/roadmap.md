# Roadmap

_Actueel op 2026-09-12. Dit document bevat alleen nog niet afgerond werk._

## Nu: betrouwbaarheid boven uitbreiding

1. **Ontleedlab-hoofdstroom herstellen**
   - alle toepasselijke rollen tegelijk op de standaardroute
   - Rollenladder alleen via `#/rollenladder`, zonder blijvende activatie
   - regressietests voor routescheiding

2. **Feedback opnieuw ijken**
   - korte herstelhandeling als standaard
   - geen onbewezen diagnose van leerlingdenken
   - vorm en betekenis combineren; losse trucjes zijn alleen controlemiddel
   - foutieve of te absolute spellingregels corrigeren

3. **Productclaims eerlijk maken**
   - lokaal browseroverzicht niet als klasdata presenteren
   - onbeoordeelde transfer niet als rubric-feedback presenteren
   - client-side hashes en API-sleutels niet als beveiliging presenteren

4. **Ontwikkelpad deterministisch maken**
   - toevalsafhankelijke tests een vaste randombron geven
   - test plus build in iedere product-CI
   - automatisch gegenereerde document-PR's verwijderen

## Daarna: één leerlus per product valideren

### Ontleedlab

Meet of een foutmelding leidt tot een betere tweede poging op hetzelfde grammaticale contrast. Herzie eerst de vaakste rolverwarringen. Splits `useTrainer.ts` alleen wanneer een concrete wijziging daardoor aantoonbaar kleiner wordt.

### Werkwoordlab

Valideer de zes units als één route van functiebepaling naar spelling en zelfcontrole. Maak unit 4–6 expliciet gefaseerd. Gebruik pas daarna voortgangsdrempels; twee of drie willekeurige goede antwoorden zijn geen robuust beheersingsmodel.

## Beslispoorten, geen toezeggingen

- **Gedeelde runtime:** alleen als dezelfde stabiele logica in beide producten aantoonbaar dubbel wordt onderhouden.
- **Backend/identiteit:** alleen met een expliciet privacy-, beheer- en beveiligingsbesluit.
- **Geïntegreerde app:** alleen als pilots aantonen dat schakelen tussen ontleden en spellen leerwinst of duidelijke gebruikswinst geeft.
- **Nieuwe content:** alleen voor een nieuw contrast, fouttype of transfercontext.

Tot die tijd blijven de twee apps zelfstandig en blijft `grammar-core` klein.
