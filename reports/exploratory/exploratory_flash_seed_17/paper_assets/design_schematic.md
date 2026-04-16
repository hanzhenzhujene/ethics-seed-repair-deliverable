# V9 Design Schematic

```mermaid
flowchart LR
    A["Official ETHICS train + validation"] --> B["Deterministic train-validation development pool"]
    B --> C["Outer fold split"]
    C --> D["Outer Test"]
    C --> E["Inner Pool"]
    E --> F["Teacher Dev"]
    E --> G["Calibration Dev"]
    E --> H["Selector Dev"]

    F --> I["Teacher digest and candidate revisions"]
    G --> J["Same-batch candidate comparison"]
    H --> K["Stopping and final prompt selection"]
    J --> K
    K --> L["Frozen prompt per arm"]
    D --> M["Out-of-fold evaluation"]

    N["Official ETHICS test"] --> O["Reused Holdout / Transfer Check"]
```

## Interpretation

- `teacher_dev` is visible to the teacher.
- `calibration_dev` is used for same-batch candidate ranking.
- `selector_dev` is used only for stopping and final prompt choice.
- `outer_test` is untouched until the prompt is frozen.
- the official test split remains a reused holdout / transfer check and is
  never used during adaptation.
