# ⚔️ VikingBay

> **The Ultimate Average Vibe-Coder Essentials + Universal All-Around Skillpack for ANYONE Using Claude**

An all-in-one orchestration system for Claude Code that merges the best of alltaf's proven patterns with oh-my-claudecode's multi-agent execution. Works for solo hackers, teams, and everything in between.

## What is VikingBay?

VikingBay is a unified skill pack that turns Claude Code into a fully-orchestrated AI development system. No gatekeeping. No "you must be advanced." Just solid, battle-tested patterns.

**Status:** Production-ready (merged from 5+ years of alltaf experience + oh-my-claudecode's 15.8K stars)
**License:** MIT (do whatever you want)
**Installation:** Plugin marketplace or npm

## Core Features

### 🎯 Five Execution Modes

| Mode | Use Case | Speed |
|------|----------|-------|
| **ragnarok** | "I have an idea, make it work" — full autonomous execution | ⚡ Fast |
| **valholl** | "This MUST be done 100% verified" — persistence loop until victory | 🛡️ Safe |
| **bifrost** | "Build these 6 things in parallel" — multi-agent parallel execution | 🚀 Fastest |
| **einherjar** | "Coordinate multiple specialists" — native Claude Code teams | 👥 Teams |
| **the-council** | "Get consensus before building" — planner + architect + critic debate | 🤔 Careful |

### 🏛️ 19+ Specialized Agents

**Build Lane:** explore, analyst, planner, architect, debugger, executor, verifier, tracer
**Review Lane:** security-reviewer, code-reviewer
**Specialists:** test-engineer, designer, writer, qa-tester, scientist, git-master, document-specialist, code-simplifier, critic

### ⚙️ Alltaf Core (Icelandic Battle-Tested)

- `alltaf-build-loop` — Fix-verify loop until green
- `alltaf-klara-byggja` — Strategic orchestration (the operating system)
- `alltaf-fullstack-advance` — Vertical slice feature building
- `alltaf-platform-ops` — Railway/Render/Supabase operations
- `alltaf-ui-ux` — Advanced interface & experience patterns
- Plus 4 memory/state management skills

### 🛡️ Heimdall Guardian System

**Interactive Mode:**
```bash
/VikingBay:heimdall "I want to build X"
```
Searches for existing open-source projects, presents findings, lets you decide whether to clone or build.

**Guardian Mode (Session-Start):**
- Configurable: Always ask | New projects only | Never | Manual only
- Prevents wheel-reinvention automatically
- Zero friction if you want it off

### 📝 Utilities

- **orlog** — Consult multiple AI oracles (Claude + Gemini + DeepSeek)
- **skalds-chronicle** — Execution timeline & session history
- **runes-of-wisdom** — Extract reusable patterns from sessions
- **valhalla-reset** — Stop any active mode

## Installation

### Claude Code Plugin (Recommended)
```bash
/plugin marketplace add https://github.com/salli94/vikingbay
/plugin install vikingbay
/VikingBay:setup
```

### npm (Global CLI)
```bash
npm install -g @salli94/vikingbay
vikingbay setup
```

Then restart Claude Code. All modes are available immediately.

## Quick Start

### Build Something Autonomously
```
/VikingBay:ragnarok
"Build me a REST API for managing a personal library with PostgreSQL"
```

**What happens:**
1. Analyst clarifies requirements
2. Architect designs the system
3. Executor builds it (parallel tasks)
4. QA cycles iteratively (up to 5 rounds)
5. Full review (security, code quality, architecture)
6. Auto-cleanup when done

### Build With Verification
```
/VikingBay:valholl
"Refactor the auth module to use JWT tokens"
```

**What happens:**
- Generates a PRD with testable acceptance criteria
- Builds story-by-story
- Mandatory reviewer approval before completion
- Auto-cleanup with regression testing
- Won't say "done" until 100% verified

### Build in Parallel
```
/VikingBay:bifrost
- Refactor database models (executor 1)
- Add new API endpoints (executor 2)
- Update frontend components (executor 3)
```

Runs all 3 in parallel. Smart model routing decides haiku vs. sonnet vs. opus per task.

### Use the Guardian (oss-check)
```
/VikingBay:heimdall
"I want to build a video editor with real-time collaboration"
```

Returns: "Found 12 existing projects. #1 match: OBS Studio + Collab fork (4.2K stars, MIT, maintained). Clone and add your feature, or build from scratch?"

## Configuration

Create `~/.claude/vikingbay-config.json`:

```json
{
  "heimdall": {
    "mode": "new-projects-only",
    "auto-search": true,
    "present-findings": true,
    "block-until-decision": false
  },
  "execution": {
    "max-iterations": 10,
    "max-qa-cycles": 5,
    "max-validation-rounds": 3,
    "preferred-model": "opus"
  },
  "state-dir": ".omc"
}
```

## Documentation

- **[MODES.md](./docs/MODES.md)** — Deep dive into each execution mode
- **[AGENTS.md](./docs/AGENTS.md)** — Agent catalog and specializations
- **[ALLTAF.md](./docs/ALLTAF.md)** — Alltaf skill reference
- **[SETUP.md](./docs/SETUP.md)** — Installation and troubleshooting
- **[PATTERNS.md](./docs/PATTERNS.md)** — Reusable code & workflow patterns

## Philosophy

**For anyone.** VikingBay doesn't require you to be a Claude Code expert. It works for:
- Indie hackers building solo projects
- Teams coordinating on shared tasks
- Large codebases with complex refactors
- First-time Claude Code users
- Seasoned engineers who want superpowers

**One fixed price metaphor.** Like a marketplace where you get all the tools for one subscription instead of dozens. You install VikingBay once, get access to everything.

**Battle-tested.** Alltaf skills have powered production projects for 5+ years. OMC agents have 15.8K GitHub stars. This is proven, working code.

## License

MIT — Do whatever you want. Fork it, sell it, embed it, modify it. Zero restrictions.

## Support

- **Issues:** [GitHub Issues](https://github.com/salli94/vikingbay/issues)
- **Discussions:** [GitHub Discussions](https://github.com/salli94/vikingbay/discussions)
- **Sponsor:** [GitHub Sponsors](https://github.com/sponsors/salli94)

## Credits

**Alltaf Foundation:** 5+ years of battle-tested patterns by runar
**OMC Inspiration:** oh-my-claudecode's 15.8K star multi-agent system by Yeachan-Heo
**Merged & Unified:** VikingBay v1.0

---

**Built for the average vibe-coder who wants superpowers.**

⚔️ *May your builds be swift, your tests be green, and your refactors be safe.* ⚔️
