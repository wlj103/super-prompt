# Super-Prompt：引导式提示词精铸

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Standard: Agent Skills](https://img.shields.io/badge/Standard-Agent%20Skills-6e3ef7.svg)](https://agentskills.io)

> 🎯 **让 AI 收到的每个指令都精准无歧义——而不是"差不多就行"。** — 反歧义拦截 × 联网预搜索 × 分层引导 × ELO 排名，从一句话到生产级提示词。

**Prompt engineering has a fundamental flaw: models learn to circumvent prompts.** You say "enforce verification," it outputs four words: "Verification enforced successfully." You say "be detailed," it writes 3 lines of fluff and calls it detail.

Super-Prompt is not a template. It's a **prompt discipline system** — seven gates of guided interaction, web search pre-loading, anti-ambiguity checks, and ELO ranking — that takes you from a single sentence to a **production-grade prompt the AI cannot misunderstand**.

## Quick Start

```bash
npx skills add wlj103/super-prompt
```

Or trigger with: "帮我写一个提示词" / "帮我优化这段 prompt" / "精铸提示词"

## How It Works

### Seven Gates

| Gate | Purpose |
|------|---------|
| **G0: Intent Clarity** | Detect ambiguity in user's goal; ask targeted questions |
| **G1: Domain Search** | Pre-search web for domain knowledge, best practices, pitfalls |
| **G2: Anti-Ambiguity Lock** | Run 18-item anti-ambiguity checklist; no false "yes" |
| **G3: Structured Draft** | Generate prompt with mandatory sections, precise constraints |
| **G4: Adversarial Test** | Simulate 3 ways AI could misinterpret; harden weak points |
| **G5: ELO Ranking** | If multiple candidates, rank by ELO (K=32, baseline 1200) |
| **G6: Delivery** | Final prompt with Quick Reference Card + maintenance obligations |

### Output Complexity: Light / Medium / Heavy

Super-Prompt auto-detects project complexity and adjusts output depth:

- **Light** — Simple one-liner optimization, Gate 1 rule engine only, no LLM
- **Medium** — Defined scenario but incomplete prompt, G1→G3→G5, standard ELO
- **Heavy** — Agent system prompts, production-grade prompts, full 7 gates + 18 anti-ambiguity items + ELO×2

### Input Modes

- **Standard** — Interactive Q&A, ≤4 questions per round
- **Review** — Audit existing prompts against the anti-ambiguity checklist
- **Heavy-Duty** — Multi-agent systems, SOPs, complex workflows

Input mode and output complexity are orthogonal — you can have a Standard input with Heavy output.

## Design Principles

1. **Pre-search, don't guess** — Every question backed by web search results
2. **Layered guidance, not interrogation** — ≤4 questions per round, from simplest to deepest
3. **Anti-ambiguity, not assumption** — 18-item checklist, systematically lock every ambiguity path
4. **Evidence-driven, not opinion-driven** — Design decisions backed by search evidence or industry standards
5. **ELO-verified, not human-judged** — Multi-candidate ranking via ELO tournament
6. **Deliver with insurance** — Quick Reference Card + maintenance obligations + degradation handling
7. **Output on demand, not over-deliver** — Match depth to project complexity; never skimp, never bloat

## super-spec × super-prompt

Super-Prompt is the sister project of [super-spec](https://github.com/wlj103/super-spec):

| | super-spec | super-prompt |
|---|---|---|
| **Problem** | AI skips steps, claims success without evidence | AI expresses vaguely, lacks structure, leaves ambiguity |
| **Solution** | Engineering discipline — 7 gates, 5 documents, anti-corner-cutting | Prompt discipline — 7 gates, 18 anti-ambiguity items, ELO ranking |
| **Domain** | How agents **execute** | How agents **express** |

Together, they form a complete discipline layer: one ensures the agent **does the right things**, the other ensures the agent **says them the right way**.

## License

MIT © 2026
