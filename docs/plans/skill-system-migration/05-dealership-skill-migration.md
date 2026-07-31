# 05 — dealership skill migration

## Eindtoestand

`<workspace-root>/dealership` bevat alleen drie dealership-domeinskills onder `.agents/skills/` en gebruikt globale UI-skills.

## Start in een verse context

- Terra `medium` voor inventarisatie, verwijdering en mechanische padupdates.
- Sol `xhigh` voor het ontwerpen en herschrijven van de drie doelskills.
- Lees repo-instructies, financiële en ingestieruntimecontracten, bestaande skills, tests en dit bestand.
- Paden: resolve `<workspace-root>` als de map met repo-checkouts en `<repo-root>` als de afzonderlijke `dealership`-checkout; neem geen vaste lokale checkoutlocatie aan.

## Afhankelijkheden

Stap 01 is valide. Deze stap heeft geen grammar-core-subtreeafhankelijkheid.

## Doelset

- `dealership-financial-integrity`
- `dealership-ingestion-workflow`
- `dealership-release-gate`

## Terra → Sol-overdracht

Terra voert alleen inventarisatie, verwijderingen en mechanische referentiecorrecties uit. Terra levert vóór de modelwissel basis-SHA, `git status --short --branch`, de uit runtime en tests afgeleide invariantinventaris zonder nieuwe ontwerpclaims, voor/na-skillinventaris, verwijder- en padmapping, `git diff --name-status`, de volledige mechanische diff en bewaarde gebruikerswijzigingen.

Sol begint pas met het ontwerpen en herschrijven van de drie doelskills nadat deze bundel compleet is en de diff uitsluitend de afgesproken mechanische scope raakt. Sol koppelt iedere semantische skillregel aan aantoonbare code, schema’s, tests of documentatie en is eigenaar van routingtests en inhoudelijke eindreview. Bij een onverklaarde inhoudelijke Terra-wijziging stopt Sol en draagt het specifieke bestand of hunk terug over.

## Procedure

1. Terra inventariseert de werkelijke financiële, ingestie- en release-invarianten uit code, schema’s, tests en documentatie zonder nieuwe productregels te formuleren.
2. Terra verwijdert `project-manager`, `senior-engineer`, `technical-writer`, `test-engineer`, `ui-designer` en de te brede `dealership-cms`.
3. Terra verwijdert Matt-duplicerende PRD-, tasklist- en implementatietemplates en werkt mechanische paden in repo-instructies, context, `docs/agents/` en catalogi bij.
4. Terra levert de bewijsbundel uit de overdrachtssectie en stopt.
5. Sol ontwerpt de drie doelskills rond de aantoonbare invarianten, met precieze triggers, grenzen, procedure, outputcontract en deterministische gates, en voegt per doelskill `agents/openai.yaml` toe.
6. Sol maakt geen lokale UI-skill tenzij runtimebewijs een unieke, niet-financiële UI-invariant toont; documenteer zo’n uitzondering eerst. Sol voert de routingtests uit en controleert de volledige inhoudelijke diff na het Terra-werk.

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
- Vanuit `<repo-root>`: `rg -n --hidden --glob '!.git/**' 'project-manager|senior-engineer|technical-writer|test-engineer|ui-designer|dealership-cms|\.codex/skills|superpowers|planetscale' -- .`.
- `git diff --check`

## Voltooiingscriteria

De drie doelskills dekken alle aangetoonde lokale invarianten, algemene procesduplicatie is weg, UI-capability blijft globaal beschikbaar en productchecks vertonen geen nieuwe regressie.

## Rollback

Revert de PR. Herstel geen brede rolskill; herstel alleen een aantoonbaar gemiste domeininvariant in de juiste doelskill.

## Overdracht

Lever skillinventaris, invariantmapping, routingtests en validatiebewijs aan stap 06.
