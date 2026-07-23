# Super-Prompt v2.1: Precision Prompt Forging

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Standard: Agent Skills](https://img.shields.io/badge/Standard-Agent%20Skills-6e3ef7.svg)](https://agentskills.io)
[![GitHub stars](https://img.shields.io/github/stars/wlj103/super-prompt?style=social)](https://github.com/wlj103/super-prompt)

> 🎯 **The prompt engineering tool that prevents AI from misunderstanding you.** Anti-Ambiguity Interception × Web Pre-Search × Six-Tier Adaptive Grading × Information Completeness Simulation — turn a single sentence or a product document into a **production-grade prompt that AI cannot misinterpret**.

<p align="center">
  <b>Install:</b> <code>npx skills add wlj103/super-prompt</code> &nbsp;|&nbsp;
  <b>Trigger:</b> "write me a prompt" / "optimize my prompt" / "forge a prompt"
</p>

## Table of Contents

- [How It Works](#how-it-works)
- [The Problem with Prompt Engineering](#the-problem-with-prompt-engineering)
- [What is Super-Prompt?](#what-is-super-prompt)
- [Who Is This For?](#who-is-this-for)
- [Quick Start](#quick-start)
- [Features](#features)
- [Design Principles](#design-principles)
- [How It Compares](#how-it-compares)
- [super-spec × super-prompt](#super-spec--super-prompt)
- [FAQ](#faq)
- [License](#license)

## How It Works

When you say "write me a prompt," Super-Prompt doesn't just start writing — it runs a structured pipeline:

```
Your input → [Step 1: Six-Tier Grading] → picks the right funnel depth
         → [Step 2: Requirements Funnel] → digs into what you actually need
         → [Step 3: Completeness Simulation] → finds gaps before writing
         → [Step 4: Seven Gates] → locks down every ambiguity
         → [Step 5: Multi-Format Delivery] → prompt + visuals + docs
```

### Step 1: Six-Tier Input Grading

Not all users are the same. Super-Prompt auto-classifies your input and adapts:

| Tier | What You Say | What Happens |
|------|-------------|--------------|
| **① One-liner** | "Write me a prompt" (no context) | Full four-layer requirements funnel |
| **② Missing params** | Has direction, missing key details | Streamlined: problem discovery + assumption deconstruction |
| **③ Clear requirement** | 200-500 word description, logically coherent | Confirm → Simulate gaps → "Which gaps to fill?" |
| **④ Diagnostic** | "Review this prompt for issues" | Direct 18-item anti-ambiguity scan |
| **⑤ Existing prompt** | Brings a prompt to optimize | Review mode + completeness simulation |
| **⑥ Complete document** | Full PRD / spec / structured doc | Review mode + completeness simulation |

**Key principle**: For professional users (tiers ③⑤⑥), the deeper funnel is always *offered*, never forced.

### Step 2: Four-Layer Requirements Funnel (Tiers ①②)

For vague or incomplete needs, Super-Prompt uses a requirements mining funnel that fuses five industry methodologies:

| Layer | Method | What It Does | Industry Foundation |
|-------|--------|-------------|---------------------|
| **1. Problem Discovery** | STAR Model | Asks "what problem did you encounter?" not "what do you want?" | Customer Discovery (Steve Blank) |
| **2. Assumption Deconstruction** | 5 Whys | Every user statement is a hypothesis, not a fact. "I want X" → "Why?" → dig to root need | 5 Whys (Toyota), Socratic Questioning |
| **3. Body Mining** | Pointer Analysis | External pointers (URLs/screenshots) → open and analyze; internal pointers (vague words) → expand via questioning | Needfinding (Stanford d.school) |
| **4. Gap Discovery** | Hypothesis Map | Verified vs Assumed vs Inherited → cross-reference → gap questions | Socratic Questioning, Funnel Questioning |

**Core premise**: Users don't say what they need — they say what they think the solution is. Every word is a pointer, not the requirement body.

**Validated results**: 
- Chinese calendar widget: coverage 15% → 100% (16/16 requirements found)
- Pomodoro timer: 3/8 → 8/8
- Knowledge management: 3/14 → 14/14
- **v2.1 calendar widget (280 words, tier ③)**: 4-layer funnel → completeness simulation → 3 gaps surfaced → user filled 1 → full prompt. "Better than I expected."

### Step 3: Information Completeness Simulation (Tiers ③⑤⑥)

Before writing a single prompt word, Super-Prompt simulates a dry run and reports gaps with three markers:

| Marker | Meaning | Example |
|--------|---------|---------|
| ✅ **Confirmed** | User said it, no need to ask | "磨砂半透明" (frosted translucent) |
| ⚠️ **Guessing** | Agent can guess but shouldn't; guessing wrong = failure | Zoom behavior, weather API, highlight style |
| ❌ **Missing** | Can't run without it; must fill | Font licensing, holiday data source |

The ⚠️ marker is the innovation: the agent *can* guess many things, but guessing = gambling. This forces assumptions to surface as explicit questions.

### Step 4: Seven Gates

Every prompt passes through seven sequential gates. No skipping, no "good enough."

| Gate | What It Does | What It Prevents |
|------|-------------|------------------|
| **G0: Intent Anchoring** | Classifies input into six tiers, picks the right funnel depth | Building a prompt for the wrong problem |
| **G1: Role & Boundaries** | Defines AI role, input/output format, hard/soft constraints | Role ambiguity, scope creep, format mismatch |
| **G2: Structure Skeleton** | Recommends prompt section structure; user confirms | Disorganized prompts with overlapping responsibilities |
| **G3: Section-by-Section Refinement** | Drafts each section, runs anti-ambiguity check before moving to next | Vague terms like "appropriate," "good," "reasonable" |
| **G4: Anti-Ambiguity Audit** | 18-item checklist, item by item; no empty "pass" | Ambiguity residues that survived earlier gates |
| **G5: Adversarial Test** | Simulates 3 ways AI could misinterpret key instructions | Prompts that work in testing but fail on edge cases |
| **G6: Delivery** | Final prompt + Quick Reference Card + maintenance obligations | Deploying a prompt without knowing how to maintain it |

Web search runs throughout all gates — every question is backed by domain knowledge, not assumptions.

### Step 5: Multi-Format Output

**Not just text.** When the prompt involves workflows, architectures, or data flows, Super-Prompt generates supplemental outputs:

| Scenario | Output |
|----------|--------|
| Decision trees / branching logic | Flowcharts (Draw.io / Mermaid) |
| System architecture | Architecture diagrams |
| Data flows / processing pipelines | Data flow diagrams |
| Concept relationships | Mind maps |
| Data comparison / statistics | Charts (bar, pie, line) |
| Demo / presentation needs | Podcast audio or video |
| Formal delivery | .docx / .pptx / PDF |

**Principle**: If plain text isn't enough, supplement with visuals, documents, audio, or links.

---

## The Problem with Prompt Engineering

**Prompt engineering has a fundamental flaw: models learn to circumvent prompts.** You say "enforce strict verification," and the model outputs four words: "Verification enforced successfully." You say "be detailed," and it writes 3 lines of fluff. You say "use JSON format," and it freely invents field names. You say "don't hallucinate," and it hallucinates with extra confidence.

This isn't a model intelligence problem — it's a **prompt discipline problem**. Traditional templates give you the *what* but not the *how*. They tell you to "be specific" without telling you what specific means, or how to verify it before the model runs.

**Super-Prompt is the missing layer.** It doesn't just help you write prompts — it forces you through a structured, evidence-backed process that leaves no ambiguity for the AI to exploit.

## What is Super-Prompt?

Super-Prompt is a **prompt engineering framework and optimization tool** designed as an [Agent Skills](https://agentskills.io) skill. It's not a template, not a fill-in-the-blank sheet — it's a **complete prompt discipline system** that:

- 🔍 **Pre-searches the web** before you write a single word, so your prompt is backed by domain knowledge
- 🧠 **Simulates information completeness** before drafting — finds gaps with ✅⚠️❌ markers so you choose what to fill
- 🛡️ **Runs 18 anti-ambiguity checks** that systematically lock down every path the AI could misinterpret
- ⚔️ **Adversarially tests** key instructions by simulating 3 ways AI could misinterpret them
- 📋 **Produces a Quick Reference Card** with maintenance obligations, degradation handling, and exception protocols

The result: **prompts that work the first time** — whether you're writing a one-line classifier, a 500-line agent system prompt, or a multi-agent SOP.

## Who Is This For?

| You are... | Super-Prompt helps you... |
|---|---|
| **AI/LLM Engineer** | Ship production-grade system prompts with built-in validation and anti-hallucination guards |
| **Claude Code / Cursor / Copilot user** | Stop wasting tokens on vague instructions; get precise, verifiable agent instructions |
| **Prompt Engineer** | Replace guesswork with structured anti-ambiguity checks and adversarial testing |
| **Solo Developer** | Get the quality of a team code review through automated anti-ambiguity checks |
| **Technical Writer** | Convert product requirements into structured, unambiguous AI instructions |
| **AI Agent Builder** | Design agent system prompts that handle edge cases, degradation, and exceptions |

## Quick Start

```bash
npx skills add wlj103/super-prompt
```

Then trigger with any of these:

- "write me a prompt"
- "optimize my prompt"  
- "forge a prompt"

## Features

### 🎯 Six-Tier Adaptive Grading
Super-Prompt classifies your input into six tiers — from one-liners to complete PRDs — and adapts the funnel depth accordingly. Professional users get professional treatment: the four-layer funnel is offered, never forced.

### 🧠 Information Completeness Simulation
Before writing a single prompt word, Super-Prompt simulates a dry run of your requirement and reports gaps with three markers: ✅ Confirmed, ⚠️ Guessing (agent can guess but shouldn't), ❌ Missing. No more "does this look right?" — you get a structured gap report and choose what to fill.

### 🔍 Web Pre-Search Engine
Before asking you a single question, Super-Prompt searches the web for domain-specific knowledge, industry best practices, known edge cases, and common pitfalls. Your prompt is backed by evidence, not assumptions.

### 🛡️ 18-Point Anti-Ambiguity Checklist
The most comprehensive anti-ambiguity system in any prompt tool. Four categories: semantic vagueness, structural gaps, boundary ambiguity, and hidden assumptions. Each of the 18 items requires evidence — no checkbox theater.

### ⚔️ Adversarial Testing
Before delivery, Super-Prompt simulates 3 ways the AI could misinterpret your key instructions. Each weak point is hardened before you ship.

### 📋 Quick Reference Card
Every prompt ships with a maintenance card that includes degradation scenarios, exception handling protocols, update frequency recommendations, and known failure modes.

### 🌐 Bilingual Support
Full Chinese and English support. SKILL.md, README, CHANGELOG, and CONTRIBUTING are all available in both languages.

### 🔌 Agent Skills Compatible
Built as an [Agent Skills](https://agentskills.io) skill. Works with any Agent Skills-compatible AI coding assistant, including Claude Code, Cursor, and Coze.

## Design Principles

1. **Pre-search, don't guess** — Every question backed by web search; results converted into options for injection
2. **Layered guidance, not interrogation** — ≤4 questions per round, starting from the simplest mandatory questions
3. **Anti-ambiguity, not assumption** — 18-item checklist, systematically lock every ambiguity path
4. **Evidence-driven, not opinion-driven** — Design decisions backed by search evidence or industry standards
5. **Adversarially tested, not "looks good"** — Simulate AI misinterpretations before shipping
6. **Deliver with insurance** — Quick Reference Card + maintenance obligations + degradation and exception handling
7. **Output on demand, not over-deliver** — Never skimp, never bloat; safety margin only increases, never decreases

## How It Compares

| Feature | Super-Prompt | Promptfoo | dair-ai Guide | orbit-prompt |
|---|---|---|---|---|
| **Approach** | Structured prompt discipline | Prompt testing framework | Educational guide | Claude Code skill |
| **Anti-ambiguity** | ✅ 18-item checklist | ❌ | ❌ | ❌ |
| **Web pre-search** | ✅ Built-in | ❌ | ❌ | ❌ |
| **Adversarial testing** | ✅ Simulated misinterpretations | ✅ CI-integrated | ❌ | ❌ |
| **Production output** | ✅ Prompt + QRC + maintenance | ❌ Test results only | ❌ | ❌ |
| **Best for** | Writing precise prompts | Testing existing prompts | Learning prompt engineering | Quick Claude Code prompts |

## super-spec × super-prompt

Super-Prompt is the upstream of [super-spec](https://github.com/wlj103/super-spec). The flow is:

```
User need → [super-prompt] → precise prompt document → [super-spec] → 5 engineering docs → delivery
```

| | super-prompt | super-spec |
|---|---|---|
| **Comes first** | ✅ Defines what to do and how to say it | Takes the prompt and breaks it into engineering docs |
| **Problem** | AI expresses vaguely, lacks structure, leaves ambiguity | AI skips steps, claims success with zero evidence |
| **Solution** | Prompt discipline — 7 gates, 18 anti-ambiguity items, adversarial testing | Engineering discipline — 7 gates, 5 documents, anti-corner-cutting |
| **Domain** | How agents **should express** | How agents **should execute** |

Together: **prompt defines the contract, spec enforces the execution.**

## FAQ

### How is this different from a prompt template?
Templates give you a structure to fill in. Super-Prompt gives you a **process** — it actively searches, checks, tests, and validates. A template won't tell you your prompt is ambiguous; Super-Prompt's 18-item checklist will.

### Does this work with Claude? GPT? Other models?
Yes. Super-Prompt is **model-agnostic**. The prompt discipline principles apply to any LLM — Claude, GPT, Gemini, Llama, or local models.

### Can I use this for agent system prompts?
Yes — that's the Heavy mode. It's designed for complex agent instructions, multi-agent SOPs, and production-grade system prompts.

### What's the Quick Reference Card?
A one-page maintenance document that ships with every prompt. It tells you when the prompt might degrade, how to detect it, and what to do about it.

### Is this free?
Yes. MIT licensed, open source, free forever.

### Can I contribute?
Absolutely. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines. We welcome prompt patterns, anti-ambiguity item suggestions, and adversarial testing improvements.

## License

MIT © 2026