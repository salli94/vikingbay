# ⚔️ VikingBay: The Ultimate All-In-One Claude Code Skill Pack

> **The Ultimate Vibe-Coder Essentials + Universal All-Around Skillpack for ANYONE Using Claude**

A unified orchestration system that merges vikingbay's battle-tested patterns with oh-my-claudecode's multi-agent execution.

## Quick Start

### Installation

```bash
# Claude Code plugin (recommended)
/plugin marketplace add https://github.com/salli94/vikingbay
/plugin install vikingbay
/VikingBay:setup

# or npm
npm install -g @salli94/vikingbay
vikingbay setup
```

### Your First Build

```
/VikingBay:ragnarok
"Build me a REST API for a book inventory system with PostgreSQL and real-time sync"
```

The system will:
1. Analyze requirements (analyst agent)
2. Design architecture (architect agent)
3. Build in parallel (executor agents)
4. Iterate QA (up to 5 cycles)
5. Full review (security, code quality, design)
6. Auto-cleanup

Done in ~30 minutes. All tested and verified.

## Five Execution Modes

### 🎯 **ragnarok** — Autonomous Full Build
"I have an idea, make it work"

Fully autonomous end-to-end execution:
- Requirements expansion
- Architecture planning
- Parallel implementation
- Iterative QA (up to 5 cycles)
- Multi-perspective validation
- Auto-cleanup

**Use when:** You have a clear idea and want hands-off execution.

### 🛡️ **valholl** — Persistence Loop with Verification
"This MUST be 100% done and verified"

Never stops until the task is complete:
- Generates PRD with testable acceptance criteria
- Builds story-by-story
- Mandatory reviewer approval (architect by default)
- Auto-deslop (regression-safe cleanup)
- Won't say "done" until 100% verified
- Resumes automatically on context reset

**Use when:** High-stakes work that cannot fail silently (auth, payments, critical paths).

### 🚀 **bifrost** — Parallel Execution
"Build these 6 things at the same time"

Multi-agent parallel execution with smart model routing:
- Fires independent tasks simultaneously (up to 6 concurrent)
- Haiku (simple) → Sonnet (standard) → Opus (complex)
- Background execution for builds/tests
- No persistence (you manage completion)

**Use when:** Multiple independent tasks, fast iteration needed.

### 👥 **einherjar** — Multi-Agent Teams
"Coordinate multiple specialists on this task"

Native Claude Code teams orchestration:
- N coordinated agents (1-20) on shared task list
- Stage-aware routing (explore → plan → execute → verify → fix)
- Task dependencies and inter-agent messaging
- External worker support (Codex, Gemini via tmux)
- Auto-fix loop with bounded attempts

**Use when:** Large coordinated efforts, team collaboration.

### 🤔 **the-council** — Consensus Planning
"Get consensus before we build this"

Three-way iterative consensus planning:
- Planner → proposes execution strategy
- Architect → critiques design and boundaries
- Critic → challenges assumptions and risks
- Iterate until consensus or decision point

**Use when:** Architecture decisions matter, need multiple perspectives.

## 19+ Specialized Agents

**Build Lane (Implementation):**
- **explore** (Haiku) — Fast codebase discovery
- **analyst** (Opus) — Requirements clarity
- **planner** (Opus) — Task sequencing
- **architect** (Opus) — System design
- **debugger** (Sonnet) — Root-cause analysis
- **executor** (Sonnet) — Code implementation
- **verifier** (Sonnet) — Completion evidence
- **tracer** (Sonnet) — Causal analysis

**Review Lane (Quality Gates):**
- **security-reviewer** (Sonnet) — Vulnerabilities, auth/crypto
- **code-reviewer** (Opus) — Logic, maintainability, performance

**Specialists:**
- **test-engineer** (Sonnet) — Test strategy, coverage
- **designer** (Sonnet) — UI/UX architecture
- **writer** (Haiku) — Documentation
- **qa-tester** (Sonnet) — Runtime validation
- **scientist** (Sonnet) — Data analysis
- **git-master** (Sonnet) — Git operations
- **document-specialist** (Sonnet) — API/SDK reference
- **code-simplifier** (Opus) — Clarity improvements
- **critic** (Opus) — Gap analysis, challenges

## VikingBay Core Skills (Battle-Tested)

- **vikingbay-build-loop** — Fix-verify loop until green
- **vikingbay-klara-byggja** — Strategic orchestration (the operating system)
- **vikingbay-fullstack-advance** — Vertical slice feature building
- **vikingbay-platform-ops** — Railway/Fly.io/Supabase/Vercel operations
- **vikingbay-ui-ux** — Advanced interface patterns
- **vikingbay-smart-compact** — Pre-compaction checkpoint
- **vikingbay-super-memory** — Cross-session memory reading
- **vikingbay-sync-build-state** — Sync build state with reality
- **vikingbay-verd-eg-betri** — Extract reusable lessons

## What's New (April 2026)

### DAG Task Dependencies (einherjar + ragnarok)
Tasks now support directed acyclic graph (DAG) dependency declarations. The planner agent emits tasks with a `blocks` field — Task C cannot start until Task A and B complete. Prevents hallucinated completion in parallel builds.
```json
{ "id": "task-3", "description": "Run tests", "blocks": ["task-1", "task-2"], "assignee": "verifier" }
```

### Peer-to-Peer Agent Messaging (einherjar direct-wire)
Agents can now message each other directly via mailbox without routing through the lead — removes the coordination bottleneck at 10+ agents. Enable with `direct-wire: true` in vikingbay-config.json.
```
security-reviewer → executor: "VULN:[file]:[line]:[severity]"
test-engineer → executor: "TEST-FAIL:[name]:[expected]:[got]"
```

### Visual Verdict Agent (UI QA)
New `visual-verdict` agent in the Review Lane. Runs after qa-tester in ragnarok QA cycles and before reviewer approval in valholl. Takes a screenshot of the running app, compares against designer agent spec, emits pass/fail with annotated diff.

### Cross-IDE Compatibility Header
VikingBay now declares compatibility with Claude Code, Cursor, Gemini CLI, Codex CLI, and Antigravity IDE — discoverable in the universal skill marketplace.

### Bifrost HUD with Worktree Awareness
`skalds-chronicle --bifrost --watch` now shows per-worktree status during parallel execution. Configure in vikingbay-config.json under `bifrost.hud`.

---

## Guardian System: Heimdall (oss-check)

### Interactive Mode
```bash
/VikingBay:heimdall
"I want to build a video editor with real-time collaboration"
```

Returns: "Found 12 existing projects. #1 match: OBS Studio + Collab fork (4.2K stars, MIT, maintained). Clone and extend, or build from scratch?"

### Guardian Mode (Session-Start)
Automatically checks for existing OSS before you build:

**Configuration options:**
- `always` — Every session, pause for review
- `new-projects-only` — Only on new project directories
- `never` — Disable (manual `/VikingBay:heimdall` only)
- `manual` — Silent check, findings in notepad

Set in `~/.claude/vikingbay-config.json`:
```json
{
  "heimdall": {
    "mode": "new-projects-only",
    "auto-search": true,
    "block-until-decision": false
  }
}
```

## Utility Skills

- **orlog** — Consult multiple AI oracles (Claude + Gemini + DeepSeek)
- **skalds-chronicle** — Execution timeline and session history
- **runes-of-wisdom** — Extract reusable patterns from sessions
- **valhalla-reset** — Stop any active mode

## State Management

VikingBay persists state across context resets via `.omc/` directory:

```
.omc/
├── state/
│   ├── ragnarok-state.json
│   ├── valholl-state.json
│   └── [other-mode]-state.json
├── plans/
│   ├── prd.json
│   └── implementation-plan.md
├── notepad.md (cross-session notes)
└── project-memory.json (learnings)
```

Session automatically resumes from checkpoint on context reset.

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

## Philosophy

**For anyone.** No gatekeeping. VikingBay works for:
- Indie hackers building solo
- Teams coordinating on shared work
- Large refactors in mature codebases
- First-time Claude Code users
- Seasoned engineers wanting superpowers

**One fixed price metaphor.** Install VikingBay once, access everything. No paying for individual skills or modes.

**Battle-tested.** VikingBay powers production systems. OMC has 15.8K GitHub stars. This works.

## Documentation

- **[MODES.md](../MODES.md)** — Deep dive into each execution mode
- **[AGENTS.md](../AGENTS.md)** — Agent roles and specializations
- **[VIKINGBAY.md](../VIKINGBAY.md)** — VikingBay skill reference
- **[PATTERNS.md](../PATTERNS.md)** — Reusable code patterns
- **[SETUP.md](../SETUP.md)** — Installation troubleshooting

## License

MIT — Do whatever you want.

## Support

- **Issues:** [GitHub Issues](https://github.com/salli94/vikingbay/issues)
- **Discussions:** [GitHub Discussions](https://github.com/salli94/vikingbay/discussions)

---

⚔️ *May your builds be swift, your tests be green, and your refactors be safe.* ⚔️
