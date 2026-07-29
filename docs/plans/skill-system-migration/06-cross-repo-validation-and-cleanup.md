# 06 — Cross-repo validation and cleanup

## Eindtoestand

De globale baseline en alle vier repos vormen één coherent skillsysteem zonder verborgen duplicaten, gebroken wrappers of foutieve UI-routing.

## Start in een verse context

- Terra `medium` voor mechanische inventarisatie en opgeschoonde verwijzingen.
- Sol `xhigh` voor afwijkende skillcorrecties en routingbeoordeling.
- Lees dit dossier, de vier PR-diffs, globale voor/na-inventaris en per-repo `AGENTS.md`.

## Afhankelijkheden

Stappen 01–05 zijn uitgevoerd; grammar-core is vóór de productrepo-syncs gemerged. Gebruik per repo een schone worktree en de exacte implementatiebranch.

## Procedure

1. Leg voor global, `grammar-core`, `werkwoordlab`, `ontledingstrainer` en `dealership` de finale skillinventaris vast.
2. Controleer directorynaam, frontmatternaam, beschrijving, `agents/openai.yaml`, default prompt en discovery.
3. Zoek repo-breed naar oude `.codex/skills`, verwijderde skillnamen, Superpowers en PlanetScale. Accepteer alleen expliciet gemarkeerde historische bronverwijzingen.
4. Test per skill minimaal één positieve en één negatieve routingprompt in een verse context.
5. Test combinaties:
   - één Matt-processkill + één domeinskill;
   - `frontend-design` + lokale learner-flow-skill;
   - `web-design-guidelines` als afsluitende audit;
   - Dealership UI zonder lokale `ui-designer`.
6. Controleer dat design- en auditskills geen eigen TDD-, Git- of projectmanagementproces starten.
7. Draai per repo alle in de implementatiestap genoemde productchecks en `git diff --check`.
8. Maak alleen gerichte correctie-PR’s; combineer geen ongerelateerde cleanup.

## Niet wijzigen

- Productfunctionaliteit, content of externe data buiten een aantoonbare migratieregressie.
- Gemergede geschiedenis via reset of force-push.
- Historische documentpaden die expliciet als historische bronreferentie zijn gemarkeerd.

## Deliverables

- Finale inventarismatrix met bron, scope en eigenaar per skill.
- Routingtestmatrix met prompt, verwachte skill(s), werkelijke skill(s) en resultaat.
- Validatiematrix per repo.
- Lijst van resterende risico’s of gerichte correctie-PR’s.

## Validatiecommando’s

Per repo:

```powershell
npx skills list --json
rg -n --hidden --glob '!.git/**' '\.codex/skills|superpowers|planetscale'
git diff --check
git status --short --branch
```

Voeg de repo-eigen build-, lint-, unit-, integratie-, content- en e2e-commando’s toe. Draai `claude plugin validate .` wanneer de grammar-core-pluginstructuur is gewijzigd.

## Voltooiingscriteria

Alle verwachte skills routeren correct, alle negatieve prompts blijven buiten scope, wrappers bereiken de gemergede canon, geen algemene methodologie is dubbel actief en alle relevante checks slagen of hebben gedocumenteerde pre-existente fouten.

## Rollback

Revert alleen de PR die de aangetoonde regressie introduceerde. Houd de globale voorinventaris beschikbaar voor gerichte herinstallatie; herstel geen volledige oude baseline.

## Overdracht

Publiceer een korte eindrapportage met links naar de vier implementatie-PR’s, grammar-core merge-SHA, finale matrices en open risico’s. Daarmee is de migratie afgerond.
