# 04 — ontledingstrainer skill migration

## Eindtoestand

`<workspace-root>/ontledingstrainer` bevat een compacte parsinggerichte skillset onder `.agents/skills/` en gebruikt globale skills voor algemene engineering en UI-audit.

## Start in een verse context

- Terra `medium` voor inventarisatie, consolidatieverplaatsingen en verwijderen.
- Sol `xhigh` voor skillontwerp, consolidatie-inhoud en routingtests.
- Lees: repo-instructies, relevante `shared/grammar-core/docs/`, lokaal productcontract, runtimewaarheid, bestaande skills, dit bestand.
- Paden: resolve `<workspace-root>` als de map met repo-checkouts en `<repo-root>` als de afzonderlijke `ontledingstrainer`-checkout; neem geen vaste lokale checkoutlocatie aan.

## Afhankelijkheden

Stap 01 is valide en de `grammar-core`-implementatie-PR uit stap 02 is gemerged. Synchroniseer die merge eerst in een afzonderlijke sync-only branch en PR en merge die PR vóór deze migratiestap.

Laat de eerste sync niet afhangen van een nog niet vindbare plugin-skill. Als `grammar-core-sync` nog niet geïnstalleerd of discoverable is, lees `<workspace-root>/grammar-core/plugins/grammar-core-toolkit/skills/grammar-core-sync/SKILL.md` rechtstreeks uit de gemergede canonieke checkout en gebruik dat bestand als runbook: verifieer schone worktree, remotes en default branches; maak een sync-only branch; voer `git subtree pull --prefix=shared/grammar-core <canonical-remote> <canonical-default-branch> --squash` uit; controleer dat de diff vóór lokale referentie-updates alleen `shared/grammar-core/` raakt; draai productchecks; merge de sync-only PR. Maak daarna vanaf de productbasisbranch mét die sync-merge een nieuwe migratiebranch. Wrapper- en skillmigratie-edits horen nooit in de sync-only PR.

## Terra → Sol-overdracht

Terra voert alleen inventarisatie, consolidatieverplaatsingen, verwijderingen en mechanische referentiecorrecties uit. Terra levert vóór de modelwissel basis-SHA, `git status --short --branch`, bewijs van de gemergede sync-PR en grammar-core-SHA, voor/na-skillinventaris, consolidatie- en padmapping, `git diff --name-status`, de volledige mechanische diff en bewaarde gebruikerswijzigingen.

Sol begint pas met consolidatie-inhoud, wrappergedrag, triggers en routingtests nadat deze bundel compleet is en de diff uitsluitend de afgesproken mechanische scope raakt. Bij ontbrekend syncbewijs of een onverklaarde inhoudelijke wijziging stopt Sol en draagt het specifieke bestand of hunk terug over; Sol mengt de sync-, Terra- en Sol-fasen niet stilzwijgend.

## Doelset

- `zinsontleding-repo-inspector`
- `zinsontleding-constraint-sentence-author`
- `zinsontleding-content-quality-gate`
- `zinsontleding-feedback-didactiek`
- `ontleedlab-learner-flow-ui`
- `ontleedlab-learning-analytics`
- `parsing-content-governance`
- `shared-content-integration`
- `documentation-sync-guardian`
- `grammar-core-sync`

## Procedure

1. Terra verifieert dat de actuele migratiebranch afstamt van de gemergede sync-only PR en inventariseert skills, wrappers, referenties en lokale runtimecontracten.
2. Terra verplaatst de bestanden voor `content-curator` naar `zinsontleding-content-quality-gate` en die voor `grammar-coach` naar `zinsontleding-feedback-didactiek`, zonder de inhoud al te herschrijven.
3. Terra verwijdert `frontend-developer`, `technical-writer`, `test-engineer` en `whimsy-injector` en werkt mechanische paden in repo-instructies, context, `docs/agents/` en catalogi bij.
4. Terra levert de bewijsbundel uit de overdrachtssectie en stopt.
5. Sol consolideert de inhoud van `content-curator` in `zinsontleding-content-quality-gate` en van `grammar-coach` in `zinsontleding-feedback-didactiek`.
6. Sol brengt productspecifieke toegankelijkheidsverplichtingen onder in `ontleedlab-learner-flow-ui` en maakt shared wrappers dun door eerst de corresponderende `.agents/skills` in de subtree te lezen.
7. Sol voegt frontmatter en `agents/openai.yaml` toe of actualiseert ze en verwijdert algemene TDD-, Git-, review- en planningsinstructies uit de doelskills.
8. Sol voert de routingtests uit en controleert de volledige inhoudelijke diff na het Terra-werk.

## UI-routing

Gebruik globale `frontend-design` samen met `ontleedlab-learner-flow-ui` voor leerlingflows en sluit af met globale `web-design-guidelines`.

## Niet wijzigen

- Lokale annotatievelden, RoleKeys, JSON-shapes, chunkconventies, evaluatorgedrag en feedbackflows zonder expliciete functionele opdracht.
- Productruntime buiten noodzakelijke wrapper- of referentiecorrecties.

## Validatie

- `npx skills list --json`
- Frontmatter/openai.yaml- en directorynaamvalidatie.
- Vanuit `<repo-root>`: `rg -n --hidden --glob '!.git/**' '\.codex/skills|frontend-developer|technical-writer|test-engineer|whimsy-injector|superpowers|planetscale' -- .`.
- Positieve en negatieve routing, inclusief combinatietest voor een leerlingflow.
- Bestaande content-, unit-, integratie- en e2e-checks.
- `git diff --check`

## Voltooiingscriteria

De doelset is volledig vindbaar, consolidaties hebben geen productregels verloren, shared canon en lokale parsingcontracten zijn zichtbaar gescheiden en alle relevante checks slagen of documenteren uitsluitend pre-existente fouten.

## Rollback

Revert de product-PR. Herstel een geconsolideerde skill alleen als de nieuwe doelskill aantoonbaar een unieke lokale invariant mist; behoud dan één bron van waarheid.

## Overdracht

Noteer grammar-core-SHA, de gemergede sync-PR en sync-merge-SHA, de afzonderlijke productmigratiebranch, syncbewijs, consolidatiemapping, routingtests en validaties voor stap 06.
