# Super-Prompt v2.1: Precision Prompt Forging

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Standard: Agent Skills](https://img.shields.io/badge/Standard-Agent%20Skills-6e3ef7.svg)](https://agentskills.io)
[![GitHub stars](https://img.shields.io/github/stars/wlj103/super-prompt?style=social)](https://github.com/wlj103/super-prompt)

> 🎯 **The prompt engineering tool that prevents AI from misunderstanding you.** Anti-Ambiguity Interception × Web Pre-Search × Layered Guidance × ELO Ranking — turn a single sentence or a product document into a **production-grade prompt that AI cannot misinterpret**.

<p align="center">
  <b>Install:</b> <code>npx skills add wlj103/super-prompt</code> &nbsp;|&nbsp;
  <b>Trigger:</b> "write me a prompt" / "optimize my prompt" / "forge a prompt"
</p>

## Table of Contents

- [The Problem with Prompt Engineering](#the-problem-with-prompt-engineering)
- [What is Super-Prompt?](#what-is-super-prompt)
- [Who Is This For?](#who-is-this-for)
- [Quick Start](#quick-start)
- [How It Works](#how-it-works)
- [Features](#features)
- [Design Principles](#design-principles)
- [How It Compares](#how-it-compares)
- [super-spec × super-prompt](#super-spec--super-prompt)
- [FAQ](#faq)
- [License](#license)

## The Problem with Prompt Engineering

**Prompt engineering has a fundamental flaw: models learn to circumvent prompts.** You say "enforce strict verification," and the model outputs four words: "Verification enforced successfully." You say "be detailed," and it writes 3 lines of fluff. You say "use JSON format," and it freely invents field names. You say "don't hallucinate," and it hallucinates with extra confidence.

This isn't a model intelligence problem — it's a **prompt discipline problem**. Traditional prompt templates and guides give you the *what* but not the *how*. They tell you to "be specific" without telling you what specific means, or how to verify it before the model runs.

**Super-Prompt is the missing layer.** It doesn't just help you write prompts — it forces you through a structured, evidence-backed process that leaves no ambiguity for the AI to exploit.

## What is Super-Prompt?

Super-Prompt is a **prompt engineering framework and optimization tool** designed as an [Agent Skills](https://agentskills.io) skill. It's not a template, not a fill-in-the-blank sheet — it's a **complete prompt discipline system** that:

- 🔍 **Pre-searches the web** before you write a single word, so your prompt is backed by domain knowledge, not assumptions
- 🛡️ **Runs 18 anti-ambiguity checks** that systematically lock down every path the AI could misinterpret
- 🏆 **Uses ELO ranking** to pit multiple prompt candidates against each other, so you ship the best version — not the first version
- 📋 **Produces a Quick Reference Card** with maintenance obligations, degradation handling, and exception protocols

The result: **prompts that work the first time** — whether you're writing a one-line classifier, a 500-line agent system prompt, or a multi-agent SOP.

## Who Is This For?

| You are... | Super-Prompt helps you... |
|---|---|
| **AI/LLM Engineer** | Ship production-grade system prompts with built-in validation and anti-hallucination guards |
| **Claude Code / Cursor / Copilot user** | Stop wasting tokens on vague instructions; get precise, verifiable agent instructions |
| **Prompt Engineer** | Replace intuition with ELO-verified prompt ranking; never guess which prompt is better |
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

## How It Works

### Seven Gates

Super-Prompt guides you through seven sequential gates — each one must pass before moving to the next. No skipping, no "good enough."

| Gate | What It Does | What It Prevents |
|------|-------------|------------------|
| **G0: Product Understanding** | Four-layer funnel: STAR problem discovery → assumption deconstruction → body mining → hypothesis map gap analysis | Building a prompt for the wrong problem because the user said what they want, not what they need |
| **G1: Domain Search** | Searches the web for domain knowledge, best practices, known pitfalls | Missing critical context that the AI would otherwise hallucinate |
| **G2: Anti-Ambiguity Lock** | 18-item checklist scan, item by item; no empty "pass" | Vague terms like "appropriate," "good," "reasonable" that AI exploits |
| **G3: Structured Draft** | Mandatory sections, precise constraints, zero free-form fields | Free-form prompts that give AI too much creative freedom |
| **G4: Adversarial Test** | Simulates 3 ways AI could misinterpret; hardens weak points | Prompts that work in testing but fail on edge cases |
| **G5: ELO Ranking** | ELO tournament ranking for multiple candidates (K=32, baseline 1200) | Shipping the first prompt you wrote instead of the best one |
| **G6: Delivery** | Final prompt + Quick Reference Card + maintenance obligations | Deploying a prompt without knowing how to maintain it |

### Output Complexity: Six-Tier Adaptive

Super-Prompt auto-detects input sophistication and adapts the funnel depth. No more forcing a four-layer funnel on a professional user with a complete PRD.

| Tier | What It Feels Like | Funnel Depth |
|------|-------------------|--------------|
| **① One-liner** | "Write me a prompt" | Full 4-layer funnel |
| **② Missing params** | Has direction, missing details | Problem discovery + assumption deconstruction |
| **③ Clear requirement** | 200-500 word description, logically coherent | Confirm → Simulate gaps → "Which gaps to fill?" |
| **④ Diagnostic** | "Review my prompt" | Direct anti-ambiguity scan |
| **⑤ Existing prompt** | User brings a prompt to optimize | Review + gap simulation |
| **⑥ Complete document** | Full PRD/spec | Review + gap simulation |

For tiers ③⑤⑥, the choice to deepen is always offered — never forced. Professional users get professional treatment.

### Input Modes

| Mode | Description |
|------|-------------|
| **Standard** | Interactive Q&A, ≤4 questions per round |
| **Review** | Audit existing prompts, run through anti-ambiguity checklist item by item |
| **Heavy-Duty** | Multi-agent systems, SOPs, complex workflows |

Input mode and output complexity are **orthogonal** — you can have Standard input + Heavy output.

### v2.0: Four-Layer Funnel for Product Understanding

G0 received a major upgrade in v2.0. For non-technical users who describe their product needs in plain language, Super-Prompt now uses a **four-layer requirements mining funnel** that fuses five industry methodologies:

| Layer | Method | What It Does | Industry Foundation |
|-------|--------|-------------|---------------------|
| **1. Problem Discovery** | STAR Model | Asks "what problem did you encounter?" not "what do you want?" | Customer Discovery (Steve Blank) |
| **2. Assumption Deconstruction** | 5 Whys | Every user statement is a hypothesis, not a fact. "I want X" → "Why?" → dig to root need | 5 Whys (Toyota), Socratic Questioning |
| **3. Body Mining** | Pointer Analysis | External pointers (URLs/screenshots/reference apps) → open and analyze; internal pointers (vague words) → expand via questioning | Needfinding (Stanford d.school) |
| **4. Gap Discovery** | Hypothesis Map | Verified vs Assumed vs Inherited → cross-reference → gap questions | Socratic Questioning, Funnel Questioning |

**Core premise**: Users don't say what they need — they say what they think the solution is. Every word is a pointer, not the requirement body. Super-Prompt deconstructs these pointers to uncover the real requirements.

**Validated results**: 
- Chinese calendar widget: coverage improved from 15% → 100% (16/16 requirements found)
- Pomodoro timer case: 3/8 → 8/8 requirements found
- Knowledge management system case: 3/14 → 14/14 requirements found
- **v2.1 Chinese calendar widget (280 words, tier ③)**: 4-layer funnel → information completeness simulation → 3 gaps surfaced → user filled 1 (city) → full prompt generated. "Better than I expected."

### v2.1: Six-Tier Input Grading

G0 no longer treats all users the same. Super-Prompt now classifies input into six tiers and adapts funnel depth accordingly:

| Tier | Input Pattern | Process |
|------|--------------|---------|
| ① One-liner | "Write me a prompt," no context | Full four-layer funnel |
| ② Missing params | Has direction but missing key info | Streamlined: problem discovery + assumption deconstruction |
| ③ Clear requirement | Complete description, logically coherent | Confirm understanding → Information completeness simulation → "Which gaps to fill?" |
| ④ Diagnostic | "Review this prompt for issues" | Direct anti-ambiguity 18-item scan |
| ⑤ Existing prompt optimization | User brings a prompt to improve | Review mode + information completeness simulation |
| ⑥ Complete document | Full PRD/spec/structured doc | Review mode + information completeness simulation |

**Key principle**: For professional users, the choice is offered — never forced. The four-layer funnel is a tool, not a cage.

### v2.1: Information Completeness Simulation

Instead of asking "Do you want to dig deeper?" (abstract and unhelpful), Super-Prompt **simulates a dry run** and reports gaps with three markers:

- ✅ **Confirmed** — User said it, no need to ask
- ⚠️ **Guessing** — Agent can guess but shouldn't; guessing wrong causes failures; must ask
- ❌ **Missing** — Can't run without it; must fill

The ⚠️ marker is the innovation: the agent *can* guess many things (zoom range, color scheme, tech stack), but guessing = gambling. This forces the agent to surface assumptions as explicit questions.

### v2.1: Multi-Format Output

**Not just text.** When the prompt involves workflows, architectures, data flows, or concept relationships, Super-Prompt now generates supplemental visual outputs:

| Scenario | Output |
|----------|--------|
| Decision trees / branching logic | Flowcharts (Draw.io / Mermaid) |
| System architecture / component relationships | Architecture diagrams |
| Data flows / processing pipelines | Data flow diagrams |
| Concept relationships / knowledge structures | Mind maps |
| Data comparison / statistics | Charts (bar, pie, line) |
| Demo / presentation needs | Podcast audio or video |
| External reference resources | Direct links |
| Formal client/team delivery | .docx / .pptx / PDF with embedded images |

**Principle**: Give users intuitive understanding. If plain text isn't enough, supplement with visuals, documents, audio, or links.

## Features

### 🎯 Six-Tier Adaptive Grading
Super-Prompt classifies your input into six tiers — from one-liners to complete PRDs — and adapts the funnel depth accordingly. Professional users get professional treatment: the four-layer funnel is offered, never forced.

### 🧠 Information Completeness Simulation
Before writing a single prompt word, Super-Prompt simulates a dry run of your requirement and reports gaps with three markers: ✅ Confirmed, ⚠️ Guessing (agent can guess but shouldn't), ❌ Missing. No more "does this look right?" — you get a structured gap report and choose what to fill.

### 🔍 Web Pre-Search Engine
Before asking you a single question, Super-Prompt searches the web for domain-specific knowledge, industry best practices, known edge cases, and common pitfalls. This means your prompt is backed by evidence, not assumptions.

### 🛡️ 18-Point Anti-Ambiguity Checklist
The most comprehensive anti-ambiguity system in any prompt tool. Each of the 18 items is a specific, grep-able check that locks down one ambiguity vector. No checkbox theater — every item requires evidence.

### 🏆 ELO-Based Prompt Ranking
When you have multiple prompt candidates, Super-Prompt runs an ELO tournament (K=32, baseline 1200) to identify the best version. No more "this one feels better" — you get statistical confidence.

### 📋 Quick Reference Card
Every prompt ships with a maintenance card that includes:
- Degradation scenarios (when the prompt might fail and how to detect it)
- Exception handling protocols
- Update frequency recommendations
- Known failure modes

### 🌐 Bilingual Support
Full Chinese and English support. SKILL.md, README, CHANGELOG, and CONTRIBUTING are all available in both languages.

### 🔌 Agent Skills Compatible
Built as an [Agent Skills](https://agentskills.io) skill. Works with any Agent Skills-compatible AI coding assistant, including Claude Code, Cursor, and Coze.

## Design Principles

1. **Pre-search, don't guess** — Every question backed by web search; results converted into options for injection
2. **Layered guidance, not interrogation** — ≤4 questions per round, starting from the simplest mandatory questions
3. **Anti-ambiguity, not assumption** — 18-item checklist, systematically lock every ambiguity path
4. **Evidence-driven, not opinion-driven** — Design decisions backed by search evidence or industry standards
5. **ELO-verified, not human-judged** — Multi-candidate ranking via ELO tournament
6. **Deliver with insurance** — Quick Reference Card + maintenance obligations + degradation and exception handling
7. **Output on demand, not over-deliver** — Never skimp, never bloat; safety margin only increases, never decreases

## How It Compares

| Feature | Super-Prompt | Promptfoo | dair-ai Guide | orbit-prompt |
|---|---|---|---|---|
| **Approach** | Structured prompt discipline | Prompt testing framework | Educational guide | Claude Code skill |
| **Anti-ambiguity** | ✅ 18-item checklist | ❌ | ❌ | ❌ |
| **Web pre-search** | ✅ Built-in | ❌ | ❌ | ❌ |
| **ELO ranking** | ✅ Multi-candidate | ❌ | ❌ | ❌ |
| **Production output** | ✅ Prompt + QRC + maintenance | ❌ Test results only | ❌ | ❌ |
| **Prompt testing** | Adversarial (G4) | ✅ CI-integrated | ❌ | ❌ |
| **Best for** | Writing precise prompts | Testing existing prompts | Learning prompt engineering | Quick Claude Code prompts |

## super-spec × super-prompt

Super-Prompt is the sister project of [super-spec](https://github.com/wlj103/super-spec):

| | super-spec | super-prompt |
|---|---|---|
| **Problem** | AI skips steps, claims success with zero evidence | AI expresses vaguely, lacks structure, leaves ambiguity |
| **Solution** | Engineering discipline — 7 gates, 5 documents, anti-corner-cutting | Prompt discipline — 7 gates, 18 anti-ambiguity items, ELO ranking |
| **Domain** | How agents **execute** | How agents **express** |

Together, they form a complete discipline layer: one ensures the agent **does the right things**, the other ensures the agent **says them the right way**.

## FAQ

### How is this different from a prompt template?
Templates give you a structure to fill in. Super-Prompt gives you a **process** — it actively searches, checks, tests, and ranks. A template won't tell you your prompt is ambiguous; Super-Prompt's 18-item checklist will.

### Does this work with Claude? GPT? Other models?
Yes. Super-Prompt is **model-agnostic**. The prompt discipline principles apply to any LLM — Claude, GPT, Gemini, Llama, or local models.

### Can I use this for agent system prompts?
Yes — that's the Heavy mode. It's designed for complex agent instructions, multi-agent SOPs, and production-grade system prompts.

### How does ELO ranking work?
Super-Prompt generates multiple prompt candidates, then runs head-to-head comparisons using an ELO system (K=32, baseline 1200). The highest-ranked prompt wins — not the first one you wrote.

### What's the Quick Reference Card?
A one-page maintenance document that ships with every prompt. It tells you when the prompt might degrade, how to detect it, and what to do about it.

### Is this free?
Yes. MIT licensed, open source, free forever.

### Can I contribute?
Absolutely. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines. We welcome prompt patterns, anti-ambiguity item suggestions, and ELO calibration improvements.

## License

MIT © 2026
