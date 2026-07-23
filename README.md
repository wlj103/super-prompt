# Super-Prompt: Precision Prompt Forging

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Standard: Agent Skills](https://img.shields.io/badge/Standard-Agent%20Skills-6e3ef7.svg)](https://agentskills.io)

> 🎯 **Make every instruction AI receives precise and unambiguous — not "good enough."** — Anti-ambiguity interception × Web pre-search × Layered guidance × ELO ranking, from a single sentence to production-grade prompts.

**Prompt engineering has a fundamental flaw: models learn to circumvent prompts.** You say "enforce verification," it outputs four words: "Verification enforced successfully." You say "be detailed," it writes 3 lines of fluff and calls it detailed. You say "use JSON format," it freely invents field names.

Super-Prompt is not a template, not a fill-in-the-blank sheet — it is a **complete prompt discipline system**. Through seven-gate guided interaction + web search pre-loading + anti-ambiguity checks + ELO ranking, it helps users forge a single sentence or a product document into a **production-grade prompt that AI cannot misunderstand**.

## Quick Start

```bash
npx skills add wlj103/super-prompt
```

Trigger with: "帮我写一个提示词" / "帮我优化这段 prompt" / "精铸提示词"

## How It Works

### Seven Gates

| Gate | What It Prevents |
|------|------------------|
| **G0: Intent Clarification** | Vague user goals causing AI to guess blindly |
| **G1: Domain Search** | Missing domain knowledge, best practices, known pitfalls |
| **G2: Anti-Ambiguity Lock** | 18-item checklist scan, item by item; no empty "pass" |
| **G3: Structured Draft** | Mandatory sections, precise constraints, zero free-form |
| **G4: Adversarial Test** | Simulate 3 ways AI could misinterpret; harden weak points |
| **G5: ELO Ranking** | ELO tournament ranking for multiple candidates (K=32, baseline 1200) |
| **G6: Delivery** | Final prompt + Quick Reference Card + maintenance obligations |

### Output Complexity: Light / Medium / Heavy

Super-Prompt auto-detects project complexity and adjusts output depth:

- **Light** — One-liner optimization; Gate 1 rule engine only, no LLM invocation
- **Medium** — Defined scenario but incomplete prompt; G1→G3→G5, standard ELO
- **Heavy** — Agent system prompts, production-grade prompts; full 7 gates + 18 anti-ambiguity items + ELO×2

### Input Modes

- **Standard** — Interactive Q&A, ≤4 questions per round
- **Review** — Audit existing prompts, run through the anti-ambiguity checklist item by item
- **Heavy-Duty** — Multi-agent systems, SOPs, complex workflows

Input mode and output complexity are orthogonal — you can have Standard input + Heavy output.

## Design Principles

1. **Pre-search, don't guess** — Every question backed by web search; results converted into options for injection
2. **Layered guidance, not interrogation** — ≤4 questions per round, starting from the simplest mandatory questions
3. **Anti-ambiguity, not assumption** — 18-item checklist, systematically lock every ambiguity path
4. **Evidence-driven, not opinion-driven** — Design decisions backed by search evidence or industry standards
5. **ELO-verified, not human-judged** — Multi-candidate ranking via ELO tournament
6. **Deliver with insurance** — Quick Reference Card + maintenance obligations + degradation and exception handling
7. **Output on demand, not over-deliver** — Never skimp, never bloat; safety margin only increases, never decreases

## super-spec × super-prompt

Super-Prompt is the sister project of [super-spec](https://github.com/wlj103/super-spec):

| | super-spec | super-prompt |
|---|---|---|
| **Problem** | AI skips steps, claims success with zero evidence | AI expresses vaguely, lacks structure, leaves ambiguity |
| **Solution** | Engineering discipline — 7 gates, 5 documents, anti-corner-cutting | Prompt discipline — 7 gates, 18 anti-ambiguity items, ELO ranking |
| **Domain** | How agents **execute** | How agents **express** |

Together, they form a complete discipline layer: one ensures the agent **does the right things**, the other ensures the agent **says them the right way**.

## License

MIT © 2026