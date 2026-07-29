---
name: evidence-based-werkwoordspellingsdidactiek
description: Evaluate shared verb-spelling didactics, progression, feedback, sentence growth, and taxonomy proposals against grammar-core's named evidence-informed principles. Use for didactic design or review; do not use to define product-local UI, evaluator implementations, or progression data.
---

# Evidence-Based Werkwoordspellingsdidactiek

## Read first

- `docs/werkwoordspellingsdidactiek-kaders.md`
- `docs/grammar-platform-principles.md`
- `docs/content-authoring-rules.md`
- `docs/taxonomy-governance.md` when codes or distinctions change

For product-repository work, also read its local product contract and runtime truth before proposing local changes.

## Procedure

1. Classify the proposal as shared canon, product-local logic, or a temporary bridge.
2. State the didactic problem and the exact distinction or misconception being targeted.
3. Link each recommendation to a named principle from the canonical framework.
4. Check function-first reasoning, visible reasoning steps, meaningful contrast, diagnostic feedback, scaffolding, and transfer as applicable.
5. Reject item growth that adds only surface variation or permits solving without grammatical-function reasoning.
6. Route taxonomy changes through `taxonomy-evaluator-guardian`.
7. Name the content, test, or validation change needed to protect the decision.

## Guardrails

- Use “evidence-informed” or “evidence-based” only with explicit principle linkage.
- Keep product-local evaluator behavior, feedback flows, progression, labels, and data shapes local.
- Do not claim future platform layers are operational.
- Escalate when canonical principles conflict or product adoption is undocumented.

## Output contract

Report:

1. the didactic problem;
2. the targeted distinction or misconception;
3. the supporting named principle or principles;
4. the shared/local boundary decision;
5. required validation, tests, or content changes;
6. verdict: accept, revise, reject, or requires local product decision.
