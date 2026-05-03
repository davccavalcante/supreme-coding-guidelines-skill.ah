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
- **Persistent across IDEs** — Claude Code, Cursor, Trae, Zed, and any agent that respects `SKILL.md`.

Load the skill once and these examples work instantly.
