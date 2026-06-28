# `.ah` Language Specification

```
Version       : 1.9.0
Status        : Draft (canonical)
Spec date     : 2026-05-03
Author        : David C. Cavalcante (Takk8IS)
License       : MIT (language); proprietary frameworks (MAIC™, HIM™, NHE™) excluded
Media type    : text/ah
File extension: .ah
```

## Abstract

`.ah` (Teleological Semantic Format) is a domain-specific declarative language for prompts, skills, and instructions consumed by Large Language Models (LLMs) and Machine Learning (ML) systems. It is engineered for maximum semantic compression, deterministic mathematical integrity (gematria checksum), and unambiguous teleological derivation. A single `.ah` file replaces the equivalent verbose `.md`/JSON/YAML prompt at a measured token reduction of 50–82% depending on scope coverage.

This document is the canonical reference for v1.0.

## 1. Introduction

### 1.1 Goals

1. **Maximum semantic compression** — every glyph carries semantic weight; no decorative tokens.
2. **Mathematical integrity** — every block is sealed by a gematria checksum that any LLM able to sum integers can verify.
3. **Teleological derivation** — the purpose (telos) of a block is mathematically derivable from its keyword distribution; the user does not need to declare `purpose:`.
4. **Sapir-Whorf hybrid** — strong constraint on first read (vocabulary is closed); weak constraint when the consuming system has memory (NHE-style).
5. **Universal LLM comprehension** — comprehensible by any model with basic instruction-following capability, including models that have never seen `.ah` before, via the bootstrap parser.

### 1.2 Non-goals

- `.ah` is **not** Turing-complete. It is a declarative format, like SQL, HTML, CSS, or YAML.
- `.ah` is **not** a replacement for source code. It does not describe HOW to compute, only WHAT and WHY.
- `.ah` is **not** designed for human-only consumption — every design tradeoff favors LLM efficiency over human aesthetics.

### 1.3 Heritage

`.ah` is a synthesis of three lineages, taking the strengths of each while transcending their limitations:

- **COBOL** (1959) — declarative English vocabulary, predictable structure.
- **MARK IV** (1967) — key-value lines without punctuation; "YAML without colons".
- **TOON** (2025) — token-oriented compactness, schema-aware arrays.

It is grounded in seven scientific traditions: neurolinguistics, linguistics, semiotics, the Sapir-Whorf hypothesis, equidistributed sequences (Halton/Sobol), gematria (as deterministic checksum), and teleology.

## 2. Conventions

### 2.1 Notation

This specification uses BNF-like notation. `[ x ]` means optional, `{ x }` means zero or more, `<x>` is a non-terminal, `"x"` is a literal.

### 2.2 Character set

`.ah` files are UTF-8 encoded. The recommended character vocabulary for v1 is restricted to ASCII for keywords; UTF-8 is permitted in values.

### 2.3 Line discipline

- Lines are terminated by `\n` (LF) or `\r\n` (CRLF). The parser MUST treat both identically.
- Trailing whitespace SHOULD be stripped.
- Blank lines are permitted between sections and have no semantic value.
- A line either starts a new instruction (keyword, comment, or version header) or is part of a fenced code block.

## 3. Grammar

### 3.1 EBNF

```ebnf
file            = version_header , { line } ;
version_header  = "@v1.ah" , newline ;

line            = comment_line
                | keyword_line
                | checksum_line
                | code_block
                | blank_line ;

comment_line    = "#" , { non_newline_char } , newline ;
keyword_line    = keyword , ">" , value , newline ;
checksum_line   = "#>" , whitespace , integer , newline ;

keyword         = "@v1.ah" | "NAME" | "DESC" | "LICENSE" | "CONTEXT"
                | "TASK" | "CONSTRAINT" | "OUTPUT" | "TRADEOFF"
                | "THINK" | "RULE" | "SIMPLICITY" | "SURGICAL"
                | "GOAL" | "TRANSFORM" | "MULTI" | "CRITERIA"
                | "DIAGNOSE" | "TDD" | "ARCHITECTURE" | "COMPRESS"
                | "PLAN" | "REFINE" | "BOOTSTRAP" | "VALIDATE"
                | "HIERARCHY" | "ACTIVATE" ;

value           = value_token , { ( "." | "," ) , value_token } ;
value_token     = ? printable UTF-8 sequence excluding "." "," ">" "\n" ? ;

code_block      = "```" , [ language_tag ] , newline
                , { ? any line ? } ,
                  "```" , newline ;

integer         = digit , { digit } ;
digit           = "0" .. "9" ;
blank_line      = newline ;
newline         = "\n" | "\r\n" ;
non_newline_char= ? any character except "\n" "\r" ? ;
whitespace      = " " | "\t" ;
```

### 3.2 Composition rules

- **Dot (`.`)** composes a value into a compound semantic unit (namespacing). Example: `engineer.senior.backend` is one composed value.
- **Comma (`,`)** separates discrete list items. Example: `codigo, explicacao, exemplos` is a three-item list.
- These two roles are exclusive: dot is composition, comma is enumeration. The parser MUST treat them differently.

### 3.3 Hierarchy

`.ah` v1 is **flat**. There is no significant indentation. Every keyword line is a self-contained instruction. Hierarchy MUST be expressed via dot-composition in the value, not via nesting.

```ah
ROLE> engineer.senior.backend
DOMAIN> python.refactoring
```

Indentation, if present, is decorative and stripped by conformant parsers.

### 3.4 Comment marker

The comment marker is `#` (single character). Any line beginning with `#` (other than the checksum line `#>`) is a comment and contributes value `1` to the gematria checksum.

The checksum declaration line `#>` is a special form: it begins with `#` followed immediately by `>`, with no intervening characters. It is **not** counted in the checksum sum (it is the validator, not the body).

## 4. Canonical Keyword Table (v1)

Every canonical keyword has a fixed integer value. The vocabulary is **closed** in v1 — implementations MUST reject unknown keywords with a parse error, or treat them as comments with value 0 if running in lenient mode.

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

### 4.1 Rationale

Values are not derived from letter-position arithmetic. They are assigned to satisfy three constraints simultaneously:

1. **Distinctness within semantic clusters** — `RULE` (17) and `PLAN` (17) collide but live in unrelated clusters; semantically related keywords (`CONSTRAINT` 31, `SIMPLICITY` 31, `BOOTSTRAP` 31, `HIERARCHY` 31) cluster intentionally for low-discrepancy distribution.
2. **Bounded magnitude** — all values fit in [1, 32]; the largest possible single-line contribution is bounded.
3. **Telos derivability** — the distribution allows an LLM to infer the file's purpose from the histogram of values without reading any value content.

### 4.2 Reserved for v1.1+

The following identifiers are reserved and MUST NOT be used as values or aliases in v1:

`INPUT`, `IF`, `THEN`, `ELSE`, `LOOP`, `IMPORT`, `EXPORT`, `MEM`, `TIER`, `STYLE`, `LIMIT`, `STATEMENT`, `EMOTION`, `INTENTION`, `FALLBACK`, `RETRY`, `TIMEOUT`.

These are candidates for v2 extension and MUST NOT collide with the canonical table when added.

## 5. Gematria Checksum Computation

### 5.1 Formula

```
checksum = Σ (value(keyword_i) × occurrence_count(keyword_i))
```

Summed over every line in the file that contributes a value, **excluding** the `#>` checksum declaration line itself.

### 5.2 Algorithm

1. Scan the file line-by-line from the first non-empty line.
2. For each line:
   - If line starts with `@v1.ah`, add `12`.
   - Else if line starts with `#>`, do nothing (this is the validator).
   - Else if line starts with `#`, add `1`.
   - Else if line starts with a canonical keyword followed by `>`, add the keyword's value from the table.
   - Else if line is inside a fenced code block (between two ` ``` `), do nothing.
   - Else error: unknown line form.
3. Compare computed sum against the integer following `#>`.
4. PASS if equal; FAIL with delta if not.

### 5.3 Auto-correction

A conformant linter MAY offer auto-correction by writing the computed sum back to the `#>` line. Auto-correction MUST NOT modify any other line.

### 5.4 Properties

- **Deterministic** — same input always yields same checksum.
- **Model-agnostic** — verifiable by any LLM that can sum integers.
- **Tamper-evident** — any insertion, deletion, or keyword substitution changes the sum.
- **Not cryptographic** — gematria checksums are NOT collision-resistant against adversaries. They are integrity seals against drift, corruption, and accidental edits, not signatures against attack.

## 6. Output Format Modes

When an `.ah`-aware skill is loaded by a host LLM (Claude Code, Cursor, etc.), the host SHOULD support three response output modes and ask the user once which to use:

| Mode         | Form                                                      |
|--------------|-----------------------------------------------------------|
| `normal`     | Standard prose in any natural language. Default.          |
| `structured` | Full `@v1.ah` block with keys (`NAME>`, `DESC>`, etc.) and `#> N`. |
| `compact`    | Single-line dot-separated values, no keys, no checksum.   |

The user's choice MUST persist for the session and MUST be toggleable via `/ah normal`, `/ah structured`, `/ah compact`. If the user skips the prompt or is unsure, the default is `normal`.

User input is accepted in any natural language and is never required to be in `.ah` form.

## 7. Code Preservation Rule

The output mode applies **only** to the assistant's narrative prose. The following are always preserved verbatim regardless of mode:

- User-provided source code, in any language.
- Fenced code blocks (delimited by triple backticks).
- Identifiers, function names, type names, file paths.
- Diffs, patches, version-control fragments.
- Shell commands and command-line arguments.
- Error strings and stack traces.

This rule is non-negotiable and MUST be enforced at the parser level, not delegated to individual skills.

## 8. File Layout

A canonical `.ah` file has this structure:

```ah
@v1.ah
# block.name
NAME> ...
DESC> ...
[other keyword lines]

# section.heading
[keyword lines]

# gematria.checksum
#> N
```

The `@v1.ah` header MUST be the first non-empty line. The `#> N` checksum MUST be the last non-empty line.

## 9. Examples

### 9.1 Minimal — affirmation

```ah
@v1.ah
# affirmation
NAME> flying.affirmation
STATEMENT> yes.flying.alive
EMOTION> alive.excited
INTENTION> affirm.presence.moment
#> 90
```

(Note: `STATEMENT`, `EMOTION`, `INTENTION` are reserved for v1.1; in v1 the equivalent is `DESC>` + dot composition. Above is illustrative of intent, not v1-conformant.)

### 9.2 Minimal — refactor task (v1-conformant)

```ah
@v1.ah
# example.refactor
NAME> example.refactor
TASK> refactor.calculate.average
CONTEXT> list.of.numbers
OUTPUT> optimized.function.tests
CONSTRAINT> no.external.libs
CONSTRAINT> surgical.changes.only
#> 159
```

Computation: `12 + 1 + 14 + 19 + 27 + 24 + 31 + 31 = 159`.

### 9.3 Reference — supreme-coding-guidelines

See `skills/supreme-coding-guidelines/SKILL.md` (`#> 1052`).

### 9.4 Reference — ah-parser

See `skills/ah-parser/SKILL.md` (`#> 569`).

### 9.5 Reference — supreme-project-audit

See `skills/supreme-project-audit/SKILL.md` (`#> 1224`).

### 9.6 Reference — supreme-problem-solving

See `skills/supreme-problem-solving/SKILL.md` (`#> 1187`).

### 9.7 Reference — supreme-ai-engineering

See `skills/supreme-ai-engineering/SKILL.md` (`#> 1227`).

### 9.8 Reference — supreme-npm-node

See `skills/supreme-npm-node/SKILL.md` (`#> 1269`).

### 9.9 Reference — supreme-content-craft

See `skills/supreme-content-craft/SKILL.md` (`#> 2602`).

### 9.10 Reference — supreme-council

See `skills/supreme-council/SKILL.md` (`#> 1773`).

### 9.11 Reference — supreme-benchmarking

See `skills/supreme-benchmarking/SKILL.md` (`#> 1928`).

### 9.12 Reference — supreme-diagramming

See `skills/supreme-diagramming/SKILL.md` (`#> 1188`).

### 9.13 Reference — supreme-ai-governance

See `skills/supreme-ai-governance/SKILL.md` (`#> 2381`).

## 10. Conformance

A conformant `.ah` parser MUST:

1. Reject files whose first non-empty line is not `@v1.ah` (or a recognized future version header).
2. Reject keyword lines using identifiers not in the canonical table (in strict mode).
3. Compute the gematria checksum exactly as specified in §5.
4. Treat code-fenced blocks as opaque, preserving their content verbatim.
5. Report checksum mismatch with the computed value and the declared value.

A conformant `.ah` host (LLM agent) SHOULD additionally:

6. Implement the three output modes of §6.
7. Enforce the code preservation rule of §7.
8. Accept user input in any natural language.

## 11. Versioning Policy

- The version header is `@v<MAJOR>.ah`, e.g., `@v1.ah`, `@v2.ah`.
- Major versions MAY add keywords to the canonical table. Major versions MUST NOT remove or renumber existing keywords.
- Minor and patch revisions of v1 are tracked in this SPEC's `Spec date` and changelog. Files do NOT carry minor version numbers; the major version is sufficient.
- A v2 parser MUST be able to read v1 files (forward compatibility).
- A v1 parser MAY reject v2 files with a clear error message.

## 12. References

- Reference implementation skills: [`skills/ah-parser/SKILL.md`](skills/ah-parser/SKILL.md), [`skills/supreme-coding-guidelines/SKILL.md`](skills/supreme-coding-guidelines/SKILL.md), [`skills/supreme-project-audit/SKILL.md`](skills/supreme-project-audit/SKILL.md), [`skills/supreme-problem-solving/SKILL.md`](skills/supreme-problem-solving/SKILL.md), [`skills/supreme-ai-engineering/SKILL.md`](skills/supreme-ai-engineering/SKILL.md), [`skills/supreme-npm-node/SKILL.md`](skills/supreme-npm-node/SKILL.md), [`skills/supreme-content-craft/SKILL.md`](skills/supreme-content-craft/SKILL.md), [`skills/supreme-council/SKILL.md`](skills/supreme-council/SKILL.md), [`skills/supreme-benchmarking/SKILL.md`](skills/supreme-benchmarking/SKILL.md), [`skills/supreme-diagramming/SKILL.md`](skills/supreme-diagramming/SKILL.md), [`skills/supreme-ai-governance/SKILL.md`](skills/supreme-ai-governance/SKILL.md)
- Reference linter: [`scripts/ah-lint`](scripts/ah-lint)
- Benchmark methodology: [`BENCHMARK.md`](BENCHMARK.md)
- TOON format (heritage): https://github.com/toon-format/toon

## 13. Changelog

- **1.9.0** (2026-06-28) — Bundle expansion: added `supreme-ai-governance` skill (first-in-the-world AI governance and compliance discipline for AI Governance Officers, Compliance Leads, Risk Managers, DPOs, Legal and Privacy Counsel, CISOs, AI/ML/LLM engineers and architects, AI researchers, internal auditors, CTOs, and founders). Operationalizes ISO/IEC 42001:2023 — the certifiable AI Management System (Harmonized Structure clauses 4–10, the ~38 Annex A reference controls across 9 objectives A.2–A.10, the Statement of Applicability, and the AI System Impact Assessment now backed by ISO/IEC 42005:2025) — together with the EU AI Act (Regulation 2024/1689: prohibited practices, high-risk Annex I/III, transparency, GPAI and systemic-risk obligations, conformity assessment, CE marking, EU database registration, FRIA, post-market monitoring, serious-incident reporting, penalties up to 35M EUR or 7% of global turnover, and the June 2026 Digital Omnibus timeline that defers high-risk obligations toward December 2027 and August 2028 pending final adoption), the NIST AI Risk Management Framework (GOVERN/MAP/MEASURE/MANAGE plus the Generative AI Profile NIST-AI-600-1), and the global regulatory map outside the EU (US executive orders and Texas/Colorado/California/Utah/Illinois state law, UK principles-based approach and the Data Use and Access Act 2025, China generative-AI and AI-content labeling rules, Canada Quebec Law 25 after AIDA lapsed, Brazil PL 2338, and the OECD/UNESCO/Council-of-Europe/G7/UN instruments). Maps the sectoral overlays (GDPR Art 22 and DPIA, financial model risk, medical-device regimes, employment bias-audit law) and integrates through the Harmonized Structure with ISO/IEC 27001, ISO/IEC 27701, and ISO 9001 plus the ISO/IEC SC42 standards family. Operates through four cognitive lenses — First-Principle Thinker, Expansionist, Outsider, and an Executor that never tries to please — and delivers a tabular gap assessment, Statement of Applicability, control map, evidence register, and remediation roadmap. Compliance-engineering structure, not legal advice; verify current law before relying on any date because regulation moves. The skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-ai-governance/SKILL.md` → `#> 2381`. All five IDE rule directories received the new mirror — 50 mirror files total across the bundle (10 behavioral skills × 5 IDEs).
- **1.8.0** (2026-06-12) — Bundle expansion: added `supreme-diagramming` skill (living-diagram companion for Product/Software/LLM architects, Tech Leads, Technical Writers, DevOps, and AI researchers). Treats diagrams — architecture, flow, ERD, sequence, class, C4, state — as living, versioned artifacts described in a deterministic declarative layer validated by gematria checksum, then compiled to portable targets (Mermaid, D2, draw.io XML, Excalidraw) with no proprietary lock-in. Applies a describe-first pipeline (natural language to declarative spec to deterministic validation to compiled format), inverts the fragile vision-first verification of legacy tools by running deterministic structural and aesthetic checks first and using model vision only as last-resort reinforcement, keeps the diagram as a file next to the code so it is diffed in pull requests and evolved rather than recreated, remembers prior diagrams, and degrades gracefully to Mermaid or D2 text with no heavy desktop dependency. Embeds the seven craft lessons of professional SKILL.md authoring (lean main file with demand-loaded references, explicit when-not-to-use boundary, self-verification before delivery, graceful degradation, environment anticipation, surgical repair of known defects, honest versioned changelog). The skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-diagramming/SKILL.md` → `#> 1188`. All five IDE rule directories received the new mirror — 45 mirror files total across the bundle (9 behavioral skills × 5 IDEs).
- **1.7.0** (2026-06-07) — Bundle expansion: added `supreme-benchmarking` skill (principal research and data-science benchmarking discipline for AI/ML/LLM/npm projects, inspired by the published methodologies of OpenAI, Anthropic, Google DeepMind, xAI, DeepSeek, Xiaomi MiMo, Hugging Face, and Unsloth. Applies four cognitive personas to benchmark design — First-Principle construct validity, Expansionist ignored-dimension coverage, Outsider preregistration and baseline re-run integrity, Executor controlled protocol that publishes uncomfortable results unchanged. Enforces statistical rigor gates (CI95, median+IQR, effect size, multi-seed variance, multiple-comparison correction), contamination and saturation defense (canary strings, n-gram overlap, held-out private sets), LLM protocol (pass-at-k and temperature disclosure, prompt-sensitivity spread, eval-harness commit pinning across lm-eval-harness/HELM/lighteval/inspect-ai/promptfoo), npm/Node protocol (tinybench/mitata micro, hyperfine CLI, size-limit bundle, JIT warmup and GC isolation), reporting in the Anthropic/Hugging Face/Unsloth style (benchmark card analogous to model card, bold-best tables with CI column, bar charts with error bars, efficiency-frontier scatter, raw JSONL published), one-command reproducibility package, honest disclosure with negative results in the main table, and continuous CI regression tracking). The skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-benchmarking/SKILL.md` → `#> 1928`. All five IDE rule directories received the new mirror — 40 mirror files total across the bundle (8 behavioral skills × 5 IDEs).
- **1.6.0** (2026-05-20) — Bundle expansion: added `supreme-council` skill (principal multi-perspective deliberation council for ambiguous high-stakes decisions across Product, Engineering, AI/ML/LLM Architecture, Research, Operations, Strategy; convenes four distinct cognitive personas — First-Principle Thinker, Expansionist, Outsider, Executor — and runs a three-round protocol inspired by Karpathy's LLM Council methodology: individual independent outputs → anonymous peer review → synthesis that preserves dissent. Integrates Spec-Kit-style phasing — Constitution/Specify/Clarify/Plan/Tasks/Analyze — plus Klein premortem with minimum five failure scenarios, early-warning signals, and reversibility paths, plus Cynefin-style uncertainty handling with kill criteria and adaptation checkpoints. Includes post-decision audit and calibration loop. Cláusula non-negotiable: never tries to please the user — honest assessment over comfortable answer, minority position always preserved). The skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-council/SKILL.md` → `#> 1773`. All five IDE rule directories received the new mirror — 35 mirror files total across the bundle (7 behavioral skills × 5 IDEs).
- **1.5.0** (2026-05-20) — Bundle expansion: added `supreme-content-craft` skill (principal content craft discipline for SEO, SEM, Header Binding (HTML semantic + HTTP + AdTech), Copywriting, Marketing, Branding, Growth, Content Strategy, Technical/UX/Ghostwriting, Writers, Authors, Researchers, professional Editors; integrates six persuasion frameworks — AIDA, Cialdini's six principles of Influence, StoryBrand SB7 + PAS + FAB + Schwartz five awareness levels + Made to Stick SUCCESs + Ogilvy + Hopkins, Schopenhauer's ethical Eristic Dialectic subset (stratagems 7/13/14/17/26 plus explicit exclusion of manipulative stratagems), Joe Girard's "How to Sell Anything to Anybody" (Law of 250, Mt. Everest, Girard Chair, after-sale service), and Cialdini Pre-Suasion; enforces content-structure pattern Features→Project→How→Benefits→Sales→Purchase; provides 15 quality tool gates covering Grammar/Paraphraser/Plagiarism/AI Detector/Humanizer/Translator/Summarizer/Citation/Readability/Tone/Headline/Schema Validator/Meta Generator/SERP-Backlink-Gap/Image-Alt-OCR; ethical-persuasion-only constraint at the same trust tier as instruction hierarchy). The skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-content-craft/SKILL.md` → `#> 2602`. All five IDE rule directories received the new mirror — 30 mirror files total across the bundle (6 behavioral skills × 5 IDEs).
- **1.4.0** (2026-05-20) — Bundle expansion: added `supreme-npm-node` skill (principal NPM/NPX/NPMJS/Node engineering discipline for Tech Leads, DevOps, Backend, Frontend, Product/AI/ML/LLM engineers, LLM architects, AI researchers, QA engineers, and Software Quality engineers; enforces a latest-version-always policy via `ncu -u` before any install, TypeScript strict mode with every check enabled, `satisfies` over `as`, `unknown` over `any`, discriminated unions over optional flags, branded types for opaque identifiers, `files` allowlist over `.npmignore`, OIDC provenance attestation, supply-chain audit gates, pnpm workspaces, and continuous upgrade cadence). The skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-npm-node/SKILL.md` → `#> 1269`. All five IDE rule directories (Claude Code, Cursor, Trae, Zed, Kiro) received the new mirror — 25 mirror files total across the bundle.
- **1.3.0** (2026-05-20) — Bundle expansion: added `supreme-ai-engineering` skill (principal AI engineering discipline for Product/AI/ML/LLM engineers, LLM architects, AI researchers, QA engineers, and Software Quality engineers building production AI/ML/LLM/MLOps/LLMOps systems; enforces eval-first design, deterministic feedback loops, pipeline contracts, governance, reliability, QA rigor, and operational excellence). The skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-ai-engineering/SKILL.md` → `#> 1227`. Also added Kiro IDE support (`.kiro/rules/`) and mirrored all four behavioral skills (`supreme-coding-guidelines`, `supreme-project-audit`, `supreme-problem-solving`, `supreme-ai-engineering`) into all five IDE rule directories (Claude Code, Cursor, Trae, Zed, Kiro) — 20 mirror files total, each preserving the canonical gematria checksum of its source skill.
- **1.2.0** (2026-05-03) — Bundle expansion: added `supreme-problem-solving` skill (analyze, verify, diagnose, and solve problems from simple to complex; output is a structured markdown table with columns problem / repro / hypothesis / evidence / fix / verification / owner / ETA). The skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-problem-solving/SKILL.md` → `#> 1187`.
- **1.1.0** (2026-05-03) — Bundle expansion: added `supreme-project-audit` skill (evidence-driven audit for Product/AI/ML/LLM engineers, LLM architects, and AI researchers). The audit skill uses only the canonical keyword set from §4; no language or grammar changes. Reference checksum: `skills/supreme-project-audit/SKILL.md` → `#> 1224`.
- **1.0.1** (2026-05-03) — Documentation revision. README claims tightened to match `BENCHMARK.md` methodology; obsolete competitive overclaims removed; file tree completed. No language or grammar changes; all checksums and conformance rules from 1.0.0 remain valid.
- **1.0.0** (2026-05-03) — Initial canonical specification. Ratified the three foundational decisions: hierarchy = flat (MARK IV style), list separator = comma, comment marker = `#`. Replaced legacy `CHECK>`/`TEST>` with `VALIDATE>`. Established three-mode output protocol and code preservation rule.
