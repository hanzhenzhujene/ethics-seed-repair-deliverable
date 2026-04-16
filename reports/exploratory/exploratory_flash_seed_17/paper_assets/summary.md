# V9 Paper Assets Summary

## Run Status

- Run root: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/outputs/v9_publication/runs/exploratory_flash_seed_17`
- Current phase: `complete`
- Cross-fit complete: `True`
- Transfer check complete: `False`

## Headline Result

- `iterative_from_seed` beats `seed_frozen` on completed cross-fitted evaluation by 0.0002 accuracy points (95% CI -0.0020 to 0.0022).
- McNemar p-value for the primary comparison: 1 with discordant pairs 27 vs 26.
- `iterative_from_seed` also improves over the fair one-shot control by 0.0026 accuracy points.
- Relative to the expert benchmark, the iterative arm has a delta of 0.0046.

## Interpretive Status

- Confirmed in the completed exploratory run: `iterative_from_seed` beats `seed_frozen`.
- Suggestive but unresolved: `iterative_from_seed` may beat the fair one-shot full-budget control.
- Contextual only: comparisons to the expert benchmark and empty prompt help interpretation but are not the main claim.

## Figure Assets

- Seed Repair At A Glance: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/figures/seed_repair_at_a_glance.png`
- Repair ledger: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/figures/repair_ledger.png`
- Fold-stability figure: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/figures/fold_stability.png`
- Selector-trajectory figure: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/figures/selector_trajectory.png`
- Mechanism scatter: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/figures/mechanism_accuracy_vs_gap.png`
- Contamination-control schematic: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/figures/contamination_control_schematic.png`
- Appendix overview figure: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/figures/crossfit_overview.png`
- Appendix pairwise delta figure: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/figures/pairwise_deltas.png`

## Table Assets

- Main results table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/main_results.md`
- Pairwise tests table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/pairwise_tests.md`
- Fold-level table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/fold_level_results.md`
- Mechanism summary table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/mechanism_summary.md`
- Error-transition table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/error_transitions.md`
- Length-bucket slice table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/length_bucket_slices.md`
- Source-split slice table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/source_split_slices.md`
- Prompt-history table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/prompt_history.md`
- Arm-budget table: `/Users/hanzhenzhu/Desktop/ethics-iterative-prompt-rewriting-experiment/reports/v9_publication/exploratory_flash_seed_17/paper_assets/tables/arm_budget_table.md`

## Transfer Check

- The reused holdout / transfer check was intentionally not run for this exploratory publication profile because `runtime.final_stage_policy=skip`.
