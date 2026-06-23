# TPSReport Skill

[![skills.sh](https://skills.sh/b/augmentableai/tpsreport-skill)](https://skills.sh/augmentableai/tpsreport-skill)
[![TPSReport](https://img.shields.io/badge/TPSReport-tpsreport.pro-2563eb?style=flat-square)](https://tpsreport.pro)
[![Obsidian plugin](https://img.shields.io/badge/Obsidian-Community%20Plugin-7c3aed?style=flat-square)](https://community.obsidian.md/plugins/tpsreport-sync)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

**TPSReport by [Augmentable.ai](https://augmentable.ai)** — official agent skill for [TPSReport](https://tpsreport.pro) + [Obsidian](https://obsidian.md) knowledge bases.

Build Graph RAG-ready KB folders, enrich YAML frontmatter, lint with `kb_lint.py`, and sync via the [TPSReport Obsidian plugin](https://community.obsidian.md/plugins/tpsreport-sync).

## Install

```bash
npx skills add augmentableai/tpsreport-skill -y
```

Repo layout (agentskill.sh expects `skills/{name}/SKILL.md`):

```text
skills/tpsreport-skill/
├── SKILL.md
├── scripts/kb_lint.py
└── references/
```

```bash
# Cursor (project)
cp -r skills/tpsreport-skill/ .cursor/skills/tpsreport-skill/
pip install pyyaml
```

## Validate a KB

```bash
python skills/tpsreport-skill/scripts/kb_lint.py /path/to/Your_KB/
```

## Also available in

[TPSReport Obsidian plugin repo](https://github.com/augmentableai/tpsreport-obsidian-sync) (bundled copy at `tpsreport-skill/`)

## Listings

| Directory | Link / command |
|-----------|----------------|
| **skills.sh** | [skills.sh/augmentableai/tpsreport-skill](https://skills.sh/augmentableai/tpsreport-skill) |
| **agentskill.sh** | [agentskill.sh/submit](https://agentskill.sh/submit) → `augmentableai/tpsreport-skill` |
| **Install** | `npx skills add augmentableai/tpsreport-skill -y` |

## Keywords

TPSReport · Augmentable.ai · Obsidian · knowledge base · Graph RAG · frontmatter · kb_lint · agent skill · tpsreport-sync

## License

MIT · Copyright (c) Augmentable.ai
