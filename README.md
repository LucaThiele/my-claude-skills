# my-claude-skills

A personal collection of 27 [Claude Code](https://docs.claude.com/en/docs/claude-code) skills used across my work and personal Macs. Drawn from Anthropic's official skill bundle, the n8n-mcp companion skills, and one third-party skill.

## Sources

| Source | Count | Notes |
|---|---|---|
| **Anthropic** | 19 | Anthropic's official skills (Office docs, design, web, dev workflow, writing, product) |
| **n8n-mcp project** | 7 | Companion skills bundled with [czlonkowski/n8n-mcp](https://github.com/czlonkowski/n8n-mcp) for n8n workflow automation |
| **Third-party** | 1 | `nano-banana` from [kkoppenhaver/cc-nano-banana](https://github.com/kkoppenhaver/cc-nano-banana) for image generation via Gemini CLI |

## Installation

Each top-level folder is a skill. Copy whichever folders you want into `~/.claude/skills/` on your machine, then restart Claude Code.

Install all of them:
```bash
git clone https://github.com/LucaThiele/my-claude-skills.git ~/.claude/skills
```

Or merge into an existing skills directory:
```bash
git clone https://github.com/LucaThiele/my-claude-skills.git /tmp/my-skills
rsync -a --exclude='.git' --exclude='README.md' /tmp/my-skills/ ~/.claude/skills/
```

### External dependencies

Some skills require extra tools installed on the host machine:

- **nano-banana** — needs the Gemini CLI: `brew install gemini-cli`
- **n8n-* skills** — most useful when paired with the [n8n MCP server](https://github.com/czlonkowski/n8n-mcp): `claude mcp add --scope user n8n -- npx -y n8n-mcp`
- **webapp-testing** — needs the Playwright MCP server
- **commit-push-pr** — needs the GitHub CLI (`gh`)

## Skills overview

### Documents & spreadsheets
| Skill | What it does |
|---|---|
| `pdf` | Read, edit, merge, split, fill, encrypt, and OCR PDF files |
| `docx` | Create, read, edit Word documents (.docx) — TOC, headings, tables, tracked changes |
| `pptx` | Create, read, edit PowerPoint decks (.pptx) — slides, layouts, speaker notes |
| `xlsx` | Create, read, edit Excel/CSV/TSV spreadsheets — formulas, charts, formatting |

### Design & creative
| Skill | What it does |
|---|---|
| `algorithmic-art` | Generative art with p5.js (flow fields, particle systems, seeded randomness) |
| `brand-guidelines` | Apply Anthropic's brand colors and typography to artifacts |
| `canvas-design` | Create posters and visual designs as PNG/PDF |
| `theme-factory` | Apply preset themes (10 included) to slides, docs, HTML, or generate new ones |
| `slack-gif-creator` | Animated GIFs optimized for Slack (size constraints, validation tools) |
| `nano-banana` | Image generation and editing via Gemini CLI (Nano Banana) |
| `frontend-design` | Production-grade frontend components and pages with strong design quality |

### Web & artifacts
| Skill | What it does |
|---|---|
| `web-artifacts-builder` | Multi-component React/Tailwind/shadcn artifacts for claude.ai |
| `webapp-testing` | Test local web apps via Playwright — browser interaction, screenshots, logs |

### Development
| Skill | What it does |
|---|---|
| `claude-api` | Build, debug, and optimize Claude API + Anthropic SDK apps; helps with model migrations |
| `mcp-builder` | Build MCP servers in Python (FastMCP) or Node/TypeScript (MCP SDK) |
| `skill-creator` | Create, edit, and benchmark Claude Code skills |
| `commit-push-pr` | One-step: commit changes → push → open a PR |

### Writing & product
| Skill | What it does |
|---|---|
| `doc-coauthoring` | Structured workflow for co-authoring docs, proposals, specs, decision docs |
| `interview-mode` | 4-round product discovery interview that produces a `spec.md` |
| `internal-comms` | Templates for status reports, leadership updates, FAQs, incident reports |

### n8n workflows
| Skill | What it does |
|---|---|
| `n8n-mcp-tools-expert` | Guide for using n8n-mcp tools effectively — consult before any n8n-mcp tool call |
| `n8n-workflow-patterns` | Proven architectural patterns: webhooks, APIs, AI agents, batch, scheduled |
| `n8n-node-configuration` | Operation-aware node config — required fields, displayOptions, surgical patches |
| `n8n-expression-syntax` | Validate and fix n8n `{{ }}` expressions, `$json` / `$node` references |
| `n8n-validation-expert` | Interpret validation errors/warnings; distinguish false positives from real fixes |
| `n8n-code-javascript` | JavaScript in n8n Code nodes — `$input` / `$json` / `$node`, helpers, dates, batching |
| `n8n-code-python` | Python in n8n Code nodes — use only when JS won't work |

---

*See each skill's `SKILL.md` for full descriptions and trigger criteria.*
