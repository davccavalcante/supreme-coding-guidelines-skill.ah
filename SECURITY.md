# Security Policy

## What this bundle is

The `.ah` skill bundle is **markdown-only**. It ships no executable code, no shell scripts, no network calls, and no filesystem access beyond the host agent's own skill loader. Every `SKILL.md` is a sequence of declarative `KEY>value` lines parsed by the host LLM agent (Claude Code, Cursor, Trae, Zed, Kiro, Codex, Gemini CLI, and others). The host enforces every action; the skill itself is inert text.

The only script in the repository is `scripts/ah-lint` — a single-file Python validator (standard library only) that sums integer keyword values from the canonical table in [`SPEC.md`](SPEC.md). It performs no network I/O, no shell execution, and no file I/O beyond the paths passed on the command line.

## Reporting a vulnerability

Email security disclosures via [takk.ag](https://takk.ag/) (use the contact form). Do not open a public GitHub issue for security reports. Confirmed reports receive a response within 72 hours; critical reports trigger a same-day patch release.

## Documented scanner false positives

Automated scanners (Snyk, Socket, and generative-AI judges) run on install via `npx skills add`. The following ratings are known content artifacts, not real code vulnerabilities, and are documented here for transparency.

### Snyk High Risk on the four oldest skills (stale cached scan)

As of the v1.8.0 install scan, four skills (`ah-parser`, `supreme-coding-guidelines`, `supreme-problem-solving`, `supreme-project-audit`) carried a Snyk High Risk rating while the six newer skills were unrated. Root-cause analysis showed the rating tracks **scan date**, not content — the four flagged skills were last scanned weeks earlier under an older, noisier ruleset and the result was cached. The skills are markdown-only and bundle no executable code. A fresh re-scan under the current ruleset is expected to clear the rating with no content change.

### OWASP LLM01 defense phrasing

Several skills declare an instruction-hierarchy constraint stating that skill directives sit at a higher trust tier than later user-supplied context. This is the canonical OWASP LLM01 (Prompt Injection) **defense** pattern — the skill defends against override attempts. ML-based prompt scanners may recognize the phrasing as a prompt-injection signature even though the intent is the opposite.

### Security-education vocabulary

`supreme-project-audit` and `supreme-ai-engineering` contain dense security vocabulary (STRIDE, OWASP LLM Top 10, prompt injection, data exfiltration, training poisoning, PII redaction, CVE, SBOM) because their job is threat modeling and audit. This vocabulary is descriptive of defensive practice, not an exploit payload.

## Supply-chain integrity

- Every `.ah` file ends with `#> N`, a deterministic gematria checksum verifiable against the canonical keyword table in [`SPEC.md`](SPEC.md). Tampering changes the sum and is detectable without external tooling.
- `scripts/ah-lint` validates checksums locally.
- The plugin manifest validates against [`schemastore.org/claude-code-plugin-manifest.json`](https://www.schemastore.org/claude-code-plugin-manifest.json) and the marketplace manifest against [`schemastore.org/claude-code-marketplace.json`](https://www.schemastore.org/claude-code-marketplace.json).
- The repository contains no hardcoded secrets, tokens, API keys, or cryptocurrency addresses. Sponsorship is routed solely through [github.com/sponsors/davccavalcante](https://github.com/sponsors/davccavalcante).

## Scope of the security model

The bundle protects file integrity (gematria checksum), schema correctness (schemastore validation), code preservation (the parser never transforms user code), prompt-injection resistance (OWASP LLM01 defense constraint), and input-language flexibility. It does **not** protect against compromise of the host agent itself, MCP server vulnerabilities, or downstream skills installed alongside it. Defense in depth is the responsibility of the user's agent and operating environment.
