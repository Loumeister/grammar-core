# grammar-core

Gedeelde canon voor [Werkwoordlab](https://github.com/Loumeister/werkwoordlab) en [Ontleedlab](https://github.com/Loumeister/ontledingstrainer). De twee apps blijven zelfstandige producten; deze repository deelt alleen stabiele didactiek, taxonomie, schema's, kleine contentsets en werkelijk gebruikte typecontracten.

## Begin hier

- `AGENTS.md`: taakgerichte leesroute en grenzen
- `docs/system-map.md`: producten, eigenaarschap en bronhiërarchie
- `docs/roadmap.md`: actuele volgorde en beslispoorten
- `docs/parsing-didactics-kaders.md`: ontleedidactiek
- `docs/werkwoordspellingsdidactiek-kaders.md`: werkwoordspellingsdidactiek
- `docs/feedback-authoring.md`: feedbackcriteria
- `docs/taxonomy-governance.md`: begrippen en misconceptiecodes
- `docs/repo-sync-strategy.md`: subtree bijwerken

## Wat hier niet hoort

Routes, componenten, opslag, evaluators, dashboards, lokale labels en voortgangslogica blijven in het productrepo. Een mogelijk geïntegreerd product rechtvaardigt nu geen gedeelde runtime, nieuw framework of monorepo.

## Indeling

- `docs/`: gedeelde afspraken
- `schemas/`: gedeelde uitwisselingsvormen die werkelijk gebruikt worden
- `content/`: gedeelde taxonomie en kleine zinsets
- `adapters/`: integratierichtlijnen voor beide producten
- `.claude/agents/` en `.codex/skills/`: smalle taakhulpen; nooit een tweede canon

Productrepo's spiegelen deze map onder `shared/grammar-core/` met git subtree. Verbeter gedeelde canon eerst hier, merge die wijziging en synchroniseer daarna beide productrepo's.
