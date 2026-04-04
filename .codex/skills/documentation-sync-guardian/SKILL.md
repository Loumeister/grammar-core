# documentation-sync-guardian

## Purpose
Shared Codex skill for safe documentation updates after pushes to main.

## Read first
- `docs/repo-scope-contracts.md`
- `docs/grammar-platform-principles.md`
- `docs/content-authoring-rules.md`
- `docs/repo-sync-strategy.md`

## Use when
- a commit landed on `main`
- generated documentation needs a fast follow-up update
- code and docs may have drifted

## Rules
- update generated documentation only unless a task explicitly asks for broader edits
- prefer `docs/auto-sync/*` over README or contract rewrites
- do not rewrite local product scope from shared automation
- call out possible drift when commit behavior seems to cross repo boundaries
- do not invent features, decisions, or architecture changes
- tie every statement to commit message, changed files, or visible diff context

## Output shape
1. commit summary
2. changed files
3. documentation impact
4. possible drift or follow-up
