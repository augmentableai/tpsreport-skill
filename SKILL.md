---
name: tpsreport-skill
description: Builds, enriches, lints, and syncs TPSReport Obsidian knowledge bases with Graph RAG frontmatter. Use when authoring KB folders, YAML metadata (summary, keywords, hyde_questions, retrieval_hint), kb_lint.py validation, or TPSReport plugin push workflows.
license: MIT
compatibility: Requires Python 3.9+ and PyYAML for kb_lint.py. Pairs with the TPSReport Obsidian plugin.
metadata:
  author: Augmentable.ai
  version: "1.2.0"
  brand: TPSReport by Augmentable.ai
---

# TPSReport KB Skill

**TPSReport by [Augmentable.ai](https://augmentable.ai)** — workflow skill for Obsidian knowledge bases synced to [TPSReport](https://tpsreport.pro).

Manages the full KB lifecycle: seed, generate, enrich retrieval metadata, validate, push via the Obsidian plugin, and iterate against real agent questions.

## When to use

- Seed a new KB or add reports/sections
- Generate report bodies from guidance (`research_brief`, `content_structure`)
- Enrich empty or partial frontmatter on finished prose
- Assess an existing KB (coverage gaps, duplicates, metadata health)
- Validate before push and tune retrieval after push

## Guardrails

- Never invent facts — derive from body or cited sources
- Never hand-edit plugin-managed keys (`node_id`, `sync_status`, `last_synced`, `tps_content_hash`)
- Never rewrite a finished doc's voice
- Never push without explicit user approval

## Quick workflow

1. **Scope** — read `00_CONTEXT.md`, inventory the vault, audit gaps. See [references/LIFECYCLE.md](references/LIFECYCLE.md) Phase 0.
2. **Seed / generate** — guidance-first for new reports (Phases 1–2).
3. **Enrich** — fill RAG frontmatter per [references/METADATA.md](references/METADATA.md) (Phase 3).
4. **Validate** — run the linter and fix until exit 0:

```bash
python scripts/kb_lint.py path/to/Your_KB/
```

5. **Push** — user maps folder and syncs via the TPSReport Obsidian plugin; set RAG + sharing (Phase 5).
6. **Iterate** — test agent questions, fix under-retrieval, loop (Phase 6).

## Bundled resources

| File | Purpose |
|------|---------|
| [references/metadata-contract.yaml](references/metadata-contract.yaml) | Machine-readable key contract |
| [scripts/kb_lint.py](scripts/kb_lint.py) | Deterministic frontmatter linter |
| [references/LIFECYCLE.md](references/LIFECYCLE.md) | Full phase-by-phase workflow |
| [references/METADATA.md](references/METADATA.md) | RAG + guidance key reference |
| [references/EXAMPLES.md](references/EXAMPLES.md) | Frontmatter examples |
| [references/QUALITY_BAR.md](references/QUALITY_BAR.md) | Quality checklist |
| [references/KB_AGENT_PROMPT.md](references/KB_AGENT_PROMPT.md) | Agent prompt template |

Plugin source: [tpsreport-obsidian-sync](https://github.com/augmentableai/tpsreport-obsidian-sync).

## Anti-patterns

- Synonym keys TPSReport ignores (`questions` instead of `hyde_questions`)
- Generic keywords that match everything
- Missing negative clause in `retrieval_hint`
- Pushing before `kb_lint.py` exits 0
- Enriching once without testing retrieval
