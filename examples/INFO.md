# Examples — Supreme Guidelines in Action

These examples show the contrast between traditional verbose prompts and the Supreme Coding Guidelines skill in `.ah` format.

- **Before** — Typical verbose prompt or standard `SKILL.md`
- **After** — Compact `.ah` block with canonical gematria checksum

All examples assume the canonical install: `ah-parser` is loaded once per session, then the supreme-coding-guidelines skill is always-on.

## What you get when the skill is active

- **Three-mode output protocol** — at parser activation, the assistant asks once whether responses should be in normal language, `.ah` structured, or `.ah` compact form. Default is normal. The choice persists for the session and is toggleable via `/ah normal`, `/ah structured`, `/ah compact`.
- **Code is always verbatim** — the chosen mode applies only to assistant prose. User code, diffs, commands, identifiers, and error strings are never reformatted into dot-notation.
- **Mathematical integrity** — every `.ah` file ends with `#> N`, the gematria checksum. The LLM verifies it on read and rejects (or auto-corrects) any block whose computed sum does not match the declared value.
- **Surgical, verifiable, disciplined behavior** — eight integrated rule sections cover think-before-coding, simplicity-first, surgical changes, goal-driven execution, diagnose loop, TDD, compress mode, and plan-then-execute.
- **Persistent across IDEs** — Claude Code, Cursor, Trae, Zed, Kiro, and any agent that respects `SKILL.md`. Four skills mirrored into each IDE's auto-apply rule directory.

Load the skill once and these examples work instantly.

## See also

The same bundle ships four additional on-demand skills for Tech Leads, DevOps, Backend, Frontend, Product / AI / ML / LLM engineers, LLM architects, AI researchers, QA engineers, and Software Quality engineers:

- [`supreme-project-audit`](../skills/supreme-project-audit/SKILL.md) — invoke via `/supreme-project-audit` for evidence-driven audits. Eight dimensions: read-before-findings, evidence chain, severity discipline, coverage map, threat modeling, cost & reproducibility, compressed findings, plan-then-execute.
- [`supreme-problem-solving`](../skills/supreme-problem-solving/SKILL.md) — invoke via `/supreme-problem-solving` to analyze, verify, diagnose, and solve specific problems (simple to complex) with a structured tabular deliverable. Eight sections: define-problem, reproduce, competing-hypotheses, instrument-evidence, minimum-invasive-fix, verify-and-validate, tabular-report, post-mortem.
- [`supreme-ai-engineering`](../skills/supreme-ai-engineering/SKILL.md) — invoke via `/supreme-ai-engineering` for principal AI engineering discipline on production AI/ML/LLM/MLOps/LLMOps systems. Eight sections: understand-before-building, measurable-success, feedback-loops-first, pipeline-contracts-and-gates, governance-architecture-and-registry, production-reliability-safety-and-chaos, quality-engineering-and-research-rigor, operational-excellence-and-refinement.
- [`supreme-npm-node`](../skills/supreme-npm-node/SKILL.md) — invoke via `/supreme-npm-node` for NPM/NPX/NPMJS/Node engineering with a latest-version-always policy via `ncu -u`. Eight sections: understand-ecosystem, always-latest-ncu-upgrade, typescript-strict-mode-maximum, development-workflow-scripts, package-publishing-discipline-architecture, production-reliability-supply-chain-security, quality-gates-before-publish, maintenance-continuous-upgrade-cycle.
- [`supreme-content-craft`](../skills/supreme-content-craft/SKILL.md) — invoke via `/supreme-content-craft` for SEO, SEM, Header Binding (HTML/HTTP/AdTech), Copywriting, Marketing, Branding, Growth, Content Strategy, Technical/UX/Ghostwriting, Writers, Authors, Researchers, Editors. Thirteen sections covering: audience/intent/brand voice, keyword/entity/GEO SEO, content structure (Features/Project/How/Benefits/Sales/Purchase), AIDA framework, Cialdini's six principles, StoryBrand/PAS/FAB/Schwartz/SUCCESs/Ogilvy/Hopkins, Schopenhauer ethical eristic (stratagems 7/13/14/17/26 with manipulative ones explicitly excluded), Joe Girard Law of 250, content production discipline, on-page SEO architecture, header binding triple coverage, fifteen quality tool gates (Grammar/Paraphraser/Plagiarism/AI Detector/Humanizer/Translator/Summarizer/Citation/Readability/Tone/Headline/Schema Validator/Meta Generator/SERP-Backlink-Gap/Image-Alt-OCR), measurement + refresh + repurpose. Ethical persuasion only.
- [`supreme-council`](../skills/supreme-council/SKILL.md) — invoke via `/supreme-council` (or "council this", "pressure-test this", "stress-test this", "war room this") for ambiguous high-stakes decisions. Twelve sections covering: when to invoke, frame decision question as constitution, four cognitive personas (First-Principle Thinker, Expansionist, Outsider, Executor), anonymous peer review round, dissent synthesis preserving minority, tabular deliverable, Klein premortem (minimum 5 failure scenarios), Cynefin uncertainty iteration, follow-up audit + calibration. Never tries to please the user — honest assessment over comfortable answer is non-negotiable.
