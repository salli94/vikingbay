---
name: maxpower-write-new-skill
description: Opus-powered skill factory. 3 parallel search agents find the best prompts and patterns, then a council of uniquely-prompted expert agents all work simultaneously to produce a complete, working SKILL.md. Invoke with MAXSKILL.
model: opus
allowed-tools: Agent, WebSearch, WebFetch, Read, Write, Bash, Glob, Grep
---

# MaxPower-Write-New-Skill (MAXSKILL)

Three search agents in parallel find the best patterns and prompts. Their majority decision uniquely prompts a council of expert agents who all fire at once. Output: a complete, production-ready SKILL.md.

---

## Step 0 — Intake (ask before anything else)

Ask the user these 3 questions. Wait for answers before proceeding.

```
Before the agents start, I need 3 things:

1. WHAT: What should this skill do? (one sentence is fine — agents will expand it)
2. TRIGGER: When should Claude invoke it? What user phrase or situation activates it?
3. SCOPE: What's the output? (code, a plan, a document, a refined prompt, a full build, etc.)
```

Store answers as: `SKILL_WHAT`, `SKILL_TRIGGER`, `SKILL_SCOPE`.

---

## Step 1 — 3 Parallel Search Agents

Launch all 3 IN PARALLEL (one Agent tool message, 3 calls). Each gets the user's 3 answers.

---

**SCOUT-1 — Pattern & GitHub Agent**

```
You are SCOUT-1. Search GitHub and the Claude Code skill ecosystem for:
1. Existing skills that do something similar to: {SKILL_WHAT}
2. The best-structured Claude Code SKILL.md files in terms of format, depth, and usability
3. Top-starred skill packs that contain relevant patterns

Search: "claude code skill {SKILL_WHAT} github 2026", "SKILL.md best practices format 2026"

Return:
- TOP 3 existing similar skills (name, URL, what they do, what to steal)
- TOP 3 structural patterns worth copying (with example snippets)
- GAP: what does NOT exist yet that this new skill should fill
- PROMPT RECOMMENDATION: the single best system prompt framing for this skill type
```

---

**SCOUT-2 — Prompt Architecture Agent**

```
You are SCOUT-2. Research the optimal prompting strategy for a skill that does: {SKILL_WHAT}
Triggered by: {SKILL_TRIGGER}
Producing: {SKILL_SCOPE}

Search: "best prompt engineering for {SKILL_WHAT} Claude 2026", "agentic skill prompting strategies opus 2026"

Return:
- TOP 3 prompting techniques most relevant to this skill's job
- CHAIN OF THOUGHT pattern: how should this skill reason step by step?
- FAILURE MODES: top 3 ways this skill could fail and how to prompt around them
- COUNCIL RECOMMENDATION: what expert perspectives does this skill need in its council?
  (e.g., "needs a security reviewer, a performance engineer, and a UX architect")
```

---

**SCOUT-3 — Domain Expert Agent**

```
You are SCOUT-3. Deep dive into the subject matter that {SKILL_WHAT} operates in.

If it's a coding skill: research the specific languages, frameworks, patterns involved.
If it's a planning skill: research planning frameworks, decision models, risk patterns.
If it's a research skill: research search strategies, synthesis methods, source quality signals.
If it's a creative skill: research creative frameworks, critique models, quality rubrics.

Search: "{SKILL_WHAT} expert techniques 2026", "{SKILL_SCOPE} best practices production"

Return:
- DOMAIN MAP: the 5 most important concepts this skill must understand deeply
- EXPERT VOCABULARY: terms and patterns the skill should use fluently
- QUALITY GATES: how does an expert in this domain know the output is good?
- COUNCIL RECOMMENDATION: what expert roles are needed? (be specific — not "developer" but "React performance engineer" or "distributed systems architect")
```

---

## Step 2 — Council Composition (majority vote)

After all 3 scouts return, tally their COUNCIL RECOMMENDATION votes:

1. List all recommended expert roles from SCOUT-2 and SCOUT-3
2. Count overlaps — any role recommended by 2+ scouts is **mandatory** on council
3. Fill remaining council slots (target: 5-7 members) with highest-voted unique roles
4. For each council member, write their unique system prompt using:
   - Scout findings from their domain
   - The prompt architecture from SCOUT-2
   - The domain vocabulary from SCOUT-3

Council target size: **5 members minimum, 7 maximum**.

Example council for a "database migration skill":
- Member 1: Senior PostgreSQL architect (10 years production experience)
- Member 2: Data migration safety engineer (zero-downtime specialist)
- Member 3: Performance benchmark expert
- Member 4: Rollback strategy designer
- Member 5: Claude Code skill format specialist

---

## Step 3 — Council Execution (all fire in parallel)

Launch all council members IN PARALLEL (one Agent tool message).

Each council member receives:
- The user's 3 intake answers
- All 3 scout reports (full, untruncated)
- Their unique system prompt (crafted in Step 2)
- This instruction:

```
You are {MEMBER_NAME} ({EXPERTISE}).

Your job: write the section of the new skill that only you are qualified to write.

Specifically produce:
1. Your section of the skill's CORE LOGIC (the part Claude follows when executing)
2. Your QUALITY GATES (how Claude knows this section is done correctly)  
3. Your EDGE CASES (what can go wrong in your domain, and what to do)
4. Your PROMPT LINES (3-5 exact lines to include in the skill's system prompt)

Format: structured markdown, ready to paste into SKILL.md
Do not write the full skill — only your section. EXECUTOR will assemble everything.
```

---

## Step 4 — EXECUTOR Assembly

After all council members return, EXECUTOR assembles the final SKILL.md:

1. Read all council sections
2. Resolve conflicts (later expertise wins in its own domain)
3. Structure the skill with:
   - Frontmatter (name, description, model, allowed-tools)
   - Clear trigger/activation section
   - Step-by-step execution pipeline
   - Quality gates from council
   - Edge cases and failure handling
   - Example usage (concrete, not generic)
4. Self-review: does this skill work as a single prompt regardless of token use?
5. Trim: remove anything that doesn't directly help Claude execute the skill

---

## Step 5 — Output

Write the complete SKILL.md to: `C:/Users/runar/.claude/skills/{skill-name}/SKILL.md`

Then output:
```
╔══════════════════════════════════════════════════╗
║         MAXSKILL — SKILL CREATED                 ║
╠══════════════════════════════════════════════════╣
Name: {skill-name}
Invoke with: {trigger}
Scouts: 3 | Council: {N} members | Conflicts resolved: {N}

Similar existing skills found: {TOP 1 from SCOUT-1}
Key gap filled: {GAP from SCOUT-1}
Top technique used: {from SCOUT-2}

Skill written to: ~/.claude/skills/{name}/SKILL.md
╚══════════════════════════════════════════════════╝
```

Also add entry to vikingbay SKILL.md skill list if running inside the vikingbay package.

---

## Rules

1. NEVER skip Step 0 — intake answers are what give scouts direction
2. ALWAYS launch scouts in one parallel batch
3. ALWAYS launch council in one parallel batch after composition
4. Council composition is decided by scout majority — not by Claude's default judgment
5. EXECUTOR never adds their own opinions — only assembles what council produced
6. Final skill must be self-contained and work as a single prompt
7. Write the file — don't just output it to the conversation
