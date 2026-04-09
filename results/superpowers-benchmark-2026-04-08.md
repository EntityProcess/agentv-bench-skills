# Superpowers Benchmark Results — 2026-04-08

Rerun after merging fix(core): extract system messages in prompt builder for LLM grader (PR #983).
Previous run was tainted by bug #982 (bare `prompt:` in assertions replaced the entire grader template).

## Results

Eval: `evals/reasoning/logic-puzzle.EVAL.yaml`

| Experiment | Target | Test | Score |
|---|---|---|---|
| without-superpowers | gemini | knights-knaves-basic | 1.000 |
| without-superpowers | gemini | river-crossing | 1.000 |
| without-superpowers | azure | knights-knaves-basic | 1.000 |
| without-superpowers | azure | river-crossing | 0.980 |
| with-superpowers | gemini | knights-knaves-basic | 1.000 |
| with-superpowers | gemini | river-crossing | 1.000 |
| with-superpowers | azure | knights-knaves-basic | 1.000 |
| with-superpowers | azure | river-crossing | 0.980 |

## Summary

| Experiment | Target | Pass Rate | Avg Score |
|---|---|---|---|
| without-superpowers | gemini | 100% | 1.000 |
| without-superpowers | azure | 100% | 0.990 |
| with-superpowers | gemini | 100% | 1.000 |
| with-superpowers | azure | 100% | 0.990 |

## Comparison vs tainted results

| Experiment | Target | Before (bug #982) | After (fix #983) |
|---|---|---|---|
| without-superpowers | gemini | 100% / 1.000 | 100% / 1.000 |
| without-superpowers | azure | 50% / 0.735 | 100% / 0.990 |
| with-superpowers | gemini | 50% / 0.750 | 100% / 1.000 |
| with-superpowers | azure | 0% / 0.250 | 100% / 0.990 |

The previous finding that `with-superpowers` performed worse than `without-superpowers` was entirely a grader artifact.
With the fix applied, both experiments score at parity (~99-100%) across providers.
