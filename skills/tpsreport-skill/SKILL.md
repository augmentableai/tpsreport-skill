---
name: tpsreport-skill
description: Builds, enriches, lints, and syncs TPSReport Obsidian knowledge bases with Graph RAG frontmatter. Use when authoring KB folders, YAML metadata, kb_lint.py validation, or TPSReport plugin push workflows.
metadata:
  author: Augmentable.ai
  brand: TPSReport by Augmentable.ai
---

# TPSReport KB Skill

**TPSReport by Augmentable.ai** — workflow skill for Obsidian knowledge bases synced to TPSReport.

## When to Use

Use this skill when:
- seeding or expanding a TPSReport knowledge base in Obsidian
- enriching YAML frontmatter (`summary`, `keywords`, `hyde_questions`, `retrieval_hint`)
- running `kb_lint.py` before push
- mapping folders and syncing via the TPSReport Obsidian plugin
- assessing KB coverage, duplicates, or retrieval quality after push

## Instructions

When activated, manage the full KB lifecycle: scope, seed, generate, enrich, validate, push, iterate.

### Phase 0 — Scope

1. Read `00_CONTEXT.md` for topic, audience, voice, and glossary.
2. Inventory the vault by section; note gaps and overlapping docs.
3. Produce a prioritized fix list; confirm scope with the user before bulk edits.

### Phase 1–2 — Seed and generate

1. Create guidance-first reports with `research_brief`, `content_structure`, `source_materials`, `llm_instructions`.
2. Generate bodies from guidance; keep facts traceable to sources.

### Phase 3 — Enrich metadata

Fill RAG frontmatter using exact key names from the TPSReport plugin (`summary`, `keywords`, `intents`, `hyde_questions`, `retrieval_hint`, `scenarios`, `canonical_for`, `defers_to`). Full key reference: `references/METADATA.md`.

### Phase 4 — Validate

```bash
python scripts/kb_lint.py path/to/Your_KB/
```

Fix every error; re-run until exit 0. Contract: `references/metadata-contract.yaml`.

### Phase 5 — Push

User maps the folder and syncs via the Obsidian plugin. Set RAG enabled and sharing preset. Never push without explicit user approval.

### Phase 6 — Iterate

Test real agent questions; fix under-retrieval in metadata or content; re-validate and re-push.

## Guardrails

- Never invent facts — derive from body or cited sources
- Never hand-edit plugin-managed keys (`node_id`, `sync_status`, `last_synced`, `tps_content_hash`)
- Never rewrite a finished doc's voice
- Never push without explicit user approval

## Bundled resources

- `references/LIFECYCLE.md` — full phase workflow
- `references/METADATA.md` — RAG and guidance key tables
- `references/EXAMPLES.md` — frontmatter examples
- `references/QUALITY_BAR.md` — quality checklist
- `scripts/kb_lint.py` — deterministic linter

## Anti-patterns

- Synonym keys TPSReport ignores (`questions` instead of `hyde_questions`)
- Generic keywords that match everything
- Missing negative clause in `retrieval_hint`
- Pushing before `kb_lint.py` exits 0
