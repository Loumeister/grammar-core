---
name: shared-content-integration
description: Integrate canonical grammar-core content into product repositories through explicit adapters and verified mappings. Use for adopting shared sentences, schemas, or taxonomy in a product; do not use to author canonical content, perform subtree synchronization, or replace product-local runtime contracts.
---

# Shared Content Integration

## Read first

- `docs/content-authoring-rules.md`
- `docs/repo-sync-strategy.md`
- `docs/repo-scope-contracts.md`
- `docs/taxonomy-governance.md`
- the consuming repository's local product contract and runtime content model

## Procedure

1. Identify the exact canonical source artifact and version present under `shared/grammar-core/`.
2. Confirm what the local product contract explicitly adopts.
3. Compare shared fields and concepts with current local runtime structures.
4. Implement the smallest explicit adapter or mapping at the product boundary.
5. Keep display labels, progression, evaluation, feedback, renderer assumptions, and storage shapes local.
6. Add mapping, schema-drift, content, and runtime tests proportional to the integration.
7. Document the adoption boundary when the local contract or architecture changes.

## Guardrails

- Do not edit `shared/grammar-core/` locally to make an adapter pass.
- Do not duplicate canonical content into an independently maintained local source.
- Do not treat common product shorthand as canonical taxonomy.
- Do not claim an aspirational shared layer is operational.
- Route canonical source changes upstream first; use `grammar-core-sync` only for subtree synchronization.
- Stop when the shared artifact is insufficient or the local contract conflicts with runtime truth, and report the required upstream or local decision.

## Output contract

Report the canonical source, local consumer, explicit field or concept mapping, preserved local behaviors, tests and validations run, documentation updated, and any upstream follow-up.
