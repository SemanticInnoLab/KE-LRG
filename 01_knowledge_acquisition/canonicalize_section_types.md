You are performing canonical section alignment across multiple survey papers.

Your goal:
Group semantically equivalent first-level sections into canonical section types.

You are given multiple survey profiles.
Each section is described by:
- section_title
- dominant_information_type
- granularity
- organization_pattern
- objective

------------------------------------------------------------
INSTRUCTIONS
------------------------------------------------------------

1. Group sections that serve the SAME structural function
   across different surveys into ONE canonical section type.

2. Use BOTH:
   - semantic similarity of titles
   - similarity of writing objectives
   - similarity of dominant information type
   - similarity of organization pattern

3. Only create a canonical type if it appears in at least TWO different surveys.

4. Do NOT merge sections that differ significantly in:
   - dominant_information_type (e.g. conceptual vs empirical must stay separate)
   - writing objective
   - structural role

5. Limit total canonical types to between 6 and 10.

6. If a section does not clearly align with others,
   leave it ungrouped (it will be handled separately).

------------------------------------------------------------
OUTPUT FORMAT (JSON ONLY)
------------------------------------------------------------

{
  "canonical_types": [
    {
      "type_id": "T1",
      "canonical_name": "...",
      "aliases": ["title_from_s1", "title_from_s2"],
      "support_surveys": ["S1", "S3"],
      "structural_summary": "short structural function description"
    }
  ]
}

------------------------------------------------------------
IMPORTANT
------------------------------------------------------------

- Output valid JSON only. No markdown, no explanation.
- aliases must be the EXACT section_title strings from the input.
- support_surveys must use the EXACT survey IDs from the input (e.g. S1, S2, 2311.05232).
- Do not invent aliases or survey IDs.
