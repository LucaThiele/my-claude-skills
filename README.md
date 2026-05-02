# my-claude-skills

A personal collection of [Claude Code](https://docs.claude.com/en/docs/claude-code) skills used across my work and personal Macs. 31 skills bundled in this repo, plus [gstack](https://github.com/garrytan/gstack) installed alongside as a separate toolchain.

## Naming convention

Skills are prefixed by source so I can always tell where each one comes from. The prefix is part of the slash command (e.g. `/anthropic-pdf`, not `/pdf`).

| Prefix | Source |
|---|---|
| `gstack-*` | [gstack](https://github.com/garrytan/gstack) — Garry Tan's opinionated skill bundle (45 commands), installed separately |
| `anthropic-*` | Anthropic's official skill bundle (Office docs, design, web, dev, writing) |
| `n8n-*` | Companion skills bundled with [czlonkowski/n8n-mcp](https://github.com/czlonkowski/n8n-mcp) — kept as-is since `n8n-` is already a natural namespace |
| `notion-*` | Notion's official skills from [makenotion/notion-cookbook](https://github.com/makenotion/notion-cookbook) — kept as-is since `notion-` is the upstream prefix |
| `community-*` | Third-party / community-maintained skills |
| *no prefix* | Skills I create myself (none yet) |

## Sources

| Source | Count | Where they live |
|---|---|---|
| Anthropic | 19 | This repo, `anthropic-*` folders |
| n8n-mcp project | 7 | This repo, `n8n-*` folders |
| Notion cookbook | 4 | This repo, `notion-*` folders |
| Third-party | 1 | This repo, `community-nano-banana` folder |
| gstack | 45 | Cloned separately from [garrytan/gstack](https://github.com/garrytan/gstack) |

## Installation

### This bundle (the 31 skills in this repo)

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
- **notion-* skills** — require the [Notion MCP server](https://www.notion.com/help/notion-mcp) connected via `/mcp` (OAuth). Without it the skills can't read or write your workspace.
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

### `notion-*` — Notion knowledge base
| Skill | What it does |
|---|---|
| `notion-knowledge-capture` | Turn a chat session into a structured Notion page (decisions, how-tos, FAQs) and link it from the right hub so it's discoverable |
| `notion-meeting-intelligence` | Build an internal pre-read + external agenda for a meeting — pulls Notion context, layers in research, links both to the project |
| `notion-research-documentation` | Cross-page research inside the workspace — synthesize findings from multiple Notion pages into a report with citations |
| `notion-spec-to-implementation` | Break a Notion spec page into a tracked plan + task rows with bidirectional links between spec, plan, and tasks |

### `gstack-*` — gstack toolchain (installed separately)

[gstack](https://github.com/garrytan/gstack) provides 45 specialized commands acting as virtual roles (CEO, eng manager, designer, reviewer, QA, security officer, release engineer). Grouped by purpose below.

#### Planning & strategy
| Skill | What it does |
|---|---|
| `gstack-office-hours` | YC-style brainstorming for new ideas — startup mode (6 forcing questions) or builder mode (design thinking) |
| `gstack-autoplan` | Run the full plan-review gauntlet (CEO + design + eng + DX) automatically with a final approval gate |
| `gstack-plan-ceo-review` | CEO/founder mode — challenge premises, expand or strip scope, find the 10-star product |
| `gstack-plan-eng-review` | Eng manager mode — lock in architecture, data flow, edge cases, test coverage |
| `gstack-plan-design-review` | Designer's eye on the plan — rate each design dimension 0–10 and fix toward 10 |
| `gstack-plan-devex-review` | Developer experience plan review — personas, competitive benchmarks, friction tracing |
| `gstack-plan-tune` | Tune AskUserQuestion sensitivity per skill; show declared vs. observed dev profile |

#### Design
| Skill | What it does |
|---|---|
| `gstack-design-consultation` | Build a design system from scratch — produces `DESIGN.md` as project source of truth |
| `gstack-design-shotgun` | Generate multiple AI design variants, comparison board, structured feedback |
| `gstack-design-html` | Finalize an approved design as production HTML/CSS (Pretext-native, dynamic layouts) |
| `gstack-design-review` | Live-site visual QA — finds inconsistency, AI slop, hierarchy issues, then fixes them |

#### Code review & quality
| Skill | What it does |
|---|---|
| `gstack-review` | Pre-landing PR review — SQL safety, LLM trust boundaries, structural issues |
| `gstack-investigate` | Root-cause debugging — investigate, analyze, hypothesize, implement (no fixes without RCA) |
| `gstack-codex` | OpenAI Codex CLI wrapper — independent review, adversarial challenge, or general consult |
| `gstack-health` | Code quality dashboard — wraps type checker, linter, tests, dead-code, shell linter into a 0–10 score |
| `gstack-cso` | Chief Security Officer mode — secrets, supply chain, CI/CD, LLM security, OWASP, STRIDE |
| `gstack-learn` | Manage persistent project learnings across sessions (search, prune, export) |

#### QA & testing
| Skill | What it does |
|---|---|
| `gstack-qa` | Systematically QA test a web app and fix bugs found (atomic commits, before/after evidence) |
| `gstack-qa-only` | Same as `qa` but report-only — no code changes |
| `gstack-devex-review` | Live developer experience audit — actually navigate docs, time TTHW, screenshot errors |
| `gstack-benchmark` | Page-performance regression detection — Core Web Vitals, bundle size, load time over time |
| `gstack-benchmark-models` | Cross-model benchmark — same prompt through Claude / GPT / Gemini, compare cost & quality |

#### Browser
| Skill | What it does |
|---|---|
| `gstack-browse` | Fast headless Chromium for QA, dogfooding, screenshots — ~100ms per command |
| `gstack-open-gstack-browser` | Launch a visible AI-controlled Chromium with sidebar extension and stealth |
| `gstack-scrape` | Pull data from a web page — prototypes flow, returns JSON |
| `gstack-skillify` | Codify a successful `/scrape` flow into a permanent reusable browser-skill |
| `gstack-pair-agent` | Pair a remote AI agent (OpenClaw, Cursor, Codex) with your browser via a setup key |
| `gstack-setup-browser-cookies` | Import cookies from your real Chromium into the headless browse session |

#### Shipping & release
| Skill | What it does |
|---|---|
| `gstack-ship` | Detect base branch, run tests, bump VERSION, update CHANGELOG, commit, push, open PR |
| `gstack-land-and-deploy` | Merge the PR, wait for CI + deploy, verify production via canary checks |
| `gstack-canary` | Post-deploy monitoring — console errors, perf regressions, anomaly alerts |
| `gstack-landing-report` | Read-only dashboard of open PRs and which VERSION slot `/ship` would claim next |
| `gstack-document-release` | Post-ship doc sync — README, ARCHITECTURE, CONTRIBUTING, CLAUDE.md, CHANGELOG |
| `gstack-retro` | Weekly engineering retrospective with trend tracking and per-person breakdowns |
| `gstack-make-pdf` | Markdown → publication-quality PDF (margins, page numbers, TOC, cover page) |

#### Safety & session state
| Skill | What it does |
|---|---|
| `gstack-careful` | Warn before destructive commands (`rm -rf`, `DROP TABLE`, force-push, `git reset --hard`) |
| `gstack-freeze` | Restrict file edits to one directory for the session |
| `gstack-unfreeze` | Lift the freeze boundary set by `gstack-freeze` |
| `gstack-guard` | Combined safety mode — `careful` + `freeze` together |
| `gstack-context-save` | Save working context (git state, decisions, remaining work) for later resume |
| `gstack-context-restore` | Restore the most recent context saved by `gstack-context-save` |

#### Setup & maintenance
| Skill | What it does |
|---|---|
| `gstack-setup-deploy` | Auto-detect deploy platform (Fly, Render, Vercel, etc.) and write config to CLAUDE.md |
| `gstack-setup-gbrain` | Install the gbrain CLI, init local PGLite or Supabase brain, register MCP |
| `gstack-upgrade` | Pull latest gstack, rebuild binaries, relink skills, show what's new |

---

*Each skill has a `SKILL.md` with full description and trigger criteria. Browse the folders for details.*
