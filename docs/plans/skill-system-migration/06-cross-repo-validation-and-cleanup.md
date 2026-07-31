# 06 — Cross-repo validation and cleanup

## Eindtoestand

De globale baseline en alle vier repos vormen één coherent skillsysteem zonder verborgen duplicaten, gebroken wrappers of foutieve UI-routing.

## Start in een verse context

- Terra `medium` voor mechanische inventarisatie en opgeschoonde verwijzingen.
- Sol `xhigh` voor afwijkende skillcorrecties en routingbeoordeling.
- Lees dit dossier, de vier PR-diffs, globale voor/na-inventaris en per-repo `AGENTS.md`.
- Paden: resolve `<workspace-root>` en voor iedere controle het actuele `<repo-root>`; neem geen vaste gebruikers- of checkoutlocatie aan.

## Afhankelijkheden

Stappen 01–05 zijn uitgevoerd. De `grammar-core`-implementatie-PR is eerst gemerged; daarna zijn de afzonderlijke sync-only PR’s in `werkwoordlab` en `ontledingstrainer` gemerged; pas daarna zijn de productmigratiebranches gemaakt en hun implementatie-PR’s gereedgemaakt. Gebruik per repo een schone worktree en de exacte implementatiebranch en leg de drie SHA-grenzen afzonderlijk vast.

## Terra → Sol-overdracht

Terra voert alleen inventarisatie, mechanische referentiecleanup en deterministische validators uit. Terra levert vóór de modelwissel per repo basis-SHA, `git status --short --branch`, grammar-core-merge-SHA, eventuele product-sync-merge-SHA, productmigratiebranch/SHA, finale skillinventaris, mechanische diff, validatoroutput en bewaarde gebruikerswijzigingen.

Sol begint pas met routingbeoordeling of een inhoudelijke skillcorrectie wanneer deze bewijsbundel compleet is. Sol controleert eerst dat grammar-core-implementatie, productsync en productmigratie afzonderlijke grenzen hebben en dat Terra geen skillbetekenis heeft gewijzigd. Sol documenteert afwijking, bronbewijs en correctiediff per skill; bij een onduidelijke mechanische wijziging gaat het specifieke bestand of hunk terug naar Terra in plaats van de fasen te vermengen.

## Procedure

1. Terra legt voor global, `grammar-core`, `werkwoordlab`, `ontledingstrainer` en `dealership` de finale skillinventaris en de vereiste SHA-grenzen vast.
2. Terra controleert directorynaam, frontmatternaam, beschrijving, `agents/openai.yaml`, default prompt en discovery.
3. Terra zoekt vanaf iedere expliciete `<repo-root>` naar oude `.codex/skills`, verwijderde skillnamen, Superpowers en PlanetScale. Accepteer alleen expliciet gemarkeerde historische bronverwijzingen.
4. Terra draait per repo alle in de implementatiestap genoemde productchecks en `git diff --check`, levert de bewijsbundel en stopt.
5. Sol test per skill minimaal één positieve en één negatieve routingprompt in een verse context.
6. Sol test combinaties:
   - één Matt-processkill + één domeinskill;
   - `frontend-design` + lokale learner-flow-skill;
   - `web-design-guidelines` als afsluitende audit;
   - Dealership UI zonder lokale `ui-designer`.
7. Sol controleert dat design- en auditskills geen eigen TDD-, Git- of projectmanagementproces starten en beoordeelt de volledige inhoudelijke diff na het Terra-werk.
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
Set-Location '<repo-root>'
npx skills list --json
rg -n --hidden --glob '!.git/**' '\.codex/skills|superpowers|planetscale' -- .
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
