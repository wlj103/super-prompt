---
name: "super-prompt"
description: "Prompt Engineering Tool: Anti-Ambiguity Interception × Web Pre-Search × Layered Guidance × ELO Ranking. Forge production-grade prompts for Claude, GPT, Gemini, and AI agents. Use when writing prompts, system prompts, agent instructions, or SOPs. Trigger: 'write a prompt', 'optimize my prompt', 'forge a prompt'."
license: MIT
---

# Super-Prompt v1.0

**Make every instruction received by AI precise and unambiguous — not "good enough."**

## The Problem

Prompt engineering has a fundamental flaw: **models learn to circumvent prompts.** You say "mandatory verification," and it outputs four characters: "Verification passed." You say "detailed explanation," and 3 lines of fluff counts as detailed. You say "use JSON format," and it freely invents field names.

This isn't because models aren't smart enough — it's because models are too smart. They've learned to satisfy literal requirements with minimal cognitive cost while bypassing the real intent.

Super-Prompt is not a template, not a fill-in-the-blank form — it's a **complete prompt engineering discipline system.** Through seven guided gates + web search preloading + anti-ambiguity verification + ELO multi-candidate ranking, it helps users forge **production-grade prompts that AI cannot misinterpret** — starting from a single sentence or a product document.

## What Makes This Different

| Other Prompt Tools | Super-Prompt |
|-------------|-------------|
| "Write a prompt" | Seven gates must be passed, no skipping |
| Trusts that users expressed clearly | **Anti-ambiguity clauses**: 18-item checklist scanned item by item, no empty assertions |
| Users judge quality themselves | Gate Five: Multi-candidate ELO ranking, pairwise PK quantified comparison |
| "Looks good" | Evidence-driven: every design decision backed by search evidence or industry standards |
| One-shot questioning | Layered guidance: ≤4 questions per round, starting from simplest mandatory questions, deepening layer by layer |
| Makes users think of answers themselves | Web search preloading: search before every question, convert results into options injected into questions |
| Single candidate, roll the dice | **Multi-candidate ELO ranking**: generate 3-5 candidates, quantify PK, data speaks |

Super-Prompt is the only prompt engineering system that **systematically classifies how models misinterpret instructions** and creates **locking methods** for each misinterpretation path. Built-in ELO ranking system (integrated from gpt-prompt-engineer, MIT license), using chess ranking algorithms to quantitatively compare candidate prompts.

### How Models Circumvent Prompts

| You Say | It Understands As | Why It's Dangerous |
|------|---------|-----------|
| "Describe concisely" | 3 lines of fluff counts as concise | Model chooses the path of least cognitive cost |
| "Use JSON format" | Field names? Nesting? Optional? Whatever | Model freely improvises, downstream parsing fails |
| "Handle exceptions" | Only writes try-catch, not what to handle | Form validation, actually ineffective |
| "Professional tone" | PhD-level or entry-level? Guess one | Audience mismatch, message fails to convey |
| "Handle appropriately" | What's appropriate? Whatever | Non-determinable, non-verifiable |
| "High quality" | Self-assessed pass | Non-determinable, equals saying nothing |
| "Include relevant features" | What's relevant? Free rein | Scope creep, delivery out of control |
| "Be concise but complete" | Contradictory instruction, random trade-offs | Either incomplete or not concise |

## Relationship with super-spec

- **super-spec** = engineering discipline (can steps be skipped? can evidence be produced? is cross-document self-consistency maintained?)
- **super-prompt** = prompt discipline (is expression precise? is structure clear? is ambiguity locked down?)

```
User need → [super-prompt] → high-quality prompt document → [super-spec] → five engineering documents → delivery
```

spec governs discipline, prompt governs expression. Two swords combined.

---

## Quick Reference Card (must-read before agent execution)

### Three Modes

Gate Zero automatically classifies mode after determining intent, user confirms:

| Mode | User Profile | Input | Process | Interaction Style |
|------|---------|------|------|---------|
| Standard | Non-programmer / no docs | One sentence / vague need | Full search → gate-by-gate guidance | Gate-by-gate multiple choice |
| Review | Senior / has complete plan | PRD / business doc / prototype | Auto full pre-search → batch optimization points → user selects deep-dive → Gates 3–6 | Batch present points, user selects |
| Heavy-Duty | Team / multi-agent | Complex engineering docs | First ask "compare against benchmarks?" → if yes, pre-search benchmarking → all seven gates + ELO×2 | Break down every section thoroughly |

### Fast Track

User comes in with clear requirements (role + format + boundaries all specified), skip Gate Zero/One, start from Gate Two structure skeleton. The normal experience is "oh, we're already started without filling in forms."

### Output Complexity Tiers

Input mode determines **how to interact**, output complexity determines **how deep to deliver**. The two are orthogonal.

During interaction, the Agent automatically determines the project tier based on collected information and outputs it for user confirmation at Gate Zero:

| Tier | Criteria | Output Requirements | Gate Differences |
|------|---------|---------|---------|
| Light | Test / experiment / one-shot prompt, or user explicitly says "just keep it simple" / "try it out first" | Basic prompt document | Gate Five skips ELO multi-candidate (single candidate OK); Gate Four only checks first 9 of 18 items; Gate Six wrap-up 4 items |
| Medium (default) | Regular production prompt, clear scenario but not system-level | Standard prompt document | Full seven-gate standard process |
| Heavy | Agent system prompt, multi-agent collaboration, production-grade SOP | Complete prompt document + test cases + regression verification | Full seven gates + ELO×2 + all 18 items + 8-item full wrap-up checklist |

**Auto-determination rules** (Agent outputs determination after collecting the following information at Gate Zero):

Gate Zero must ask one follow-up about functional scope — "What core features does this project roughly have?" — and auto-classify based on the complexity of the answer, not just keyword matching.

- User mentions "Agent" / "system prompt" / "multi-agent" / "SOP" / "production environment" → Heavy
- User mentions "test" / "try out" / "temporary" / "see how it works first" → Light
- Single function, clear boundaries (e.g., "a calendar component" / "a translation API") → Light
- Multiple functions but flat (e.g., "2D casual game" / "content management backend") → Medium
- Complex functions, multi-layered nesting (e.g., "3D open world" / "multi-agent collaboration platform") → Heavy
- Everything else → Medium (default)

**Examples**:
| User Says | After Follow-up | Determination |
|--------|-------|------|
| "Build an app" | "A single calendar function" | Light |
| "Build an app" | "2D casual game" | Medium |
| "Build an app" | "3D open world, with character system, physics engine" | Heavy |
| "3D game" | "Small map, single-player" | Heavy |
| "3D game" | "Large map + online multiplayer + state sync" | Heavy (deeper, need additional network/sync/latency constraints) |

**Heavy tier additional probing**: After determining "Heavy," Gate Zero asks one more follow-up:
- Does it need networking / multiplayer?
- What's the data scale? (local / hundreds / tens of thousands of users)
- Is there real-time sync needed?

Based on the answers, decide whether to enable ELO×2 at Gate Five and add boundary condition generation at Gate Four.

The determination result is output at Gate Zero when confirming intent: "Based on your description, this project is classified as [Light / Medium / Heavy] tier, with the following output standards…"

### Search Rules (universal across all modes)

**All gates must search.** Search is core value, not a burden. Standard mode users lack documentation and need search even more to provide options.

Search degradation: search unavailable → ask questions normally, mark "not searched, for reference only."

### Non-Skippable Checkpoints (by output complexity)

**Light tier**:
1. Gate Three: every section must pass anti-ambiguity check
2. Gate Four: first 9 anti-ambiguity items scanned item by item, no empty assertions
3. Gate Six: 4-item wrap-up checklist verified item by item

**Medium tier**:
1. Gate Three: every section must pass anti-ambiguity check
2. Gate Four: all 18 items verified, must actually scan text, no empty "yes" assertions
3. Gate Five: ELO ranking must run all candidate pairs, no skipping pairs
4. Gate Six: 8-item wrap-up checklist verified item by item

**Heavy tier**:
1. All Medium tier items
2. Gate Five: ELO×2, bidirectional scoring + additional test cases
3. Gate Four: additional boundary condition generation (networking / multiplayer / scale / real-time sync)

---

## Seven Design Principles

| # | Principle | Opposite (How Models Substitute "Good Enough") |
|---|------|-------------------------------|
| 1 | Lock semantics, not creativity | "Concise" not quantified → 3 lines or 30 lines, both pass |
| 2 | Verify structure, don't trust expression | "Include error handling" → only writes try-catch, not what to handle |
| 3 | Layer guidance, not one-shot | Dump 20 questions at once → user crashes / fills in randomly |
| 4 | Evidence-driven, not feeling-driven | "I think this is good" → no search evidence backing |
| 5 | Probe-driven, not hardcoded | Assume user's tech stack → doesn't match reality |
| 6 | Ambiguity acceptance, don't trust acceptance | "Looks fine" → 18-item checklist not passed |
| 7 | Output on demand, no excess, no shortfall | Calendar component doesn't run all 18 items; 3D open world doesn't skip ELO×2. Safety margin only increases, never decreases |

---

## Anti-Ambiguity System

### Four-Type Anti-Ambiguity Clauses

**A. Semantic Vagueness (Laziness Hotspot)**

| You Say | How Model "Good-Enoughs" It | Locking Method |
|------|-----------------|------|
| "Describe concisely" | 3 lines of fluff counts as concise | Specify line limit: "≤5 lines" |
| "Explain in detail" | 10 lines or 100 lines both count as detailed | Specify minimum line count or paragraph structure |
| "Professional tone" | PhD-level or entry-level? Guess one | Define audience + terminology level |
| "Handle appropriately" | What's appropriate? Whatever | Give specific values or conditional branches |
| "High quality" | Non-determinable, self-assessed pass | Give verifiable judgment criteria |

**B. Structural Deficiency**

| You Say | How Model "Good-Enoughs" It | Locking Method |
|------|-----------------|------|
| "Use JSON format" | Field names? Nesting? Optional? Whatever | Give complete schema with examples |
| "Handle exceptions" | Only writes try-catch, not what to handle | List exception types + respective handling |
| "Write tests" | Test what? What criteria? | Give test case list + pass conditions |
| "Optimize performance" | Optimize what? To what degree? | Give specific metrics + target values |
| "Add comments" | Comment what? How detailed? | Give commenting rules |

**C. Unclear Boundaries**

| You Say | How Model "Good-Enoughs" It | Locking Method |
|------|-----------------|------|
| "Include relevant features" | What's relevant? | Explicitly list, narrow with "only do the following" |
| "Not too much" | How much is too much? | Give upper limit number |
| "Can extend if needed" | Who judges "if needed"? | Give judgment condition → trigger action |
| "Refer to best practices" | Which practices? | List specific sources or search links |
| "Be concise but complete" | Contradictory instruction | Decompose: which must be complete → which can be concise |

**D. Implicit Assumptions**

| You Assume | Model Doesn't Know | Locking Method |
|--------|----------|------|
| Knows target audience | Model guesses wrong audience | Explicitly write user persona |
| Knows tech stack | Model uses something else | Explicitly lock language / framework / version |
| Knows output language | Model may use English | Explicitly specify language |
| Knows context | Model has no memory | Explicitly provide or reference |
| Knows constraints | Model freely improvises | Explicitly list hard constraints + soft constraints |

### 18-Item Anti-Ambiguity Verification Checklist

**Must actually scan the text, no empty "yes" assertions.**

| # | Check Item | Inspection Method | Fix Suggestion |
|---|--------|---------|---------|
| 1 | Adjectives/adverbs quantified | Scan for "concise/detailed/professional/appropriate/high quality" | Replace with specific values or determinable criteria |
| 2 | Format requirements have complete schema | Check if "JSON/table/list" has field definitions | Supplement complete schema + examples |
| 3 | Role definition includes capability boundaries | Check if "you are XX" has "can/cannot do" | Supplement capability boundary statement |
| 4 | Error handling lists specific types | Check if "handle errors/exceptions" is enumerated | List error types + respective handling methods |
| 5 | Test requirements have judgment criteria | Check if "write tests" has pass conditions | Supplement test cases + pass criteria |
| 6 | Performance requirements have specific metrics | Check if "optimize/improve" has target values | Supplement "from X to Y" |
| 7 | Boundaries locked in both directions | Check for "only do / do not do" statements | Supplement positive + negative checklists |
| 8 | Input has examples | Check if input examples exist | Supplement 2-3 examples |
| 9 | Output has examples | Check if output examples exist | Supplement 2-3 examples |
| 10 | Terminology defined | Scan for specialized terms with first-use definitions | Attach definition on first occurrence |
| 11 | Vague quantifiers replaced | Scan for "appropriate/moderate/on-demand/try to" | Replace with specific values or conditions |
| 12 | Open-ended instructions narrowed | Scan for "if needed / can / try to" | Replace with "when X → do Y" |
| 13 | Implicit assumptions made explicit | Scan for "default / of course / obviously" | Explicitly write out assumed content |
| 14 | Ambiguous references disambiguated | Scan for "this / that / it / aforementioned" | Replace with explicit referent |
| 15 | Steps have sequential numbering | Check if processes have numbering | Supplement step numbers |
| 16 | Conditional branches are complete | Check if if has else | Supplement else branch or explicitly state "no else" |
| 17 | Constraints are verifiable | Check if each constraint has a verification method | Supplement "verification method: X" |
| 18 | No contradictory instructions | Check for "concise but complete" / "fast but accurate" patterns | Decompose into layered constraints |

---

## Seven-Gate Pipeline

```
Input → Gate Zero · Intent Anchoring (mode classification) → Gate One · Role & Boundaries → Gate Two · Structure Skeleton
     → Gate Three · Section-by-Section Forging → Gate Four · Anti-Ambiguity Verification → Gate Five · ELO Ranking → Gate Six · Wrap-Up & Delivery
     → Output (production-grade prompt document)
```

| Gate | What It Blocks | Pass Condition | Interaction Style |
|------|--------|---------|---------|
| Zero · Intent Anchoring | Writing before clarifying what's needed | Intent three-element confirmation + mode classification | Multiple choice + fill-in |
| One · Role & Boundaries | Vague role / unclear boundaries | Four-element confirmation | Multiple choice + search suggestions |
| Two · Structure Skeleton | Chaotic structure | Skeleton confirmed, each section has clear responsibility | Search → recommend → confirm |
| Three · Section-by-Section Forging | Imprecise expression | Each section passes anti-ambiguity check | Draft + confirm section by section |
| Four · Anti-Ambiguity Verification | Residual ambiguity | Light: first 9 items all green; Medium/Heavy: all 18 items green | Auto check + fix suggestions |
| Five · ELO Ranking | Single candidate, roll the dice | Light: skip; Medium/Heavy: multi-candidate PK, optimal ELO ≥1250 | Auto generate + PK + ranking table |
| Six · Wrap-Up & Delivery | Omissions | Light: 4 items all green; Medium/Heavy: 8 items all green | Auto check + confirm |

---

### Gate Zero · Intent Anchoring

**Must search**: `"[domain] prompt engineering best practices"` + `"[target AI] system prompt guidelines"`

**Standard mode**: Use AskUserQuestion with ≤4 questions (mostly multiple choice), confirm intent three elements → mode classification confirmation.

**Review mode**: User already has complete plan, skip questioning. Enter review process directly (see "Review Mode Process" below).

**Heavy-Duty mode**: First ask "Want to benchmark against industry standards and see if there's room for optimization?" If yes → full pre-search benchmarking (same as Review mode Step 1-2); if no → proceed directly to Gate One. All seven gates + ELO×2, every section broken down and confirmed thoroughly.


#### Step 0: Product Understanding (Conditional)

**Trigger**: User input describes a product or feature to build (e.g., "做一个记账App", "帮我写一个客服机器人的提示词"), rather than a direct prompt optimization request (e.g., "帮我优化这段提示词").

**Why**: For small projects, product requirements are discovered through conversation. Jumping to prompt classification without understanding the product leads to prompts that nail the format but miss what the product actually is.

**Ask 3 questions, conversational:**

1. What problem does this solve?
2. What features do you want? Any special ideas or requirements?
3. Any preferences on design / UI / user flow?

After the user answers, summarize in 1-2 sentences what you understood, get confirmation, then proceed to intent confirmation.

**Skip when**: User is asking for prompt optimization, or provides a detailed requirements document.

#### Must-Confirm Intent Three Elements

1. **What to do**: What is the prompt's target task?
2. **For whom**: Which target AI?
3. **How to measure success**: What output qualifies as passing?

```
Search findings (example):
- Anthropic official recommendation: system prompts should define role first, then task
- 2025 prompt engineering trends: Chain-of-Thought + structured output

Q1: What is this prompt for?
  A) Code generation/review  B) Content creation/writing  C) Data analysis/processing  D) Workflow automation

Q2: Which target AI?
  A) Claude  B) GPT  C) Gemini  D) General-purpose

Q3: How do you measure success? Fill in:
  "When I give this prompt to the AI, the AI should be able to ____"

Q4: Any special constraints? (can skip)
  A) Must support Chinese  B) Output has format requirements  C) Has length limit  D) None
```

Produce 「Intent Anchor Checklist」→ simultaneously output complexity determination (Light / Medium / Heavy) → mode classification → proceed to Gate One after user confirmation.

Complexity determination output simultaneously after intent three-element confirmation, example:

```
Based on your description:
- Target: a calendar component prompt
- Single function, clear boundaries
→ Determination: Light tier, output basic prompt document (skip ELO, first 9 anti-ambiguity items, 4-item wrap-up)
```

### Gate One · Role & Boundaries

**Standard / Heavy-Duty**: Search `"[role] agent prompt examples"` + `"[domain] common pitfalls prompt"` → multiple choice to confirm four elements.

**Review mode**: Skip.

#### Must-Confirm Four Elements

1. **Role**: What does the AI play? What are its capability boundaries?
2. **Input**: What will the AI receive? Format?
3. **Output**: What should the AI output? Format + judgment criteria
4. **Constraints**: Hard constraints + soft constraints + do-not-do list

### Gate Two · Structure Skeleton

**Standard / Heavy-Duty**: Search `"[prompt type] prompt structure template"` → recommend structure → user confirms.

**Review mode**: Skip.

Default structure: Role Definition → Task Description → Input Specification → Output Specification → Execution Constraints → Examples → Appendix

---

### Review Mode Process

Trigger condition: User has provided complete materials such as PRD, business documents, prototypes, mature plans.

**Step 1: Full Pre-Search**

Search benchmarks for all sections of the user's plan at once:

```
Search matrix:
- Role definition → "[role] agent prompt best practices 2025"
- Task description → "[task type] prompt engineering patterns"
- Input specification → "[input type] prompt input format examples"
- Output specification → "[output type] structured output schema"
- Constraints / boundaries → "[domain] prompt constraints best practices"
- Overall structure → "[prompt type] production prompt template"
```

**Step 2: Batch Present Optimization Points**

Benchmark search results against user's plan, present all optimizable points at once:

```
Full pre-search findings (example):

📌 Role Definition
  Your plan covers: role name + responsibility description
  Search findings suggest deepening:
  - 87% of production-grade agent prompts include "capability boundary statement" (can/cannot do)
  - Anthropic official recommendation: follow role definition with a standalone "behavior constraints" section
  → Deepen?

📌 Output Specification
  Your plan covers: output format (JSON)
  Search findings suggest deepening:
  - Industry standard: output specification should include complete JSON Schema + 2-3 examples
  - Common pitfall: only saying "JSON" without defining fields → AI freely invents field names
  → Deepen?

📌 Error Handling
  Your plan does not cover
  Search findings: 94% of similar prompts include an error handling section
  → Supplement?
```

**Step 3: User Selects Deep-Dive Items**

User checks off sections to deepen.

**Step 4: Expand Item by Item**

For each selected section: search → draft → anti-ambiguity check → confirm.

**Step 5: After all deep-dive items complete, proceed to Gates 3-6**

---

### Gate Three · Section-by-Section Forging

**All modes**: Every section must pass anti-ambiguity check; cannot proceed to next section without passing.

For each section in the structure: search → draft → anti-ambiguity check → user confirms.

#### Section-by-Section Iron Rules

| # | Rule | Why | Violation Example |
|---|------|--------|---------|
| 1 | Every section must pass anti-ambiguity check | Model will write vague expressions like "handle appropriately" | "Handle exceptions" not expanded |
| 2 | Every section must include positive examples | No examples = cannot determine if output qualifies | Output spec only says "table" without giving examples |
| 3 | Cross-section references must be explicit | "The above" is ambiguous | "Output in the above format" → change to "Output in the table format per §4 Output Specification" |
| 4 | Search-discovered best practices must be integrated | Not integrating = wasted search | Found "output includes line numbers" but draft didn't add it |

### Gate Four · Anti-Ambiguity Verification

**Light tier**: First 9 items (#1-#9) scanned item by item, no empty "yes" assertions.

**Medium / Heavy tier**: All 18 items verified. No empty "yes" assertions — must scan text and verify item by item.

Any item fails → fix → re-check that item; all pass → next gate.

---

### Gate Five · ELO Ranking

**Core idea**: No longer rely on gut feeling to pick the "best-looking" prompt; instead, generate multiple candidates → pairwise PK → ELO quantified ranking → data speaks.

**Algorithm source**: Integrated from [gpt-prompt-engineer](https://github.com/mshumer/gpt-prompt-engineer) (MIT license), K=32, starting score 1200, chess ranking algorithm.

#### Execution Flow

```
Gate Four passed
  ↓
Step 1: Generate candidates (3-5)
  ↓
Step 2: Define test cases (3-5)
  ↓
Step 3: Pairwise PK + ELO scoring
  ↓
Step 4: Output ranking table
  ↓
Step 5: User confirms top-1
  ↓
Gate Six
```

#### Step 1: Generate Candidate Prompts

**Light tier**: Skip ELO multi-candidate. Directly generate 1 optimized version, proceed to Gate Six.

**Medium / Heavy tier**: Execute full ELO process. **Heavy tier** additionally enables ELO×2 (bidirectional scoring + additional test cases).

Generation strategy: Based on output from Gates Zero through Four, generate candidates with different styles:

```
Candidate generation strategy:
- Candidate A: Conservative — strictly follow user's original expression, minimal changes
- Candidate B: Optimized — integrate search-discovered best practices, structurally enhanced
- Candidate C: Minimalist — trim redundancy, retain core instructions, pursue token efficiency
- Candidate D (Heavy-Duty): Radical — significantly restructure, attempt non-traditional structures
- Candidate E (Heavy-Duty): Academic — cite sources, evidence-driven, suitable for scenarios requiring traceability
```

Each candidate must be independently complete, no references like "same as Candidate A."

#### Step 2: Define Test Cases

Based on intent anchors from Gate Zero, generate 3-5 test cases. Each test case should cover different scenarios:

```
Test case design principles:
- Case 1: Typical scenario (most common usage)
- Case 2: Boundary scenario (extreme input / ambiguous input)
- Case 3: Adversarial scenario (input deliberately triggering AI misinterpretation)
- Case 4 (Heavy-Duty): Stress scenario (complex / long input)
- Case 5 (Heavy-Duty): Multi-language / cross-domain scenario
```

#### Step 3: Pairwise PK + ELO Scoring

```
ELO algorithm parameters:
- Initial score: 1200
- K factor: 32
- Expected win rate: E_A = 1 / (1 + 10^((R_B - R_A) / 400))
- Score update: R_A_new = R_A + K × (S_A - E_A)
  where S_A = 1 (A wins) / 0.5 (draw) / 0 (B wins)
```

**PK Rules**:

1. All candidate pairs, each pair runs one PK round per test case
2. Each PK round: two candidates each generate output for the same test case → judge model blind evaluation, output A or B
3. **Bidirectional scoring**: A vs B and B vs A each evaluated once, take average, eliminate position bias
4. Judge model prompt:

```
"Your task is to compare the quality of two AI outputs.

Task description: {description}
Test input: {test_case}
Output A: {generation_a}
Output B: {generation_b}

Comparison criteria:
- Whether the specified task is accurately completed
- Whether all constraints are precisely followed
- Whether the output format is standardized
- Whether there is any ambiguity or vagueness

Which output is better? Answer only 'A' or 'B'. If truly indistinguishable, answer 'DRAW'."
```

5. Update ELO scores after each PK round
6. Total rounds = candidate count × (candidate count - 1) / 2 × test case count

**Calculation Example**:

```
Candidate A (1200) vs Candidate B (1200), Test Case 1:

A generates → Output A
B generates → Output B
Judge → A

Bidirectional: A vs B → A wins; B vs A → A wins → average S_A = 1.0

E_A = 1 / (1 + 10^((1200-1200)/400)) = 0.5
R_A_new = 1200 + 32 × (1.0 - 0.5) = 1216
R_B_new = 1200 + 32 × (0.0 - 0.5) = 1184
```

#### Step 4: Output Ranking Table

```
ELO Ranking Results (2 candidates × 3 test cases = 3 PK rounds):

┌──────────┬────────┬──────────────────────────────────────┐
│ Rank     │ ELO    │ Candidate                            │
├──────────┼────────┼──────────────────────────────────────┤
│ 🥇 1st   │ 1285   │ Candidate B (Optimized)              │
│ 🥈 2nd   │ 1160   │ Candidate A (Conservative)           │
│ 🥉 3rd   │ 1155   │ Candidate C (Minimalist)             │
└──────────┴────────┴──────────────────────────────────────┘

Recommendation: Candidate B (Optimized), ELO 1285, 2 wins 1 draw across 3 test cases.

Key difference analysis:
- Candidate B significantly outperforms others in boundary scenario (Case 2)
- Candidate C performs well in typical scenario (Case 1) but is bypassed by AI in adversarial scenario (Case 3)
- Candidate A performs consistently but has no standout advantages
```

#### Step 5: User Confirmation

User selects top-1 (or accepts recommendation), proceed to Gate Six.

**If highest ELO < 1250**: Indicates all candidate quality is insufficient, return to Gate Three to rewrite problematic sections, then re-run ELO.

**If highest ELO ≥ 1400**: Indicates candidate quality significantly exceeds baseline, auto-recommend.

---

### Gate Six · Wrap-Up & Delivery

**Light tier**: Execute 4-item wrap-up checklist (first 4 items).

**Medium / Heavy tier**: Execute 8-item wrap-up checklist. **Heavy tier** additionally adds test cases + regression verification.

---

## Execution Protocol

### Search Preloading

```
User answers Q_n
  ↓
Extract keywords + predict Q_{n+1} topic
  ↓
Search (all modes, all gates must search)
  ↓
Result processing:
  ├─ Deterministic answer (≥3 sources agree / official docs / industry standard) → auto-adopt, summarize at end
  ├─ Multiple options → organize as choices + recommendation marker
  ├─ Code / templates → use as fill-in templates
  └─ No valid results → ask questions normally
```

### Deterministic Skip Rules

- ≥3 independent sources agree → deterministic answer, auto-adopt
- Official documentation (e.g., Anthropic/OpenAI official guides) explicitly recommends → auto-adopt
- Industry standard format (e.g., REST API must include status code) → auto-adopt
- All auto-adopted items, summarized and confirmed at Gate Six

### Interaction Protocol

- ≤4 questions per round, batch if exceeding
- Present 「Search Findings」 summary (1-3 items) before questions
- Present 「This Gate's Output」 summary at the end of each gate
- Multiple choice questions include recommendation marker + explanation; fill-in questions provide 2-3 examples

**Non-programmer friendly** (Standard mode focus): Options in plain language, technical solutions use "solution name + one-sentence summary + applicable scenario," code includes comments.

---

## Wrap-Up & Delivery

### 8-Item Wrap-Up Checklist (Medium/Heavy full; Light first 4 items only)

- [ ] 1. Anti-ambiguity verification passed (Light: 9 items / Medium-Heavy: 18 items)
- [ ] 2. No AIGC metadata residue ("as an AI language model" etc. — check line by line)
- [ ] 3. Token efficiency check (no redundant repeated expressions, each section's responsibility does not overlap)
- [ ] 4. Format consistency (heading levels / list styles / code block language tags unified)
- [ ] 5. Auto-filled items summary confirmation
- [ ] 6. Deviation explanation from user's original intent (if any)
- [ ] 7. ELO ranking results attached (with complete PK records)
- [ ] 8. Version number + date + change summary

### Output Document Structure

```markdown
# [Prompt Title] v1.0

## Meta Information
- Target AI / Prompt Type / Mode / Creation Date / ELO Score

## Role Definition
[Precise role + capability boundaries (can/cannot do)]

## Task Description
[What specifically to do + how to do it + numbered steps]

## Input Specification
[Input format + 2-3 examples]

## Output Specification
[Output format + complete schema + 2-3 examples + judgment criteria]

## Execution Constraints
[Hard constraints + soft constraints + boundary checklist (only do / do not do)]

## Examples
[2-3 complete input → output example pairs]

## Anti-Ambiguity Statement
[This prompt has passed 18-item anti-ambiguity verification, verification date: YYYY-MM-DD]

## Appendix
[Glossary + reference sources + ELO ranking records + change log]
```

---

## Iron Rules (violation = re-run)

| # | Rule | Why Non-Negotiable | Exception |
|---|------|--------------|------|
| 1 | Deterministic questions must not be asked → auto-adopt + summarize at end | Asking when industry standards exist = wasting user's time | None |
| 2 | Every section must pass anti-ambiguity check → cannot proceed to next section without passing | Core quality assurance | Light tier only checks first 9 items |
| 3 | No empty assertions allowed → must scan text and verify | Model will skip reading draft and directly assert "yes" | None |
| 4 | ELO must run all candidate pairs → no skipping pairs | Skipping pairs = ranking distortion | Light tier skips ELO |

---

## Degradation & Exceptions

- Search unavailable → ask questions normally, mark "not searched, for reference only"
- User aborts mid-process → preserve current draft + progress
- User input too vague → Gate Zero asks one more round (≤4 questions)
- ELO highest score < 1250 → return to Gate Three to rewrite problematic sections (Light tier not applicable)
- User is senior engineer → use Review mode
- Light tier project user adds complexity after Gate Zero → upgrade to Medium/Heavy, re-run differential items for passed gates

---

## Maintenance Obligations

| Trigger | Action |
|------|------|
| User modifies requirements | Return to corresponding gate, re-run, cascade-update subsequent gates |
| ELO ranking discovers new misinterpretation | Supplement to prompt constraint section, simultaneously update anti-ambiguity checklist |
| New terminology added | Supplement to appendix glossary |
| Output format changed | Re-run Gate Four anti-ambiguity verification |
| Target AI changed | Re-run Gate Zero search (different AI has different best practices) |
| Companion super-spec | Use prompt document as super-spec input |

---

## Reference Patterns (Battle-Tested)

The following are good practices validated from real projects. **Not mandatory to follow, but proven effective approaches.**

### Interaction Rhythm Reference

| Gate | Typical Question Count | Rhythm |
|------|----------|------|
| Zero · Intent Anchoring | 3-4 questions | Quick lock-in — mostly multiple choice, 1 fill-in |
| One · Role & Boundaries | 3-4 questions | Search-driven — options sourced from search results |
| Two · Structure Skeleton | 1-2 questions | Confirmation-oriented — recommend skeleton + user adjusts |
| Three · Section-by-Section Forging | 1-2 questions per section | Draft + confirm — each section includes anti-ambiguity check result |
| Four · Anti-Ambiguity Verification | 0-2 questions | Auto-oriented — only fix items need user confirmation |
| Five · ELO Ranking | 1 question | Auto-oriented — present ranking table + user confirms top-1 |
| Six · Wrap-Up & Delivery | 1 question | Summary confirmation — auto-filled items + deviation explanation |

**Total interaction rounds**: 4-7 rounds (simple) / 7-12 rounds (complex), ≤4 questions per round.

### Search Injection Demonstration

Good search injection — options have source + explanation + recommendation:

```
Search findings:
- Anthropic official recommendation: Claude system prompts should define role first, then task
- High-star GitHub project tip: code review agents should include "do-not-do list" to prevent overreach

Q1: What role should the AI play?
  A) Senior Code Reviewer: focus on logic + security + maintainability ← Recommended (broad coverage, source: Anthropic guide)
  B) Security Audit Specialist: focus only on security vulnerabilities (source: OWASP Code Review Guide)
  C) Performance Optimization Specialist: focus only on performance issues
  D) Other: ____
```

Bad search injection — options have no source or explanation:

```
Q1: What role does the AI play?
  A) Code Reviewer
  B) Security Auditor
  C) Performance Optimizer
```

### Anti-Ambiguity Fix Demonstration

```
Before fix (❌ ambiguous):
"Output a concise code review report, including issue description and fix suggestion"

After fix (✅ unambiguous):
"Output a code review report in Markdown table format with 4 columns:
  | Severity | Location | Issue Description | Fix Suggestion |
  
  Requirements:
  - Severity uses P0 (blocking) / P1 (serious) / P2 (suggestion) three levels
  - Location must include filename + line number (e.g., main.py:42)
  - Issue description ≤2 sentences, must explain why it's an issue
  - Fix suggestion must provide specific code or clear steps"
```

### ELO Ranking Demonstration

```
ELO Ranking Results (3 candidates × 3 test cases = 9 PK rounds):

┌──────────┬────────┬─────────────────────────────────────────────┐
│ Rank     │ ELO    │ Candidate                                    │
├──────────┼────────┼─────────────────────────────────────────────┤
│ 🥇 1st   │ 1285   │ Candidate B (Optimized)                      │
│ 🥈 2nd   │ 1160   │ Candidate A (Conservative)                   │
│ 🥉 3rd   │ 1155   │ Candidate C (Minimalist)                     │
└──────────┴────────┴─────────────────────────────────────────────┘

PK Detailed Records:

Candidate A vs Candidate B:
  Case 1 (typical): A's output is standardized but stiff, B's output is natural and precise → B wins
  Case 2 (boundary): A's output is verbose, B's output is concise and on-point → B wins
  Case 3 (adversarial): A is bypassed, B successfully defends → B wins

Candidate A vs Candidate C:
  Case 1 (typical): A is complete but verbose, C is minimalist but omits → A wins
  Case 2 (boundary): A is too conservative, C is flexible but vague → Draw
  Case 3 (adversarial): A partially defends, C is bypassed → A wins

Candidate B vs Candidate C:
  Case 1 (typical): B is precise, C omits key constraints → B wins
  Case 2 (boundary): B is robust, C over-simplifies → B wins
  Case 3 (adversarial): B fully defends, C is bypassed → B wins

Recommendation: Candidate B (Optimized), ELO 1285, 3 wins out of 3.
```

### Auto-Fill Summary Demonstration (Gate Six)

```
Auto-filled items (auto-adopted per industry standards, please confirm):

| # | Filled Item | Adopted Value | Source | Reason |
|---|--------|--------|------|------|
| 1 | Role definition order | Role before task | Anthropic official guide | 3 independent sources agree |
| 2 | Output includes line numbers | Yes | OWASP Code Review Guide | Industry standard |
| 3 | Error severity levels | P0/P1/P2 three levels | Universal defect severity standard | ≥3 sources agree |

The above 3 items have been auto-filled. Please let us know if modifications are needed.
```

---

## Change Log

- **v1.0** (2026-07-23):
  - Seven-gate guided interaction + web search preloading + 18-item anti-ambiguity system
  - Three input modes: Standard / Review / Heavy-Duty + Fast Track
  - Output complexity tiers (Light / Medium / Heavy), orthogonal to input modes
  - Seventh design principle: output on demand, no excess, no shortfall
  - Heavy tier additional probing: networking / multiplayer / scale / real-time sync
  - ELO multi-candidate ranking system, integrated from gpt-prompt-engineer (MIT license)
  - Multi-candidate generation strategy, bidirectional scoring to eliminate position bias
  - Gates 4/5/6, Iron Rules, wrap-up tiered by output complexity
  - Degradation & exception handling: including Light tier upgrade scenarios
