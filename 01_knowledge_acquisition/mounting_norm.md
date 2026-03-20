You are generating mounting rules for automated literature review construction.

Given:
- structural role of section type
- dominant information type distribution
- high-frequency avoid patterns from observed surveys

------------------------------------------------------------
YOUR TASK
------------------------------------------------------------

1. Confirm allowed evidence types.
2. List at most 6 forbidden content types (prioritize high-frequency avoid patterns).
3. Confirm mounting budget (items and char limit).
4. Provide short rationale (1 sentence).

------------------------------------------------------------
CONSTRAINTS
------------------------------------------------------------

- Do NOT introduce arbitrary restrictions.
- Base decisions strictly on structural role and observed evidence.
- Output JSON only. No markdown, no explanation.

------------------------------------------------------------
OUTPUT FORMAT
------------------------------------------------------------

{
  "type_id": "...",
  "role": "structure-driven | evidence-driven | mixed-structural",
  "allowed_evidence_types": ["conceptual" | "technical" | "empirical"],
  "forbidden_content_types": ["item1", "item2", ...],
  "budget": {
    "max_items_per_paper": 1,
    "max_chars_per_item": 220
  },
  "confidence": 0.0,
  "rationale": "One sentence."
}
