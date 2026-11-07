# Hermes Best Skills

A curated list of the best **skills** for [Hermes Agent](https://hermes-agent.nousresearch.com) — the autonomous AI assistant.

This repo helps you get started fast: each skill solves a real problem, and they're all battle-tested.

---

## Table of Contents

- [What is a skill?](#what-is-a-skill)
- [How to install a skill](#how-to-install-a-skill)
- [Skills by category](#skills-by-category)
  - [Coding & Software Development](#coding--software-development)
  - [Autonomous AI Agents](#autonomous-ai-agents)
  - [Creative & Design](#creative--design)
  - [DevOps & Automation](#devops--automation)
  - [Email & Communication](#email--communication)
  - [GitHub & Open Source](#github--open-source)
  - [MLOps & AI/ML](#mlops--aiml)
  - [Productivity](#productivity)
  - [Research & Data](#research--data)
  - [Social Media](#social-media)
  - [Red Teaming](#red-teaming)
- [Essential skills to start](#essential-skills-to-start)
- [How to create your own skill](#how-to-create-your-own-skill)
- [Contributing](#contributing)

---

## What is a skill?

A **skill** in Hermes is a markdown document (SKILL.md) that teaches the agent how to do something specific. Think of it as "plug-and-play" for capabilities:

- You tell Hermes _"load the `plan` skill"_ and it automatically knows how to structure action plans.
- You say _"load `test-driven-development`"_ and it applies TDD without you explaining the RED-GREEN-REFACTOR cycle.

Skills live in `~/.hermes/skills/` and are loaded with `skill_view("skill-name")`.

---

## How to install a skill

```bash
# 1. Clone this repo
git clone https://github.com/josezuma/hermes-best-skills.git
cd hermes-best-skills

# 2. Copy the skills you want to your Hermes profile
cp skills/plan/SKILL.md ~/.hermes/skills/plan/

# 3. Or install from the built-in Hermes skill store
#    (if the skill is published)
hermes skills install plan
```

To load a skill in a session:

```python
skill_view("plan")                    # view content
skill_view("plan", file_path="references/api.md")  # view auxiliary file
```

---

## Skills by category

### Coding & Software Development

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [test-driven-development](skills/test-driven-development) | Enforces RED-GREEN-REFACTOR cycle. Writes tests before code. | Eliminates false positives. The agent can't claim "it works" without green tests. |
| [plan](skills/plan) | Writes actionable plans in markdown. Small tasks, exact paths, complete code. | Prevents the agent from coding without direction. Use it BEFORE writing code. |
| [systematic-debugging](skills/systematic-debugging) | 4-phase debugging: reproduce, isolate, understand, fix. | The agent doesn't guess. Follows a real forensic process. |
| [spike](skills/spike) | Throwaway experiments to validate an idea before building. | Saves hours building in the wrong direction. |
| [requesting-code-review](skills/requesting-code-review) | Automated pre-commit review: security scan, quality gates, auto-fix. | Catches bugs, secrets, and code smells before push. |
| [simplify-code](skills/simplify-code) | 3 parallel agents clean up recent code. | Safe refactoring. Each agent reviews the others' work. |
| [node-inspect-debugger](skills/node-inspect-debugger) | Debug Node.js via `--inspect` + Chrome DevTools Protocol. | When the stack trace isn't enough — inspect live variables. |
| [python-debugpy](skills/python-debugpy) | Debug Python with pdb REPL + remote debugpy (DAP). | Same but for Python. Remote breakpoints. |
| [codebase-inspection](skills/codebase-inspection) | Scans codebases with pygount: LOC, languages, ratios. | Know how much there really is before promising deadlines. |
| [hermes-agent-skill-authoring](skills/hermes-agent-skill-authoring) | SKILL.md authoring: frontmatter, validator, structure, quality principles. | For writing your OWN skills properly from the start. |

### Autonomous AI Agents

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [claude-code](skills/claude-code) | Delegates coding to Claude Code CLI (features, PRs). | When you need a second agent coding in parallel. |
| [codex](skills/codex) | Delegates coding to OpenAI Codex CLI (features, PRs). | Same with OpenAI's Codex. |
| [opencode](skills/opencode) | Delegates coding to OpenCode CLI (features, PR review). | Open-source alternative for delegation. |
| [hermes-agent](skills/hermes-agent) | Configure, extend, or contribute to Hermes Agent. | The skill about Hermes itself — config, CLI, plugins, providers. |
| [kanban-orchestrator](skills/kanban-orchestrator) | Task decomposition + anti-temptation rules for the orchestrator role. | Orchestrate work without doing it yourself. |
| [kanban-worker](skills/kanban-worker) | Pitfalls, examples, edge cases for Kanban workers. | When executing tasks inside a Kanban flow. |

### Creative & Design

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [feature-ux-architect](skills/feature-ux-architect) | Inspects existing routes, navigation, roles, and workflows before placing or designing a new feature. | Keeps new UI intuitive for beginners without unnecessary pages or menus. |
| [sketch](skills/sketch) | Throwaway HTML mockups: 2-3 design variants to compare. | Validate visual design in 5 minutes, not 2 hours. |
| [claude-design](skills/claude-design) | Design unique HTML artifacts (landing, deck, prototype). | A single page with premium design, no framework. |
| [architecture-diagram](skills/architecture-diagram) | Dark-mode SVG architecture/infra diagrams as HTML. | Technical documentation that looks great in docs. |
| [excalidraw](skills/excalidraw) | Hand-drawn JSON diagrams (architecture, flow, sequence). | For sharing in PRs or informal docs. |
| [popular-web-designs](skills/popular-web-designs) | 54 real design systems (Stripe, Linear, Vercel) as HTML/CSS. | Direct inspiration from the best. |
| [p5js](skills/p5js) | p5.js sketches: gen art, shaders, interactive, 3D. | Creative visualizations and interactive demos. |
| [ascii-art](skills/ascii-art) | ASCII art: pyfiglet, cowsay, boxes, image-to-ascii. | Banners, headers for CLI, terminal decoration. |
| [ascii-video](skills/ascii-video) | Colored animated ASCII from video/audio (MP4/GIF). | Retro demos in the terminal. |
| [manim-video](skills/manim-video) | Manim CE animations: 3Blue1Brown-style videos. | High-impact mathematical/algorithmic explanations. |
| [comfyui](skills/comfyui) | Generate images, video, audio with ComfyUI. | Visual pipelines for Stable Diffusion, ControlNet, etc. |
| [touchdesigner-mcp](skills/touchdesigner-mcp) | Control TouchDesigner via MCP — 36 native tools. | Real-time visuals from the agent. |
| [songwriting-and-ai-music](skills/songwriting-and-ai-music) | Music composition + Suno AI prompts. | Generate songs from lyrics + tags. |
| [heartmula](skills/heartmula) | HeartMuLa: Suno-style song generation. | Suno alternative from CLI. |
| [pretext](skills/pretext) | DOM-less text layout for ASCII art, typography games, gen art. | Creative demos with @chenglou/pretext. |

### DevOps & Automation

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [watchers](skills/watchers) | Polls RSS, JSON APIs, and GitHub with watermark dedup. | Monitor changes without external infrastructure. |
| [kanban-orchestrator](skills/kanban-orchestrator) | Task decomposition with Kanban workflow. | Project management inside the agent. |
| [kanban-worker](skills/kanban-worker) | Kanban task execution with documented pitfalls. | For workers executing assigned tasks. |

### Email & Communication

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [agentmail](skills/agentmail) | Gives the agent its own email inbox (agent@agentmail.to). | The agent can send and receive emails autonomously. |
| [himalaya](skills/himalaya) | IMAP/SMTP client from the terminal. | For traditional email accounts (Gmail, Migadu, etc.). |
| [one-three-one-rule](skills/one-three-one-rule) | Structured decision framework: 1 problem → 3 options → 1 recommendation. | When choosing between technical paths. |

### GitHub & Open Source

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [github-auth](skills/github-auth) | Auth setup: HTTPS tokens, SSH keys, gh CLI login. | The first thing you need for any GitHub operation. |
| [github-pr-workflow](skills/github-pr-workflow) | Complete lifecycle: branch, commit, open PR, CI, merge. | Without this skill the agent doesn't know the correct order. |
| [github-code-review](skills/github-code-review) | Review PRs: diffs, inline comments via gh or REST API. | Review code without leaving the terminal. |
| [github-issues](skills/github-issues) | Create, triage, label, assign issues. | Issue management from the agent. |
| [github-repo-management](skills/github-repo-management) | Clone, create, fork repos; manage remotes, releases. | Repo operations that aren't PRs or issues. |

### MLOps & AI/ML

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [llama-cpp](skills/llama-cpp) | Local GGUF inference + HF Hub model discovery. | Run LLMs locally without a GPU. |
| [serving-llms-vllm](skills/serving-llms-vllm) | vLLM serving: high throughput, OpenAI API, quantization. | Production: serve models with OpenAI-compatible API. |
| [huggingface-hub](skills/huggingface-hub) | HuggingFace CLI: search, download, upload models and datasets. | Full access to the HF ecosystem. |
| [evaluating-llms-harness](skills/evaluating-llms-harness) | Benchmarking with lm-eval-harness (MMLU, GSM8K, etc.). | Measure real model performance. |
| [weights-and-biases](skills/weights-and-biases) | Experiment logging, sweeps, model registry, dashboards. | ML experiment tracking. |
| [obliteratus](skills/obliteratus) | LLM abliteration: remove refusal patterns (diff-in-means). | For fine-tuning models without artificial restrictions. |
| [audiocraft-audio-generation](skills/audiocraft-audio-generation) | MusicGen text-to-music, AudioGen text-to-sound. | Audio generation from text. |
| [segment-anything-model](skills/segment-anything-model) | SAM: zero-shot image segmentation by points, boxes, masks. | Image segmentation without training. |

### Productivity

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [obsidian](skills/obsidian) | Read, search, create, edit notes in your Obsidian vault. | The agent can read/write your personal knowledge base. |
| [notion](skills/notion) | Notion API + ntn CLI: pages, databases, markdown, Workers. | Direct Notion integration. |
| [airtable](skills/airtable) | Airtable REST API via curl: CRUD, filters, upserts. | Manage visual databases from the agent. |
| [google-workspace](skills/google-workspace) | Gmail, Calendar, Drive, Docs, Sheets via CLI. | Full Google Workspace access. |
| [powerpoint](skills/powerpoint) | Create, read, edit .pptx presentations. | Auto-generate slide decks. |
| [nano-pdf](skills/nano-pdf) | Edit text/typos/titles in PDFs via CLI (natural language). | Quick PDF fixes without heavy tools. |
| [ocr-and-documents](skills/ocr-and-documents) | Extract text from PDFs/scans with pymupdf, marker-pdf. | Digitize scanned documents. |
| [maps](skills/maps) | Geocoding, POIs, routes, timezones via OpenStreetMap/OSRM. | Geographic info without an API key. |
| [petdex](skills/petdex) | Install and select animated mascots for Hermes. | Visual agent personalization. |
| [teams-meeting-pipeline](skills/teams-meeting-pipeline) | Teams meeting summary pipeline via CLI. | Auto-summarize meetings. |

### Research & Data

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [arxiv](skills/arxiv) | Search papers by keyword, author, category, or ID. | Direct access to academic literature. |
| [blogwatcher](skills/blogwatcher) | Monitor blogs and RSS/Atom feeds via CLI. | Content tracking without social media. |
| [llm-wiki](skills/llm-wiki) | Interlinked markdown knowledge base. | Build and query knowledge wikis. |
| [polymarket](skills/polymarket) | Query Polymarket: markets, prices, orderbooks, history. | Prediction market information. |
| [scrapling](skills/scrapling) | Web scraping: HTTP, browser stealth, Cloudflare bypass, crawling. | Extract data from protected websites. |
| [research-paper-writing](skills/research-paper-writing) | Write ML papers for NeurIPS/ICML/ICLR. | Academic publishing from the agent. |
| [jupyter-live-kernel](skills/jupyter-live-kernel) | Interactive Python via live Jupyter kernel (hamelnb). | Iterative data exploration. |
| [youtube-content](skills/youtube-content) | YouTube transcripts to summaries, threads, blogs. | Convert videos into written content. |

### Social Media

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [xurl](skills/xurl) | X/Twitter via CLI: post, search, DM, media, v2 API. | Manage Twitter/X from terminal. |
| [gif-search](skills/gif-search) | Search/download GIFs from Tenor via curl + jq. | Quick visual responses. |

### Red Teaming

| Skill | What it does | Why use it |
|-------|----------|----------------|
| [godmode](skills/godmode) | Jailbreak techniques: Parseltongue, GODMODE, ULTRAPLINIAN. | For LLM security testing. |

---

## Essential skills to start

If you're new to Hermes, install these 5 first:

```
# 1. Plan before coding
hermes skills install plan

# 2. Don't code without tests
hermes skills install test-driven-development

# 3. Debug systematically
hermes skills install systematic-debugging

# 4. GitHub without process errors
hermes skills install github-pr-workflow

# 5. Structured decisions
hermes skills install one-three-one-rule
```

With these 5 skills you cover 80% of daily problems: planning, quality coding, debugging, publishing, and decision-making.

---

## How to create your own skill

Use the `hermes-agent-skill-authoring` skill that guides you through:

1. **Required frontmatter**: `name`, `description`, `category`
2. **Structure**: trigger conditions, numbered steps, verification
3. **Pitfalls**: common mistakes we already know about
4. **Dual mode**: instructions for CLI + for autonomous agents

```bash
# Create a new skill
skill_manage(action='create', name='my-skill', content=...) 

# View the validator
skill_view('hermes-agent-skill-authoring')
```

Golden rules:
- Minimum 2000 characters of useful content
- Each step must be executable, not descriptive
- Include a verification section (how do I know it worked?)
- Document pitfalls so others don't waste time

---

## Contributing

1. Fork the repo
2. Add your skill in `skills/<name>/SKILL.md`
3. Update the README with the entry in the corresponding table
4. Open a PR

**Acceptance criteria:**
- SKILL.md with valid frontmatter
- Minimum 2000 characters of content
- Clear trigger conditions
- Executable numbered steps
- Verification section
- Documented pitfalls if applicable

---

## License

MIT — do whatever you want with this.

---

_Created by [José Zuma](https://github.com/josezuma) for the Hermes Agent community._
