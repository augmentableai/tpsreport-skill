# TPSReport Skill

**Official agent skill for [TPSReport](https://tpsreport.pro) + [Obsidian](https://obsidian.md) knowledge bases.**

Build Graph RAG-ready KB folders, enrich YAML frontmatter, lint with `kb_lint.py`, and sync via the [TPSReport Obsidian plugin](https://community.obsidian.md/plugins/tpsreport-sync).

## Install

```bash
npx skills add augmentableai/tpsreport-skill -y
```

```bash
# Cursor (project)
cp -r . .cursor/skills/tpsreport-skill/
pip install pyyaml
```

## Validate a KB

```bash
python scripts/kb_lint.py /path/to/Your_KB/
```

## Also available in

[TPSReport Obsidian plugin repo](https://github.com/augmentableai/tpsreport-obsidian-sync) (bundled copy at `tpsreport-skill/`)

## Submit / list

| Directory | URL |
|-----------|-----|
| agentskill.sh | [agentskill.sh/submit](https://agentskill.sh/submit) → `augmentableai/tpsreport-skill` |
| skills.sh | `npx skills add augmentableai/tpsreport-skill -y` |

## Keywords

TPSReport · Obsidian · knowledge base · Graph RAG · frontmatter · kb_lint · agent skill · tpsreport-sync

## License

MIT
