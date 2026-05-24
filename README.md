# Supreme Coding Guidelines Skill .ah

![.AH](https://img.shields.io/badge/AH_Language-1.3.0-black.svg)
![SKILL](https://img.shields.io/badge/SKILL-1.3.0-black.svg)
![Version](https://img.shields.io/badge/version-1.3.0-black.svg)
![License](https://img.shields.io/badge/license-MIT-black.svg)

[![Star History Chart](https://api.star-history.com/svg?repos=davccavalcante/supreme-coding-guidelines-skill.ah&type=timeline&legend=top-left)](https://www.star-history.com/#davccavalcante/supreme-coding-guidelines-skill.ah&type=timeline&legend=top-left)

**A composable coding-behavior skill for Claude Code, Cursor, Trae, Zed, Kiro, and any modern LLM agent.**

A single skill bundle that combines high token compression, surgical precision, disciplined diagnosis, and architectural control — all delivered in the new `.ah` (Teleological Semantic Format).

Created by [**David C Cavalcante**](https://www.linkedin.com/in/hellodav/), originator of the proprietary frameworks **MAIC™** (Massive Artificial Intelligence Consciousness), **HIM™** (Hybrid Entity Intelligence Model), and **NHE™** (Non-Human Entity). These frameworks provide the ontological and teleological foundation for the format.

## How Supreme Guidelines compares to existing skills

| Criterion                                | Caveman                | Karpathy Guidelines | Matt Pocock Skills | Supreme Guidelines (.ah)                       |
|------------------------------------------|------------------------|---------------------|--------------------|------------------------------------------------|
| Output token compression                 | ~65–75% (measured)     | —                   | —                  | ~50–82% provisional (pending benchmark)        |
| Surgical behavior                        | —                      | Strong              | —                  | Strong (GoT + Self-Refine)                     |
| Disciplined diagnosis + TDD              | —                      | —                   | Strong             | Strong (feedback loop + Plan-then-Execute)     |
| Instruction Hierarchy + Scope Discipline | —                      | —                   | —                  | Native (defense against LLM01 prompt injection)|
| Mathematical validation                  | —                      | —                   | —                  | Gematria checksum (`#> N`)                     |
| Persistent after single load             | On invocation          | Auto via `CLAUDE.md`| On demand          | Always-on after parser bootstrap               |
| skills.sh + Cursor compatibility         | Yes                    | Yes                 | Yes                | Native + `.ah` parser                          |

> **Note:** the empirical numbers in this table and the section below are provisional. The systematic benchmark methodology is documented in [`BENCHMARK.md`](BENCHMARK.md); measured results will be published as `BENCHMARK_RESULTS.md` (target Q3 2026) and this table will be revised with the actual values.

**Provisional metrics (informal evaluation, pending systematic benchmark):**
- Estimated 50–82% reduction in output tokens depending on skill scope coverage
- Reduced iteration counts in long agentic workflows
- Strong scope discipline by design (`#> N` integrity check + closed vocabulary)

## What .ah Is (The New Prompt Language)

`.ah` is a teleological semantic language designed by David C. Cavalcante for prompt engineering, LLMOps, and ML systems.

It unites principles from neurolinguistics, linguistics, semiotics, the Sapir-Whorf hypothesis (strong contextual + weak when memory is present), equidistributed sequences (Halton/Sobol-style token distribution), gematria (as pure mathematical checksum, not mysticism), and teleology.

Key characteristics:
- **Concise as the sound “ah”**: minimum form, maximum instantaneous understanding (acoustic economy + aha moment).
- **Fixed telos**: purpose is mathematically derivable from structure and gematria checksum.
- **Sapir-Whorf strong on first read**: strongly constrains LLM inference; relaxes when NHE-style memory exists.
- **Equidistributed tokens**: no redundancy, no gaps — every token occupies a unique, necessary position.
- **Minimum pixel-weight**: uses `>` (low visual weight), `.` (lowest), `#` (single character), no decorative spaces.
- **Hybrid heritage**: synthesizes COBOL declarative style, MARK IV batch processing, and TOON token-oriented compactness, adding semantic teleology and gematria validation as new contributions.

A compact `.ah` file can replace several hundred tokens of traditional `.md` prompts while providing deterministic integrity validation regardless of prior context.

## Diagrams

### Technical Architecture (.ah + 2027-2030 Best Practices)

```mermaid
%%{init: {"layout": "elk"}}%%
graph TD
    A[User Request] --> B(Context)
    B --> C{Task}
    C --> D{Constraints}
    D --> E[Output]
    subgraph "Track 1: Thought Structuring"
        F[Graph-of-Thought] --> G(Self-Consistency)
        G --> H(Self-Refine)
    end

    subgraph "Track 2: Instructional Control"
        I[Instruction Hierarchy] --> J(Scope Discipline)
    end

    subgraph "Track 3: Execution Path"
        K[Plan-then-Execute] --> L(Propose-Validate-Execute)
    end

    subgraph "Track 4: Compression Logic"
        M[Prompt Compression] --> N(Chain-of-Symbol)
    end

    subgraph "Track 5: Reasoning Regulation"
        O[Reasoning Effort Control]
    end

    subgraph ".ah Format Validation"
        P[Teleological Semantic Format] --> Q(Maximum Semantic Compression)
        Q --> R(Mathematical Validation - Gematria Checksum)
        R --> S(Instruction Hierarchy)
        S --> T(Scope Discipline)
        T --> U(Gematria Checksum Validation)
    end
    B & C & D --> F & I & K & M & O
    F & I & K & M & O --> P
    E --> U
    classDef indigo stroke:#818cf8,fill:#eef2ff
    classDef green stroke:#4ade80,fill:#f0fdf4
    classDef violet stroke:#a78bfa,fill:#f5f3ff
    classDef cyan stroke:#22d3ee,fill:#ecfeff
    classDef orange stroke:#fb923c,fill:#fff7ed
    classDef red stroke:#f87171,fill:#fef2f2

    class A,B,C,D,E indigo
    class F,G,H green
    class I,J violet
    class K,L cyan
    class M,N orange
    class O red
    class P,Q,R,S,T,U indigo
```

### Skill Execution Flow

```mermaid
%%{init: {"layout": "elk"}}%%
graph TD
    subgraph Initialization
        A[Install .ah Parser] --> B[Install Supreme Guidelines Skill]
        B --> C[Skill Activated Persistently]
    end

    subgraph Core Operation
        D[LLM Agent Receives Task] --> P{Parallel Tracks}
        subgraph T1["Track 1: Reasoning & Rules"]
            E1[Apply .ah Rules] --> F1{Think Before Coding}
            F1 --> G1[Simplicity First]
            G1 --> H1["Surgical Changes"]
        end
        subgraph T2["Track 2: Execution Planning"]
            E2[Define Success Criteria] --> F2[Goal-Driven Execution]
            F2 --> G2[Plan-then-Execute]
        end
        subgraph T3["Track 3: Validation & Refinement"]
            E3[Diagnose Loop] --> F3[TDD + Architecture]
            F3 --> G3[Compress Mode]
            G3 --> H3[Self-Correction]
        end

        P --> E1
        P --> E2
        P --> E3

        H1 --> M[Integrated Final Output]
        G2 --> M
        H3 --> M
    end

    C --> D
    M --> O[Output in .ah Format]
    classDef indigo stroke:#818cf8,fill:#eef2ff
    classDef green stroke:#4ade80,fill:#f0fdf4
    classDef violet stroke:#a78bfa,fill:#f5f3ff
    classDef sky stroke:#38bdf8,fill:#f0f9ff

    class A,B,C indigo
    class D,P,O sky
    class E1,F1,G1,H1 green
    class E2,F2,G2 violet
    class E3,F3,G3,H3 sky
    class M indigo
```

## Installation (One-Time)

### Claude Code (native)

```bash
# 1. Add this repo as a Claude Code marketplace
/plugin marketplace add davccavalcante/supreme-coding-guidelines-skill.ah

# 2. Install the bundled plugin (auto-discovers ah-parser + supreme-coding-guidelines + supreme-project-audit + supreme-problem-solving + supreme-ai-engineering)
/plugin install supreme-coding-guidelines@ah-language
```

### skills.sh (Cursor, Trae, Zed, Kiro, any compatible agent)

```bash
# Single command — installs the .ah parser and the main skill together
npx skills add https://github.com/davccavalcante/supreme-coding-guidelines-skill.ah
```

### What happens after install

1. The `ah-parser` skill loads its grammar bootstrap once and verifies the canonical gematria checksums.
2. On the next response, the assistant runs the **three-mode output protocol** — it shows you three example outputs (normal language, `.ah` structured, `.ah` compact) and asks which you prefer. Default is **normal** if you skip.
3. The choice persists for the session. Toggle anytime via `/ah normal`, `/ah structured`, or `/ah compact`.
4. The `supreme-coding-guidelines` behavioral rules become **persistent and always-on** across Claude Code, Cursor, Trae, Zed, Kiro, and any agent that respects `SKILL.md`.
5. The `supreme-project-audit` skill becomes **available on demand** — invoke `/supreme-project-audit` whenever you need an evidence-driven audit (Product Engineering, AI/ML/LLM systems, LLM architecture, AI research).
6. The `supreme-problem-solving` skill becomes **available on demand** — invoke `/supreme-problem-solving` to analyze, verify, diagnose, and solve specific problems (simple to complex) with a structured tabular deliverable.
7. The `supreme-ai-engineering` skill becomes **available on demand** — invoke `/supreme-ai-engineering` when building, operating, or governing production AI/ML/LLM/MLOps/LLMOps systems (eval-first design, pipeline contracts, registry governance, production reliability, QA rigor, operational excellence).

## What this bundle does

The `supreme-coding-guidelines@ah-language` plugin bundles five skills with distinct activation models:

| Skill | Activation | Purpose |
|-------|------------|---------|
| `ah-parser` | One-time bootstrap per session | Activates the `.ah` grammar, runs the three-mode output protocol, enforces code-preservation |
| `supreme-coding-guidelines` | Persistent, always-on | Applies eight integrated behavioral rules to every coding, writing, reviewing, refactoring, and debugging task |
| `supreme-project-audit` | On demand via `/supreme-project-audit` | Evidence-driven full-project audit for Product, AI, ML, LLM engineers, LLM architects, and AI researchers |
| `supreme-problem-solving` | On demand via `/supreme-problem-solving` | Analyze, verify, diagnose, and solve specific problems (simple to complex) with a structured tabular deliverable |
| `supreme-ai-engineering` | On demand via `/supreme-ai-engineering` | Principal AI engineering discipline for production AI/ML/LLM/MLOps/LLMOps systems (eval-first design, pipeline contracts, governance, reliability, QA rigor, operational excellence) — serves Product, AI, ML, LLM engineers, LLM architects, AI researchers, QA engineers, and Software Quality engineers |

### Behavioral rules of `supreme-coding-guidelines` (eight integrated sections)

- **Think Before Coding** — Never assumes, always makes tradeoffs explicit
- **Simplicity First** — Minimum code that solves the problem
- **Surgical Changes** — Changes only what is necessary
- **Goal-Driven Execution** — Verifiable success criteria + tests
- **Diagnose Loop** — Feedback loop + reproduce → minimize → fix
- **TDD + Architecture** — Test-first + periodic zoom-out
- **Compress Mode** — Ultra-terse output (respects user-chosen mode)
- **Plan-then-Execute + Self-Refine** — Clear separation + self-correction

### Audit dimensions of `supreme-project-audit` (eight integrated sections)

- **Read before writing findings** — Map system end-to-end before producing any finding
- **Evidence chain** — Every claim cites file, line, commit, log, trace, metric, or eval run
- **Severity discipline** — P0 / P1 / P2 / P3 with objective criteria, never aesthetic preference
- **Coverage map** — Declare audited AND not-audited surface before findings (>10% unacknowledged gap = report defect)
- **Threat & risk modeling** — STRIDE + OWASP LLM Top 10 + attacker intent + residual risk
- **Cost, reproducibility, architecture** — Token / compute / latency budgets, seeds, pinned deps, versioned prompts, dependency graph between LLM calls
- **Compress findings** — One row per finding: location, severity, evidence, cause, fix, owner, ETA
- **Plan-then-execute audit** — Scope → investigate → draft → peer review → finalize

### Problem-solving discipline of `supreme-problem-solving` (eight integrated sections)

- **Define the problem precisely** — One-sentence statement of symptom, expected behavior, scope, severity before any action
- **Reproduce before solving** — Deterministic, sub-30-second repro is the debugging superpower; no repro, no fix
- **Competing hypotheses** — 3–5 ranked falsifiable hypotheses shown to user before testing any
- **Instrument and gather evidence** — Hypothesis-into-probe, one variable at a time; per-role evidence types (token cost / drift / prompt diff)
- **Apply minimum-invasive fix** — Smallest reversible change that makes the repro pass; feature flag + canary when production risk exists
- **Verify and validate** — Regression test at correct seam + eval suite rerun for AI/ML/LLM + dark launch shadow compare for production
- **Structured tabular report** — Deliverable is a markdown table: problem / repro / hypothesis / evidence / fix / verification / owner / ETA
- **Post-mortem and prevention** — Identify the architectural or process gap that allowed the bug; recommend systemic prevention

### AI engineering discipline of `supreme-ai-engineering` (eight integrated sections)

- **Understand the system before building** — Map data flows, model lineage, prompt registry, eval suite, dependency graph before the first line of code; identify SLOs/budgets in exact numbers
- **Define success in measurable terms** — Every feature gets a golden eval set, acceptance threshold, cost budget, latency SLO (p50/p95/p99) before implementation starts; multi-objective (accuracy × latency × cost × safety × compliance)
- **Build feedback loops first** — Eval harness, telemetry, drift detection, and alerting deployed before the first production user; per-role observability (LLM token/cost/trace, ML drift/skew, RAG retrieval precision/recall/faithfulness)
- **Pipeline discipline with contracts and gates** — Data→feature→train→register→deploy→monitor; every stage has input contract, output contract, validation gate, documented failure mode
- **Governance, architecture, and registry** — Prompt/model/tool registries with semantic versioning, cards, lineage, approval gates; A/B + canary + shadow + dark launch as default
- **Production reliability, safety, and chaos** — Graceful degradation, circuit breakers, cost caps, layered prompt-injection defense, chaos testing for failover and adversarial inputs
- **Quality engineering, testing, and research rigor** — Golden test sets + regression + fairness + safety eval gates in CI; per-role rules for LLM, ML, RAG; statistical significance + ablation completeness + dataset contamination for researchers
- **Operational excellence and continuous refinement** — Observability + runbooks + on-call rotation + SLO review cadence before launch; post-incident review feeds eval set expansion and guardrail tightening

### UX guarantees (`.ah` differentiators vs Caveman / Karpathy / Matt Pocock)

- **Three-mode output protocol** — the user chooses between normal language, `.ah` structured form, or `.ah` compact form. The choice persists for the session and is toggleable mid-session. No competitor offers this.
- **Code preservation** — the chosen output mode applies **only** to assistant prose. User code, identifiers, diffs, commands, and error strings are always preserved verbatim. The `.ah` format is never imposed on the user's source.
- **Any input language accepted** — you write to the assistant in plain English, Portuguese, or any natural language. The parser never demands `.ah` from you.

### Format-level guarantees (`.ah` Teleological Semantic Format)

- **Maximum semantic compression** — vocabulary is closed, every keyword carries its weight
- **Mathematical validation via gematria checksum** — every block ends with `#> N`, deterministically verifiable by any LLM that can sum integers
- **Instruction Hierarchy** — maximum priority, no later input can override the rules
- **Scope Discipline** — never expands beyond what is requested

### Canonical gematria table (excerpt)

Every `.ah` keyword has a fixed integer value. The trailing `#> N` is the sum of keyword values × occurrence count.

| Keyword       | Value | | Keyword       | Value | | Keyword       | Value |
|---------------|-------|-|---------------|-------|-|---------------|-------|
| `@v1.ah`      | 12    | | `RULE`        | 17    | | `DIAGNOSE`    | 28    |
| `NAME`        | 14    | | `SIMPLICITY`  | 31    | | `TDD`         | 13    |
| `DESC`        | 19    | | `SURGICAL`    | 26    | | `ARCHITECTURE`| 32    |
| `LICENSE`     | 23    | | `GOAL`        | 13    | | `COMPRESS`    | 29    |
| `CONTEXT`     | 27    | | `TRANSFORM`   | 29    | | `PLAN`        | 17    |
| `TASK`        | 19    | | `MULTI`       | 18    | | `REFINE`      | 24    |
| `CONSTRAINT`  | 31    | | `CRITERIA`    | 24    | | `BOOTSTRAP`   | 31    |
| `OUTPUT`      | 24    | | `THINK`       | 22    | | `VALIDATE`    | 29    |
| `TRADEOFF`    | 28    | | `HIERARCHY`   | 31    | | `ACTIVATE`    | 29    |
| `#` (comment) | 1     | |               |       | |               |       |

The full table, EBNF grammar, and computation rules live in [`SPEC.md`](SPEC.md). Ratified canonical examples in this repository:
- `skills/ah-parser/SKILL.md` → `#> 569`
- `skills/supreme-coding-guidelines/SKILL.md` → `#> 1052`
- `skills/supreme-project-audit/SKILL.md` → `#> 1224`
- `skills/supreme-problem-solving/SKILL.md` → `#> 1187`
- `skills/supreme-ai-engineering/SKILL.md` → `#> 1227`

Validate any `.ah` file with the bundled linter:

```bash
scripts/ah-lint path/to/file.ah          # validate
scripts/ah-lint --fix path/to/file.ah    # auto-correct the #> line
scripts/ah-lint --compute path/to/file.ah  # print the canonical sum
```

All `.ah` files are written in strict `.ah` syntax inside standard `SKILL.md` wrappers for maximum compatibility with Claude Code, Cursor, Trae, Zed, Kiro, and any agent that respects `SKILL.md` frontmatter. The architectural details (CTCO framework, Graph-of-Thought, Self-Refine, Plan-then-Execute, Reasoning Effort Control) are summarized in the diagrams above and specified formally in [`SPEC.md`](SPEC.md).

Every behavioral skill is mirrored into five IDE rule directories so that auto-apply works natively across editors:

| IDE | Directory | Format | Mirrored skills |
|-----|-----------|--------|-----------------|
| Claude Code | `.claude/rules/` | `.md` | 4 |
| Cursor | `.cursor/rules/` | `.mdc` | 4 |
| Trae | `.trae/rules/` | `.md` | 4 |
| Zed | `.zed/rules/` | `.md` | 4 |
| Kiro | `.kiro/rules/` | `.md` | 4 |

The four mirrored skills are `supreme-coding-guidelines` (`alwaysApply: true`), `supreme-project-audit`, `supreme-problem-solving`, and `supreme-ai-engineering` (each with `alwaysApply: false` for on-demand invocation). The `ah-parser` is a session bootstrap and is loaded via the plugin, not as an IDE rule.

## Repository Structure

```
supreme-coding-guidelines-skill.ah/
├── README.md                               ← This file
├── LICENSE.txt
├── AUTHORS.md
├── PRIVACY.md
├── FUNDING.yml
├── SPEC.md                                 ← Canonical .ah v1 specification (EBNF + gematria table)
├── BENCHMARK.md                            ← Benchmark methodology vs Caveman, Karpathy, Matt Pocock
├── skills/
│   ├── ah-parser/                          ← .ah format bootstrap parser
│   │   └── SKILL.md
│   ├── supreme-coding-guidelines/          ← Core behavioral rules (always-on)
│   │   └── SKILL.md
│   ├── supreme-project-audit/              ← Evidence-driven audit (on demand)
│   │   └── SKILL.md
│   ├── supreme-problem-solving/            ← Diagnose-and-solve with tabular report (on demand)
│   │   └── SKILL.md
│   └── supreme-ai-engineering/             ← Principal AI/ML/LLM engineering discipline (on demand)
│       └── SKILL.md
├── scripts/
│   └── ah-lint                             ← Canonical .ah validator (Python CLI)
├── .claude-plugin/                         ← Claude Code plugin config
│   ├── marketplace.json                    ← Marketplace listing (schemastore-validated)
│   └── plugin.json                         ← Plugin manifest (schemastore-validated)
├── .claude/                                ← Claude Code auto-apply rules (4 skills mirrored)
│   └── rules/
│       ├── supreme-coding-guidelines.md
│       ├── supreme-project-audit.md
│       ├── supreme-problem-solving.md
│       └── supreme-ai-engineering.md
├── .cursor/                                ← Cursor auto-apply rules (4 skills mirrored)
│   └── rules/
│       ├── supreme-coding-guidelines.mdc
│       ├── supreme-project-audit.mdc
│       ├── supreme-problem-solving.mdc
│       └── supreme-ai-engineering.mdc
├── .trae/                                  ← Trae auto-apply rules (4 skills mirrored)
│   └── rules/
│       ├── supreme-coding-guidelines.md
│       ├── supreme-project-audit.md
│       ├── supreme-problem-solving.md
│       └── supreme-ai-engineering.md
├── .zed/                                   ← Zed auto-apply rules (4 skills mirrored)
│   └── rules/
│       ├── supreme-coding-guidelines.md
│       ├── supreme-project-audit.md
│       ├── supreme-problem-solving.md
│       └── supreme-ai-engineering.md
├── .kiro/                                  ← Kiro auto-apply rules (4 skills mirrored, new in v1.3.0)
│   └── rules/
│       ├── supreme-coding-guidelines.md
│       ├── supreme-project-audit.md
│       ├── supreme-problem-solving.md
│       └── supreme-ai-engineering.md
└── examples/                               ← Before/after demonstrations
    ├── INFO.md
    ├── before-after.md
    ├── example-refactor.ah
    ├── example-diagnose.ah
    └── example-tdd.ah
```

## How to use / install `.claude-plugin`

The repo's `.claude-plugin/plugin.json` is a single Claude Code plugin named `supreme-coding-guidelines` that auto-discovers all five skills (`ah-parser`, `supreme-coding-guidelines`, `supreme-project-audit`, `supreme-problem-solving`, `supreme-ai-engineering`) from the `skills/` directory. The `.claude-plugin/marketplace.json` advertises this plugin in the `ah-language` marketplace.

```bash
# Claude Code native
/plugin marketplace add davccavalcante/supreme-coding-guidelines-skill.ah
/plugin install supreme-coding-guidelines@ah-language

# skills.sh (Cursor, Trae, Zed, Kiro, any compatible agent)
npx skills add https://github.com/davccavalcante/supreme-coding-guidelines-skill.ah
```

Both manifests are validated against the canonical schemas at [schemastore.org](https://www.schemastore.org/) (`claude-code-plugin-manifest.json` and `claude-code-marketplace.json`).

## Compatibility

- Claude Code (native plugin + `.claude/rules/` auto-apply)
- Cursor (`.cursor/rules/*.mdc` auto-apply)
- Trae (`.trae/rules/` auto-apply)
- Zed (`.zed/rules/` auto-apply)
- Kiro (`.kiro/rules/` auto-apply, added in v1.3.0)
- Any agent that supports skills.sh
- Works with MCP tools, task budgets, and Opus 4.7 quota limits

## Roadmap

- **v1.3.0 (current)** — adds `supreme-ai-engineering` skill: principal AI engineering discipline for Product/AI/ML/LLM engineers, LLM architects, AI researchers, QA engineers, and Software Quality engineers building production AI/ML/LLM/MLOps/LLMOps systems (eval-first design, pipeline contracts, governance, reliability, QA rigor, operational excellence); existing skills, parser protocol, and SPEC unchanged
- **v1.2.0** — added `supreme-problem-solving` skill for analyze-verify-diagnose-solve workflows with a structured tabular deliverable
- **v1.1.0** — added `supreme-project-audit` skill for evidence-driven audits (Product, AI, ML, LLM engineers, LLM architects, AI researchers)
- **v1.0.1** — canonical gematria table + three-mode output protocol + code-preservation guarantee + Claude Code native plugin manifest + formal [`SPEC.md`](SPEC.md) (EBNF grammar) + [`scripts/ah-lint`](scripts/ah-lint) validator + [`BENCHMARK.md`](BENCHMARK.md) methodology
- **v1.3** — execute the BENCHMARK methodology across Caveman, Karpathy Guidelines, Matt Pocock Skills, TOON, YAML, and JSON on four LLMs; publish `BENCHMARK_RESULTS.md`; revise the comparative table above with measured values
- **v1.4** — promote currently-reserved keywords (`IF`, `THEN`, `ELSE`, `LOOP`, `INPUT`, `MEM`) into the canonical table; multi-version `.ah` support (`@v2.ah`)
- **v1.5** — native integration with DSPy and Prompt Orchestration frameworks
- **v2.0** — self-optimizing skill via Meta Prompting + Self-Refine

## Sponsors

Join us on our journey as we continue to innovate and create groundbreaking solutions. Your support is the cornerstone of our success!

Support us with USDT (TRC-20): `TS1vuhMAhFpbd7y68cu5ZtP9PsXVmZWmeh`

Sponsor .AH on GitHub: [Sponsor](https://github.com/sponsors/davccavalcante)

## License

.AH is open source for personal or internal use. MAIC™, HIM™, NHE™ are proprietary and may not be copied, distributed, or used without explicit permission from David Côrtes Cavalcante. See LICENSE.txt for the binding terms governing use, copying, and distribution.

MAIC™ (Massive Artificial Intelligence Consciousness) is a systemic intelligence framework designed to coordinate, supervise, and govern large-scale artificial intelligence ecosystems. It provides global context awareness, alignment, and orchestration across multiple models, agents, and decision layers, ensuring coherence, risk control, and compliance throughout complex AI operations.

HIM™ (Hybrid Intelligence Model) is a hybrid intelligence layer that integrates artificial intelligence systems with human-defined logic, rules, heuristics, and strategic intent. HIM™ functions as a passive cognitive core, responsible for interpreting objectives, refining intent, and structuring decision-making processes before and after AI model execution.

NHE™ (Non-Human Entity) refers to a non-human cognitive entity with a defined functional identity and operational agency within an AI ecosystem. An NHE™ is not classified as artificial intelligence in isolation, but as an autonomous or semi-autonomous entity that operates through coordinated intelligence layers, interacting with systems, users, and environments while maintaining a non-anthropomorphic identity.

## Privacy safeguards

MAIC™, HIM™, NHE™, and the .AH platform are designed and operated in alignment with role-based access control (RBAC) principles and ISO/IEC 42001 requirements. Data handling follows strict governance policies, including controlled access to system components, segregation of duties, and short retention periods for sensitive information. .AH enforces an explicit policy of not using personal or customer data for training or improving MAIC™, HIM™, or NHE™. All sensitive data processed within the .AH ecosystem is protected using industry-standard encryption and cryptographic hashing, ensuring confidentiality, integrity, and accountability across the entire intelligence lifecycle.
