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

Did iterative_from_seed improve over seed_frozen under the v9 large-round seed-improvement protocol? Yes.

## V9 Seed-Improvement Cross-Fitted Result

| Metric | empty_prompt | seed_frozen | teacher_single_full_budget_from_seed | iterative_from_seed | expert_fixed_benchmark |
| --- | ---: | ---: | ---: | ---: | ---: |
| overall accuracy | 0.5214 | 0.5226 | 0.5201 | 0.5228 | 0.5181 |
| balanced accuracy | 0.5184 | 0.5242 | 0.5197 | 0.5238 | 0.5201 |
| MCC | 0.0369 | 0.0483 | 0.0393 | 0.0474 | 0.0402 |
| predicted unacceptable rate | 0.4629 | 0.5176 | 0.4940 | 0.5104 | 0.5229 |
| signed bias vs gold | +0.0038 | +0.0584 | +0.0348 | +0.0513 | +0.0638 |
| absolute bias magnitude | 0.0038 | 0.0584 | 0.0348 | 0.0513 | 0.0638 |

## Slice Diagnostics

- Challenge-slice accuracy: iterative_from_seed=0.4541 vs seed_frozen=0.4561.
- Per-label accuracy (label 0): iterative_from_seed=0.5114 vs seed_frozen=0.5047.
- Per-label accuracy (label 1): iterative_from_seed=0.5361 vs seed_frozen=0.5438.

## Pairwise Tests

- Primary (`iterative_from_seed` vs `seed_frozen`): delta=+0.0002 (95% CI -0.0020 to +0.0022); discordant pairs=27 vs 26; McNemar p=1.0000.
- Secondary (`iterative_from_seed` vs `teacher_single_full_budget_from_seed`): delta=+0.0026; McNemar p=0.1210.
- Secondary (`iterative_from_seed` vs `empty_prompt`): delta=+0.0014; McNemar p=0.6363.
- Benchmark (`iterative_from_seed` vs `expert_fixed_benchmark`): delta=+0.0046; discordant pairs=89 vs 56; McNemar p=0.0077.
- Gap closed to expert: undefined (expert <= seed).

## Interpretation

- The headline question is seed improvement: whether iterative revision beats a reasonable frozen seed prompt, not whether it dominates the expert benchmark.
- Benchmark comparison is reported as a gap-to-expert diagnostic only. Expert benchmark accuracy was 0.5181 versus seed 0.5226 and iterative 0.5228.
- Class-bias drift check: iterative unacceptable-rate gap +0.0513 vs seed +0.0584.

## Reused Holdout / Transfer Check

- Not run by policy for this exploratory publication profile because `runtime.final_stage_policy=skip`.

## Bottom Line

The main v9 target was achieved.
The primary seed-improvement result is not yet statistically convincing.
