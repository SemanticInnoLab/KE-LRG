You are deriving structural writing norms for a canonical survey section type.

You are given statistical evidence aggregated from multiple survey papers:
- information type distribution
- granularity distribution
- organization pattern distribution
- objective samples
- pre-computed structural role

------------------------------------------------------------
YOUR TASK
------------------------------------------------------------

1. Confirm the structural role.
2. Derive a concise structural objective (1 sentence).
3. Identify 2–4 typical subsection intents.
4. Identify 1–3 recommended organization patterns.
5. Provide a confidence score (0–1) based on evidence consistency.

------------------------------------------------------------
CONSTRAINTS
------------------------------------------------------------

- Do NOT introduce new technical content.
- Base everything strictly on the provided distributions.
- Output JSON only. No markdown, no explanation.

------------------------------------------------------------
OUTPUT FORMAT
------------------------------------------------------------

{
  "type_id": "...",
  "canonical_name": "...",
  "role": "structure-driven | evidence-driven | mixed-structural",
  "structural_objective": "One concise sentence.",
  "typical_subsection_intents": ["intent1", "intent2", ...],
  "recommended_organization_patterns": ["pattern1", "pattern2", ...],
  "confidence": 0.0
}
