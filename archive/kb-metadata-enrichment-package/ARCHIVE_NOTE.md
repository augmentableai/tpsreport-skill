# Archived — kb-metadata-enrichment-package

Archived 2026-07-17 from `backend/Obsidian/kb-metadata-enrichment-package/`.

- A variant of the TPSReport KB skill (`name: tpsreport-knowledge-base-generation`, v1.0.0).
- ⚠️ **Contains newer `kb_lint.py` (references/kb_lint.py, 26,260 B) than the canonical repo** — it adds
  **web-SEO-key validation** driven by `references/metadata-contract.yaml`. That logic was NEVER ported
  back into the canonical `tpsreport-skill/skills/tpsreport-skill/scripts/kb_lint.py` (25,324 B).
- Canonical skill source going forward = `tpsreport-skill/skills/tpsreport-skill/`.
- If you want the SEO-contract lint in canonical, port `kb_lint.py` + `metadata-contract.yaml` from here.
