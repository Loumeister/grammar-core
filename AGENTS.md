# AGENTS.md — grammar-core

## Repository purpose

`grammar-core` is the canonical shared layer for grammar didactics, content governance, taxonomy, schemas, and portable AI instructions. It is not a product repository.

## Working order

For every task:

1. Read this file.
2. Read only the relevant canonical documents in `docs/`.
3. Read the exactly matching skill in `.agents/skills/`.
4. Inspect current files, schemas, content, and tests as runtime truth.
5. Apply the task prompt.

Runtime truth outranks documentation. Correct stale documentation in the same change; do not change runtime merely to make it match a document.

## Shared/local boundary

Promote only portable principles, governance, schemas, content, or type contracts. Keep product-local UI, evaluator behavior, progression, labels, JSON shapes, annotations, feedback flows, dashboards, and route logic in the product repository.

When work touches a product repository, read `shared/grammar-core/` first, its local product contract second, and local runtime truth third.

## Skills

Use exactly the domain skill matching the workstream:

- `documentation-sync-guardian` for generated post-main documentation summaries.
- `evidence-based-werkwoordspellingsdidactiek` for didactic review of verb-spelling proposals.
- `parsing-content-governance` for shared parsing content and parsing boundary decisions.
- `shared-content-authoring` for creating or reviewing canonical shared content.
- `shared-content-integration` for product adapters and subtree content adoption.
- `taxonomy-evaluator-guardian` for canonical taxonomy or evaluator distinctions.

General engineering process comes from the globally installed Matt Pocock skills. Use global `frontend-design` for any explicitly requested UI design/build work and `web-design-guidelines` for the closing UI audit; this repository normally owns no product UI. Do not duplicate generic planning, TDD, Git, review, frontend, or debugging procedures in repo skills.

## Delivery discipline

- Anchor non-trivial work to an issue or numbered plan step, and state its scope.
- Before editing, select the applicable global Matt process skill and local domain skill.
- Decide the test and validation evidence before implementation.
- Review the exact Git range before claiming completion.
- Report commands, results, and failures honestly.
- Do not claim work is done until applicable checks and required review pass.

## Required reporting

For substantial changes, report files read and changed, validations run, the shared/local boundary decision, and any remaining product-specific ambiguity. Do not call a proposal evidence-based without naming the supporting canonical principle.
