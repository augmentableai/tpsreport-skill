# TPSReport Metadata Reference

Authoritative key lists live in the [Obsidian plugin `main.js`](https://github.com/augmentableai/tpsreport-obsidian-sync/blob/main/main.js). Machine-readable contract: [metadata-contract.yaml](metadata-contract.yaml).

## Two layers on every content doc

| Layer | Purpose | Validated by |
|-------|---------|--------------|
| **RAG core** | Agent retrieval routing | `required_core` in contract |
| **Web SEO core** | Public page `<title>`, meta description, OG tags | `required_seo` in contract |

`summary` is for **retrieval**, not a substitute for `description`. Always author both.

## RAG keys (`RAG_FM_KEYS`)

| Key | Type | Purpose |
|-----|------|---------|
| `summary` | string | Dense 2-3 sentence abstract with concrete nouns/numbers. Primary retrieval signal. |
| `keywords` | list | Exact terms/phrases a user would search. Include synonyms, acronyms, product names, numbers. |
| `intents` | list | What jobs this doc answers (snake_case verbs/nouns), e.g. `compare_networks`, `payout_lookup`. |
| `hyde_questions` | list | 4-8 natural questions this doc fully answers (HyDE-style). |
| `retrieval_hint` | string | Router instruction: when to use AND when NOT to use this doc. Keep the "Do NOT use for..." clause. |
| `scenarios` | list | Concrete situations/personas. |
| `canonical_for` | list | Topics this doc is the single source of truth for. |
| `defers_to` | map | `aspect: target-file-slug` — delegate sub-topics to the canonical doc. |
| `lifecycle_position` | int | Reading order within a learning path (1 = foundational). |
| `prerequisites` | list | Slugs the reader should know first. |
| `unlocks` | list | Slugs that become useful after this one. |
| `entities` | list | Named things (orgs, people, tools, standards). |
| `topics` | list | Broad subject areas (coarser than keywords). |
| `brands` | list | Brand/product brand names mentioned. |
| `product_skus` | list | Concrete SKUs/IDs (catalog KBs only). |
| `product_categories` | list | Category taxonomy values. |
| `region` | string/list | Geographic scope, e.g. `US`, `global`. |
| `audience` | string/list | Who the doc is for. |
| `metadata_canary` | string | Optional sentinel token to verify metadata round-trips through indexing. |

Every **content** doc gets the RAG core set: `summary`, `keywords`, `tags`, `intents`, `hyde_questions`, `retrieval_hint`, `scenarios`.

## Web SEO keys (`seo_keys`)

Stored in document frontmatter; synced to Mongo; read by SSR (`buildResourcesDocumentSeo` → `GlobalSEO`).

| Key | Required | Purpose |
|-----|----------|---------|
| `description` | **Yes** | Meta description for search/social (50–160 chars). Plain-language hook with concrete nouns. |
| `seo_title` | No | Override `<title>` when different from `title` (≤70 chars). |
| `seo_description` | No | Override meta/OG description when different from `description`. |
| `og_title` | No | Override Open Graph title (defaults to seo/title). |
| `og_description` | No | Override Open Graph description. |
| `og_image` | No | Absolute or site-relative social preview image URL. |
| `cover` | No | Alias for hero/social image when `og_image` omitted. |

**Priority on the public site (SSR):**

- Title: `seo_title` → `title` → node title
- Description: `seo_description` → `description` → `summary` → route fallback
- Image: `og_image` → `cover` → dynamic `/og/social` card

**Synonym traps (linter flags these):** `meta_title` → `seo_title`, `meta_description` → `seo_description`, `social_image` / `cover_image` / `image` → `og_image`.

## Bookkeeping keys

- Author-owned structural: `title`, `date`, `topic`, `see_also` (list of `{file, reason}`).
- Plugin-managed (NEVER hand-edit): `node_id`, `sync_status`, `last_synced`, `tps_content_hash`.

## Per-KB custom fields

KBs declare extra fields in `00_CONTEXT.md` under `kb_schema:`. The linter and plugin Gatekeeper load `kb_schema` automatically.

## Guidance keys (`GUIDANCE_FM_KEYS`)

| Key | Type | Purpose |
|-----|------|---------|
| `research_brief` | string | Assignment: scope, angle, agent question answered. |
| `research_notes` | string/list | Raw findings and facts. |
| `source_materials` | list | URLs / citations / file refs. |
| `content_structure` | string/list | Intended section outline. |
| `llm_instructions` | string | Voice, tone, formatting rules. |
| `model_preferences` | map/string | Optional model/temperature hints. |

Companion classifiers: `index_type`, `guidance_type`.

## Validation tools

| Audience | Tool | Python? |
|----------|------|---------|
| Authoring agent | [kb_lint.py](kb_lint.py) | Yes — dev/CI only |
| End client | Obsidian plugin Gatekeeper | No |
| Server | backend `/validate` on push | Server-side |

All three enforce the same contract in [metadata-contract.yaml](metadata-contract.yaml).
