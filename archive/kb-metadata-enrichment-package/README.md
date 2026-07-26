# KB Metadata Enrichment — Skills Package

Distribution bundle for the **TPSReport KB generation** skill (Obsidian + Cursor + agents).

**Gold source (monorepo):** `.agents/skills/tpsreport-knowledge-base-generation/`

**Sync all copies:** `powershell scripts/sync-tpsreport-kb-skill.ps1` from repo root.

## Package layout (same everywhere)

```text
SKILL.md
evals/evals.json
references/
├── metadata-contract.yaml   ← contract (sync with plugin Gatekeeper)
├── kb_lint.py               ← Phase 4 linter
├── METADATA.md
├── LIFECYCLE.md
├── QUALITY_BAR.md
├── KB_AGENT_PROMPT.md
└── EXAMPLES.md
```

## Install — Cursor (project skill)

Copy this entire folder to:

```text
.cursor/skills/kb-metadata-enrichment/
```

(or `.cursor/skills/tpsreport-knowledge-base-generation/` — same contents)

Cursor discovers skills from `.cursor/skills/*/SKILL.md`.

## Validate a KB folder

```bash
python .cursor/skills/kb-metadata-enrichment/references/kb_lint.py path/to/your/KB_folder/
```

Requires **Python 3.9+** and **PyYAML** (`pip install pyyaml`).

## Public installs

| Channel | Command / repo |
|---------|----------------|
| **Skills CLI** | `npx skills add augmentableai/skills --skill tpsreport-knowledge-base-generation -y` |
| **GitHub** | [github.com/augmentableai/kb-metadata-enrichment](https://github.com/augmentableai/kb-metadata-enrichment) |

## License

MIT · Augmentable.ai / TPSReport
