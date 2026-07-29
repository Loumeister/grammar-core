# 05 — dealership skill migration

## Eindtoestand

`C:\Users\cpfva\Code\dealership` bevat alleen drie dealership-domeinskills onder `.agents/skills/` en gebruikt globale UI-skills.

## Start in een verse context

- Terra `medium` voor inventarisatie, verwijdering en mechanische padupdates.
- Sol `xhigh` voor het ontwerpen en herschrijven van de drie doelskills.
- Lees repo-instructies, financiële en ingestieruntimecontracten, bestaande skills, tests en dit bestand.

## Afhankelijkheden

Stap 01 is valide. Deze stap heeft geen grammar-core-subtreeafhankelijkheid.

## Doelset

- `dealership-financial-integrity`
- `dealership-ingestion-workflow`
- `dealership-release-gate`

## Procedure

1. Inventariseer de werkelijke financiële, ingestie- en release-invarianten uit code, schema’s, tests en documentatie.
2. Ontwerp de drie doelskills rond die aantoonbare invarianten, met precieze triggers, grenzen, procedure, outputcontract en deterministische gates.
3. Verwijder `project-manager`, `senior-engineer`, `technical-writer`, `test-engineer`, `ui-designer` en de te brede `dealership-cms`.
4. Verwijder Matt-duplicerende PRD-, tasklist- en implementatietemplates.
5. Voeg per doelskill `agents/openai.yaml` toe en werk repo-instructies, context, agentsdocs, catalogi en paden bij.
6. Maak geen lokale UI-skill tenzij runtimebewijs een unieke, niet-financiële UI-invariant toont; documenteer zo’n uitzondering eerst.

## UI-routing

- Ontwerp/bouw: globale `frontend-design`.
- Audit: globale `web-design-guidelines`.
- Financiële vergelijkings- of invoerintegriteit blijft in `dealership-financial-integrity`, niet in een generieke UI-skill.

## Niet wijzigen

- Individuele deals, productiegegevens of functionele productlogica.
- Financiële berekeningen behalve wanneer nodig om een bestaande invariant correct te documenteren; rapporteer discrepanties zonder stilzwijgende fix.
- Externe systemen of productie-ingestie.

## Validatie

- `npx skills list --json`
- Frontmatter/openai.yaml-validatie en positieve/negatieve routing.
- Een Dealership-UI-taak routeert naar globale designsystemen en nooit naar verwijderde `ui-designer`.
- Financiële, ingestie- en releasechecks uit de repo.
- `rg` op verwijderde skills, `.codex/skills`, Superpowers en PlanetScale.
- `git diff --check`

## Voltooiingscriteria

De drie doelskills dekken alle aangetoonde lokale invarianten, algemene procesduplicatie is weg, UI-capability blijft globaal beschikbaar en productchecks vertonen geen nieuwe regressie.

## Rollback

Revert de PR. Herstel geen brede rolskill; herstel alleen een aantoonbaar gemiste domeininvariant in de juiste doelskill.

## Overdracht

Lever skillinventaris, invariantmapping, routingtests en validatiebewijs aan stap 06.
