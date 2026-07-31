# 03 — werkwoordlab skill migration

## Eindtoestand

`<workspace-root>/werkwoordlab` bevat alleen domein- en productskills onder `.agents/skills/`; algemene engineering en UI komen uit de globale baseline.

## Start in een verse context

- Terra `medium` voor inventarisatie, verplaatsen en verwijderen.
- Sol `xhigh` voor skillherschrijving en routingtests.
- Lees: `AGENTS.md`, relevante `shared/grammar-core/docs/`, `docs/product-contract.md`, runtimewaarheid, bestaande skills, dit bestand.
- Paden: resolve `<workspace-root>` als de map met repo-checkouts en `<repo-root>` als de afzonderlijke `werkwoordlab`-checkout; neem geen vaste lokale checkoutlocatie aan.

## Afhankelijkheden

Stap 01 is valide en de `grammar-core`-implementatie-PR uit stap 02 is gemerged. Synchroniseer die merge eerst in een afzonderlijke sync-only branch en PR en merge die PR vóór deze migratiestap.

Laat de eerste sync niet afhangen van een nog niet vindbare plugin-skill. Als `grammar-core-sync` nog niet geïnstalleerd of discoverable is, lees `<workspace-root>/grammar-core/plugins/grammar-core-toolkit/skills/grammar-core-sync/SKILL.md` rechtstreeks uit de gemergede canonieke checkout en gebruik dat bestand als runbook: verifieer schone worktree, remotes en default branches; maak een sync-only branch; voer `git subtree pull --prefix=shared/grammar-core <canonical-remote> <canonical-default-branch> --squash` uit; controleer dat de diff vóór lokale referentie-updates alleen `shared/grammar-core/` raakt; draai productchecks; merge de sync-only PR. Maak daarna vanaf de productbasisbranch mét die sync-merge een nieuwe migratiebranch. Wrapper- en skillmigratie-edits horen nooit in de sync-only PR.

## Terra → Sol-overdracht

Terra voert alleen inventarisatie, verplaatsingen, verwijderingen en mechanische referentiecorrecties uit. Terra levert vóór de modelwissel basis-SHA, `git status --short --branch`, bewijs van de gemergede sync-PR en grammar-core-SHA, voor/na-skillinventaris, oude→nieuwe padmapping, `git diff --name-status`, de volledige mechanische diff en bewaarde gebruikerswijzigingen.

Sol begint pas met wrapperinhoud, triggers, outputcontracten en routingtests nadat deze bundel compleet is en de diff uitsluitend de afgesproken mechanische scope raakt. Bij ontbrekend syncbewijs of een onverklaarde inhoudelijke wijziging stopt Sol en draagt het specifieke bestand of hunk terug over; Sol mengt de sync-, Terra- en Sol-fasen niet stilzwijgend.

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

1. Terra verifieert dat de actuele migratiebranch afstamt van de gemergede sync-only PR en legt repo-status, skillinventaris en globale duplicaten vast.
2. Terra corrigeert `workwoordspellingsdidactiek` naar `werkwoordspellingsdidactiek` in directory, frontmatter en verwijzingen.
3. Terra verwijdert repo-kopieën van Matt-skills, generieke frontend/test/docs/projectskills, PlanetScale-skills en bijbehorende repo-locks.
4. Terra verwijdert verouderde `scaffold-exercises`, `migrate-to-shoehorn`, Claude-git-guardrails en ongebruikte Obsidian/loop-skills en werkt mechanische paden in `AGENTS.md`, `CONTEXT.md`, `docs/agents/` en catalogi bij.
5. Terra levert de bewijsbundel uit de overdrachtssectie en stopt.
6. Sol maakt shared wrappers dun: lees eerst `shared/grammar-core/.agents/skills/...`, pas daarna het lokale productcontract en runtimewaarheid toe.
7. Sol versterkt lokale triggers, outputcontracten en deterministische gates; behoud de niet-onderhandelbare function-first, deterministic-evaluator, data-driven, privacy- en teacher-insightregels.
8. Sol voegt `agents/openai.yaml` toe of actualiseert het, voert de routingtests uit en controleert de volledige inhoudelijke diff na het Terra-werk.

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
- Vanuit `<repo-root>`: `rg -n --hidden --glob '!.git/**' '\.codex/skills|scaffold-exercises|migrate-to-shoehorn|superpowers|planetscale' -- .`.
- Positieve/negatieve routing voor iedere doelskill.
- UI-combinatietest met `frontend-design` + `learner-flow-ui` + `web-design-guidelines`.
- Repo-checks uit `docs/testing-strategy.md`, minimaal contentvalidatie, plus lint/test/e2e waar beschikbaar.
- `git diff --check`

## Voltooiingscriteria

Alleen de doelset is repo-lokaal vindbaar, wrappers verwijzen naar de gemergede canon, geen algemene workflow wordt gedupliceerd en productchecks tonen geen nieuwe regressie.

## Rollback

Revert de product-PR. Herstel verwijderde skills alleen vanuit hun exacte Git-versie wanneer een routingtest een aantoonbare capabilitykloof vindt.

## Overdracht

Noteer grammar-core-SHA, de gemergede sync-PR en sync-merge-SHA, de afzonderlijke productmigratiebranch, subtree-syncbewijs, skillinventaris, routingtests, checks en bewaarde gebruikerswijzigingen voor stap 06.
