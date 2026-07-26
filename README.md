# TPSReport Skill — moved

> **This repo is retired.** The skill now lives in the Augmentable.ai skills hub,
> together with the renderer and everything else:
>
> ### 👉 [github.com/augmentableai/skills](https://github.com/augmentableai/skills)

[![TPSReport](https://img.shields.io/badge/TPSReport-tpsreport.pro-2563eb?style=flat-square)](https://tpsreport.pro)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

## What changed

`tpsreport-skill` is now **`tpsreport-author`**, published from the hub. Same skill,
clearer name, and it no longer lives in three places under three names.

```bash
# new
npx skills add augmentableai/skills --skill tpsreport-author -y

# and the renderer that ships alongside it
npx skills add augmentableai/skills --skill vault-viewer -y
```

Prefer no install at all? Connect the
[TPSReport MCP server](https://github.com/augmentableai/tpsreport-mcp) — it serves
these same skill packages on demand (`get_skill`), plus a server-side validator.

## The TPSReport stack

| # | Piece | Role |
|---|---|---|
| 1 | [`augmentableai/skills`](https://github.com/augmentableai/skills) | **Author** — authoring + linting + rendering skills |
| 2 | [`tpsreport-obsidian-sync`](https://github.com/augmentableai/tpsreport-obsidian-sync) | **Sync** — Obsidian plugin, vault ↔ cloud |
| 3 | [`tpsreport-mcp`](https://github.com/augmentableai/tpsreport-mcp) | **Operate** — MCP server: serves the skills + recall/remember |

## `archive/`

Kept for history only — a superseded variant of the skill package. Do not use it;
the hub is the source of truth.

## License

MIT · Copyright (c) Augmentable.ai
