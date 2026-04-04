# Repo Scope Contracts

This document states what belongs in each repo.

## grammar-core
- Owns shared didactic canon.
- Owns shared taxonomy governance.
- Owns shared schema direction.
- Owns shared sentence and content rules.
- Owns shared AI instruction layers.
- Does not own local runtime UI, local evaluator behavior, local dashboards, local route logic, or product-specific feedback flows.
- Does not become a third product.

## ontledingstrainer
- Owns the local parsing product.
- Owns parsing UI, learner flow, local annotation conventions, local evaluator behavior, local sentence presentation, and parsing-specific teacher tooling.
- May contain parsing-adjacent support flows if parsing remains the main instructional mode.
- Does not own canonical werkwoordspelling runtime or shared didactic governance.

## werkwoordlab
- Owns the local werkwoordspelling product.
- Owns the learner flow from grammar function to rule choice to spelling application.
- Owns local evaluator behavior, misconception mapping, unit progression, and spelling-specific teacher insights.
- May contain short transfer tasks if they remain subordinate to werkwoordspelling.
- Does not own parsing runtime UI or shared didactic governance.

## Boundary rule
If a change mainly affects shared didactic principles, shared taxonomy, shared sentence rules, or shared AI instructions, it belongs in grammar-core.
If a change mainly affects local learner flow, local UI, local evaluator behavior, local annotations, or local teacher workflows, it belongs in the product repo.
