# Agent guide

`grammar-core` bevat gedeelde didactische en inhoudelijke afspraken. Het bevat geen productruntime.

## Lees alleen wat de taak nodig heeft

- Systeemgrenzen of planning: `docs/system-map.md`, `docs/roadmap.md`
- Feedback- of typecontract: `docs/feedback-authoring.md`, `src/feedback/types.ts`
- Ontleedidactiek of ontleedfeedback: `docs/parsing-didactics-kaders.md`, `docs/feedback-authoring.md`
- Werkwoordspelling of spellingfeedback: `docs/werkwoordspellingsdidactiek-kaders.md`, `docs/werkwoordspellingsalgoritme.md`, en bij feedback `docs/feedback-authoring.md`
- Content of taxonomie: `docs/content-authoring-rules.md`, `docs/taxonomy-governance.md`, daarna het relevante schema
- Subtree-sync: `docs/repo-sync-strategy.md`

Lees niet standaard alle documenten. Volg in een productrepo deze volgorde: de relevante gedeelde canon hierboven, het lokale productcontract en daarna alleen de relevante runtime en tests. Code en tests bepalen het feitelijke huidige gedrag.

## Grenzen

- Deel hier alleen regels die voor minstens twee producten gelden.
- Houd routes, UI, opslag, evaluators, lokale labels en voortgang in het productrepo.
- Noem een ontwerp niet evidence-informed zonder een controleerbare bron en een concrete ontwerpregel.
- Voeg geen nieuwe abstractie, schema of tool toe voor een denkbeeldige toekomstige app.
- Wijzig canon eerst hier en synchroniseer daarna de subtree naar de productrepo's.

## Afronden

Controleer verwijzingen en JSON-syntax van gewijzigde schemas/content. Meld productrepo's die na merge een subtree-sync nodig hebben.
