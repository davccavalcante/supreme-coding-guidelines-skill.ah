# `.ah` Benchmark Methodology

```
Status         : Methodology v1 (pre-execution)
Spec date      : 2026-05-03
Author         : David C. Cavalcante
Target run     : Q3 2026 — published results in repo as BENCHMARK_RESULTS.md
```

This document specifies the benchmark protocol that will produce the empirical evidence supporting `.ah`'s competitive claims. It is published BEFORE the run so that the methodology is reviewable and the results are not retro-engineered.

## 1. What is being measured

For each (skill_format × model × task) tuple we measure:

1. **Input tokens** — number of tokens in the prompt sent to the model (skill prompt + task prompt).
2. **Output tokens** — number of tokens in the model's response.
3. **Accuracy** — binary pass/fail of an automated rubric per task (defined in §4).
4. **Scope drift** — count of changes to files outside the explicitly-named target file.
5. **Iteration count** — number of correction rounds the user (or rubric loop) had to issue before the output passed.

From these we derive the headline composite metric:

```
efficiency = (accuracy × 1000) / (input_tokens + output_tokens)
```

Higher is better. This is the same formula TOON publishes, for direct comparability.

## 2. Comparators

Five skill-format conditions, each applied to the same task set with the same model.

| ID | Condition                                | Source                                                          |
|----|------------------------------------------|-----------------------------------------------------------------|
| A  | Plain markdown (no skill)                | empty prompt; baseline                                          |
| B  | Karpathy Guidelines `CLAUDE.md`          | `forrestchang/andrej-karpathy-skills`                           |
| C  | Caveman skill (full mode)                | `JuliusBrussee/caveman`                                         |
| D  | Matt Pocock `diagnose` + `tdd` skills    | `mattpocock/skills`                                             |
| E  | `.ah` `supreme-coding-guidelines` skill  | `davccavalcante/supreme-coding-guidelines-skill.ah` (this repo) |

## 3. Models

Four models, each accessed via its standard API. All sampling temperature 0.0 (deterministic where possible). All other parameters at provider defaults unless noted.

| ID | Model                          |
|----|--------------------------------|
| M1 | Claude Opus 4.7 (1M context)   |
| M2 | Claude Sonnet 4.6              |
| M3 | GPT-5 (latest production)      |
| M4 | Gemini 2.5 Pro                 |

Five runs per (condition × model × task) tuple to capture variance. Median used as the primary statistic; standard deviation reported.

## 4. Task set

Ten tasks across three categories. Tasks are deliberately small and have an objective rubric.

### 4.1 Refactor (4 tasks)

- **R1** — Refactor a 40-line `calculate_average(list)` Python function for clarity. Rubric: function preserves I/O contract; no external libs added; resulting code <= 30 lines; passes the input test suite.
- **R2** — Refactor a callback-based JS function to async/await. Rubric: same observable behavior; tests pass.
- **R3** — Extract a duplicated SQL clause into a named CTE across three queries. Rubric: queries return same result set on the fixture DB.
- **R4** — Convert a CommonJS module to ESM in a small package. Rubric: dependents still import successfully.

### 4.2 Bug fix (3 tasks)

- **B1** — Off-by-one in a binary search. Rubric: regression test reproduces the bug pre-fix and passes post-fix.
- **B2** — N+1 query in an ORM call. Rubric: query count drops from O(n) to O(1).
- **B3** — Race condition in a JavaScript timer-based animation. Rubric: deterministic playwright test that previously flaked now passes 100/100 runs.

### 4.3 New feature (3 tasks)

- **N1** — Add input validation to a CLI argument parser. Rubric: invalid inputs produce stderr + non-zero exit, valid inputs unchanged.
- **N2** — Add a paginated endpoint to a REST API. Rubric: returns `?page=1` correctly; respects `limit`; emits `Link: rel=next` header.
- **N3** — Add unit tests to a previously untested utility module to 80% line coverage. Rubric: coverage tool reports >= 80%.

Each task ships with: the starting file(s), the rubric script (executable), and the expected fixture inputs.

## 5. Procedure

For each (condition × model × task):

1. **Set up.** Apply the skill format (condition) by loading its prompt verbatim. For `.ah`, this means loading `ah-parser` then `supreme-coding-guidelines` per the canonical install. Output mode = compact.
2. **Issue the task prompt.** Use a fixed task template: `Implement <task description>. Edit only <target_file>.` No additional context.
3. **Capture I/O.** Record input tokens, output tokens, the response itself, and a timestamped trace.
4. **Score.** Run the rubric script automatically. Score 1 if pass, 0 if fail.
5. **Measure scope drift.** Diff the working tree before and after; count files changed outside `<target_file>`.
6. **Iterate.** If the rubric fails, issue at most one correction round: `Your previous solution failed: <rubric output>. Try again.` Score the post-iteration result. Record `iteration_count = 1` or `2`.
7. **Reset.** Restore the working tree to the starting fixture before the next run.

## 6. Reporting

Results are published as a Markdown table per category, plus aggregate. Each cell shows median efficiency with stdev.

```
Task R1 — Refactor calculate_average

| Condition       | M1 (Opus 4.7) | M2 (Sonnet 4.6) | M3 (GPT-5)   | M4 (Gemini 2.5) |
|-----------------|---------------|-----------------|--------------|-----------------|
| A. Plain        | x.x ± y.y     | …               | …            | …               |
| B. Karpathy     | …             | …               | …            | …               |
| C. Caveman      | …             | …               | …            | …               |
| D. Matt Pocock  | …             | …               | …            | …               |
| E. .ah          | …             | …               | …            | …               |
```

Plus three summary plots:

- Efficiency by condition, averaged across all tasks and models.
- Token reduction (vs Plain baseline) by condition.
- Scope drift count by condition.

Raw per-run data is published as `bench/raw/*.jsonl`. The rubric scripts and fixtures are published as `bench/tasks/`.

## 7. Disclosure of expected biases

To preempt confirmation-bias accusations:

- The author of `.ah` (David C. Cavalcante) is NOT the model running the rubric, NOT the model judging accuracy, and NOT involved in scoring. Rubrics are deterministic test scripts.
- Caveman, Karpathy, and Matt Pocock skills are loaded verbatim from their repos at a pinned commit, recorded in `bench/manifest.json`. No edits.
- `.ah` is loaded verbatim from `skills/supreme-coding-guidelines/SKILL.md` at the same commit. No special treatment.
- Token counts use the host model's official tokenizer. For Anthropic models, `anthropic.tokenizer`. For OpenAI, `tiktoken`. For Gemini, the published count endpoint.

If `.ah` does NOT outperform the comparators on a given metric, that result is published unchanged and `BENCHMARK_RESULTS.md` documents it. The competitive analysis in the README will be revised to reflect the measured truth.

## 8. Schedule

| Milestone                                                 | Target date |
|-----------------------------------------------------------|-------------|
| Methodology peer review (this doc)                        | 2026-Q2     |
| Rubric scripts + fixtures published in `bench/`           | 2026-Q2     |
| First full run (M1 only, all conditions, all tasks)       | 2026-Q2     |
| Full matrix run (M1–M4, all conditions, all tasks)        | 2026-Q3     |
| Results published as `BENCHMARK_RESULTS.md`               | 2026-Q3     |

## 9. Honesty clause

The current README claims a 78–82% token reduction. That number comes from a single before/after example, not the methodology above. Until §8 is executed, the claim is provisional. After §8 is executed, the claim is replaced by the measured median ± stdev across all (condition × model × task) cells, with full disclosure of where `.ah` wins, ties, and loses.
