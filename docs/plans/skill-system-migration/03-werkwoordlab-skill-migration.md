# 03 — werkwoordlab skill migration

## Eindtoestand

`C:\Users\cpfva\Code\werkwoordlab` bevat alleen domein- en productskills onder `.agents/skills/`; algemene engineering en UI komen uit de globale baseline.

## Start in een verse context

- Terra `medium` voor inventarisatie, verplaatsen en verwijderen.
- Sol `xhigh` voor skillherschrijving en routingtests.
- Lees: `AGENTS.md`, relevante `shared/grammar-core/docs/`, `docs/product-contract.md`, runtimewaarheid, bestaande skills, dit bestand.

## Afhankelijkheden

Stap 01 is valide en stap 02 is gemerged. Synchroniseer eerst de gemergede `grammar-core` via `grammar-core-sync`.

## Doelset

- `content-seed-generator`
- `didactic-workwoordspelling`
- `evals-and-release`
- `evidence-based-werkwoordspellingsdidactiek`
- `exercise-quality-gate`
- `learner-flow-ui`
- `teacher-insights`
- `documentation-sync-guardian`
- `shared-content-integration`
- `grammar-core-sync`

## Procedure

1. Leg repo-status, skillinventaris en globale duplicaten vast.
2. Corrigeer `workwoordspellingsdidactiek` naar `werkwoordspellingsdidactiek` in directory, frontmatter en verwijzingen.
3. Maak shared wrappers dun: lees eerst `shared/grammar-core/.agents/skills/...`, pas daarna het lokale productcontract en runtimewaarheid toe.
4. Versterk lokale triggers, outputcontracten en deterministische gates; behoud de niet-onderhandelbare function-first, deterministic-evaluator, data-driven, privacy- en teacher-insightregels.
5. Voeg of actualiseer `agents/openai.yaml`.
6. Verwijder repo-kopieën van Matt-skills, generieke frontend/test/docs/projectskills, PlanetScale-skills en bijbehorende repo-locks.
7. Verwijder verouderde `scaffold-exercises`, `migrate-to-shoehorn`, Claude-git-guardrails en ongebruikte Obsidian/loop-skills.
8. Werk `AGENTS.md`, `CONTEXT.md`, `docs/agents/`, catalogi en actuele paden bij.

## UI-routing

- Bouw en visuele richting: globale `frontend-design`.
- Didactische interactieregels: lokale `learner-flow-ui`.
- Eindcontrole: globale `web-design-guidelines`.

## Niet wijzigen

- `.claude/settings*` met bestaande gebruikerswijzigingen.
- Productlogica buiten noodzakelijke wrapper- of referentiecorrecties.
- Hardcoded oefenitems in UI-code toevoegen.

## Validatie

- `npx skills list --json`
- Frontmatter/openai.yaml-validatie voor iedere doelskill.
- `rg` op oude `.codex/skills`, verwijderde namen, Superpowers en PlanetScale.
- Positieve/negatieve routing voor iedere doelskill.
- UI-combinatietest met `frontend-design` + `learner-flow-ui` + `web-design-guidelines`.
- Repo-checks uit `docs/testing-strategy.md`, minimaal contentvalidatie, plus lint/test/e2e waar beschikbaar.
- `git diff --check`

## Voltooiingscriteria

Alleen de doelset is repo-lokaal vindbaar, wrappers verwijzen naar de gemergede canon, geen algemene workflow wordt gedupliceerd en productchecks tonen geen nieuwe regressie.

## Rollback

Revert de product-PR. Herstel verwijderde skills alleen vanuit hun exacte Git-versie wanneer een routingtest een aantoonbare capabilitykloof vindt.

## Overdracht

Noteer grammar-core-SHA, subtree-syncbewijs, skillinventaris, routingtests, checks en bewaarde gebruikerswijzigingen voor stap 06.
