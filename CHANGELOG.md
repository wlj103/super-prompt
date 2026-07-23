# Changelog

## v2.2.0 (2026-07-24)

### Added
- 🔒 Security Declaration section
- 🧩 Four-Element Quick Diagnostic Framework (Role/Task/Constraints/Output)
- 🔍 Diagnostic Five Questions for reverse attribution
- ⚖️ Proportional Complexity Principle (simple/medium/complex tiering)
- 🛡️ Injection risk awareness in Gate 5 adversarial testing

### Changed
- Complete English translation of SKILL.md
- Description updated: "ELO ranking" → "seven gates"
- Enhanced description with SEO keywords
- README title updated to v2.2 with improved search terms

### Fixed
- AIGC metadata cleanup from all documents


## v2.1 (2026-07-24)

### Six-Tier Input Grading

Replaced the old three-tier (Light/Medium/Heavy) auto-detection with a **six-tier input classification** that adapts the funnel depth to user sophistication:

| Tier | Input Pattern | Process |
|------|--------------|---------|
| ① One-liner | "Write me a prompt," no context | Full four-layer funnel |
| ② Missing params | Has direction but missing key info | Streamlined: problem discovery + assumption deconstruction |
| ③ Clear requirement | Complete description, logically coherent | Confirm understanding → Information completeness simulation → "Which gaps to fill?" |
| ④ Diagnostic | "Review this prompt for issues" | Direct anti-ambiguity 18-item scan |
| ⑤ Existing prompt optimization | User brings a prompt to improve | Review mode + information completeness simulation |
| ⑥ Complete document | Full PRD/spec/structured doc | Review mode + information completeness simulation |

**Key principle**: For professional users (tiers ③⑤⑥), the choice to deepen requirements is offered — never forced. The four-layer funnel is a tool, not a cage.

### Information Completeness Simulation

Instead of asking "Do you want to dig deeper?" (which is abstract and unhelpful), Super-Prompt now **simulates a dry run** of the requirement and reports gaps with three markers:

- ✅ **Confirmed** — User said it, no need to ask
- ⚠️ **Guessing** — Agent can guess but shouldn't; guessing wrong causes failures; must ask
- ❌ **Missing** — Can't run without it; must fill

**Why this matters**: The agent can guess many things (zoom range, color scheme, tech stack), but guessing = gambling. The ⚠️ marker forces the agent to surface these as explicit questions rather than silently filling in assumptions.

### Multi-Format Output

**Not just text.** Super-Prompt now delivers content in multiple formats based on what users need to understand:

- **Flowcharts** (Draw.io / Mermaid) — for decision trees and branching logic
- **Architecture diagrams** — for system architecture and component relationships
- **Data flow diagrams** — for processing pipelines
- **Mind maps** — for concept relationships and knowledge structures
- **Charts** (bar, pie, line) — for data comparison and statistics
- **Podcast audio / video** — for demo and presentation needs
- **Direct links** — for external reference resources
- **Formal documents** (.docx / .pptx / PDF) — for client/team delivery with embedded images

**Principle**: Give users intuitive understanding. If plain text isn't enough, supplement with visuals, documents, audio, or links.

### Interaction Rules
- One question at a time (not multiple questions bundled together)
- Each question includes 1-2 concrete examples
- Share search results with users before asking questions — help them open their thinking

### Validated Test
- Chinese calendar desktop widget (280 words, tier ③): 4-layer funnel → information completeness simulation → 3 gaps surfaced → user filled 1 (city) → full prompt generated. User feedback: "Better than I expected."

---

## v2.0 (2026-07-24)

### G0: Four-Layer Requirements Mining Funnel

**Major upgrade to Step 0 (Product Understanding).** Changed from simple "three pointers" approach to a four-layer funnel backed by five industry methodologies:

- **Layer 1: Problem Discovery** — STAR model (Situation/Task/Action/Result). Asks "what problem did you encounter?" instead of "what do you want?" Based on Customer Discovery (Steve Blank).
- **Layer 2: Assumption Deconstruction** — Every user statement is a hypothesis, not a fact. "I want X" → "Why?" → 5 Whys to root need. Based on 5 Whys (Toyota) and Socratic Questioning.
- **Layer 3: Body Mining** — External pointers (URLs/screenshots) → open and analyze; internal pointers (vague words) → expand via questioning. Based on Needfinding (Stanford d.school).
- **Layer 4: Gap Discovery** — Hypothesis map: Verified vs Assumed vs Inherited. Cross-reference, gap questions, benchmark comparison. Based on Socratic Questioning and Funnel Questioning.

**Core premise**: Users don't say what they need — they say what they think the solution is. Every word is a pointer, not the requirement body.

**Validated results**:
- Chinese calendar widget: 15% → 100% coverage (16/16 requirements)
- Pomodoro timer: 37.5% → 100% coverage (8/8 requirements)
- Knowledge management system: 21% → 100% coverage (14/14 requirements)

### Documentation
- README.md: Added v2.0 four-layer funnel section with methodology table and validated results
- SKILL_zh.md: Step 0 fully rewritten with four-layer framework
- SKILL.md (English): unchanged per user request

---

## v1.0 (2026-07-23)

### Initial Release

- **Seven gates**: G0 Intent Clarity → G1 Domain Search → G2 Anti-Ambiguity Lock → G3 Structured Draft → G4 Adversarial Test → G5 ELO Ranking → G6 Delivery
- **18-item anti-ambiguity checklist**: systematically locking every ambiguity path
- **ELO ranking system**: K=32, baseline 1200, from gpt-prompt-engineer (MIT)
- **Output complexity**: Light / Medium / Heavy, auto-detected from project scope
- **Input modes**: Standard / Review / Heavy-Duty, orthogonal to output complexity
- **Pre-search**: web search pre-loading before every question, results injected as options
- **Layered guidance**: ≤4 questions per round, from simplest to deepest
- **Quick Reference Card**: one-page prompt summary for daily use
- **Maintenance obligations**: degradation handling, version tracking, update triggers
- **4-platform benchmark**: comparison with SkillOpt, prompt-optimizer, gpt-prompt-engineer
- **Chinese + English**: full bilingual SKILL.md

### Design Principles
1. Pre-search, don't guess
2. Layered guidance, not interrogation
3. Anti-ambiguity, not assumption
4. Evidence-driven, not opinion-driven
5. ELO-verified, not human-judged
6. Deliver with insurance
7. Output on demand, not over-deliver
