# my-claude-skills

A personal collection of [Claude Code](https://docs.claude.com/en/docs/claude-code) skills used across my work and personal Macs. 27 skills bundled in this repo, plus [gstack](https://github.com/garrytan/gstack) installed alongside as a separate toolchain.

## Naming convention

Skills are prefixed by source so I can always tell where each one comes from. The prefix is part of the slash command (e.g. `/anthropic-pdf`, not `/pdf`).

| Prefix | Source |
|---|---|
| `gstack-*` | [gstack](https://github.com/garrytan/gstack) — Garry Tan's opinionated skill bundle (45 commands), installed separately |
| `anthropic-*` | Anthropic's official skill bundle (Office docs, design, web, dev, writing) |
| `n8n-*` | Companion skills bundled with [czlonkowski/n8n-mcp](https://github.com/czlonkowski/n8n-mcp) — kept as-is since `n8n-` is already a natural namespace |
| `community-*` | Third-party / community-maintained skills |
| *no prefix* | Skills I create myself (none yet) |

## Sources

| Source | Count | Where they live |
|---|---|---|
| Anthropic | 19 | This repo, `anthropic-*` folders |
| n8n-mcp project | 7 | This repo, `n8n-*` folders |
| Third-party | 1 | This repo, `community-nano-banana` folder |
| gstack | 45 | Cloned separately from [garrytan/gstack](https://github.com/garrytan/gstack) |

## Installation

### This bundle (the 27 skills in this repo)

```bash
git clone https://github.com/LucaThiele/my-claude-skills.git /tmp/my-skills
rsync -a --exclude='.git' --exclude='README.md' /tmp/my-skills/ ~/.claude/skills/
rm -rf /tmp/my-skills
```

Restart Claude Code to pick up the skills.

### gstack (separately)

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup --prefix
```

`--prefix` namespaces all gstack commands as `gstack-*` (otherwise they'd be flat names like `/qa`, `/review`, etc., which clash less cleanly with the rest of the bundle).

### External dependencies

Some skills require extra tools installed on the host machine:

- **community-nano-banana** — needs the Gemini CLI: `brew install gemini-cli`
- **n8n-* skills** — most useful when paired with the [n8n MCP server](https://github.com/czlonkowski/n8n-mcp): `claude mcp add --scope user n8n -- npx -y n8n-mcp`
- **anthropic-webapp-testing** — needs the Playwright MCP server
- **anthropic-commit-push-pr** — needs the GitHub CLI (`gh`)
- **gstack** — needs Bun (`brew install oven-sh/bun/bun`); setup also auto-installs Playwright Chromium and coreutils

## Skills overview

### `anthropic-*` — Documents & spreadsheets
| Skill | What it does |
|---|---|
| `anthropic-pdf` | Read, edit, merge, split, fill, encrypt, and OCR PDF files |
| `anthropic-docx` | Create, read, edit Word documents (.docx) — TOC, headings, tables, tracked changes |
| `anthropic-pptx` | Create, read, edit PowerPoint decks (.pptx) — slides, layouts, speaker notes |
| `anthropic-xlsx` | Create, read, edit Excel/CSV/TSV spreadsheets — formulas, charts, formatting |

### `anthropic-*` — Design & creative
| Skill | What it does |
|---|---|
| `anthropic-algorithmic-art` | Generative art with p5.js (flow fields, particle systems, seeded randomness) |
| `anthropic-brand-guidelines` | Apply Anthropic's brand colors and typography to artifacts |
| `anthropic-canvas-design` | Create posters and visual designs as PNG/PDF |
| `anthropic-theme-factory` | Apply preset themes (10 included) to slides, docs, HTML, or generate new ones |
| `anthropic-slack-gif-creator` | Animated GIFs optimized for Slack (size constraints, validation tools) |
| `anthropic-frontend-design` | Production-grade frontend components and pages with strong design quality |
| `community-nano-banana` | Image generation and editing via Gemini CLI (Nano Banana) |

### `anthropic-*` — Web & artifacts
| Skill | What it does |
|---|---|
| `anthropic-web-artifacts-builder` | Multi-component React/Tailwind/shadcn artifacts for claude.ai |
| `anthropic-webapp-testing` | Test local web apps via Playwright — browser interaction, screenshots, logs |

### `anthropic-*` — Development
| Skill | What it does |
|---|---|
| `anthropic-claude-api` | Build, debug, and optimize Claude API + Anthropic SDK apps; helps with model migrations |
| `anthropic-mcp-builder` | Build MCP servers in Python (FastMCP) or Node/TypeScript (MCP SDK) |
| `anthropic-skill-creator` | Create, edit, and benchmark Claude Code skills |
| `anthropic-commit-push-pr` | One-step: commit changes → push → open a PR |

### `anthropic-*` — Writing & product
| Skill | What it does |
|---|---|
| `anthropic-doc-coauthoring` | Structured workflow for co-authoring docs, proposals, specs, decision docs |
| `anthropic-interview-mode` | 4-round product discovery interview that produces a `spec.md` |
| `anthropic-internal-comms` | Templates for status reports, leadership updates, FAQs, incident reports |

### `n8n-*` — n8n workflow automation
| Skill | What it does |
|---|---|
| `n8n-mcp-tools-expert` | Guide for using n8n-mcp tools effectively — consult before any n8n-mcp tool call |
| `n8n-workflow-patterns` | Proven architectural patterns: webhooks, APIs, AI agents, batch, scheduled |
| `n8n-node-configuration` | Operation-aware node config — required fields, displayOptions, surgical patches |
| `n8n-expression-syntax` | Validate and fix n8n `{{ }}` expressions, `$json` / `$node` references |
| `n8n-validation-expert` | Interpret validation errors/warnings; distinguish false positives from real fixes |
| `n8n-code-javascript` | JavaScript in n8n Code nodes — `$input` / `$json` / `$node`, helpers, dates, batching |
| `n8n-code-python` | Python in n8n Code nodes — use only when JS won't work |

### `gstack-*` — gstack toolchain (installed separately)

[gstack](https://github.com/garrytan/gstack) provides 45 specialized commands acting as virtual roles (CEO, eng manager, designer, reviewer, QA, security officer, release engineer). Highlights:

| Skill | What it does |
|---|---|
| `gstack-office-hours` | Discuss what to build (CEO/PM mode) |
| `gstack-autoplan` | Auto-generate an implementation plan from a description |
| `gstack-plan-ceo-review` | Review a plan from a CEO/product perspective |
| `gstack-plan-eng-review` | Review a plan from an engineering-architecture perspective |
| `gstack-review` | Review code changes on the current branch |
| `gstack-cso` | Security audit (OWASP Top 10 + STRIDE) |
| `gstack-investigate` | Root-cause analysis on a bug or unknown behavior |
| `gstack-qa` | QA test a live URL in a real browser |
| `gstack-ship` | Commit + push + open PR |
| `gstack-document-release` | Generate release docs |
| `gstack-retro` | Retrospective on a project |
| `gstack-browse` | Drive a real Chrome browser via gstack's compiled binary |
| `gstack-upgrade` | Pull latest gstack, rebuild binaries, relink skills |

Full list: see the [gstack README](https://github.com/garrytan/gstack).

---

*Each skill has a `SKILL.md` with full description and trigger criteria. Browse the folders for details.*
