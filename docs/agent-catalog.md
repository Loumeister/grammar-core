# Agent and Skill Catalog

This catalog maps the canonical AI instruction layers in `grammar-core`. Shared theory belongs in `docs/`; these files stay concise and operational.

## Canonical Claude agents

| Concept | Path | Goal | Primary canon |
|---|---|---|---|
| `content-expander` | `.claude/agents/content-expander.md` | Grow shared content with didactic and taxonomy discipline. | Content authoring and verb-spelling didactics |
| `didactic-architect` | `.claude/agents/didactic-architect.md` | Evaluate shared didactic structure and progression. | Platform principles and verb-spelling didactics |
| `documentation-sync-guardian` | `.claude/agents/documentation-sync-guardian.md` | Guard generated post-main summaries. | Documentation sync policy |
| `parsing-didactic-architect` | `.claude/agents/parsing-didactic-architect.md` | Guard parsing didactics and shared/local boundaries. | Parsing didactics and product contract template |
| `taxonomy-evaluator-guardian` | `.claude/agents/taxonomy-evaluator-guardian.md` | Guard meaningful taxonomy distinctions. | Taxonomy governance |

## Canonical cross-agent skills

The public discovery interface is `.agents/skills/<name>/SKILL.md`. Each skill also has `agents/openai.yaml` for Codex UI metadata.

| Skill | Goal | Read first |
|---|---|---|
| `documentation-sync-guardian` | Produce evidence-bound summaries only under `docs/auto-sync/`. | `docs/documentation-sync-policy.md`, `docs/repo-scope-contracts.md` |
| `evidence-based-werkwoordspellingsdidactiek` | Review shared verb-spelling decisions against named evidence-informed principles. | `docs/werkwoordspellingsdidactiek-kaders.md`, `docs/grammar-platform-principles.md` |
| `parsing-content-governance` | Govern parsing content and protect product-local parsing contracts. | `docs/parsing-didactics-kaders.md`, `docs/content-authoring-rules.md` |
| `shared-content-authoring` | Create portable shared content with didactic value and complete metadata. | `docs/content-authoring-rules.md`, relevant didactic framework |
| `shared-content-integration` | Adopt canonical content through explicit product adapters. | `docs/repo-sync-strategy.md`, local product contract |
| `taxonomy-evaluator-guardian` | Guard grammar labels, misconception codes, and evaluator distinctions. | `docs/taxonomy-governance.md`, relevant didactic framework |

These skills contain domain knowledge and quality gates only. General planning, TDD, debugging, Git, review, and frontend processes come from globally installed skills.

## Plugin-distributed sync skill

| Skill | Path | Goal | Installed as |
|---|---|---|---|
| `grammar-core-sync` | `plugins/grammar-core-toolkit/skills/grammar-core-sync/SKILL.md` | Safely pull canonical subtree changes, validate the product, and prepare a draft-PR handoff. | `/grammar-core-toolkit:grammar-core-sync` |

The plugin marketplace is a complementary Claude Code distribution channel. Git subtree remains the channel that makes docs, schemas, agents, and `.agents/skills` physically visible in product repositories.

## Routing boundaries

- Route canonical content creation to `shared-content-authoring`; route product adoption to `shared-content-integration`.
- Route parsing didactic or boundary decisions to `parsing-content-governance`.
- Route taxonomy changes to `taxonomy-evaluator-guardian`, even when another domain skill is also active.
- Route subtree synchronization to `grammar-core-sync`, not to content integration.
- Keep product-local UI, evaluator implementations, progression, labels, and data shapes in product repositories.
