---
name: "super-prompt"
description: "Prompt engineering tool: anti-ambiguity interception × web pre-search × layered guidance × seven gates, from one sentence to production-grade prompts. Suitable for Claude/GPT/Agent system prompts, SOPs, Agent instructions. Supports multi-format delivery: flowcharts, architecture diagrams, mind maps, podcasts, documents, etc. Trigger words: write prompt, refine prompt, optimize prompt, write system prompt."
license: MIT
---

# Super-Prompt v2.2

## Security Declaration

| Dimension | Status |
|-----------|--------|
| Asset Type | Documentation-only |
| Network Requests | Search only (user-visible) |
| System Commands | None |
| File Deletion | Workspace only |
| External Dependencies | None |
| Data Collection | None |
| Security Level | Safe |

**Make every instruction AI receives precise and unambiguous—not "good enough."**

## The Problem

Prompt engineering has a fundamental flaw: **models learn to bypass prompts.** You say "enforce verification," it outputs four words: "enforce verification passed." You say "detailed explanation," 3 lines of filler counts as detailed. You say "use JSON format," it freely invents field names.

This isn't the model lacking intelligence—it's the model being too smart. It learns to satisfy literal requirements with minimal cognitive cost while bypassing true intent.

Super-Prompt is not a template, not a fill-in-the-blank form—it's a **complete prompt discipline system**. Through seven-gate guided interaction + web search preloading + anti-ambiguity verification, it helps users refine a single sentence or product document into a **production-grade prompt that AI cannot misinterpret**.

## What Makes This Different

| Other Prompt Tools | Super-Prompt |
|-------------------|-------------|
| "Write a prompt" | Seven gates must be passed; no skipping |
| Trusts user expressed clearly | **Anti-ambiguity clauses**: 18-item checklist scanned line by line; passing empty forbidden |
| User judges quality themselves | Gate 5: Adversarial testing, simulating 3 paths AI might misinterpret |
| "Looks fine" | Evidence-driven: every design decision backed by search evidence or industry standards |
| One-shot questioning | Layered guidance: <=4 questions per round, starting from simplest mandatory questions, deepening layer by layer |
| Makes user think of answers themselves | Web search preload: search before every question, convert results into options injected into questions |

Super-Prompt is the only prompt engineering system that **systematically classifies how models misinterpret instructions** and creates **locking methods** for each misinterpretation path.

### How Models Circumvent Prompts

| You Say | It Understands As | Why It's Dangerous |
|---------|-------------------|-------------------|
| "Describe concisely" | 3 lines of filler counts as concise | Model picks minimal cognitive cost path |
| "Use JSON format" | Field names? Nesting? Optional? Doesn't matter | Model freely invents; downstream parsing fails |
| "Handle exceptions" | Only writes try-catch, not what to handle | Form-text validation, actually useless |
| "Professional tone" | PhD-level or entry-level? Guess one | Audience mismatch, message can't land |
| "Handle appropriately" | What's appropriate? Whatever | Undeterminable, unverifiable |
| "High quality" | Self-assessed pass | Undeterminable, equals saying nothing |
| "Include relevant features" | What's relevant? Free rein | Scope creep, delivery out of control |
| "Be concise but complete" | Contradictory instruction, random tradeoffs | Either incomplete or not concise |

## Relationship with super-spec

- **super-spec** = Engineering discipline (can we not skip steps, can we produce evidence, can we be cross-document self-consistent)
- **super-prompt** = Prompt discipline (is expression precise, is structure clear, is ambiguity locked down)

```
User need -> [super-prompt] -> High-quality prompt doc -> [super-spec] -> Five engineering documents -> Delivery
```

spec governs discipline, prompt governs expression. Two swords as one.

---

## Quick Reference Card (Agent must read before execution)

### Three Modes

Gate 0 determines intent then auto-assigns mode; user confirms:

| Mode | User Profile | Input | Process | Interaction |
|------|-------------|-------|---------|-------------|
| Standard | Non-programmer / no docs | One sentence / vague need | Full search -> guided per gate | Per-gate multiple choice |
| Review | Senior / has complete plan | PRD / business doc / prototype | Auto full pre-search -> batch optimization points -> select deep-dive -> Gates 3-6 | Batch present points, user selects |
| Heavy | Team / multi-Agent | Complex engineering docs | First ask "compare with web?" -> if yes, pre-search benchmark -> full seven gates + adversarial x2 | Break down and confirm each section |

### Search Rules (All Modes Universal)

**Search before every gate.** Search is core value, not burden. Standard mode users have no docs and need search to provide options even more.

Search degradation: Search unavailable -> normal questioning, mark "unsearched, for reference only."

### Non-Skippable Checkpoints

1. Gate 3: Every section must pass anti-ambiguity check
2. Gate 4: Must actually scan text; filling "Yes" empty is forbidden
3. Gate 6: 8-item cleanup checklist verified item by item

## Six Design Principles

| # | Principle | Counterexample (How model swaps in "good enough") |
|---|-----------|---------------------------------------------------|
| 1 | Lock semantics, not creativity | "Concise" unquantified -> 3 lines or 30 lines both okay |
| 2 | Structural verification, not trust expression | Saying "include error handling" -> only writes try-catch, not what to handle |
| 3 | Layered guidance, not one-shot | Dumping 20 questions at once -> user overwhelmed / fills randomly |
| 4 | Evidence-driven, not feeling-driven | "I think this is good" -> no search evidence backing |
| 5 | Probe-driven, not hardcoded | Assuming user's tech stack -> doesn't match reality |
| 6 | Ambiguity acceptance, not trust acceptance | "Looks fine" -> 18-item checklist not passed |

---

## Anti-Ambiguity System

### Four-Type Anti-Ambiguity Clauses

**A. Semantic Vagueness (Laziness Hotspot)**

| You Say | How Model "Good-Enough"s It | Lock Method |
|---------|---------------------------|-------------|
| "Describe concisely" | 3 lines of filler counts as concise | Specify line limit: "max 5 lines" |
| "Detailed explanation" | 10 lines or 100 lines both count as detailed | Specify line floor or paragraph structure |
| "Professional tone" | PhD-level or entry-level? Guess one | Define audience + terminology level |
| "Handle appropriately" | What's appropriate? Whatever | Give concrete value or conditional branch |
| "High quality" | Undeterminable, self-assess pass | Give verifiable judgment criteria |

**B. Structural Deficiency**

| You Say | How Model "Good-Enough"s It | Lock Method |
|---------|---------------------------|-------------|
| "Use JSON format" | Field names? Nesting? Optional? Doesn't matter | Give complete schema with examples |
| "Handle exceptions" | Only writes try-catch, not what to handle | List exception types + respective handling |
| "Write tests" | Test what? What's the pass criteria? | Give test case list + pass conditions |
| "Optimize performance" | Optimize what? To what degree? | Give concrete metrics + target values |
| "Add comments" | Comment what? How detailed? | Give commenting rules |

**C. Boundary Ambiguity**

| You Say | How Model "Good-Enough"s It | Lock Method |
|---------|---------------------------|-------------|
| "Include relevant features" | What's relevant? | Explicitly list, narrow with "only do the following" |
| "Not too many" | How many is too many? | Give upper limit number |
| "Can extend if needed" | Who judges "needed"? | Give judgment condition -> trigger action |
| "Reference best practices" | Which practices? | List specific sources or search links |
| "Be concise but complete" | Contradictory instruction | Decompose: what must be complete -> what can be concise |

**D. Implicit Assumptions**

| You Assume | Model Doesn't Know | Lock Method |
|-----------|-------------------|-------------|
| Knows target user | Model guesses audience wrong | Explicitly write user persona |
| Knows tech stack | Model uses something else | Explicitly lock language/framework/version |
| Knows output language | Model may use English | Explicitly specify language |
| Knows context | Model has no memory | Explicitly provide or reference |
| Knows constraints | Model freely improvises | Explicitly list hard + soft constraints |

### 18-Item Anti-Ambiguity Verification Checklist

**Must actually scan text; filling "Yes" empty is forbidden.**

| # | Check Item | Check Method | Fix Suggestion |
|---|-----------|-------------|----------------|
| 1 | Adjectives/adverbs quantified | Scan "concise/detailed/professional/appropriate/high quality" | Replace with concrete values or determinable criteria |
| 2 | Format requirements have complete schema | Check if "JSON/table/list" has field definitions | Supplement complete schema + examples |
| 3 | Role definition includes capability boundaries | Check if "You are X" has "can/cannot do" | Supplement capability boundary declaration |
| 4 | Error handling lists concrete types | Check if "handle errors/exceptions" are enumerated | List error types + respective handling |
| 5 | Test requirements have judgment criteria | Check if "write tests" has pass conditions | Supplement test cases + pass criteria |
| 6 | Performance requirements have concrete metrics | Check if "optimize/improve" has target values | Supplement "from X to Y" |
| 7 | Boundaries locked bidirectionally | Check if "only do/don't do" declaration exists | Supplement positive + negative lists |
| 8 | Input has examples | Check for input examples | Supplement 2-3 examples |
| 9 | Output has examples | Check for output examples | Supplement 2-3 examples |
| 10 | Terms have definitions | Scan for first occurrence of technical terms with definitions | Attach definition on first occurrence |
| 11 | Vague quantifiers replaced | Scan "appropriate/moderate/on-demand/as much as possible" | Replace with concrete values or conditions |
| 12 | Open instructions narrowed | Scan "if needed/can/try to" | Replace with "when X -> do Y" |
| 13 | Implicit assumptions made explicit | Scan "by default/of course/obviously" | Explicitly write the assumed content |
| 14 | Ambiguous references disambiguated | Scan "this/that/it/the above" | Replace with explicit referent |
| 15 | Steps have sequential numbering | Check if process has numbering | Supplement step numbers |
| 16 | Conditional branches complete | Check if if has else | Supplement else branch or explicitly "no else" |
| 17 | Constraints verifiable | Check if each constraint has judgment method | Supplement "verification method: X" |
| 18 | No contradictory instructions | Check for "concise but complete" / "fast but accurate" type | Decompose into layered constraints |

---

## Prompt Quality Four Elements (Quick Diagnostic Framework)

> Reference: promptify's four-element core contract. Not a replacement for seven gates—a quick positioning tool before the gates.

Before writing a prompt, ask yourself four questions:

| Element | Ask Yourself | Counterexample—What happens without this |
|---------|-------------|----------------------------------------|
| **Role** Role + domain expertise | Who does the AI play? What are the capability boundaries? | AI role wavers, output style unstable |
| **Task** Precise action | Specifically what? "Analyze" -> "List top 3 issues ordered by severity" | AI free-reins, output unpredictable |
| **Constraints** Hard constraints | Word count/format/forbidden items/boundaries | AI output too long, format messy, out of bounds |
| **Output** Output format | JSON/Markdown/plain text? Schema? | AI freely invents field names, downstream parsing fails |

### Diagnostic Five Questions (Reverse attribution after getting unsatisfactory AI output)

| # | Question | Symptom | Missing Element |
|---|---------|---------|-----------------|
| Q1 | Purpose unclear? | Output drifts, unrelated to expected direction | Task |
| Q2 | Audience/expertise unspecified? | Direction correct but depth wrong (too shallow / too deep) | Role |
| Q3 | Context missing? | Looks fine in isolation, but doesn't fit the overall scenario | Constraints |
| Q4 | Model knowledge boundary not considered? | AI confidently gives wrong answer | Task + Constraints |
| Q5 | Missing length/refinement constraints? | Too much filler or too terse | Constraints + Output |

**How to use**: Get unsatisfactory AI output -> locate issue via Five Questions -> targeted prompt fix. Lightweight tasks: Four Elements suffice; complex tasks: full Seven Gates pipeline.

---

## Proportional Complexity Principle

| Input Complexity | What to Use | Minimum Elements |
|-----------------|------------|-----------------|
| Simple (fact queries, rewrites) | Four Elements quick diagnosis | Role + Task |
| Medium (code review, report generation) | Four Elements + partial gates | Role + Task + Constraints + Output |
| Complex (system prompts, multi-Agent orchestration) | Full Seven Gates pipeline | Complete seven gates |

**Core**: Don't over-engineer. Simple problems don't add elements; complex problems don't skip steps.

## Seven Gates Pipeline

```
Input -> Gate 0·Intent Anchoring (mode assignment) -> Gate 1·Role & Boundaries -> Gate 2·Structural Skeleton
     -> Gate 3·Section-by-Section Refinement -> Gate 4·Anti-Ambiguity Verification -> Gate 5·Adversarial Testing -> Gate 6·Cleanup & Delivery
     -> Output (Production-grade prompt document)
```

| Gate | What It Blocks | Pass Condition | Interaction |
|------|---------------|----------------|-------------|
| 0·Intent Anchoring | Starting without knowing what's needed | Intent three elements confirmed + mode assigned | Multiple choice + fill-in |
| 1·Role & Boundaries | Role vague / boundaries unclear | Four elements confirmed | Multiple choice + search suggestions |
| 2·Structural Skeleton | Structure chaotic | Skeleton confirmed, each section has clear responsibility | Search -> recommend -> confirm |
| 3·Section Refinement | Expression imprecise | Each section passes anti-ambiguity check | Draft + confirm per section |
| 4·Anti-Ambiguity Verification | Residual ambiguity | 18-item checklist all green | Auto check + fix suggestions |
| 5·Adversarial Testing | Real-world usage failure | Key instructions pass AI testing | Auto test + report |
| 6·Cleanup & Delivery | Omissions | 8-item cleanup checklist all green | Auto check + confirm |

---

### Gate 0·Intent Anchoring

**Must search**: `"[domain] prompt engineering best practices"` + `"[target AI] system prompt guidelines"`

**Standard mode**: Use AskUserQuestion to ask <=4 questions (mainly multiple choice), confirm intent three elements -> confirm mode.

**Review mode**: User already has complete plan, skip questioning. Enter review process directly (see "Review Mode Workflow" below).

**Heavy mode**: First ask "Want to compare against web resources and see if there's optimization room?" Yes -> full pre-search benchmark (same as Review Mode Step 1-2); No -> directly enter Gate 1. Full seven gates + adversarial x2, confirm every section in detail.

#### Step 0: Product Understanding (Conditional Trigger)

**Trigger condition**: User input is product/feature requirement (e.g., "build a bookkeeping app," "help me write a customer service bot prompt"), not a direct prompt optimization request (e.g., "help me optimize this prompt").

**Why**: Requirements for small-to-medium projects are "talked out," not "thrown over." Skipping product understanding and going straight to classification results in precise prompt formatting but deviation from product essence.

**Core premise**: Every word from the user is a hypothesis, not a fact. User says "want semi-transparent" might mean "don't block background"—the real need is "non-obstructive." Don't ask "what do you want," ask "why." User says "want X" -> first ask "why X?" -> dig until you can't dig deeper; that's the real need.

**General rules**:
- **Ask only one question at a time**. User answers, then ask next. Don't dump multiple questions at once.
- **Each question comes with 1-2 concrete examples** to help user understand what this question is asking. Use plain language, no jargon.
- **Search before asking, share search results with user**. User may not have thought about it or may be vague; search results help open up thinking. E.g., before asking "what methods have you tried," search similar tools on the market first, tell user "there's A, B, C on the market—which have you used?"
- Guide with examples, don't prescribe with examples. No jargon.

---

**Layer 1: Gather Problems (STAR Model)**

Don't ask "what do you want," ask "what problem did you encounter." User is problem expert, Agent is solution expert. One question at a time, with examples.

1. **Situation**: "What was the most recent situation where you encountered this problem?"
   -> E.g.: *"Last week wanted to find an article you'd saved long ago, searched WeChat, browser bookmarks, Notes—couldn't find it anywhere?"*
2. **Target**: "What result were you trying to achieve?"
   -> E.g.: *"Were you trying to quickly find that article? Or organize what you've saved?"*
3. **Action**: "What methods have you tried? What tools have you used?"
   -> E.g.: *"Used WeChat Favorites? Notion? Feishu? Or just wrote it in Notes?"*
4. **Result**: "What's unsatisfying? What frustrates you the most?"
   -> E.g.: *"Is it that you can't search? Too messy? Too much hassle to save? Or always having to decide where to put things?"*

Purpose: Let user articulate the problem scenario, not design their own solution.

---

**Layer 2: Decompose Assumptions**

After receiving user responses, first judge each word: **Is this a problem description, or a solution hypothesis?**

| User Says | Type | Handling |
|-----------|------|----------|
| "Display date and lunar calendar and auspiciousness" | Solution hypothesis (UI elements they want) | Ask "Why auspiciousness?" -> dig to underlying need |
| "Nothing on the market matches what I want" | Problem description (unmet need exists) | Expand scenario details |
| "Data source is likuiming.com" | External pointer | Enter Layer 3 to open and analyze |
| "Frosted transparent black minimal" | Solution hypothesis (style they want) | Ask "Why this style?" |
| "Just for myself" | Constraint (user persona) | Confirm |

**Key**: Ask "why" until you can't go further. User says "want auspiciousness" -> "Why?" -> "Want to know if today is good for going out" -> that's the real need.

---

**Layer 3: Mine the Essence**

Handle by pointer type. Don't explain steps to user; just do it:

| Pointer Type | Mining Method | Example |
|-------------|--------------|---------|
| External pointer (URL/screenshots/reference apps) | Open and analyze the source -> cross-compare: what's in the source, what user didn't mention | Open likuiming.com, see what info the almanac has that user didn't mention |
| Internal pointer (vague words like "auspiciousness," "clock," "weather") | Ask "specifically what?" -> expand | "Auspiciousness specifically means what? Taboos? Clashes? Hourly auspiciousness?" |
| Solution-type expression ("want semi-transparent") | Ask "why?" -> behavioral verification "how did you do it before?" | "Why semi-transparent? Used similar before?" |
| Emotional cues ("frustrating," "unsatisfactory") | Ask "what frustrates you most?" | "What's most unsatisfying about what you've tried?" |

---

**Layer 4: Find the Delta (Assumption Map)**

Draw assumption map, three levels:

- **Verified**: User explicitly stated, or material definitely contains
- **Assumed**: You inferred from user description, but user hasn't confirmed
- **Inherited**: Industry defaults, common practices, you assume user also needs

Cross-compare -> delta questions -> benchmark object secondary judgment. Assumed + Inherited -> confirm with user item by item.

---

**Confirmation summary**: After user answers, summarize understanding in 1-2 sentences, get confirmation. Don't skip.

**Skip conditions** (Six-tier judgment, by user input quality):

| Tier | User Input Characteristics | Process |
|------|--------------------------|---------|
| One sentence only | "Write me a prompt," said nothing else | Full four-layer funnel: gather problems -> decompose assumptions -> mine essence -> find delta |
| Missing parameters | Has direction but missing key info (e.g., "build a bookkeeping app" without platform) | Streamlined gather+decompose, focus on mining essence to fill key info |
| Clear requirements | Complete description, logically self-consistent, understandable without follow-up (e.g., almanac 280 chars) | Confirm understanding, simulate information completeness (see rules below), then ask "what gaps to fill?" -> user points to what; says "no need" then continue Gate 0 |
| Diagnostic | "Check if this prompt has issues" | Directly run anti-ambiguity 18-item scan; no four-layer funnel |
| Existing prompt optimization | Brought an existing prompt to optimize | Review mode: full pre-search -> batch optimization points -> user selects. Also simulate information completeness -> ask "what gaps to fill?" |
| Complete document | Full PRD/plan/structured doc | Review mode full pre-search benchmark. Also simulate information completeness -> ask "what gaps to fill?" |

**Information completeness simulation rules** (Tiers 3, 5, 6 common):
After receiving requirements, don't write full prompt—just do a quick scan. Three categories:

| Mark | Meaning | Example |
|------|---------|---------|
| Confirmed | User said it, no need to ask | Frosted semi-transparent, auto-start on boot, display lunar calendar |
| Would guess | User didn't say, but Agent can guess—guessing wrong means failure, must ask | Zoom method (drag/preset?), weather data source, hour highlighting (highlight/color?) |
| Missing | User didn't say, Agent can't guess; missing means can't run | Holiday data source, font license |

Output "Information Completeness Report":

```
Confirmed: date format, lunar calendar, taboos, hourly auspiciousness, frosted semi-transparent, auto-start on boot
Would guess: (1) Zoom method (drag/preset? Agent will blindly guess) (2) Weather data source (which API?) (3) Hour highlighting method (highlight/color/border?)
Missing: digital clock position, font preference, holiday data source
```

After user sees it, point to what to fill. Says "no need" then continue current flow—but Would-guess items default to follow-up, Missing items must be filled.

**Core**: Don't make decisions for the user. What Agent can guess != what Agent should guess. 100-200 words, three seconds to scan.

#### Intent Three Elements That Must Be Confirmed

1. **What to do**: What is the prompt's target task?
2. **For whom**: Which target AI?
3. **What counts as success**: What output qualifies?

```
Search findings (example):
- Anthropic official recommendation: system prompt should define role first, then task
- 2025 prompt engineering trends: Chain-of-Thought + structured output

Q1: What is this prompt for?
  A) Code generation/review  B) Content creation/writing  C) Data analysis/processing  D) Workflow automation

Q2: Which target AI?
  A) Claude  B) GPT  C) Gemini  D) General

Q3: What counts as success? Fill in the blank:
  "When I give this prompt to the AI, the AI should be able to ____"

Q4: Any special constraints? (Can skip)
  A) Must support Chinese  B) Output has format requirements  C) Length limits  D) None
```

Produce "Intent Anchor Checklist" -> assign mode -> after user confirmation, enter Gate 1.

### Gate 1·Role & Boundaries

**Standard/Heavy**: Search `"[role] agent prompt examples"` + `"[domain] common pitfalls prompt"` -> multiple choice to confirm four elements.

**Review mode**: Skip.

#### Four Elements That Must Be Confirmed

1. **Role**: What does AI play? Capability boundaries?
2. **Input**: What will AI receive? Format?
3. **Output**: What should AI output? Format + judgment criteria
4. **Constraints**: Hard constraints + soft constraints + do-not-do list

### Gate 2·Structural Skeleton

**Standard/Heavy**: Search `"[prompt type] prompt structure template"` -> recommend structure -> user confirm.

**Review mode**: Skip.

Default structure: Role definition -> Task description -> Input spec -> Output spec -> Execution constraints -> Examples -> Appendix

---

### Review Mode Workflow

Trigger condition: User provides complete materials like PRD, business docs, prototypes, mature plans.

**Step 1: Full Pre-Search**

Search for benchmarks across all sections of user's plan at once:

```
Search matrix:
- Role definition -> "[role] agent prompt best practices 2025"
- Task description -> "[task type] prompt engineering patterns"
- Input spec -> "[input type] prompt input format examples"
- Output spec -> "[output type] structured output schema"
- Constraints/boundaries -> "[domain] prompt constraints best practices"
- Overall structure -> "[prompt type] production prompt template"
```

**Step 2: Batch Present Optimization Points**

Benchmark search results against user's plan, present all optimizable points at once:

```
Full pre-search findings (example):

Role Definition
  Your plan covers: role name + responsibility description
  Search reveals deeper options:
  - 87% of production-grade agent prompts include "capability boundary declaration" (can/cannot do)
  - Anthropic official recommendation: follow role definition with standalone "behavior constraints" section
  -> Want to deepen?

Output Spec
  Your plan covers: output format (JSON)
  Search reveals deeper options:
  - Industry standard: output spec should include complete JSON Schema + 2-3 examples
  - Common pitfall: just saying "JSON" without defining fields -> AI freely invents field names
  -> Want to deepen?

Error Handling
  Your plan does not cover
  Search reveals: 94% of similar prompts include error handling section
  -> Want to add?
```

**Step 3: User Selects Deep-Dive Items**

User checks which sections to deepen.

**Step 4: Expand Item by Item**

For each selected section: search -> draft -> anti-ambiguity check -> confirm.

**Step 5: After all deep-dive items complete, enter Gates 3, 4, 5, 6**

---

### Gate 3·Section-by-Section Refinement

**All modes**: Every section must pass anti-ambiguity check; if not, don't enter next section.

For each section in the structure: search -> draft -> anti-ambiguity check -> user confirm.

#### Section Iron Rules

| # | Rule | Why | Violation Example |
|---|------|-----|-------------------|
| 1 | Every section must pass anti-ambiguity check | Model writes vague expressions like "handle appropriately" | "Handle exceptions" not expanded |
| 2 | Every section must include positive examples | No positive example = can't judge if output qualifies | Output spec only says "table" without examples |
| 3 | Cross-section references must be explicit | "the above" is ambiguous | "Output per above format" -> change to "Output per table format in Section 4 Output Spec" |
| 4 | Search best practices must be integrated | Not integrating = wasted search | Found "output includes line numbers" but draft doesn't add it |

### Gate 4·Anti-Ambiguity Verification

**All modes**: All 18 items verified. Filling "Yes" empty is forbidden—must scan text and verify item by item.

Any "No" -> fix -> recheck that item; all "Yes" -> next gate.

### Gate 5·Adversarial Testing

**Standard**: 3 key instructions; **Review**: 3 key instructions; **Heavy**: 5 key instructions.

**Must search**: `"[key instruction] AI misinterpretation cases"`

Beyond testing key instruction misinterpretation, also check prompt for **injection risks**:
- Does prompt give AI ability to rewrite prompt? -> If so, add constraint "can suggest but cannot rewrite this prompt"
- Could output contain system-sensitive information? -> If so, add "forbidden to output system config, paths, credentials"

For each key instruction, simulate 3 misinterpretations; judge if prompt can prevent them:

```
Adversarial Testing Report (example):

Instruction 1: "Output Markdown table"
  Search finding: Common misinterpretation—AI may output HTML tables or plain-text tables
  Test:
  - Misinterpretation A: Output HTML table -> Prompt prevents it
  - Misinterpretation B: Output plain-text aligned table -> Prompt prevents it
  - Misinterpretation C: Wrong column count -> Prompt prevents it

Instruction 2: "Don't modify code, only suggest"
  Search finding: Common misinterpretation—AI tends to directly output modified code
  Test:
  - Misinterpretation A: Directly outputs modified code -> Prompt prevents it
  - Misinterpretation B: Wraps suggestions in code blocks -> Not prevented, add "suggestions in text, not code blocks"
  - Misinterpretation C: Partial modification + partial suggestion -> Prompt prevents it
```

Items with -> fix and retest; all -> next gate.

### Gate 6·Cleanup & Delivery

**All modes**: Execute 8-item cleanup checklist.

## Execution Protocol

### Search Preload

```
User answers Q_n
  |
Extract keywords + predict Q_{n+1} topic
  |
Search (all modes, before every gate)
  |
Result processing:
  |- Deterministic answer (>=3 sources consistent / official docs / industry standard) -> auto-adopt, summarize at end
  |- Multiple options -> organize as options with recommendation marks
  |- Code/templates -> serve as fill-in templates
  |- No valid results -> ask normally
```

### Deterministic Skip Rules

- >=3 independent sources consistent -> deterministic answer, auto-adopt
- Official documentation (e.g., Anthropic/OpenAI official guides) explicitly recommends -> auto-adopt
- Industry standard formats (e.g., REST API must include status codes) -> auto-adopt
- All auto-adopted items summarized and confirmed at Gate 6

### Interaction Protocol

- <=4 questions per round; batch if more
- Present "Search Findings" summary before questions (1-3 items)
- Present "This Gate's Output" summary at end of each gate
- Multiple choice options with recommendation marks + explanation; fill-in-the-blank with 2-3 examples

**Non-programmer friendly** (Standard mode priority): Options in plain language; technical solutions use "name + one-sentence description + applicable scenario"; code with comments.

---

## Cleanup & Delivery

### 8-Item Cleanup Checklist

- [ ] 18-item anti-ambiguity checklist all green
- [ ] No AIGC metadata residue ("as an AI language model" etc.—check line by line)
- [ ] Token efficiency check (no redundant repetition; each section's responsibility doesn't overlap)
- [ ] Format consistency (heading hierarchy / list style / code block language markers unified)
- [ ] Auto-filled items summary confirmed
- [ ] Deviation from user's original intent explained (if any)
- [ ] Supporting super-spec usage recommendation (if needs decomposition into engineering documents)
- [ ] Output format judgment: need non-text deliverables (diagrams/docs/audio/links) -> see "Output Format Expansion" below
- [ ] Version number + date + change summary

### Output Document Structure

```markdown
# [Prompt Title] v1.0

## Meta Information
- Target AI / Prompt type / Mode / Creation date

## Role Definition
[Precise role + capability boundaries (can/cannot do)]

## Task Description
[Specifically what to do + how to do it + numbered steps]

## Input Spec
[Input format + 2-3 examples]

## Output Spec
[Output format + complete schema + 2-3 examples + judgment criteria]

## Execution Constraints
[Hard constraints + soft constraints + boundary list (only do / don't do)]

## Examples
[2-3 complete input->output examples]

## Anti-Ambiguity Declaration
[This prompt has passed 18-item anti-ambiguity verification, verification date: YYYY-MM-DD]

## Appendix
[Glossary + References + Change log]
```

---

### Output Format Expansion

**Core principle: Give user intuitive feel.** Text is not the only delivery method. Before delivery, judge: is plain text intuitive enough? If not, supplement.

| Scenario | What to add beyond text | How |
|----------|----------------------|-----|
| Prompt involves decision trees / branching logic | Flowchart | Generate Draw.io diagram or Mermaid diagram, embed in doc or share link |
| Prompt involves system architecture / component relationships | Architecture diagram | Generate C4 architecture diagram or block diagram, embed in doc |
| Prompt involves data flow / processing pipelines | Data flow diagram | Generate flowchart or sequence diagram |
| Prompt involves concept relationships / knowledge structures | Mind map | Generate mind map |
| Prompt involves data comparison / statistics | Charts | Generate bar, pie, line charts, embed in doc |
| Prompt needs demo effect | Podcast / video | Generate podcast audio or video demo |
| Prompt involves external reference resources | Links | Directly share URL, one-click for user |
| Needs formal delivery to client / team | Documents | Generate .docx / .pptx / PDF with images as formal docs |

**Judgment flow**:
1. At Gate 6 cleanup, scan through prompt content
2. Ask yourself: can user intuitively understand from plain text?
3. If not -> determine which supplement form is needed -> generate -> deliver with text
4. If yes -> skip

**Professional user downgrade**: Review mode, or user input is structurally clear and logically self-consistent -> default to text-only prompt output. Don't proactively add diagrams, docs, audio. Unless user explicitly says "draw me a diagram," "make a document."

**Format rules**:
- Diagrams: generate image first, then embed in doc or share link directly
- Documents: use docx skill to generate .docx with images, or PPT skill for presentations
- Audio: use podcast to generate audio
- Links: share URL directly, no wrapping

---

## Iron Rules (Violation = Rerun)

| # | Rule | Why Non-Negotiable |
|---|------|-------------------|
| 1 | Deterministic questions MUST NOT be asked -> auto-adopt + final summary | Asking when industry standards exist = wasting user time |
| 2 | Every section must pass anti-ambiguity check -> if not, don't enter next section | Core quality assurance |
| 3 | Passing empty is forbidden -> must scan text and verify | Model will fill "Yes" without reading draft |

---

## Degradation & Exceptions

- Search unavailable -> ask normally, mark "unsearched, for reference only"
- User aborts mid-way -> preserve current draft + progress
- User input too vague -> Gate 0 ask one more round (<=4 questions)
- Adversarial testing all fails -> return to Gate 3, rewrite problematic sections
- User is senior engineer -> use Review mode

---

## Integration with super-spec

```
[super-prompt output: Prompt document]
  |
[super-spec decomposes into five engineering documents]
  |- CONSTITUTION.md  <- Constraints from prompt -> Constitution
  |- spec.md          <- Tasks from prompt -> Requirements
  |- tasks.md         <- Steps from prompt -> Tasks
  |- checklist.md     <- Judgment criteria from prompt -> Acceptance
  |- decisions.md     <- Design decisions from prompt -> Decisions
```

Simple prompts: super-prompt only; complex prompts: super-prompt refine -> super-spec decompose.

---

## Reference Patterns (Battle-Tested)

The following are good practices verified in real projects. **Not mandatory—just proven useful approaches.**

### Interaction Rhythm Reference

| Gate | Typical Questions | Rhythm |
|------|-----------------|--------|
| 0·Intent Anchoring | 3-4 questions | Quick lock—mainly multiple choice, 1 fill-in |
| 1·Role & Boundaries | 3-4 questions | Search-driven—options come from search results |
| 2·Structural Skeleton | 1-2 questions | Confirmation-focused—recommend skeleton + user adjusts |
| 3·Section Refinement | 1-2 per section | Draft + confirm—each section with anti-ambiguity check result |
| 4·Anti-Ambiguity Check | 0-2 questions | Auto-focused—only fixes need user confirmation |
| 5·Adversarial Testing | 0-2 questions | Auto-focused—only fixes need user confirmation |
| 6·Cleanup & Delivery | 1 question | Summary confirmation—auto-filled items + deviation explanation |

**Total interaction rounds**: 4-7 rounds (simple) / 7-12 rounds (complex), <=4 questions per round.

### Search Injection Demonstration

Good search injection—options have sources + explanation + recommendation:

```
Search findings:
- Anthropic official recommendation: Claude system prompts should define role first, then task
- High-star GitHub project tip: code review agents should include "do-not-do list" to prevent overreach

Q1: What role should AI play?
  A) Senior Code Reviewer: focuses on logic + security + maintainability <- Recommended (comprehensive coverage, source: Anthropic guidelines)
  B) Security Audit Expert: focuses only on security vulnerabilities (source: OWASP Code Review Guide)
  C) Performance Optimization Expert: focuses only on performance issues
  D) Other: ____
```

Bad search injection—options without sources or explanation:

```
Q1: What role should AI play?
  A) Code Reviewer
  B) Security Auditor
  C) Performance Optimizer
```

### Anti-Ambiguity Fix Demonstration

```
Before fix (ambiguous):
"Output a concise code review report, including issue descriptions and fix suggestions"

After fix (unambiguous):
"Output a code review report in Markdown table format with 4 columns:
  | Severity | Location | Issue Description | Fix Suggestion |
  
  Requirements:
  - Severity uses P0 (blocking) / P1 (serious) / P2 (suggestion) three levels
  - Location must include filename + line number (e.g., main.py:42)
  - Issue description <=2 sentences, must explain WHY it's an issue
  - Fix suggestion must provide concrete code or explicit steps"
```

### Auto-Fill Summary Demonstration (Gate 6)

```
Auto-filled items (adopted per industry standards, please confirm):

| # | Filled Item | Adopted Value | Source | Reason |
|---|------------|--------------|--------|--------|
| 1 | Role definition order | Role before task | Anthropic official guide | 3 independent sources consistent |
| 2 | Output includes line numbers | Yes | OWASP Code Review Guide | Industry standard |
| 3 | Error severity levels | P0/P1/P2 three levels | General defect severity standard | >=3 sources consistent |

Above 3 items auto-filled; please advise if changes needed.
```

---

## Maintenance Obligations

| Trigger | Action |
|---------|--------|
| User modifies requirements | Return to corresponding gate and rerun; subsequent gates cascade update |
| Adversarial testing discovers new misinterpretation | Supplement to prompt constraints section |
| New term added | Supplement to appendix glossary |
| Output format changes | Rerun Gate 4 anti-ambiguity verification |
| Target AI changes | Rerun Gate 0 search (different AI best practices differ) |
| Paired with super-spec | Use prompt document as super-spec input |
