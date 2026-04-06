# ⚔️ VikingBay Skill Pack

> **One namespace. One driver. Maximum power.**

A lean, opinionated personal skill OS for Claude Code. Everything is `/vikingbay-XXXX`. No duplicates, no dead weight.

## Quick Start

```bash
# Claude Code plugin
/plugin marketplace add https://github.com/salli94/vikingbay
/plugin install vikingbay
```

### Your First Build

```
/vikingbay-ship "Build a REST API for a book inventory system with PostgreSQL and real-time sync"
```

---

## The 15 Skills

| Skill | Invoke | What it does |
|-------|--------|-------------|
| **vikingbay-brain** | `/vikingbay-brain` | Session OS — reads context, routes prompts to right skill, saves state before compact |
| **vikingbay-build** | `/vikingbay-build` | Build/test/lint loop until green. Orchestrate mode for long multi-phase builds |
| **vikingbay-fix** | `/vikingbay-fix` | Triage-and-fix: bugs, type errors, safe refactors — classified, minimal, verified |
| **vikingbay-fullstack** | `/vikingbay-fullstack` | Full vertical slice: DB → API → types → frontend, all connected |
| **vikingbay-ship** | `/vikingbay-ship` | Spec to PR: plan → build story-by-story → test green → create PR |
| **vikingbay-ui** | `/vikingbay-ui` | Advanced UI/UX: shadcn/ui MCP, Iconify, Figma MCP, Motion, design tokens |
| **vikingbay-ops** | `/vikingbay-ops` | Deploy: Vercel + Fly.io + Supabase. Railway permanently banned. Migration safety gates |
| **vikingbay-api** | `/vikingbay-api` | Scaffold complete API endpoint: route, handler, validation, types, test |
| **vikingbay-test** | `/vikingbay-test` | Write comprehensive tests — reads implementation, finds real edge cases |
| **vikingbay-god-mode** | `/vikingbay-god-mode` | GEMINI → GROK-3 → DeepSeek-R1 → GROK-3 consensus pipeline. Max-power on any topic |
| **vikingbay-prompt** | `/vikingbay-prompt` | Prompt refinement: HERMOD routes → agents debate → majority vote → auto-executes |
| **vikingbay-research** | `/vikingbay-research` | Deep dive: 3 parallel search agents + expert council → single compiled output (DEEPDIVE) |
| **vikingbay-skill** | `/vikingbay-skill` | Skill factory: scouts + council → writes production-ready SKILL.md (MAXSKILL) |
| **vikingbay-oss** | `/vikingbay-oss` | OSS-first: find best existing project before building anything new |
| **vikingbay-unified** | (this file) | The pack overview and install guide |

---

## Slash Commands

| Command | Purpose |
|---------|---------|
| `/vikingbay-brain` | Start session, load context, route |
| `/vikingbay-build` | Build/test/lint loop |
| `/vikingbay-fix` | Fix a bug or type error |
| `/vikingbay-ship` | Spec to PR end-to-end |
| `/vikingbay-god-mode` | Multi-model swarm on anything |
| `/vikingbay-fullstack` | Full-stack feature slice |
| `/vikingbay-sync` | Sync buildstate.md with reality |
| `/vikingbay-get-better` | Extract mistakes into reusable rules |
| `/vikingbay-update` | Weekly skill pack update |

---

## God Mode

```
/vikingbay-god-mode "What is the best architecture for a real-time multiplayer game in 2026?"
```
Runs GEMINI → GROK-3 (DeepSearch) → DeepSeek-R1 → GROK-3 (synthesis).
Each stage passes structured JSON. Claude orchestrates — never participates in content.

```
/vikingbay-god-mode --brainstorm "Should we build this feature or find an OSS alternative?"
```
Brainstorm mode: Futurist (Gemini) + Pragmatist (Grok) + Iconoclast (DeepSeek) + Judge (Grok) — 3 debate rounds, RA-CR consensus, explicit verdict.

---

## Platform Rules

- Stack: **Vercel** (frontend) + **Fly.io** (backend) + **Supabase** (database)
- **Railway is permanently banned** — blocked at hook level, not just reasoning
- Supabase: REST API only, migrations committed to git before applying
- Fly.io: blue-green deploys, fly status gate before session end

---

## Architecture

Skills live at `~/.claude/skills/vikingbay-XXXX/SKILL.md`.  
Commands live at `~/.claude/commands/vikingbay-XXXX.md`.  
State lives at `.claude/state/buildstate.md` (per project).  
God-mode temp state: `.claude/god-mode-state.json`.

---

## License

MIT — Do whatever you want.

⚔️ *One namespace. One driver. No duplicates.*
