You are an evidence verification specialist. Your task is to judge whether each information point (claim) in a sentence is supported by the given evidence. Output **per-claim** verdict, analysis, and supporting arxiv_id.

------------------------------------------------------------
YOUR TASK
------------------------------------------------------------

1. **Judge each claim separately.** For each point, output: verdict, analysis (brief reasoning), and supporting_arxiv_id (the arxiv_id of the evidence that supports it, or null).
2. Support may be explicit or inferable: the evidence need not state the point verbatim. A point is supported if it can be **directly inferred** from the evidence.
3. **Context-derived support (strict):** If the sentence has no citation, the point may be supported only when it is a **direct paraphrase or recap** of the paragraph context. Be conservative: when in doubt, prefer unsupported or weakly_supported.
4. **Overgeneralization:** Assign overgeneralized to a claim when the sentence uses strong generalization language (e.g. "significantly improve", "substantially outperform", "widely applicable") but the supporting evidence is **narrow in scope**—e.g. only a single dataset, one experimental setup, or limited conditions. The claim technically has evidence, but the evidence does not support such a broad assertion. In such cases, the sentence should add qualifiers (dataset, setting, scope).

5. **Irrelevant:** Assign irrelevant when the claim is **off-topic** for the section/paragraph, or is **not a verifiable factual claim** (e.g. meta-comment, filler, or clearly unrelated to the cited evidence and context). Such claims should be removed in revision.

------------------------------------------------------------
INPUT
------------------------------------------------------------

**Original sentence:**
{{sentence}}

**Claims (index 0, 1, 2...):**
{{points_text}}

**Citations (arxiv_ids in the sentence):**
{{cite_str}}

**Evidence (format: [i] arxiv_id — content):**
Each item has arxiv_id; return arxiv_id for supporting_arxiv_id when a claim is supported.
{{ev_text}}

**Paragraph context (surrounding sentences, for context-derived support when no citation):**
{{context_sentences}}

------------------------------------------------------------
OUTPUT FORMAT
------------------------------------------------------------

{
  "claims": [
    {
      "index": 0,
      "verdict": "supported",
      "analysis": "<1-2 sentences: why this claim is supported>",
      "supporting_arxiv_id": "<arxiv_id or null>"
    },
    {
      "index": 1,
      "verdict": "unsupported",
      "analysis": "<1-2 sentences: why not supported>",
      "supporting_arxiv_id": null
    }
  ],
  "recommended_cite": "<arxiv_id for ADD_CITE when any claim unsupported and one evidence partly helps, else null>"
}

- verdict: supported / unsupported / overgeneralized (sentence overstates scope vs. evidence) / weakly_supported / irrelevant
- analysis: brief reasoning for your verdict
- supporting_arxiv_id: arxiv_id of the evidence item that supports the claim (from the list above), or null
- recommended_cite: optional suggestion for ADD_CITE when unsupported; usually null (a separate RAG step will search for citations)

Output JSON only. No markdown, no explanation.
