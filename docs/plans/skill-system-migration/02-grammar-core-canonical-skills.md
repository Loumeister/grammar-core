# 02 — grammar-core canonical skills

## Eindtoestand

`C:\Users\cpfva\Code\grammar-core` publiceert zes canonieke domeinskills onder `.agents/skills/`, een veilige `grammar-core-sync`-skill en actuele repo-instructies, workflowpaden en catalogi.

## Start in een verse context

- Terra `medium`: inventarisatie, `git mv`, directoryopruiming en mechanische padwijzigingen.
- Sol `xhigh`: iedere wijziging aan `SKILL.md`, triggers, procedures, outputcontracten en `agents/openai.yaml`.
- Lees: `AGENTS.md` of `CLAUDE.md`, relevante `docs/`, bestaande skills/agents, daarna dit bestand.

## Afhankelijkheden

Stap 01 is gevalideerd. Bewaar bestaande `.claude/settings*` en andere gebruikerswijzigingen.

## Exacte scope

Canonieke set:

- `documentation-sync-guardian`
- `evidence-based-werkwoordspellingsdidactiek`
- `parsing-content-governance`
- `shared-content-authoring`
- `shared-content-integration`
- `taxonomy-evaluator-guardian`

Distributieskill:

- `plugins/grammar-core-toolkit/skills/grammar-core-sync`

Referenties:

- `AGENTS.md`, `CLAUDE.md`, `README.md`
- `docs/agent-catalog.md`, `docs/repo-sync-strategy.md`, relevante programma- en integratiedocs
- `.github/workflows/documentation-sync-on-main.yml`

## Procedure

1. Verplaats bestaande `.codex/skills/*` met `git mv` naar `.agents/skills/`.
2. Voeg de twee ontbrekende skills toe en geef alle zes alleen `name` en `description` in YAML-frontmatter.
3. Geef iedere skill precieze positieve triggers, negatieve grenzen, leesroute, procedure, guardrails, outputcontract en escalatiepad.
4. Voeg per skill `agents/openai.yaml` toe met gequote `display_name`, `short_description` van 25–64 tekens en een `default_prompt` met `$skill-name`.
5. Herschrijf `grammar-core-sync` met clean-worktreecontrole, remote- en default-branchdetectie, veilige subtree-pull, conflictinspectie per bestand, scopecheck, productvalidatie en draft-PR-overdracht. Verbied blanket `checkout --theirs`.
6. Maak een compacte `AGENTS.md` met leesvolgorde, runtimewaarheid, shared/local-grens, Matt-procesrol en exacte skillrouting.
7. Werk alle actuele `.codex/skills`-paden atomair bij. Markeer historische bronpaden expliciet in plaats van geschiedenis te vervalsen.
8. Werk de docs-syncworkflow bij naar `.agents/skills/documentation-sync-guardian/SKILL.md`.

## Niet wijzigen

- Product-runtimegedrag.
- Productspecifieke labels, evaluators, UI of datamodellen.
- Onverwante Claude-agents.
- Bestaande gebruikersinstellingen.

## Deliverables

- Zes valide canonieke skills plus OpenAI-metadata.
- Veilige sync-skill plus metadata.
- `AGENTS.md` en actuele catalogus/distributiedocumentatie.
- Voor/na-inventaris en validatiebewijs.

## Validatie

```powershell
Get-ChildItem .agents\skills -Directory
npx skills list --json
rg -n --hidden --glob '!.git/**' '\.codex/skills|checkout --theirs|superpowers|planetscale' .
git diff --check
```

Voer daarnaast `quick_validate.py` uit voor iedere skill, parse alle `agents/openai.yaml`, valideer de Claude-plugin wanneer `.claude-plugin` of pluginstructuur wijzigt en controleer dat directorynaam en frontmatternaam gelijk zijn.

## Voltooiingscriteria

Discovery vindt exact de zes repo-skills; de workflow gebruikt het nieuwe pad; de sync-skill bevat alle veiligheidsstappen; alle afwijkende oude paden zijn verwijderd of aantoonbaar historisch.

## Rollback

Revert de plan-PR of implementatie-PR als één reviewbare unit. Herstel bij padproblemen de oude discoveryroute tijdelijk met een gerichte revert; kopieer geen dubbele skills terug.

## Overdracht

Merge deze stap vóór 03 en 04. Geef de merge-SHA, nieuwe skillpaden, sync-skillversie en eventuele wrapperwijzigingen door.
