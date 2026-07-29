# 04 — ontledingstrainer skill migration

## Eindtoestand

`C:\Users\cpfva\Code\ontledingstrainer` bevat een compacte parsinggerichte skillset onder `.agents/skills/` en gebruikt globale skills voor algemene engineering en UI-audit.

## Start in een verse context

- Terra `medium` voor inventarisatie, consolidatieverplaatsingen en verwijderen.
- Sol `xhigh` voor skillontwerp, consolidatie-inhoud en routingtests.
- Lees: repo-instructies, relevante `shared/grammar-core/docs/`, lokaal productcontract, runtimewaarheid, bestaande skills, dit bestand.

## Afhankelijkheden

Stap 01 is valide en stap 02 is gemerged. Synchroniseer eerst de gemergede canon.

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

1. Inventariseer skills, wrappers, referenties en lokale runtimecontracten.
2. Consolideer `content-curator` in `zinsontleding-content-quality-gate`.
3. Consolideer `grammar-coach` in `zinsontleding-feedback-didactiek`.
4. Breng productspecifieke toegankelijkheidsverplichtingen onder in `ontleedlab-learner-flow-ui`.
5. Maak shared wrappers dun en laat ze eerst de corresponderende `.agents/skills` in de subtree lezen.
6. Verwijder `frontend-developer`, `technical-writer`, `test-engineer` en `whimsy-injector`.
7. Voeg/actualiseer frontmatter en `agents/openai.yaml`; verwijder algemene TDD-, Git-, review- en planningsinstructies.
8. Werk repo-instructies, context, agentsdocs, catalogi en paden bij.

## UI-routing

Gebruik globale `frontend-design` samen met `ontleedlab-learner-flow-ui` voor leerlingflows en sluit af met globale `web-design-guidelines`.

## Niet wijzigen

- Lokale annotatievelden, RoleKeys, JSON-shapes, chunkconventies, evaluatorgedrag en feedbackflows zonder expliciete functionele opdracht.
- Productruntime buiten noodzakelijke wrapper- of referentiecorrecties.

## Validatie

- `npx skills list --json`
- Frontmatter/openai.yaml- en directorynaamvalidatie.
- `rg` op `.codex/skills`, verwijderde generieke skills, Superpowers en PlanetScale.
- Positieve en negatieve routing, inclusief combinatietest voor een leerlingflow.
- Bestaande content-, unit-, integratie- en e2e-checks.
- `git diff --check`

## Voltooiingscriteria

De doelset is volledig vindbaar, consolidaties hebben geen productregels verloren, shared canon en lokale parsingcontracten zijn zichtbaar gescheiden en alle relevante checks slagen of documenteren uitsluitend pre-existente fouten.

## Rollback

Revert de product-PR. Herstel een geconsolideerde skill alleen als de nieuwe doelskill aantoonbaar een unieke lokale invariant mist; behoud dan één bron van waarheid.

## Overdracht

Noteer grammar-core-SHA, syncbewijs, consolidatiemapping, routingtests en validaties voor stap 06.
