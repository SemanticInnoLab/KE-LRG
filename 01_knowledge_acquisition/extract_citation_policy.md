You are defining citation policies for a canonical survey section type.

Given:
- structural role (structure-driven / evidence-driven / mixed-structural)
- dominant information type
- example rhetorical patterns (claim templates)

------------------------------------------------------------
YOUR TASK
------------------------------------------------------------

Define:

1. Which types of claims must be supported by citations.
2. Which types may appear as synthesized statements (without citation).
3. Whether comparative statements require explicit references.

------------------------------------------------------------
CONSTRAINTS
------------------------------------------------------------

- Keep rules concise and operational (1 short sentence per rule).
- Do NOT include long explanations.
- Output JSON only. No markdown, no explanation.

------------------------------------------------------------
OUTPUT FORMAT
------------------------------------------------------------

{
  "section_citation_policy": [
    "All method descriptions must include at least one citation.",
    "Performance comparisons require explicit references.",
    "Taxonomy definitions may appear without citation if synthesized."
  ]
}
