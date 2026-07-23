# Super-Prompt: Precision Prompt Forging

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Standard: Agent Skills](https://img.shields.io/badge/Standard-Agent%20Skills-6e3ef7.svg)](https://agentskills.io)
[![GitHub stars](https://img.shields.io/github/stars/wlj103/super-prompt?style=social)](https://github.com/wlj103/super-prompt)

> 🎯 **The prompt engineering tool that prevents AI from misunderstanding you.** Anti-Ambiguity Interception × Web Pre-Search × Layered Guidance × ELO Ranking — turn a single sentence or a product document into a **production-grade prompt that AI cannot misinterpret**.

<p align="center">
  <b>Install:</b> <code>npx skills add wlj103/super-prompt</code> &nbsp;|&nbsp;
  <b>Trigger:</b> "帮我写一个提示词" / "精铸提示词" / "optimize my prompt"
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

| Language | Trigger Phrases |
|---|---|
| **Chinese** | "帮我写一个提示词" / "帮我优化这段 prompt" / "精铸提示词" |
| **English** | "write me a prompt" / "optimize my prompt" / "forge a prompt" |

## How It Works

### Seven Gates

Super-Prompt guides you through seven sequential gates — each one must pass before moving to the next. No skipping, no "good enough."

| Gate | What It Does | What It Prevents |
|------|-------------|------------------|
| **G0: Intent Clarification** | Extracts concrete goals from vague user requests | AI guessing blindly because you said "make it better" |
| **G1: Domain Search** | Searches the web for domain knowledge, best practices, known pitfalls | Missing critical context that the AI would otherwise hallucinate |
| **G2: Anti-Ambiguity Lock** | 18-item checklist scan, item by item; no empty "pass" | Vague terms like "appropriate," "good," "reasonable" that AI exploits |
| **G3: Structured Draft** | Mandatory sections, precise constraints, zero free-form fields | Free-form prompts that give AI too much creative freedom |
| **G4: Adversarial Test** | Simulates 3 ways AI could misinterpret; hardens weak points | Prompts that work in testing but fail on edge cases |
| **G5: ELO Ranking** | ELO tournament ranking for multiple candidates (K=32, baseline 1200) | Shipping the first prompt you wrote instead of the best one |
| **G6: Delivery** | Final prompt + Quick Reference Card + maintenance obligations | Deploying a prompt without knowing how to maintain it |

### Output Complexity: Light / Medium / Heavy

Super-Prompt auto-detects project complexity and adjusts output depth:

| Mode | When to Use | What You Get |
|------|------------|--------------|
| **Light** | One-liner optimization, simple classification | Gate 1 rule engine only, no LLM invocation |
| **Medium** | Defined scenario but incomplete prompt | G1→G3→G5, standard ELO ranking |
| **Heavy** | Agent system prompts, production-grade prompts | Full 7 gates + 18 anti-ambiguity items + ELO×2 |

### Input Modes

| Mode | Description |
|------|-------------|
| **Standard** | Interactive Q&A, ≤4 questions per round |
| **Review** | Audit existing prompts, run through anti-ambiguity checklist item by item |
| **Heavy-Duty** | Multi-agent systems, SOPs, complex workflows |

Input mode and output complexity are **orthogonal** — you can have Standard input + Heavy output.

## Features

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