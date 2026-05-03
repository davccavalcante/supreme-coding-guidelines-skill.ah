# `.ah` Language Specification

```
Version       : 1.0.1
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

- Reference implementation skills: [`skills/ah-parser/SKILL.md`](skills/ah-parser/SKILL.md), [`skills/supreme-coding-guidelines/SKILL.md`](skills/supreme-coding-guidelines/SKILL.md)
- Reference linter: [`scripts/ah-lint`](scripts/ah-lint)
- Benchmark methodology: [`BENCHMARK.md`](BENCHMARK.md)
- TOON format (heritage): https://github.com/toon-format/toon

## 13. Changelog

- **1.0.1** (2026-05-03) — Documentation revision. README claims tightened to match `BENCHMARK.md` methodology; obsolete competitive overclaims removed; file tree completed. No language or grammar changes; all checksums and conformance rules from 1.0.0 remain valid.
- **1.0.0** (2026-05-03) — Initial canonical specification. Ratified the three foundational decisions: hierarchy = flat (MARK IV style), list separator = comma, comment marker = `#`. Replaced legacy `CHECK>`/`TEST>` with `VALIDATE>`. Established three-mode output protocol and code preservation rule.
