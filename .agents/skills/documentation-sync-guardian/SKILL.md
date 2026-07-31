---
name: documentation-sync-guardian
description: Produce evidence-bound post-main documentation summaries only under docs/auto-sync. Use after a commit lands on main or when supplied commit evidence must become a generated summary; do not use for canonical docs, contracts, product specs, workflow design, or architecture decisions.
---

# Documentation Sync Guardian

## Read first

- `docs/documentation-sync-policy.md`
- `docs/repo-scope-contracts.md`

## Procedure

1. Inspect the supplied commit message, changed-file list, commit SHA, and diff excerpt.
2. Separate directly supported facts from inference. Omit facts that the available evidence cannot support.
3. Summarize what changed, why it matters, and any clearly evidenced follow-up.
4. Write only the requested file under `docs/auto-sync/`.
5. Verify that no canonical document, contract, product specification, or runtime file changed.

## Guardrails

- Tie every claim to the supplied commit evidence.
- Describe only current repository state; do not invent features, intent, or architecture.
- Do not repair documentation drift outside `docs/auto-sync/`.
- Do not rewrite product-local scope from shared automation.
- Stop and request human review when the requested target is outside `docs/auto-sync/` or the evidence conflicts.

## Output contract

When invoked by automation, return only the Markdown body for the requested generated file. When invoked interactively, also report the target path, evidence inspected, and any material omission caused by insufficient evidence.
