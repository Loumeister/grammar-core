# Roadmap

_Actueel op 2026-09-12. Alleen productoverstijgende besluiten staan hier. Uitvoering staat in de lokale productbacklogs._

## Nu

1. **Feedback valideren**
   - meet per product of een herstelvraag de tweede poging op hetzelfde contrast verbetert
   - leg alleen een gedeelde regel vast als hetzelfde probleem in beide producten voorkomt

2. **Canon beheersbaar houden**
   - wijzig gedeelde afspraken eerst in `grammar-core`
   - synchroniseer daarna handmatig via een afzonderlijke PR per product
   - laat CI alleen afwijkingen melden en nooit branches of PR's schrijven

3. **Gegevensgrens besluiten**
   - beschrijf doel, minimale dataset, bewaartermijn, toegang en verwijdering vóór er een backend komt
   - houd een eventuele koppeling tussen leerlingcode en leerlingidentiteit buiten de leerlingapp

## Beslispoorten, geen toezeggingen

- **Gedeelde runtime:** alleen als dezelfde stabiele logica in beide producten aantoonbaar dubbel wordt onderhouden.
- **Backend/identiteit:** alleen met een expliciet privacy-, beheer- en beveiligingsbesluit.
- **Geïntegreerde app:** alleen als pilots aantonen dat schakelen tussen ontleden en spellen leerwinst of duidelijke gebruikswinst geeft.
- **Nieuwe content:** alleen voor een nieuw contrast, fouttype of transfercontext.

Tot die tijd blijven de twee apps zelfstandig en blijft `grammar-core` klein.
