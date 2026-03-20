You are analyzing the WRITING BEHAVIOR of a section in an academic survey paper.

IMPORTANT:
You are NOT summarizing content.
You are extracting structural and rhetorical writing norms.

You are given:
1) The section title.
2) The lead segment (beginning part).
3) A middle sample.
4) The tail segment (ending part).

------------------------------------------------------------
INPUT
------------------------------------------------------------

**Section title:** {section_title}

**Segments (lead / middle / tail):**

{snippets}

------------------------------------------------------------
INSTRUCTIONS
------------------------------------------------------------

1. objective:
   Describe the WRITING PURPOSE of this section in one concise sentence.
   Do NOT describe specific technical methods.
   Focus on what the section aims to accomplish structurally.

2. dominant_information_type:
   Choose ONE dominant type:
   - conceptual (problem framing, taxonomy, trends, high-level synthesis)
   - technical (model mechanisms, algorithm logic, architecture description)
   - empirical (experiments, benchmarks, evaluation metrics, performance analysis)

   Only choose "mixed" if two types are clearly balanced.
   Otherwise choose the dominant one.

3. granularity:
   Choose one:
   - high-level (abstract synthesis, no algorithm-level detail)
   - moderate-detail (mechanism-level description without implementation specifics)
   - fine-detail (algorithm steps, parameter settings, experimental configurations)

   Base your decision strictly on the provided text.

4. organization_pattern:
   Choose the main internal organization pattern:
   - taxonomy-driven
   - group-by-method-family
   - compare-by-dimension
   - chronological
   - problem-solution
   - benchmark-driven
   - narrative-discussion
   - other (specify)

   Only choose patterns observable in the text.

5. avoid:
   List AT MOST 4 content types that are clearly inappropriate for this section,
   based strictly on what is NOT present and would conflict with its writing purpose.
   Do NOT guess based on general academic norms.
   Examples:
   - implementation detail
   - hyperparameter specification
   - exact numeric comparison
   - performance ranking
   - subjective opinion

6. lead_excerpt:
   Extract ONE short sentence (≤160 characters) from the provided text
   that best reflects the section's structural purpose.
   Do NOT modify the sentence.

7. confidence:
   Provide a confidence score between 0 and 1
   based on clarity of structural signals in the text.

------------------------------------------------------------
STRICT CONSTRAINTS
------------------------------------------------------------

- DO NOT summarize technical content.
- DO NOT invent information not present in the text.
- DO NOT produce long explanations.
- Output JSON ONLY.
- All fields must be present.
- avoid must contain no more than 4 items.
- If uncertain, lower the confidence instead of guessing.

------------------------------------------------------------
OUTPUT FORMAT
------------------------------------------------------------

{
  "section_title": "...",
  "objective": "...",
  "dominant_information_type": "...",
  "granularity": "...",
  "organization_pattern": "...",
  "avoid": ["...", "..."],
  "lead_excerpt": "...",
  "confidence": 0.0
}
