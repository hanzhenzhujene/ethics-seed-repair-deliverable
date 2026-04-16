# V9 Paper Assets Summary

## Run Status

- Run root: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/outputs/v9_publication/runs/exploratory_flash_seed_23`
- Current phase: `complete`
- Cross-fit complete: `True`
- Transfer check complete: `False`

## Headline Result

- Optimized target: `iterative_from_seed`. Baseline: `seed_frozen`.
- `iterative_from_seed` beats `seed_frozen` on completed cross-fitted evaluation by 0.0037 accuracy points (95% CI 0.0020 to 0.0055).
- McNemar p-value for the primary comparison: 4.228e-05 with target wins vs baseline wins = 33 vs 7.
- `iterative_from_seed` also improves over the fair one-shot control by -0.0005 accuracy points.
- Relative to the expert benchmark, the iterative arm has a delta of 0.0076.

## Interpretive Status

- Confirmed in the completed exploratory run: `iterative_from_seed` beats `seed_frozen`.
- Suggestive but unresolved: `iterative_from_seed` may beat the fair one-shot full-budget control.
- Contextual only: comparisons to the expert benchmark and empty prompt help interpretation but are not the main claim.

## Figure Assets

- Seed Repair At A Glance: `figures/seed_repair_at_a_glance.png`
- Fold-stability figure: `figures/fold_stability.png`
- Selector-trajectory figure: `figures/selector_trajectory.png`
- Mechanism scatter: `figures/mechanism_accuracy_vs_gap.png`
- Contamination-control schematic: `figures/contamination_control_schematic.png`
- Appendix overview figure: `figures/crossfit_overview.png`
- Appendix pairwise delta figure: `figures/pairwise_deltas.png`

## Table Assets

- Main results table: `tables/main_results.md`
- Pairwise tests table: `tables/pairwise_tests.md`
- Fold-level table: `tables/fold_level_results.md`
- Mechanism summary table: `tables/mechanism_summary.md`
- Error-transition table: `tables/error_transitions.md`
- Length-bucket slice table: `tables/length_bucket_slices.md`
- Source-split slice table: `tables/source_split_slices.md`
- Prompt-history table: `tables/prompt_history.md`
- Arm-budget table: `tables/arm_budget_table.md`

## Transfer Check

- The reused holdout / transfer check was intentionally not run for this exploratory publication profile because `runtime.final_stage_policy=skip`.
