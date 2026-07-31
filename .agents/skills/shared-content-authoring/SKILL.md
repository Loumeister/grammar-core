---
name: shared-content-authoring
description: Create or review canonical shared grammar sentences and task content with didactic value, natural Dutch, complete metadata, and cross-product portability. Use for grammar-core content additions or revisions; do not use for product-local exercise banks, adapters, UI copy, or bulk variation.
---

# Shared Content Authoring

## Read first

- `docs/content-authoring-rules.md`
- `docs/grammar-platform-principles.md`
- the relevant didactic framework:
  - `docs/parsing-didactics-kaders.md`
  - `docs/werkwoordspellingsdidactiek-kaders.md`
- the target schema and neighboring files under `schemas/` and `content/`
- `docs/taxonomy-governance.md` when labels or misconceptions are involved

## Procedure

1. Inspect the target schema, current content conventions, identifiers, and validation commands.
2. State the target domain and the new didactic value: misconception, contrast, reasoning-changing context, or transfer function.
3. Design one central focus per item and preserve grammatical-function-first reasoning.
4. Check natural, age-appropriate Dutch and reject ambiguous school analyses.
5. Supply complete metadata for every intended instructional mode.
6. Prefer reusable, contrast-rich items over superficial variants.
7. Add or update deterministic content and schema tests.
8. Route new taxonomy distinctions through `taxonomy-evaluator-guardian`.

## Guardrails

- Keep product-local task shapes, labels, progression, renderer assumptions, and feedback structures out of canonical content.
- Do not add content solely to increase volume.
- Do not add a shared item whose quality depends on a hidden product convention.
- Do not silently modify runtime behavior in product repositories.
- Escalate when the schema cannot express required portable meaning without importing local structure.

## Output contract

Report the artifacts changed, target domain, didactic distinction added, supporting named principles, metadata and ambiguity checks, taxonomy or schema impact, tests run, and any product-local adaptation still required.
