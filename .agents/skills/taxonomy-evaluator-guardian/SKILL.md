---
name: taxonomy-evaluator-guardian
description: Guard canonical grammar labels, misconception codes, and proposed evaluator distinctions against taxonomy drift. Use when adding, renaming, deprecating, mapping, or reviewing a taxonomy distinction; do not use to define product-local keys, feedback matrices, evaluator implementations, or progression.
---

# Taxonomy Evaluator Guardian

## Read first

- `docs/taxonomy-governance.md`
- the relevant didactic framework in `docs/`
- `content/taxonomy/misconceptions.nl.json` for misconception-code changes
- affected schemas, content, and product contracts

## Procedure

1. Classify the proposal as a grammar-role label, misconception code, alias, product-local key, or evaluator-only distinction.
2. Check whether an existing canonical concept already covers it.
3. For a grammar label, require a distinct Dutch school-grammar concept, cross-product applicability, and a non-product-specific name.
4. For a misconception code, require a systematically distinct error, a meaningfully different recovery path, and improved teacher insight.
5. For rename or deprecation, document compatibility, replacement, notification, and at least one sync cycle where required.
6. Keep product-local evaluator logic and mappings local; update canonical sources only for genuinely portable distinctions.
7. Update affected schemas, content, docs, mappings, and deterministic tests together.

## Guardrails

- Never promote RoleKeys, short labels, display strings, JSON fields, feedback matrices, or progression levels into shared canon.
- Reject cosmetic splits and distinctions with identical recovery or intervention.
- Do not call a distinction evidence-informed without naming its didactic principle.
- Escalate conflicting analyses or changes that require an undocumented local adoption decision.

## Output contract

Report the proposed distinction and category, duplicate check, didactic justification, recovery and teacher-signal test, shared/local decision, compatibility impact, required files and validations, and verdict: accept, revise, reject, or local-only.
