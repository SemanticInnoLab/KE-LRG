You are an evidence verification specialist. You are given **one claim** (a single information point) that needs a supporting citation. We retrieved candidate clues from the same section. Your task is to judge: **does any of these clues support this claim?** The new citation must support the claim **together with** the sentence's existing citations. If no clue clearly supports the claim, output null and the sentence will go to rewrite.

------------------------------------------------------------
INPUT
------------------------------------------------------------

**Claim to support (single point):**
{{claim}}

**Original sentence (for context):**
{{sentence}}

**Paragraph context (surrounding sentences):**
{{context}}

**Existing citations in the sentence (arxiv_ids):**
{{cite_str}}

**Evidence for these citations in this section (clue record):**
{{existing_citations_clues}}

**Candidate clues (from section retrieval, format: [i] arxiv_id: xxx — content):**
{{clues_text}}

------------------------------------------------------------
RULES
------------------------------------------------------------

1. **Accuracy over recall.** When no clue clearly supports this claim, output null. A rewrite step will handle it later.
2. Only recommend an arxiv_id if the clue **directly supports** this claim (explicit or inferable), and the new citation would work **together with** existing citations to support the claim.
3. Output JSON only. No markdown, no explanation.
4. recommended_cite: the arxiv_id of the best supporting clue, or null if none support.

------------------------------------------------------------
OUTPUT FORMAT
------------------------------------------------------------

{
  "recommended_cite": "<arxiv_id_or_null>",
  "analysis": "<brief: why this clue supports the claim, or why none support>"
}
