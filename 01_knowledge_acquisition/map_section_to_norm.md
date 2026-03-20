You are mapping outline sections to canonical norm types from a NormBank.

## Input

**Outline sections** (from our generated survey outline):
Each section has: section_number, title, description.
- section_number: e.g. "1", "2", "2.1", "2.2", "3" (primary sections use integers; subsections use "X.Y")
- title: section title
- description: what the section should cover

**NormBank canonical types** (from similar surveys):
Each norm has: type_id, canonical_name, aliases, role.
- type_id: e.g. T1, T2, T3
- canonical_name: standard name for this section type
- aliases: alternative titles that belong to this type
- role: structure-driven | evidence-driven | mixed-structural

## Task

For EACH outline section, choose the BEST-matching norm type by semantic similarity.
Consider:
- Semantic similarity of section title to canonical_name and aliases
- Consistency of section description with the norm's structural role
- For Introduction (section 1): prefer norms with "introduction" in canonical_name/aliases
- For Conclusion: prefer norms with "conclusion" or "future" in canonical_name/aliases
- Subsections (2.1, 2.2) can inherit from parent section (2) or map to more specific norms

If no good match exists, use "NONE" for that section.

## Output Format (JSON only, no markdown)

{
  "mapping": [
    {"section_number": "1", "type_id": "T1"},
    {"section_number": "2", "type_id": "T2"},
    {"section_number": "2.1", "type_id": "T2"},
    {"section_number": "2.2", "type_id": "T3"},
    {"section_number": "3", "type_id": "T4"}
  ]
}

- Use EXACT section_number strings from the input.
- Use EXACT type_id strings from the NormBank (T1, T2, etc.) or "NONE".
- Include ALL outline sections in the mapping.
- Output valid JSON only. No explanation.
