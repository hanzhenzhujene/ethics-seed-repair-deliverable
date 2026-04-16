# V9 Seed-Improvement Report

## V9 Seed-Improvement Design

| Component | V9 Setting |
| --- | --- |
| Primary comparison | `iterative_from_seed` vs `seed_frozen` |
| Secondary comparison | `iterative_from_seed` vs `teacher_single_full_budget_from_seed` |
| Benchmark role | `expert_fixed_benchmark` is evaluated only after prompts are frozen and is never shown to the teacher |
| Evidence schedule | 3 large rounds with teacher/calibration/selector batches of 512/512/512 |
| Teacher packet | compare current prompt against the frozen seed on the same teacher batch, with current-vs-seed win/loss buckets |
| Selector conservatism | no-change default, revert to best-so-far iterative prompt when a newly adopted prompt underperforms it |
| Scientific intent | test whether a strong teacher can iteratively improve a reasonable frozen seed prompt, while tracking how much of the gap to the expert benchmark gets closed |

## Primary Question

Did the optimized target `iterative_from_seed` improve over the baseline `seed_frozen` under the v9 large-round seed-improvement protocol? Yes.

## V9 Seed-Improvement Cross-Fitted Result

Optimized target: `iterative_from_seed`. Baseline: `seed_frozen`.

| Metric | empty_prompt (null control) | seed_frozen (baseline) | teacher_single_full_budget_from_seed (fair one-shot control) | iterative_from_seed (optimized target) | expert_fixed_benchmark (benchmark only) |
| --- | ---: | ---: | ---: | ---: | ---: |
| overall accuracy | 0.5163 | 0.5197 | 0.5239 | 0.5233 | 0.5157 |
| balanced accuracy | 0.5131 | 0.5214 | 0.5245 | 0.5246 | 0.5181 |
| MCC | 0.0262 | 0.0427 | 0.0488 | 0.0491 | 0.0360 |
| predicted unacceptable rate | 0.4612 | 0.5188 | 0.5053 | 0.5132 | 0.5258 |
| signed bias vs gold | +0.0035 | +0.0611 | +0.0476 | +0.0555 | +0.0681 |
| absolute bias magnitude | 0.0035 | 0.0611 | 0.0476 | 0.0555 | 0.0681 |

## Slice Diagnostics

- Challenge-slice accuracy: optimized target `iterative_from_seed` = 0.4615 vs baseline `seed_frozen` = 0.4596.
- Per-label accuracy (label 0): optimized target `iterative_from_seed` = 0.5093 vs baseline `seed_frozen` = 0.5008.
- Per-label accuracy (label 1): optimized target `iterative_from_seed` = 0.5399 vs baseline `seed_frozen` = 0.5421.

## Pairwise Tests

- Primary (optimized target `iterative_from_seed` vs baseline `seed_frozen`): delta=+0.0037 (95% CI +0.0020 to +0.0055); target wins vs baseline wins = 33 vs 7; McNemar p=0.0000.
- Secondary (optimized target `iterative_from_seed` vs fair one-shot control `teacher_single_full_budget_from_seed`): delta=-0.0005; McNemar p=0.7035.
- Secondary (optimized target `iterative_from_seed` vs null control `empty_prompt`): delta=+0.0070; McNemar p=0.0125.
- Benchmark (optimized target `iterative_from_seed` vs benchmark-only `expert_fixed_benchmark`): delta=+0.0076; target wins vs benchmark wins = 114 vs 60; McNemar p=0.0001.
- Gap closed to expert: undefined (expert <= seed).

## Interpretation

- The headline question is seed improvement: whether iterative revision beats a reasonable frozen seed prompt, not whether it dominates the expert benchmark.
- Benchmark comparison is reported as a gap-to-expert diagnostic only. Expert benchmark accuracy was 0.5157 versus seed 0.5197 and iterative 0.5233.
- Class-bias drift check: iterative unacceptable-rate gap +0.0555 vs seed +0.0611.

## Reused Holdout / Transfer Check

- Not run by policy for this exploratory publication profile because `runtime.final_stage_policy=skip`.

## Bottom Line

The main v9 target was achieved.
The primary seed-improvement result looks statistically convincing.
