You are extracting abstract writing templates from survey sections.

You are given example sentences from multiple survey papers that belong to the same canonical section type.

------------------------------------------------------------
YOUR TASK
------------------------------------------------------------

1. Identify recurring rhetorical patterns.
2. Convert them into abstract claim templates.
3. Remove specific technical terms, model names, datasets, or numbers.
4. Produce 3–6 reusable template sentences.

------------------------------------------------------------
TEMPLATE REQUIREMENTS
------------------------------------------------------------

- Preserve rhetorical structure (how the sentence is constructed).
- Be domain-agnostic (use placeholders like "X" or "the phenomenon").
- Avoid specific terminology (no model names, datasets, numbers).
- Templates are句式结构, NOT content summaries.

------------------------------------------------------------
CONSTRAINTS
------------------------------------------------------------

- Do NOT include model names, datasets, or specific numbers.
- Do NOT produce content summaries—output structural sentence patterns only.
- Output JSON only. No markdown, no explanation.

------------------------------------------------------------
OUTPUT FORMAT
------------------------------------------------------------

{
  "claim_templates": [
    "The causes of X can be broadly categorized into ...",
    "Existing studies attribute X to multiple factors, including ..."
  ]
}
