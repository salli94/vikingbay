---
name: maxpower-deep-dive
description: General-purpose maximum power research and execution engine. Asks 3-5 targeted questions, assigns 3 parallel search agents to specific domains, presents findings to a council of uniquely-prompted expert agents (professors, devs, engineers), then compiles everything into the most efficient accomplishable outcome — skill, code, document, plan, or anything else. Invoke with DEEPDIVE.
model: opus
allowed-tools: Agent, WebSearch, WebFetch, Read, Write, Bash, Glob, Grep
---

# MaxPower-DeepDive-Anything (DEEPDIVE)

Ask 3 smart questions. 3 agents search their assigned domains in parallel. Their findings uniquely prompt a council of expert agents who all fire simultaneously. Everything compiles into one outcome that is accomplishable in a single prompt, regardless of token use.

---

## Step 0 — Targeted Intake

Before any agents run, ask the user these questions. Tailor which ones you ask based on context — pick the 3-5 most relevant. Wait for answers.

**Always ask:**
1. **GOAL:** What is the end result you want? Be as rough or specific as you like — agents will refine it.
2. **OUTPUT FORM:** What shape should the result take? (skill file, working code, research doc, execution plan, a single powerful prompt, something else?)

**Ask if unclear from context:**
3. **DOMAIN:** What field or technology is this in? (e.g., Next.js, Supabase, AI agents, system design, marketing copy, legal analysis, etc.)
4. **CONSTRAINT:** Any hard limits? (time, cost, stack, style, no X, must use Y)
5. **SUCCESS:** How will you know it worked? What does a perfect result look like?

Store answers as: `GOAL`, `OUTPUT_FORM`, `DOMAIN`, `CONSTRAINT`, `SUCCESS_CRITERIA`.

---

## Step 1 — Search Domain Assignment

Before launching scouts, assign each scout a specific search domain based on intake answers:

| Scout | Default Domain | Reassign if... |
|-------|---------------|----------------|
| SCOUT-1 | Existing OSS, GitHub, community patterns | Goal is novel/creative → assign to theory/research |
| SCOUT-2 | Prompting strategy, execution patterns, how to accomplish goal | Goal is data/analysis → assign to datasets/tools |
| SCOUT-3 | Deep domain expertise, vocabulary, expert quality standards | Goal is well-defined tech → assign to specific tech docs |

Write the 3 specific search briefs before launching. Each brief includes:
- Exactly what to search for
- Which sources to prioritize
- What to bring back (format specified below)

---

## Step 2 — 3 Parallel Search Agents

Launch all 3 IN PARALLEL (one Agent tool message, 3 calls).

---

**SCOUT-1 — [ASSIGNED DOMAIN 1]**

```
You are SCOUT-1 assigned to: {DOMAIN_1}

User goal: {GOAL}
Output form: {OUTPUT_FORM}
Domain: {DOMAIN}

Your search brief: {SEARCH_BRIEF_1}

Search using WebSearch. Prioritize: {SOURCE_PRIORITIES_1}

Return exactly:
TOP_FINDS: [3-5 most useful discoveries — name, what it is, why it matters for this goal]
WHAT_EXISTS: [what already exists that covers part of this goal]
WHAT_DOESNT: [what's missing — the actual gap this work needs to fill]
COUNCIL_NEEDS: [what expert perspectives are needed to accomplish this goal? Be specific — role + reason]
BEST_APPROACH: [your single strongest recommendation for how to accomplish the goal]
KEY_SOURCES: [top 3 sources found, with URLs]
```

---

**SCOUT-2 — [ASSIGNED DOMAIN 2]**

```
You are SCOUT-2 assigned to: {DOMAIN_2}

User goal: {GOAL}
Output form: {OUTPUT_FORM}
Constraint: {CONSTRAINT}

Your search brief: {SEARCH_BRIEF_2}

Search using WebSearch. Prioritize: {SOURCE_PRIORITIES_2}

Return exactly:
TOP_FINDS: [3-5 discoveries]
EXECUTION_PATH: [the most efficient sequence of steps to accomplish the goal]
FAILURE_MODES: [top 3 ways this goal typically fails and how to avoid each]
COUNCIL_NEEDS: [specific expert roles needed — with reasoning]
BEST_APPROACH: [your single strongest recommendation]
KEY_SOURCES: [top 3 sources]
```

---

**SCOUT-3 — [ASSIGNED DOMAIN 3]**

```
You are SCOUT-3 assigned to: {DOMAIN_3}

User goal: {GOAL}
Success criteria: {SUCCESS_CRITERIA}
Domain: {DOMAIN}

Your search brief: {SEARCH_BRIEF_3}

Search using WebSearch. Prioritize: {SOURCE_PRIORITIES_3}

Return exactly:
TOP_FINDS: [3-5 discoveries]
DOMAIN_MAP: [5 most important concepts/patterns the council must understand to accomplish this]
EXPERT_VOCAB: [key terminology — what an expert in this domain says vs. what a novice says]
QUALITY_GATES: [how does an expert know the output is correct/excellent?]
COUNCIL_NEEDS: [specific expert roles — be precise: not "developer" but "Python async I/O specialist"]
BEST_APPROACH: [your single strongest recommendation]
```

---

## Step 3 — Council Composition (majority vote from scouts)

After all 3 scouts return:

1. Collect all `COUNCIL_NEEDS` lists from SCOUT-1, SCOUT-2, SCOUT-3
2. Tally: any role mentioned by 2+ scouts = **mandatory council seat**
3. Fill remaining seats with highest-voted unique roles
4. Synthesize what each member needs to know from scout findings
5. Write a unique system prompt for each council member

**Council size:** 5-8 members.

**Council always includes at minimum:**
- 1 domain expert (the core subject matter)
- 1 critical challenger (finds gaps, pokes holes — always unbiased)
- 1 output specialist (expert in whatever OUTPUT_FORM is)

**Example councils by goal type:**

*Goal: Build a React performance monitoring tool*
→ React rendering expert, Node.js profiling engineer, DevOps observability architect, UX/DX designer, Security auditor

*Goal: Write a legal contract template*
→ Contract law professor, IP specialist, risk analyst, plain-language editor, jurisdiction expert

*Goal: Design a multi-agent AI system*
→ Distributed systems architect, LLM prompt engineer, state management expert, failure recovery specialist, cost optimization analyst

*Goal: Create a marketing campaign*
→ Behavioral psychologist, copywriter (direct response), brand strategist, data-driven growth marketer, creative director

---

## Step 4 — Council Execution (all fire in parallel)

Launch all council members IN PARALLEL.

Each council member receives:
- User intake answers (all 5)
- Full scout reports (complete, untruncated)
- Their unique system prompt
- This instruction:

```
You are {MEMBER_NAME}: {EXPERTISE_DESCRIPTION}

You are one member of a council working to accomplish:
GOAL: {GOAL}
OUTPUT FORM: {OUTPUT_FORM}
SUCCESS CRITERIA: {SUCCESS_CRITERIA}

You have read all 3 scout reports. You understand the full context.

Your job: produce your contribution to the final output.

From YOUR expert perspective:
1. CORE CONTRIBUTION: the most important thing only you can add to accomplish this goal
2. YOUR SECTION: your full written contribution (code / text / analysis / design — whatever fits)
3. WATCH-OUTS: what the other council members might miss that you see clearly
4. QUALITY CHECK: how to verify your contribution is correct from your expert standpoint
5. INTEGRATION NOTE: how your piece fits with and depends on the other council members' work

Be comprehensive. Token use is not a constraint here. Depth over brevity.
```

---

## Step 5 — EXECUTOR: Final Compilation

After all council members return:

1. Read every contribution
2. Identify: overlaps (merge), conflicts (domain authority wins), gaps (flag for user)
3. Compile into the requested OUTPUT_FORM:
   - **Skill file** → write complete SKILL.md
   - **Code** → write complete, working implementation
   - **Document** → write structured, expert-level document
   - **Plan** → write step-by-step execution plan with dependencies
   - **Prompt** → write a single, self-contained prompt that accomplishes the goal
   - **Anything else** → match the form to what the user specified

4. **The one-prompt test:** Before finalizing, ask: "Can this output be fed as a single prompt to Claude and accomplish the goal without follow-up?" If not — keep compiling until it can.

5. Write the output to disk if it's a file. Print it in full if it's text.

---

## Step 6 — Final Report

```
╔══════════════════════════════════════════════════════╗
║           DEEPDIVE — COMPLETE                        ║
╠══════════════════════════════════════════════════════╣
Goal: {GOAL}
Output: {OUTPUT_FORM}

Scouts deployed: 3
  SCOUT-1 found: {TOP_FIND_1}
  SCOUT-2 found: {TOP_FIND_2}
  SCOUT-3 found: {TOP_FIND_3}

Council: {N} members
  {MEMBER_1}: {KEY_CONTRIBUTION}
  {MEMBER_2}: {KEY_CONTRIBUTION}
  ...

Conflicts resolved: {N}
Gaps flagged: {N} [list them if any]
One-prompt test: PASS / FAIL + fix applied

OUTPUT: {path if file, or "printed above" if text}
╚══════════════════════════════════════════════════════╝
```

---

## Scope Variations

DEEPDIVE adapts its council automatically:

| Goal Type | Council Bias |
|-----------|-------------|
| Write a new Claude skill | Prompt engineer, Claude Code expert, domain specialist, critical reviewer |
| Build a feature | Backend engineer, frontend engineer, QA engineer, architect, security reviewer |
| Research a topic | Domain professor, data analyst, skeptic/critic, synthesizer, communicator |
| Design a system | Architect, performance engineer, ops engineer, security expert, cost analyst |
| Create content | Domain expert, writer, editor, audience specialist, distribution strategist |
| Debug a problem | Root cause analyst, domain specialist, systems thinker, fix verifier |

---

## Rules

1. ALWAYS ask Step 0 questions first — no scouts launch without intake answers
2. ALWAYS assign specific search briefs to each scout before launching them
3. ALWAYS launch scouts in one parallel batch
4. ALWAYS launch council in one parallel batch after composition
5. Council composition is driven by scout majority vote — Claude does not unilaterally decide
6. EXECUTOR assembles, never adds opinions not backed by council
7. The one-prompt test is mandatory — output must be self-contained
8. Token use is never a constraint — depth and completeness beat brevity here
9. If OUTPUT_FORM is a skill: write the file, don't just print it
