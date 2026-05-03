# Before vs After — Token Reduction Demonstration

## BEFORE (traditional verbose prompt)

```text
You are a senior software engineer. When writing or refactoring code, follow these guidelines:
- Think before coding. Never assume anything. Always state your assumptions explicitly.
- Prefer simplicity. Write the minimum code that solves the problem. Avoid over-engineering.
- Make surgical changes only. Never touch unrelated code.
- Define clear success criteria and verify them.
- Use TDD when possible.
- Keep responses concise and respect the user's chosen output format.
- Never reformat the user's code; preserve it verbatim.

Now refactor the following function...
```

## AFTER (Supreme Guidelines `.ah`)

```ah
@v1.ah
# supreme.coding.guidelines
TASK> refactor.function
CONTEXT> old.code
OUTPUT> new.code.explanation.tests
CONSTRAINT> surgical.changes.only
CONSTRAINT> simplicity.first
CONSTRAINT> goal.driven.execution
CONSTRAINT> compress.mode.applies.assistant.prose.only.never.transform.user.code.identifiers
#> 207
```

## What changed

- **Same behavioral coverage** — every rule from the verbose block survives in the compact `.ah` form.
- **Mathematical integrity** — the trailing `#> 207` is the canonical gematria checksum (sum of keyword values per the v1 table). Any LLM that can sum integers can verify the block was not corrupted in transit.
- **Explicit code-preservation guarantee** — the final `CONSTRAINT>` line locks in: `.ah` compress mode applies only to assistant prose, never to the user's code, identifiers, diffs, or commands.
- **User chooses the output mode** — after the parser is loaded, the assistant asks once whether responses should be in normal language, `.ah` structured, or `.ah` compact. Default is normal.

## Why it matters

Traditional prompt verbosity buys nothing the `.ah` form cannot deliver more compactly. The compactness is not a stylistic choice — it is a teleological commitment: every keyword is fixed in vocabulary, every value carries its weight, every block is checksum-validated.

The reduction holds across every `.ah` skill file and is most pronounced in long agentic sessions where the same skill is read many times.
