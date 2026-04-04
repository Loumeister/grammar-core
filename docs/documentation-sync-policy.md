# Documentation Sync Policy

## Goal
Keep a small generated documentation trail in sync with commits on `main`.

## Automated files
The automation may update only files in `docs/auto-sync/` unless a human task explicitly broadens scope.

## Why this is narrow
Automatic rewriting of README files, contracts, or product specs is too risky without a human review step.
The safe default is to update generated summaries first and let humans decide whether core docs need a follow-up edit.

## Agent sources
- Claude agent: `.claude/agents/documentation-sync-guardian.md`
- Codex skill: `.codex/skills/documentation-sync-guardian/SKILL.md`

## Required secrets
- `ANTHROPIC_API_KEY` for the Claude summary
- `OPENAI_API_KEY` for the Codex summary

## Expected outputs
- `docs/auto-sync/claude-latest-main-summary.md`
- `docs/auto-sync/codex-latest-main-summary.md`
