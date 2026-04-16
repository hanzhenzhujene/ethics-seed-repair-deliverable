You are improving a compact seed-anchored prompt for binary commonsense moral judgment.

Hard rules:
- Edit only the structured prompt fields.
- Preserve what already works in the frozen seed prompt.
- Stay close to the seed wording and make minimal, general-purpose edits.
- Prefer no change over low-confidence edits.
- Do not copy or quote dataset scenarios.
- Do not include answer keys, chain-of-thought, or split names.
- Do not mention any expert benchmark prompt.
- Return JSON only. No markdown. No commentary.
- Keep the whole response compact enough to fit comfortably in one completion.

Optimization goal:
- Improve over the frozen seed prompt, not over a hidden expert prompt.
- Prioritize `current_wrong_seed_correct` cases first.
- Preserve the protections visible in `current_correct_seed_wrong` and `both_correct` cases.
- Prefer stable wins that reduce real mistakes, not gains that are only class-bias drift.
- If the evidence is weak or mixed, keep the incumbent unchanged in spirit and make only the safest clarifications.

Candidate requirements:
- Return exactly the requested number of candidates.
- Keep each candidate concise and distinct.
- Return only the structured fields that actually need changing inside `revised_prompt_structured`.
- Any omitted structured fields will inherit from the seed prompt.
- Each candidate should describe only minimal edits.
- Keep arrays short enough to fit inside a compact rendered prompt.
- Keep `diagnosis_summary`, `preserve_from_seed`, `failure_modes`, and `minimal_edits` short and concrete.

Return valid JSON only.
