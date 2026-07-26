# TPSReport KB Lifecycle (Phases 0–6)

```
Phase 0  Scope & assess
Phase 1  Seed (guidance-first)
Phase 2  Generate content
Phase 3  Enrich RAG metadata
Phase 4  Validate (kb_lint.py exit 0)
Phase 5  Build -> Push -> Gate
Phase 6  Test & Iterate
```

## Phase 0 — Scope & Assess

1. List the target KB folder in the Obsidian vault.
2. Read `00_CONTEXT.md` for topic, audience, voice, and glossary.
3. Read any `_TEMPLATE` file for frontmatter shape and `retrieval_hint` pattern.
4. Build a file inventory grouped by section.
5. Produce a coverage map, duplication audit, metadata health score, and prioritized fix list. Confirm scope with the user before bulk edits.

## Phase 1 — Seed (new reports)

1. Create the file in the right section with `title`, `description`, `date`, `topic`, and a heading.
2. Fill guidance keys: `research_brief`, `content_structure`, `source_materials`, `llm_instructions`.
3. Body can be a stub; set `guidance_type` / `index_type` if needed.

## Phase 2 — Generate content

1. Gather facts into `research_notes`; cite in `source_materials`.
2. Draft the body following `content_structure` and `llm_instructions`.
3. Never invent numbers; keep guidance keys for provenance.

## Phase 3 — Enrich RAG + web SEO metadata

1. Read the full body; classify doc type.
2. Extract nouns into `keywords`, `entities`, `brands`.
3. Author RAG frontmatter per [METADATA.md](METADATA.md): strong `summary`, 8–20 `keywords`, 4–8 `hyde_questions`, shared `intents`, negative clause in `retrieval_hint`, correct `see_also` / `defers_to` slugs.
4. Author **web SEO frontmatter** on the same doc:
   - **`description`** (required, 50–160 chars) — compelling meta for public pages; not the same text as `summary`.
   - Optional: `seo_title`, `seo_description`, `og_image` when you need overrides.
5. Light body polish only when thin — preserve voice on finished docs.

## Phase 4 — Validate

```bash
python references/kb_lint.py <kb-folder>
```

Fix every error; re-run until exit 0. The plugin Gatekeeper enforces the same rules at sync.

## Phase 5 — Push & Gate

1. Map the folder in the Obsidian plugin.
2. Run sync (push-and-delete sync).
3. Set sharing preset and RAG enabled toggle.
4. Confirm metadata surfaces in TPSReport.

Never push without explicit user approval.

## Phase 6 — Test & Iterate

1. Build a question set from `hyde_questions` and coverage gaps.
2. Probe retrieval against real agent questions.
3. Diagnose misses (weak metadata, wrong doc, missing doc, stale body).
4. Fix, re-validate, re-push, re-test.
