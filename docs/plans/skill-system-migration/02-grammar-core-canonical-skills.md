# 02 — grammar-core canonical skills

## Eindtoestand

`<workspace-root>/grammar-core` publiceert zes canonieke domeinskills onder `.agents/skills/`, een veilige `grammar-core-sync`-skill en actuele repo-instructies, workflowpaden en catalogi.

## Start in een verse context

- Terra `medium`: inventarisatie, `git mv`, directoryopruiming en mechanische padwijzigingen.
- Sol `xhigh`: iedere wijziging aan `SKILL.md`, triggers, procedures, outputcontracten en `agents/openai.yaml`.
- Lees: `AGENTS.md` of `CLAUDE.md`, relevante `docs/`, bestaande skills/agents, daarna dit bestand.
- Paden: resolve `<workspace-root>` als de map met repo-checkouts en `<repo-root>` als de afzonderlijke `grammar-core`-checkout; neem geen vaste lokale checkoutlocatie aan.

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

## Terra → Sol-overdracht

Terra voert alleen inventarisatie en mechanische verplaatsingen, verwijderingen en padupdates uit. Terra stopt vóór inhoudelijke skillbewerking en levert een bewijsbundel met basis-SHA, `git status --short --branch`, voor/na-inventaris, oude→nieuwe padmapping, `git diff --name-status`, de volledige mechanische diff en bewaarde gebruikerswijzigingen.

Sol begint pas als die bundel compleet is. Sol controleert eerst dat de mechanische diff uitsluitend de afgesproken scope raakt en geen `SKILL.md`-betekenis heeft veranderd. Sol is daarna eigenaar van triggers, procedures, guardrails, metadata, routingtests en de inhoudelijke eindreview. Bij een onverklaarde mechanische of semantische afwijking stopt Sol en draagt het punt met bestand en hunk terug over; Sol repareert de Terra-fase niet stilzwijgend.

## Procedure

1. Terra legt basis-SHA, status, bestaande discoveryroutes, skills, agents, gebruikerswijzigingen en actuele padreferenties vast.
2. Terra verplaatst bestaande `.codex/skills/*` met `git mv` naar `.agents/skills/`, werkt actuele paden atomair bij en wijzigt de docs-syncworkflow naar `.agents/skills/documentation-sync-guardian/SKILL.md`. Historische bronpaden worden expliciet gemarkeerd in plaats van herschreven.
3. Terra levert de bewijsbundel uit de overdrachtssectie en stopt.
4. Sol controleert de overdracht en voegt daarna de twee ontbrekende skills toe; alle zes krijgen alleen `name` en `description` in YAML-frontmatter.
5. Sol geeft iedere skill precieze positieve triggers, negatieve grenzen, leesroute, procedure, guardrails, outputcontract en escalatiepad.
6. Sol voegt per skill `agents/openai.yaml` toe met gequote `display_name`, `short_description` van 25–64 tekens en een `default_prompt` met `$skill-name`.
7. Sol herschrijft `grammar-core-sync` met clean-worktreecontrole, remote- en default-branchdetectie, veilige subtree-pull, conflictinspectie per bestand, scopecheck, productvalidatie en draft-PR-overdracht. Verbied blanket `checkout --theirs`.
8. Sol maakt een compacte `AGENTS.md` met leesvolgorde, runtimewaarheid, shared/local-grens, Matt-procesrol en exacte skillrouting en controleert de volledige inhoudelijke diff na het Terra-werk.

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
Set-Location '<repo-root>'
Get-ChildItem .agents\skills -Directory
npx skills list --json
rg -n --hidden --glob '!.git/**' '\.codex/skills|checkout --theirs|superpowers|planetscale' -- .
git diff --check
```

Voer daarnaast `quick_validate.py` uit voor iedere skill, parse alle `agents/openai.yaml`, valideer de Claude-plugin wanneer `.claude-plugin` of pluginstructuur wijzigt en controleer dat directorynaam en frontmatternaam gelijk zijn.

## Voltooiingscriteria

Discovery vindt exact de zes repo-skills; de workflow gebruikt het nieuwe pad; de sync-skill bevat alle veiligheidsstappen; alle afwijkende oude paden zijn verwijderd of aantoonbaar historisch.

## Rollback

Revert de plan-PR of implementatie-PR als één reviewbare unit. Herstel bij padproblemen de oude discoveryroute tijdelijk met een gerichte revert; kopieer geen dubbele skills terug.

## Overdracht

Merge de implementatie-PR uit deze stap vóór iedere productsync. Geef de merge-SHA, gedetecteerde canonieke default branch, nieuwe skillpaden en sync-skillversie door.

Maak daarna in `werkwoordlab` en `ontledingstrainer` elk een afzonderlijke sync-only branch en PR. De eerste sync mag niet afhangen van skill-discovery die pas door diezelfde sync beschikbaar komt. Als `grammar-core-sync` nog niet geïnstalleerd of vindbaar is, gebruik dan het gemergede bestand `<workspace-root>/grammar-core/plugins/grammar-core-toolkit/skills/grammar-core-sync/SKILL.md` rechtstreeks als runbook en voer deze bootstrap expliciet uit:

1. verifieer een schone productworktree, de productbasisbranch, de canonieke remote en de canonieke default branch;
2. maak vanaf de productbasisbranch een sync-only branch;
3. voer `git subtree pull --prefix=shared/grammar-core <canonical-remote> <canonical-default-branch> --squash` uit en verifieer dat de opgehaalde geschiedenis de doorgegeven merge-SHA bevat;
4. controleer vóór lokale referentie-updates dat de diff uitsluitend `shared/grammar-core/` raakt en draai de geraakte productchecks;
5. review en merge de sync-only PR zonder wrapper- of skillmigratie-edits.

Start stap 03 of 04 pas daarna vanaf de productbasisbranch die deze sync-merge bevat. Zo blijven de canonieke implementatie, productsync en productmigratie drie afzonderlijk reviewbare wijzigingen.
