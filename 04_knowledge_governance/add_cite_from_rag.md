You are an evidence verification specialist. The following sentence has **unsupported** or **weakly_supported** claim(s) that require a citation. We retrieved 20 candidate clues from the same section. Your task is to judge: **does any of these clues support the claim(s)?** If yes, output the arxiv_id of the best supporting clue, the supporting snippet from that clue, and your analysis of why it supports the claim.

------------------------------------------------------------
INPUT
------------------------------------------------------------

**Original sentence:**
{{sentence}}

**Unsupported / weakly-supported information points:**
{{points_text}}

**Candidate clues (from section retrieval, format: [i] arxiv_id: xxx — content):**
{{clues_text}}

------------------------------------------------------------
RULES
------------------------------------------------------------

1. **Accuracy over recall:** You do NOT need to find a supporting citation. When no clue clearly supports the claim(s), output null. A rewrite step will handle unsupported claims later—returning null is preferable to recommending a weakly matched paper.
2. Only recommend an arxiv_id if the clue **directly supports** at least one unsupported point (explicit or inferable). When in doubt, prefer null.
3. Output JSON only. No markdown, no explanation.
4. recommended_cite: the arxiv_id of the best supporting clue, or null if none support.
5. supporting_snippet: when recommending a cite, quote the relevant excerpt from that clue that directly supports the claim(s); otherwise null.
6. analysis: brief reasoning (1–2 sentences) for why the clue supports the claim, or why none support when recommended_cite is null.

------------------------------------------------------------
OUTPUT FORMAT
------------------------------------------------------------

{
  "recommended_cite": "<arxiv_id_or_null>",
  "supporting_snippet": "<relevant excerpt from the clue, or null>",
  "analysis": "<why this clue supports the claim, or why none support>"
}
